
**1- Sinais de tempo continuo ou discreto**
**2- Sinais analógicos ou digitais**
**3- Sinais periódicos e não periódicos**
4- Sinais de energia ou potencia 
5- Sinais determinísticos ou probabilísticos


---

## Sinais de tempo continuo

→ É um sinal continuo ao longo da variável tempo. O sinal é definido para todos os instantes de tempo.

![[Pasted image 20250927092544.png]]


## Sinais em tempo discreto

→ É um sinal quantizado na variável tempo. Ele apresenta valores específicos em um intervalo de tempo definido. O sinal apresenta valores somente em tempos intervalos de tempo. Uma sequencia de números. 

![[Pasted image 20250927092827.png]]


## Sinal analógicos

→ Representa as grandezas físicas do mundo real. Tempo continuo e amplitude continua.

![[Pasted image 20250927094740.png]]


## Sinal digital

→ É um sinal discreto no tempo e quantizado na amplitude. Sequencia de valores definidas tanto para o tempo quanto para a amplitude do sinal.

![[Pasted image 20250927094941.png]]


## Sinais periódicos

→ Sinal de duração indeterminado, se repete ao longo do tempo. E segue a definição de:

#### $$X(t) = X(t + T)$$
→ X(t): Amplitude do sinal
→ T é o período do sinal. Representa o comprimento de um ciclo completo do sinal.

![[Pasted image 20250927100221.png]]


## Sinais não-periodicos 

→ Sinal de duração finita

![[Pasted image 20250927100458.png]]



## Sinal de energia

→ Sinal que possui a energia finita

## Sinal de potencia

→ Sinal que possui a potencia finita

## Sinal determinístico

→ Modelos físicos

## Sinal probabilístico

→ Modelos estatísticos

---

# Funções uteis de sinais

## 1- Função degrau unitário

→ Representada por u(t). Possui as seguintes condições:

![[Pasted image 20250927101342.png]]

**Representação gráfica:**
![[Pasted image 20250927101605.png]]

**Atraso de 1 segundo na função:**

![[Pasted image 20250927101821.png]]

**Adiantamento de 2 segundos:**

![[Pasted image 20250927101843.png]]

### Operações com degraus unitários: 

![[Pasted image 20250927103454.png]]

→ Para resolver esse problema, o primeiro passo é resolver os dois degraus unitários separadamente.

**1- u(t-1)**

t - 1 = u(t)
t - 1 = 0
t = 1 ← gráfico vale 1 quando tempo = a 1.

![[Pasted image 20250927103600.png]]

**2- -u(t-5)** 
→ Como o ‘u’ é negativo, basta desenhar o gráfico do lado negativo.

t - 5 = 0
t = 5 ← Gráfico vale -1 quando tempo = 5.

![[Pasted image 20250927103707.png]]

**3- Juntar os gráficos!**
→ Para fazer isso, precisamos realizar o seguinte estudo:

$- \infty$ até 0, os dois gráficos valem 0. → 0 + 0 = 0, então gráfico resultante = 0 em t = 0

1 até 5, o primeiro vale 1 e o segundo vale 0. → 1 + 0 = 1, então o gráfico resultante = 1 em t = 1

5 até $+ \infty$, o primeiro vale 1 e o segundo vale -1. → 1 + -1 = 0, então o gráfico resultante = 0 em
t = 5.

**Resultado: Pulso retangular!**

![[Pasted image 20250927113305.png]]

---

### Multiplicação de sinais

→ Basta sobrepor os sinais e mesclar!

→ Dado um sinal y(t), como seria o grafico y(t) * x(t)?

![[Pasted image 20250927113707.png]]


---

## Função impulso unitário ou delta de Dirac

**Propriedades:**


![[Pasted image 20250927115449.png]]


**Representação gráfica:**

![[Pasted image 20250927115746.png]]

### Operações com a delta de Dirac:

![[Pasted image 20250927120030.png]]

![[Pasted image 20250927120105.png]]

### Propriedade da delta de Dirac:


![[Pasted image 20250927120230.png]]

