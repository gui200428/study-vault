## Comunicação digital: paralela e serial

Na comunicação digital, os dispositivos podem assumir dois papéis:
- **TX (Transmissor):** escreve os dados no barramento.
- **RX (Receptor):** lê os dados presentes no barramento.
A transmissão pode ocorrer de forma **paralela** ou **serial**.

### Comunicação paralela
Na comunicação paralela, **vários bits são transmitidos ao mesmo tempo**, utilizando condutores diferentes.

**Características:**
- transmite vários bits simultaneamente;
- apresenta maior velocidade;
- necessita de **mais condutores** para transportar os dados.

### Comunicação serial
Na comunicação serial, os bits são transmitidos **um após o outro**, em sequência.

**Características:**
- utiliza menos condutores;
- os bits são enviados sequencialmente;
- apresenta menor velocidade que a comunicação paralela.

Para comunicações na ordem de **kB/s e MB/s**, é defendido a implementação da comunicação serial.

![[Pasted image 20260927200851.png]]

### Protocolos e interfaces seriais
Existem diferentes protocolos e interfaces que utilizam comunicação serial.

![[Pasted image 20260927200852.png]]

## UART

A **UART (Universal Asynchronous Receiver Transmitter)** é uma forma simples de comunicação **serial entre dois dispositivos**, sem relação de hierarquia entre eles.

**A comunicação utiliza os sinais:**
- **TX (Transmit):** transmite os dados.
- **RX (Receive):** recebe os dados.


A ligação é cruzada:
**Dispositivo A        Dispositivo B**

    TX ─────────────► RX
    RX ◄───────────── TX



**Modos de comunicação:**

- **Simplex:** dados enviados em apenas uma direção.
- **Half-duplex:** dados enviados nas duas direções, mas **uma de cada vez**.
- **Full-duplex:** dados enviados nas duas direções **ao mesmo tempo**, utilizando linhas separadas de TX e RX.

#### Requisitos elétricos

Para que dois dispositivos se comuniquem corretamente:
- devem compartilhar a **mesma referência de GND**;
- devem utilizar **níveis lógicos compatíveis**.

Se os dispositivos trabalharem com tensões diferentes, deve ser utilizado um **conversor de nível lógico (transceiver)**.

![[Pasted image 20260930160548.png]]

### Comunicação assíncrona e quadro

A UART é uma comunicação **assíncrona**, ou seja, não existe uma linha de clock compartilhada entre TX e RX.

Cada dispositivo possui seu próprio clock e, por isso, ambos devem ser configurados com a **mesma taxa de transmissão**.

**Exemplos:**
- **9600 b/s**
- **15200 b/s**

O transmissor envia os dados sem confirmar diretamente se o receptor está realizando a leitura. Caso o receptor não processe os dados a tempo, as informações recebidas podem se acumular.

### Quadro UART
Como não existe um clock compartilhado, cada transmissão possui bits que ajudam o receptor a identificar o início e o fim dos dados.

Exemplo de envio de **10010011**:
- **Bit de início (start bit):** `0`
- **Bits de dados:** normalmente 8 bits.
- Os dados são tipicamente enviados do **LSB para o MSB**.
- **Bit de paridade:** utilizado para verificar a integridade dos dados.
- **Bit de término (stop bit):** `1`

![[Pasted image 20260927200853.png]]

Como o **LSB é transmitido primeiro**, a sequência enviada no barramento é: 

$$\boxed{0\ |\ 11001001\ |\ 1\ |\ 1}$$
**Onde:**
- `0` → **bit de início**
- `11001001` → **8 bits de dados**, enviados do LSB para o MSB
- `1` → **bit de paridade**, conforme o exemplo do slide
- `1` → **bit de término**

## I2C

O **I2C (Inter-Integrated Circuit)** é um protocolo de comunicação **serial síncrona**, utilizado principalmente em sistemas embarcados e comunicações de curta distância.

**Características:**
- utilizado em distâncias curtas, tipicamente **menores que 30 cm**;
- comunicação **síncrona**, pois os dispositivos compartilham um clock;
- comunicação **half-duplex**.

**Exemplos de dispositivos que utilizam I2C:**
- conversores **A/D e D/A**;
- relógios de tempo real (**RTC**);
- displays LCD.

### Barramentos SDA e SCL
O I2C utiliza apenas **duas linhas compartilhadas** entre os dispositivos:

- **SDA (Serial Data):** transporta os dados, endereços e bits de reconhecimento.
- **SCL (Serial Clock):** transporta o sinal de clock usado para sincronizar a comunicação. Clock comum controlado pelo **mestre.**

Vários dispositivos podem utilizar **os mesmos barramentos SDA e SCL**.


![[Pasted image 20260927200854.png]]

### Hierarquia mestre–escravos
A comunicação apresentada possui uma hierarquia de **mestre e escravos**.
- **Mestre:** inicia e controla a comunicação e o sinal de clock em SCL.
- **Escravos:** respondem quando são selecionados pelo endereço correspondente.
- O mestre pode **enviar ou receber dados** dos escravos.

No exemplo: um **ATmega328P** atua como mestre e compartilha SDA e SCL com:
- um RTC;
- um display LCD;
- outro ATmega328P.


![[Pasted image 20260927200855.png]]

### Requisitos elétricos e pull-up
As linhas **SDA e SCL** utilizam resistores **pull-up** ligados à alimentação.
Esses resistores mantêm as linhas em nível lógico alto quando nenhum dispositivo está puxando o barramento para nível baixo.

$$SDA,\ SCL \xrightarrow{\text{pull-up}} +5V$$

Os dispositivos devem trabalhar com **níveis elétricos compatíveis**.

### Funcionamento da comunicação
**Inicio:**
A comunicação começa quando:
- **SCL está em nível alto**;
- **SDA muda de 1 para 0**.

**Transmissão de um bit:**
Durante a transmissão:

- o valor do bit está presente em **SDA**;
- o receptor registra esse valor durante o pulso de **SCL**;
- enquanto SCL estiver alto, **SDA deve permanecer estável**.
**SDA transporta o dado e SCL determina quando esse dado deve ser lido.**


**Término**
A comunicação termina quando:
- **SCL está em nível alto**;
- **SDA muda de 0 para 1**.


No exemplo, a mensagem é **01101110**. O gráfico a apresenta temporalmente do **LSB para o MSB** como **01110110**.

![[Pasted image 20260930200911.png]]


### Estrutura de uma mensagem I2C

### Campos
- **Start:** indica o início da comunicação.
- **Endereço:** identifica qual dispositivo deve responder.
    - pode possuir **7 ou 10 bits**.
- **R/W (Read/Write):** define o sentido da comunicação.
- **Dados:** enviados em grupos de **8 bits**.
- **ACK/NACK:** informa se o dado foi reconhecido pelo receptor.
- **Stop:** encerra a comunicação.


![[Pasted image 20260927200857.png]]

### ACK e NACK

Após determinadas partes da transmissão, o receptor responde:

- **ACK (Acknowledge):** dado recebido/reconhecido.
- **NACK (Not Acknowledge):** não houve reconhecimento.

Assim, diferentemente da UART apresentada anteriormente, o I2C possui um mecanismo de **reconhecimento do recebimento**.

## SPI

O **SPI (Serial Peripheral Interface)** é um protocolo de comunicação **serial síncrona**, desenvolvido pela **Motorola em 1985**.

- utilizado em comunicações de curta distância, tipicamente **menores que 30 cm**;
- bastante usado em **sistemas embarcados**;
- comunicação **síncrona**, pois os dispositivos compartilham um clock;
- comunicação **full-duplex**, permitindo transmitir e receber dados simultaneamente.

**Exemplos:**
- sensores/leitores **RFID**;
- cartões **SD**;
- displays LCD.

### Barramentos do SPI

O SPI utiliza três linhas principais compartilhadas:
- **MOSI (Master Out Slave In):** leva dados do **mestre para o escravo**.
- **MISO (Master In Slave Out):** leva dados do **escravo para o mestre**.
- **SCLK (Serial Clock):** sinal de clock utilizado para sincronizar a comunicação.


![[Pasted image 20260930210832.png]]

A existência de uma linha para cada sentido permite que dados sejam enviados e recebidos **ao mesmo tempo**: **SPI = Full-duplex.**


![[Pasted image 20260927200858.png]]

### Seleção dos escravos — SS / CS
Além das três linhas principais, cada escravo possui uma linha de seleção:
- **SS (Slave Select)**;
- também chamada **CS (Chip Select)**.
MOSI, MISO e SCLK podem ser compartilhados entre vários dispositivos, mas o mestre utiliza uma linha **SS própria para selecionar qual escravo deve participar da comunicação**


![[Pasted image 20260927200859.png]]

Normalmente, o escravo é selecionado colocando sua linha SS em nível baixo:
$$\boxed{SS=0\Rightarrow\text{escravo selecionado}}$$
Tipicamente, utiliza-se resistores pull-up entre o os barramentos de comunicação e a alimentação para manter o nível lógico alto consistente.


### Funcionamento da comunicação

#### Início

A comunicação começa quando o mestre coloca o **SS do escravo escolhido em nível baixo**:

$$SS:1\rightarrow0$$

Isso seleciona o dispositivo que participará da transmissão.

Enquanto **SS permanece baixo**:

- o mestre envia dados pelo **MOSI**;
- o escravo envia dados pelo **MISO**;
- o **SCLK** sincroniza a leitura dos bits.

Assim, para cada pulso de clock, pode ocorrer simultaneamente:
Mestre ──MOSI──► Escravo
Mestre ◄─MISO─── Escravo
          ↑
       mesmo SCLK

**Full-duplex!**

#### Término

Ao terminar a comunicação, o mestre coloca SS novamente em nível alto:

$$SS:0\rightarrow1$$

A borda de subida de SS encerra a transmissão com aquele escravo.

### Estrutura da transmissão
Ao contrário do I2C apresentado anteriormente, o SPI **não precisa transmitir um endereço pelo barramento para selecionar o dispositivo**.

A seleção é feita diretamente pelas linhas **SS/CS**.

**O controle ocorre diretamente por:**

$$\boxed{SS + SCLK}$$

**Enquanto:**

$$\boxed{MOSI + MISO}$$

**transportam os dados.**



### Exemplo:

Durante **8 pulsos de SCLK**, com SS em nível baixo:

- o mestre envia `01101110` por **MOSI**;
- o escravo envia `00100011` por **MISO** simultaneamente.

![[Pasted image 20260927200900.png]]


## Suposições finais da aula

O último slide propõe estas comparações:

- **UART:** mais flexível nos modos (simplex, half-duplex e full-duplex), arquitetura mais simples e possibilidade de longas distâncias em comparação com I2C e SPI, geralmente restritos à placa de circuito impresso.
- **I2C:** half-duplex, porém mais rápido que UART e com maior integridade na entrega/recepção dos dados.
- **SPI:** full-duplex e mais rápido que I2C, ao custo de usar mais barramentos.




