#faculdade #resumos #java 
## 1. Interfaces

É um contrato que define um conjunto de métodos que uma classe deve implementar.
Exemplo: lista de tarefas, a interface define as tarefas, mas cada classe que a implementa decide como realizar essas tarefas.

```java
// Declaração da interface
public interface Animal {
	void makeSound();
}

// Implementação da interface
public class Dog implements Animal {
	@Override
	public void makeSound() {
		System.out.println("Latir!");
	}
}
```


**Importante:** diferente de uma herança de classes, uma classe pode implementar várias interfaces.


![[Pasted image 20251123182814.png]]

**Exemplo:**

```java
// Contrato 1: Coisas que nadam
public interface Nadador {
    void nadar();
}

// Contrato 2: Coisas que voam
public interface Voador {
    void voar();
}

// O Pato assume o compromisso de fazer as duas coisas
public class Pato implements Nadador, Voador {
    
    @Override
    public void nadar() {
        System.out.println("O pato está boiando...");
    }

    @Override
    public void voar() {
        System.out.println("O pato voou para longe!");
    }
}
```


---

## 2. Classes abstratas

Uma classe abstrata é um “rascunho incompleto” de uma classe. Ela não pode ser instanciada diretamente (new AnimalAbstrato()). Ela serve apenas de base para outras classes.

→ Pode ter métodos concretos (com código) e abstratos (sem código).
→ Pode ter atributos de estado (variáveis).


```java
public abstract class Funcionario {
    protected String nome;
    protected double salario;

    // Método Concreto (Igual para todos)
    public void baterPonto() {
        System.out.println("Entrada registrada no sistema.");
    }

    // Método Abstrato (Cada cargo calcula de um jeito)
    public abstract void calcularBonus();
}

public class Gerente extends Funcionario {
    @Override
    public void calcularBonus() {
        this.salario = this.salario * 1.2; // 20% de bônus
    }
}
```


---

## 3. Interfaces X Classes Abstratas

| Interfaces                                                                                                                                                           | Classes Abstratas                                                                                                                                 |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Uma interface não é considerada uma Classe e sim uma Entidade.                                                                                                       | As classes abstratas devem conter pelo menos um método abstrato, que não tem corpo.                                                               |
| Não possui implementação, apenas assinatura, ou seja, apenas a definição dos seus métodos sem o corpo.                                                               | É um tipo especial de classe que não há como criar instâncias dela.                                                                               |
| Todos os métodos são abstratos.                                                                                                                                      | É usada apenas para ser herdada, funciona como uma super classe.                                                                                  |
| Seus métodos são implicitamente Públicos e Abstratos.                                                                                                                | Uma grande vantagem é que força a hierarquia para todas as sub-classes.                                                                           |
| Não há como fazer uma instância de uma Interface e nem como criar um Construtor.                                                                                     | É um tipo de contrato que faz com que as sub-classes contemplem as mesmas hierarquias e/ou padrões.                                               |
| Uma classe pode implementar diversas interfaces.                                                                                                                     | Uma classe pode herdar somente uma classe.                                                                                                        |
| Funcionam como um tipo de “contrato”, onde são especificados atributos, métodos e funções que as classes que implementem essa interface são obrigadas a implementar. | Uma classe abstrata pode fornecer código completo, código padrão ou ter apenas a declaração de seu esqueleto para ser posteriormente sobrescrita. |
| Uma interface não pode conter qualquer tipo de código, muito menos código padrão.                                                                                    | Pode conter constantes estáticas e de instância.                                                                                                  |
| Suporte somente constantes do tipo estática.                                                                                                                         | Se você incluir um novo método em uma classe abstrata você tem a opção de fornecer uma implementação padrão para ele.                             |
| Se você incluir um novo método em uma interface você precisa ajustar todas as implementações dessa interface.                                                        | Se você incluir um novo método em uma classe abstrata, você tem a opção de fornecer uma implementação para ele.                                   |

| **Característica** | **Interface**                                     | **Classe Abstrata**                          |
| ------------------ | ------------------------------------------------- | -------------------------------------------- |
| **Foco**           | O que o objeto **FAZ** (Capacidades).             | O que o objeto **É** (Identidade).           |
| **Herança**        | Uma classe implementa várias (`implements A, B`). | Uma classe estende apenas uma (`extends A`). |
| **Atributos**      | Apenas constantes (`public static final`).        | Qualquer tipo de variável de estado.         |
| **Construtor**     | Não tem.                                          | Pode ter (para inicializar atributos).       |
|                    |                                                   |                                              |


---

## 4. Classe Interna

Utilizada para manipular dados de processamento interno. É limitada pela classe que precisa dela. A classe interna tem acesso aos dados primitivos declarados pela classe que a chamou.

```java
public class Calculadora {
    private int resultado = 0; // Atributo privado da Externa
    
    // Método da Externa usando a Interna
    public void executarSoma(int valor) {
        Soma s = new Soma();
        s.adicionar(valor);
    }
    
    public int getResultado() {
        return this.resultado;
    }

    // --- CLASSE INTERNA ---
    private class Soma {
        public void adicionar(int valor) {
            // ACESSO DIRETO: Acessa e modifica 'resultado' da classe pai
            // sem precisar de getters ou setters.
            resultado += valor; 
        }
    }
}
```


### Classe interna - Instanciação externa

```java
public static void main(String[] args){
	Calculadora c = new Calculadora();
	Calculadora.Soma s = c.new Soma();
	s.somar();
}
```


### Classe interna - Métodos

```java
protected void Calcular(){
	class Calculo{
		private int soma;
		public void setSoma(int soma){
			this.soma = somal
		}
		public int getSoma(){
			return soma;
		}
	}
}
```


---

## 5. Classe anônima

Toda classe que não é declarada explicitamente, mas esta sendo chamada no código. Representa o comportamento de uma classe ou de uma interface.

É uma classe interna **sem nome**, definida no exato momento da instanciação. Geralmente é usada para sobrescrever métodos de uma classe ou implementar uma interface para uso único e imediato.

```java
public interface Animal {
    void fazerSom();
}

public class Main {
    public void main(String[] args) {
        
        // Estamos instanciando a interface diretamente?
        // NÃO! O Java cria uma classe sem nome que implementa Animal.
        Animal animalMisterioso = new Animal() {
            @Override
            public void fazerSom() {
                System.out.println("Grrruuuahhh (Som único deste objeto)");
            }
        };

        animalMisterioso.fazerSom();
    }
}
```

