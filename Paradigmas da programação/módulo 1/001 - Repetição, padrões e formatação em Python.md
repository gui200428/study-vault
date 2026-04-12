
## Código base:

---

```python
# --- Cabeçalho Decorativo ---
print("#############################")
print("# Mostrando padrões na tela #")
print("#############################\n\n")

# --- Entrada de Dados ---
contador = int(input("Digite o número para padrão: "))
print()

# --- Lógica do Padrão ---
for x in range(1, contador + 1):
    padrao = "#" * x
    print(f"{x}\t{padrao}")
```


## Elementos:

### 1- Print com formatação:

```python
print(f"{x}\t{padrao}")
```

**Comandos de formatação de texto:**

- Por padrão, o print ja faz a quebra de linhas
- \n : quebra linha
- \t: equivalente a tecla tab do teclado, tem a função de dar um espaço para a próxima tabulação do console.

**f-strings**
- as f-strings (prefixadas com `f`) permitem inserir variáveis ou expressões diretamente dentro da _string_, usando chaves `{}`.
### 2. Entrada de dados e tipagem dinâmica

**input()** : Pausa a execução e aguarda a entrada do usuário. É possível inserir a mensagem do input dentro do próprio input. Diferente do C, que precisaria de um printf e um scanf.

```python
contador = input("Digite o número para padrão: ")
```


**Type casting (Conversão de tipos):** É o processo de converter um dado de um tipo em outro.

- Por padrão, o input do python usa o tipo string. Para que seja atribuído outro tipo a uma variável, o input precisa passar por uma conversão de tipos.

```python
# int atribuido a variável contador
contador = int(input("Digite o número para padrão: "))
```


**Tipos padrão:**

**1. int():**

int(“25”) → 25

int(3.9) → 3

**2. float():**

float(5) → 5.0

float(“10.4”) → 10.4

**3. str():**

str(100) → “100”

**4. bool():**

bool(1) → True

bool(0) → False

bool(“banana”) → True

bool(10) → True


### 3. Iteração com o for e a função range()

#### Função range()
A função pode receber até três argumentos: `range(start, stop, step)`.
Sintaxe:

```python
range(start, stop, step)
```

- **`start` (Início):** Onde a contagem começa. É **inclusivo**. (Padrão: 0) 
- **`stop` (Parada):** Onde a contagem termina. É **exclusivo** (nunca inclui este número). (Obrigatório) 
- **`step` (Passo):** O incremento a cada iteração. Pode ser negativo para contagens regressivas. (Padrão: 1)


```python
# Apenas com o 'stop' (conta de 0 até 4)
for i in range(5):
    print(i) # Saída: 0, 1, 2, 3, 4
  
# Com 'start' e 'stop' (conta de 2 até 5)
for i in range(2, 6):
    print(i) # Saída: 2, 3, 4, 5

# Com 'start', 'stop' e 'step' (números pares de 0 a 8)
for i in range(0, 10, 2):
    print(i) # Saída: 0, 2, 4, 6, 8

# Contagem regressiva (passo negativo)
for i in range(5, 0, -1):
    print(i) # Saída: 5, 4, 3, 2, 1
    
```


#### Laço for

Diferente do C / java, que possui um for dividido em 3 partes (init, condição, incremento), o python possui um for diferente. Ele é responsável para percorrer coleções de dados que podem ser percorridas.

O for permite varrer por diferentes tipos de dados sem precisar de um índice ou variável de contagem.

```python
# Iterando sobre uma lista
cores = ["roxo", "preto", "branco"]
for cor in cores:
    print(cor)

# Iterando sobre uma string (strings são iteráveis de caracteres)
palavra = "Python"
for letra in palavra:
    print(letra) # Imprime uma letra por linha

# Lista de diferentes tipos
lista = ["banana", 1, "morango", 3.1]
for variavel in lista:
	print(variavel)
```


