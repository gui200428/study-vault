## Conceitos básicos:

- **Processo:** programa em execução.
- **Burst de CPU:** tempo de CPU que o processo precisa para terminar.
- **Chegada:** momento em que o processo entra na fila de prontos.
- **Escalonador:** regra que decide quem recebe a CPU.

→ Os algoritmos de escalonamento mudam **a ordem** em que os processos usam a CPU. O trabalho total é o mesmo, o que muda é quem espera e quanto.

### Processos usados nos exemplos:

| Processo | Chegada | Burst |
|---|---|---|
| P1 | 0 | 6 |
| P2 | 1 | 2 |
| P3 | 2 | 4 |

Cada algoritmo gera uma linha do tempo com fatias de execução `(início, fim, processo)`, que é desenhada como um **diagrama de Gantt**.


## Métricas:

### 1. Tempo de resposta:
**Definição:** Quanto tempo o processo esperou desde a chegada até usar a CPU **pela primeira vez**.

$$\text{resposta} = \text{início} - \text{chegada}$$

### 2. Tempo de retorno (turnaround):
**Definição:** Tempo total desde a chegada até o processo **terminar**.

$$\text{retorno} = \text{fim} - \text{chegada}$$

### 3. Tempo de espera:
**Definição:** Tempo que o processo passou na fila sem usar a CPU.

$$\text{espera} = \text{retorno} - \text{burst}$$

→ Do tempo total que ele ficou no sistema (retorno), tira o tempo em que ele estava de fato executando (burst). O que sobra é espera.

**Obs:** A resposta mede quando o processo **começa**, o retorno mede quando ele **termina**. Um algoritmo pode melhorar uma sem melhorar a outra.


## 1. FCFS — First Come, First Served:

**Definição:** O primeiro processo que chega executa primeiro e **mantém a CPU até concluir**. É uma fila comum.

- **O processo recebe todo o burst de uma vez. Não há preempção.** Ninguém tira a CPU dele no meio do caminho, só quando ele termina o próximo da fila entra.
- **Se nenhum processo estiver pronto, a CPU fica ociosa até a próxima chegada.**

![[Pasted image 20261117234412.png]]

```text
P1: 0 → 6
P2: 6 → 8
P3: 8 → 12
```

| Processo | Resposta | Espera | Retorno |
|---|---|---|---|
| P1 | 0 | 0 | 6 |
| P2 | 5 | 5 | 7 |
| P3 | 6 | 6 | 10 |
| **Médias** | **3,67** | **3,67** | **7,67** |

### O problema: convoy effect:

**P2 precisa de só 2 ms, mas espera 5.**

- **P1 chegou antes e usa a CPU até terminar.** P2 chegou no instante 1, mas só começa no 6.
- Esse efeito é o **convoy effect** (efeito comboio): **um processo longo atrasa vários processos curtos** que ficam presos atrás dele.


## 2. Round Robin:

**Definição:** Cada processo recebe um **quantum** (fatia fixa de tempo). Se o processo consumir o quantum e ainda não tiver terminado, ele **volta para o fim da fila**.

- **O processo usa no máximo um quantum, mas pode terminar antes.** Se faltar menos que o quantum, ele usa só o que falta e libera a CPU.
- **Isso dá oportunidade para vários processos executarem cedo.** Ninguém fica preso atrás de um processo longo, porque o longo é interrompido a cada quantum.
- **Processos que chegam durante o turno entram na fila antes do processo que acabou de ser interrompido.** Ele volta para o fim depois deles.
- **Se a fila de prontos estiver vazia, a CPU fica ociosa até a próxima chegada**, igual no FCFS.

### Exemplo com quantum = 2 ms:

```text
t=0   fila: [P1]          → P1 executa 0–2   (falta 4)
t=2   chegaram P2 e P3    → fila: [P2, P3, P1]
      P2 executa 2–4      (terminou)
t=4   P3 executa 4–6      (falta 2) → fila: [P1, P3]
t=6   P1 executa 6–8      (falta 2) → fila: [P3, P1]
t=8   P3 executa 8–10     (terminou)
t=10  P1 executa 10–12    (terminou)
```

![[Pasted image 20261117234731.png]]

| Processo | Resposta | Espera | Retorno |
|---|---|---|---|
| P1 | 0 | 6 | 12 |
| P2 | 1 | 1 | 3 |
| P3 | 2 | 4 | 8 |
| **Médias** | **1,00** | **3,67** | **7,67** |

### FCFS x Round Robin (mesmos processos):

Os dois algoritmos rodam sobre a mesma carga (P1, P2, P3) para a comparação ser justa.

| Médias | FCFS | Round Robin (q = 2) |
|---|---|---|
| Resposta | 3,67 | **1,00** |
| Espera | 3,67 | 3,67 |
| Retorno | 7,67 | 7,67 |

- **A resposta média caiu de 3,67 para 1,00.** Todo mundo começa a executar cedo.
- **Espera e retorno médios ficaram iguais.** O tempo foi redistribuído: P2 e P3 ganharam (P2 caiu de 5 para 1 de espera), mas P1, que é longo, passou a esperar 6 em vez de 0.

→ O Round Robin favorece os processos curtos e a sensação de resposta rápida, às custas do processo longo.


## Experimento: o quantum muda o resultado:

**Quantum pequeno costuma melhorar a resposta, mas cria mais trocas de contexto.**

- Cada fatia é uma entrada de um processo na CPU. **Quanto menor o quantum, mais fatias, ou seja, mais trocas de contexto** (que são custo, não trabalho útil do programa).

Com os mesmos três processos:

| Quantum | Fatias de CPU | Espera média |
|---|---|---|
| 1 | 12 | 4,33 ms |
| 2 | 6 | 3,67 ms |
| 4 | 4 | 4,33 ms |
| 8 | 3 | 3,67 ms |

- **Quantum 1 gera 12 fatias** para o mesmo trabalho que o quantum 8 faz em 3.
- **A espera média não melhora só porque o quantum diminuiu.** Ela depende da combinação entre quantum, chegadas e bursts.
- **Com quantum 8, maior que qualquer burst, ninguém é interrompido:** a execução fica igual à do FCFS (P1 0–6, P2 6–8, P3 8–12).

→ Quantum muito pequeno = muitas trocas de contexto. Quantum muito grande = o Round Robin vira FCFS.


## Comparação das estratégias:

| Estratégia | Analogia | Quando funciona bem | Principal limitação |
|---|---|---|---|
| **FCFS** | Fila de banco: quem chegou antes é atendido primeiro | Processamento em lote simples | Um trabalho longo prende os curtos atrás dele |
| **Round Robin** | Roda de conversa: cada pessoa fala por um tempo fixo | Sistemas interativos, como desktops e servidores compartilhados | Quantum muito pequeno gera muitas trocas de contexto |
| **SJF** | Caixa rápido: atende primeiro quem tem poucos itens | Quando o tempo de CPU pode ser estimado | Processos longos podem esperar demais |
| **Prioridades** | Pronto-socorro: casos urgentes recebem atendimento primeiro | Quando algumas tarefas são mais importantes | Baixa prioridade pode sofrer starvation |

**SJF (Shortest Job First):** quando a CPU fica livre, escolhe o processo pronto com **menor burst**.

### Como decidir:

- **Simplicidade** → FCFS pode bastar.
- **Usuário precisa perceber resposta rápida** → Round Robin.
- **Reduzir a espera média** → SJF costuma ser melhor, quando as estimativas de burst são confiáveis.
