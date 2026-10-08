## Gerenciamento de memória e paginação

Vários programas podem executar ao mesmo tempo e todos precisam de memória. O sistema operacional organiza quais informações permanecem na **RAM**, onde serão armazenadas e quais podem ser retiradas quando não há espaço para novas informações.

A **paginação** organiza a memória em unidades de tamanho fixo:

- **Página (page):** bloco da memória virtual de um processo.
- **Frame (quadro ou moldura):** espaço da memória física capaz de armazenar uma página.

Com **3 frames** disponíveis para um processo, apenas três páginas podem permanecer simultaneamente na memória. Os espaços podem ser identificados como frame 0, frame 1 e frame 2.

Para a sequência de acessos `1 → 2 → 3 → 1 → 4 → 2 → 5 → 1`, essa capacidade não permite manter todas as páginas solicitadas. Quando uma página ausente precisa entrar e não há frame livre, um **algoritmo de substituição de páginas** escolhe qual página será retirada.

## HIT e PAGE FAULT

Um **HIT** ocorre quando a página solicitada já está carregada na memória. Com a memória `[1, 2, 3]`, acessar a página `2` produz um HIT.

Um **PAGE FAULT** ocorre quando a página solicitada não está presente na memória. Com a mesma memória `[1, 2, 3]`, acessar a página `4` produz um PAGE FAULT.

Se houver frame livre, a página é carregada nesse espaço. Se todos estiverem ocupados, é necessário substituir uma página. Portanto, **uma falta de página não exige que a memória esteja cheia** e não significa necessariamente um erro no programa: pode fazer parte do carregamento normal de uma página ainda ausente.

```text
Programa solicita uma página
           ↓
A página está na memória?
      ┌────┴────┐
     SIM       NÃO
      ↓          ↓
     HIT     PAGE FAULT
                 ↓
         Existe frame livre?
            ┌────┴────┐
           SIM       NÃO
            ↓          ↓
         Carrega    Escolhe página
                    para substituir
                         ↓
                  FIFO / LRU / OPT
```

## Simulação em Python

A simulação reproduz, de forma simplificada, decisões de substituição de páginas. **Não controla diretamente a RAM do computador.**

```python
paginas = [1, 2, 3, 1, 4, 2, 5, 1]
quantidade_frames = 3
```

A lista `paginas` representa a ordem dos acessos: página 1, página 2, página 3, página 1 novamente e assim por diante. A variável `quantidade_frames` limita quantas páginas podem estar carregadas ao mesmo tempo.

A lista `memoria` começa vazia. As variáveis `faltas` e `hits` contam os resultados dos acessos. As implementações a seguir pressupõem uma quantidade de frames inteira e positiva.

## FIFO

**FIFO (First In, First Out)** significa **primeiro que entra, primeiro que sai**. Quando uma página precisa entrar e a memória está cheia, sai a página que está há mais tempo na memória, considerando sua ordem de carregamento.

Com a lista `[1, 2, 3]` em ordem de chegada, a entrada da página `4` remove a página `1`, produzindo `[2, 3, 4]`. Um HIT não altera essa ordem.

### Implementação inicial

```python
paginas = [1, 2, 3, 1, 4, 2, 5, 1]
quantidade_frames = 3

memoria = []
faltas = 0
hits = 0

for pagina in paginas:

    if pagina in memoria:
        hits += 1
        print(f"Página {pagina}: HIT        -> {memoria}")

    else:
        faltas += 1

        if len(memoria) < quantidade_frames:
            memoria.append(pagina)
        else:
            memoria.pop(0)
            memoria.append(pagina)

        print(f"Página {pagina}: PAGE FAULT -> {memoria}")

print("\nResultado")
print("Page Faults:", faltas)
print("Hits:", hits)
```

A condição `pagina in memoria` verifica se a página está carregada. Em caso positivo, incrementa `hits`. Caso contrário, incrementa `faltas` e carrega a página.

- `len(memoria) < quantidade_frames`: ainda existe espaço livre.
- `memoria.pop(0)`: remove a página mais antiga, na posição zero.
- `memoria.append(pagina)`: adiciona a nova página ao final da lista.

A lista representa a **ordem de chegada das páginas**, permitindo identificar qual será removida na próxima substituição.

### Função reutilizável

Uma função permite testar outras sequências e quantidades de frames sem repetir a implementação. O parâmetro `mostrar_passos=True` exibe cada acesso, a memória resultante e a indicação de HIT ou PAGE FAULT. Com `False`, esses passos não são impressos. O retorno é o par `faltas, hits`.

```python
def fifo(paginas, quantidade_frames, mostrar_passos=True):
    memoria = []
    faltas = 0
    hits = 0

    for pagina in paginas:

        if pagina in memoria:
            hits += 1
            resultado = "HIT"

        else:
            faltas += 1
            resultado = "PAGE FAULT"

            if len(memoria) >= quantidade_frames:
                memoria.pop(0)

            memoria.append(pagina)

        if mostrar_passos:
            print(
                f"Página: {pagina:<2} | "
                f"Memória: {str(memoria):<15} | "
                f"{resultado}"
            )

    return faltas, hits
```

### Exemplo com 3 frames

```python
paginas = [1, 2, 3, 1, 4, 2, 5, 1]
faltas, hits = fifo(paginas, 3)
```

| Acesso | Página | Memória após o acesso | Resultado |
| --- | --- | --- | --- |
| 1 | 1 | `[1]` | PAGE FAULT |
| 2 | 2 | `[1, 2]` | PAGE FAULT |
| 3 | 3 | `[1, 2, 3]` | PAGE FAULT |
| 4 | 1 | `[1, 2, 3]` | HIT |
| 5 | 4 | `[2, 3, 4]` | PAGE FAULT |
| 6 | 2 | `[2, 3, 4]` | HIT |
| 7 | 5 | `[3, 4, 5]` | PAGE FAULT |
| 8 | 1 | `[4, 5, 1]` | PAGE FAULT |

Resultado: **6 page faults e 2 hits**. Mesmo acessada no quarto passo, a página 1 continua sendo a primeira candidata a sair, pois o FIFO não atualiza a ordem em um HIT.

### Alterando a quantidade de frames

```python
for frames in [2, 3, 4, 5]:
    faltas, hits = fifo(paginas, frames, mostrar_passos=False)
    print(f"{frames} frames -> Page Faults: {faltas} | Hits: {hits}")
```

| Frames | Page faults | Hits |
| --- | --- | --- |
| 2 | 8 | 0 |
| 3 | 6 | 2 |
| 4 | 6 | 2 |
| 5 | 5 | 3 |

Nessa sequência, passar de 3 para 4 frames mantém a quantidade de faltas. Com 5 frames, as cinco páginas distintas cabem na memória: o primeiro acesso a cada uma gera falta e os demais geram hits.

## LRU

**LRU (Least Recently Used)** significa **menos recentemente utilizada**. A substituição retira a página que está há mais tempo sem ser usada.

A lista mantém a página menos recentemente utilizada no início e a mais recente no final. Se a ordem atual for `[1, 2, 3]` e ocorrer um acesso à página `1`, a ordem passa a ser `[2, 3, 1]`. Se a próxima solicitação for a página `4`, sai a página `2`, produzindo `[3, 1, 4]`.

Essa ordem representa o histórico de uso na simulação, não uma movimentação física das páginas entre frames da RAM a cada HIT.

### Implementação

```python
def lru(paginas, quantidade_frames, mostrar_passos=True):
    memoria = []
    faltas = 0
    hits = 0

    for pagina in paginas:

        if pagina in memoria:
            hits += 1
            resultado = "HIT"

            # A página acabou de ser utilizada.
            # Portanto, ela se torna a mais recente.
            memoria.remove(pagina)
            memoria.append(pagina)

        else:
            faltas += 1
            resultado = "PAGE FAULT"

            if len(memoria) >= quantidade_frames:
                memoria.pop(0)

            memoria.append(pagina)

        if mostrar_passos:
            print(
                f"Página: {pagina:<2} | "
                f"Memória: {str(memoria):<15} | "
                f"{resultado}"
            )

    return faltas, hits
```

Em um HIT, `memoria.remove(pagina)` retira a página de sua posição na lista e `memoria.append(pagina)` a coloca no final. Ela passa a ser a mais recentemente utilizada.

Em um PAGE FAULT com memória cheia, `memoria.pop(0)` remove a menos recentemente utilizada. A página carregada entra no final. A interface e o retorno seguem o mesmo padrão da função `fifo`.

### Exemplo com 3 frames

```python
paginas = [1, 2, 3, 1, 4, 2, 5, 1]
faltas, hits = lru(paginas, 3)
```

| Acesso | Página | Memória em ordem de uso, da menos para a mais recente | Resultado |
| --- | --- | --- | --- |
| 1 | 1 | `[1]` | PAGE FAULT |
| 2 | 2 | `[1, 2]` | PAGE FAULT |
| 3 | 3 | `[1, 2, 3]` | PAGE FAULT |
| 4 | 1 | `[2, 3, 1]` | HIT |
| 5 | 4 | `[3, 1, 4]` | PAGE FAULT |
| 6 | 2 | `[1, 4, 2]` | PAGE FAULT |
| 7 | 5 | `[4, 2, 5]` | PAGE FAULT |
| 8 | 1 | `[2, 5, 1]` | PAGE FAULT |

Resultado: **7 page faults e 1 hit**. No quinto acesso, a página 2 sai porque está há mais tempo sem uso. Como ela é solicitada logo depois, ocorre uma nova falta.

## Comparação entre FIFO e LRU

| Algoritmo | Critério de substituição | Efeito de um HIT na ordem |
| --- | --- | --- |
| FIFO | Página que entrou primeiro | Não altera a ordem de chegada |
| LRU | Página sem uso há mais tempo | Atualiza a página acessada para a posição mais recente |

Os resultados podem divergir quando a ordem de chegada é diferente da ordem de uso. Na sequência anterior, o FIFO teve menos faltas que o LRU. O desempenho depende **do algoritmo e do padrão de acesso**, portanto o LRU não vence necessariamente em toda sequência.

Para comparar outra sequência, mantendo as mesmas condições para os dois algoritmos:

```python
paginas_teste = [7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2]

print(f"{'Algoritmo':<12} {'Frames':<8} {'Faults':<8} {'Hits':<8}")
print("-" * 40)

for frames in [3, 4, 5]:
    faltas_fifo, hits_fifo = fifo(paginas_teste, frames, False)
    faltas_lru, hits_lru = lru(paginas_teste, frames, False)

    print(f"{'FIFO':<12} {frames:<8} {faltas_fifo:<8} {hits_fifo:<8}")
    print(f"{'LRU':<12} {frames:<8} {faltas_lru:<8} {hits_lru:<8}")
```

| Algoritmo | Frames | Page faults | Hits |
| --- | --- | --- | --- |
| FIFO | 3 | 10 | 3 |
| LRU | 3 | 9 | 4 |
| FIFO | 4 | 7 | 6 |
| LRU | 4 | 6 | 7 |
| FIFO | 5 | 6 | 7 |
| LRU | 5 | 6 | 7 |

Nessa sequência de 13 acessos, o LRU apresenta menos faltas com 3 e 4 frames. Com 5 frames, os resultados são iguais.

### Taxas de page faults e hits

A quantidade total de acessos é a soma de faltas e hits:

$$
N = F + H
$$

$$
\text{Taxa de Page Faults} = \frac{F}{N} \times 100
$$

$$
\text{Taxa de Hits} = \frac{H}{N} \times 100
$$

`F` representa a quantidade de page faults, `H` a quantidade de hits e `N` o total de acessos. As taxas são expressas em porcentagem. Para uma sequência não vazia, somam 100%, desconsiderando diferenças de arredondamento.

Com a sequência de 13 acessos e 3 frames:

| Algoritmo | Taxa de page faults | Taxa de hits |
| --- | --- | --- |
| FIFO | $10/13 \times 100 = 76{,}92\%$ | $3/13 \times 100 = 23{,}08\%$ |
| LRU | $9/13 \times 100 = 69{,}23\%$ | $4/13 \times 100 = 30{,}77\%$ |

Quanto menor a taxa de faltas, melhor o resultado segundo esse critério **para aquela sequência e quantidade de frames**.

```python
paginas_teste = [7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2]

for nome, algoritmo in [("FIFO", fifo), ("LRU", lru)]:
    faltas, hits = algoritmo(paginas_teste, 3, False)
    total = faltas + hits

    taxa_fault = (faltas / total) * 100
    taxa_hit = (hits / total) * 100

    print(nome)
    print(f"Taxa de Page Faults: {taxa_fault:.2f}%")
    print(f"Taxa de Hits:        {taxa_hit:.2f}%")
    print()
```

## Anomalia de Belady

A **Anomalia de Belady** ocorre quando aumentar a quantidade de frames aumenta o número de page faults. O FIFO pode apresentar esse comportamento em determinadas sequências.

```python
belady = [1, 2, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5]

for frames in [3, 4]:
    faltas, hits = fifo(belady, frames, False)
    print(f"FIFO com {frames} frames -> {faltas} Page Faults")
```

| Frames | Page faults no FIFO |
| --- | --- |
| 3 | 9 |
| 4 | 10 |

Adicionar um frame piora o resultado nessa sequência: as faltas passam de 9 para 10. A capacidade maior altera a sequência de substituições e as páginas disponíveis nos acessos seguintes. Portanto, **mais frames não garantem menos faltas no FIFO**; a comparação precisa considerar os resultados da execução.

## Algoritmo Ótimo (OPT)

O **Ótimo (OPT)** substitui a página cujo próximo acesso acontecerá **mais distante no futuro**. Uma página que não será mais usada é candidata à remoção antes das que ainda serão necessárias.

Considere a memória `[1, 2, 3]` e os próximos acessos `2, 4, 1, 5, 3`:

- A página 2 será usada imediatamente.
- A página 1 será usada depois.
- A página 3 será usada mais tarde.

Entre essas três páginas, a página 3 tem o próximo uso mais distante. Na sequência indicada, o acesso à página 2 é um HIT; quando a página 4 precisar entrar, a página 3 será removida.

Conhecer os acessos futuros permite escolher a substituição que minimiza as faltas para a sequência e capacidade consideradas. Por isso, o OPT serve como **referência teórica e de comparação**. Um sistema operacional real não consegue aplicá-lo perfeitamente quando a sequência futura é desconhecida.

### Implementação

```python
def otimo(paginas, quantidade_frames, mostrar_passos=True):
    memoria = []
    faltas = 0
    hits = 0

    for i, pagina in enumerate(paginas):

        if pagina in memoria:
            hits += 1
            resultado = "HIT"

        else:
            faltas += 1
            resultado = "PAGE FAULT"

            if len(memoria) < quantidade_frames:
                memoria.append(pagina)

            else:
                futuro = paginas[i + 1:]
                distancias = {}

                for pagina_memoria in memoria:
                    if pagina_memoria in futuro:
                        distancias[pagina_memoria] = futuro.index(pagina_memoria)
                    else:
                        # Se nunca mais será usada, é a melhor candidata a sair.
                        distancias[pagina_memoria] = float("inf")

                pagina_remover = max(distancias, key=distancias.get)
                memoria.remove(pagina_remover)
                memoria.append(pagina)

        if mostrar_passos:
            print(
                f"Página: {pagina:<2} | "
                f"Memória: {str(memoria):<15} | "
                f"{resultado}"
            )

    return faltas, hits
```

`enumerate(paginas)` fornece o índice e a página de cada acesso. A expressão `paginas[i + 1:]` separa os acessos futuros.

Para cada página carregada, `futuro.index(pagina_memoria)` identifica a posição de seu próximo uso. Se ela não aparece novamente, recebe `float("inf")`, representando uma distância infinita. O comando `max(distancias, key=distancias.get)` escolhe a página com maior distância, que é removida para carregar a nova página.

### Comparação com 3 frames

```python
paginas_teste = [7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2]

for nome, algoritmo in [
    ("FIFO", fifo),
    ("LRU", lru),
    ("Ótimo", otimo)
]:
    faltas, hits = algoritmo(paginas_teste, 3, False)
    print(f"{nome:<8} -> Page Faults: {faltas} | Hits: {hits}")
```

| Algoritmo | Page faults | Hits |
| --- | --- | --- |
| FIFO | 10 | 3 |
| LRU | 9 | 4 |
| Ótimo | 7 | 6 |

Para os mesmos 13 acessos, o OPT produz o menor número de faltas, utilizando o conhecimento da sequência futura.


