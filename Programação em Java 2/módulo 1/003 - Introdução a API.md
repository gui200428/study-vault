
## Modelo:

![[Pasted image 20260412111838.png|697]]

---

## APIs REST (Representational State Transfer) e Métodos HTTP

Uma API REST é um padrão arquitetural que permite a comunicação entre sistemas através do protocolo HTTP
Trabalham com resources (recursos) acessados por URLs

**Métodos HTTP:**
- GET → buscar dados
- POST → criar dados
- PUT → atualizar dados existentes
- DELETE → remover dados

```txt
GET /produtos     (Busca a lista de produtos)
POST /produtos    (Cria um novo produto)
PUT /produtos/1   (Atualiza o produto com ID 1)
DELETE /produtos/1 (Remove o produto com ID 1)
```


## Spring boot - visão geral

- O **Spring boot** se trata de um framework com o objetivo de simplificar o desenvolvimento de aplicações em Java. Elimina configurações complexas.

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
- Serve para abstrair a complexidade do banco de dados. Herda as funcionalidades dos conectores do Spring Datam como o **MongoRepository**.  
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

