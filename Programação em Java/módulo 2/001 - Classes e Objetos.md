#faculdade #resumos #java 
## 1. Conceitos Fundamentais

A base da POO é a relação entre a definição (Classe) e a concretização (Objeto).

### Classe (Molde)
É o **Modelo / Template** utilizado para definir a estrutura. Ela organiza os dados (atributos) e as regras (métodos). Não ocupa espaço na memória até ser instanciada (exceto membros estáticos).

```java
public class Cliente {
    // Atributos (Estado)
    private String nome; // Apenas a classe visualiza (private)
    private double limiteCredito; // 'double' é comum para decimais em Java
    private static int clienteID; // 'static' pertence à classe
}
```

### Objeto (A Instância)
É a **utilização do modelo** com valores e estados reais. É a materialização da classe na memória.

```java
// Instanciando uma classe (Criando objetos)
Cliente objCliente1 = new Cliente();
Cliente objCliente2 = new Cliente();
```

---

## 2. Métodos (Comportamento)

Métodos são as ações que a classe pode executar. São as formas de interagir com os dados.

### Tipos de Escopo (Static vs. Instância)

* **Métodos de Instância (Padrão):** Pertencem ao **objeto**. Exigem que você crie um `new Cliente()` para serem usados.
* **Métodos de Classe (`static`):** Pertencem à **classe**.
    * Utiliza-se a palavra reservada `static`.
    * Não precisam de uma instância para serem acessados.
    * Todos os objetos compartilham o mesmo valor/método, pois ele pertence à classe, não aos objetos individuais.

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

### Chamadas de Métodos

![[Pasted image 20251122155548.png]]

---

## 3. Modificadores de Acesso (Encapsulamento)

Servem para definir a **visibilidade** de atributos e métodos, protegendo o código.

| Modificador | Visibilidade | Descrição |
| :--- | :--- | :--- |
| **`public`** | Global | Acessível por qualquer classe, em qualquer lugar do projeto. |
| **`protected`** | Hereditária | Acessível pela própria classe, classes do mesmo pacote e subclasses (herança). |
| **`default`** | Pacote | (Quando não se escreve nada). Acessível apenas por classes do mesmo pacote. |
| **`private`** | Restrita | Acessível **apenas** dentro da própria classe. Nem as subclasses têm acesso direto. |


**Declarações:**

```java
public decimal limiteCredito;
private String nome;
protected int valor;
//default
double preco;
```


---

## 4. Encapsulamento

Em algumas situações, as variáveis não podem ser acessadas diretamente, devido a regras de negócio. Uma forma de garantir validações é impossibilitar o acesso direto a variável e fornecer o acesso apenas através de métodos onde o acesso pode ser controlado.


### Métodos de encapsulamento GET e SET


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


---

## 5. Sobrecarga de Método

Criar vários métodos com o **mesmo nome**, mas **parâmetros diferentes** (assinatura diferente). Ocorre na **mesma classe**.

```java
public class Cliente {
	private String nome;
}

public void setNome(String nome) {
	this.nome = nome;
}

public void setNome(String nome, String sobrenome) {
	this.nome = nome + " " + sobrenome;
}

public void setNome(int valor){
	this.nome = "" + valor;
}
```


---

## 6. Sobrescrita

Um método herdado da classe Pai é **refeito/reescrito** na classe Filho para ter um comportamento específico. Ocorre na **herança**.


```java
public class Pai {
	public void add(Object object){
		System.out.println(object);
	}
}

public class Filho extends Pai {
	public void add(Object object){
		object = null;
	}
}

public class Sobre extends Pai {
	public void add(Object object){
		object = new Sobre;
	}
}
```

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

---

## 7. Métodos Fundamentais (Classe Object)

Toda classe em Java herda implicitamente da classe `Object`.

### To String
Converte o objeto em uma representação de texto (String). Útil para logs e debug.

```java
public String toString(){
	return "Meu nome é " + nome;
}
System.out.println(p);
```

```java 
public String toString(){ 
	return "Cliente: " + this.nome; 
} // Uso:
System.out.println(objCliente);// -> Vai imprimir "Cliente: [nome]" 

```

### Equals
Define a regra de comparação entre dois objetos. Por padrão, o `==` compara o endereço de memória, o `equals` deve comparar o **conteúdo**.


```java
public boolean equals(Object o){
	if(o instanceof Cliente){ 
		Cliente outro = (Cliente) o; 
		return this.nome.equals(outro.nome);
	} return false;	
}

Cliente p1 = new Cliente(); 
p1.setNome("Gui");
Cliente p2 = new Cliente(); 
p2.setNome("Gui");

if(p1 == p2) { ... } // FALSO (Endereços de memória diferentes)
if(p1.equals(p2)) { ... } // VERDADEIRO (Conteúdo igual, se implementado)
```


---

## 8. HASHCODE

Gera um número inteiro (hash) que serve como uma "impressão digital" do objeto. Sua principal função é permitir que o objeto seja armazenado e encontrado rapidamente em estruturas baseadas em hash (como `HashMap`, `HashSet`, `Hashtable`).

![[Pasted image 20251123131343.png]]

**Regra:** 
1. Se dois objetos são iguais pelo método `equals()`, eles **DEVEM** ter o mesmo `hashCode()`. 
2. Se dois objetos têm `hashCode()` diferentes, eles com certeza são diferentes.

Método que retorna um código hash de um objeto. Ele é usado normalmente para agilizar a busca em collections.

```java
public int hashCode(){
	// Retorna o hash baseado nos atributos usados no equals
	// O número primo 31 é frequentemente usado para evitar colisões
	return Objects.hash(nome, id);
	
	// Ou a versão simplificada que você usou (se for apenas um atributo):
	return nome.hashCode();
}
```


## 9. Herança
A herança permite que uma classe (Filha/Subclasse) herde atributos e métodos de outra classe (Pai/Superclasse). O principal objetivo é o **reaproveitamento de código** e a criação de uma hierarquia lógica.

A regra fundamental é a relação **"É UM"** (*Is-A*).
- Um Poodle **é um** Cachorro. 
- Um Carro **é um** Veículo.


### Sintaxe Básica
Utiliza-se a palavra-chave **`extends`**. Em Java, uma classe só pode herdar de **uma** única classe pai (não existe herança múltipla de classes).

```java

// CLASSE PAI (Superclasse)
public class Cachorro {
	protected String nome; // protected: filhos podem acessar direto
	
	public Cachorro(String nome) {
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


---
### Próximo conteúdo:

[[002 - Interfaces e Classes abstratas]]
