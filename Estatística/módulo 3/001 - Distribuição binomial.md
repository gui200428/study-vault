
## Definição:

Usado para modelar o número de sucessos em uma sequência de n tentativas independentes, onde cada tentativa tem apenas dois resultados possíveis (sucesso ou fracasso) e a probabilidade de sucesso (p) permanece constante em todas as tentativas.

**Detalhando:** Ao realizar um experimento por várias vezes seguidas, existe uma “tentativa” e há somente duas coisas que podem acontecer:

1. **Sucesso:** O evento de interesse ocorreu.
2. **Fracasso:** O evento de interesse não ocorreu.

A **distribuição binomial** ajuda a calcular a probabilidade de obter um número específico de “sucessos” em um número total de “tentativas”.


## Quando usar?

1. **Número fixo de tentativas ($n$)**: O experimento é realizado um número específico e fixo de vezes.
2. **Tentativas independentes:** O resultado de uma tentativa não afeta o resultado das outras.
3. **Dois resultados possíveis:** Cada tentativa resulta em um de dois resultados mutuamente exclusivos: sucesso ou fracasso.
4. **Probabilidade constante de sucesso (p):** A probabilidade de "sucesso" é a mesma para cada tentativa. A probabilidade de "fracasso" será, portanto, q=1−p.

## Fórmulas da distribuição binomial:


**Função massa de probabilidade (FMP):**
→ Esta fórmula calcula a probabilidade de obter exatamente $k$ sucessos em $n$ tentativas.

### $$P(X = k) = \binom{n}{k} \cdot p^k \cdot q^{n - k}$$
**Sendo:**
- n: número total de tentativas.
- k: número de sucessos desejados (um valor entre 0 e n).
- p: probabilidade de sucesso em uma única tentativa.
- q: probabilidade de fracasso em uma única tentativa (q=1−p).
- $\binom{n}{k}$: Coeficiente Binomial, também lido como "n escolhe k", que representa o número de maneiras diferentes de escolher k sucessos em n tentativas. Ele é calculado como:


### $$\binom{n}{k} = \frac{n!}{k!(n-k)!}$$
