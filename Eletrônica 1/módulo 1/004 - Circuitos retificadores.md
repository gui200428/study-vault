#faculdade #resumos #eletronica 
## Fontes de corrente alternada

**Não tem polaridade, possuem um comportamento senoidal.**

![[Pasted image 20250919122754.png]]


### Comportamento no gráfico:

![[Pasted image 20250919122900.png]]


**Onde:**
- Vp: Tensão de pico [V]


### Tensão de pico x valor eficaz:

→ Sempre trabalhamos com o valor eficaz da fonte, esse valor é usado para cálculos de potência.
→ Para calcular o valor eficaz (RMS) usamos a seguinte fórmula:


Tensão eficaz:
### $$V_{rms}=\frac{Vp}{\sqrt{2}}$$

Tensão de pico:

### $$Vp=V_{rms}*\sqrt{2}$$

![[Pasted image 20250919123424.png]]


**Exemplo de aplicação:**
→ Tomadas residenciais: tensões de 127V e 220V, os valores de pico são 180V e 311V.
→ Além disso, a frequência da rede e de 60 Hz (60 ciclos por segundo).

![[Pasted image 20250919123727.png]]


---

## Transformadores

→ Dispositivos desenvolvidos a partir de indutores, são capazes de elevar ou reduzir a tensão de corrente alternada, conservando a mesma potência de entrada, na saída.

![[Pasted image 20250919123939.png]]


---

## Circuito retificador: Convertendo uma fonte de tensão de corrente alternada em uma fonte de tensão de corrente continua.


![[Pasted image 20250919125041.png]]


### Circuito retificador de meia onda

→ Usa apenas um diodo e um resistor
→ O diodo retificador apenas entra em condução durante o semi-ciclo positivo da tensão de entrada. 
→ A tensão de polarização do diodo faz com que a onda seja ligeiramente menor do que a onda original.

![[Pasted image 20250919162758.png]]

→ Durante o semi-ciclo negativo da tensão de entrada, o diodo corta o circuito e não conduz nada.

![[Pasted image 20250919163004.png]]

→ A tensão produzida na saída do retificador pode ser considerada um tipo de tensão de corrente continua, pois não possui a parte negativa

![[Pasted image 20250919163209.png]]

→ Porem não é o ideal, somente 31,8% é utilizado considerando a área total de uma tensão de corrente continua. Isso implica em perda de potência.

**Processo de filtragem:**
→ Para corrigir o problema das lacunas entre as ondas, podemos fazer a retificação completa, isso pode ser feito pela adição de um capacitor em paralelo com a tensão de saída.


![[Pasted image 20250919163845.png]]

**Tensão de ripple:**
→ É possível observar uma pequena queda de tensão, isso é denominado de tensão de ripple e pode ser reduzida a partir do aumento da capacitância do capacitor. (>1000 uF)
→ É importante lembrar que a tensão ainda será limitada proporcionalmente a área da curva gerada antes da filtragem.


### Circuito retificador de ponte completa

→ Usa 4 diodos e um resistor

![[Pasted image 20250919164338.png]]

**Funcionamento:**
→ Semi-ciclo positivo: Os diodos D2 e D3 entram em condução.
→ Semi-ciclo negativo: Os diodos D4 e D1 entram em condução.

**→ Independente do sentido da corrente, os terminais da resistencia sempre vão ser + e -. Convertendo os semi-ciclo para o lado positivo da tensão de saída.**

![[Pasted image 20250919164801.png]]

![[Pasted image 20250919164809.png]]

**Gráfico gerado:**

![[Pasted image 20250919165303.png]]

→ A tensão gerada na saída do retificador de ponte completa ja se aproxima mais de uma tensão de corrente continua. E é muito mais eficiente do que o de meia onda.

#### Filtragem:

→ Ao adicionar um capacitor em paralelo, é possível observar que o processo de filtragem é mais eficiente.

→ Tensões de corrente continua filtradas a partir de retificadores de ponte completa **entregam o dobro de potência** comparado ao circuito retificador de meia onda.

![[Pasted image 20250919165628.png]]


**Obs importante:** Os terminais da fonte de tensão de saída não possui terminais em comum com a fonte de tensão da entrada. Isso significa que podemos trabalhar com dois níveis de referência:

**1. Fonte simples**
**2. Fonte simétrica (transformador com terminal central).**


### Fonte simples:

![[Pasted image 20250919170545.png]]

→ Terminal de referência GND conectado em um dos terminais do resistor
(tipicamente, o negativo)

→ O transformador está flutuante, pois ele não se conecta diretamente ao GND do circuito de saída.

### Fonte simétrica:

![[Pasted image 20250919171213.png]]


→ Terminal GND conectado no terminal central da fonte proveniente do transformador


---
### Próximo conteúdo:
**Módulo 2:**
[[001 - Diodo Zener]]
