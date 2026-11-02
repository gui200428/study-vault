## Revisando:

### Estágios do pipeline:

**A execução de uma instrução segue uma sequência bem definida, dividida em estágios de pipeline:**
- IF (Instruction Fetch) → Busca a instrução na memória.
- ID (Instruction Decode) → Decodifica a instrução e identifica os operandos.
- EX (Execute) → Realiza a operação (aritmética, lógica, etc.).
- MEM (Memory Access) → Acessa a memória, se necessário.
- WB (Write Back) → Escreve o resultado no registrador de destino.

**Obs:** Cada estágio é executado em um ciclo de clock, e várias instruções podem estar em estágios diferentes ao mesmo tempo, graças ao pipeline.

### Pipeline de instruções:

![[Pasted image 20261024210412.png]]

- **O programa multiplica A = 3 por B = 4 usando somas sucessivas.** Os quatro `addi` iniciais carregam A, B, o contador e o resultado. Dentro do `loop`, o `add` soma A no resultado e o `addi` incrementa o contador, até o `beq` ver que contador == B e pular para `fim`.
- **O loop roda 4 vezes (blocos 1, 2, 3 e 4) e no final x8 contém 12.**
- **Cada instrução entra no pipeline um clock depois da anterior.** Enquanto uma está no EX, a seguinte já está no ID e a outra no IF. A partir do clock 5 o pipeline fica cheio, com 5 instruções em andamento ao mesmo tempo.

```asm
    addi x5, x0, 3    # x5 = A (multiplicando)
    addi x6, x0, 4    # x6 = B (multiplicador)
    addi x7, x0, 0    # x7 = contador
    addi x8, x0, 0    # x8 = resultado
loop:
    beq  x7, x6, fim  # se contador == B, fim
    add  x8, x8, x5   # resultado += A
    addi x7, x7, 1    # contador += 1
    j    x0, loop     # salta para loop (jal x0 = jump sem link)
fim:
    # x8 contém o resultado final: 12
```

**Obs:** A tabela é uma versão idealizada do pipeline:
- Mostra só 4 passagens pelo loop, mas na prática o `beq` roda uma 5ª vez, quando o contador chega em 4, e é essa execução que pula para `fim`.
- Não aparece nenhuma espera, mesmo com o `beq x7, x6, fim` precisando do x7 que o `addi x7, x7, 1` anterior acabou de calcular. Isso é uma dependência de dados, e em um pipeline real geraria bolhas. É exatamente o tipo de limitação do ILP visto mais à frente.


## Ponto fixo vs ponto flutuante:

### 1. Ponto fixo:
**Definição:** O número é armazenado com uma posição fixa para a vírgula (decimal ou binária). Ex: em um sistema de 8 bits, 4 bits para a parte inteira e 4 para a parte fracionária.

- **Precisão:** alta para números pequenos e operações simples.
- **Desempenho:** mais rápido e exige menos do hardware. Ideal para sistemas embarcados e microcontroladores.
- **Limitações:**
	- Faixa de valores limitada.
	- Pode causar erros de arredondamento significativos com números muito grandes ou muito pequenos.

### 2. Ponto flutuante:
**Definição:** Usa uma notação parecida com a científica, então a vírgula "flutua" conforme o necessário.

$$número = mantissa \times base^{expoente}$$

- **Precisão:** menor em alguns casos, mas consegue representar uma faixa muito maior de valores (inclusive muito grandes ou muito pequenos).
- **Desempenho:** mais complexo e exige mais recursos computacionais, mas é essencial para aplicações científicas, gráficos 3D, simulações etc.
- **Vantagens:**
	- Grande faixa dinâmica.
	- Mais adequado para cálculos que envolvem variações de escala.

→ Ponto fixo ganha em velocidade e simplicidade de hardware; ponto flutuante ganha em faixa de valores.

---

## Superescalar:
**Definição:** Termo criado em 1987 para processadores capazes de **executar múltiplas instruções simultaneamente**, aumentando o desempenho em aplicações com operações escalares.

### Características principais:

- **Executa instruções independentes em paralelo, usando múltiplos pipelines.** Se duas instruções não dependem uma da outra, não tem por que uma esperar a outra terminar.
- **Permite reordenar instruções para aproveitar melhor o paralelismo.**
- **Usa várias unidades funcionais, cada uma com seu próprio pipeline.**
- **O hardware e o compilador garantem que a execução paralela preserve a lógica do programa.** Ou seja, o resultado final tem que ser o mesmo que seria executando uma instrução por vez.

### Escalar x superescalar:

![[Pasted image 20261024211537.png|500]]

- **Escalar:** uma instrução por vez, com uma unidade funcional por tipo de operação (uma de inteiro, uma de ponto flutuante).
- **Superescalar:** várias instruções por vez, com múltiplas unidades funcionais operando em paralelo (várias de inteiro e várias de ponto flutuante, todas com pipeline).


## Superpipeline:
**Definição:** Abordagem proposta em 1988 por **Jouppi** que melhora o desempenho **dobrando a velocidade interna do clock**, permitindo que duas tarefas sejam executadas dentro de um único ciclo de clock externo.

### Como funciona:

1. Muitos estágios do pipeline tradicional fazem tarefas que ocupam **menos da metade de um ciclo de clock**. Ou seja, parte do ciclo fica sobrando.
2. Dividindo essas tarefas em partes menores e acelerando o clock interno, o processador consegue **executar dois estágios por ciclo externo**.
3. Isso resulta em uma **maior taxa de instruções por tempo**, sem necessariamente aumentar o número de unidades funcionais.

### Comparação com as outras abordagens:

- **Pipeline comum:** uma instrução por ciclo, com estágios como busca, decodificação, execução e write-back.
- **Superpipeline:** divide cada estágio em subestágios, permitindo **duas instruções em andamento por ciclo**.
- **Superescalar:** executa **múltiplas instruções em paralelo**, usando várias unidades funcionais, cada uma com seu próprio pipeline.

→ O superpipeline acelera o mesmo pipeline; o superescalar coloca vários pipelines lado a lado.

### Limitação:

- **O superpipeline aumenta a taxa de execução, mas não supera o superescalar em situações como início de programa ou desvios de fluxo**, onde o paralelismo do superescalar é mais eficiente. Como o superpipeline tem mais subestágios em sequência, no início do programa ele demora mais para encher, e em um desvio há mais instruções em andamento para descartar.

### Resumo:

![[Pasted image 20261024212248.png|500]]


## Paralelismo em nível de instruções (ILP):
**Definição:** O ILP (Instruction-Level Parallelism) é o quanto as instruções de um programa podem ser executadas em paralelo, em média.

- **A arquitetura superescalar busca aumentar o desempenho executando múltiplas instruções simultaneamente, explorando o ILP.** O superescalar é o hardware; o ILP é o paralelismo que existe no código para esse hardware aproveitar.
- **Para maximizar esse paralelismo, são usadas:**
	1. **Técnicas de hardware:** múltiplas unidades funcionais e pipelines paralelos.
	2. **Otimizações de compilador:** reordenação de instruções e análise de dependências.

## Limitações fundamentais do ILP:

Mesmo com essas técnicas, existem **cinco limitações principais** que restringem o paralelismo:

### 1. Dependência verdadeira de dados (data dependency):
- **Uma instrução depende do resultado de outra anterior.** A segunda só pode executar depois que a primeira produzir o valor.
- **Exemplo:** `A = B + C` seguido de `D = A + E`. O D precisa do A, então tem que esperar a primeira instrução terminar.

### 2. Dependência procedural (control dependency):
- **Relacionada ao fluxo de controle do programa (desvios e loops).**
- **A execução de uma instrução depende da decisão tomada por uma instrução anterior.** Enquanto o desvio não é resolvido, o processador não sabe quais instruções vêm depois.

### 3. Conflitos de recursos (resource conflicts):
- **Duas ou mais instruções competem pelo mesmo recurso de hardware (registradores ou unidades funcionais).** Mesmo sendo independentes, se só existe um recurso, uma delas espera.

### 4. Dependência de saída (output dependency):
- **Duas instruções tentam escrever no mesmo destino.**
- **Exemplo:** `A = B + C` e `A = D + E`. Se a ordem das escritas for invertida, A termina com o valor errado.

### 5. Antidependência (anti-dependency):
- **Uma instrução posterior sobrescreve um operando que uma instrução anterior ainda precisa ler.**
- **Exemplo:** `A = B + C` seguido de `B = D + E`. A segunda escreve em B, então não pode fazer isso antes da primeira ler o B antigo.

**Obs:** No slide a frase aparece invertida: "uma instrução posterior lê um operando que será sobrescrito por uma instrução anterior". O exemplo do próprio slide mostra o caso certo: quem lê é a anterior (`A = B + C` lê B) e quem sobrescreve é a posterior (`B = D + E`).


## ILP x paralelismo de máquina:

**Jouppi e Wall (1989a) fazem uma distinção entre dois conceitos relacionados:** paralelismo em nível de instruções e paralelismo de máquina.

### Paralelismo em nível de instruções:
**Definição:** Existe quando as instruções de uma sequência são independentes e, assim, podem ser executadas em paralelo por sobreposição.

#### Exemplo (Jouppi, 1989b):

```asm
; esquerda                  ; direita
Load R1 ← R2                Add   R3 ← R3, "1"
Add  R3 ← R3, "1"           Add   R4 ← R3, R2
Add  R4 ← R4, R2            Store [R4] ← R0
```

- **As três instruções da esquerda são independentes e, na teoria, todas poderiam ser executadas em paralelo.** Nenhuma usa o resultado de outra.
- **As três da direita não podem ser executadas em paralelo.** A segunda usa o R3 calculado pela primeira, e a terceira usa o R4 calculado pela segunda.

- **O grau de paralelismo depende de quantas vezes ocorrem dependências de dados e de controle no código.** Essas dependências variam conforme a arquitetura do processador e o tipo de aplicação.
- **A latência das operações também influencia.** Latência é o tempo que uma instrução leva para produzir um resultado utilizável por outra; quanto maior, mais a dependência atrasa a execução paralela.

### Paralelismo de máquina:
**Definição:** Mede a capacidade do processador de executar várias instruções ao mesmo tempo, aproveitando o ILP.

**Depende:**
- Do **número de pipelines paralelos** disponíveis.
- Da **eficiência do processador em identificar instruções independentes**.

- **Mesmo que o programa tenha alto paralelismo, o desempenho só é maximizado se o processador tiver estrutura suficiente para explorá-lo.** E o contrário: se o paralelismo de máquina for limitado, o desempenho fica comprometido independentemente do programa.
- **Arquiteturas com instruções de tamanho fixo, como as RISC, facilitam a identificação de paralelismo entre instruções.**

→ ILP é o que o código oferece; paralelismo de máquina é o quanto o hardware consegue aproveitar disso.

### Exemplo com ILP:

Processador com pipeline e várias unidades de execução (ALUs independentes): dá para executar várias instruções ao mesmo tempo, desde que não haja dependência entre elas.

```asm
; Suponha que temos dois pares de inteiros: (A, B) e (C, D)
; Queremos somar A+B e C+D simultaneamente
ADD R1, R2, R3   ; R1 = R2 + R3   (soma A + B)
ADD R4, R5, R6   ; R4 = R5 + R6   (soma C + D)

; Essas duas instruções podem ser executadas em paralelo se o processador tiver duas ALUs
```

- **O compilador ou o hardware identifica instruções independentes e as executa simultaneamente.** Exemplo clássico de ILP.

### Exemplo com paralelismo de máquina (multithreading ou multiprocessing):

Com dois núcleos de CPU disponíveis, o trabalho é dividido entre eles:

```c
// Thread 1
int resultado1 = a + b;

// Thread 2
int resultado2 = c + d;
```

- **Cada thread é atribuída a um núcleo diferente e a execução ocorre em paralelo real.**

**Obs:** Nesse exemplo o paralelismo de máquina aparece como paralelismo entre múltiplos núcleos ou processadores, e não só entre pipelines de um mesmo processador.

### Combinando ILP e paralelismo de máquina:

Em um sistema moderno, o compilador pode gerar código que:
1. **Distribui tarefas entre múltiplos núcleos** (paralelismo de máquina).
2. **Dentro de cada núcleo, organiza as instruções para serem executadas em paralelo** (ILP).


## Execução fora de ordem (Out-of-Order Execution):
**Definição:** Técnica usada em processadores modernos em que o processador **reorganiza dinamicamente as instruções** para aproveitar melhor os recursos internos, **sem alterar o resultado final**.

- **Normalmente as instruções são executadas na ordem em que aparecem no programa (execução em ordem).**

### O problema:
- **Em um pipeline, algumas instruções podem ficar esperando** (ex: aguardando dados da memória). Em execução em ordem, tudo que vem depois fica parado junto.

### Solução:
- **Em vez de parar tudo, o processador executa outras instruções independentes que já estão prontas.**
- Isso **reduz o tempo ocioso** e aumenta a eficiência.

### Exemplo:

```asm
LOAD R1, [MEM]    ; Carrega dado da memória (pode demorar)
ADD  R2, R3, R4   ; Soma valores (não depende do LOAD)
```

- **Em ordem:** o processador esperaria o LOAD terminar antes de fazer o ADD.
- **Fora de ordem:** detecta que o ADD não depende do LOAD e executa o ADD enquanto espera o dado do LOAD chegar.

### Como é implementado:
- **O hardware usa estruturas como:**
	- Reservation Stations
	- Reorder Buffer
- **Elas garantem que, mesmo executando fora de ordem, o resultado final seja correto** (mantém as dependências e a ordem lógica).

### Benefícios:
- Aumenta o paralelismo interno.
- Melhora o uso das unidades funcionais (ALUs, FPUs).
- Reduz bolhas no pipeline.

**Obs:** **Bolhas no pipeline** (pipeline bubbles ou stalls) são ciclos de clock em que nenhuma instrução útil é executada dentro do pipeline.


## Influência do programador:

### 1. O programador pode influenciar, mas não controla diretamente o ILP:

- **O programador não escreve instruções dizendo "execute isso em paralelo" no nível de instrução.** Quem decide isso é o compilador e o hardware.
- **O que ele pode fazer:**
	- Escrever código limpo e otimizado, com instruções independentes.
	- Evitar dependências entre operações (ex: usar variáveis diferentes).
	- Usar diretivas ou extensões específicas (como `#pragma` em C/C++) para sugerir paralelismo ao compilador.

**Exemplo em C com sugestão de paralelismo:**

```c
#pragma GCC ivdep
for (int i = 0; i < N; i++) {
    A[i] = B[i] + C[i];
}
```

- **A diretiva sugere ao compilador que não há dependências entre as iterações, permitindo paralelismo.** É só uma sugestão, o compilador continua decidindo.

### 2. O compilador decide como aplicar o ILP:

- **O compilador analisa o código e tenta reordenar instruções, aplicando técnicas como:**
	- Pipeline
	- Execução fora de ordem
	- Alocação de registradores
	- Unroll de loops
- **Ele faz isso com base nas capacidades do processador-alvo e nas dependências entre instruções.**

**Obs:** **Unroll de loops (loop unrolling)** é uma técnica de otimização usada por compiladores (e às vezes pelo programador) para **reduzir o overhead do controle de loops** e aumentar o desempenho, principalmente em arquiteturas com paralelismo.

### 3. O hardware executa o paralelismo:

- **O hardware é quem realmente executa as instruções em paralelo, se tiver recursos para isso:**
	- Várias unidades funcionais (ALUs, FPU etc.)
	- Execução fora de ordem
	- Multithreading ou multicore
- **Exemplo:** o hardware pode executar duas instruções ADD ao mesmo tempo se elas forem independentes e houver duas ALUs disponíveis.

### 4. O programador pode controlar o paralelismo de máquina:

- **Aqui sim o programador tem mais controle:**
	- Threads (pthread, OpenMP, std::thread)
	- Processos paralelos (MPI)
	- GPUs com CUDA ou OpenCL

**Exemplo com OpenMP:**

```c
#pragma omp parallel for
for (int i = 0; i < N; i++) {
    A[i] = B[i] + C[i];
}
```

- **Aqui o programador está dizendo explicitamente: "execute essas iterações em paralelo".** Diferente do `ivdep`, que só sugere ao compilador.

### Resumo:

![[Pasted image 20261024220931.png|500]]

→ ILP: quem decide é o compilador + hardware, e o programador só influencia indiretamente.
→ Paralelismo de máquina: quem decide é o programador + sistema, e o programador controla diretamente.
