
### **Tabela Usuarios**

Armazena informações sobre os usuários da biblioteca (quem pode pegar livros emprestados).

| Campo         | Tipo de Dado    | Descrição                          | Observação                    |
| ------------- | --------------- | ---------------------------------- | ----------------------------- |
| id_usuario    | Inteiro         | Identificador único do usuário     | Chave primária                |
| nome          | Texto (VARCHAR) | Nome completo do usuário           |                               |
| email         | Texto (VARCHAR) | Email do usuário                   | Opcional, único se preenchido |
| telefone      | Texto (VARCHAR) | Telefone do usuário                | Opcional                      |

*   **Chave primária**: `id_usuario` (garante que cada usuário tenha um identificador único).

### **Tabela Livros**

Armazena informações sobre os livros disponíveis na biblioteca.

| Campo      | Tipo de Dado    | Descrição                  | Observação                    |
| ---------- | --------------- | -------------------------- | ----------------------------- |
| id_livro   | Inteiro         | Identificador único do livro | Chave primária                |
| titulo     | Texto (VARCHAR) | Título do livro            |                               |
| autor      | Texto (VARCHAR) | Nome do autor              |                               |
| isbn       | Texto (VARCHAR) | Código ISBN do livro       | Opcional, único se preenchido |
| quantidade | Inteiro         | Quantidade disponível      |                               |

*   **Chave primária**: `id_livro` (identificador único para cada livro).

### **Tabela Emprestimos**

Registra os empréstimos de livros feitos pelos usuários, conectando as tabelas Usuarios e Livros.

| Campo           | Tipo de Dado | Descrição                               | Observação                        |
| --------------- | ------------ | --------------------------------------- | --------------------------------- |
| id_emprestimo   | Inteiro      | Identificador único do empréstimo       | Chave primária                    |
| id_usuario      | Inteiro      | ID do usuário que pegou o livro         | Chave estrangeira (ref. Usuarios) |
| id_livro        | Inteiro      | ID do livro emprestado                  | Chave estrangeira (ref. Livros)   |
| data_emprestimo | Data         | Data em que o livro foi emprestado      |                                   |
| data_devolucao  | Data         | Data prevista ou real de devolução      | Opcional (NULL se não devolvido)  |

*   **Chave primária**: `id_emprestimo` (identificador único para cada empréstimo).
*   **Chaves estrangeiras**:
    *   `id_usuario`: referencia `id_usuario` da tabela `Usuarios`.
    *   `id_livro`: referencia `id_livro` da tabela `Livros`.

Script SQL para criação das tabelas

```sql
CREATE TABLE Usuarios (
    id_usuario INT PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    telefone VARCHAR(20)
);
CREATE TABLE Livros (
    id_livro INT PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(200) NOT NULL,
    autor VARCHAR(100) NOT NULL,
    isbn VARCHAR(13) UNIQUE,
    quantidade INT NOT NULL DEFAULT 1
);
CREATE TABLE Emprestimos (
    id_emprestimo INT PRIMARY KEY AUTO_INCREMENT,
    id_usuario INT NOT NULL,
    id_livro INT NOT NULL,
    data_emprestimo DATE NOT NULL,
    data_devolucao DATE,
    FOREIGN KEY (id_usuario) REFERENCES Usuarios(id_usuario),
    FOREIGN KEY (id_livro) REFERENCES Livros(id_livro)
);
```



```sql
INSERT INTO Usuarios (nome, email, telefone) VALUES
('Ana Silva', 'ana.silva@email.com', '(11) 98765-4321'),
('Bruno Costa', 'bruno.costa@email.com', '(21) 91234-5678'),
('Carla Dias', 'carla.dias@email.com', NULL),
('Daniel Martins', 'daniel.m@email.com', '(31) 99999-8888'),
('Elena Ferreira', 'elena.f@email.com', '(41) 98888-7777'),
('Fábio Gomes', 'fabio.gomes@email.com', '(51) 97777-6666'),
('Gabriela Lima', 'gabi.lima@email.com', '(61) 96666-5555'),
('Heitor Santos', 'heitor.s@email.com', '(71) 95555-4444'),
('Isabela Oliveira', NULL, '(81) 94444-3333'),
('João Pereira', 'joao.pereira@email.com', '(91) 93333-2222');

INSERT INTO Livros (titulo, autor, isbn, quantidade) VALUES
('O Segredo do Abismo', 'Mariana Carvalho', '978-1111111111', 3),
('A Última Fronteira', 'Ricardo Alves', '978-2222222222', 2),
('Sombras do Passado', 'Sofia Bernardes', '978-3333333333', 1),
('Crônicas de Valinor', 'Lucas Andrade', NULL, 5),
('Engenharia de Dados Moderna', 'Beatriz Ramos', '978-5555555555', 4),
('Receitas da Vovó', 'Clara Medeiros', '978-6666666666', 2),
('Jardinagem para Iniciantes', 'Pedro Rocha', '978-7777777777', 3),
('A Arte da Guerra (Ed. Comentada)', 'Sun Tzu (Trad.)', '978-8888888888', 1),
('Introdução à Filosofia', 'Helena Costa', NULL, 6),
('Contos da Meia-Noite', 'Tiago Nunes', '978-0000000000', 2);

INSERT INTO Emprestimos (id_usuario, id_livro, data_emprestimo, data_devolucao) VALUES
(1, 5, '2023-10-01', '2023-10-15'),
(3, 1, '2023-10-05', NULL),
(2, 8, '2023-10-10', '2023-10-20'),
(5, 2, '2023-10-12', NULL),
(7, 4, '2023-10-15', NULL),
(1, 9, '2023-10-18', '2023-11-01'),
(9, 3, '2023-10-20', NULL),
(4, 7, '2023-10-22', NULL),
(6, 10, '2023-10-25', '2023-11-05'),
(8, 6, '2023-10-28', NULL);
```

