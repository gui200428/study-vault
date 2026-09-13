
## Comandos iniciais:

```bash
ps # lista os processos ativos no terminal
top # lista todos os serviços em execução e o uso de memória e CPU
sleep 120 & # <- espera por 120 segundos. O & joga essa espera pro segundo plano.
jobs # lista toda as tarefas em execução controladas pelo shell
kill $! # Mata o ultimo PID iniciado.
```


## Competição para o uso da CPU

- Quando se tem muitos processos em andamento, eles competem pelo uso da CPU, a CPU executa uma instrução por núcleo a cada ciclo de clock, cabe ao sistema operacional decidir quem usa e por quanto tempo.
- A alternância entre os processos cria a sensação de simultaneidade.

![[Pasted image 20260910161322.png]]


## Programa X Processo X Thread


### 1. Programa:

- Um programa é um Arquivo / código armazenado, ainda passivo.
- Enquanto ele estiver simplesmente salvo no SSD é um **programa.**
- Não está fazendo absolutamente nada.

Exemplo:

```bash
meuPrograma.jar
```

### 2. Processo:

- Ao executar um programa:

```bash
java -jar meuPrograma.jar
```

O sistema operacional carrega o código na memória e cria um **processo.**

**Processo:** é uma execução concreta do programa.

É possível executar **o mesmo programa duas vezes:**

```
meuPrograma.jar
       │
       ├── Processo 1 — PID 100
       │
       └── Processo 2 — PID 101
```
- Isso gera dois processos diferentes e independentes que vieram do mesmo programa.

- **Cada processo é independente e possui seu próprio espaço na memória**


**Exemplo básico:**

Se ambos os processos tiverem a variável:

```
int contador = 0;
```

- O contador do processo 100 não é o mesmo contador do processo 101. 


### 3. Thread

Dentro de um processo, ele não necessariamente executa apenas uma coisa.

**Dentro de um processo podem existir várias threads!**

```
Processo
│
├── Thread 1
├── Thread 2
├── Thread 3
└── Thread 4
```

Cada thread se comporta como um fluxo de execução:

```
Programa.java
       ↓
Processo Java
       │
       ├── Thread main
       ├── Thread download 1
       ├── Thread download 2
       └── Thread download 3
```

As threads compartilham grande parte da memória e dos recursos do processo.

```
THREADS

             Processo A
                 │
        memória compartilhada
                 │
        ┌────────┼────────┐
        ↓        ↓        ↓
     Thread 1 Thread 2 Thread 3
```

**Problema:** Race condition!

Como as threads estão relacionadas ao mesmo processo e possuem a memória compartilhada, pode ocorre a race condition. Basicamente ocorre quando duas threads do mesmo processo tentam acessar de forma concorrente a mesma variável ao mesmo tempo, ambas podem tentar modificar a mesma variavel.


### Múltiplos processos X threads:

```
PROCESSOS

Processo A             Processo B
memória A              memória B
contador = 10          contador = 50

separados
```

```
THREADS

             Processo A
                 │
        memória compartilhada
                 │
        ┌────────┼────────┐
        ↓        ↓        ↓
     Thread 1 Thread 2 Thread 3
```


### importante em java:

Ao iniciar um método main, ja criamos uma thread!

```
public static void main(String[] args) {
}
```


```
Thread "main"
```

Ao criar uma thread, temos algo assim:

```
Thread t = new Thread(() -> {
    System.out.println("Olá");
});

t.start();
```


```
Processo Java
│
├── main
│
└── t
```

#### Exemplo:

```
             Programa
          Livro de receitas
             /       \
            ↓         ↓
      Processo 1   Processo 2
      Restaurante Restaurante
        /   \          |
       ↓     ↓         ↓
    Thread Thread    Thread
```


## Processo:

- Basicamente um processo não é simplesmente um “programa rodando¨.  Para que o processo seja executado corretamente, ele precisa salvar alguns pontos na memória.

### Composição do processo em memória:

```
Processo
│
├── Código
├── Dados
├── Heap
└── Stack
```

#### 1. Código:
- As instruções do programa que serão executadas.

```java
System.out.println("Olá!");
```

#### 2. Dados:
- Armazena as variáveis globais e estáticas.

#### 3. Heap:
- Área usada para alocação dinâmica de memória.

- Em java é normalmente onde ficam armazenados os objetos.

```java
Pessoa p = new Pessoa();
```

```java
Stack                    Heap
p ─────────────────── Pessoa()
```


#### 4. Stack
- Responsável por guardar informações associadas às chamadas de funções / métodos.
- Exemplo: parâmetros, variáveis locais e informações necessárias para retornar de uma função.

```java
void soma() {
    int x = 10;
}
```

Basicamente a varável X é local e pertence à stack da execução.

### Elementos básicos do sistema:

#### 1. Contador de programa:
- Define qual é a próxima instrução

#### 2. Registradores:
- Guardam valor temporários usados durante os cálculos das instruções.

#### 3. Recursos do processo:
- Um processo pode possuir recursos controlados pelo sistema operacional.

```java
Processo Java
│
├── arquivo.txt aberto
├── conexão de rede
├── acesso a dispositivo
├── PID
└── permissões
```

### Relação com as threads:

As threads compartilham várias dessas regiões:

```
              Processo
                 │
        ┌────────┴────────┐
        │                 │
   memória compartilhada
   código / dados / heap
        │
   ┌────┼────┐
   ↓    ↓    ↓
Thread Thread Thread
  1      2      3
```

**Cada thread possui seu próprio fluxo de execução.** 
- Cada thread possui seu próprio **Stack, Program counter e uso dos registradores.**

#### Estrutura do processo:

```
PROCESSO
├── Código        ← compartilhado
├── Dados         ← compartilhado
├── Heap          ← compartilhado
│
├── Thread 1
│   ├── Stack
│   ├── PC
│   └── Registradores
│
└── Thread 2
    ├── Stack
    ├── PC
    └── Registradores
```

### Ideia principal:
- Um processo é composto por muito mais que código executando. Ele possui memória, estado de execução e recursos controlados pelo sistema operacional.


## Comando bash:

```bash
cat /proc/$$/status 2>/dev/null
# cat lê o status; $$ é o PID do shell
# 2>/dev/null oculta mensagens de erro
echo "PID do shell: $$" # imprime texto e PID
```

## PID e PPID

### 1. PID
**Definição:**  PID é o identificado de processo. Cada processo em execução recebe um identificador (PID).

```java
Processo Java
PID = 4120
```

O PID é responsável por diferenciar as execuções que estão ocorrendo.

```
meuPrograma.jar
       │
       ├── Processo 1 — PID 100
       │
       └── Processo 2 — PID 101
```


### 2. PPID:
**Definição:** É o processo pai de um processo filho, ou seja, o processo que criou outro processo.

**Exemplo:**

```
Shell
PID 2000
   │
   ├── java programa.jar
   │      PID 2100
   │      PPID 2000
   │
   └── sleep 10
          PID 2200
          PPID 2000
```


O shell iniciou os dois comandos, java e sleep.


## Comandos do shell:

**Comando para imprimir o PID do próprio shell:**
``` bash
echo $$
```

**Comando para listar todos os processos:**
```bash
ps
```

Melhor view:
```
ps -o pid,ppid,stat,comm
```

**Exemplo:**
```
PID    PPID   STAT   COMMAND
5320   4200   S      bash
5401   5320   R      java
```
```
bash
PID 5320
   │
   └── java
       PID 5401
       PPID 5320
```


## Estado de um processo conforme a execução (STAT)

**Definição:** Um processo não fica executando o tempo todo. Ele muda de estado conforme usa a CPU ou espera algum evento.

### Estados:

### 1. Novo:
- Processo acabou de ser criado.

Programa iniciado
      ↓
Processo NOVO

### 2. Pronto:
- O processo está apto a executar, mas está esperando a CPU ficar disponível.

### 3. Executando
- Processo está usando a CPU.
CPU
 ↓
Processo A executando


### 4. Bloqueado:
- O processo precisa esperar alguma coisa antes de continuar.
- Precisa esperar algo externo: leitura de arquivo, rede, teclado, disco etc.

Processo
   ↓
pede leitura do disco
   ↓
BLOQUEADO

### 5. Encerrado:
- O processo terminou a execução.

### Preempção:
- Ocorre quando o sistema operacional tira um processo do uso da CPU mesmo que ele ainda não tenha terminado. 
- **Motivo:** permitir que outros processos também tenham tempo de CPU.

### Fluxo:

PRONTO
  ↓ CPU disponível
EXECUTANDO
  │
  ├── terminou → ENCERRADO
  │
  ├── perdeu a CPU → PRONTO
  │
  └── espera I/O → BLOQUEADO
                       │
                       └── evento terminou → PRONTO

### No linux:

R → Running / Runnable
    executando ou pronto para executar

S → Sleeping
    esperando algum evento

D → espera não interrompível
    geralmente relacionada a I/O

T → parado/suspenso

Z → Zombie
    processo terminou, mas ainda possui registro no sistema


## PCB - Process control block.

**Definição:**  PCB é a estrutura que o kernel usa para guardar as informações e o estado de cada processo.

Basicamente é uma **ficha do processo.**

PCB do Processo 100
│
├── PID
├── estado
├── contador de programa
├── registradores
├── memória
├── arquivos abertos
└── prioridade


O PCB é muito importante para garantir o gerenciamento dos processos, gerando a capacidade de pausar e continuar processos.

```
Processo A executando
        ↓
SO precisa executar B
        ↓
salva o estado de A no PCB
        ↓
executa B
        ↓
depois restaura o PCB de A
        ↓
A continua de onde parou
```


### Comandos do shell:

``` bash
ps -o pid,stat,comm # seleciona PID, estado e nome

cat /proc/$$/status 2>/dev/null # lê o status do shell

cat /proc/$$/limits 2>/dev/null # lê limites derecursos

# $$ = PID do shell; 2>/dev/null = descarta erros
```


## TROCA DE CONTEXTO:

**Definição:** a troca de contexto acontece quando a CPU deixa de executar um processo e passa executar outro.

Processo A executando
        ↓
troca de contexto
        ↓
Processo B executando

### Etapas:

#### 1. Salvar:
- O sistema operacional salva o estado atual do processo A.

#### 2. Escolher:
- O escalonador decide qual processo vai executar em seguida, dado uma fila de processos com o estado pronto.


```
Fila de prontos

Processo B
Processo C
Processo D
```


#### 3. Restaurar:
- O sistema operacional carrega o contexto do processo escolhido.

```
PCB do Processo B
        ↓
restaura registradores e estado
        ↓
Processo B continua executando
```

### Troca de contexto gera custo:
- Durante a troca, a CPU está basicamente trabalhando para o sistema operacional. Não diretamente para os programas. Esse intervalo consome tempo.

**Troca de contexto é necessário para multitarefa, mas não é trabalho útil do programa.**

- CPU passa tempo administrando processos em vez de executar diretamente o código deles.


--- 

## Comandos do shell:

```bash
whoami # mostra o usuário atual
pwd # mostra o diretório atual
uname -a # -a exibe dados completos do sistema
echo $SHELL # imprime a variável com o shell configurado

date # mostra data, hora e fuso
```

```bash
pwd # mostra o diretório atual
ls -la # -l detalha; -a inclui ocultos
mkdir aula-processos # cria um diretório
cd aula-processos # muda o diretório do shell
printf 'alpha\nbeta\n' > nomes.txt # > grava a saída
cat nomes.txt # lê e imprime o arquivo
wc -l nomes.txt # -l conta linhas
```

### PS:

```bash
ps # processos ligados ao terminal
ps -ef # -e: todos (todos os processos rodando em background); -f: formato completo

ps -o pid,ppid,stat,comm # -o define as colunas desejadas

ps -o pid,stat,time,comm # inclui tempo acumulado de CPU
```

![[Pasted image 20260911170531.png]]


```bash
ps -ef | grep sleep # filtra linhas com sleep (greep tem o sleep, então grep é listado.)
ps -ef | grep '[s]leep' # evita mostrar o próprio grep
ps -o pid,ppid,stat,comm | head # mostra apenas o início
ps -o pid,stat,comm | sort -n # ordena numericamente
ps -ef | wc -l # conta as linhas da saída
```

![[Pasted image 20260911170810.png]]


### TOP:

```bash
top # atualiza processos continuamente

watch ps 2>/dev/null # repete ps; oculta erros do watch

ps # alternativa: fotografia única

```

**Importante: TOP x PS:** Top lista informações dos processos de forma dinâmica. Ps é uma “fotografia¨ estática.



### Shell:

```bash
sleep 120 & # & inicia em segundo plano
echo "último PID: $!" # $! = PID do último processo
jobs # lista tarefas deste shell
ps # lista processos visíveis
fg %1 # traz a tarefa 1 ao primeiro plano
bg %1 # retoma a tarefa 1 ao fundo
jobs # confirma o novo estado
```

![[Pasted image 20260911171458.png]]


### Sinais de controle de processos:

```bash
sleep 300 & # cria processo em segundo plano
PID=$! # guarda o último PID na variável
PID
echo $PID # imprime o valor da variável
kill -STOP $PID # suspende o processo
ps -o pid,stat,comm # verifica PID, estado e comando
kill -CONT $PID # continua o processo suspenso
kill -TERM $PID # solicita encerramento normal
wait $PID 2>/dev/null # aguarda o fim e oculta erros
```

![[Pasted image 20260911171634.png]]


### Relação entre pais e filhos:

```bash
sh -c 'sleep 180 & wait' & # novo shell cria sleep e espera
PAI=$! # guarda o PID do novo shell
echo "PID do novo shell: $PAI" # imprime o PID armazenado
ps -ef # mostra todos em formato completo
ps -o pid,ppid,stat,comm # evidencia relação PID–PPID
pstree -p # se existir, desenha árvore com PIDs
```

![[Pasted image 20260911171833.png]]



### Acompanhamento de um processo:

### 1. Criar:

```bash
sleep 200 &
# inicia sleep ao fundo
# [1] 188263
```

### 2. Identificar:

```bash
PID=$!; echo $PID
# guarda e imprime o PID
# 188263
```

### 3. Observar:

```bash
ps -o pid,ppid,stat,comm

# escolhe colunas do ps
    PID    PPID STAT COMMAND
 187613  187603 S<s  fish
 187643  187613 S<   sleep
 188153  187613 S<   sh
 188263  188153 S<   sleep
 189642  188153 R<+  ps
```


### 4. Suspender:

```bash
kill -STOP $PID
# envia o sinal STOP
```

### 5. Retomar:

```bash
kill -CONT $PID
# envia o sinal CONT
```

### 6. Encerrar:

```bash
kill -TERM $PID
# solicita término normal
```

### Pergunta final: o que o sistema operacional precisa salvar para interromper um processo e retomá-lo corretamente?

O sistema operacional precisa salvar o contexto do processo, contado de programa e os registradores da CPU, alem do estado do processo. Essas informações ficam associadas ao PCB.

