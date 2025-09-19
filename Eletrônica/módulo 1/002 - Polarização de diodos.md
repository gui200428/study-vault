
## Polarização direta

→ Conecta o ânodo do diodo ao terminal positivo da fonte e o cátodo ao terminal negativo da fonte. Vamos estudar como a corrente vai se comportar.

![[Pasted image 20250917170717.png]]

→ A fonte fornece mais elétrons para o material N (Negativo) e mais lacunas para o material P (Positivo).

![[Pasted image 20250917170850.png]]

→ Se a tensão da fonte for maior que a tensão de polarização do diodo, a força de atração entre as cargas consegue vencer a camada de depleção, conduzindo corrente do ânodo para o cátodo.

→ O diodo entra no estado de **condução** e não se opões a passagem de corrente. (Constante que a tensão de polarização continue sendo “Compensada”).

![[Pasted image 20250917171333.png]]

### Representação gráfica:

→ Como o circuito não possui nenhuma resistência, é esperado que a curva da corrente pela tensão cresça rápido a partir do momento que a fonte supera a tensão de polarização do diodo. 

→ Isso mostra a capacidade de um diodo semicondutor de alterar de forma rápida entre um circuito aberto (Região de corte) e um circuito fechado (Região de condução).

![[Pasted image 20250917171818.png]]


---
## Polarização reversa

→ Conecta o ânodo no negativo da fonte e o cátodo no positivo da fonte. Vamos inverter os terminais da fonte!

![[Pasted image 20250917173658.png]]

→ A fonte fornece elétrons para o material P (Positivo) e lacunas para o material N (Negativo), isso provoca o aumento da camada de depleção

![[Pasted image 20250917173828.png]]


→ A troca de cargas para manter o equilíbrio da camada de depleção cria uma pequena corrente negativa (do catodo para o ânodo) chamada de **corrente de saturação reversa**

![[Pasted image 20250917174042.png]]


### Representação gráfica:

→ A curva na região em que a tensão é menor que zero, permanece constante. Porem com o aumento da tensão de polarização reversa pode levar ao ponto de ruptura. (Situação em que o semicondutor não suporta a tensão gerada pela camada de depleção, queimando o componente).

![[Pasted image 20250917174320.png]]


### Junção dos dois gráficos:

![[Pasted image 20250917174448.png]]

---

## Diodo + resistor

→ Analise do comportamento de um diodo em série com um resistor.

![[Pasted image 20250917175157.png]]


**Situação 1:** Tensão da fonte inferior a tensão de polarização do diodo:
→ O diodo se comporta como circuito aberto
→ Não tem passagem de corrente

![[Pasted image 20250917175326.png]]

**Situação 2:** Tensão da fonte superior à tensão de polarização do diodo (Vd):
→ Diodo se torna um circuito fechado que “segura” a tensão de polarização do diodo
→ Tensão no resistor Vr vai ser a tensão da fonte menos a tensão de polarização Vr = (V - Vd).
→ A corrente não cresce exponencialmente, mas de forma linear seguindo a lei de ohm.

**O resistor “limita” a corrente sobre o circuito**

![[Pasted image 20250917180705.png]]

**Gráfico:**

![[Pasted image 20250917180023.png]]
![[Pasted image 20250917180452.png]]

![[Pasted image 20250917180813.png]]


→ O diodo acrescenta um comportamento não linear no circuito, que permite que ele trabalhe de duas formas:

**1. Região de corte (V < Vd)**
**2. Região linear (V > Vd)**

![[Pasted image 20250917180833.png]]




