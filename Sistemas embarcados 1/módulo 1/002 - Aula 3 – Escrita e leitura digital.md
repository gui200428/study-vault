# Aula 3 – Escrita e leitura digital

## Níveis lógicos em circuitos discretos

Em circuitos discretos, diferentes circuitos podem fazer escrita e leitura digital comunicando-se por um **nível lógico no barramento**. Tipicamente:

- **Nível baixo (0):** GND.
- **Nível alto (1):** tensão definida pela aplicação, como +3,3 V, +5 V ou +12 V.

## Escrita digital

A aula apresenta dois circuitos para realizar escritas digitais: **coletor aberto** e **totem-pole**.

### Coletor aberto

O circuito de coletor aberto tem lógica inversora. No esquema, a entrada **E** chega à base do transistor NPN **Q1** pelo resistor **R1**, e a saída **S** está no coletor. Quando Q1 satura, a saída pode gerar nível lógico **baixo (0)**. Quando Q1 está em corte, a saída fica em **alta impedância (Z)**: o circuito não gera corrente para produzir nível alto. Esse estado Z também será usado em leituras digitais.

![[Pasted image 20260927194557.png]]

Para obter nível alto, o material acrescenta um resistor **pull-up externo (R2)** entre a saída S e **+Vcc**. Assim, o pull-up fornece o nível alto quando Q1 está em corte; com Q1 saturado, a saída continua em nível baixo.

![[Pasted image 20260927194558.png]]

Vantagens apresentadas para essa topologia:

- flexibilidade na escolha da tensão de nível lógico alto;
- maior capacidade de fornecer corrente.

### Totem-pole

Nessa topologia, o sinal **E**, proveniente do microcontrolador/registrador, e a saída **S** seguem uma lógica inversora:

- **E = 1:** o BJT **Q3 satura** e **Q4 entra em corte** → **S = 0**.
- **E = 0:** **Q3 entra em corte** e **Q4 satura** → **S = 1**.

O nome vem da coluna do circuito que lembra um totem, destacada na figura.

![[Pasted image 20260927194559.png]]

Vantagens apresentadas:

- pode trabalhar em altas frequências;
- não necessita de fonte externa.

## Leitura digital

### Porta tri-state e barramento

Em microcontroladores de arquitetura mais simples, como o **ATmega328P**, a escrita e a leitura digital são controladas por uma **porta tri-state**. A tabela da aula mostra que:

- **Enable = 0:** a saída **B = Z**, independentemente da entrada A.
- **Enable = 1:** a saída **B** acompanha **A** (0 ou 1).

![[Pasted image 20260927194600.png]]

Em **alta impedância (Z)**, o microcontrolador não impõe tensão ao barramento. É esse o estado usado para efetuar a **leitura digital**. No exemplo de comunicação, um microcontrolador coloca 0 ou 1 no barramento, enquanto os outros dispositivos aparecem em Z e podem receber esse sinal.

![[Pasted image 20260927194601.png]]

### Schmitt-Trigger

Outra técnica de leitura digital usa uma porta **Schmitt-Trigger** para evitar a região de indeterminação da leitura. Ela apresenta **histerese**: o nível lógico lido depende do caminho da tensão no barramento, ou seja, se a tensão está subindo ou descendo. Por isso, a **tensão de gatilho de 0 → 1 é diferente da de 1 → 0**.

Na figura, uma entrada de tensão variável (vermelho) produz uma saída digital (azul), que muda de estado em pontos diferentes na subida e na descida.

![[Pasted image 20260927194602.png]]

## Arquitetura das portas digitais do ATmega328P

O esquema da aula liga o pino **Pxn** aos bits **DDxn, PORTxn e PINxn** e ao barramento de dados. O registrador **DDRx controla a porta tri-state**, conforme destacado no material. No caminho de leitura, a figura mostra uma porta Schmitt-Trigger e um sincronizador antes de **PINxn**.

![[Pasted image 20260927194603.png]]
