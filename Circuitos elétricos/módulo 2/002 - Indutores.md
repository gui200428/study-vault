#faculdade #resumos #circuitos
### Definição:

→ Um indutor genérico se trata de um enrolado feito com um fio condutor, conhecido como bobina.
→ Quando é aplicado uma tensão, uma corrente sobre o indutor faz com que ele comece a se carregar e armazenar energia por meio do campo magnético gerado sobre a bobina.

![[Pasted image 20250326203018.png]]


### Comportamento de um indutor inicialmente descarregado

→ Conectado a uma fonte de tensão

**Momento 01:**  Chave aberta, portanto o circuito está aberto e não passa nenhuma corrente pelo indutor. $i_{indutor}$ e $V_{indutor}$ são nulas.

![[Pasted image 20250326203511.png]]

→ Chave fechada

**Momento 02 (Regime transitório):** 
→ Imediatamente quando a chave fecha, o indutor se comporta como um circuito aberto por um curto período de tempo. Pois ele resiste a passagem de corrente.
→ A corrente começa a passar pelo indutor.
→ Tensão da fonte está totalmente sobre o indutor (tensão salta para o mesmo valor da tensão da fonte Vf)
→ Ao passar do tempo, a corrente começa a conseguir passar pelo indutor e ele deixa de ser um circuito aberto.

![[Pasted image 20250326205451.png]]

**Gráfico da corrente e tensão sobre o indutor**
![[Notes/Faculdade/Disciplinas/Circuitos elétricos/módulo 2/Imgs/Pasted image 20250326205503.png]]

**Momento 03: (Regime estacionário)**

→ Indutor foi completamente carregado.
→ Indutor passa a ser um curto circuito. Simplesmente um fio conectando os dois terminais da fonte.
→ A tensão sobre ele passa a ser zero. 
→ A corrente estaciona no valor de $I_i=\frac{V_f}{R}$

![[Pasted image 20250326205334.png]]

![[Pasted image 20250326205343.png]]


### Cálculo da indutância:

→ Diferentes indutores vão ser carregados em diferentes tempos, ou seja, cada indutor consegue “resistir” à passagem de corrente elétrica por mais tempo ou menos tempo.
→ É possível dimensionar um indutor por meio da sua indutância **L**..
**Dado pela seguinte relação:**

$$
L=\frac{N^2μA}{l}
$$

**Sendo:**
- L: Indutância, medida em Henrys (H)
- N: Número de espiras
- μ: Permeabilidade do núcleo (H/m)
- A: Área da secção transversal ($m^2$)
- l: Comprimento do indutor ($m$)

![[Pasted image 20250326210403.png]]

A permeabilidade pode ser escrita como:

$$μ=μ_rμ_0$$
**Sendo:**
$μ_r$ : Permeabilidade relativa, Fator de multiplicação (No vácuo, $μ_r$ = 1) 
$μ_0$ : Permeabilidade nominal no valor $4𝝿*10^{-7}$ H/m


**Exemplo:** Um aço de permeabilidade relativa $μ_r$ = 6, possui uma permeabilidade de: 

$$μ = 4𝝿*10^{-7} * 6$$ 
$$μ = 75,4*10^{-7}$$ 

### Tensão em indutores:

→ A tensão sobre um indutor é proporcional à variação de corrente.

$$
V(t) = L.\frac{di(t)}{dt}
$$

→ Tendo a função da corrente, podemos calcular o valor da tensão.
→ Assim, é possível identificar qual é a tensão sobre um indutor a partir da corrente que passa por ele.

## Corrente em indutores

→ Se a função da tensão sobre um indutor for conhecida, é possível achar a função da corrente entre o instante $t_0$ e um instante t qualquer.

$$
i(t)=\frac{1}{L}\int_{t_0}^{t}V(t)dt
$$

→ A constante obtida na integração representa a corrente inicial sobre o indutor (nula, se estava descarregado).
→ Se a corrente inicial não for conhecida, ainda é possível calcular qual foi a variação de corrente $Δi$ entre dois instantes quaisquer.
→ Esta fórmula calcula somente a parte da corrente que foi adicionada (ou subtraída) pela tensão V(t) entre os instantes $t_0$ e $t$. Calcula a mudança na corrente.

### **Formula mais completa:**
### $$i(t)-i(t_0)=\frac{1}{L}\int_{t0}^{t}V(t)\space dt$$
→ Esta fórmula indica a mudança total na corrente entre o tempo $t_0$ e $t$. 
→ A mudança na corrente (Corrente Final - Corrente Inicial) é igual a 1/L vezes a integral da tensão ao longo do tempo.
## Energia acumulado por um indutor

→ Acumula energia por meio da corrente que passa por ele.
→ É possível calcular o acumulo de energia de um indutor em um certo instante.

$$
E = \frac{Li^2}{2}
$$
**Sendo:**
- E: energia acumulada.
- L: indutância
- i: corrente

### Indutores em regime estacionário

→ Em regime estacionário, indutores se comportam como um circuito fechado. Ou seja, não existe tensão passando por ele.

![[Pasted image 20250326232158.png]]


→ Ainda podemos concluir sobre a **energia armazenada nos indutores** a partir da corrente elétrica que passa sobre eles.

![[Pasted image 20250326232409.png]]

### Associação de indutores

→ Indutores podem ser associados em **série** ou em **paralelo**.
→ É possível identificar a **indutância equivalente** de dois ou mais indutores em um circuito

![[Pasted image 20250326232700.png]]

### Indutores em série

→ A corrente é a mesma que passa por todos os indutores
→ Não tem tensão

**Indutância equivalente:**

$$Leq=L_1+L_2+...+L_n$$

![[Pasted image 20250326233022.png]]

### Indutores em paralelo

→ A corrente se divide igualmente para cada indutor.
→ Não tem tensão.

$$\frac{1}{Leq}=\frac{1}{L_1}+\frac{1}{L_2}+...\frac{1}{L_n}$$

$$Leq=\frac{L_1L_2}{L_1+L_2}$$

![[Pasted image 20250326233334.png]]


---
### Próximo conteúdo:

[[Notes/Faculdade/Disciplinas/Circuitos elétricos/módulo 2/Formulário|Formulário]]
