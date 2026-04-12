
## Exceção

**Definição:** é um problema que ocorre em tempo de execução e interrompe o fluxo normal do programa.

**Exemplos comuns:**
- Dividir por zero
- Converter texto inválido para número
- Acessar uma posição inexistente em um vetor
- Abrir um arquivo que não existe

### Tipos:

#### Checked Exception
- Compilador obriga a tratar (com try/catch) ou declarar (com throws).
- Ex.: IOException, FileNotFoundException.
#### Unchecked Exception 
- São exceções em tempo de execução. Compilador não obriga a tratar.
- Ex.: NullPointerException, ArithmeticException, NumberFormatException.

#### Error
- Problemas da JVM
- Ex.: OutOfMemoryError.


## Estrutura para o tratamento:


### 1- try / catch / finally (Estrutura Básica)
- Tem a função de executar um bloco de código (try), capturar o erro para evitar que o programa quebre (catch), e executar um bloco final independente de ter dado erro ou não (finally).
- O finally é útil para fechar recursos, como scanners, arquivos ou conexões com o banco de dados.

**Exemplo:**

```java
try {
    int resultado = a / b; // pode dar erro se b = 0
    System.out.println("Resultado: " + resultado);
} catch (ArithmeticException e) {
    System.out.println("Erro: não dá para dividir por zero!");
} finally {
    System.out.println("Finally: sempre executa (com erro ou sem erro).");
    sc.close();
}
```


### 2- Multi-catch 

Serve para capturar e tratar mais de um tipo específico de erro no mesmo bloco de código. A regra fundamental aqui é que a exceção mais genérica (**Exception**) deve vir sempre por último, senão ela "engole" as exceções mais específicas que estiverem abaixo dela.

```java
try {
    int numero = Integer.parseInt(texto);
    System.out.println("Número: " + numero);
} catch (NumberFormatException e) {
    System.out.println("Erro: isso não é um número!");
} catch (Exception e) {
    System.out.println("Erro genérico: " + e.getMessage());
}
```


### 3- Throw (lançar exceção)

Serve para lançar uma exceção manualmente no momento em que detectar que uma regra do sistema foi violada. Forma de dizer ativamente que algo deu errado.

```java
static void validarIdade(int idade) {
    if (idade < 18) {
        throw new IllegalArgumentException("Idade mínima é 18!");
    }
    System.out.println("Acesso liberado!");
}
```


### 4- Throws (declarar que a exceção pode ocorrer)

Serve para declarar na assinatura do método que ele pode gerar uma exceção verificada. Forma de avisar ao compilador e a que for usar o método que aquele erro pode ocorrer. Passando a responsabilidade de tratar este erro “para frente”.

```java
static void lerArquivo() throws IOException {
    FileReader fr = new FileReader("arquivo_inexistente.txt");
    fr.close();
}
```


### 5- Exceção personalizada

Serve para criar tipos de erros nas regras da aplicação. Herdando o comportamento da classe padrão **Exception**

```java
class SaldoInsuficienteException extends Exception {
    public SaldoInsuficienteException(String msg) {
        super(msg);
    }
}
```


---

## Boas práticas

- Use exceção para casos excepcionais, não para “controle normal” do sistema
- Mensagens claras: throw new ...("Explique o problema e o valor")
- Evite catch (Exception e) em excesso (só quando fizer sentido)
- Nunca engula erro vazio: não faça catch(Exception e){} sem nada
- Em projetos reais: log (ex.: logger.error(...))