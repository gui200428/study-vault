
## Circuito inicial de CC

![[Pasted image 20260523192149.png]]

### Questão: como montar um amplificador?

- Capacitor de acoplamento - ligado entre a fonte CA e a base
- Capacitor de acoplamento - aberto para corrente contínua
- **Corrente CC na base é a mesma com ou sem o capacitor e a fonte CA**
- Outro capacitor de acoplamento → ligado entre o coletor e o resistor de carga.
- Capacitor aberto em CC → tensão CC no coletor é a mesma com ou sem capacitor e o resistor de carga

![[Pasted image 20260523192605.png]]


### Ponto principal:

- Capacitor de acoplamento evita que a fonte de corrente alternada e o resistor de carga mudem a localização do ponto Q.

### Analise geral do circuito:

- Fonte Ca é de 100 $\mu V$  
- Capacitor de acoplamento → Curto para CA
- Tensão de CA da fonte aparece entre a base e o terra
- Tensão de CA → produz uma CA na base que é somada com a CC existente na base

- **Corrente total na base: componente CA e CC**
- **Componente CA é superposta a uma componente CC**

![[Pasted image 20260523201927.png]]

- **Semiciclo positivo - CA na base é somado aos 30$\mu$A da corrente CC **
- **Semiciclo negativo - corrente CA na base é subtraída dos 30$\mu A$ da corrente CC**

### Comportamento no coletor:

![[Pasted image 20260523202153.png]]

- CA na base - produz uma variação amplificada na corrente do coletor. Devido ao ganho de corrente.
- Grafico: corrente de coletor tem uma componente CC de 3mA
- CA do coletor será superposta a ela.
- **Corrente do coletor amplificada - passa por Rc - produz uma variação de tensão em RC**

![[Pasted image 20260523202423.png]]


### Formas de onda da tensão
- Ondas de um amplificador com polarização de base:
![[Pasted image 20260523202508.png]]

- Fonte de tensão CA - tensão senoidal baixa
- Acoplada na base → superposta à componente CC de 0,7V
- Variação da tensão na base → produz uma variação senoidal na corrente da base, na corrente do coletor e na tensão do coletor
- Tensão do coletor - **onda senoidal invertida superposta à tensão de 15V**

#### Função do capacitor de acoplamento
- Capacitor aberto em CC → bloqueia a componente CC da tensão no coletor
- Curto para CA - acopla a tensão CA do coletor no resistor de carga
- Tensão na carga é um sinal CA puro com valor médio zero.

## Funções importantes:

### Ganho de tensão
- Ganho de tensão do amplificador - tensão de saída pela tensão de entrada

### $$A_v=\frac{v_{saída}}{v_{entrada}}$$
![[Pasted image 20260523203129.png]]


(08/03) 