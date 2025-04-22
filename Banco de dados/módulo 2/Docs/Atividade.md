
1- Como o sistema garante que um livro só seja emprestado se houver exemplares disponíveis, considerando o campo quantidade na tabela Livros?

Na tabela livros, o campo da quantidade tem os seguintes atributos: INT NOT NULL DEFAULT 1. Isso define que a quantidade seja inteira e diferente de nulo e que o valor padrão é 1. Antes de realizar o Emprestimos, o sistema verifica esse atributo e só realiza o empréstimo se esse valor for ≥ 1. Se essa condição for verdade, o sistema realiza o empréstimo e subtrai o valor do atributo quantidade.


2- De que forma a tabela Emprestimos pode ser usada para identificar quais livros estão atualmente emprestados e quem são os usuários responsáveis por eles?

A tabela Emprestimos possui os atributos do id_livro e id_usuario, esses atributos indicam os quais livros foram emprestados e quais usuários realizaram esses empréstimos. É possível verificar o atributo data_devolucao da tabela de empréstimos, se o valor for nulo, então o empréstimo está em andamento. Juntando essas 3 informações podemos identificar os usuários e os livros que eles pegaram.


3- Como uma consulta poderia ser estruturada para listar todos os livros de um autor específico que nunca foram emprestados, utilizando as tabelas Livros e Emprestimos?

É preciso selecionar toda a tabela livros, aplicar um filtro para procurar por um autor específico, fazer uma comparação entre o atributo id_livro da tabela livros e o id_livro da tabela Emprestimos. Se o id_livro não estiver contido na tabela de empréstimos, significa que o livro do autor específico nunca foi emprestado.


4- Qual é o papel das chaves estrangeiras id_usuario e id_livro na tabela Emprestimos para manter a integridade dos dados no sistema?

O papel dessas chaves estrangeiras é o de identificar o usuário e os livros que ele emprestou da biblioteca. Dessa forma, só é possível registrar o empréstimo se o usuário e o livro estiverem registrados no banco de dados. Garantindo a integridade do sistema.


5 - Como o sistema poderia usar os campos data_emprestimo e data_devolucao da tabela Emprestimos para gerar um relatório de livros atrasados, considerando uma data limite para devolução?

O sistema pode estabelecer um limite de quantos dias o livro pode ser emprestado. Então ele pode verificar o atributo data_devolucao, os que estiverem vazios, significa que ainda não foram devolvidos. Assim o sistema pode fazer uma comparação entre a data atual e a data do empréstimo, se o valor de dias for maior que a quantidade limite de dias para a devolução, significa que a devolução está atrasada. Assim, gerando um relatório dos livros que estão atrasados.


---

# Parte 2:

1- Qual comando SQL posso usar para listar todos os livros disponíveis na tabela Livros cujo autor seja 'Jane Austen'?

select titulo from livros where autor = ‘Jane Austen’;


2- Como escrever uma consulta SQL para contar quantos usuários estão registrados na tabela Usuarios?

select count(id_usuario) from Usuarios;


3- Qual seria o comando SQL para encontrar todos os empréstimos ativos (sem data de devolução) na tabela Emprestimos?

select * from emprestimos where data_devolucao is null;


4- Como posso listar os nomes dos usuários e os títulos dos livros que eles pegaram emprestado, juntando as tabelas Usuarios, Livros e Emprestimos?


SELECT Usuarios.nome, Livros.titulo FROM Usuarios JOIN Emprestimos ON Usuarios.id_usuario = Emprestimos.id_usuario JOIN Livros ON Emprestimos.id_livro = Livros.id_livro;


5- Qual comando SQL atualiza a quantidade de um livro na tabela Livros para diminuir em 1 quando ele é emprestado?

UPDATE Livros SET quantidade = quantidade - 1 WHERE id_livro = X; ← Sendo X o id do livro emprestado.