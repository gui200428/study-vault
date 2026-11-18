## Deadlock (impasse):

**Definição:** Situação em que duas ou mais threads ficam esperando **indefinidamente** por recursos que estão presos umas pelas outras.

- **Situação-problema: duas pessoas precisam de dois recursos compartilhados.** Cada uma pega um dos recursos e fica esperando o outro ser liberado. Como nenhuma solta o que já tem, ninguém nunca consegue os dois.
- **Cada thread possui um lock e aguarda o outro.** O processo não trava com erro, ele simplesmente nunca termina.

```
        possui                    possui
Thread A ──────→ RECURSO_1   Thread B ──────→ RECURSO_2

Thread A ── espera RECURSO_2 (que está com B)
Thread B ── espera RECURSO_1 (que está com A)

        ┌──────────────┐
        ↓              │
    Thread A ──→ Thread B
        │              ↑
        └──────────────┘
         ciclo de espera
```

→ Deadlock é um **ciclo de espera bloqueada**.


## Deadlock x espera normal x starvation x livelock:

Nem toda thread parada é deadlock.

### 1. Espera normal:
- A thread espera um recurso, mas quem está com ele **vai liberar** em algum momento. A espera tem fim.

### 2. Starvation (inanição):
- Uma thread **nunca recebe oportunidade/recurso**, enquanto as outras continuam progredindo normalmente.

### 3. Livelock:
- Existe **atividade, mas sem progresso**. As threads não estão bloqueadas, ficam o tempo todo fazendo alguma coisa (tentando, desistindo, tentando de novo), mas nenhuma avança.

### 4. Deadlock:
- **Ciclo de espera bloqueada.** As threads estão paradas, uma esperando a outra, e nenhuma vai sair disso sozinha.

```
starvation → só uma fica sem recurso, o resto anda
livelock   → todas trabalham, nenhuma avança
deadlock   → todas paradas, esperando em ciclo
```


## Condições de Coffman:

**Definição:** São as quatro condições que precisam estar presentes **ao mesmo tempo** para um deadlock clássico acontecer.

### 1. Exclusão mútua:
- **Um recurso só pode ser usado por uma thread por vez.** Se o recurso pudesse ser compartilhado, ninguém precisaria esperar.

### 2. Posse e espera:
- **A thread mantém um recurso enquanto espera por outro.** Ela não solta o que já pegou antes de conseguir o próximo.

### 3. Não preempção:
- **O recurso não pode ser retirado à força de quem o possui.** Só a própria thread pode liberar.

### 4. Espera circular:
- **T1 espera algo de T2, que espera algo de T1.** As esperas fecham um ciclo.

→ Como as quatro precisam acontecer juntas, **basta quebrar uma delas para impedir o deadlock**. As soluções da aula atacam exatamente isso, sem abandonar a sincronização.

### Onde cada condição aparece no código Java:

| Condição | Onde aparece no programa? |
|---|---|
| Exclusão mútua | blocos `synchronized` |
| Posse e espera | `synchronized` aninhado |
| Não preempção | a JVM não retira o monitor da thread |
| Espera circular | A: 1→2; B: 2→1 |

**Obs:** Em Java, cada objeto usado no `synchronized` funciona como um lock (o **monitor** do objeto). Enquanto a thread está dentro do bloco, ela é dona do monitor e nenhuma outra entra.


## Produzindo o deadlock:

Duas threads usam os mesmos dois recursos, mas pegam em **ordem inversa**:

```java
// Thread-A: RECURSO_1 → RECURSO_2
() -> usarRecursos(RECURSO_1, RECURSO_2, "RECURSO_1", "RECURSO_2")

// Thread-B: RECURSO_2 → RECURSO_1
() -> usarRecursos(RECURSO_2, RECURSO_1, "RECURSO_2", "RECURSO_1")
```

```java
synchronized (primeiro) {
    // ...obteve o primeiro
    synchronized (segundo) {   // tenta o segundo SEM soltar o primeiro
        System.out.println("Esta linha nunca será alcançada.");
    }
}
```

**Saída:** (a ordem pode variar)

```text
Thread-A: obteve RECURSO_1
Thread-B: obteve RECURSO_2
Thread-A: tentando obter RECURSO_2
Thread-B: tentando obter RECURSO_1
```

→ Cada thread pegou o primeiro recurso dela e ficou esperando o segundo, que está com a outra. O processo não termina (só com `Ctrl+C`).

**Obs:** A ordem das mensagens muda de uma execução para outra porque o escalonamento das threads não é determinístico.

- **O `synchronized` aninhado é o que cria a posse e espera.** A thread entra no segundo bloco ainda dentro do primeiro, ou seja, segurando o primeiro lock.
- **A ordem inversa (A: 1→2, B: 2→1) é o que cria a espera circular.** Se as duas pedissem na mesma ordem, não teria ciclo.

**Obs:** O código usa um `CountDownLatch` (uma barreira) para garantir que as duas threads peguem o primeiro lock antes de tentar o segundo. Ele e o `Thread.sleep` dos exemplos só servem para **tornar a intercalação reproduzível**, não são a causa do deadlock. Sem eles o deadlock continua possível, só fica mais raro de aparecer.


## Diagnóstico do deadlock:

### 1. Pelo terminal:

Em outro terminal, encontra o PID do processo Java e gera um **thread dump** (fotografia do estado de todas as threads):

```bash
jps -l        # lista os processos Java e seus PIDs
jstack PID    # gera o thread dump
jcmd PID Thread.print   # alternativa ao jstack
```

- **No final do relatório aparece `Found one Java-level deadlock`.** O relatório também mostra qual monitor cada thread possui e qual ela está esperando, ou seja, dá para ver o ciclo.

### 2. Dentro da própria aplicação:

A JVM consegue procurar deadlocks sozinha pela API de gerenciamento:

```java
ThreadMXBean bean = ManagementFactory.getThreadMXBean();
long[] ids = bean.findDeadlockedThreads();
```

- **`findDeadlockedThreads()` procura ciclos envolvendo monitores `synchronized` ou locks próprios.** Se não achar nada, retorna `null`; se achar, devolve os ids das threads envolvidas.
- **Uma thread monitora a aplicação, imprime quem espera por qual lock e quem mantém esse lock, e encerra o processo.** O encerramento é com `System.exit(0)`, porque as threads bloqueadas nunca terminariam sozinhas.

```text
- Thread-A espera por <lock>, mantido por Thread-B
- Thread-B espera por <lock>, mantido por Thread-A
```

**Detectar não significa recuperar.** Em produção, o programa pode registrar métricas e detalhes para análise, mas liberar com segurança os recursos de uma thread qualquer costuma ser difícil.

→ Uma espera longa não prova deadlock. A prova é o **ciclo** aparecendo no thread dump ou no `findDeadlockedThreads()`.


## Solução 1: ordem global para adquirir locks:

**Definição:** Todas as threads adquirem os locks **sempre na mesma ordem** (ex.: primeiro `RECURSO_1`, depois `RECURSO_2`), independentemente de qual thread seja.

```java
// Regra global: todos adquirem RECURSO_1 antes de RECURSO_2.
synchronized (RECURSO_1) {
    synchronized (RECURSO_2) {
        System.out.println(nome + ": obteve RECURSO_2 e concluiu");
    }
}
```

- **Uma das threads pode precisar esperar, mas não existe ciclo.** Quem pegou o `RECURSO_1` primeiro consegue pegar o `RECURSO_2` também; a outra fica esperando o `RECURSO_1` sem segurar nada, então a espera tem fim.
- **Quebra a condição de espera circular.** As outras três condições continuam lá (os blocos `synchronized` não foram removidos).

```
Thread-A: RECURSO_1 → RECURSO_2   (conclui e libera)
Thread-B: espera RECURSO_1 ... → RECURSO_1 → RECURSO_2   (conclui)
```

Com os `join()` no final, o main só termina quando as duas acabaram: `"As duas threads terminaram: não houve deadlock."`

**Obs:** O `Thread.sleep()` dentro do bloco suspende a thread **sem liberar os monitores que ela possui**. Ou seja, dormir segurando um lock continua bloqueando quem precisa dele.

### Vantagens:
- Simples e eficiente.
- Funciona bem quando os recursos têm identidade e uma ordem estável.

### Cuidados:
- **A regra precisa ser seguida em todo o sistema.** Basta um trecho de código pegar na ordem errada para o ciclo voltar a ser possível.
- Pode ser difícil definir uma ordem quando os recursos são descobertos dinamicamente.


## Solução 2: tryLock com timeout:

**Definição:** Em vez de esperar o lock para sempre, a thread **tenta adquirir dentro de um prazo**. Se não conseguir o segundo lock a tempo, **libera o primeiro** e tenta de novo depois.

Para isso não dá para usar `synchronized` (ele sempre espera indefinidamente). Usa-se um lock explícito, o `ReentrantLock`, que tem o `tryLock` com tempo limite.

**Obs:** No exemplo, as threads continuam pegando os locks em **ordem inversa** (A: `LOCK_1 → LOCK_2`, B: `LOCK_2 → LOCK_1`), igual ao caso do deadlock. Mesmo assim o programa termina (`"Programa encerrado sem espera indefinida."`), porque quem não consegue o segundo lock desiste e solta o primeiro.

```java
obtevePrimeiro = primeiro.tryLock(200, TimeUnit.MILLISECONDS);
// ...
obteveSegundo = segundo.tryLock(200, TimeUnit.MILLISECONDS);
```

### Funcionamento:

```
tentativa (até 5)
    ↓
tenta o 1º lock por até 200 ms
    ├── não conseguiu → próxima tentativa
    ↓
tenta o 2º lock por até 200 ms
    ├── conseguiu → executa e termina
    └── não conseguiu → "desistiu da tentativa"
            ↓
     libera os locks que tinha (finally)
            ↓
     espera um tempo aleatório (backoff)
            ↓
     próxima tentativa
```

- **Ao desistir, a thread solta o primeiro lock.** Isso elimina a posse durante a próxima tentativa, então a outra thread consegue avançar.
- **Os locks são liberados no `finally`.** Com `ReentrantLock` a liberação é manual (`unlock()`), e o `finally` garante que ela aconteça em sucesso, falha ou desistência.
- **Espera aleatória (backoff) entre tentativas.** Se as duas threads desistissem e tentassem de novo sempre no mesmo ritmo, poderiam ficar se atrapalhando para sempre (livelock). O tempo aleatório reduz esse risco.
- **Limite de tentativas.** Garante que o programa sempre tenha um fim controlado (`"limite de tentativas atingido"`).

→ Evita espera indefinida e permite **recuperação controlada**: o programa consegue desistir, registrar, repetir ou devolver erro.

### Vantagens:
- Permite desistir, registrar, repetir ou devolver erro.
- Útil quando não existe uma ordem global prática.

### Cuidados:
- Timeout **não garante justiça** (uma thread pode ficar perdendo sempre).
- Tentativas agressivas podem causar **livelock** ou consumo excessivo de CPU.
- Em sistemas reais: usar espera aleatória/backoff e limite de tentativas.


## Ordem global x timeout:

| | Ordem global | tryLock com timeout |
|---|---|---|
| Ideia | todos pegam os locks na mesma ordem | tenta por um tempo, se falhar solta e tenta de novo |
| Condição atacada | espera circular | posse e espera (solta o que tinha ao desistir) |
| Ferramenta em Java | `synchronized` normal | `ReentrantLock` + `tryLock` |
| Quando usar | recursos com identidade e ordem estável | quando não há ordem global prática |
| Risco | alguém não seguir a regra | injustiça, livelock, gasto de CPU |


## Exemplo: transferências bancárias:

### O problema:

Duas contas com R$ 1.000 cada (conta A `id = 1`, conta B `id = 2`) e duas transferências ao mesmo tempo, em sentidos opostos:

- `A-para-B`: R$ 100
- `B-para-A`: R$ 200

O método `transferir` bloqueia **primeiro a origem e depois o destino**:

```java
synchronized (origem) {
    synchronized (destino) {
        origem.saldo -= valor;
        destino.saldo += valor;
    }
}
```

```
A-para-B: trava A → espera B
B-para-A: trava B → espera A
        → espera circular → deadlock
```

→ A ordem dos locks depende da **direção da transferência**, então transferências opostas pegam as contas em ordem inversa. A soma dos saldos nunca é exibida porque o main fica preso no `join()` esperando threads que nunca terminam.

### Solução:

Bloquear sempre a conta de **menor `id` primeiro**, independentemente da direção:

```java
Conta primeira = origem.id < destino.id ? origem : destino;
Conta segunda  = origem.id < destino.id ? destino : origem;

synchronized (primeira) {
    synchronized (segunda) {
        // verifica saldo, debita origem, credita destino
    }
}
```

- **As duas transferências travam a conta 1 primeiro e a conta 2 depois.** Não importa quem é origem ou destino, a ordem dos locks é sempre a mesma.
- **Os blocos de sincronização continuam lá.** Só a ordem mudou, então os saldos continuam protegidos contra acesso concorrente.
- **Condição eliminada: espera circular.**

**Resultado:**

```text
Conta A: R$ 1100 | Conta B: R$ 900 | Total: R$ 2000
```

→ A: 1000 − 100 + 200 = 1100. B: 1000 + 100 − 200 = 900. As duas transferências terminam e o total continua R$ 2.000.


## Ideia principal:

**Deadlocks são evitados por projeto, não pela velocidade das threads.**

- Colocar mais `synchronized` sem pensar na ordem pode piorar: mais locks aninhados = mais chances de ciclo.
- Ao revisar código concorrente:
  1. procurar locks aninhados;
  2. documentar uma ordem global;
  3. monitorar bloqueios em produção.

```
ordem global de locks → elimina a espera circular
tryLock com timeout   → evita a espera indefinida
```
