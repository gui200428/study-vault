#faculdade #logica_matematica #resumos #formulario 

## Conjunto das partes

**Definição:** Se trata de todas as combinações possíveis para um conjunto. Partes do conjunto.
### $$P(a)=2^n$$
→ Número de itens individuais do conjunto, contando com o vazio.

**Exemplo:**
A: {{4},{6},{4,6},{ }}

$P(A)=2^2=4$

→ O conjunto possui todos as combinações possíveis do conjunto original. Portanto é o conjunto das partes (conjunto de conjuntos!)

---
## Operações entre conjuntos

### 1. ∪ (União)

→ União de dois conjuntos, descartar itens repetidos.

A = {1,2,3,4}
B = {3,4,5}
A ∪ B = {1,2,3,4,5}



### 2. ∩ (Interseção)

→ Gera um conjuntos de somente os elementos comuns de dois conjuntos

A = {1,2,3,4}
B = {3,4,5}
A ∩ B = {3,4}

### 3. ⊂ (Subconjunto)

→ Indica que todos os elementos de um conjunto estão dentro de outro conjunto (um conjunto inteiro)
A = {1,2,3,4}
B = {3,4}

B ⊂ A

### 4. ∈ (pertence)

→ Indica que um elemento pertence a um conjunto (um elemento único)

A = {1,2,3,4}
3 ∈ A

### 5. ∉ (Não pertence)

→ Indica que um elemento **não** pertencem ao conjunto
A = {1,2,3,4}
6 ∉ A

### 6. Diferença entre dois conjuntos

→ Na subtração dos conjuntos, o conjunto resultante serão todos os elementos que estão no primeiro conjunto e que não estão no segundo conjunto.

A = {1,2,3,4}
B = {3,4,5}

(A - B) = {1,2}
(B - A) = {5}

### 7. Produto cartesiano

→ Operação que permite combinar elementos de dois ou mais conjuntos de forma estruturada, gerando pares ordenados.

A={1,2}
B={x,y}
**Cardinalidade:** A x B = m * n
(A x B) = 2 * 2 = 4 elementos
(A x B) = {(1,x),(1,y),(2,x),(2,y)}


### 8. Complementar

→ O complemento de um conjunto  é o conjunto de todos os elementos que não pertencem a ele.

A = {2,4}
B = {1,2,3,4,5}

Complementar de A em relação a B: 

B - A = Ca = {1,3,5}

---

## Determinar se **R** é uma relação de equivalência

**Objetivo:** Analise da relação R definida em um conjunto, onde dois números a e b estão relacionados (a R b). Se eles tiverem a mesma paridade (ambos pares ou impares). É preciso verificar 3 propriedades.

### Reflexividade

→ A relação é reflexiva se todo elemento do conjunto estiver relacionado consigo mesmo. 

$$∀\ a ∈ A, a\ R \ a$$
→ Para todo a pertencente ao conjunto A, a está relacionado com a. (ele mesmo)
**Exemplo:**
A={1,2,3,4,5,6,7,8,9}

Se a=2 (par), então 2 e 2 são ambos pares.

### Simetria

→ A relação sempre será simétrica se a R b, então b R a. (se tiverem a mesma paridade)

a R b  <-> b R a

**Exemplo:**
2R4 (ambos pares), e 4R2 também é verdadeiro.

### Transitividade 

→ : Se a e b têm a mesma paridade, e b e c têm a mesma paridade, precisamos verificar se a e c têm a mesma paridade.

a R b
b R c

Como a e b tem a mesma paridade, então: a R c

2R4 (ambos pares) e 4R6 (ambos pares), então 2R6 (ambos pares).

**Resumindo:**
- **Reflexividade**: Todo número tem a mesma paridade que ele mesmo. 
- **Simetria**: Se ae b têm a mesma paridade, b e a também têm. 
- **Transitividade**: Se a e b têm a mesma paridade, e b e c têm a mesma paridade, então a e c têm a mesma paridade. 

