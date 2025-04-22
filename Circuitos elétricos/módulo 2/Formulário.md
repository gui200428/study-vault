#faculdade #resumos #circuitos 
## Capacitores

### Capacitância (F)


$$C=\frac{q}{V}$$
$$C[F]=\frac{ε[?]A[m^2]}{d[m]}$$
- q Carga (C)
- V tensão(V)
- Area (m2)
- Distancia (m)


| Símbolo |   Notação    |
| :-----: | :----------: |
|    F    |      -       |
|   mF    | ${10}^{-3}$  |
|   uF    | ${10}^{-6}$  |
|   nF    | ${10}^{-9}$  |
|   pF    | ${10}^{-12}$ |
### Carga → Capacitor

$$Q = C.V$$

$$dq = C.dV$$

$$i=\frac{dq}{dt}$$

### Corrente → Capacitor

$$i(t)=C\frac{dV(t)}{dt}$$
- Varia quando o capacitor é carregado / descarregado


### Tensão acumulada

$$V(t)=\frac{1}{C}\int_{t0}^{t} i(t)dt$$
Depende do acumulo da corrente

![[Pasted image 20250224190254.png]]

![[Pasted image 20250224193518.png]]

### Energia acumulada

$$E=\frac{CV^2}{2}$$
### Regime estacionário

→ Circuito aberto
→ I = 0 // n corrente malha
→ Vc = Vf = 0.

### Associação de capacitores

### Serie:
→ Tensão se divide (Menor capacitancia, Maior tensão)
→ Carga igual a carga total

$$V=\frac{Q}{C}$$


$V_{total} = V_1 + V_2 + ... + V_n$
$Q_{total} = Q_1 = Q_2 = ... = Q_n$

$$
\frac{1}{Ceq} = \frac{1}{C_1}+\frac{1}{C_2}+...+\frac{1}{C_n}
$$



$$
Ceq=\frac{C_1C_2}{C_1+C_2}
$$

### Paralelo
→ Tensão é igual
→ Carga divide, diretamente proporcional a capacitancia.
→ Maior capacitancia, maior carga
$$Q = C.V$$
$V_{total} = V_1 = V_2 = ... = V_n$
$Q_{total} = Q_1 + Q_2 + ... + Q_n$

$$
Ceq = C_1+C_2+...+C_n
$$

---

## Indutores

**Gráfico da corrente e tensão sobre o indutor**
![[Pasted image 20250326205343.png]]


### Regime estacionário
→ Indutor carregado
→ Circuito aberto
→ Tensão = 0
→ Corrente depende da tensão pela resistência: $I_i=\frac{V_f}{R}$
→ **energia armazenada nos indutores** a partir da corrente elétrica que passa sobre eles.

### Indutância
→ Determina quanto o indutor resiste a passagem de corrente

$$
L[H]=\frac{N^2μ[?]A[m^2]}{l[m]}
$$

**Sendo:**
- L: Indutância, medida em Henrys (H)
- N: Número de espiras
- μ: Permeabilidade do núcleo (H/m)
- A: Área da secção transversal ($m^2$)
- l: Comprimento do indutor ($m$)

**Permeabilidade**
$$μ=μ_rμ_0$$
$μ_r$ : Permeabilidade relativa, Fator de multiplicação (No vácuo, $μ_r$ = 1) 
$μ_0$ : Permeabilidade nominal no valor $4𝝿*10^{-7}$ H/m


### Tensão em indutores:

$$
V(t) = L.\frac{di(t)}{dt}
$$

### Corrente em indutores - Variação
$$
i(t)-i(t_0)=\frac{1}{L}\int_{t0}^{t}V(t)\space dt
$$
### Energia acumulado por um indutor
$$
E = \frac{Li^2}{2}
$$

### Associação de indutores

### Série
→ Corrente é a mesma
→ N tem tensão
$$Leq=L_1+L_2+...+L_n$$
### Paralelo
→ A corrente se divide igualmente para cada indutor.
→ Não tem tensão.

$$\frac{1}{Leq}=\frac{1}{L_1}+\frac{1}{L_2}+...\frac{1}{L_n}$$

$$Leq=\frac{L_1L_2}{L_1+L_2}$$




