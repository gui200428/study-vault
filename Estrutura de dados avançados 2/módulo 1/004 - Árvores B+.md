
## Definição:
- É uma lista encadeada com indices! 
- Possibilita que os dados sejam acessados de forma mais rápida
- Altamente usado em banco de dados

### Analogias:

- Uso de indices para achar um item dentro de uma biblioteca muito grande.
- O índice não guarda o conteúdo, ele apenas aponta para onde o item está.
- **Em banco de dados:** navegação por índices para encontrar o dado na folha


### Estrutura:
- **Nós internos** guardam os índices
- **Folhas:** guarda os valores
- **Encadeamento:** folha aponta para a próxima folha

![[Pasted image 20260419195757.png]]


### Busca:

![[Pasted image 20260419195902.png]]


## Vantagem da ligação das folhas:

- Ao encontrar uma folhas valida, basta seguir a lista de forma sequencial até achar o dado.
- Leitura sequencial rápida
- Menos acessos aleatórios


## Split em árvores b+ de ordem 4

- O nó vai estourar quando atingir 4 itens

![[Pasted image 20260419200308.png]]



## Questões:

### 1. Por que encadear folhas ajuda mais do que subir para a raiz toda hora?
**R:** Ao encadear as folhas, a busca sequencial fica mais rápida


### 2. Por que bancos de dados preferem B+ em vez de BST simples?
**R:** menos altura, melhor uso de disco e busca por intervalo.

