
## Listas em python

→ Uma lista em python pode ser formada por diferentes tipos de dados combinados

```python
lista = [1, 2, "banana", "python", 200428]
```


### Operações de acesso nas listas:

| Operações de Acesso | Função                                               |
| ------------------- | ---------------------------------------------------- |
| lista[0]            | Aponta para o primeiro item                          |
| lista[-1]           | Lista reversa, aponta para o ultimo item da lista    |
| lista[-2]           | Lista reversa, aponta para o penúltimo item da lista |
| len(lista)          | Retorna o tamanho total da lista                     |

### Manipulação de listas:

```java
lista = ["Gui", "Ronald", "Gonza", "João", "Miguel"]
```

#### Função adicionar:

```python
lista.append("Luccas")
# ['Gui', 'Ronald', 'Gonza', 'João', 'Miguel', 'Luccas']
```

#### Função remove:
→ Busca e remove o item com o valor definido. 
**Obs: só remove a primeira ocorrencia!**

```python
lista = ["Gui", "Gui", "Ronald", "Gonza", "João", "Miguel"]
lista.remove("Gui")
# ['Gui', 'Ronald', 'Gonza', 'João', 'Miguel', 'Luccas'
```


#### Função pop
→ Trabalha com parâmetros. 
→ Se não for passado nenhum parâmetro, a função remove o ultimo item da lista!

```python
lista = ["Gui", "Ronald", "Gonza", "João", "Miguel", "Luccas"]
lista.pop()
# ['Gui', 'Ronald', 'Gonza', 'João', 'Miguel']

lista.pop(0)
# ['Ronald', 'Gonza', 'João', 'Miguel']
```



#### Função sort
→ Organiza a lista de forma crescente, para todos os tipos de dados.


```python
num = [5,3,2,4,1]
num.sort()
# [1, 2, 3, 4, 5]

letras = ["c", "a", "b", "C", "A", "B"]
letras.sort()
# ['A', 'B', 'C', 'a', 'b', 'c']
# ASCII: letras maiusculas vem antes

boolean = [True, False, False, True]
boolean.sort()
# [False, False, True, True]
```


#### Função reverse
→ Inverte a lista

```python
num = [5,3,2,4,1]
num.reverse()
# [1, 4, 2, 3, 5]


letras = ["c", "a", "b", "C", "A", "B"]
letras.reverse()
# ['B', 'A', 'C', 'b', 'a', 'c']

boolean = [True, False, False, True]
boolean.reverse()
# [True, False, False, True]
```

#### Função max
→ Retorna o maior termo da lista

```python
num = [5,3,2,4,1]
print("O maior termo da lista é:", max(num))
# 5
```

#### Função min
→ Retorna o menor termo da lista

```python
num = [5,3,2,4,1]
print("O menor termo da lista é:", min(num))
# 1
```

#### Função sum
→ Retorna a soma dos termos da lista

```python
num = [5,3,2,4,1]
print("A soma da lista é:", sum(num))
# 15
```


#### Função copy
→ **Importante:** para copiar uma lista, não podemos simplesmente atribuir ela a outra variável. Isso apenas cria um link para a mesma lista.

```python
a = [1,2,3,4]
b = a
print(b)
# [1, 2, 3, 4]
a.pop(0)
print(b)
# [2, 3, 4]
```

Função .copy()

```python
a = [1,2,3,4]
b = a.copy()
print(b)
# [1, 2, 3, 4]
a.pop(0)
print(b)
# [1, 2, 3, 4]
```



### Extra:
→ Percorrer uma lista e imprimir um item especifico

```python 
lista = [1,2,3,4]

num = int(input("Procurar o número: "))

for item in lista:
    if item == num:
	    # Retorna a posição do item na lista.
        posicao = lista.index(num)
        print(f"Número encontrado! na posição: {posicao}")
        break
# Só entra no else se o break não parar o laço
else:
    print("Não encontrado!")
```

#### Popular uma lista:

```python
lista = []
for item in range(10):
    lista.append(item)
```

List comprehension:
```python
lista = [item for item in range(10)]

for num in lista:
    print(num)
```

Condicional em List comprehension:

```python
lista1 = [-1,-2,3,4,5]

lista2 = [item for item in lista1 if item >= 0]
# [3, 4, 5]
```

