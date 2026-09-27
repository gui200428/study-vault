# Suporte do Sistema Operacional - Escalonamento

## Processos e multiprogramação

Um **processo** é um programa em execução, ou a entidade à qual a CPU é atribuída para executar esse programa. O material usa processo como um termo mais amplo que *job*. Na multiprogramação, vários processos existem ao mesmo tempo e disputam o processador. Como mais de um pode estar **pronto** para executar, o sistema operacional precisa decidir quem recebe a CPU e por quanto tempo.

O esquema mostra a alternância entre processos: cada um mantém seu próprio ponto de execução, mas a CPU atende um de cada vez ao longo do tempo.

![[Pasted image 20260927171000.png]]

### Estados de um processo

O estado indica a condição do processo em um momento de sua vida. O diagrama da aula apresenta cinco estados e as passagens entre eles:

- **Novo → Pronto:** o processo é admitido no sistema.
- **Pronto → Executando:** recebe a CPU pelo despacho.
- **Executando → Pronto:** o tempo concedido se esgota.
- **Executando → Bloqueado:** precisa esperar um evento.
- **Bloqueado → Pronto:** o evento esperado ocorre.
- **Executando → Saída:** termina e é liberado.

![[Pasted image 20260927171001.png]]

### Bloco de controle de processo

O sistema operacional mantém um **bloco de controle de processo** para guardar o estado e os dados necessários para continuar sua execução. Ele normalmente contém:

- identificador exclusivo, estado atual e prioridade;
- contador de programa, com o endereço da próxima instrução;
- ponteiros que indicam a área ocupada na memória;
- dados de contexto dos registradores;
- requisições e dispositivos de entrada/saída (E/S), além dos arquivos associados;
- dados de contabilização, como tempo de CPU, tempo de clock, limites e número de conta.

Quando o processo deixa a CPU, o contador de programa e os dados de contexto são salvos. Quando volta a executar, são recuperados. Isso permite retomar a execução do ponto em que ela parou.

## O que é escalonamento

**Escalonamento** (*scheduling*) é a decisão do sistema operacional sobre a ordem de execução de processos ou *threads* (linhas de execução) e a distribuição do tempo de CPU. É o que intermedeia a disputa pelo processador na multiprogramação.

A política usada procura manter a interação com o usuário, dividir o processador de forma justa entre processos, threads e usuários, equilibrar a carga e evitar recursos ociosos. Os critérios de justiça e eficiência dependem do algoritmo escolhido.

A aula distingue quatro decisões:

| Tipo | O que decide |
| --- | --- |
| Longo prazo | Quais processos serão admitidos para execução. |
| Médio prazo | Quais processos serão mantidos na memória principal ou suspensos. |
| Curto prazo | Qual processo pronto usará a CPU agora. |
| E/S | Qual solicitação pendente será atendida por um dispositivo de E/S. |

## Escalonamento de longo prazo

Decide quais processos que aguardam na memória secundária serão **admitidos na memória principal** e colocados na fila de prontos. Assim, controla o **grau de multiprogramação**: a quantidade de processos ativos no sistema.

A seleção acontece antes da disputa direta pela CPU. Pode considerar tipo de processo (interativo ou *batch*), prioridade, tempo estimado de execução e política de uso dos recursos. Admitir processos demais sobrecarrega o sistema; controlar a entrada ajuda a equilibrar desempenho, uso de recursos e resposta às tarefas interativas.

Exemplo: se a interface precisa continuar fluida, o escalonador pode admitir uma tarefa interativa antes de um backup em lote.

### Exemplo de admissão

A aula apresenta cinco processos em espera e um limite de **três processos simultâneos** na fila de prontos:

| Processo | Tipo | Prioridade | Tempo estimado |
| --- | --- | --- | ---: |
| P1 | Interativo | Alta | 5 ms |
| P2 | Batch | Baixa | 30 ms |
| P3 | Interativo | Média | 10 ms |
| P4 | Batch | Média | 25 ms |
| P5 | Interativo | Alta | 8 ms |

A regra é priorizar processos **interativos** e, entre eles, os de **menor tempo estimado**. Portanto, a ordem de admissão é **P1 (5 ms) → P5 (8 ms) → P3 (10 ms)**. P2 e P4 ficam em espera. O limite impede admitir mais processos do que o sistema definiu para essa fila.

## Escalonamento de médio prazo

Gerencia a movimentação de processos entre a **RAM** e a memória secundária (*swap*). Pode suspender um processo pronto ou bloqueado que não precise executar imediatamente e reativá-lo quando houver recursos.

Isso libera memória para processos mais urgentes e reduz a carga do sistema. É útil quando há processos demais na RAM, quando algum está bloqueado por tempo indeterminado (por exemplo, esperando E/S) ou quando é preciso abrir espaço para outro de maior prioridade.

Também ajuda a evitar **thrashing**: a situação em que o sistema gasta mais tempo trocando processos entre memória e disco do que executando-os. No exemplo da aula, processos menos prioritários são suspensos e movidos para o disco para liberar memória às interações do usuário.

## Escalonamento de curto prazo

Escolhe **qual processo da fila de prontos executará na CPU**. Essa decisão acontece com frequência, por exemplo após interrupções, eventos de E/S e trocas de contexto, e afeta diretamente o tempo de resposta e de espera. A aula associa a execução dessa escolha ao *dispatcher* do sistema operacional.

Algoritmos citados: FIFO (*First-In, First-Out*), Round Robin, SJF (*Shortest Job First*), prioridade e filas multinível com realimentação. A escolha pode considerar tempo estimado de execução, prioridade, chegada e tempo de espera acumulado.

### Round Robin com quantum de 2 ms

Em **Round Robin**, cada processo recebe até um *quantum* de CPU. Se ainda não terminou após 2 ms, volta ao final da fila; novos processos também entram nessa fila. Essa alternância evita que um processo longo monopolize a CPU e favorece a resposta das tarefas interativas.

Dados do exercício:

| Processo | Chegada | Tempo de execução |
| --- | ---: | ---: |
| P1 | 0 ms | 5 ms |
| P2 | 1 ms | 3 ms |
| P3 | 2 ms | 8 ms |
| P4 | 3 ms | 6 ms |

Sequência de execução apresentada:

```text
0–2 P1 → 2–4 P2 → 4–6 P3 → 6–8 P1 → 8–10 P4 → 10–11 P2
→ 11–13 P3 → 13–14 P1 → 14–16 P4 → 16–18 P3 → 18–20 P4 → 20–22 P3
```

P1 termina em 14 ms, P2 em 11 ms, P3 em 22 ms e P4 em 20 ms. O **tempo de execução** (*burst time*) é o tempo de CPU necessário para concluir cada processo. Para calcular os tempos pedidos:

- **Tempo de retorno:** término − chegada.
- **Tempo de espera:** tempo de retorno − tempo de execução.

| Processo | Término | Retorno | Espera |
| --- | ---: | ---: | ---: |
| P1 | 14 ms | 14 − 0 = 14 ms | 14 − 5 = 9 ms |
| P2 | 11 ms | 11 − 1 = 10 ms | 10 − 3 = 7 ms |
| P3 | 22 ms | 22 − 2 = 20 ms | 20 − 8 = 12 ms |
| P4 | 20 ms | 20 − 3 = 17 ms | 17 − 6 = 11 ms |

**Tempo médio de espera:** (9 + 7 + 12 + 11) / 4 = **9,75 ms**.

**Tempo médio de retorno:** (14 + 10 + 20 + 17) / 4 = **15,25 ms**.
