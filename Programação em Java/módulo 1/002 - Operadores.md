
# Tabela de Operadores em Java

| Categoria       | Operador | Descrição                    | Exemplo de Uso          |
| :-------------- | :------: | :--------------------------- | :---------------------- |
| **Aritméticos** |   `+`    | Adição                       | `int soma = a + b;`     |
|                 |   `-`    | Subtração                    | `int dif = a - b;`      |
|                 |   `*`    | Multiplicação                | `int prod = a * b;`     |
|                 |   `/`    | Divisão                      | `int quot = a / b;`     |
|                 |   `%`    | Módulo (resto da divisão)    | `int resto = a % b;`    |
| **Atribuição**  |   `=`    | Atribuição simples           | `int a = 10;`           |
|                 |   `+=`   | Atribuição com adição        | `a += 5;` // a = a + 5  |
|                 |   `-=`   | Atribuição com subtração     | `a -= 5;` // a = a - 5  |
|                 |   `*=`   | Atribuição com multiplicação | `a *= 2;` // a = a * 2  |
|                 |   `/=`   | Atribuição com divisão       | `a /= 2;` // a = a / 2  |
|                 |   `%=`   | Atribuição com módulo        | `a %= 3;` // a = a % 3  |
| **Relacionais** |   `==`   | Igual a                      | `if (a == b)`           |
|                 |   `!=`   | Diferente de                 | `if (a != b)`           |
|                 |   `>`    | Maior que                    | `if (a > b)`            |
|                 |   `<`    | Menor que                    | `if (a < b)`            |
|                 |   `>=`   | Maior ou igual a             | `if (a >= b)`           |
|                 |   `<=`   | Menor ou igual a             | `if (a <= b)`           |
| **Lógicos**     |   `&&`   | E Lógico (AND)               | `if (a > 0 && b > 0)`   |
|                 |   \|\|   | OU Lógico (OR)               | `if (a > 0 \|\| b > 0)` |
|                 |   `!`    | NÃO Lógico (NOT)             | `if (!condicao)`        |
| **Unários**     |   `++`   | Incremento (adiciona 1)      | `a++;` ou `++a;`        |
|                 |   `--`   | Decremento (subtrai 1)       | `a--;` ou `--a;`        |
|                 |   `-`    | Inversão de sinal            | `int neg = -a;`         |

## Conversão de tipos

# Tabela de Conversão de Tipos em Java

Esta tabela mostra como converter valores entre os tipos primitivos mais comuns e String.

### De String para Tipos Numéricos

| Tipo de Destino | Método de Conversão    | Exemplo de Código                                      |
| :-------------- | :--------------------- | :----------------------------------------------------- |
| `int`           | `Integer.parseInt()`   | `String s = "120"; int i = Integer.parseInt(s);`       |
| `double`        | `Double.parseDouble()` | `String s = "3.14"; double d = Double.parseDouble(s);` |
| `float`         | `Float.parseFloat()`   | `String s = "9.81"; float f = Float.parseFloat(s);`    |
| `long`          | `Long.parseLong()`     | `String s = "100000"; long l = Long.parseLong(s);`     |
| `short`         | `Short.parseShort()`   | `String s = "10"; short sh = Short.parseShort(s);`     |
| `byte`          | `Byte.parseByte()`     | `String s = "5"; byte b = Byte.parseByte(s);`          |

### De Tipos Numéricos para String

| Tipo Original | Método de Conversão      | Exemplo de Código                              |
| :------------ | :----------------------- | :--------------------------------------------- |
| `int`         | `String.valueOf()`       | `int i = 120; String s = String.valueOf(i);`     |
| `double`      | `String.valueOf()`       | `double d = 3.14; String s = String.valueOf(d);` |
| `float`       | `String.valueOf()`       | `float f = 9.81; String s = String.valueOf(f);`  |
| `long`        | `String.valueOf()`       | `long l = 100000; String s = String.valueOf(l);` |
| `qualquer`    | `"" + valor` (Concatenação) | `int i = 10; String s = "" + i;` // Funciona para todos |

### Entre Tipos Numéricos (Casting Explícito e Implícito)

| Conversão                   | Tipo     | Descrição                                         | Exemplo de Código                |
| :-------------------------- | :------- | :------------------------------------------------ | :------------------------------- |
| `int` para `double`         | Implícita | Ocorre automaticamente, sem perda de dados.       | `int i = 10; double d = i;`      |
| `double` para `int`         | Explícita | **Exige cast**. Há perda da parte decimal (truncamento). | `double d = 9.99; int i = (int) d;` // i valerá 9 |
| `long` para `int`           | Explícita | **Exige cast**. Pode haver perda de dados se o valor for muito grande. | `long l = 120L; int i = (int) l;` |