## Simulação 3: chave com pull-up acionando um LED:

**Enunciado:**
- Leitura digital e escrita digital: **LED laranja** (em série com **330 Ω**) deve ser **acionado quando a chave é aberta** e **apagado quando a chave está fechada**.
- A chave deve ser montada em um circuito com resistor **pull-up de 10 kΩ**.
- Medir a **tensão sobre a chave**, que é a tensão enviada para o microcontrolador.

Primeira simulação com **leitura**: o pino da chave é entrada e o pino do LED é saída. O microcontrolador lê o nível no pino da chave e decide o que escrever no pino do LED.

**No circuito:**
- **Pino 8** = entrada digital que lê a chave.
- **Resistor de 10 kΩ (pull-up)** = entre o +5 V e o pino 8. Puxa o pino para nível alto quando a chave está aberta.
- **Chave** = entre o pino 8 e o GND. Quando fecha, liga o pino direto no GND.
- **Pino 4** = saída digital que aciona o LED.
- **LED laranja + resistor de 330 Ω** = ligados entre o pino 4 e o GND. Acende com nível alto no pino, igual ao LED vermelho da simulação 1.
- **Multímetro (V)** = em paralelo com a chave, mede a tensão que chega no pino 8.

![[Pasted image 20261024214608.png|600]]

#### Estudando os casos de funcionamento:

O pino 8 está como entrada, ou seja, em **alta impedância (Z)** (aula 3): ele não impõe nível nenhum, só lê o que o circuito externo coloca nele.

**Quando a chave está aberta**
- A chave é uma chave **aberta**: não liga o pino 8 ao GND.
- Nada puxa o pino para baixo, então o **pull-up puxa o pino 8 para +5 V**.
- Multímetro: **≈ 5 V** sobre a chave.
- `digitalRead` lê **1** → o código cai no `else` → `digitalWrite(ledPin,1)` → pino 4 em +5 V.

$$\text{chave aberta} \Rightarrow \text{pino }8=1 \Rightarrow \text{LED aceso}$$

**Quando a chave está fechada**
- A chave vira uma chave **fechada** para o GND: **puxa o pino 8 para GND**.
- O +5 V fica todo sobre o resistor de 10 kΩ.
- Multímetro: **≈ 0 V** sobre a chave.
- `digitalRead` lê **0** → o código entra no `if` → `digitalWrite(ledPin,0)` → pino 4 em GND.

$$\text{chave fechada} \Rightarrow \text{pino }8=0 \Rightarrow \text{LED apagado}$$

→ O LED acaba copiando o valor lido na chave: **lê 1, escreve 1; lê 0, escreve 0**.

**A chave só consegue puxar o pino para 0. Quando ela abre, apenas "solta" o pino, e quem produz o nível alto é o pull-up. É a mesma ideia do coletor aberto da aula 3, só que com uma chave no lugar do transistor.**

**Pegadinha:** com pull-up, a lógica fica invertida em relação ao que parece natural: **chave fechada = 0** e **chave aberta = 1**. Por isso o LED acende com a chave aberta.

**Obs:** o resistor de pull-up também é o que evita um curto: com a chave fechada, sem ele o +5 V ficaria ligado direto no GND pela chave.

**Corrente no pull-up com a chave fechada:** o caminho é +5 V → 10 kΩ → chave → GND, e o pino 8 (entrada em Z) praticamente não puxa corrente:

$$I_{pull\text{-}up} = \frac{5\ V}{10\ k\Omega} = 0{,}5\ mA$$

→ Por isso o pull-up é um resistor **alto**: ele só precisa "segurar" o pino em +5 V quando a chave está aberta, e com a chave fechada deixa passar uma corrente pequena. Com a chave aberta, não há caminho para o GND e a corrente é ≈ 0.

**Corrente esperada no LED laranja:** com o pino 4 em +5 V, a tensão se divide entre o LED e o resistor de 330 Ω (mesma conta da simulação 1, só que agora o resistor já é dado e a incógnita é a corrente):

$$I_{LED} = \frac{5 - V_{LED}}{330\ \Omega}$$

**Exemplo:** com $V_{LED} = 2\ V$ → $I_{LED} = \frac{3}{330} \approx 9\ mA$. Na prova, use o $V_{LED}$ que o multímetro mostrar.

### Na prática: ler a chave e acionar o LED:

**Montagem:**
- +5 V → resistor 10 kΩ → pino 8.
- Pino 8 → chave → GND.
- Pino 4 → LED laranja → resistor 330 Ω → GND.
- Multímetro (V) em paralelo com a chave (uma ponta no lado do pino 8, outra no GND).

**Configuração:**
1. Nomear os pinos com `#define`: `chavePin` = 8 e `ledPin` = 4.
2. Criar uma variável `bool` para guardar o **valor lido** da chave (0 ou 1).
3. No `setup()`: pino 8 como **entrada** (`INPUT`) e pino 4 como **saída** (`OUTPUT`).

Pela pinagem do Arduino Uno, o pino 8 é o **PB0** e o pino 4 é o **PD4**. O `pinMode(..., INPUT)` faz o contrário do `OUTPUT`: zera o bit no DDRx e deixa a porta tri-state em Z, liberando o pino para leitura.

**Código:**

```cpp
#define chavePin 8   // chave no pino digital 8
#define ledPin 4     // LED laranja no pino digital 4

bool estadoChave = 0;   //Variável que recebe o estado da chave
                        //Não confundir com o número da porta digital!

void setup(){
  pinMode(chavePin, INPUT);   //Define a porta digital da chave como de entrada
  pinMode(ledPin, OUTPUT);    // pino 4 como saída
}

void loop(){
  estadoChave = digitalRead(chavePin);  //Realiza a leitura digital da chave

  if(estadoChave == 0){      //Estrutura condicional que aciona/apaga o LED
    digitalWrite(ledPin,0);  // chave fechada → pino 4 em GND → LED apagado
  }
  else{
    digitalWrite(ledPin,1);  // chave aberta → pino 4 em +5 V → LED aceso
  }

  delay(10);     //Atraso pequeno de 10 ms para limitar o laço de repetição
}
```

- `pinMode(chavePin, INPUT)` → pino 8 vira **entrada**: o microcontrolador para de impor nível e passa a ler o que está nele.
- `digitalRead(chavePin)` → devolve o nível presente no pino 8: **1** se estiver em +5 V, **0** se estiver em GND.
- `estadoChave` guarda o **valor lido** (0/1); `chavePin` é o **número do pino** (8). São coisas diferentes, como o próprio comentário avisa.
- `if (estadoChave == 0)` → testa se a chave está fechada. Se sim, apaga o LED; senão (`else`), acende.
- `delay(10)` → espera **10 ms** antes de ler de novo. O `loop()` fica relendo a chave o tempo todo, então qualquer mudança aparece no LED quase na hora.

**O que acontece:**
- Chave aberta: multímetro ≈ 5 V, **LED aceso**.
- Chave fechada: multímetro ≈ 0 V, **LED apagado**.
- Mexendo na chave durante a simulação, o LED muda junto.

**Cuidado:**
- Esquecer o pull-up → com a chave aberta o pino fica **solto (flutuante)**, sem nível definido, e a leitura não é confiável.
- Inverter a lógica no `if` → testar `== 1` para "chave fechada" faz o LED acender ao contrário do pedido.
- Confundir `chavePin` com `estadoChave` → `if (chavePin == 0)` compara o número 8 com 0, nunca é verdadeiro.
- Configurar o pino da chave como `OUTPUT` → o microcontrolador passa a impor nível no pino e briga com a chave, em vez de ler o que ela coloca nele.

## Simulação 4: 4 chaves acionando 2 LEDs (E / OU):

**Enunciado:**
- Leitura e escrita digital: **4 chaves** acionam **2 LEDs** (verde e amarelo).
- Caso a chave 1 **e** a chave 2 estejam pressionadas, o **LED verde** deve ser acionado.
- Caso a chave 1 **ou** a chave 2 estejam pressionadas, o **LED amarelo** deve ser acionado.
- Chaves com resistores **pull-up de 10 kΩ** e LEDs em série com resistores de **330 Ω**.

**Obs:** o enunciado do slide diz "chave 1 **ou** chave 2" para o LED amarelo, mas o código (e as 4 chaves do esquema) usam as **chaves 3 e 4** para o OU. O certo, conforme a solução:
- **LED verde** → chave 1 **E** chave 2.
- **LED amarelo** → chave 3 **OU** chave 4.

Se na prova aparecer a frase do slide (chaves 1 e 2 nos dois LEDs), basta trocar `estadoChave3`/`estadoChave4` por `estadoChave1`/`estadoChave2` no segundo `if`; aí só 2 chaves seriam necessárias.

**Obs:** no esquema as chaves são interruptores deslizantes. "Pressionada" aqui quer dizer **chave fechada**.

É a simulação 3 multiplicada: cada chave é o mesmo circuito de pull-up, cada LED é o mesmo circuito de saída. O que é novo é a **lógica no código**, combinando duas leituras com E (`&&`) e OU (`||`).

**No circuito:**
- **Pinos 13, 12, 11 e 10** = entradas das chaves 1, 2, 3 e 4.
- **4 resistores de 10 kΩ (pull-up)** = um entre o +5 V e cada pino de chave.
- **4 chaves** = cada uma entre o seu pino e o GND.
- **Pino 4** = saída do **LED verde** (resistor de 330 Ω para o GND).
- **Pino 5** = saída do **LED amarelo** (resistor de 330 Ω para o GND).

| Chave | Pino | Porta |
|---|---|---|
| 1 | 13 | PB5 |
| 2 | 12 | PB4 |
| 3 | 11 | PB3 |
| 4 | 10 | PB2 |
| LED verde | 4 | PD4 |
| LED amarelo | 5 | PD5 |

![[Pasted image 20261024215231.png|650]]

#### Estudando os casos de funcionamento:

Cada chave funciona igual à da simulação 3: **fechada (pressionada) → lê 0**, **aberta → lê 1**. Por isso o código testa `== 0` para saber se a chave está pressionada.

**LED verde (chave 1 E chave 2)**

| Chave 1 | Chave 2 | Lido 1 | Lido 2 | LED verde |
|---|---|---|---|---|
| aberta | aberta | 1 | 1 | apagado |
| aberta | fechada | 1 | 0 | apagado |
| fechada | aberta | 0 | 1 | apagado |
| fechada | fechada | 0 | 0 | **aceso** |

$$\text{chave 1 fechada} \;\textbf{E}\; \text{chave 2 fechada} \Rightarrow \text{LED verde aceso}$$

**LED amarelo (chave 3 OU chave 4)**

| Chave 3 | Chave 4 | Lido 3 | Lido 4 | LED amarelo |
|---|---|---|---|---|
| aberta | aberta | 1 | 1 | apagado |
| aberta | fechada | 1 | 0 | **aceso** |
| fechada | aberta | 0 | 1 | **aceso** |
| fechada | fechada | 0 | 0 | **aceso** |

$$\text{chave 3 fechada} \;\textbf{OU}\; \text{chave 4 fechada} \Rightarrow \text{LED amarelo aceso}$$

**Pegadinha:** o E e o OU são sobre as chaves **pressionadas**, não sobre os valores lidos. Como pressionada = 0, o verde acende quando as duas leituras são **0**, e não quando são 1.

**A porta lógica não está no circuito: as chaves só entregam 0 ou 1 para o microcontrolador, e quem faz o E e o OU é o `if` no código.**

### Na prática: implementar E e OU com 4 chaves:

**Montagem:**
- Para cada chave: +5 V → resistor 10 kΩ → pino (13, 12, 11 ou 10) → chave → GND.
- Pino 4 → LED verde → resistor 330 Ω → GND.
- Pino 5 → LED amarelo → resistor 330 Ω → GND.

**Configuração:**
1. `#define` para os 4 pinos de chave (13, 12, 11, 10) e os 2 de LED (4, 5).
2. Uma variável `bool` por chave para guardar o valor lido.
3. No `setup()`: os 4 pinos de chave como `INPUT` e os 2 de LED como `OUTPUT`.
4. No `loop()`: ler as 4 chaves primeiro, depois decidir cada LED com o seu `if`.

**Código:**

```cpp
#define chavePin1 13   // chave 1 no pino 13
#define chavePin2 12   // chave 2 no pino 12
#define chavePin3 11   // chave 3 no pino 11
#define chavePin4 10   // chave 4 no pino 10
#define ledGPin 4      // LED verde (Green) no pino 4
#define ledYPin 5      // LED amarelo (Yellow) no pino 5

bool estadoChave1 = 0;   // valor lido da chave 1
bool estadoChave2 = 0;   // valor lido da chave 2
bool estadoChave3 = 0;   // valor lido da chave 3
bool estadoChave4 = 0;   // valor lido da chave 4

void setup(){
  pinMode(chavePin1, INPUT);   // pino 13 como entrada
  pinMode(chavePin2, INPUT);   // pino 12 como entrada
  pinMode(chavePin3, INPUT);   // pino 11 como entrada
  pinMode(chavePin4, INPUT);   // pino 10 como entrada
  pinMode(ledGPin, OUTPUT);    // pino 4 como saída
  pinMode(ledYPin, OUTPUT);    // pino 5 como saída
}

void loop(){
  estadoChave1 = digitalRead(chavePin1);   // lê o pino 13 (0 = pressionada)
  estadoChave2 = digitalRead(chavePin2);   // lê o pino 12
  estadoChave3 = digitalRead(chavePin3);   // lê o pino 11
  estadoChave4 = digitalRead(chavePin4);   // lê o pino 10

  if(estadoChave1 == 0 && estadoChave2 == 0){ //Implementação de condicional E
    digitalWrite(ledGPin,1);   // chaves 1 e 2 pressionadas → pino 4 em +5 V → verde aceso
  }
  else{
    digitalWrite(ledGPin,0);   // senão → pino 4 em GND → verde apagado
  }

  if(estadoChave3 == 0 || estadoChave4 == 0){ //Implementação de condicional OU
    digitalWrite(ledYPin,1);   // chave 3 ou 4 pressionada → pino 5 em +5 V → amarelo aceso
  }
  else{
    digitalWrite(ledYPin,0);   // nenhuma das duas → pino 5 em GND → amarelo apagado
  }

  delay(10);   // espera 10 ms antes de ler de novo
}
```

- `&&` → **E**: a condição só é verdadeira se as **duas** comparações forem verdadeiras.
- `||` → **OU**: basta **uma** das comparações ser verdadeira.
- Os dois `if` são independentes: o LED verde depende só das chaves 1 e 2, e o amarelo só das chaves 3 e 4.
- As 4 leituras acontecem no começo do `loop()`, e os `if` usam esses valores guardados.

**O que acontece:**
- Fechando só a chave 1 ou só a chave 2 → verde continua **apagado**.
- Fechando as chaves 1 e 2 juntas → verde **acende**.
- Fechando a chave 3, a 4 ou as duas → amarelo **acende**.
- Mexer nas chaves 1 e 2 não muda o amarelo, e mexer nas 3 e 4 não muda o verde.
- Correntes iguais às da simulação 3: **0,5 mA** em cada pull-up com a chave fechada, e $\frac{5 - V_{LED}}{330}$ (≈ 9 mA com $V_{LED} = 2\ V$) em cada LED aceso.

**Cuidado:**
- Testar `== 1` para "pressionada" → com pull-up a lógica fica toda invertida (o verde acenderia com as duas chaves abertas).
- Trocar `&&` por `||` (ou o contrário) → troca o comportamento dos dois LEDs.
- Cada chave precisa do **seu** pull-up. Sem ele, o pino daquela chave fica flutuante quando ela está aberta.
- Ligar a chave no pino errado → ela passa a controlar o LED errado. Confira a tabela chave ↔ pino.

## Resumo prático:

**Funções do Arduino (novas nesta aula):**
- `pinMode(pino, INPUT)` → pino como **entrada** (em Z, só lê).
- `digitalRead(pino)` → devolve **1** (+5 V no pino) ou **0** (GND no pino).
- `bool variavel = 0;` → guarda o valor lido (não é o número do pino).
- `if (...) { } else { }` → decide o que escrever na saída.
- `&&` = E (as duas condições) | `||` = OU (pelo menos uma).
- `delay(10)` → 10 ms entre uma leitura e outra.

**Chave com pull-up:**
- +5 V → 10 kΩ → pino → chave → GND.
- Chave **aberta** → pull-up puxa para +5 V → lê **1**.
- Chave **fechada / pressionada** → chave puxa para GND → lê **0**.
- "Pressionada?" no código = `== 0`.
- Corrente com a chave fechada: $5\ V / 10\ k\Omega = 0{,}5\ mA$ (aberta: ≈ 0).

**LED na saída:**
- Pino → LED → 330 Ω → GND: acende com `digitalWrite(pino, 1)`.
- Corrente: $I = \dfrac{5 - V_{LED}}{330}$ (≈ 9 mA com $V_{LED} = 2\ V$).

**Pinos usados:**

| Pino Arduino | Porta | Uso |
|---|---|---|
| 8 | PB0 | chave (Sim. 3) |
| 4 | PD4 | LED laranja (Sim. 3) / LED verde (Sim. 4) |
| 5 | PD5 | LED amarelo (Sim. 4) |
| 13, 12, 11, 10 | PB5, PB4, PB3, PB2 | chaves 1, 2, 3, 4 (Sim. 4) |

**Sequência mínima de leitura + escrita:**
1. `#define` dos pinos e variáveis `bool` para as leituras.
2. `setup()`: chaves em `INPUT`, LEDs em `OUTPUT`.
3. `loop()`: `digitalRead` das chaves → `if` com a lógica pedida → `digitalWrite` nos LEDs → `delay(10)`.

**Medição:**
- Tensão na chave → multímetro em **V**, em **paralelo** com a chave: ≈ 5 V aberta, ≈ 0 V fechada.
