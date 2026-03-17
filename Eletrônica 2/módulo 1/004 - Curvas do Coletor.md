
#faculdade #eletronica_2 #resumos 

---
## Circuito:

![[Pasted image 20260314174103.png]]

**Variações:**
- Variar a $V_{BB}$ e a $V_{CC}$ → Produz diferentes valores de tensão e corrente no transistor.
- Medir $I_C$ e $V_{EC}$ → produz um gráfico $I_C$ X $V_{EC}$

**Exemplo:**
Variação da corrente de base ($V_{BB}$)
Com $I_B = 10 \micro A$

![[Pasted image 20260314174525.png]]

**Analise:**

![[Pasted image 20260314174832.png]]

![[Pasted image 20260314174916.png]]


## Tensão e potência do coletor:

![[Pasted image 20260314175058.png]]

### Aplicando a LKT na malha do coletor:

### $$V_{EC}=V_{CC}-I_CR_C$$

### Potência dissipada em um transistor:

### $$P_D=V_{EC}I_C$$
**Consequências:**
→ Quanto maior a potencia, maior a temperatura na junção do diodo coletor.
→ Todo transistor tem uma $P_D$ máxima.
→ Se $P_D$ > $P_{D(máx)}$ = diodo danificado.


## Região de operação de transistores:

![[Pasted image 20260314225849.png]]

**Região de operação: → $V_{EC}$ está entre 1 e 40V**

**Características:**

- Região ativa
- Operação normal do transistor
- Diodo emissor diretamente polarizado
- Diodo coletor reversamente polarizado
- Coletor captura quase todos os elétrons livres
- Corrente no coletor constante

**Região de ruptura (DIREITA DO GRAFICO)**
- Transistor nunca deve operar nessa região

**Região de saturação:**
- Região do começo → $V_{EC}$ está entre 0 e alguns décimos de 1V.
- Diodo coletor → tensão positiva insuficiente para capturar todos os elétrons livre injetados na base.
- A corrente $I_B$ é maior que a normal e o ganho de corrente $\beta_{CC}$ é menor que o normal.

**Região de corte:**
- Primeira curva → $I_B = 0$ mas existe uma $I_C$
- $I_C$ é desprezada por ser muito baixa
- Baixa corrente $I_C$ → **Corrente de corte do coletor.**

![[Pasted image 20260314230726.png]]

(24/02)