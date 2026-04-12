
## Estrutura principal:

```c#
using System;

class Program
{
    static void Main(string[] args)
    {
        // O código começa a rodar aqui
    }
}
```


**Sendo:**
1. **Using:** equivalente ao import do python ou o `#include`  do C.
2. **class Program:** c# é uma linguagem orientada a objetos, qualquer código deve estar dentro de uma classe.
3. **static void Main:** Este é o ponto principal do programa, o sistema procurar especificamente por este método para iniciar a execução. Tudo que estiver fora do método principal precisa ser chamado por ele para rodar.

### Outro uso do Using:

→ A palavra `using` tem um segundo significado completamente diferente de importar bibliotecas, quando usado como um bloco de execução.

```c#
using (var connection = new MySqlConnection(connectionString))
{
    connection.Open();
    // Faz consultas no banco...
}
```


Ele é usado para garantir que o bloco seja encerrado, mesmo que ocorra qualquer erro fatal no programa. 
O não fechamento dessa conexão, causaria vazamento de memória.


### Print do c sharp

```c#
Console.WriteLine("Hello World!");
```

#### Equivalente do f-string do python:

→ Ai usar o $ fora das aspas e as chaves dentro da string, podemos injetar variáveis no texto.

```c#
Console.WriteLine($"Erro: {ex.Message}");
```


### Tratamento de exceções: (try-catch)

C# utiliza blocos try/catch para impedir que o programa quebre. Ele serve como tratamento de erros.

```c#
try 
{
    // Tenta conectar ao banco
}
catch (MySqlException ex) 
{
    // Captura apenas erros específicos do MySQL
    Console.WriteLine($"Erro MySQL: {ex.Message}");
}
catch (Exception ex) 
{
    // Captura qualquer outro erro genérico
    Console.WriteLine($"Erro genérico: {ex.Message}");
}
```

**Obs:** A ordem importa, o C# avalia os catchs de cima para baixo. É fundamental deixar o erro mais específico primeiro e o mais genérico por último.

