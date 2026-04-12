
## Funcionamento clássico de um script em python:

1. Interpretado lê e executa uma instrução por vez.
2. Fluxo é linear e segue um caminho único.
3. A próxima linha só inicia depois que a atual termina.

![[Pasted image 20260412183748.png]]


### O problema:

- Programas sequenciais são mais lentos, por conta do tempo de espera por dados.

 ![[Pasted image 20260412183932.png]]


### A solução:

#### Threads!

→  Uma thread (linha de execução) é uma subdivisão de um processo. Ela permite múltiplos fluxos de controle operando no mesmo programa, compartilhando a memória.

![[Pasted image 20260412184112.png]]


### Biblioteca do python

- O python disponibiliza um biblioteca nativa chamada threading

```python
import threading
```

Funcionamento:

```python
def baixar_arquivo(url):
...

# lento, trava o programa até concluir
baixar_arquivo(x)

# não trava o programa
t = threading.Thread(target=baixar_arquivo, args=("https://...",))
t.start()
t.join()
```


```python
t = threading.Thread(target=funcao, args("arg da funcao1", "arg2"))
```

**Sendo:**

**target:** indica qual função a thread irá executar
**args:** argumentos da função


### Ciclo de funcionamento:

#### 1. Instanciar a thread

```python
t = threading.Thread(target=funcao, args("arg da funcao1", "arg2"))
```

#### 2. Iniciar a thread

Solicita ao sistema operacional que inicie a execução do bloco de código. Script principal não espera a thread para seguir
```python 
t.start()
```

#### 3. Sincronização:

Ponto de encontro da thread com o script principal, ele trava o script para esperar pelo resultado da thread. 
**Sem isso, o programa ignora as threads e encerra a execução.**

```python
# aguarda a thread retornar os dados e continua
t.join()
```


## Race condition

- Ocorre quando duas threads tentam modificar uma variável ao mesmo tempo

### Solução: GIL (Global interpreter lock):

- Trava de segurança, apenas uma thread pode executar bytecode python por vez.

#### Caso de tarefa I/O Bound (Existe espera para uma açãoser concluida)

→ Quando uma thread bate em uma operação de I/O, leitura de disco ou de uma página na internet, o python libera o GIL. Isso permite que outra thread comece a rodar e executar sua tarefa.


#### Caso CPU-bound (Não existe espera)

→ Neste caso, quando se tem múltiplas threads que precisam usar o processador para fazer cálculos, elas ficam brigando pelo o GIL, cada uma executa um pouco e passa o GIL para outra.
→ **Código concorrente:** as threads avançam juntas aos poucos.
→ **Não é paralelo de verdade!**
→ **Pode até ser mais lento que a execução sequencial!**


| Tarefa                                                             | Ferramenta python                                                                                                                       |
| ------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------- |
| **I/O Bound:** Downloads, web scraping, consulta de banco de dados | **Threads!** A CPU processa outras linhas de código enquanto aguarda pela resposta externa.                                             |
| **CPU Bound:** Processamento de imagens, cálculos matemáticos      | **Não usar threads!** Usar multiprocessing! Foge do uso do GIL criando múltiplos processos isolados e dedicados em núcleos reais da CPU |

Diferente das Threads, que operam dentro do mesmo processo e **compartilham a mesma memória** (causando o bloqueio do GIL e Race Conditions), o `multiprocessing` burla o GIL porque cria processos filhos isolados do sistema operacional, **cada um com seu próprio espaço de memória independente**."
## Padrões de arquitetura:

### Padrão worker pool (Lista de threads:)

```python
threads = []
for url in urls:
    t = threading.Thread(...)
    threads.append(t)
    t.start()

for t in threads:
    t.join() # Aguarda a tropa toda voltar
```

Cria uma lista de threads, uma para cada url, executa elas e depois espera pelo resultado delas.


### Padrão “delegação de tarefas:”

Definir manualmente cada thread.

```python
t1 = threading.Thread(target=thread_diagonais)
t2 = threading.Thread(target=thread_soma)
# ... inícios e joins manuais
```

