## Objetivo:

Até agora estudamos o comportamento de capacitores e indutores e como eles fazem com que uma das saídas (tensão ou corrente) variem com relação ao tempo.

O objetivo dessa matéria é o de estudar essas curvas em seus regimes transitórios e identificar as funções que descrevem o comportamento da curva.

Os circuitos abordados nessa parte da matéria, normalmente envolvem o indutor ou capacitor, ligados a algum elemento que armazena energia.

---

### Relembrando o comportamento de capacitores:

![[Pasted image 20250531193932.png]]

- A corrente no capacitor assume um valor de pico enquanto o capacitor carrega.
- A tensão do capacitor aumenta gradualmente


### Relembrando o comportamento de indutores:

![[Notes/Faculdade/Disciplinas/Circuitos elétricos/módulo 3/Imgs/Pasted image 20250326205503.png]] 2020250326205503


---

## Estudando os tipos de circuitos de primeira ordem:


### 1. Circuito RC sem fonte

![[Pasted image 20250531194734.png]]

- Capacitor de capacitância C e resistor de resistência R
- Capacitor inicialmente carregado com uma tensão $V_C(0)$

**Encontrar a função que descreve o comportamento da corrente que passa pelo resistor $I_r$ quando a chave é fechada em t = 0**

No instante que a chave fecha, temos a seguinte situação:

### $$V_c=V_r$$
### $$-(\frac{1}{C}\int{i_R(t)dt})=R \cdot i_r (t)$$
- Colocado sinal negativo para indicar que o capacitor está sendo descarregado.

**Reorganizando a expressão, vamos obter uma EDO!**
(Uma EDO é uma equação que apresenta uma função e suas derivadas / integrais em relação a uma variável, no caso deste exemplo, o tempo!)
(EDOs que contem somente uma derivada / integral são caracterizadas como equações de primeira ordem.)
### $$\frac{1}{C}\int{i_R(t)dt} +R \cdot i_r (t)=0$$
**Resolvendo a EDO:**

![[Pasted image 20250531195905.png]]

![[Pasted image 20250531195950.png]]

**Obtendo a tensão:**

![[Pasted image 20250531200509.png]]

#### Atribuindo valores e montando o gráfico:

![[Pasted image 20250531200604.png]]



### 2. Circuito RL sem fonte:

![[Pasted image 20250531200757.png]]

- Indutor de indutância L e resistor de resistência R
- O indutor está inicialmente carregado com uma corrente $i_L(t=0)$

**Encontrar a função que descreve o comportamento da corrente que passa pelo resistor $i_r(t)$ e a tensão $V_r(t)$ quando a chave é fechada em t = 0**

No instante que a chave fecha, temos a seguinte situação:
### $$V_R = V_L$$

![[Pasted image 20250531201241.png]]

![[Pasted image 20250531201321.png]]


### 3. Circuito RC em séria com fonte:

![[Pasted image 20250531202210.png]]

- Fonte de valor $V_f$.
- Capacitor de capacitância C e resistor de resistência R.
- Capacitor inicialmente descarregado.

**Encontrar a função que descreve o comportamento da corrente que passa pelo circuito $i(t)$, a tensão $V_r(t)$ e a tensão $V_c(t)$ quando a chave é fechada em t = 0**

No instante que a chave fecha, temos a seguinte situação:

### $$V_f= V_r+V_c$$
![[Pasted image 20250531202703.png]]

![[Pasted image 20250531202732.png]]

![[Pasted image 20250602160743.png]]

![[Pasted image 20250531202822.png]]

![[Pasted image 20250531202841.png]]


### 4. Circuito RL em série com fonte

![[Pasted image 20250531203227.png]]

- Fonte de valor $V_f$
- Indutor de indutância L e resistor de resistência R
- O indutor está inicialmente descarregado

**Encontrar a função que descreve o comportamento da corrente que passa pelo circuito $i(t)$, a tensão $V_r(t)$ e a tensão $V_L(t)$ quando a chave é fechada em t = 0**

No instante que a chave fecha, temos a seguinte situação:


### $$i_R(t)=i_L(t)$$
![[Pasted image 20250531203606.png]]
![[Pasted image 20250531203647.png]]


---

## Problemas do circuito RC e RL em paralelo:

![[Pasted image 20250531205349.png]]

- Ao fechar a chave, um pico de corrente tendendo ao infinito passa pelo capacitor
- Em regime permanente o indutor vira um curto circuito sobre os terminais da fonte


---

## Análise do termo $e^{-at}$

- Varia entre 1 (inicialmente carregado) quando $e^0=1$ até 0 (regime estacionário)
- Pode ser visto na forma de % quando comparado ao valor final.
- Apresenta uma constante de tempo **τ** que define a rapidez com que a resposta transitória ocorre.
**Regime estacionário:** o circuito atinge o regime estacionário após aproximadamente 4τ a 5τ.

![[Pasted image 20250531221029.png]]

**Calculo do τ para os circuitos:**

![[Pasted image 20250531221125.png]]


---

## Circuito RLC em série com a fonte

- Capacitor de capacitância C, indutor de indutância L e resistor de resistência R.
- Tensão da fonte $V_f$.
- O capacitor e o indutor estão inicialmente descarregados.

![[Pasted image 20250531221528.png]]

**Como a tensão Vc varia em regime transitório?**

Usando LKT:

![[Pasted image 20250531221704.png]]

→ Chegamos a uma equação diferencial ordinária de segunda ordem, esta é muito difícil de resolver.

![[Pasted image 20250531221807.png]]

### Analise do comportamento da saída a partir do valor da capacitância C:

![[Pasted image 20250531221926.png]]

#### Gráfico:

![[Pasted image 20250531221947.png]]

