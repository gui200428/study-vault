## Definição:

- O **Spring boot** é um framework que facilita a criação de aplicações Java utilizando o ecossistema spring. Spring boot automatiza processos e elimina configurações complexas.

**Vantagens:**
- Auto-configuração
- Servidor embutido
- Integração com banco de dados
- Alta produtividade

**Estrutura do Projeto**
src/
└── main/
	├── java/
	└── resources/
pom.xml

## Inversão de Controle (IoC) e injeção de dependência (DI)

Tem a função de tirar a responsabilidade do desenvolvedor de instanciar objetos manualmente. Com a finalidade de evitar que o comando **new** seja espalhado por todo código.
O spring boot assume a responsabilidade de criar os objetos (**inversão de controle**) e entrega eles prontos automaticamente onde for necessário (**injeção de dependência**). 

```java
@Service
public class ProdutoService {
	public String mensagem() {
		return "Serviço funcionando";
	}
}

@RestController
public class ProdutoController {
    private final ProdutoService service;

    // O Spring injeta automaticamente o ProdutoService aqui no construtor
    public ProdutoController(ProdutoService service) {
        this.service = service;
    }

    @GetMapping("/teste")
    public String teste() {
        return service.mensagem();
    }
}
```

#### Tipos de injeção:

- Construtor 
- Setter
- Campo (@Autowired)


## Arquitetura em camadas

- Serve para organizar o projeto e dividir responsabilidades de maneira definida, facilitando a escalabilidade do sistema. 
- Utiliza 3 pontos principais:

1. **Controller:** Porta de entrada. Serve exclusivamente para receber as requisições HTTP e repassar os pedidos adiante.
2. **Service:** É o cérebro. Serve para armazenar as regras de negócio e validações da aplicação.
3. **Repository:** É o acesso. Serve unicamente para se conectar com o banco de dados.

Controller → Service → Repository → Banco de dados

### Detalhamento: (CRUD)

![[Pasted image 20260412124110.png]]

### 1. Model (Entity) 
- Serve como model da informação. É a classe de modelo que representa a estrutura exata do que será salvo e manipulado no banco de dados.

```java
public class Produto {
    private String id;
    private String nome;
}
```


### 2. Repository
- Serve para abstrair a complexidade do banco de dados. Herda as funcionalidades dos conectores do Spring Data como o **MongoRepository**.  
- Acesso a métodos como **findAll(), save(), e delete(),** sem precisar escrever nenhuma query manualmente.

```java
public interface ProdutoRepository extends MongoRepository<Produto, String> {
}
```


### 3. Service
- Serve para centralizar o processamento real da aplicação. O controlador chama o serviço, o serviço executa a lógica necessária (e usa o repositório se precisar buscar algo do banco) e então devolve a resposta final. A anotação **@Service** avisa ao framework que essa classe contém regras de negócio.

```java
@Service
public class ProdutoService {
    
    @Autowired
    private ProdutoRepository repository;

    public List<Produto> listar() {
        return repository.findAll();
    }
}
```


### 4. Controller
- Serve para expor as funções do backend para a internet. A anotação **@RestController** é definida como gerenciador de APIs e o **@RequestMapping(“/produtos”)** define o endereço base da URL. 
- A anotação **@GetMapping** atrela o método à requisição HTTP específica.

```java
@RestController
@RequestMapping("/produtos")
public class ProdutoController {
    
    @Autowired
    private ProdutoService service;

    @GetMapping
    public List<Produto> listar() {
        return service.listar();
    }
}
```



---

## Banco de dados H2

**Definição:** Banco de dados leve utilizado para prototipagem e desenvolvimento.
**Característica:** É um banco de dados em memória. Ele só retém os dados enquanto a aplicação esta rodando.

**Configuração:**

```java
spring.datasource.url=jdbc:h2:mem:testdb
```

jdbc - conexão java com o banco de dados
h2 - banco de dados H2
mem - em memória
testdb - nome do banco

### Console:

Pode ser ativo com a config:

```java
spring.h2.console.enabled=true
```

**Acesso:**
http://localhost:8080/h2-console

---

## Swagger / OpenAPI

**Definição:** Se trata um ferramenta de documentação de APIs REST de forma automática.

- Lista todos os endpoints
- Permite o teste de requisições
- Gera documentação de forma automática
- Integração entre a equipe

---

