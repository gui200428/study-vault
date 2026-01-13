#faculdade #aom #resumos 
## Definição de computador:

→ Conjunto integrado de hardware, software e dispositivos periféricos. Projetados para funcionar em conjunto e executar tarefas computacionais.

**Principais elementos do hardware:**
- CPU - unidade central de processamento
- RAM - Memória de dados
- ROM - Memória de programa
- SDD / HDD - Dispositivos de armazenamento
- Dispositivos de entrada e saída

**Principais elementos do software:**
- SO - sistema operacional
- Firmware- controle de baixo nível do hardware


## Organização X Arquitetura

**Organização:**
- Modo como o hardware é implementado
- Relacionado aos aspectos relativos dos componentes físicos do computador. (Ex: Tecnologia das memórias, interface e construção dos dispositivos).
- “Pouco importante ao programador”

**Arquitetura:**
- Relacionada aos componentes implementados
- Tamanho da memoria e barramento
- Conjunto de instruções e registradores
- Modos de endereçamento
- Número de bits para representação de um dado
- “Muito importante ao programador”

**Exemplo**

→ É uma questão de projeto da arquitetura do computador se existe ou não instrução de
multiplicação.

→ No entanto, é uma questão de organização do computador se essa instrução é realizada
por um circuito multiplicador ou por múltiplas adições em um circuito somador.

## Modelo de Von Neumann

![[Pasted image 20250928164859.png]]

→ “O programa que direciona as atividades da CPU é armazenado na mesma memória em que
estão os dados, que devem ser manipulados pelo programa”

→ O computador é uma máquina de programas armazenados e sequencialmente executados

**Ciclo da maquina:**
→ Processo que a CPU executa para completar uma instrução
→ Envolve a busca, decodificação e execução de operações.
→ A eficiência do processador é medida pela quantidade de ciclos de maquina necessários para executar diferentes instruções
→ Busca <-> Execução


## Elementos de um computador


### Memória:

**Memoria de Programa - ROM**
→ Somente leitura/não-volátil
→ Instruções

**Memória de Dados - RAM**
→ Escrita e leitura/volátil
→ Dados temporários

**Memória Secundária (Externa)**
→ Escrita e leitura /não-volátil
→ Armazenamento de grande volume de dados
Ex: SSD, HDD.

### Barramentos:

→ Canal de comunicação entre o microprocessador e os periféricos e memórias.
→ Todos os periféricos e memória compartilham o mesmo canal de comunicação
→ O tamanho do barramento determina quantos bits podem ser transmitidos por vez (Ex: barramento de 16 bits, 32 bits… etc.)
→ Comnica-se apenas com um por vez

**Tipos:**

**Barramento de dados**
**Barramento de endereçamento**
**Barramento de controle**

### CPU / Microprocessador

**Componentes:**

**ULA** - Realiza as operações aritméticas (adição, subtração…) e operações lógicas (E, OU…)

**Unidade de controle** - Responsável por gerar sinais necessários de controle e temporização (**CLK**) para todas as operações de controle do fluxo de dados entre o microprocessador (uP), memorias e periféricos. Controla o acesso aos barramentos. Controla o fluxo de dados.

**Conjunto de registradores** - Permitem o armazenamento de valores temporários, intermediários ou informações de comando.

**Função:**
→ Dispositivo de lógica programável usado para:
- Controlar processor
- Ligar/desligar dispositivos
→ Execução é sequencia;: apenas uma instrução por vez
→ Cada microprocessador tem seu conjunto de instruções

**Clock:**
- Gera sinais de sincronismo interno
- Permite a sequencia ordenada de eventos
- Um ciclo de máquina tem duração de vários períodos de CLK

#### Diferença entre registradores e a memória RAM

→ Um registrador armazena um número limitado de bits
→ Registrador é interno a CPU e realizam funções específicas. 
→ A memória RAM é externa a CPU e é usada para armazenar dados temporários.

**Nos microprocessadores os registradores são internos à CPU, e nos microcontroladores parte deles podem estar mapeados em memória RAM, dedicada a esses registradores.**

---
## Microprocessador X Microcontrolador

### Microprocessador (uP): 
→ Dispositivo lógico programável compactado em um único chip de silício
→ Tem a capacidade de executar operações lógicas, e de controle.
→ Precisam ser interligados com memória do tipo ROM e RAM. Alem dos outros dispositivos.
### Microcontroladores (uC):
→ Circuito integrado (CI) que possui internamente um microprocessador e todos os periféricos
 essenciais ao seu funcionamento.
 - Memoria de programa ROM
 - Memoria de dados
 - Dispositivos de entrada e saída
 - Temporizadores
 - Comunicação serial

---

## PLD x Microprocessador

### PLD (Programmable Logic Device)
→ Dispositivo de hardware digital que pode ser programado para realizar funções lógicas.
→ Programado por linguagens de descrição de hardware como VHDL ou Verilog
### Microprocessador (μP)
→ Unidade de processamento central de um sistema de computador, responsável por
executar instruções de um programa
→ Programado usando linguagens de programação como Assembly, C, ou C++


---

### Próximo conteúdo:

[[003 - Barramentos]]
