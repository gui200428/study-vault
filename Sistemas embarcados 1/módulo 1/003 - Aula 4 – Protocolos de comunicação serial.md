## Comunicação digital: paralela e serial

Na comunicação digital, um dispositivo **escreve** no barramento como transmissor (**TX**) e outro **lê** como receptor (**RX**). Na comunicação **paralela**, vários bits são transmitidos ao mesmo tempo por condutores diferentes. Na **serial**, os bits são transmitidos em sequência. A paralela é mais rápida, mas exige mais condutores; a serial usa menos condutores, com menor velocidade na comparação apresentada pela aula.

Para comunicações na ordem de **kB/s e MB/s**, o slide defende a implementação da comunicação serial.

![[Pasted image 20260927200851.png]]

Há diferentes protocolos e conectores para comunicação serial. O slide mostra HDMI 1.4V (**10,2 Gb/s**), USB 3.0 (**5 Gb/s**), Ethernet CAT 5e (**1 Gb/s**), RS232 (**0,25 Gb/s**) e SATA (**6 Gb/s**). Na tabela, os destaques para esta aula são **UART máx. 2,7648 Mbit/s (345,6 kB/s)**, **I2C 3,4 Mbit/s (425 kB/s)** e **SPI até 100 MHz, 100 Mbit/s (12,5 MB/s)**.

![[Pasted image 20260927200852.png]]

Obs: no mesmo slide, a imagem indica **RS232 = 0,25 Gb/s**, enquanto a tabela indica **Serial EIA-232 máx. = 230,4 kbit/s**. Os valores não concordam; ambos foram mantidos como aparecem no material.

## UART

**UART (Universal Asynchronous Receiver Transmitter)** é uma ligação simples entre dois pontos, **sem hierarquia**. A aula cita RS232 e RS485 como protocolos de dispositivos industriais definidos a partir dela. Com transdutores, pode alcançar longas distâncias. Exemplos apresentados: monitor serial do Arduino a **9600 baud**, cabo RS232, módulo GPS e comunicação sem fio entre dispositivos.

A transmissão pode ser:

- **Simplex:** em uma direção.
- **Half-duplex:** nas duas direções, uma por vez.
- **Full-duplex:** nas duas direções ao mesmo tempo, usando dois barramentos.

TX de um dispositivo se liga ao RX do outro. Os dois dispositivos devem compartilhar a **mesma referência de GND** e possuir o **mesmo nível lógico alto**. Se operarem com tensões diferentes, usam-se conversores de nível lógico (**transceivers**); o exemplo da aula liga um **ATmega328P de +5 V** a um **ESP8266 de +3,3 V** por um transceiver bidirecional.

### Comunicação assíncrona e quadro

Na UART, TX e RX têm **clocks diferentes**: a comunicação é **assíncrona**. Para esse tipo de comunicação, deve-se usar uma **largura de banda (taxa de transmissão) pré-definida** no transmissor e no receptor; o slide dá os exemplos **9600 b/s** e **15200 b/s**. O TX envia sem saber se o RX está lendo, então informações podem se acumular.

No exemplo de envio de **10010011**, o quadro tem **bit de início = 0**, **8 bits de dados** (tipicamente enviados do **LSB para o MSB**), **bit de paridade** para verificar a integridade e **bit de término = 1**. O gráfico mostra os bits de dados na ordem temporal **11001001**, começando pelo LSB.

![[Pasted image 20260927200853.png]]

## I2C

**I2C (Inter-Integrated Circuit)** foi desenvolvido em **1982**, segundo a aula, pela **Phillips**. É usado em curtas distâncias (**< 30 cm**) em sistemas embarcados como ATmega328P e ESP8266. É **síncrono** (clock comum) e **half-duplex**. Exemplos: conversores A/D e D/A, relógio de tempo real (**RTC**) e display LCD **20×4**.

Usa dois barramentos compartilhados:

- **SDA (Serial Data):** transporta endereço, dados e bits de reconhecimento.
- **SCL (Serial Clock):** clock comum controlado pelo **mestre**.

Há uma hierarquia **mestre–escravos**: o mestre controla o clock e pode enviar ou receber dados dos escravos. Na pinagem mostrada, o **Arduino Uno** usa **A4 = SDA** e **A5 = SCL**; o **ESP8266** usa **D2 = SDA** e **D1 = SCL**.

![[Pasted image 20260927200854.png]]

O material indica que todos os dispositivos devem estar sujeitos à **mesma alimentação**. Tipicamente, resistores **pull-up** ligam SDA e SCL à alimentação para manter o nível lógico alto consistente. No circuito da aula, um **ATmega328P mestre** compartilha SDA e SCL com três escravos: **RTC**, **LCD 16×2** e outro **ATmega328P**; os pull-ups estão ligados a **+5 V**.

![[Pasted image 20260927200855.png]]

### Sinais e mensagem

- **Início:** SDA cai enquanto SCL está em nível alto.
- **Registro de bit:** o valor em SDA é registrado durante o pulso alto de SCL. Nesse pulso, **SDA não pode mudar de nível**.
- **Término:** SDA sobe enquanto SCL está em nível alto.

No exemplo, a mensagem é **01101110**. O gráfico a apresenta temporalmente do **LSB para o MSB** como **01110110**.

![[Pasted image 20260927200856.png]]

O quadro da mensagem contém **Start**, janela de endereço de **7 ou 10 bits**, bit de **leitura/escrita**, **ACK/NACK**, janelas de dados de **8 bits** com **ACK/NACK** após cada uma e **Stop**. Os escravos verificam o endereço requisitado pelo mestre para decidir se farão a leitura dos dados; o bit de leitura/escrita indica o sentido da comunicação. **ACK** é o reconhecimento do dispositivo receptor sobre o recebimento.

![[Pasted image 20260927200857.png]]

## SPI

**SPI (Serial Peripheral Interface)** foi desenvolvido em **1985** pela **Motorola**. É usado em curtas distâncias (**< 30 cm**) em sistemas embarcados como ATmega328P e ESP8266. É **síncrono** e **full-duplex**. Exemplos da aula: sensor **RFID**, cartão **SD** e display LCD **240 px × 240 px**.

Três barramentos são compartilhados:

- **MOSI (Master Out Slave In):** dados do mestre para o escravo.
- **MISO (Master In Slave Out):** dados do escravo para o mestre.
- **SCLK (Serial Clock):** clock comum.

Cada escravo tem uma linha própria de seleção **SS (Slave Selection)**, também chamada **CS (Chip Selection)**. Na pinagem mostrada, o **Arduino Uno** usa **13 = SCLK**, **12 = MISO**, **11 = MOSI** e **10 = SS**; o **ESP8266** usa **D5 = SCLK**, **D6 = MISO**, **D7 = MOSI** e **D8 = SS**.

![[Pasted image 20260927200858.png]]

O material indica a **mesma alimentação** para todos os dispositivos e o uso típico de **pull-up** entre barramentos e alimentação para manter o nível alto consistente. O esquema mostra um **ATmega328P mestre** ligado a três escravos (**RFID**, **cartão SD** e outro **ATmega328P**): MOSI, MISO e SCLK são compartilhados; **SS1, SS2 e SS3** selecionam cada escravo.

![[Pasted image 20260927200859.png]]

Obs: o próprio slide chama esse circuito de **exemplo didático** e avisa que o **ATmega328P possui apenas um canal SS**, embora o desenho mostre SS1, SS2 e SS3.

### Sinais e envio simultâneo

O **início** ocorre na borda de descida do **SS** do escravo escolhido. Os bits em **MOSI** e **MISO** são registrados com os pulsos de **SCLK**; a borda de subida do SS marca o **término**. Não há janelas de endereço nem de ACK: a seleção é direta pela linha SS.

No exemplo, enquanto SS fica baixo durante **8 pulsos de SCLK**, o mestre envia **01101110** por MOSI e recebe **00100011** por MISO ao mesmo tempo. O gráfico dispõe os bits do **LSB para o MSB**: MOSI **01110110** e MISO **11000100**.

![[Pasted image 20260927200900.png]]

## Suposições finais da aula

O último slide propõe estas comparações:

- **UART:** mais flexível nos modos (simplex, half-duplex e full-duplex), arquitetura mais simples e possibilidade de longas distâncias em comparação com I2C e SPI, geralmente restritos à placa de circuito impresso.
- **I2C:** half-duplex, porém mais rápido que UART e, segundo o slide, com maior integridade na entrega/recepção dos dados.
- **SPI:** full-duplex e mais rápido que I2C, ao custo de usar mais barramentos.

