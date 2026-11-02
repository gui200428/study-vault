## Organizações de múltiplos processadores:

### Taxonomia de Flynn (1972):
**Definição:** Classificação dos sistemas de processamento paralelo de acordo com quantos fluxos de instrução e quantos fluxos de dados são tratados ao mesmo tempo.

![[Pasted image 20261024204318.png|500]]

#### 1. SISD (Single Instruction, Single Data):
- **Um único processador executa uma única instrução sobre um único conjunto de dados.** É o modelo sequencial clássico, sem paralelismo entre processadores.
- **Exemplo:** computadores uniprocessados.

#### 2. SIMD (Single Instruction, Multiple Data):
- **Uma instrução é aplicada simultaneamente a múltiplos dados por vários processadores.** Todos fazem a mesma operação ao mesmo tempo, cada um sobre um dado diferente.
- **Exemplo:** processadores vetoriais e de matriz.

#### 3. MISD (Multiple Instruction, Single Data):
- **Múltiplos processadores executam diferentes instruções sobre o mesmo conjunto de dados.** O mesmo dado passa por operações diferentes em cada processador.
- **Exemplo:** sistemas tolerantes a falhas, sistemas de diagnóstico médico.

**Obs:** Mesmo com esses exemplos, o MISD é tratado como um sistema hipotético e raro comercialmente (ver exercício 1). Ou seja, é a categoria menos usada na prática.

#### 4. MIMD (Multiple Instruction, Multiple Data):
- **Múltiplos processadores executam diferentes instruções sobre diferentes conjuntos de dados.** Cada processador segue o seu próprio programa com os seus próprios dados.
- **Exemplo:** SMPs, clusters e sistemas NUMA.

→ O que define a categoria é a combinação: instrução única ou múltipla × dado único ou múltiplo.

### Subcategorias de MIMD:

O MIMD se divide em **memória compartilhada (fortemente acoplada)**, onde ficam SMP e NUMA, e **memória distribuída (fracamente acoplada)**, onde ficam os clusters.

1. **SMP (Multiprocessador Simétrico):** processadores compartilham memória com **tempo de acesso uniforme**.
2. **NUMA (Acesso Não Uniforme à Memória):** o **tempo de acesso à memória varia conforme a localização** da memória acessada.
3. **Clusters:** conjunto de computadores interconectados, **comunicando-se via rede**.


## SMP (Symmetric Multiprocessing):
**Definição:** Arquitetura em que **dois ou mais processadores semelhantes** compartilham a memória, a E/S e têm as mesmas funções, sob o controle de um único sistema operacional.

**Os processadores compartilham:**
- **Memória principal com tempo de acesso uniforme.** Qualquer processador leva o mesmo tempo para acessar qualquer posição da memória (é isso que diferencia do NUMA).
- **Dispositivos de E/S, acessados por canais comuns ou distintos.**
- **Funções iguais, ou seja, todos os processadores podem executar qualquer tarefa.** Daí o "simétrico": não existe processador mestre ou especializado.

- **O sistema é gerenciado por um sistema operacional integrado, que distribui processos e threads entre os processadores e coordena a sincronização.**

### Vantagens do SMP:
1. **Desempenho:** tarefas paralelas são executadas mais rapidamente.
2. **Disponibilidade:** a falha de um processador não paralisa o sistema. Como todos fazem as mesmas funções, os outros continuam trabalhando.
3. **Crescimento incremental:** é possível adicionar mais processadores para melhorar o desempenho.
4. **Escalabilidade:** fabricantes podem oferecer versões com diferentes números de processadores.

**Obs:** Esses benefícios dependem da capacidade do sistema operacional de explorar o paralelismo. Ter vários processadores não adianta se o SO não distribuir o trabalho entre eles.


## Organização de sistemas multiprocessadores:

![[Pasted image 20261024205142.png|400]]

- **Dois ou mais processadores, cada um com sua própria unidade de controle, ALU, registradores e cache.** Cada processador é completo; o que eles dividem é o resto do sistema.
- **Todos têm acesso à memória principal compartilhada e aos dispositivos de E/S por meio de um mecanismo de interconexão, geralmente um barramento de tempo compartilhado.**
- **A comunicação entre os processadores pode ocorrer via memória compartilhada ou sinais diretos.**
- **Em algumas arquiteturas, cada processador pode ter memória e E/S próprias, além dos recursos compartilhados.**


## Barramento de tempo compartilhado:
**Definição:** A forma mais simples de interconexão em sistemas multiprocessadores, composta por **linhas de controle, endereço e dados**.

- **Permite que múltiplos processadores e dispositivos de E/S acessem a memória, mas um de cada vez.** Por isso o nome "tempo compartilhado": o barramento é um só e o uso dele é dividido no tempo, o que pode limitar o desempenho.

![[Pasted image 20261024205426.png|500]]

### Recursos do barramento:
1. **Endereçamento:** identifica a origem e o destino dos dados.
2. **Arbitração:** define qual dispositivo controla o barramento em caso de concorrência. Quando dois processadores pedem o barramento ao mesmo tempo, é a arbitração que decide quem usa.
3. **Tempo compartilhado:** apenas um dispositivo usa o barramento por vez; os demais aguardam.

### Vantagens:
- **Simplicidade:** fácil de implementar.
- **Flexibilidade:** permite adicionar novos processadores facilmente. É só ligar mais um no barramento.
- **Confiabilidade:** falhas em dispositivos não comprometem o sistema todo.

### Desvantagem:
- **Desempenho limitado: o barramento único pode se tornar um gargalo.** Como só um usa por vez, quanto mais processadores e dispositivos disputando, mais tempo cada um fica esperando.

**Obs:** O barramento não elimina conflitos de acesso, ele só organiza (pela arbitração) quem usa primeiro.


## Uso de memória cache:

- **Para melhorar o desempenho, cada processador possui cache L1, L2 e, às vezes, L3.** Com cache própria, boa parte dos acessos é resolvida dentro do processador, sem disputar o barramento e sem ir até a memória principal.
- **O uso de cache exige controle de coerência, para garantir que todos os processadores tenham dados atualizados.** Se cada um tem a sua cópia, uma alteração feita em uma cache precisa ser percebida pelas outras.
- **Esse controle é feito por hardware, evitando inconsistências entre caches.**


## Sistema operacional em SMP:
**Definição:** O SO SMP gerencia os vários processadores de forma integrada, fazendo com que o usuário perceba o sistema **como se fosse um único processador multiprogramado**.

### Principais responsabilidades e desafios:

### 1. Concorrência simultânea:
- **Rotinas do SO devem ser reentrantes, permitindo execução simultânea por vários processadores.** Reentrante = pode ser executado simultaneamente por múltiplas threads ou processos sem causar erros ou inconsistências. Como vários processadores podem estar rodando código do SO ao mesmo tempo, a mesma rotina pode ser chamada por dois deles de uma vez.
- **É necessário gerenciar estruturas internas para evitar deadlocks e inconsistências.**

### 2. Escalonamento:
- **Qualquer processador pode agendar processos.**
- **O SO deve evitar conflitos e distribuir eficientemente os processos entre os processadores disponíveis.**

### 3. Sincronização:
- **Múltiplos processos acessam memória e recursos compartilhados, exigindo mecanismos de exclusão mútua e ordenação de eventos.** Sem isso, dois processos podem alterar o mesmo dado ao mesmo tempo e deixar ele inconsistente.

### 4. Gerenciamento de memória:
- **Além das funções tradicionais, o SO deve explorar o paralelismo do hardware, como memórias com múltiplas portas.**
- **Deve garantir consistência na paginação entre processadores que compartilham dados.**

### 5. Confiabilidade e tolerância a falhas:
- **O SO deve detectar falhas em processadores e reconfigurar o sistema para continuar operando com desempenho reduzido.** É o que torna possível a vantagem de disponibilidade do SMP.


## Coerência de cache e protocolo MESI:

### O problema: coerência de cache:
**Definição:** Problema que ocorre quando **muitas cópias de um mesmo dado** existem em caches diferentes e são **atualizadas de forma independente**, causando inconsistência na memória.

- Cada processador tem um ou mais níveis de cache para melhorar o desempenho. **Se o processador A altera o dado só na sua cache, o processador B continua com a cópia antiga na dele.** Os dois passam a "enxergar" valores diferentes para o mesmo endereço.

### Políticas de escrita em cache:

#### 1. Write-back:
- **A escrita ocorre apenas na cache; a memória principal é atualizada somente quando a linha é removida da cache.**
- **Pode causar inconsistência entre caches.** Enquanto a linha alterada não sai da cache, a memória principal (e as outras caches) ficam com o valor desatualizado.

#### 2. Write-through:
- **A escrita ocorre simultaneamente na cache e na memória principal.**
- **Reduz o risco de inconsistência, mas ainda exige mecanismos de sincronização entre caches.** A memória fica sempre atualizada, mas as cópias que já estavam nas caches dos outros processadores continuam antigas.

→ Write-back: memória atualizada só na remoção da linha. Write-through: memória atualizada a cada escrita, mais fácil de manter consistente.

### Soluções para coerência de cache:

- **Protocolo MESI (Modified, Exclusive, Shared, Invalid): é o protocolo mais usado (inclusive em arquiteturas x86) para manter a consistência entre caches.**
- **Objetivo dos protocolos: permitir que dados locais fiquem em cache para acesso rápido, enquanto garantem consistência dos dados compartilhados entre múltiplos processadores.** Ou seja, manter o ganho da cache sem ter o problema das cópias diferentes.

**Abordagens:**
1. **Por hardware:** mais comuns e eficientes.
2. **Por software:** menos frequentes, mas ainda utilizadas.
3. **Híbridas:** combinam elementos de hardware e software.

**Obs:** Quando se diz que o controle de coerência "é feito por hardware" (ver uso de memória cache), isso é o caso mais comum. As abordagens por software e híbridas também existem.


## Desempenho de processadores:

**A principal medida de desempenho é a Taxa MIPS (Millions of Instructions Per Second):**

$$Taxa\ MIPS = f \times IPC$$

- $f$ → frequência do clock.
- $IPC$ → instruções executadas por ciclo de clock.

**Obs:** A fórmula dá o resultado direto em MIPS quando $f$ está em MHz. Se $f$ estiver em Hz, é preciso dividir por $10^6$.
**Exemplo:** $f = 2\ GHz = 2000\ MHz$ e $IPC = 2$ → $Taxa\ MIPS = 2000 \times 2 = 4000\ MIPS$.

**Os projetistas buscam melhorar o desempenho de duas formas:**
1. Aumentando a frequência do clock.
2. Aumentando o número de instruções executadas por ciclo (IPC).

### Técnicas para aumentar o IPC:
- **Pipeline de instruções:** permite executar várias etapas de diferentes instruções simultaneamente.
- **Arquitetura superescalar:** executa múltiplas instruções em paralelo.
- **Técnicas avançadas:** execução fora de ordem e execução especulativa.

**Essas abordagens aumentam a complexidade e o consumo de energia, o que limita sua escalabilidade.** Cada uma exige mais hardware para detectar e controlar o paralelismo, então não dá para ir aumentando indefinidamente.

### Multithreading - alternativa eficiente:
- **Divide o fluxo de instruções em múltiplas threads, que podem ser executadas em paralelo.**
- **Permite maior paralelismo sem aumentar significativamente a complexidade ou o consumo de energia.** É a saída para o limite das técnicas acima.
- **É amplamente adotado em sistemas comerciais e experimentais.**


## Exercícios:

### Exercício 1: Classificação de Flynn:

Classificar cada cenário segundo Flynn:

- a) Múltiplos processadores aplicando a mesma instrução sobre diferentes conjuntos de dados → **SIMD**.
- b) Um único processador executando uma única instrução sobre um único conjunto de dados → **SISD**.
- c) Diferentes processadores executando diferentes instruções sobre diferentes conjuntos de dados → **MIMD**.
- d) Sistema hipotético onde diferentes instruções são aplicadas ao mesmo conjunto de dados → **MISD** (raro comercialmente).

### Exercício 2: Barramento de tempo compartilhado:

**Explicar como funciona e citar uma vantagem e uma desvantagem.**

É uma forma simples de interconexão, composta por linhas de controle, endereço e dados, que permite que vários processadores e dispositivos de E/S acessem a memória principal. Só um dispositivo usa o barramento por vez, enquanto os demais aguardam.

- **Vantagem:** simplicidade, fácil de implementar e flexível para adicionar novos processadores.
- **Desvantagem:** desempenho limitado, o barramento único pode virar um gargalo e reduzir a eficiência em sistemas com muitos processadores.
