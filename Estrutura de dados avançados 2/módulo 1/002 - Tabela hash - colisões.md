
## Introdução:

**Tabela hash:** Guarda dados em um **array.** Utilizando uma função hash para transformar uma chave em um índice.

```java
chave: "banana"  -> hash("banana") -> indice: 3
```

## Colisões:

→ Este problema acontece quando duas chaves diferentes caem no mesmo índice.

```java
hash("banana") -> 4
hash("laranja") -> 4
```


 → Colisões são esperadas. Diferentes chaves podem cair no mesmo índice.

## Soluções:

### 1. Encadeamento (Separate Chaining)

→ Cada posição da tabela guarda uma lista de elementos. 
→ Quando a colisão ocorre, o dado é simplesmente adicionado na lista do índice

**Passos:**

```java
hash("banana") -> indice: 3 -> se tiver outro elemento, adiciona na lista
```

```java
{  
  "0": [],
  "1": [],
  "2": [],
  "3": [],
  "4": [
    { "chave": "banana", "valor": 10 },
    { "chave": "laranja", "valor": 18 }
  ],
}
```

**Implementação em java:**

```java
int idx = hash(key);
table[idx].add(new Entry(key, value));
```

### 2. Endereçamento Aberto (Open Addressing)

→ Cada posição do array guarda apenas um elemento
→ Se ocorrer colisão: procurar outra posição livre usando probing (sondagem)

**Passos:**
1. Calcula o hash
2. Se estiver livre → inserir
3. Se  ocupado → procurar outra posição

#### Formas de probing:

#### 1. Linear Probing
→ Avança de 1 em 1 até encontrar uma posição livre

```java
int pos = (idx + step) % table.length;
```

#### 2. Quadratic Probing
→ Usa saltos quadráticos:

$$i+i^2, i+ 2^2 ,i+3^2$$
Reduz clustering em relação ao linear

#### 3. Double hashing
→ Utiliza duas funções hash: uma define a posição inicial e outra define o tamanho do salto.


```java
pos = (hash1(key) + step * hash2(key)) % tamanho;
```



### Comparação:


| Tipo:              | Encadeamento     | Endereçamento Aberto |
| ------------------ | ---------------- | -------------------- |
| Estrutura          | Lista por índice | Tudo no array        |
| Memória            | Usa mais memória | Usa menos memória    |
| Remoção            | Fácil            | Complexo             |
| Multiplas colisões | Lida melhor      | Degrada              |


### Resumo:

**Encadeamento:** várias pessoas na mesma casa
**Endereçamento aberto:** cada pessoa procura outra casa