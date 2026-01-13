#faculdade #resumos #eda 
## Algoritmo de balanceamento AVL

**Relembrando conceitos - árvores binárias:**
→ Árvores binárias podem ter 0, 1 ou 2 nós filhos em cada ponto.
→ Possui nó raiz e nó folha

**Altura da árvore:**
→ Para calcular a altura de uma árvore binaria, basta contar as linhas de ligação, entre o nó raiz e as folhas. 

![[Pasted image 20251104030838.png]]

nó 5, altura = 2.

#### **Balanceamento:**

→ Para calcular o balanceamento, é preciso calcular o fato de balanceamento. O fator é calculado a partir das folhas até chegar na raiz.

### $$Fb = |He - HD| < 2$$
Sendo:

Fb = fator de balanceamento
He = altura da esquerda
Hd = altura da esquerda

→ Após o calculo e identificar um nó desbalanceado, aplicamos a seguinte regra:

**Fb negativo:** girar para esquerda
**Fb positivo:** girar para direita

![[Pasted image 20251104031233.png]]


Para balancear, basta fixar o ponto que desbalanceou primeiro e girar para a esquerda ou direita.

![[Pasted image 20251104031402.png]]

**Regra de inserção:**

→ Menores esquerda
→ Maiores direita

![[Pasted image 20251104031619.png]]

![[Pasted image 20251104031713.png]]



---
### Próximo conteúdo:
