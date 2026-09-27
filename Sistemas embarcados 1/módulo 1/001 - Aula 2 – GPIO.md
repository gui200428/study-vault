## Sistema embarcado e microcontrolador

Um **sistema embarcado** reúne hardware e software para executar uma função específica. A aula apresenta o **microcontrolador** como parte de todo sistema embarcado: é um circuito integrado complexo que opera de forma semelhante a um computador.

Alguns microcontroladores ficam em uma **plataforma de prototipagem**, placa que também contém recursos como reguladores, conectores e osciladores. O Arduino é um exemplo de plataforma; **a placa Arduino não é o microcontrolador**. No Arduino Uno mostrado, o microcontrolador é o ATmega328P. A figura também identifica os conectores, a chave de RESET, o regulador de +5 V, o oscilador/temporizador e a alimentação.

![[Pasted image 20260927191536.png]]

Exemplos de microcontroladores citados na aula:

- STM32 (STMicroelectronics);
- ESP8266 (Expressif Systems);
- ATmega328P (Atmel).

Nos exemplos visuais, o ESP8266 está em uma plataforma de prototipagem dentro de um sistema embarcado; o STM32 aparece em outro sistema embarcado sem estar montado em uma plataforma de prototipagem.

![[Pasted image 20260927191537.png]]

## Organização do microcontrolador

A aula usa a arquitetura **Von Neuman** para dividir um computador ou microcontrolador em três componentes principais:

- unidade de processamento + Unidade Lógica Aritmética (ULA);
- memória;
- dispositivos de entrada e saída.

No esquema, sinais dos dispositivos de entrada chegam ao microcontrolador e sinais de saída seguem para os dispositivos de saída. A aula apresenta os **registradores** como blocos da memória principal que contêm ou recebem informações, acessados diretamente pelos dispositivos de entrada e saída.

![[Pasted image 20260927191538.png]]

## GPIO e níveis lógicos

**GPIO** (*General Purpose In Out*) são portas de entrada e saída para uso geral. Elas recebem sinais de sensores (**entradas**) e enviam sinais para atuadores (**saídas**). A interligação do microcontrolador aos periféricos define o hardware de um sistema embarcado.

No exemplo visual, um sensor de luz envia sinal ao microcontrolador; há ligações dele com um monitor, um display LCD e um circuito de saída que aciona um LED.

![[Pasted image 20260927191539.png]]

Sinais elétricos são tipicamente representados por níveis de tensão. Para a **maioria** dos sistemas embarcados:

- **Nível lógico baixo (0):** GND, ou tensão de referência de 0 V.
- **Nível lógico alto (1):** tensão padrão dependente da aplicação, como +3,3 V, +5 V ou +12 V.

O microcontrolador envia e recebe sinais digitais pelas **portas digitais**.

## Leitura e escrita nas portas digitais

A direção do sinal é considerada em relação ao dispositivo de referência, aqui o microcontrolador: sinal que **entra** corresponde a uma **leitura**; sinal que **sai** corresponde a uma **escrita**.

### Leitura: estado da chave

Obs: o slide identifica este trecho como “Acionar um LED a partir de um microcontrolador”, porém o circuito e a explicação apresentados são referentes à leitura do estado de uma chave.

No circuito mostrado, a porta digital recebe o sinal do ponto entre um resistor ligado a +Vcc e uma chave ligada ao GND:

- **+5 V na entrada:** chave recuada.
- **GND na entrada:** chave pressionada.

Assim, o microcontrolador faz a **leitura do estado da chave**.

![[Pasted image 20260927191540.png]]

### Escrita: acionamento do LED

No circuito mostrado, o LED e o resistor estão ligados entre +Vcc e a saída digital do microcontrolador:

- **+5 V na saída:** LED apagado.
- **GND na saída:** LED aceso.

Assim, o microcontrolador faz uma **escrita sobre o LED**. Quando escreve GND, a corrente que aciona o LED **entra no microcontrolador**. O sentido do sinal de saída indicado no esquema não é o sentido da corrente.

![[Pasted image 20260927191541.png]]

## Registradores de GPIO do ATmega328P

O ATmega328P possui três grupos de GPIO: **B, C e D**. Para cada grupo, a aula apresenta três tipos de registrador:

- **DDRx (*Data Direction Register*):** define se a porta será de entrada ou saída; controla a porta *tri-state*.
- **PORTx:** controla os níveis lógicos alto e baixo usados nas escritas.
- **PINx:** recebe os níveis lógicos lidos nas entradas.

A tabela do material associa cada registrador aos seus bits, do bit 7 ao bit 0, e mostra dois endereços para cada um:

| Grupo | Leitura | Direção | Escrita |
|---|---|---|---|
| B | PINB: 0x03 (0x23) | DDRB: 0x04 (0x24) | PORTB: 0x05 (0x25) |
| C | PINC: 0x06 (0x26) | DDRC: 0x07 (0x27) | PORTC: 0x08 (0x28) |
| D | PIND: 0x09 (0x29) | DDRD: 0x0A (0x2A) | PORTD: 0x0B (0x2B) |

![[Pasted image 20260927191542.png]]

Na pinagem apresentada para o Arduino Uno, as portas digitais **0 a 7** correspondem a **PD0 a PD7** e as **8 a 13** correspondem a **PB0 a PB5**. As entradas **A0 a A5** aparecem associadas a **PC0 a PC5**.

Exemplos da aula:

- **DDRD (0x2A):** define se as portas dos pinos 0 a 7 serão de entrada ou saída.
- **PINB (0x23):** recebe os bits das portas 8 a 13 quando elas realizam leitura.

O desenho também mostra os nomes das portas, os números dos pinos e suas funções indicadas na placa.

![[Pasted image 20260927191543.png]]
