#faculdade #resumos #calc_numerico #formulario 
# Interpolação polinomial

### 1. Significado:
→  A interpolação tem como objetivo de realizar ou facilitar certas operações. Substituindo uma função f(x) por uma g(x).
→ Usada quando temos funções com operações muito difíceis ou impossíveis de serem resolvidas.
→ Quando se conhece somente os valores numéricos da função para um conjunto de pontos e é necessário calcular o valor da função em um ponto não tabelado.


## Conceito e Aplicação

A interpolação polinomial é um método para aproximar uma função complexa \( f(x) \) usando um polinômio \( P(x) \) que passa exatamente pelos pontos que já conhecemos. Em outras palavras, quando temos um conjunto de pontos conhecidos, podemos criar um polinômio que "interpolará" esses pontos, isto é, que terá os mesmos valores da função original em cada um deles.

---

### Conceito Básico

- **Definição:**  
  Se \( f(x) \) é definida em \( n+1 \) pontos distintos \( x_0, x_1,…, x_n \), então existe um polinômio \( P(x) \) de grau menor ou igual a \( n \) tal que:

  $$  
  P(x_i) = f(x_i) \quad \text{para cada } i=0,1,\dots,n.  
  $$  

  Esse polinômio \( P(x) \) é chamado de **polinômio interpolador**.

- **Objetivo:**  
  O polinômio \( P(x) \) serve como uma aproximação ou substituto da função \( f(x) \) nos pontos onde seu valor é conhecido, facilitando o cálculo e a análise.


---

### Exemplos Práticos

- **4 Pontos:**  
  Se você tem 4 pontos conhecidos da função \( f(x) \), pode interpolar esses pontos com um polinômio de grau no máximo 3.

- **3 Pontos:**  
  Para 3 pontos, o polinômio interpolador terá grau no máximo 2.

- **2 Pontos:**  
  Com 2 pontos, o polinômio será de grau no máximo 1, ou seja, uma reta que passa pelos dois pontos.


### Passos para  resolver

- Analisar a tabela, identificar a quantidade pontos.

**Exemplo:**

|  x   | -1  |  0  |  3  |
| :--: | :-: | :-: | :-: |
| f(x) | 15  |  8  | -1  |

**Pontos**:
(x,y) → (-1,15); (0,8); (3,-1).

**Temos o polinômio genérico:**

$$P(x) = A_0 + A_1x + A_2x^2$$

**Precisamos encontrar os valores de A0, A1, A2. Para isso, basta pegar os pontos e substituir na função de P(x).**

**Exemplo:**

![[1.png]]

**Substitui A0 nas outras equação, para formar um sistema de equações:**

![[2.png]]

![[3.png]]

**Após resolver o sistema, devemos substituir a variável encontrada em uma das equações iniciais.**

![[4.png]]

**Sendo assim, encontramos os valores de A0, A1 e A2. Basta substituir estes valores no polinômio genérico para achar a função interpoladora:**

![[5.png]]

**Após isso, basta substituir pelo ponto a ser encontrado:**

![[6.png]]

---

# Fórmula interpolatória de Lagrange

### Motivo:
→ A determinação do polinômio de interpolação por meio da solução de sistemas é muito trabalhosa.

### Notação:

### Polinômio de Lagrange de ordem 2:

**Tabela:**

| xi    | x₀  | x₁  | x₂  |
| ----- | --- | --- | --- |
| f(xi) | y₀  | y₁  | y₂  |

**Podemos definir os polinômios de Lagrange:**

$$
L_0(x) = \frac{(x - x_1)(x - x_2)}{(x_0 - x_1)(x_0 - x_2)}
$$

$$
L_1(x) = \frac{(x - x_0)(x - x_2)}{(x_1 - x_0)(x_1 - x_2)}
$$

$$
L_2(x) = \frac{(x - x_0)(x - x_1)}{(x_2 - x_0)(x_2 - x_1)}
$$

O polinômio de Lagrange de ordem 2 é:

$$
P_2(x) = y_0 L_0(x) + y_1 L_1(x) + y_2 L_2(x)
$$



### Polinômio de Lagrange de ordem 3:

**Obs: Dado uma tabela de 4 itens podemos usar todos os ponto**

| xi  | x₀  | x₁  | x₂  | x₃  |
|-----|-----|-----|-----|-----|
| f(xi) | y₀  | y₁  | y₂  | y₃  |

**Podemos definir os polinômios de Lagrange:**

$$
L_0(x) = \frac{(x - x_1)(x - x_2)(x - x_3)}{(x_0 - x_1)(x_0 - x_2)(x_0 - x_3)}
$$

$$
L_1(x) = \frac{(x - x_0)(x - x_2)(x - x_3)}{(x_1 - x_0)(x_1 - x_2)(x_1 - x_3)}
$$

$$
L_2(x) = \frac{(x - x_0)(x - x_1)(x - x_3)}{(x_2 - x_0)(x_2 - x_1)(x_2 - x_3)}
$$

$$
L_3(x) = \frac{(x - x_0)(x - x_1)(x - x_2)}{(x_3 - x_0)(x_3 - x_1)(x_3 - x_2)}
$$

O polinômio de Lagrange de ordem 3 é:

$$
P_3(x) = y_0 L_0(x) + y_1 L_1(x) + y_2 L_2(x) + y_3 L_3(x)
$$

