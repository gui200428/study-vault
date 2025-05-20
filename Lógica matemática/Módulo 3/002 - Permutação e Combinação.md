
# Permutação:

## Definição:

Uma **permutação** refere-se a qualquer uma das diferentes **ordenações** ou **arranjos** possíveis de um conjunto de objetos. A ordem importa!
Basicamente é quantas maneiras diferentes podemos enfileirar ou organizar os itens.


## Permutação sem repetição:

Todos os elementos do conjunto são distintos!

#### Fórmula (para arranjar todos os n itens):

### $$P(n)= n!$$
#### Fórmula (para arranjar k itens de um total de n itens distintos):

### $$P(n,k)=\frac{n!}{(n-k)!}$$


##### Exemplos:

**1. Permutação sem repetição (arranjando todos os itens):**
Imagine que você tem 3 livros diferentes: A (Algoritmos), B (Banco de Dados), C (Criptografia). De quantas maneiras diferentes você pode organizá-los em uma prateleira?

- Itens: {A, B, C}
- Número de itens (n) = 3
- Permutações possíveis (3!):

1. A - B - C
2. A - C - B
3. B - A - C
4. B - C - A
5. C - A - B
6. C - B - A

$P(3)= 3! =$ 6 maneiras diferentes!

**2. Permutação sem repetição (arranjando um subconjunto k de n itens):**
Quantas senhas de 4 dígitos **diferentes** podem ser formadas com os números 0-9?

- Total de itens (n) = 10 (dígitos 0, 1, 2, 3, 4, 5, 6, 7, 8, 9)
- Número de itens a serem arranjados (k) = 4

$$P(10,4)=\frac{10!}{(10-4)!}$$ 
$$P(10,4)=\frac{10!}{6!}$$
$$P(10,4)=\frac{10*9*8*7*6!}{6!}$$ $$P(10,4)=10*9*8*7 = 5040$$ 

## Permutação com repetição:

Existem elementos idênticos dentro do conjunto! O número de permutações distintas é menor do que se todos os elementos fossem únicos, porque trocar dois elementos idênticos de posição não cria um novo arranjo visualmente distinto.

#### Fórmula:

### $$P(n; r₁, r₂, ..., rk)=\frac{n!}{r₁! * r₂! * ... * rk!}$$
Onde:
- n = número total de elementos
- r₁, r₂, ..., rk = número de vezes que cada elemento distinto se repete.

##### Exemplos:

**1- Considere a palavra "CASA". Quantos anagramas (arranjos das letras) podemos formar?**

- Número total de letras (n) = 4
- Repetições:
- C: aparece 1 vez (r₁ = 1)
- A: aparece 2 vezes (r₂ = 2)
- S: aparece 1 vez (r₃ = 1)

$$P(4; 1, 2, 1)=\frac{4!}{(1! * 2! * 1!)}$$

$$P(4; 1, 2, 1)=\frac{4*3*2!}{2!}$$
$$P(4; 1, 2, 1)=12$$

Os 12 anagramas são:
1. CASA
2. CAAS
3. CSAA
4. ACSA
5. ACAS
6. ASCA
7. ASAC
8. AACS
9. AASC
10. SCAA
11. SACA
12. SAAC


**2- Considere a palavra "SISTEMA". Quantos anagramas (arranjos das letras) podemos formar?**

- n = 7 letras
- 'S' repete 2 vezes (r₁ = 2)

$$P(7;2)=\frac{7!}{2!}=2520$$

---


# Combinação:

Uma **combinação** refere-se à **seleção** de itens de um conjunto maior onde a **ordem da seleção não importa** . A palavra-chave é **seleção** (ou escolha, ou formação de um grupo). Se você seleciona os mesmos itens, mas em uma ordem diferente, ainda é considerada a mesma combinação.

#### 1. Combinação Sem Repetição
É a seleção de um subconjunto de itens distintos de um conjunto maior, onde a ordem em que os itens são escolhidos não altera o subconjunto formado. Cada item pode ser escolhido no máximo uma vez para formar um subconjunto específico.

#### Fórmula:

### $$C(n,k) = \frac{n!}{k!(n-k)!}$$
Onde:
- n = número total de itens disponíveis.
- k = número de itens a serem escolhidos.
(A divisão por k! remove as duplicatas que surgiriam se a ordem importasse (como nas permutações).)

##### Exemplos:

**Imagine que você tem um grupo de 4 amigos: Ana (A), Bruno (B), Carlos (C) e Daniela (D). Você quer escolher 2 amigos para ir ao cinema com você. Quantos grupos diferentes de 2 amigos você pode formar?**

- Itens disponíveis: {A, B, C, D}
- Número total de itens (n) = 4
- Número de itens a serem escolhidos (k) = 2
(A ordem não importa: escolher {Ana, Bruno} é o mesmo que escolher {Bruno, Ana}.)

$$C(4,2)=\frac{4!}{2!(4-2)!} = 6$$

Possíveis combinações (grupos de 2):
1. {Ana, Bruno}
2. {Ana, Carlos}
3. {Ana, Daniela}
4. {Bruno, Carlos}
5. {Bruno, Daniela}
6. {Carlos, Daniela}