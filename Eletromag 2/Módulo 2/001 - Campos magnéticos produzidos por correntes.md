
## Fontes de campo magnético:

## 1. Partículas fundamentais:

Campo magnético pode ser produzido por partículas fundamentais.
## Elétron
- Massa
- Carga
- **Campo magnético**

## Partícula em movimento:

![[Pasted image 20260513190527.png]]

- Partículas eletricamente carregas **em movimento** como os elétrons, responsáveis pela corrente elétrica em um fio.

## 2. Objetivo de estudo: Fio condutor com fluxo de cargas

- Cada carga gera um campo magnético.
- O fluxo de cargas gera um campo relevante para o estudo.


### Evidência experimental

Partículas carregadas em movimento produzem campos magnéticos em um ponto do espaço.  

![[Pasted image 20260523110525.png]]

**Relações:**

1. Campo magnético (B) é proporcional à carga (q)
2. Campo magnético (B) é proporcional a velocidade
3. Campo magnético (B) é inversamente proporcional ao quadrado da distancia (r) da carga até o ponto P. (Quanto maior a distancia (r), menor o campo magnético) (Ex: r = 3m → $\frac{B}{3^2}$ → B/9))
4. Campo magnético (B) é proporcional ao sen($\theta$), sendo que $\theta$ é o ângulo entre o vetor da velocidade e o vetor da distancia.
5. Campo magnético (B) máximo: quando o ângulo for 90 graus ou 270 graus
6. Campo magnético (B) mínimo: quando o ângulo for 0 graus 

---

## Lei de Biot Savart

### Campos magnéticos produzidos por correntes em um fio


![[Pasted image 20260523114109.png]]

Cada ponto do fio, gera um campo magnético.
**Campo magnético contorna o fio**
### Direção e sentido do campo magnético.

**Regra da mão direita:**

- Apontar o polegar no sentido da corrente.
- O outros dedos mostram a orientação das linhas de campo magnético produzidos pela corrente no fio.


![[Pasted image 20260523114358.png]]


### Lei de Biot Savart

**Objetivo:** Calcular o campo magnético de um pedaço de fio passando corrente.

![[Pasted image 20260523114748.png]]
![[Pasted image 20260523115044.png]]
### $\mu_0$ - Constante de permeabilidade magnética do vacuo

**Sendo:**
i = Corrente que passa pelo fio
$d \vec{s}$ = Pequeno pedaço do fio ← Somar todos os pedaços para encontrar o campo total
r = Distancia até o ponto P ← Quanto mais longe do fio, mais fraco o campo magnético


## Aplicação - Fio reto

![[Pasted image 20260523120040.png]]

**Análise:**
- Campo entrando no ponto P

#### **Aplicando a fórmula:**
![[Pasted image 20260523120252.png]]

**Termos:**
### $d\vec{s}$ ← Pedaço de fio. 
- Posição do fio: Y → J^
- Pequeno pedaço do fio: dyj^ ← pedaço do y na direção j. (positivo pois a corrente flui para +y)

$d\vec{s}$ = dyj^

### d$\vec{B}$  ← Pedaço do campo.
- Campo entrando: -K^
- $d\vec{B}$ = -$d\vec{B}$k^


### $\vec{r}$ ← Distancia reta entre d$\vec{s}$ até o ponto.

### $$\vec{r}=\vec{r}_p-\vec{r′}$$
![[Pasted image 20260523122729.png]]

![[Pasted image 20260523122748.png]]

Módulo do vetor r:

![[Pasted image 20260523122807.png]]


### Desenvolvendo produto vetorial:

![[Pasted image 20260523123001.png]]


### Montando a relação:

![[Pasted image 20260523123216.png]]


### Resolvendo a integral para achar o campo magnético do fio reto:

![[Pasted image 20260523123408.png]]

### $$\vec{B}=-\frac{\mu_0i}{4\pi x}[\frac{b}{\sqrt{x^2+b^2}}+\frac{a}{\sqrt{x^2+a^2}}]\hat{k}$$
**Sendo:**
- a = extensão do fio abaixo da origem (o fio vai até y=−a).
- b = extensão do fio acima da origem (o fio vai até y=+b).
- i = corrente.
- x = distancia perpendicular do fio até o ponto. ($\vec{r}_p$ seguindo o desenho)


**Nota: Como identificar $a$, $b$ e $x$ na fórmula do fio finito**

Para qualquer orientação do fio, siga os passos:

1. Encontre o **pé da perpendicular** de P até o fio (o ponto do fio mais próximo de P).
2. Meça quanto de fio há para **cada lado** desse ponto → esses são $a$ e $b$.
3. Meça a **distância perpendicular** de P até o fio → esse é $x$.

$a$ e $b$ são sempre **positivos** — o sinal negativo da extensão inferior já está embutido na fórmula.

> **Dica:** Trate o pé da perpendicular como sua origem local. Independente do eixo em que o fio estiver, a lógica é sempre a mesma.