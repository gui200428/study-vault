
## Diagrama funcional:

![[Pasted image 20260319175337.png]]

## BIU - (Bus Interface Unit) - “Lado externo da CPU”

### Funções principais:

### 1. Busca de instruções (Fetch):
**Definição:** Trabalho continuo da BIU de ler as próximas instruções do programa direto da memória e trazê-las para dentro do processador antes da **unidade de execução (EU)** precisar delas.
- Lê bytes de instrução da memória usando o CS:IP (Code segment + instruction pointer). **A BIU usa a combinação dos registradores CS (CODE SEGMENT) e IP (Instruction pointer) para saber exatamente qual é a próxima linha de código a ser lida.**
- Armazena os bytes na fila de pré-busca (Instruction queue) de 6 bytes. **Os bytes lidos não vão direto para a execução, eles ficam armazenados em uma pequena fila de espera de 6 bytes (no 8086). Isso cria um pipeline rudimentar, economizando tempo.**

### 2. Formação de endereços físicos:
**Definição:** Cálculo matemático que a BIU realiza nos bastidores para transformar um endereço lógico (Segmento : Deslocamento) trabalhado pelo programador em um endereço real e físico de 20 bits que a memória consiga entender.
- **Fórmula:** A BIU pega o valor do registrador de segmento, multiplica por 16 (ou desloca 4 bits para a esquerda) e soma com o valor do deslocamento (offset).  **( Deslocamento em endereço físico: Endereço Físico=Segmento×16 + Deslocamento. )**
- Usa os registradores de segmento: CS, DS, SS e ES.

### 3. Controle de barramento e temporização:
**Definição:** A BIU é a “porta-voz” do processador. É a única parte do chip que tem permissão e capacidade de se comunicar com a parte externa (RAM e periféricos de entrada/saída).
- **Sinais e Temporização:** Ela gera todos os sinais elétricos de controle que dizem à placa mãe se o processador quer ler ou escrever dados no momento. **(Gera sinais para memória e E/S (Ciclos de leitura/ escrita))**.
- **Execução de Pedidos:** quando a unidade de execução (EU) precisa de um dado para fazer uma conta, ela pede para a BIU. A BIU vai até a memória, busca a informação e entrega para a EU. **Coordena o acesso ao barramento (Endereços, dados e controle.)**

### 4. Leituras/escritas de dados:
**Definição:** Execução prática da movimentação de informações (buscar / salvar) na memória ou nos periféricos, trabalhando sob demanda para o processador.
- Executa os acessos de dados solicitados pela EU (por exemplo, ler um operando na memoria apontado por DS ou SS.) **Quando a EU precisa de um dado para uma conta, a BIU vai até a memória física, executa a leitura / escrita e entrega o resultado.**

### 5. Eventos especiais:
**Definição:** São situações imprevistas ou comandos específicos do programa que quebram a sincronia e interrompem o trabalho contínuo da fila de pré-busca da BIU.

- Desvios, chamadas, interrupções e mudanças de segmento → esvaziam a fila de pré-busca (flush). A BIU então reinicia a busca a partir do novo CS:IP. **Como o caminho do código mudou, as instruções que já estavam na fila não servem mais e são descartadas.**
 
- Se a EU consumir a fila mais rápido do que a BIU consegue encher (por exemplo, muitas instruções curtas), ocorre bolha/espera por fetch **A CPU fica ociosa (ocorre uma “bolha” no processamento) apenas esperando a BIU ir até a memória e trazer o próximo dado.**.


## EU (Execution Unit) - “Lado interno” da CPU

### Componentes e funções:

### 1. ALU e registradores gerais:
**Definição:** É a área de trabalho ativa da CPU, composto pelo “cérebro matemático” (ALU).

- **ALU:** executa operações aritméticas / lógicas. **A unidade lógica e aritmética** é uma calculadora do sistema, onde as somas, subtrações e operações comparativas (AND, OR) realmente acontecem na prática.

- **Regs gerais:** 
1. AX, BX, CX, DX;
2. índices/pilhas: SI, DI, BP, SP; 
3. Flags (CF, ZF, SF, OF, PF, AF, IF, DF, TF).
**Esses registradores são usados pela EU para guardar temporariamente os dados durante as contas. Já o registrador de Flags indica o status do último cálculo.**

### 2. Decodificação e execução:
**Definição:** É o processo de traduzir a linguagem de máquina (bytes puros) para uma ação compreensível pelo processador, e então realizá-la.

- **Decodifica bytes da fila de instruções (vindos da BIU).** A EU pega a próxima instrução que estava guardada na fila de espera da BIU e a “lê”, descobrindo qual é o comando exato que o programa mandou fazer.

- **Executa a instrução (opera na ALU, atualiza registradores e Flags).** Após entender o comando, ela começa a trabalhar: ativa a ALU para calcular, move os dados entre os registradores e atualiza os sinalizadores de status.

### 3. Cálculo de endereços efetivos (EA - Effective Address):
**Definição:** é a matemática preparatória que a EU faz para descobrir a distância exata (deslocamento/offset) em que um dado se encontra dentro de um segmento de memória.

**A EU calcula o deslocamento a partir do modo de endereçamento (Ex: BX+ SI + disp).** Ela resolva as equações dos modos avançados de endereçamento para descobrir o valor final do deslocamento antes de pedir o dados para o lado de fora.

**Em seguida, solicita à BIU a formação do endereço físico (segmento << 4 + deslocamento) e o acesso à memória, quando necessário.** Como a EU é “cega” para a parte externa, ela entrega esse valor de deslocamento resolvido para a BIU com a mensagem: “Some isso ao registrador de segmento, encontre o endereço físico final de 20 bits e me traga o que está lá”.


### 4. Controle de fluxo:
**Definição:** é o poder da EU de decidir qual caminho o programa vai seguir, controlando qual será a próxima instrução a ser lida.

- **Atualiza IP (próxima instrução) ou solicita salto/chamada/retorno, o que causa flush da fila na BIU.** Se o código seguir reto, ela apenas manda o IP avançar. Mas se o código mandar “pular” para outra parte do programa, a EU avisa a BIU para mudar o IP drasticamente, forçando a BIU a jogar fora as instruções lidas previamente (o flush) e começar a buscar no novo endereço.


