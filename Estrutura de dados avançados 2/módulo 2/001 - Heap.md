## Definição:
Heap é uma árvore binária completa que satisfaz duas propriedades:

**Forma:**
- Árvore binária completa: todos os niveis preenchidos da esquerda para a direita.

**Heap:**
- Cada nó pai tem uma relação ordenada com seus filhos. sendo elas:
1. Min-heap (nó pai é menor ou igual ao seus filhos).
2. Max-heap (nó pai é maior ou igual ao seus filhos).

**A raiz sempre guarda o elemento de maior prioridade.**
→ **Heaps são ideais para FILAS DE PRIORIDADE.**


## Max-heap: (Maior elemento na raiz)
**Definição:**
Todo pai é maior ou igual a seus filhos. O maior elemento sempre fica na raiz. Fila de prioridade máxima.

![[Pasted image 20260607104244.png]]

**Ao extrair a raiz (90) o heap se reorganiza em O($log_n$)** colocando o próximo maior no topo.

**Uso:** Fila de prioridade máxima.


## Min-heap: (Menor elemento na raiz)
**Definição:**
Todo pai é menor ou igual a seus filhos. O menor elemento sempre fica na raiz.

![[Pasted image 20260607104554.png]]

**Uso:** O algoritmo de Dijkstra e Prim usa o min-heap para sempre processar o vértice de menor custo primeiro.


## Comparação:

![[Pasted image 20260607104801.png]]


## Detalhe importante:

**Importante:** Heap não é uma **árvore binária de busca.** Não existe ordem garantida entre o filho esquerdo e o direito. Apenas a relação pai/filho é assegurada. Por esse motivo buscar um elemento qualquer no heap custa O(n) e não O(log n).

**Operações  fundamentais do heap:**
- **Insert:** O(log n), sobe o novo elemento até a posição correta
- **Extract max/min:** O(log n), remove a raiz e reorganiza
- **Build heap:** Constrói um heap a partir de um array
- **Peak max/min:** Acessar o elemento máximo/mínimo.
## Revisando:

Em qualquer tipo de heap, os elementos de maior prioridade sempre ficam mais próximos da raiz. A diferença está somente em como esta prioridade é definida.

- **Max-heap:** prioridade = valor maior → 90 sai antes do 70, que sai antes do 40.
- **Min-heap:** prioridade  = valor menor → 5 sai antes do 10, que sai antes do 30.

**O heap só garante que a raiz sempre terá o elemento de maior prioridade segundo a regra escolhida.**

**Importante:** Fila de prioridade não é uma fila FIFO. Quem chegou primeiro não é quem sai primeiro, independente de quando entrou. **Quem tem maior prioridade é o que sai primeiro.**



## Exemplo fila de pacientes - Max-heap

- Pacientes chegam em momentos diferentes, mas são atendidos pela **gravidade** e não pela ordem de chegada. Internamente o max-heap mantém o mais grave sempre no topo.

![[Pasted image 20260607105610.png]]

![[Pasted image 20260607105629.png]]

Diana chegou depois de todos, porem subiu para o topo de prioridade pois tem o estado mais urgente.
![[Pasted image 20260607105700.png]]

![[Pasted image 20260607105838.png]]

![[Pasted image 20260607105851.png]]
