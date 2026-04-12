
## Definição:

Uma matriz é uma lista de listas!

```python
matriz = [
[1,2,3],
[4,5,6]]

# Linha 0, coluna 0
print(matriz[0][0])
# 1
```



### Percorrer uma matriz completamente:

```python
matriz = [
[1,2,3],
[4,5,6]]

# O loop externo trava na linha, o loop interno percorre os elementos individuais da linha.
# percorre a linha
for linha in matriz:
    # percorre o elemento da linha
    for elemento in linha:
        print(elemento)
        
# 1 2 3 4 5 6
```



## Geração dinâmica com list comprehension

```python
import random
ordem = 10
matriz = [[random.randint(1, 100) for _ in range(ordem)] for _ in range(ordem)]
```


- **Variável _ :** Usar o _ como variável do laço for é uma forma de indicar que o índice não será utilizado na lógica. O objetivo é que o laço rode 10 vezes, não importa o valor de 0 a 9.

**Ordem de execução:**
- **laço interno:** `[random.randint(1, 100) for _ in range(ordem)]` gera uma linha com 10 números aleatórios (1 - 100).
- **laço externo:** `... for _ in range(ordem)` pega essa lógica geradora e repete 10 vezes, criando as 10 linhas independentes.


```python
for linha in matriz:
    for elemento in linha:
	    # end: força o terminal a continuar imrpimindo na mesma linha 
	    # 4D: formata o elemento para usar 4 espaços de largura no terminal
        print(f"{elemento:4d}", end="")
    print() # Quebra a linha quando a linha da matriz acaba
```


#### Print da diagonal principal:

```python
# preenche uma lista com os termos da diagonal principal da matriz inicial
diagonal_principal = [matriz[i][i] for i in range(ordem)]
```


#### Diagonal secundaria:
```python 
# preenche uma lista com os termos da diagonal secundaria da matriz inicial
diagonal_secundaria = [matriz[i][ordem -1 -i] for i in range(ordem)]
```



## Extra:


### Problema de iniciar uma matriz vazia:

```python 
matriz_errada = [[0] * 3] * 3
```

Visualmente, isso gera `[[0, 0, 0], [0, 0, 0], [0, 0, 0]]`. Parece perfeito. Mas veja o que acontece se você tentar alterar apenas o primeiro elemento (Linha 0, Coluna 0):


```python
matriz_errada[0][0] = 9 print(matriz_errada) 
# Saída errada: [[9, 0, 0], [9, 0, 0], [9, 0, 0]]
```

A multiplicação de listas no nível externo `* 3` não criou três linhas novas. Ela criou **uma única linha** na memória e fez três ponteiros diferentes apontarem para ela (espaço compartilhado). Alterar uma "linha", altera todas.


### Forma correta:

```python
# preenche a linha com 0 / repete o comando 3x
matriz_correta = [[0 for _ in range(3)] for _ in range(3)]
```



