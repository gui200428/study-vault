## Agrupamento de computadores (clustering):
**Definição:** Um **cluster** é um conjunto de computadores independentes (nós) interconectados que funcionam como se fossem uma única máquina. É uma técnica usada para aumentar o desempenho e a disponibilidade de sistemas, principalmente em servidores.

**Exemplos:** Beowulf, Google Data Centers.

### Benefícios (Brewer, 1997):

- **Escalabilidade absoluta:** permite formar clusters com centenas ou milhares de máquinas, superando o poder de sistemas únicos.
- **Escalabilidade incremental:** possibilita expandir o cluster gradualmente, sem substituições grandes. Ou seja, dá para ir adicionando nós conforme a necessidade.
- **Alta disponibilidade:** a falha de um nó não compromete o serviço, graças à tolerância a falhas.
- **Melhor relação custo/desempenho:** oferece alto poder computacional com custo menor que o de máquinas grandes.


## Configurações de cluster:

![[Pasted image 20261102155214.png|500]]

### Classificação pelo compartilhamento de discos:

1. **Cluster sem disco compartilhado:** cada nó tem seus próprios discos e se comunica por uma rede de alta velocidade. Como nada é compartilhado, é preciso software para balancear a carga e garantir tolerância a falhas, com troca constante de dados entre os nós.

2. **Cluster com disco compartilhado:** os nós acessam um subsistema comum de discos (como RAID, Redundant Array of Independent Disks). Isso reduz a sobrecarga de comunicação e melhora a disponibilidade, mas exige controle de acesso aos dados para evitar conflitos.

3. **Cluster sem compartilhamento (variação):** os discos comuns são divididos em volumes exclusivos para cada nó. Em caso de falha, outro nó assume os volumes do nó que falhou.

4. **Cluster com memória compartilhada:** menos comum, envolve compartilhamento direto de memória entre os nós.

### Modelos funcionais:

- **Secundário passivo (passive standby):** um nó ativo e outro inativo, que só assume em caso de falha. Como o segundo nó fica parado, não melhora o desempenho e **não é considerado um cluster verdadeiro**.
- **Secundário ativo (active standby):** todos os nós processam ativamente e mantêm a **imagem de sistema único** para o usuário externo. Quem está de fora enxerga uma máquina só.

### Disco compartilhado x memória compartilhada:

![[Pasted image 20261102155938.png]]

→ Compartilhar memória é mais complexo e limita a escalabilidade; compartilhar disco escala melhor e tem implementação mais simples.


## Métodos de clustering - benefícios e limitações:

![[Pasted image 20261102160347.png]]

**Obs:** "Servidores separados" corresponde ao cluster sem disco compartilhado, "servidores conectados aos discos" à variação sem compartilhamento e "servidores que compartilham discos" ao cluster com disco compartilhado.

- **Secundário passivo é fácil de implementar, mas tem custo alto.** O servidor secundário fica indisponível para outras tarefas de processamento.
- **Secundário ativo reduz o custo, mas aumenta a complexidade.** O servidor secundário também é usado para processamento.
- **Em servidores separados, os dados são copiados continuamente do primário para o secundário.** Isso dá alta disponibilidade, mas é daí que vem a grande sobrecarga de rede e de servidores.
- **Ligar os servidores aos mesmos discos elimina as cópias, então a carga diminui.** Por outro lado, para compensar o risco de falha de disco, esses métodos costumam usar espelhamento de discos ou RAID.
- **Quando os servidores compartilham os discos simultaneamente, também é preciso software de gerenciamento de bloqueio.**


## Questões de projeto do sistema operacional:

Para aproveitar totalmente o hardware de um cluster, o sistema operacional precisa de aprimoramentos específicos.

### 1. Gerenciamento de falhas:

- **Alta disponibilidade:** garante que os recursos estejam quase sempre ativos. Em caso de falha, outra máquina assume, mas **transações incompletas podem ser perdidas**.
- **Tolerância a falhas:** mantém todos os recursos disponíveis mesmo após falhas, com **recuperação automática de transações**.
- **Failover:** transferência automática de aplicações e dados para outro nó após a falha.
- **Failback:** retorno dos recursos ao nó original após o reparo, de preferência de forma controlada para evitar instabilidade.

→ A diferença entre alta disponibilidade e tolerância a falhas está nas transações: na primeira elas podem se perder, na segunda são recuperadas.

### 2. Balanceamento de carga:

- Distribui automaticamente as tarefas entre os nós do cluster.
- Deve reconhecer novos nós adicionados e ajustar o agendamento de aplicações.
- O middleware precisa lidar com serviços que podem migrar entre os nós.

### 3. Computação paralela:

**Três abordagens para executar aplicações em paralelo:**
1. **Compilação paralela:** o compilador identifica as partes paralelizáveis da aplicação.
2. **Aplicações paralelas:** o programador desenvolve a aplicação com troca de mensagens entre os nós.
3. **Computação paramétrica:** ideal para simulações repetitivas com diferentes parâmetros, usando ferramentas para gerenciar os múltiplos cenários.


## Arquitetura de um cluster e middleware:

Em um cluster típico, os computadores são conectados por uma rede de alta velocidade e operam de forma independente. **Para funcionar como um sistema único, cada nó possui um middleware.**

### Middleware:
**Definição:** Software intermediário que funciona como um tradutor ou ponte, permitindo que diferentes componentes de software trabalhem juntos de forma eficiente.

**Responsável por:**
- Comunicação entre sistemas (ex: troca de mensagens, APIs).
- Integração de aplicações heterogêneas.
- Gerenciamento de transações.
- Segurança e autenticação.
- Escalabilidade e distribuição.

**Exemplos usados em clusters:** OpenMPI, Hadoop, Kubernetes.

### Funções desejáveis do middleware (Hwang et al., 1999):

1. **Ponto de entrada único:** login feito no cluster, não em máquinas individuais.
2. **Hierarquia única de arquivos:** todos os nós compartilham a mesma estrutura de diretórios.
3. **Ponto de controle único:** uma estação gerencia o cluster.
4. **Rede virtual única:** qualquer nó acessa qualquer outro, mesmo em redes diferentes.
5. **Espaço único de memória:** permite compartilhamento de variáveis entre nós.
6. **Sistema único de gerenciamento de trabalhos:** o usuário não precisa escolher o nó que vai executar o trabalho.
7. **Interface de usuário única:** mesma interface gráfica para todos os usuários.
8. **Espaço único de E/S:** acesso remoto a dispositivos de entrada/saída.
9. **Espaço único de processos:** processos podem se comunicar entre nós.
10. **Pontos de verificação:** salvam o estado dos processos para recuperação.
11. **Migração de processos:** permite redistribuir a carga entre os nós.

→ Quase todas seguem a mesma ideia: esconder que são várias máquinas e passar a imagem de um sistema único.


## Servidores blade em clusters:
**Definição:** Servidor compacto e modular, projetado para economizar espaço físico e otimizar recursos em data centers. É uma forma comum de implementar clusters.

![[Pasted image 20261102161822.png|500]]

- **Consiste em placas (blades) que contêm processador, memória, interfaces de rede e, às vezes, armazenamento básico.**
- **As blades são inseridas em um chassi, que fornece:**
	- Energia elétrica compartilhada.
	- Conectividade de rede.
	- Sistema de refrigeração.
	- Gerenciamento centralizado.
- **É muito usado em centros de dados, porque economiza espaço e facilita o gerenciamento.** Cada blade não precisa ter tudo isso próprio, o chassi fornece para todas.

### Características e tendências:

- Blades com portas de **10 Gbps** para suportar tráfego intenso de multimídia.
- **Comutadores Ethernet de 100 Gbps** para interligar servidores e redes corporativas.
- Alta capacidade de interconexão e largura de banda, essencial para grandes volumes de dados.

---

## Arquitetura UMA (Uniform Memory Access):
**Definição:** Acesso uniforme à memória, ou seja, o tempo de acesso é sempre o mesmo, seja qual for o processador ou a região da memória.

- **Todos os processadores têm acesso a todas as partes da memória principal usando leituras e escritas.**
- **O tempo de acesso de um processador é o mesmo para todas as regiões da memória.**
- **Os tempos de acesso de processadores diferentes também são os mesmos.**

**Obs:** O SMP se encaixa aqui, já que os processadores compartilham a memória com tempo de acesso uniforme.


## Acesso não uniforme à memória (NUMA):

As duas abordagens comerciais comuns para sistemas com vários processadores são **SMPs e clusters**. O NUMA é uma outra abordagem, que por alguns anos foi assunto de pesquisa e hoje já tem produtos comerciais.

### O problema: limite do SMP:

- **O SMP tem limite prático de processadores (16 a 64), devido ao aumento do tráfego no barramento e à troca de sinais de coerência de cache.** Quanto mais processadores, mais tráfego e mais sinais de coerência, até isso virar gargalo de desempenho.

### Solução: clusters e NUMA:

- **Para superar essas limitações, surgem os clusters e a arquitetura NUMA (Non-Uniform Memory Access), que permite maior escalabilidade com múltiplos nós, cada um com sua própria memória e barramento.** Com o barramento dividido por nó, os processadores deixam de disputar um único barramento.

### Termos:

#### 1. NUMA (Non-Uniform Memory Access):
- **Todos os processadores têm acesso a todas as partes da memória principal usando leituras e escritas.** Essa parte é igual ao UMA.
- **O tempo de acesso de um processador muda dependendo da região da memória acessada.** Isso vale para todos os processadores, mas as regiões mais lentas e mais rápidas são diferentes para cada um.

#### 2. CC-NUMA (NUMA com coerência de cache):
- **Sistema NUMA no qual a coerência de cache é mantida entre as caches dos vários processadores.**

**Obs:** Um sistema NUMA **sem** coerência de cache é mais ou menos equivalente a um cluster. Já os sistemas CC-NUMA, que são os produtos comerciais que receberam mais atenção recentemente, são bastante diferentes de SMPs e clusters. Na literatura comercial, esses sistemas geralmente aparecem com o nome CC-NUMA, mas nem sempre.


## Arquitetura CC-NUMA:

- **Cada nó é um sistema SMP com múltiplos processadores, caches L1/L2 e memória principal.**
- **Os nós são interligados por redes (comutadores, anéis etc.).**
- **O sistema oferece uma memória única e endereçável, mesmo que fisicamente distribuída.** Cada nó tem um pedaço da memória, mas todos enxergam um único espaço de endereços.
- **O acesso à memória remota é feito de forma automática e transparente ao processador.**

### Coerência de cache:

- **Cada nó mantém um diretório que rastreia onde estão os dados e o estado das caches.**
- **Protocolos de coerência garantem que modificações em uma cache sejam refletidas nos demais nós.**
- **Exemplo: a leitura de memória remota envolve múltiplas etapas entre diretórios e barramentos, mas é invisível ao processador.** O processador não vê essas etapas; para ele, é como se estivesse lendo a memória normalmente.

### Vantagens:
- Alta escalabilidade com desempenho eficiente.
- Redução de gargalos locais de barramento.
- Aproveitamento de localidade temporal e espacial do software.
- Migração de páginas melhora o desempenho.

### Desvantagens:
- **Não é totalmente transparente como o SMP: exige adaptações no sistema operacional e nas aplicações.**
- Questões de disponibilidade dependem da implementação específica.

**Obs:** O acesso remoto é transparente para o **processador**, mas o sistema como um todo não é: o SO e as aplicações precisam de adaptações.
