
## Tipos de variáveis

- boolean
- byte
- char
- string
- int
- float
- long 
- double


## A estrutura da classe main

Em java, precisamos de um objeto que vai representar o bloco principal do script. Ele é declaro da seguinte forma:

```java
public class Main{
	public static void main(String[] args){
		System.out.println("Hello, world!");
	}
}
```


## Input / output de dados


### Input:
→ Para inserir dados, o scanner. 

**Processo para usar o scanner:**

1. Importar o scanner

```java
import java.util.Scanner;
```

2. Iniciar o scanner e atribuir ele a um novo objeto do tipo scanner

```java
Scanner input = new Scanner(System.in);
```

3. Usar o objeto do tipo scanner: atribuir ele a uma variável

```java
int numero = input.nextInt();
```


**Métodos do input**

| Tipo   | Operador     |
| ------ | ------------ |
| float  | nextFloat()  |
| double | nextDouble() |
| String | nextLine()   |
| int    | nextInt()    |




### Output: 
→ Para printar no Java, usamos o seguinte comando:

```java
System.out.println("Hello, world!"); // usa linha inteira

System.out.print("Hello, world!"); // usa só o espaço necessario da linha
```


