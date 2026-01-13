#faculdade #resumos #eda
## Definição:

→ Estrutura de dados usada para representação hierárquica.
→ A forma mais simples de definir uma árvore é usando recursividade.

## Funcionamento:

→ Composto por um conjunto de nós.
→ Um nó raiz (r), pode conter sub-árvores ou conter zero elementos.
→ Os nós das sub-árvores são filhos do nó raiz (r).
→ Nós filhos tem o nome de nós internos e nós que não possuem filhos são chamados de folhas ou nós externos.

![[Pasted image 20250919225331.png]]

→ O número de filhos por nós e as informações armazenadas se diferenciam nos vários tipos de árvores.


### Árvore binária:

→ Os nós de uma árvore binária podem ter no máximo 2 filhos.

![[Pasted image 20250919225728.png]]

→ Nessa árvore, os nós folhas representam operandos e os nós
internos operadores.


**Representação recursiva:**

Uma árvore binária pode assumir as seguintes condições:

1. Árvore vazia
2. Um nó raiz tendo duas sub-árvores

**Estrutura:**

Um nó raiz tem a sub-árvore da direita (sad) e a sub-árvore da esquerda (sae).

![[Pasted image 20250919230011.png]]


**Exemplo de árvore binária:**

![[Pasted image 20250919230124.png]]

→ “a” é a raiz
→ “b” e “c” são as sub-árvores
→ “d”, “e”, “f” são folhas

sae: b d
sad: c e f


#### Propriedade de árvores:

→ Só existe um caminho da raiz até qualquer nó.
→ A altura de uma árvore é definida pelo comprimento do caminho mais longo da raiz até uma das folhas. Sendo que a raiz é a camada zero.

![[Pasted image 20250919230124.png]]

→ Tem altura de 2.

→ Nesse sentido, a altura de uma árvore vazia e -1.


## Representação de Árvores binárias em C

→ Estrutura personalizada para árvore
→ Armazena um caractere
→ Cada nó da árvore armazena 3 informações:
1. Info da árvore
2. Ponteiro para sub-arvore esquerda (sae)
3. Ponteiro para sub-arvore direita (sad)

```C
struct arv {
	char info;
	struct arv* esq;
	struct arv* dir;
};
```

Passos de implementação:

→ Criar a estrutura do tipo arvore
→ Iniciar uma árvore vazia:

```c
Arv* inicializa(){
	return NULL;
}
```

→ Função que cria os nós:
- Cria o nós raiz e suas sub-árvores
- Coloca a informação
- Retorna o endereço do nó

```C
Arv* cria(char c, Arv* sae, Arv* sad){
	Arv* no =(Arv*) malloc(sizeof(Arv));
	no->info = c;
	no->esq = sae;
	no->dir = sad;
	return no;
}
```


---
### Próximo conteúdo:
**Módulo 2:**
[[001 - Árvores binárias]]
