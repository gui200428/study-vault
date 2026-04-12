
## Objetivo geral:

- Prever a resposta de um sistema dinâmico de primeira e segunda ordem
- Dado uma EDO com condições iniciais, resolver e achar uma solução

![[Pasted image 20260407145210.png]]



## Solução geral:

→ A solução geral desse tipo de equação é descrita por:

### $$y(t)=y_H(t) + y_P(t)$$
**Sendo:**

$y_H$: Solução da equação homogênea

$y_P$ Solução particular



## Método passo a passo para resolução:

**Objetivo:** Encontrar: $$y(t)=y_H(t) + y_P(t)$$

### 1- Equação homogênea:
→ Chamar Y ou X de Xh ou Yh e igualar a equação a 0.


### 2- Polinômio característico:

![[Pasted image 20260407145802.png]]

![[Pasted image 20260407145838.png]]

### 3- Resolver a equação
→ Encontrar o valor de r.

### 4- Substituir os valores de r para a equação característica geral:


![[Pasted image 20260407150144.png]]


**Caso importante:**

![[Pasted image 20260407150219.png]]


### 5- Encontrar a solução particular
- Depende do formato da entrada.
- Observar o valor da direita (f(t)) e comparar com a tabela

![[Pasted image 20260407150708.png|459]]


- Dado o valor Yp da tabela, aplicar as derivadas para encontrar os valores derivados de Y ou X na equação original.


### 6 - Com os valores de Yp ou Xp  e suas derivadas, voltamos na equação original e substituímos por esses valores

- Encontramos os valores de A ou de A e B para a equação
- Substituimos os valores de A e B encontrados em Yp(t) da tabela
- **Encontramos nossa solução particular Yp**

### 7 - Montar a solução geral
- Montamos a solução geral:

### $$y(t) = y_H + y_P$$
### 8- Aplicar o valor da condição inicial para achar o termo C da equação


### 9 - Montar a equação da solução geral com o valor de C







## Casos importantes:

### Todas as raízes “r” diferentes

![[Pasted image 20260407174126.png]]


### Duas raízes “r” iguais (r1 = r2)

![[Pasted image 20260407174201.png]]



## Resumindo:


![[Pasted image 20260407174226.png]]

