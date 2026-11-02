## Ambiente de simulação do TinkerCAD:

**Definição:** ambiente onde se monta o circuito com o Arduino, escreve o código do microcontrolador e simula tudo junto, medindo tensão e corrente com multímetros virtuais.

**Pontos da tela que vão ser usados:**
- **Circuitos / Esquemático / Componentes** = abas de visualização no topo.
- **Código** = abre o editor onde fica o programa do Arduino (`setup()` e `loop()`).
- **Iniciar simulação** = roda o circuito com o código carregado.
- **Painel de componentes (Básico)** = Resistor, LED, Botão, Potenciômetro, Capacitor, Interruptor deslizante, Bateria 9V, Bateria 3V do tipo moeda, Bateria 1,5V, Placa de ensaio, micro:bit, Arduino Uno R3. Tem também o campo **Pesquisar**.

![[Pasted image 20261024211304.png|600]]

### Medindo com o multímetro:

O multímetro do TinkerCAD tem os modos **A** (corrente), **V** (tensão) e **R** (resistência). O modo ativo fica destacado no canto do aparelho.

- **Corrente (A)** → o multímetro entra **em série**, no meio do caminho da corrente. Ela precisa passar por dentro dele.
- **Tensão (V)** → o multímetro entra **em paralelo**, com uma ponta de cada lado do componente.

**Amperímetro faz parte do caminho; voltímetro só "encosta" nos dois lados do componente.**

## Simulação 1: LED vermelho e LED azul:

**Enunciado:**
- Escrita digital: LED vermelho e LED azul, controlados de forma independente.
- O LED vermelho deve ser acionado a partir de um **nível lógico alto**, com corrente de **20 mA**.
- O LED azul deve ser acionado a partir de um **nível lógico baixo**, com corrente de **10 mA**.
- Os LEDs devem acender de forma **alternada, de 3 em 3 segundos**.
- Medir a **tensão de polarização direta** e a **corrente** sobre cada LED.

Os dois LEDs ligados de jeitos opostos: o vermelho com a lógica "normal" e o azul com a lógica invertida, que é o mesmo caso do LED da escrita digital da aula 2 (o que acende com GND na saída).

**No circuito:**
- **Pino 3** = saída digital que controla o LED vermelho.
- **Pino 5** = saída digital que controla o LED azul.
- **LED vermelho** = ligado entre o pino 3 e o GND, passando pelo resistor.
- **LED azul** = ligado entre o +5 V e o pino 5, passando pelo resistor.
- **Resistores** = um em série com cada LED, limitando a corrente (20 mA no vermelho e 10 mA no azul).
- **Multímetros em modo A** = em série com cada LED, medem a corrente.
- **Multímetros em modo V** = em paralelo com cada LED, medem a tensão de polarização direta.

![[Pasted image 20261024212151.png|600]]

#### Estudando os casos de funcionamento:

**LED vermelho (pino 3, aciona em nível alto)**

**Quando pino 3 = 1**
- O pino vai para +5 V.
- O outro lado do caminho está no GND → existe diferença de tensão sobre o LED e o resistor.
- O pino **empurra** a corrente: ela sai do microcontrolador, passa pelo LED e vai para o GND.

$$\text{pino }3=1 \Rightarrow \text{LED vermelho aceso}$$

**Quando pino 3 = 0**
- O pino vai para GND.
- Os dois lados do caminho estão em GND → não tem diferença de tensão, não passa corrente.

$$\text{pino }3=0 \Rightarrow \text{LED vermelho apagado}$$

**LED azul (pino 5, aciona em nível baixo)**

**Quando pino 5 = 0**
- O pino vai para GND.
- O outro lado está no +5 V → existe diferença de tensão sobre o LED e o resistor.
- O pino **puxa** a corrente para GND: ela vem do +5 V, passa pelo LED e **entra no microcontrolador**.

$$\text{pino }5=0 \Rightarrow \text{LED azul aceso}$$

**Quando pino 5 = 1**
- O pino vai para +5 V.
- Os dois lados do caminho estão em +5 V → não tem diferença de tensão, não passa corrente.

$$\text{pino }5=1 \Rightarrow \text{LED azul apagado}$$

**O LED só acende quando os dois lados dele estão em tensões diferentes. No vermelho quem fornece o +5 V é o pino; no azul o +5 V já está lá, e o pino só precisa fechar o caminho para GND.**

### Pegadinha: alternar com o mesmo valor nos dois pinos:

O código escreve **o mesmo valor** nos dois pinos ao mesmo tempo, e mesmo assim os LEDs alternam:

| Escrita nos pinos 3 e 5 | LED vermelho | LED azul |
|---|---|---|
| 1 | aceso | apagado |
| 0 | apagado | aceso |

→ Quem faz a alternância é a **montagem** (lógicas opostas), não o código.

**Obs:** "controlados de forma independente" quer dizer que cada LED tem o seu pino. Daria para escrever valores diferentes em cada um, mesmo que este código escreva sempre o mesmo valor nos dois.

### Dimensionando os resistores:

O enunciado fixa a **corrente** de cada LED (20 mA e 10 mA), então quem define essa corrente é o resistor em série. Com o LED aceso, a tensão da fonte se divide entre o LED e o resistor:

$$V_{fonte} = V_{LED} + V_R \Rightarrow V_R = V_{fonte} - V_{LED}$$

E pela lei de Ohm no resistor:

$$R = \frac{V_{fonte} - V_{LED}}{I}$$

- $V_{fonte}$ → 5 V nos dois LEDs (no vermelho vem do pino em nível alto; no azul vem do pino 5V do Arduino).
- $V_{LED}$ → tensão de polarização direta do LED, a mesma que o enunciado pede para medir com o multímetro (V).
- $I$ → corrente pedida, **em ampères** (20 mA = 0,020 A; 10 mA = 0,010 A).

**Exemplo:** se o multímetro mostrar $V_{LED} = 2\ V$ nos dois LEDs:

$$R_{verm} = \frac{5 - 2}{0{,}020} = 150\ \Omega \qquad R_{azul} = \frac{5 - 2}{0{,}010} = 300\ \Omega$$

→ Metade da corrente pede o dobro da resistência.

**Na prática:** monte com um valor inicial, rode a simulação, leia $V_{LED}$ no multímetro (V) e recalcule $R$ com o valor medido. Depois confira no multímetro (A) se a corrente ficou em 20 mA / 10 mA.

**Cuidado:**
- Corrente em **mA** na fórmula sem converter → resistor 1000 vezes menor que o certo.
- Resistor menor que o calculado → corrente acima do pedido. Resistor maior → corrente abaixo e LED mais fraco.

### Na prática: acender os dois LEDs alternando de 3 em 3 s:

**Montagem:**
- **Vermelho:** pino 3 → LED vermelho → resistor → multímetro (A) → GND.
- **Azul:** +5 V → multímetro (A) → resistor → LED azul → pino 5.
- Um multímetro (V) em paralelo com cada LED.

**Configuração:**
1. Dar um nome para cada pino com `#define`. Assim, para trocar de pino, basta mudar uma linha.
2. Configurar os pinos 3 e 5 como **saída** com `pinMode(..., OUTPUT)` dentro do `setup()`. Isso é feito uma vez só, quando o Arduino liga.

Pela pinagem do Arduino Uno, o pino 3 é o **PD3** e o pino 5 é o **PD5**. O `pinMode(..., OUTPUT)` faz por baixo o que a aula 2 fazia direto no DDRD.

**Código:**

```cpp
#define pinoLEDverm 3   // LED vermelho no pino digital 3
#define pinoLEDazul 5   // LED azul no pino digital 5

void setup(){
  pinMode(pinoLEDverm, OUTPUT);  //Configura a porta digital como saída
  pinMode(pinoLEDazul, OUTPUT);  // pino 5 como saída
}

void loop(){
  digitalWrite(pinoLEDverm, 1);  //Escrita digital (1 nível alto, 0 nível baixo)
  digitalWrite(pinoLEDazul, 1);  // pino 5 em +5 V → azul apagado
  delay(3000);                   //Comando de espera (medido em ms)
  digitalWrite(pinoLEDverm, 0);  // pino 3 em GND → vermelho apagado
  digitalWrite(pinoLEDazul, 0);  // pino 5 em GND → azul aceso
  delay(3000);                   // espera 3 s
}
```

- `pinMode(pino, OUTPUT)` → o pino passa a ser **saída**: o microcontrolador impõe o nível nele.
- `digitalWrite(pino, 1)` → coloca **nível alto (+5 V)** no pino; `digitalWrite(pino, 0)` → coloca **nível baixo (GND)**.
- `delay(3000)` → segura o estado atual por **3000 ms = 3 s**.
- O `loop()` repete para sempre: 3 s vermelho aceso → 3 s azul aceso → volta.

**O que acontece:**
- Primeiros 3 s: pino 3 = 1 e pino 5 = 1 → **vermelho aceso, azul apagado**.
- Próximos 3 s: pino 3 = 0 e pino 5 = 0 → **vermelho apagado, azul aceso**.
- Nos multímetros: a tensão de polarização direta e a corrente aparecem no LED que está aceso (≈ 20 mA no vermelho e ≈ 10 mA no azul).

**Cuidado:**
- Esquecer o `pinMode(..., OUTPUT)` → o pino não fica configurado como saída e o LED não é acionado como esperado.
- Ligar o azul igual ao vermelho (pino → LED → GND) → ele passa a acender junto com o vermelho e a alternância some.
- O `delay` é em **ms**: `delay(3)` dá 3 ms, não 3 s.
- Amperímetro em paralelo não mede a corrente do LED. Ele tem que estar **em série**.

## Simulação 2: 4 LEDs com transistor NPN como chave:

**Enunciado:**
- Escrita digital: **4 LEDs verdes em paralelo** controlados pela **mesma porta digital**, com **18 mA por LED**.
- Usar um **Transistor Bipolar de Junção (TBJ) NPN como chave**, com resistência de polarização de base de **330 Ω**.
- Uma **bateria de 9 V** aciona a carga pelo caminho **coletor-emissor**.
- Os LEDs devem acender/apagar de forma **alternada, de 5 em 5 segundos**.
- Medir a **tensão entre coletor e emissor** e a **corrente que sai da bateria**.

**Obs:** os slides 6 e 8 dizem **330 Ω** no resistor de base, mas o slide 7 (o do esquemático) diz **220 Ω**. Pode aparecer qualquer um dos dois.

Aqui o pino não acende os LEDs diretamente: ele só liga ou desliga o transistor. A corrente dos LEDs sai da **bateria de 9 V**, e o pino fornece só a pequena corrente de base. É a mesma ideia do coletor aberto da aula 3: o transistor só puxa o coletor para GND, e o nível alto vem de uma fonte externa, que pode ter outra tensão (aqui 9 V).

**No circuito:**
- **Pino 5** = saída digital que comanda o transistor.
- **Resistor de base (330 Ω)** = limita a corrente que sai do pino e entra na base do NPN.
- **Transistor NPN** = chave entre o coletor e o emissor.
- **Emissor** = ligado ao GND do Arduino.
- **4 LEDs verdes + 4 resistores** = cada LED com o seu resistor em série (limita em 18 mA). Os 4 ramos ficam em paralelo, entre a bateria e o coletor.
- **Bateria 9 V** = o + alimenta os LEDs e o − vai no GND do Arduino (GND comum).
- **Multímetro (A)** = em série entre o + da bateria e os LEDs, mede a corrente que sai da bateria.
- **Multímetro (V)** = em paralelo entre coletor e emissor, mede $V_{CE}$.

![[Pasted image 20261024213417.png|600]]

#### Estudando os casos de funcionamento:

**Quando pino 5 = 1**
- Corrente sai do pino, passa pelo resistor de 330 Ω e entra na base.
- O NPN **satura** → chave **fechada** entre coletor e emissor.
- O coletor é **puxado para GND** → a corrente sai da bateria, passa pelos 4 ramos de LED e desce pelo transistor até o GND.
- $V_{CE}$ fica pequena, já que a chave está fechada.

$$\text{pino }5=1 \Rightarrow \text{NPN satura} \Rightarrow \text{4 LEDs acesos}$$

**Quando pino 5 = 0**
- Não existe corrente na base.
- O NPN fica em **corte** → chave **aberta** entre coletor e emissor.
- O caminho dos LEDs até o GND fica interrompido → não passa corrente, nenhum LED acende.
- Com a chave aberta não passa corrente pelos ramos, então os resistores e LEDs não "gastam" tensão e o coletor fica no potencial da bateria: a tensão fica praticamente toda sobre o transistor, **$V_{CE} \approx 9\ V$**.

$$\text{pino }5=0 \Rightarrow \text{NPN em corte} \Rightarrow \text{4 LEDs apagados}$$

**Corrente total da bateria** com os LEDs acesos: os 4 ramos estão em paralelo, então as correntes se somam:

$$I_{bateria} = 4 \times 18\ \text{mA} = 72\ \text{mA}$$

**O pino só decide se a chave abre ou fecha. Quem empurra a corrente pelos LEDs é a bateria de 9 V, pelo caminho coletor-emissor.**

### Dimensionando os resistores dos LEDs:

Cada ramo tem o seu resistor, e cada ramo precisa de **18 mA**. Com o transistor saturado, a tensão da bateria se divide entre o resistor, o LED e o transistor ($V_{CE}$, pequena mas não zero):

$$R = \frac{V_{bateria} - V_{LED} - V_{CE}}{I_{LED}}$$

- $V_{bateria}$ → 9 V.
- $V_{LED}$ → tensão de polarização direta do LED verde (medir no TinkerCAD).
- $V_{CE}$ → tensão coletor-emissor com o transistor saturado, a que o enunciado pede para medir.
- $I_{LED}$ → 18 mA = 0,018 A. É a corrente **de um ramo**, não a total da bateria (72 mA).

**Exemplo:** com $V_{LED} = 2\ V$ e $V_{CE} = 0{,}2\ V$ medidos:

$$R = \frac{9 - 2 - 0{,}2}{0{,}018} \approx 378\ \Omega$$

→ Como os 4 LEDs são iguais e estão em paralelo entre os mesmos pontos, os 4 resistores têm o mesmo valor.

**Obs:** O resistor de **base** não é calculado: o enunciado já dá o valor (330 Ω, ou 220 Ω no slide do esquemático). Ele só limita a corrente que sai do pino para a base; não define a corrente dos LEDs.

**Cuidado:**
- Usar a corrente total (72 mA) no cálculo de cada resistor → resistor 4 vezes menor que o certo.
- Usar 5 V em vez de 9 V → nesta montagem quem alimenta os LEDs é a bateria, não o pino.

### Na prática: acender/apagar os 4 LEDs de 5 em 5 s:

**Montagem:**
- Pino 5 → resistor 330 Ω → base do NPN.
- Emissor do NPN → GND do Arduino.
- + da bateria 9 V → multímetro (A) → 4 ramos em paralelo (LED + resistor cada) → coletor do NPN.
- − da bateria 9 V → GND do Arduino.
- Multímetro (V) entre coletor e emissor.

**Configuração:**
1. Nomear o pino com `#define pinoLeds 5`.
2. Configurar o pino 5 como **saída** no `setup()`. Um pino só controla os 4 LEDs, porque todos dependem do mesmo transistor.

**Código:**

```cpp
#define pinoLeds 5   // pino digital 5 comanda a base do NPN

void setup(){
  pinMode(pinoLeds, OUTPUT);   // pino 5 como saída
}

void loop(){
  digitalWrite(pinoLeds, 1);   // pino 5 em +5 V → NPN satura → LEDs acesos
  delay(5000);                 // espera 5 s
  digitalWrite(pinoLeds, 0);   // pino 5 em GND → NPN em corte → LEDs apagados
  delay(5000);                 // espera 5 s
}
```

- A estrutura é a mesma da simulação 1. O que muda é o pino escrevendo na **base do transistor**, e não direto no LED.
- `delay(5000)` → **5000 ms = 5 s** em cada estado.

**O que acontece:**
- 5 s com os **4 LEDs acesos**: o amperímetro da bateria mostra a soma das correntes dos 4 ramos (≈ 72 mA) e $V_{CE}$ fica baixa.
- 5 s com os **4 LEDs apagados**: a corrente da bateria vai para 0 e $V_{CE}$ sobe para ≈ 9 V.

**Cuidado:**
- Esquecer de ligar o **− da bateria no GND do Arduino** → a corrente dos LEDs não tem como voltar para a bateria pelo emissor, e o circuito não fecha.
- Ligar a base direto no pino, sem o resistor de 330 Ω → nada limita a corrente que sai do pino para a base.
- Ramos de LED sem resistor próprio → nada limita os 18 mA de cada LED.

## Resumo prático:

**Funções do Arduino:**
- `#define nome pino` → dá nome ao pino.
- `pinMode(pino, OUTPUT)` → pino como saída (no `setup()`).
- `digitalWrite(pino, 1)` → +5 V no pino | `digitalWrite(pino, 0)` → GND no pino.
- `delay(ms)` → espera em milissegundos (3000 = 3 s, 5000 = 5 s).

**Pinos usados:**

| Pino Arduino | Porta | Uso |
|---|---|---|
| 3 | PD3 | LED vermelho (Sim. 1) |
| 5 | PD5 | LED azul (Sim. 1) / base do NPN (Sim. 2) |

**Lógica do LED:**
- Pino → LED → resistor → GND: **acende com 1**.
- +5 V → resistor → LED → pino: **acende com 0** (a corrente entra no microcontrolador).

**Transistor NPN como chave:**
- Pino → resistor de base (330 Ω) → base; emissor no GND; carga entre +9 V e coletor; − da bateria no GND do Arduino.
- 1 na base → satura → chave fechada → carga liga.
- 0 na base → corte → chave aberta → carga desliga ($V_{CE} \approx 9\ V$).

**Resistor do LED:**
- LED direto no pino/5 V: $R = \dfrac{5 - V_{LED}}{I}$.
- LED pelo transistor com bateria de 9 V: $R = \dfrac{9 - V_{LED} - V_{CE}}{I_{LED}}$ (corrente de um ramo).
- $I$ sempre em **A** (18 mA = 0,018 A); $V_{LED}$ e $V_{CE}$ medidos no multímetro.

**Medição:**
- Corrente → multímetro em **A**, em **série**.
- Tensão → multímetro em **V**, em **paralelo**.
