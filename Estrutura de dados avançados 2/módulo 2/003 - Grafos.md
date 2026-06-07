## Analogia dos mapas

Na teoria dos grafos, existem dois elementos principais:

### Vértices (Nós):
- São os pontos de interesse. Na analogia do mapa, seriam as cidades em si.

### Arestas (linhas / trilhas): 
- São as conexões entre os pontos. No mapa, seriam as rodovias que ligam as cidades.

![[Pasted image 20260523222950.png]]

Vértices conectados por arestas.

---

## Grafo ponderado:

**Definição:** Cada **aresta** carrega um valor numérico associado, chamado de **peso.** O peso pode representar distância, custo, tempo, capacidade, etc.


---

## Grafos direcionados e não direcionados:


### Grafos direcionados

**Definição:** As arestas tem sentidos, são representadas por setas. Se existe uma aresta de A para B, **não significa** que existe uma aresta de B para A. 

**Grau:**
Se divide da seguinte forma:

**Grau de entrada:** quantidade arestas que chegam ao vértice.
**Grau de saída:** quantidade de arestas que saem do vértice.
**Grau total:** soma do grau de entrada e de saída.

**Propriedade:** a soma de todos os graus de entrada de um grafo é igual a soma de todos os graus de saída.

![[Pasted image 20260607115201.png]]


### Grafos não direcionados

**Definição:** É um grafo em que as arestas não tem direção. A conexão entre dois vértices é de mão dupla. Se A está conectado a B, B esta conectado a A.

**Grau:** é simplesmente o número de arestas  conectadas a ele. Sem distinção de entrada ou saída, pois não há direção. 

![[Pasted image 20260607115150.png]]


![[Pasted image 20260607115521.png]]

---
## Tipo de conexões de grafos:

### Grafo Acíclico
**Definição:** é um grafo que não possui nenhum ciclo. Ao sair de um vértice, não é possível chegar nele mesmo sem repetir arestas.

### Grafo completo
**Definição:** é um grafo em que todos os vértices estão conectados a todos os outros.

![[Pasted image 20260607122433.png]]

### Grafo bipartido
**Definição:** é um grafo em que os vértices podem ser divididos em dois conjuntos. Todas as arestas conectam os vértices do conjunto A no conjunto B. Nunca no mesmo grupo.

![[Pasted image 20260607122808.png]]


### Grafo ciclico:
**Definição:** é um grafo que contem pelo menos um ciclo. É possível sair do vértice e chegar nele mesmo sem repetir arestas.

![[Pasted image 20260607123004.png]]


### Árvore:
**Definição:** Caso especial de grafo acíclico, sem ciclos por definição.


---

## Grafo esparso e representações:

**Definição:** é simplesmente um grafo com poucos vértices conectados entre si. Maioria dos vértices não se conecta com a maioria dos outros.

![[Pasted image 20260607120033.png]]

## Representações:

### Matriz de adjacência
**Definição:** Basicamente é uma matriz que indica se existe uma aresta entre dois vértices.
M\[i]\[j]  = 1 se existe  aresta, 0 se não existe.

**Detalhe:** extremamente ineficiente em grafos esparsos, ocupa vários espaços com 0.
![[Pasted image 20260607120333.png]]


### Lista de adjacência
**Definição:** Cada vértice tem uma lista com seus vizinhos. Só armazena as conexões que realmente existem.

**Detalhe:** Ideal para grafos esparsos, armazena somente o que existe.

![[Pasted image 20260607120632.png]]


### Lista de arestas
**Definição:** Armazena apenas os pares de vértices que formam cada aresta. 
- 3 arestas = 3 entradas
- Somente armazena as arestas, sem informação de vértices isolados.

![[Pasted image 20260607120847.png]]


![[Pasted image 20260607120950.png]]

### Matriz de incidência:
**Definição:** é uma tabela VxE (vértices por arestas). Cada linha é um vértice cada coluna é uma aresta. A célula vale 1 se aquele vértice participa daquela aresta.
**Desvantagem:** Ruim para percorrer vizinhos.

![[Pasted image 20260607121254.png]]

### Hash table de arestas
**Definição:** armazena cada aresta como uma chave em uma tabela hash. 

{(A,B): 1, (A,C): 1, (B,D): 1}

**Vantagem:** verificar se uma aresta existe em O(1).
**Desvantagem:** listar os vizinhos de um vértice é custoso. Exige varrer todas as entradas.

