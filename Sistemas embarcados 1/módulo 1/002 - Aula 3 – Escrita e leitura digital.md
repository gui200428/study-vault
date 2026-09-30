## Níveis lógicos em circuitos discretos

Em circuitos discretos, diferentes circuitos podem fazer escrita e leitura digital comunicando-se por um **nível lógico no barramento**. Tipicamente:

- **Nível baixo (0):** GND.
- **Nível alto (1):** tensão definida pela aplicação, como +3,3 V, +5 V ou +12 V.

## Escrita digital

A aula apresenta dois circuitos para realizar escritas digitais: **coletor aberto** e **totem-pole**.

### 1- Coletor aberto

O circuito de coletor aberto tem lógica inversora. No esquema, a entrada **E** chega à base do transistor NPN **Q1** pelo resistor **R1**, e a saída **S** está no coletor. Quando Q1 satura, a saída pode gerar nível lógico **baixo (0)**. Quando Q1 está em corte, a saída fica em **alta impedância (Z)**: o circuito não gera corrente para produzir nível alto. Esse estado Z também será usado em leituras digitais.

**No circuito:**
- **E** = entrada digital.
- **R1** = limita a corrente que entra na base do transistor.
- **Q1** = transistor NPN funcionando como chave.
- **S** = saída, ligada ao coletor.
- **R2** = resistor de **pull-up**, que “puxa” S para +Vcc quando Q1 está desligado.


**Sem o pull-up externo:**

Quando Q1 está desligado:
- A saída fica “solta”, não força a saída nem para nível baixo nem para nível alto.
- Ela está em um terceiro estado denominado de **alta impedância (Z)**

![[Pasted image 20260927194557.png]]

Para obter nível alto, é acrescentado um resistor **pull-up externo (R2)** entre a saída S e **+Vcc**. Assim, o pull-up fornece o nível alto quando Q1 está em corte;

![[Pasted image 20260927194558.png]]

**Vantagens para essa topologia:**

- flexibilidade na escolha da tensão de nível lógico alto;
- maior capacidade de fornecer corrente.


#### Estudando os casos de funcionamento:

**Quando E = 0**
Não existe corrente suficiente na base para ligar o Q1.
- **Q1:** está em corte (desligado), transistor se comporta como uma chave aberta
- Q1 não está puxando a saída para o GND.
- O resistor R2 (pull-up) puxa a saída S para +Vcc.

$$E=0 \Rightarrow S=1$$
**Quando E = 1**
- Corrente passa por R1 e entra na base de Q1.
- Q1 entra em condução e, com corrente de base suficiente, satura.
- O transistor se comporta como uma chave fechada para GND
- A saída S é puxada para o nível lógico baixo.

$$E=1 \Rightarrow S=0$$
**Com o resistor de pull-up, o circuito se torna uma porta NOT!**

$$S=\overline E$$
**O transistor consegue puxar a saída para 0, mas não consegue empurrá-la para 1. Quando ele desliga, apenas “solta” a saída; quem produz o nível alto é o pull-up.**

### 2- Totem-pole

Esta topologia vem para resolver o grande problema do coletor aberto: a necessidade de um pull-up externo para empurrar a saída para +Vcc.

É colocado dois transistores na saída. Este empilhamento lembra um totem.

O sinal **E**, proveniente do microcontrolador/registrador, e a saída **S** seguem uma lógica inversora:

**Q4 empurra a saída para HIGH e Q3 puxa a saída para LOW.**

- **E = 1:** o **Q3 satura** e **Q4 entra em corte** → **S = 0**.
- **E = 0:** **Q3 entra em corte** e **Q4 satura** → **S = 1**.


![[Pasted image 20260927194559.png]]

**Vantagens para essa topologia:**
- pode trabalhar em altas frequências;
- não necessita de resistor pull-up externo para gerar o nível alto

#### Estudando os casos de funcionamento:

**E=1**
- Q3 satura → Q4 corta
- Q3 vira aproximadamente uma chave fechada para o terra.
- S = 0V

$$\boxed{E=1\Rightarrow S=0}$$

**E=0**
- Q3 corta → Q4 conduz.
- Q3 não está puxando a saída para o terra.
- **Q4** leva a saída para o nível lógico alto a partir de +Vcc

$$\boxed{E=0\Rightarrow S=1}$$

HIGH → Q4 empurra S para cima
LOW  → Q3 puxa S para baixo

**Não necessita de um pull-up externo para obter o nível lógico alto.**
## Leitura digital

### Porta tri-state e barramento

Uma porta tri-state possui 3 estados possíveis:

$$\boxed{0,\ 1,\ Z}$$

- **Z:** é o estado de alta impedância.
- Quando a saída está em Z, o circuito não força o pino nem para nível alto nem para nível baixo.

A porta tri-state possui o pino de ENABLE, este pino serve para colocar a saída em um estado de alta impedância se estiver em 0, ou permitir que A controle a tensão no pino B.

#### Casos:
**Enable = 1:** 
- a saída **B** acompanha **A** (0 ou 1).
$$\boxed{B=A}$$
**Enable = 0:**
- a saída **B = Z**, independentemente da entrada A.

$$\boxed{B=Z}$$


- **O estado Z permite que o microcontrolador realize leituras, pois o estágio de saída deixa de controlar o pino e o circuito externo pode impor o nível lógico presente nele.**

Em microcontroladores de arquitetura mais simples, como o **ATmega328P**, a escrita e a leitura digital são controladas por uma **porta tri-state**. A tabela mostra que:


![[Pasted image 20260927194600.png]]

Em **alta impedância (Z)**, o microcontrolador não impõe nível lógico ao barramento. Esse estado é usado durante a **leitura digital**, pois permite que um sinal externo determine a tensão no pino. Na **comunicação digital entre dispositivos**, um dispositivo pode colocar 0 ou 1 no barramento, enquanto os demais mantêm suas saídas em Z, evitando interferência e permitindo a leitura do sinal.


![[Pasted image 20260927194601.png]]

**Z não é um valor lido pelo microcontrolador; é o estado em que sua saída deixa de interferir no pino.**
### Schmitt-Trigger

O **Schmitt-Trigger** ajuda a evitar leituras incorretas causadas por **ruído** e pela **região de indeterminação** do sinal.

**Possui dois limiares:**
- $V_{T+}$ ← usado quando a tensão está subindo
- $V_{T-}$ ← usado quando a tensão está descendo

O estado lógico só muda quando a tensão cruza um desses limiares:

$$V_{in}>V_{T+} \Rightarrow S=1$$

$$V_{in}<V_{T-} \Rightarrow S=0$$


#### **E se estiver no meio dos dois?**

$$V_{T-}<V_{in}<V_{T+}$$

É necessário saber **de onde o sinal veio.**
- **Se está subindo e ainda não passou do $V_{T+}$**: **S=0**
- **Se está descendo e ainda não passou do $V_{T-}$**: **S=1**
Essa dependência do histórico do sinal é chamada de **histerese**.

Na figura, uma entrada de tensão variável (vermelho) produz uma saída digital (azul), que muda de estado em pontos diferentes durante a subida e a descida.

![[Pasted image 20260927194602.png]]

**Histerese = a saída depende não só da tensão atual, mas também do caminho anterior do sinal.**
## Arquitetura das portas digitais do ATmega328P

O esquema da aula liga o pino **Pxn** aos bits **DDxn, PORTxn e PINxn** e ao barramento de dados. O registrador **DDRx controla a porta tri-state**, conforme destacado no material. No caminho de leitura, a figura mostra uma porta Schmitt-Trigger e um sincronizador antes de **PINxn**.

![[Pasted image 20260927194603.png]]
