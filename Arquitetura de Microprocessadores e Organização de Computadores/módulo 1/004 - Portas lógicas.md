#faculdade #aom #resumos 
## Revisão - Decimal para binário:

→ Dividir por 2 e anotas os restos da divisão
→ As sequencias dos restos lidos de baixo para cima será o binário

![[Pasted image 20250928180601.png]]


## Binário para decimal:

→ Multiplicar cada digito pela potencia de 2 correspondente a posição do numero. Da direita para esquerda, começando do $2^0$

![[Pasted image 20250928180809.png]]

## Soma de binário:

![[Pasted image 20250928180920.png]]

![[Pasted image 20250928180938.png]]

## Complemento de 2:

→ Método para representar números positivos e negativos.
**Passos:**

1- Representação binária do número
2- Inversão dos bits (complemento de 1)
3- Adição de um: Some 1 ao resultado da inversão dos bits

![[Pasted image 20250928181227.png]]

---

## Portas lógicas:
→ Possuem pelo menos uma entrada e exatamente uma saída.

### Porta E (AND):

![[Pasted image 20250928181358.png]]

### Porta OU (OR):

![[Pasted image 20250928181417.png]]

### Porta NOT:

![[Pasted image 20250928181438.png]]


## Portas compostas:

### Porta NAND:

![[Pasted image 20250928181518.png]]

### Porta NOR:

![[Pasted image 20250928181538.png]]

### Porta XOR
→ Ou exclusivo, só da 1 se apenas uma das entradas for 1

![[Pasted image 20250928181649.png]]


## Circuitos combinacionais

→ Circuito construído com portas logicas. Que implementam funções mais complexas. A saída desse circuito apenas depende da entrada.



### Somador binário:

→ Realiza as operações de soma e subtração em complemento de dois.
→ Constituído por um XOR que calcula o resultado e um AND que calcula o “vai-um”

![[Pasted image 20250928182646.png]]


![[Pasted image 20250928182721.png]]

---
### Próximo conteúdo:

[[005 - Circuitos sequenciais]]
