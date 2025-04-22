#faculdade #resumos #calc_numerico #formulario 
# Interpolados por Lagrange

## Polinômio  de ordem 2

**→ 3 pontos $X_0$, $X_1$ e $X_2$**

### $$L_0(x)=\frac{(x-x_1)(x-x_2)}{(x_0-x_1)(x_0-x_2)}$$
### $$L_1(x)=\frac{(x-x_0)(x-x_2)}{(x_1-x_0)(x_1-x_2)}$$
### $$L_2(x)=\frac{(x-x_0)(x-x_1)}{(x_2-x_0)(x_2-x_1)}$$
### $$P_2(x)=y_0L_0(x)+y_1L_1(x)+y_2L_2(x)$$
## Polinômio de ordem 3

**→ Quando se tem 4 pontos, $X_0$, $X_1$, $X_2$, $X_3$**

### $$L_0(x)=\frac{(x-x_1)(x-x_2)(x-x_3)}{(x_0-x_1)(x_0-x_2)(x_0-x_3)}$$
### $$L_1(x)=\frac{(x-x_0)(x-x_2)(x-x_3)}{(x_1-x_0)(x_1-x_2)(x_1-x_3)}$$
### $$L_2(x)=\frac{(x-x_0)(x-x_1)(x-x_3)}{(x_2-x_0)(x_2-x_1)(x_2-x_3)}$$
### $$L_3(x)=\frac{(x-x_0)(x-x_1)(x-x_2)}{(x_3-x_0)(x_3-x_1)(x_3-x_1)}$$
### $$P_3(x)=y_0L_0(x)+y_1L_1(x)+y_2L_2(x)+y_3L_3(x)$$
## Termo geral - Polinômio de Lagrange de ordem $n$

**→ Para $n$ numeros, a ordem serão sempre “n-1”**

### $$L_i(x)= \frac{(x - x_0)(x - x_1)\cdots(x - x_{i-1})(x - x_{i+1})\cdots(x - x_n)}{(x_i - x_0)(x_i - x_1)\cdots(x_i -x_{i-1})(x_i - x_{i+1})\cdots(x_i - x_n)}.$$
- - - 

# Polinomio  interpolador de Newton


|     | X   | Ordem 0 | Ordem 1                         | Ordem 2                           | Ordem 3                            |
| --- | --- | ------- | ------------------------------- | --------------------------------- | ---------------------------------- |
| X0  | 1   | 0       |                                 |                                   |                                    |
|     |     |         | f[x0,x1]=$\frac{6-0}{3-1}=3$    |                                   |                                    |
| X1  | 3   | 6       |                                 | f[x0,x1,x2]=$\frac{18-3}{4-1}=5$  |                                    |
|     |     |         | f[x1,x2]=$\frac{24-6}{4-3}=18$  |                                   | f[x0,x1,x2,x3]=$\frac{9-5}{5-1}=1$ |
| X2  | 4   | 24      |                                 | f[x1,x2,x3]=$\frac{36-18}{5-3}=9$ |                                    |
|     |     |         | f[x2,x3]=$\frac{60-24}{5-4}=36$ |                                   |                                    |
| X3  | 5   | 60      |                                 |                                   |                                    |

## Montando o polinômio

### $$P(x)= 0 + 3(x-1) + 5(x-1)(x-3) + 1(x-1)(x-3)(x-4)$$
### $$P(x)=x^3-3x^2-2x$$
- - - 

# Interpelação linear 

**Interpolação com dois pontos $X_0$ e $X_1$**
## Métodos:
**Pode ser resolvida com:**
1. Lagrange
2. Newton

## Lagrange:

### $$L_0(x)=\frac{x-x_1}{x_0-x_1}$$
### $$L_1(x)=\frac{x-x_0}{x_1-x_0}$$
### $$P_1(x)=y_0L_0(x)+y_1L_1(x)$$
---

# Interpolação inversa

**Quando temos o valor de F(x) e queremos saber o valor de X**

## Método de resolução

**Inverter a tabela:**
![[Pasted image 20250323005324.png]]
![[Pasted image 20250323005554.png]]

**Resolver usando newton**

![[Pasted image 20250323005800.png]]

**Encontrar o ponto por briot ruffini**
![[Pasted image 20250323005813.png]]

- - -

# Cálculo do erro na interpolação

**Descobrir quantas casas acertamos na interpolação**

## Fórmula

![[Pasted image 20250323010554.png]]


## Método de resolução

1. Identificar o número de pontos
2. Calcular a derivada da função $f^{n+1}(x)$
3. Calcular o M:
4. Pegar os pontos escolhidos
5. Substituir na derivada
6. Pegar o maior valor (esse é o M)
7. Substituir os pontos na fórmula do erro
8. O número de casas decimais depois da virgula, é o numero de casas decimais corretas.
9. **Importante $n$ começa contando a partir do 0, Ex: x0, x1, x2. Então n = 2**



![[Pasted image 20250323011657.png]]

![[Pasted image 20250323011752.png]]

![[Pasted image 20250323011816.png]]

![[Pasted image 20250323011839.png]]

