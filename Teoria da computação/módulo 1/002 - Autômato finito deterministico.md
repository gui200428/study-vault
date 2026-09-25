## Definição:
**AFD:** é um modelo computacional formado por uma **quantidade finita de estados**.

Ele recebe uma **cadeia de símbolos** como entrada e, ao final, decide se essa cadeia será:

- **aceita**
- **rejeitada**

Em outras palavras, o AFD percorre seus estados seguindo regras definidas até determinar se a cadeia pertence ou não à linguagem reconhecida pelo autômato.

### Funcionamento do AFD

Como o computador possui **memória finita**, um AFD também trabalha com uma quantidade **finita de estados**.

A cada nova entrada, o autômato:

- lê um símbolo da cadeia;
- verifica o **estado atual**;
- muda para um **novo estado** de acordo com a regra definida.

Essa mudança de estado é **determinística**, ou seja, para cada estado e símbolo de entrada existe **um único próximo estado possível**.

Por isso, a mesma sequência de entrada sempre produz o mesmo resultado.

### Elementos de um AFD

Um AFD é formado basicamente por:

- **Estados:** representam as possíveis situações em que o autômato pode estar.
- **Transições:** definem para qual estado o autômato deve ir após receber uma entrada.
- **Controle:** acompanha o estado atual e executa as transições conforme os símbolos são lidos.

Exemplo:

Um sistema pode ter os estados `aberta` e `fechada`.

- ao receber `abrir`: `fechada → aberta`
- ao receber `fechar`: `aberta → fechada`

Ou seja, o AFD muda de estado conforme a entrada recebida.

![[Pasted image 20260923002903.png]]

### Exemplo de AFD – Zumbi em um jogo

O comportamento de um zumbi pode ser representado por um AFD, em que cada estado representa uma ação possível.

Estados do zumbi:

- **Parado**
- **Perseguir**
- **Atacar**
- **Comer**
- **Morto**

As entradas fazem o zumbi mudar de estado.

Exemplos de transições:

- `Parado → Perseguir`
- `Perseguir → Parado`
- `Perseguir → Atacar`
- `Atacar → Perseguir`
- `Atacar → Comer`
- `Comer → Parado`
- `Atacar → Morto`

Assim, o autômato representa de forma organizada como o zumbi reage a cada situação do jogo.

![[Pasted image 20260923003015.png]]

### Resumo do funcionamento de um AFD

- O AFD trabalha com uma quantidade **finita de estados**.
- Em cada momento, ele está em **apenas um estado**.
- Ele muda de estado conforme a **entrada recebida**.
- O próximo estado depende do **estado atual + símbolo de entrada**.
- Seu funcionamento é **determinístico**: a mesma entrada, no mesmo estado, sempre leva ao mesmo próximo estado.
- As entradas podem gerar **saídas ou decisões** do autômato.
- Em uma implementação computacional, essas operações podem ser sincronizadas pelos **ciclos de clock**.


### Definição formal de um AFD
Formalmente, um **Autômato Finito Determinístico** pode ser definido como uma **5-tupla**:

### $$A = (Q, Σ, δ, S₀, F)$$
**Onde:**
- **Q**: conjunto finito de estados;
- **Σ**: alfabeto de entrada;
- **δ**: função de transição;
- **S₀**: estado inicial;
- **F**: conjunto de estados finais, também chamados de **estados de aceitação**.


### Função de transição

A função de transição `δ` indica **como o autômato muda de estado** ao receber um símbolo de entrada.

Ela é do tipo:

`δ: Q × Σ → Q`

Isso significa que, dado:

- um **estado atual**, e
- um **símbolo do alfabeto**,

o autômato determina **um único próximo estado**.

> **estado atual + símbolo lido → próximo estado**

#### Exemplo:

![[Pasted image 20260925115240.png]]

- `Q = {q0, q1}` → estados possíveis
- `Σ = {0,1}` → símbolos que podem chegar na entrada
- `S₀ = q0` → inicia em `q0`
- `F = {q1}` → `q1` é estado de aceitação

#### Função de transição:

| Estado atual | Entrada `0` | Entrada `1` |
| ------------ | ----------- | ----------- |
| **q0**       | q1          | q0          |
| **q1**       | q0          | q1          |
`δ(q0, 0) = q1`

> Estou em **q0**, li um **0**, então vou para **q1**.

**Da mesma forma:**

- `δ(q0, 1) = q0` → estou em q0, leio `1`, continuo em q0.
- `δ(q1, 0) = q0` → estou em q1, leio `0`, volto para q0.
- `δ(q1, 1) = q1` → estou em q1, leio `1`, continuo em q1.

### Vendo uma cadeia inteira:

**Usando a cadeia `1011`.**

Começando em `q0`:

`q0 --1→ q0 --0→ q1 --1→ q1 --1→ q1`

A cadeia terminou em **q1**.

**Como:**

`F = {q1}`

é aceito.

**RESUMINDO:**
**δ responde à pergunta: "Estou neste estado e chegou este símbolo. Para onde eu vou?"**


`δ(estado atual, entrada) = próximo estado`

