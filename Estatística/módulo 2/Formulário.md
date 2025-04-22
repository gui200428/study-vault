#faculdade #estatistica #resumos #formulario 
# Exercícios com urna

## Teorema da probabilidade total

→ A probabilidade total de um item ser escolhido é a soma do produto entre a chance de cada urna ser escolhida e a chance do item de interesse ser escolhido dentro dessa urna.

### Exemplo:

Dado duas urnas, a urna 1 contem: 2 bolas vermelhas e 3 bolas azuis, a urna 2 contem 4 bolas vermelhas e 1 bola azul. A chance de escolher qualquer umas das urnas é igual a 50% cada.

Qual é a probabilidade de sortear uma bola vermelha?

#### Passo 1: Probabilidade de cada urna

- $P(U_1) = 0.5$
- $P(U_2) = 0.5$

#### Passo 2: Probabilidade de sair uma bola vermelha em cada urna

- $P(Vermelha | U_1) = \frac{2}{5}$
- $P(Vermelha | U_2) = \frac{4}{5}$

#### Passo 3: Aplicar a fórmula da probabilidade

 $$P(Vermelha)=P(U_1).P(Vermelha|U_1)+P(U_2).P(Vermelha|U_2)$$

$$P(Vermelha)=0.5*\frac{2}{5}+0.5*\frac{4}{5}=0.6$$

---
## Probabilidade condicional

#### Qual é a **probabilidade de a urna escolhida ser a II**, **sabendo que** a bola sorteada foi **verde**?


$$P(U_2∣Verde)$$

##### Têm-se 4 urnas (I, II, III e IV). A I tem: 4 bolas brancas e  6 verdes; a II tem 4 brancas e 8 verdes; a III tem 3 brancas e 4 verdes e a IV tem 4 brancas e 9 verdes. Qual a prob. da urna escolhida ser a II, sabendo-se que a bola sorteada é verde?
### Passo 1: Anotar as informações do problema.


**Urna I**: 4 brancas, 6 verdes → total: 10

**Urna II**: 4 brancas, 8 verdes → total: 12

**Urna III**: 3 brancas, 4 verdes → total: 7

**Urna IV**: 4 brancas, 9 verdes → total: 13

**Probabilidade de cada urna ser escolhida:** $\frac{1}{4}$

### Passo 2: Encontrar a probabilidade total de sair o item

$$P(v)=\frac{1}{4}*\frac{6}{10}+\frac{1}{4}*\frac{8}{12}+\frac{1}{4}*\frac{4}{7}+\frac{1}{4}*\frac{9}{13}=0,633$$

### Passo 3: Aplicar o teorema de Bayes (Sabendo que…)
→ Usado para descobrir a **probabilidade de uma causa, dado um efeito observado**.
→ “Saiu uma bola branca. Qual é a chance de ter vindo da urna 1?”

$$P(U_2∣V)=\frac{P(U_2)*P(V∣U_2)}{P(V)}$$

→ Probabilidade de sair a urna que queremos, multiplicado pela probabilidade de sair o item que queremos naquela urna, dividido pela probabilidade total de sair o item que queremos.

$$P(U_2∣V)=\frac{\frac{8}{12}*\frac{1}{4}}{0,633}=0,263$$

---
## Probabilidade conjunta

→ Quando queremos saber a probabilidade de escolher um item e o item relacionado a esse item.
→ 2 itens conhecidos já

### $$P(U1∩B)=P(U1)⋅P(B∣U1)$$

---

# Operações com conjuntos

#### Normalmente envolve lançamento de moedas e dados

## Caso com lançamento de moedas:

**lançamento de 3 moedas:**

### Passo 1: Definir o espaço amostral

Cada moeda pode dar cara (C) ou coroa (K), então o espaço amostral S tem:

$$S={CCC,CCK,CKC,CKK,KCC,KCK,KKC,KKK}$$

### Passo 2: Definindo os eventos

A: a primeira face e a terceira são caras;
B: as três faces são iguais;


$$A={CCC,CCK}$$
$$B={CCC,KKK}$$

### a) P(A∪B)

→ Definir todos os casos que estão em A ou B.

**União:**

$$A∪B={CCC,CCK,KKK}$$

**Probabilidade:**

$$P(A∪B)=\frac{3}{8}$$

### b) P($\bar{A}$)

→ São todas as possibilidades excluindo o A

$$P(\bar{A})=\frac{8}{8}-\frac{2}{8}=\frac{3}{4}=0.75$$

### c) P(A/B)

→ Probabilidade de A dado que B aconteceu

A={CCC,CCK}
B={CCC,KKK}

→ Definir a interseção de A e B

$$A \cap B = \{CCC\}$$

→ Jogar na fórmula:

$$P(A/B)=\frac{P(A\ \cap\ B)}{P(B)}$$

$$P(A/B)=\frac{\frac{1}{8}}{\frac{2}{8}}=\frac{1}{2}=0.5$$

### d) P(B/A)

→ Probabilidade de A dado que B aconteceu

A={CCC,CCK}
B={CCC,KKK}

→ Definir a interseção de A e B

$$B \cap A = \{CCC\}$$

→ Jogar na fórmula:

$$P(B/A)=\frac{P(B\ \cap\ A)}{P(A)}$$

$$P(B/A)=\frac{\frac{1}{8}}{\frac{2}{8}}=\frac{1}{2}=0.5$$


## Caso com lançamento de dados:

#### Lançamento de dois dados

### Passo 1: Definir o espaço amostral

→ Cada dado tem 6 faces → total de combinações:

$$S =6*6=36$$

### Passo 2: Definir os eventos:

A: a primeira face é par;
B: a segunda face é par;

#### A: primeira face é par:

→ Em um dados temos 3 faces pares (2,4,6)
→ O segundo pode ter qualquer face

$$A=3*6=18$$
#### B: segunda face é par:

→ O primeiro pode ter qualquer face
→ Em um dados temos 3 faces pares (2,4,6)

$$B=6*3=18$$

#### A ∩ B: ambas as faces são pares

→ Primeira e segunda face são pares 
→ 3 opções na primeira e 3 na segunda

$$A \cap B=3*3=9$$

### a) P(A ∪ B)

→ Probabilidade de A ou B acontecer

$$P(A ∪ B)=P(A)+P(B)-P(A \cap B)$$

$$P(A ∪ B)= \frac{18}{36} + \frac{18}{36} - \frac{9}{36}=\frac{3}{4}=0.75$$

### b) P($\bar{A}$)

→ Probabilidade de não A, primeira face não é par.

$$P(\bar{A})=\frac{36}{36}-\frac{18}{36}=\frac{18}{36}=0.5$$



### c) P(A | B)

→ Probabilidade de A acontecer, dado que B aconteceu

$$P(A/B)=\frac{P(A\ \cap\ B)}{P(B)}$$

$$P(A/B)=\frac{\frac{9}{36}}{\frac{18}{36}}=\frac{1}{2}=0.5$$

### d) P(B | A)

→ Probabilidade de A acontecer, dado que B aconteceu

$$P(B/A)=\frac{P(B\ \cap\ A)}{P(A)}$$

$$P(A/B)=\frac{\frac{9}{36}}{\frac{18}{36}}=\frac{1}{2}=0.5$$


