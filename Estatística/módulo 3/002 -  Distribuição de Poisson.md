

## Definição:

Usado para descrever a probabilidade de um certo número de eventos ocorrerem em um intervalo fixo de tempo ou espaço, assumindo que esses eventos acontecem a uma taxa média constante e de forma independente uns dos outros.

**Detalhes:** Ao observar eventos que acontecem de forma aleatória, mas com uma certa frequência média. Exemplo:
- O número de chamadas telefônicas recebidas por um call center em uma hora.
- O número de defeitos em um rolo de tecido de um determinado comprimento.
- O número de clientes que chegam a uma loja em um dia.
- O número de acidentes de trânsito em um cruzamento específico por mês.

A **Distribuição de Poisson** nos ajuda a calcular a probabilidade de observar um número específico desses eventos ($k$) em um dado intervalo, sabendo a taxa média ($λ$) com que eles costumam ocorrer nesse mesmo tipo de intervalo.

## Quando usar?

1. **Eventos ocorrem independentemente:** A ocorrência de um evento não afeta a probabilidade de ocorrência de outro evento.
2. **A taxa média de ocorrência (λ) é constante:** A taxa média com que os eventos ocorrem é constante para o intervalo considerado.
3. **A probabilidade de um evento ocorrer é proporcional ao tamanho do intervalo:** Se você dobrar o intervalo, espera-se que o número médio de eventos também dobre.
4. **É improvável que dois eventos ocorram exatamente no mesmo instante (ou ponto no espaço).**

A Distribuição de Poisson é frequentemente usada para eventos considerados "raros" dentro de um pequeno subintervalo, mas que podem ocorrer várias vezes ao longo de um intervalo maior.


## Fórmulas da distribuição de Poisson:

**1. Função Massa de Probabilidade (FMP):**
→ Esta fórmula calcula a probabilidade de ocorrerem exatamente k eventos no intervalo.
### $$P(X = k) = \frac{e^{-\lambda} \cdot \lambda^k}{k!}$$

**Sendo:**
- k: número de ocorrências do evento cujo cálculo de probabilidade se deseja (um inteiro não negativo: 0, 1, 2, ...).
- λ (lambda): é a taxa média de ocorrência de eventos no intervalo especificado. É importante que a unidade de λ seja consistente com o intervalo do problema.
