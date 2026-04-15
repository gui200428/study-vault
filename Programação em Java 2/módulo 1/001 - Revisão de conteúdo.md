2
## Modificadores de Acesso (Encapsulamento)

Servem para definir a **visibilidade** de atributos e métodos, protegendo o código.

| Modificador     | Visibilidade | Descrição                                                                           |
| :-------------- | :----------- | :---------------------------------------------------------------------------------- |
| **`public`**    | Global       | Acessível por qualquer classe, em qualquer lugar do projeto.                        |
| **`protected`** | Hereditária  | Acessível pela própria classe, classes do mesmo pacote e subclasses (herança).      |
| **`default`**   | Pacote       | (Quando não se escreve nada). Acessível apenas por classes do mesmo pacote.         |
| **`private`**   | Restrita     | Acessível **apenas** dentro da própria classe. Nem as subclasses têm acesso direto. |


**Declarações:**

```java
public decimal limiteCredito;
private String nome;
protected int valor;
//default
double preco;
```


---

## Encapsulamento

Serve para ocultar e proteger o estado interno de um objeto. Tem a função de impedir que os dados sejam modificados diretamente fora da classe.


### Métodos de encapsulamento GET e SET

Servem como porta de entrada (set) e saída (get) para os atributos protegidos com o encapsulamento. Permitem a implementação de lógicas de validação para impedir que dados inválidos sejam atribuídos.


```java
public class Cliente {
	private String nome; // Ninguém acessa diretamente
}

public String getNome(){
	return this.nome;
}

public void setNome(String nome){
	this.nome = nome;
}
```


## Herança
A herança permite que uma classe (Filha/Subclasse) herde atributos e métodos de outra classe (Pai/Superclasse). O principal objetivo é o **reaproveitamento de código** e a criação de uma hierarquia lógica.

A regra fundamental é a relação **"É UM"**.
- Um Poodle **é um** Cachorro. 
- Um Carro **é um** Veículo.


### Sintaxe Básica
Utiliza-se a palavra-chave **`extends`**. Em Java, uma classe só pode herdar de **uma** única classe pai (não existe herança múltipla de classes).

```java

// CLASSE PAI (Superclasse)
public class Cachorro {
	protected String nome; // protected: filhos podem acessar direto
	
	public cachorro(String nome) {
		this.nome = nome;
	}

	public void latir() {
		System.out.println("latido genérico!");
	}
}

// CLASSE FILHA (Subclasse)
public class Poodle extends Cachorro {
	private String tamanhoDoPelo; // Atributo exclusivo do filhos
	
	public Poodle(String nome, String tamanhoDoPelo) {
		// 'super' chama o construtor da classe pai
		super(nome);
		this.tamanhoDoPelo = tamanhoDoPelo;
	}

	// Sobrescrita (Override) de método do pai
	@Override
	public void latir() {
		System.out.println("latido de Poodle!");
	}

	// Método exclusivo do filho
	public void cortarPelo() {
		System.out.println("Cortando pelo...");
	}
}
```



## Sobrescrita de métodos (polimorfismo / @override)

Um método herdado da classe Pai é **refeito/reescrito** na classe Filho para ter um comportamento específico. Ocorre na **herança**.


```java 
public class Pai {
	public void add(Object object){
		System.out.println("Adicionando no Pai: " + object);
	} 
} 

public class Filho extends Pai {
	// Reescrevendo o comportamento do pai
	@Override public void add(Object object){ 
		object = null; // Comportamento diferente 
	} 
} 
```


### Sobrecarga de Métodos (Overloading)

É a capacidade de criar mais de um método com o **mesmo nome**, mas com **parâmetros diferentes**.

```java
// Exemplo 1: Recebe um valor float
public void aumentarLimite(float val) {
    limiteCredito += val;
}

// Exemplo 2: Recebe um objeto Cliente
public void aumentarLimite(Cliente c) {
    System.out.println("Limite aumentado baseado no cliente");
}

// Exemplo 3: Recebe múltiplos parâmetros
public void aumentarLimite(String nome, int limite, int clienteID) {
    System.out.println("Limite aumentado com dados completos");
}
```


### Instanciação de objetos:

Serve para materializar o conceito. A classe é apenas uma "planta" ou um molde. A palavra reservada `new` aloca um espaço na memória e cria o objeto real para ser operado no sistema.

```java
// No arquivo Main.java
Person p = new Person();
```
