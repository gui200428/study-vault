
## 1. Loop `for`

O loop `for` é ideal quando você sabe exatamente quantas vezes deseja repetir uma operação.

### Sintaxe

```java
for (inicialização; condição; incremento) {
    // código a ser executado
}
```

### Exemplo

```java
// Imprime números de 1 a 5
for (int i = 1; i <= 5; i++) {
    System.out.println("Número: " + i);
}
```

### Características

- **Inicialização**: Executada apenas uma vez, no início
- **Condição**: Verificada antes de cada iteração
- **Incremento**: Executado após cada iteração
- **Uso típico**: Contadores, índices de arrays

---

## 2. Loop `for-each` (Enhanced for)

O `for-each` é uma versão simplificada do `for` tradicional, ideal para percorrer coleções e arrays.

### Sintaxe

```java
for (tipo elemento : coleção) {
    // código a ser executado
}
```

### Exemplos

```java
// Percorrendo um array
int[] numeros = {1, 2, 3, 4, 5};
for (int numero : numeros) {
    System.out.println("Número: " + numero);
}

// Percorrendo uma lista
List<String> nomes = Arrays.asList("Ana", "Bruno", "Carlos");
for (String nome : nomes) {
    System.out.println("Nome: " + nome);
}
```

### Características

- **Mais limpo**: Sem necessidade de índices
- **Seguro**: Evita erros de índice fora dos limites
- **Limitação**: Não permite modificar a estrutura durante a iteração
- **Uso típico**: Leitura de arrays, listas, conjuntos

---

## 3. Loop `while`

O loop `while` repete enquanto uma condição for verdadeira. A condição é verificada **antes** da execução.

### Sintaxe

```java
while (condição) {
    // código a ser executado
}
```

### Exemplo

```java
int contador = 1;
while (contador <= 5) {
    System.out.println("Contador: " + contador);
    contador++; // Importante: atualizar a variável de controle
}
```

### Características

- **Pré-condição**: Testa a condição antes de executar
- **Pode não executar**: Se a condição inicial for falsa
- **Cuidado**: Risco de loop infinito se a condição nunca se tornar falsa
- **Uso típico**: Quando não sabemos quantas iterações serão necessárias

---

## 4. Loop `do-while`

O loop `do-while` executa o código **pelo menos uma vez**, pois a condição é verificada **após** a execução.

### Sintaxe

```java
do {
    // código a ser executado
} while (condição);
```

### Exemplo

```java
int numero;
Scanner scanner = new Scanner(System.in);

do {
    System.out.print("Digite um número positivo: ");
    numero = scanner.nextInt();
    
    if (numero <= 0) {
        System.out.println("Número inválido! Tente novamente.");
    }
} while (numero <= 0);

System.out.println("Você digitou: " + numero);
```

### Características

- **Pós-condição**: Testa a condição após executar
- **Execução garantida**: Sempre executa pelo menos uma vez
- **Uso típico**: Validação de entrada, menus interativos

---

## Comparação Rápida

|Loop|Quando Usar|Condição|Execução Mínima|
|:-:|:--|:-:|:-:|
|`for`|Número conhecido de iterações|Antes|0 vezes|
|`for-each`|Percorrer coleções/arrays|Implícita|0 vezes|
|`while`|Condição pode ser falsa inicialmente|Antes|0 vezes|
|`do-while`|Precisa executar pelo menos uma vez|Depois|1 vez|

---

## Exemplos Práticos

### 1. Somando elementos de um array

```java
int[] valores = {10, 20, 30, 40, 50};
int soma = 0;

// Usando for tradicional
for (int i = 0; i < valores.length; i++) {
    soma += valores[i];
}

// Usando for-each (mais limpo)
for (int valor : valores) {
    soma += valor;
}
```

### 2. Menu interativo

```java
Scanner scanner = new Scanner(System.in);
int opcao;

do {
    System.out.println("\n=== MENU ===");
    System.out.println("1. Opção A");
    System.out.println("2. Opção B");
    System.out.println("0. Sair");
    System.out.print("Escolha: ");
    
    opcao = scanner.nextInt();
    
    switch (opcao) {
        case 1:
            System.out.println("Você escolheu A");
            break;
        case 2:
            System.out.println("Você escolheu B");
            break;
        case 0:
            System.out.println("Saindo...");
            break;
        default:
            System.out.println("Opção inválida!");
    }
} while (opcao != 0);
```

### 3. Lendo arquivo linha por linha

```java
Scanner arquivo = new Scanner(new File("dados.txt"));

while (arquivo.hasNextLine()) {
    String linha = arquivo.nextLine();
    System.out.println(linha);
}

arquivo.close();
```

---

## Dicas Importantes

1. **Evite loops infinitos**: Sempre certifique-se de que a condição será alterada
2. **Use `for-each` quando possível**: Mais legível e seguro para coleções
3. **Escolha o loop certo**: Considere se você sabe o número de iterações
4. **Cuidado com modificações**: Evite alterar a estrutura durante `for-each`
5. **Performance**: `for` tradicional é geralmente mais rápido que `for-each` para arrays grandes