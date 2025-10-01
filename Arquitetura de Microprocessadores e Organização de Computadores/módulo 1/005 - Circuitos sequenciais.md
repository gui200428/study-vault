## Definição:

→ Circuitos combinacionais implementam as funções essenciais de um computador lógico.

**Exemplos:**
- Flip-flops
- Registradores
- Contadores

## Flip-flop

→ Forma mais simples de circuito sequencial
→ Existem varios tipos de flip-flops
**Propriedade:**

→ O flip-flop existe em dois estados e na ausência de entrada, permanece no estado. Podendo ser usado como uma memória de 1 bit.
→ Tem duas saídas que são complementos uma da outra. Q e /Q

### Flip-flop S-R

→ Possui duas entradas, S (set) e R(Reset). e duas saidas Q e /Q.

![[Pasted image 20250928183853.png]]

![[Pasted image 20250928184002.png]]

### Flip-flop S-R
→ Mudança somente acontece com o pulso do clock

![[Pasted image 20250928184052.png]]


### Flip-flop D

→ Resolve o problema com o flip-flop S-R em que não pode ter entrada S e R como 1.

![[Pasted image 20250928184432.png]]


### Flip-flop J-K

![[Pasted image 20250928184517.png]]

![[Pasted image 20250928184550.png]]

---

## Registradores:

→ Circuito digital usado dentro da CPU para armazenar um ou mais bits de dados. 
→ Um **registrador** é um conjunto de **Flip-Flops** (geralmente tipo D) que trabalham juntos para armazenar múltiplos bits simultaneamente.
→ Tipos: Registradores paralelos e registradores de deslocamento.

### Registradores paralelos:

→ Conjunto de memória de 1 bit que pode ser lido ou escrito de modo simultâneo. Usado para armazenar dados.

![[Pasted image 20250928185205.png]]

### Registradores de deslocamento

→ Aceita / transfere informação serialmente.

![[Pasted image 20250928185307.png]]


## Contadores:

→ 