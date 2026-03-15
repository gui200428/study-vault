
## Tipos de conexão:

- **Emissor comum (EC)**
- **Coletor comum (CC)**
- **Base comum (BC)**

**OBS:** Conexão mais usada é a Emissor comum.



## Emissor comum:

![[Pasted image 20260314171057.png]]

Nesta configuração, temos o GND de cada fonte conectado ao emissor.

**Analise do circuito:**
O circuito apresenta duas malhas:
→ Malha da base
→ Malha do coletor

**Malha da base:**
→ Fonte de tensão da base (Vbb): Polariza o diodo emissor diretamente com $Rb$:
São responsáveis por “Abrir o caminho para a corrente do Vcc passar”
→ Variar ($V_{BB}$) ou ($R_B$) → varia corrente da base.
→ Variar corrente da base → **varia corrente do coletor** (Amplificador!)
→ **Corrente da base controla a corrente do coletor:** corrente baixa controla corrente alta!

**Malha do coletor:**
→ Fonte de tensão do coletor (Vcc): Polariza reversamente o diodo do coletor com o ($R_C$).
Fonte principal que alimenta a carga do sistema.
→ Coletor positivo para coleta os elétrons livres injetados na base.



![[Pasted image 20260314172855.png]]


## Curva da base:

Gráfico ($I_B$ x $V_{BE}$) → Parecido com a curva do diodo:

![[Pasted image 20260314173247.png]]

Aplicando a lei de Ohm no resistor da base:

### $$I_B = \frac{V_{BB}-V_{BE}}{R_B}$$
**Aproximações:**

Diodo ideal: $V_{BE} = 0$ 
Diodo real: $V_{BE}=0,7$ 

**Mais usado: diodo real.**

