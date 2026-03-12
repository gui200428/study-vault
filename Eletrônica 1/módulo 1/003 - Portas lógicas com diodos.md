#faculdade #resumos #eletronica 
## Relembrando a tabela verdade das portas AND e OR

→ Em electronica, a implementação das portas logicas são feitas pela relação de nível logico baixo (0 ou GND) e nível logico alto (1 / 5V / 12V).

![[Pasted image 20250919111333.png]]


---

## Porta lógica OR - Estudo

![[Pasted image 20250919113239.png]]

### Caso 1: A e B em nível logico baixo:

**Não existe passagem de corrente pelo circuito**

![[Pasted image 20250919111659.png]]


### Caso 2: A em nível logico alto:

**Passagem de corrente pelo resistor R1 e queda de tensão sobre o diodo. Saída de +4.3V, considerado nível logico alto.**

![[Pasted image 20250919111844.png]]


### Caso 3: B em nível logico alto

**Passagem de corrente pelo resistor R1 e queda de tensão sobre o diodo. Saída de +4.3V, considerado nível logico alto.**

![[Pasted image 20250919112036.png]]


### Caso 4: A e B em nível logico alto

**Queda de tensão sobre os diodos D1 e D2 e passagem de corrente sobre o resistor R1, a saída esta em estado alto +4.3V**

![[Pasted image 20250919112154.png]]


---

## Porta lógica AND - Estudo

→ Em portas lógicas AND, temos uma configuração diferente: 
- Diodos invertidos com relação aos terminais A e B
- Tensão de +5V no resistor R1

### Caso 1: A e B em nível lógico baixo:

**A corrente vai passar pelo resistor R1 e se dividir ao meio, existe queda de tensão nos diodos D1 e D2. Saída em estado baixo.**

![[Pasted image 20250919113528.png]]


### Caso 2: A em nível lógico alto:

**A corrente vai passar pelo resistor R1 e ir direto para o diodo D2, existe uma queda de tensão no diodo D2. Como não existe uma diferença de potencial entre a entrada do resistor e o ponto A, nenhuma corrente vai passar pelo diodo D1. Saída em estado baixo.**

![[Pasted image 20250919113757.png]]


### Caso 3: B em nível lógico alto:

**A corrente vai passar pelo resistor R1 e ir direto para o diodo D1, existe uma queda de tensão no diodo D1. Como não existe uma diferença de potencial entre a entrada do resistor e o ponto B, nenhuma corrente vai passar pelo diodo D1. Saída em estado baixo.**

![[Pasted image 20250919114105.png]]


### Caso 4: A e B em nível lógico alto:

**Todos os pontos estão com a mesma tensão, portanto nenhuma corrente vai passar pelo circuito, a saída sera de +5V.**

![[Pasted image 20250919114346.png]]


**Obs importante:** O nível lógico da saída é afetado pela tensão de polarização direta do diodo. (Vd).



---
### Próximo conteúdo:

[[004 - Circuitos retificadores]]
