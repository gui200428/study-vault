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