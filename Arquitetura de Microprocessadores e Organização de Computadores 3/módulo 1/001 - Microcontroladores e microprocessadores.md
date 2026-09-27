# Microcontroladores e microprocessadores

## O que compõe um computador

Um computador reúne hardware, software e periféricos para executar tarefas. Pode ser usado para uma função específica, como em sistemas embarcados com microcontrolador (µC), ou para tarefas gerais, como em sistemas com sistema operacional e microprocessador (µP).

- **Hardware:** CPU, memórias RAM e ROM, armazenamento (HDD, SSD, cartão SD) e dispositivos de entrada e saída, como teclado, monitor, mouse, botões e LEDs.
- **Software:** sistema operacional (SO) e firmware, que controla o hardware em baixo nível.

Na placa-mãe ficam as conexões para o processador, a memória, o armazenamento e os periféricos. As placas SBC (*Single Board Computer*) mostradas na aula reúnem esses recursos em uma placa menor.

![[Pasted image 20260927163911.png]]

## Organização e arquitetura

**Organização:** como os recursos de hardware são implementados fisicamente. Inclui a tecnologia das memórias, as interconexões, as interfaces e a construção dos dispositivos. Em geral, é pouco visível para quem programa.

**Arquitetura:** características implementadas que o programador pode usar ou precisa considerar, como conjunto de instruções, registradores, modos de endereçamento, tamanho das memórias e barramentos e quantidade de bits usada para representar dados.

Exemplo: existir uma instrução de multiplicação é uma decisão de **arquitetura**. Realizá-la com um circuito multiplicador ou com várias adições em um somador é uma decisão de **organização**.

Na classificação feita em aula:

- **Arquitetura:** 32 registradores de uso geral visíveis ao programador; instruções de multiplicação e divisão; barramento de dados de 64 bits; endereçamento indireto e indexado.
- **Organização:** cache implementada em SRAM; mudança de 5 para 10 estágios internos de pipeline sem alterar as instruções; três barramentos físicos separados para dados, endereços e controle; aumento da cache L1 de 32 KB para 64 KB.

## Modelo de Von Neumann

O programa que orienta a CPU fica armazenado na mesma memória que os dados manipulados por ele. É o modelo de **programa armazenado**: a CPU busca instruções na memória e as executa sequencialmente.

No esquema, a CPU contém ULA, registradores e unidade de controle. Ela se comunica com memórias e dispositivos de entrada/saída pelos barramentos.

![[Pasted image 20260927163910.png]]

### Ciclo de máquina

É o processo básico para completar uma instrução: **buscar** a instrução, **decodificá-la** e **executá-la**. A quantidade de ciclos necessária para executar instruções é uma das formas de avaliar a velocidade do processador.

## Memórias e barramentos

### Tipos de memória

- **Memória de programa (tipo ROM):** não volátil e apresentada na aula como memória de leitura para instruções e dados que precisam permanecer armazenados. Exemplos: PROM, EEPROM e Flash ROM.
- **Memória de dados (tipo RAM):** permite leitura e escrita; é volátil e guarda dados temporários. Exemplos citados: DRAM, SRAM e cache.
- **Memória secundária (externa):** permite leitura e escrita e guarda grande volume de dados de forma não volátil. Exemplos: HDD, SSD, CD, microSD e pen drive.

### Barramentos

São os canais de comunicação entre o µP, as memórias e os periféricos. Os dispositivos compartilham esses canais, e o µP se comunica com um deles por vez. A largura de um barramento indica quantos bits podem ser transmitidos de uma vez, como 16 ou 32 bits.

O barramento é dividido em três partes:

- **Dados:** transporta os dados.
- **Endereços:** indica a posição ou o dispositivo acessado.
- **Controle:** transporta os sinais que coordenam o acesso.

![[Pasted image 20260927163912.png]]

## CPU e microprocessador

A CPU é a unidade que executa as instruções do programa e pode controlar processos ou ligar e desligar dispositivos. Seus três componentes principais são **ULA, conjunto de registradores e unidade de controle (UC)**. Quando a CPU é encapsulada em um chip, temos um microprocessador (µP).

O µP trabalha com valores binários (0 e 1) e executa instruções representadas em linguagem de máquina. Cada modelo possui seu próprio conjunto de instruções. Nos exemplos de memória de programa da aula, essas instruções ficam armazenadas em ROM. A execução é apresentada como uma sequência de instruções, uma por vez.

### Clock (CLK)

O clock fornece sinais de sincronismo para ordenar os eventos internos da CPU. A unidade de controle coordena as operações nesse ritmo. Um ciclo de máquina pode ocupar diferentes quantidades de períodos de clock, conforme o processador.

A comparação apresentada na aula é: 8051, 12 pulsos; PIC, 4; AVR (Arduino) e STM32, 1; Intel Core i9, menos de 1 pulso por ciclo de máquina. No diagrama, os pulsos do clock acompanham a sequência binária do sinal A.

![[Pasted image 20260927163913.png]]

### ULA (Unidade Lógica e Aritmética)

A ULA, ou ALU (*Arithmetic Logic Unit*), executa operações aritméticas, como soma, subtração, multiplicação e divisão, e operações lógicas, como AND, OR, NAND, NOR e XOR. Os **flags** são bits que sinalizam resultados dessas operações.

### UC (Unidade de Controle)

A UC controla e temporiza as operações do µP. Ela lê o **opcode** no registrador de instruções (IR), decodifica o comando e gera os sinais necessários para executá-lo. Também controla o acesso aos barramentos e a direção do fluxo de dados.

### Registradores

São áreas pequenas e rápidas, normalmente internas à CPU, que guardam valores temporários, resultados intermediários ou informações de controle. Cada registrador tem uma função:

- **GPR (*General Purpose Registers*):** uso geral, principalmente para dados temporários.
- **SFR (*Special Function Registers*):** funções especiais de controle do dispositivo.

A aula mostra como exemplos o contador de programa (PC), o registrador de instrução (RI), o ponteiro de dados acumulador (DPTRA), o temporizador (TMR) e o ponteiro de pilha (SP).

Um registrador armazena poucos bits, geralmente uma palavra, e tem acesso rápido dentro da CPU. A RAM guarda dados temporários em uma área de memória mais ampla, normalmente externa à CPU. Em alguns microcontroladores, os SFR podem ficar mapeados na RAM junto aos GPR.

## Microprocessador e microcontrolador

### Microprocessador (µP)

É uma CPU programável em um único chip, capaz de realizar operações lógicas, aritméticas e de controle. Para funcionar em um sistema, precisa ser interligado a memórias de programa e dados (ROM e RAM) e a dispositivos de entrada e saída.

O Intel 4004, de 4 bits, foi apresentado como o primeiro chip com uma CPU completa: lançado em 1971, tinha 2.300 transistores. A aula compara esse número com cerca de 700 milhões de transistores em um Intel Core i7 Quad.

### Microcontrolador (µC)

Reúne em um único chip um microprocessador, memórias, barramentos, interfaces e dispositivos de entrada e saída. Assim, já incorpora os recursos essenciais para controlar um sistema específico.

Entre os recursos internos apresentados estão:

- memória de programa, geralmente ROM, e memória de dados, geralmente RAM;
- seleção de entrada e saída e temporizadores;
- conversores A/D e D/A;
- lógica de interrupções e comunicação serial.

→ O µP precisa se conectar a memórias e E/S para funcionar como sistema; no µC, esses recursos já estão integrados ao chip.

## PLD e microprocessador

Um **PLD (*Programmable Logic Device*)** é um dispositivo digital programável para implementar funções lógicas específicas. FPGA e CPLD são exemplos. Ele possui blocos lógicos e interconexões configuráveis, podendo incluir memória.

O PLD é usado para criar lógica de hardware personalizada, como controle de sinais e processamento paralelo. Não segue uma arquitetura fixa: sua configuração pode ser alterada para outras aplicações, o que ajuda na prototipagem. Essa lógica é descrita em linguagens de hardware, como VHDL ou Verilog.

O **µP**, por sua vez, tem uma arquitetura definida, como x86 ou ARM, com ULA, registradores e unidade de controle. Ele executa sequencialmente instruções de software para operações aritméticas, controle de fluxo e gerenciamento de memória. Pode ser programado em Assembly, C ou C++. Sua flexibilidade está em mudar o programa executado dentro da arquitetura do processador.

![[Pasted image 20260927163914.png]]

## VHDL e Assembly

**VHDL (*VHSIC Hardware Description Language*)** descreve e permite simular o comportamento e a estrutura de circuitos digitais em PLDs: portas lógicas, flip-flops, registradores e suas conexões. Trabalha em um nível de abstração mais alto para o projeto de hardware e exige compreender como o circuito é construído e funciona.

**Assembly** é uma linguagem de programação de baixo nível, próxima ao código de máquina e específica de uma arquitetura, como x86 ou ARM. Suas instruções definem uma sequência de operações para o processador, incluindo acesso a registradores e memória. A sintaxe é simples, mas é necessário conhecer a arquitetura e o efeito de cada instrução.

No exemplo de circuito da aula, um decodificador 3 × 8 recebe três entradas (A, B e C) e possui oito saídas (D0 a D7). As combinações das entradas determinam qual saída é ativada.

![[Pasted image 20260927163915.png]]

O exemplo de código mostra essa diferença de enfoque: em VHDL, as entradas e saídas e o comportamento do circuito são descritos; em Assembly, aparece uma sequência de instruções que o processador executa.

![[Pasted image 20260927163916.png]]
