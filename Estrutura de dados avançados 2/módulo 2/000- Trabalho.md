## Analogia dos mapas

Na teoria dos grafos, existem dois elementos principais:

### Vértices (Nós):
- São os pontos de interesse. Na analogia do mapa, seriam as cidades em si.

### Arestas (linhas / trilhas): 
- São as conexões entre os pontos. No mapa, seriam as rodovias que ligam as cidades.

![[Pasted image 20260523222950.png]]

Vértices conectados por arestas.


---

## O algoritmo PRIM:

**Objetivo:** Interligar todos os vértices verificando os pesos de cada aresta contida na 
árvore e escolhendo a que possui o menor custo de processamento.

**Analogia:** Conectar todas as cidades de uma área (grafo conexo), gastando o menos possível com cabo de fibra ótica. Sem repetir pontos que ja estão conectados por outros caminhos.

**Funcionamento:** O Prim tem o objetivo de conectar todos os pontos a partir de um único ponto. Gerando uma árvore geradora mínima.

**1. O ponto de inicio não altera o custo total (peso final) da árvore geradora** permite começar por qualquer vértice.
**2. Faz o calculo de qual vértice tem o menor custo.**
**3. Escolhe o caminho mais barato**
**4. Passa para o próximo vértice**
**5. Verifica se o caminho mais barato leva a um vértice que ja foi incluído na conexão**
**6. Repete o processo até que todos os vértices estejam conectados.**

**Iniciando com o nó A.**: Analisa as opções e A-B(2) e A-C(4).
![[Pasted image 20260525191158.png]]


**Próximas opções: A-C(4) B-C(1) B-D(7)**
![[Pasted image 20260525191448.png]]

**Próximas opções: B-D(7) e C-E(3)**
![[Pasted image 20260525191603.png]]

**Próximas opções: B-D(7) E-D(2) E-F(1)**
![[Pasted image 20260525191704.png]]

**Próximas opções: B-D(7) E-D(2) F-D(5)**
![[Pasted image 20260525191751.png]]

---

## Kruskal

**Objetivo:** Interligar todos os vértices listando os pesos e conectando os de menor valor, até que a árvore geradora mínima seja formada.

**Passos de execução:**
1. Lista todas as arestas (linhas) do grafo e ordena da menor para maior
2. Pega a menor aresta disponível no grafo inteiro
3. Se ligar dois pontos soltos, ele adiciona
4. Se a aresta ligar pontos que ja foram ligados, ele rejeita

![[Pasted image 20260525192739.png]]

![[Pasted image 20260525192826.png]]


![[Pasted image 20260525192845.png]]

![[Pasted image 20260525192910.png]]

![[Pasted image 20260525192938.png]]

![[Pasted image 20260525193002.png]]

![[Pasted image 20260525193033.png]]

![[Pasted image 20260525193051.png]]

![[Pasted image 20260525193106.png]]


---

## Dijkstra

![[Pasted image 20260525194655.png]]

**Nó selecionado A. (Distância atual: 0.**
**Vizinhos:** 
B: 0 +2 = 2 **Menor!**
C: 0+ 4 = 4
![[Pasted image 20260525194722.png]]


**Nó selecionado B. (Distância atual: 2.)**
**Vizinhos:** 
C: 2 + 1 = 3 **Menor!**
D: 2 + 7 = 4

![[Pasted image 20260525194902.png]]


**Nó selecionado C. (Distância atual: 3.)**
**Vizinhos:** 
E: 3 + 3 = 6 **Menor!**

![[Pasted image 20260525195039.png]]


**Nó selecionado D. (Distância atual: 6.)**
**Vizinhos:** 
D: 6 + 2 = 8
F: 6 + 1 = 7 **Menor!**

![[Pasted image 20260525195226.png]]


**Nó selecionado F. (Distância atual: 7.)**
**Vizinhos:** 
D: 7 + 5 = 12 > 8 **Ignorado!**


![[Pasted image 20260525195413.png]]

**Nó selecionado D. (Distância atual: 8.)**
![[Pasted image 20260525195603.png]]
