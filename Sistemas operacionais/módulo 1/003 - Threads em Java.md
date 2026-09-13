
## 1. Todo programa em  Java já começa com uma thread.

```java
public static void main(String[] args) {
    System.out.println(Thread.currentThread().getName());
}
```

**Saída:** main

→ O método main() ja está sendo executado por uma thread chamada **main.**

```java
Processo Java
│
└── Thread main
```


## 2. Runnable representa uma tarefa.

→ A forma mais comum de definir **o trabalho que uma thread deverá executar** é implementar um **Runnable**


```java
public class Pedido implements Runnable {

    @Override
    public void run() {
        System.out.println("Preparando pedido...");
    }
}
```

→ O método **run()** contém o código da tarefa.

```
Runnable = tarefa
Thread   = quem executa a tarefa
```

```
Pedido
(Runnable)
    │
    ↓
Thread
    │
    ↓
executa run()
```


----

## run() X start()

→ Ao fazer uma chamada com o método .run(), ele se torna uma simples chamada normal de método. Tudo continua executando na mesma thread.

```java
public class Pedido implements Runnable {

    @Override
    public void run() {
        System.out.println("Preparando pedido...");
    }
}
```

```
pedido.run();
```

```
Thread main
    │
    ├── pedido1.run()
    │
    └── pedido2.run()
```

Para criar uma thread, é necessário seguir a seguinte estrutura:

```java
Thread t = new Thread(pedido);
// start() é fundamental para executar a thread.
t.start();
```

→ start() cria uma execução concorrente e a nova thread executa o método run().

```
Processo Java
│
├── main
│
└── Thread t
      │
      └── pedido.run()
```

**Resumindo:**
```
run()   → executa na thread atual

start() → inicia outra thread, que executará run()
```


## 3. Threads podem executar de forma concorrente.


```java
Thread cozinheiro =
    new Thread(new Pedido("Hambúrguer"));

Thread atendente =
    new Thread(new Pedido("Suco"));
    
    
cozinheiro.start();
atendente.start();
```

View do processo:


```
              Processo Java
                   │
        ┌──────────┼──────────┐
        ↓          ↓          ↓
      main     cozinheiro   atendente
```

As duas tarefas p odem progredir de forma intercalada. A ordem das mensagens **não é garantida.**

**Exemplo de saída:**

```
Hambúrguer etapa 1
Suco etapa 1
Hambúrguer etapa 2
Suco etapa 2

outra possibilidade:
Suco etapa 1
Hambúrguer etapa 1
Suco etapa 2
Hambúrguer etapa 2
```

**O escalonamento das threads fica sob controle da JVM e do sistema operacional.**


## 4. sleep()

O método sleep() faz a thread atual esperar por uma quantidade X de tempo.

``` java
Thread.sleep(1000);
// Esperar 1 segundo.
```

sleep() pausa **somente a thread que chamou o método,** não o processo inteiro. As outras threads continuam executando normalmente.

```
Thread A
│
├── trabalha
│
├── sleep(1000)
│       ↓
│     espera
│
└── continua
```

## 5. join()

Serve para resolver um problema interessante:

```java
cozinheiro.start();
atendente.start();

System.out.println("Terminou!");
```

**Problema:** A thread **main** não espera automaticamente as outras terminarem.

``` java
main inicia cozinheiro
main inicia atendente
main imprime "Terminou!"

cozinheiro ainda trabalhando...
atendente ainda trabalhando...
```

Para esperar uma thread terminar, é usado o join():

```java
cozinheiro.join();
```

A thread que chamou join() deve esperar a outra terminar.


``` java
cozinheiro.start();
atendente.start();

cozinheiro.join();
atendente.join();

System.out.println("Todos terminaram!");
```

```java
main
 │
 ├── start cozinheiro
 ├── start atendente
 │
 ├── join cozinheiro ───┐
 │                      │ espera
 ├── join atendente ────┘
 │
 └── "Todos terminaram!"
```

**Importante:**
→ Iniciar todas as threads e depois esperar.

```java
t1.start();
t2.start();
t3.start();

t1.join();
t2.join();
t3.join();
```

Ao fazer isso:

```java
t1.start();
t1.join();

t2.start();
t2.join();
```

Todo o conceito de threads é perdido e o programa faz execução sequencial.


## Resumo rápido dos métodos importantes:

```java
run()
→ executa a tarefa na thread atual

start()
→ inicia uma nova thread

sleep()
→ pausa a thread atual

join()
→ espera outra thread terminar
```


## 6. Memória compartilhada entre threads:

Quando várias threads pertencem ao **mesmo processo,** elas compartilham grande parte da memória do processo.

**Exemplo:**

```java
public class Contador {

    private int total = 0;

    public void incrementar() {
        total++;
    }

    public int getTotal() {
        return total;
    }
}
```

``` java
public class TesteContador {

    public static void main(String[] args)
            throws InterruptedException {

        Contador contador = new Contador();

        Runnable registrarPedidos = () -> {
            for (int i = 0; i < 100_000; i++) {
                contador.incrementar();
            }
        };

        Thread funcionario1 =
                new Thread(registrarPedidos, "Funcionário 1");

        Thread funcionario2 =
                new Thread(registrarPedidos, "Funcionário 2");

        funcionario1.start();
        funcionario2.start();

        funcionario1.join();
        funcionario2.join();

        System.out.println("Esperado: 200000");
        System.out.println("Obtido: " + contador.getTotal());
    }
}
```

O ponto principal é este aqui: 

```
Contador contador = new Contador();
```

Duas threads usam esse mesmo objeto.

```java
Thread funcionario1 =
        new Thread(registrarPedidos, "Funcionário 1");

Thread funcionario2 =
        new Thread(registrarPedidos, "Funcionário 2");
```

```
                Contador
               total = 0
                   ↑
                   │
        ┌──────────┴──────────┐
        │                     │
 Funcionário 1           Funcionário 2
   Thread 1                Thread 2
```

Isso gera race condition!
Duas threads concorrendo por um objeto, pode fazer com que ele funcione de forma incorreta.

```
total = 10

Thread 1 lê 10
Thread 2 lê 10

Thread 1 calcula 11
Thread 2 calcula 11

Thread 1 grava 11
Thread 2 grava 11


resultado = 11

Porem: 
As duas threads incrementaram, o resultado deveria ser 12. 
```

## 7. Synchronized:

Para impedir duas threads de executarem uma região critica ao mesmo tempo. É possivel usar o synchronized.

```java
public synchronized void incrementar() {
    total++;
}
```
→ Somente uma thread por vez pode executar o método naquele objeto.

```
Thread 1 ──────┐
               ↓
          incrementar()
               ↑
Thread 2 ── espera


Depois:

Thread 1 sai

Thread 2
   ↓
incrementar()
```

## join() X  synchronized

É importante não confundir os dois:

```
join()
→ controla QUANDO continuar

synchronized
→ controla QUEM pode acessar ao mesmo tempo


join()
→ espera uma thread terminar

synchronized
→ protege uma região contra execução concorrente
```


## 8. Várias threads usando a mesma tarefa:

```java
Thread[] funcionarios = new Thread[4];
```

```
                    Contador
                  total = 0
                      ↑
        ┌─────────────┼─────────────┐
        │             │             │
    Thread 1      Thread 2      Thread 3      Thread 4
     50.000        50.000        50.000        50.000
```

Resultado esperado: 

```
4 × 50.000 = 200.000
```

Com o uso do synchronized, atualizações perdidas são evitadas. E com o join() é garantido que o main só vai ler o resultado **depois que todos terminarem.**



## Conceito geral:

Threads permitem executar múltiplos fluxos dentro do mesmo processo, mas como compartilham memória, precisamos tomar cuidado com acesso concorrente aos dados.

