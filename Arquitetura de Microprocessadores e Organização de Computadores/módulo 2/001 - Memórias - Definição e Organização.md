## Componentes do computador

![[Pasted image 20251028172549.png]]

**O modelo representa a arquitetura de Von Neumann (Memória única para dados e instruções)**

### Funcionamento:

→ CPU troca dados com a memória, para isso, é preciso o uso de dois registradores internos na CPU.

**Registrador de endereço de memória (MAR):** especifica o endereço na memória para próxima leitura / escrita

**Registrador de buffer de memória (MBR):** contem os dados a serem escritos na memória. Recebe os dados lidos da memória.

**Registrador de endereço de E/S (Entrada/saída):** especifica um dispositivo de E/S
**Registrador de buffer de E/S:** Usado para troca de dados entre um módulo de E/S e a CPU

**Módulo de memória:** Conjunto de locais definidos por endereços numerados de maneira sequencial. Cada local possui um número binário que pode ser interpretado como uma instrução ou um dado.

**Módulo de E/S:** transfere dados dos dispositivos externos para a CPU e a memória e vice-versa. Contem buffers internos para manter esses dados temporariamente, até que possam ser enviados.

## MAR e MBR

### MAR (Memory Address Register):

**Função:** armazena o endereço da memória onde a CPU quer ler ou escrever dados
**Operação:** CPU coloca o endereço desejado no MAR, esse endereço é enviado para a memória.


### MBR (Memory Buffer Register):

**Função:** Armazena os **dados** que estão sendo **transferidos** entre a memória e a CPU.
**Operação:** 
- **Leitura:** o dado da memória vai para o MBR
- **Escrita:** o dado da CPU vai para o MBR antes de ser enviado à memória.


## MAR / MBR: Funcionamento conjunto

**Leitura:**
→ A CPU precisa ler o conteúdo da posição 0x1000
→ CPU coloca 0x1000 no **MAR**
→ Memória manda o dado da posição 0x1000 para o **MBR**
→ CPU lê o dado do **MBR**

**Escrita:**
→ A CPU precisa escrever o valor 42 na posição 0x2000
→ CPU coloca o endereço 0x2000 no **MAR**
→ CPU coloca o valor 42 no **MBR**
→ O dado do **MBR** é escrito na memória no endereço marcado no **MAR**


## Características do sistemas de memória

### Localização e capacidade

**Interna x Externa**
→ **Memória interna**: Caracterizada como a memória principal. Existem tipos específicos de memória interna: **memória interna do processador, na forma de registradores** e **memória cache (armazenamento temporário)** 

→ **Memória externa:** Consiste em dispositivos de armazenamento periféricos, como **discos e fitas.** São acessíveis ao processador por meio de controladores de E/S.

**Características:**

→ **Memória interna capacidade:** É expresso em termos de bytes (1 byte = 8bits) ou palavras. Tamanhos comuns de palavra são (8/16/32/64) bits.

→ **Memória externa capacidade:** É expressa em termos de bytes.


### Unidade de transferência

#### Memória interna:
→ Unidade de transferência é igual ao número de linhas elétricas que chegam e saem do módulo de memória. pode ser igual ao tamanho da palavra ou maior: 64/128/256 bytes

**Definições importantes:**

**Palava:** unidade “natural” de organização da memória. O tamanho da palavra pode ser igual ao número de bits usados para representar um inteiro e ao tamanho de instrução. Existem muitas exceções a esse tamanho. A arquitetura da intel x86 tem diferentes tamanhos de instrução e uma palavra com o tamanho de 32 bits.
**→ Unidade natural de dados que o processador manipula.**

**Unidades endereçáveis:** Em muitos sistemas o endereçamento é no nível de byte. O relacionamento entre o tamanho em bits A de um endereço e o número N de unidades endereçáveis é de $2^A = N$
**→ Menor unidade que pode ser acessada diretamente via endereço**

**Unidade de transferência:** Para a **memória principal**, se trata do número de bits lidos / escritos na memória de uma só vez. A unidade de transferência não precisa ser igual a uma palavra ou uma unidade endereçável. 
Para a **memória externa**, os dados são transferidos em unidades muito maiores que uma palavra. Estas unidades são chamadas de blocos.
**→ Quantidade de dados lida ou escrita de uma vez.**

**Lembrando: (8 bits = 1 byte)**
![[Pasted image 20251029145140.png]]


### Método de acesso
→ Se trata da forma com que a memória é acessada. os métodos são:

**Acesso sequencial:** dados são acessados em uma sequência linear, um após o outro. Para acessar um dado específico, é necessário percorrer os anteriores.
**Ex:** Fitas magnéticas para backup, para acessar um arquivo, o sistema precisa “avançar” até encontrar o ponto exato.

**Acesso direto:** possível ir diretamente para uma posição específica, com base em um endereço ou deslocamento. Sem precisar percorrer os anteriores.
**Ex:** HDs e SSDs, é possível acessar diretamente o setor onde está armazenado um dado.

**Acesso aleatório:** qualquer posição da memória pode ser acessada diretamente e com o mesmo tempo de acesso, independente da localização.
**Ex:** memória RAM, o processador pode acessar qualquer célula de memória diretamente, independente da posição, com o mesmo tempo de resposta.

**Associativo ou por conteúdo:** Os dados são acessados com base em seu conteúdo e não por um endereço específico. O sistema compara simultaneamente todos os dados armazenados para encontrar uma correspondência.
**Ex:** memória cache associativa ou TLB (Translation Lookaside Buffer). Quando o processador precisa de um dado, ele fornece uma chave, e a memória retorna o conteúdo correspondente, se estiver armazenado.


## Desempenho:

→ Características mais importantes da memória são **capacidade** e **desempenho**. Existem 3 parâmetros de desempenho:

**Tempo de acesso (latência):** é o tempo necessário para localizar uma posição de memória, ler / escrever nela. Começa com o momento em que o endereço é enviado à memória e termina quando os dados estão disponíveis para uso (leitura) / quando escrita for concluída.
**Ex:** Processador solicita um dado da memória RAM, ele demora 50 nano segundos para ser disponibilizado, então o acesso é de 50 ns

**Tempo de Ciclo de Memória:** é o intervalo entre o inicio de uma operação de leitura/escrita e o momento em que a memória está pronta para uma nova operação.
**Ex:** Uma memória precisa de 70 ns para completar uma operação e estar para a proxima operação, portanto o ciclo é de **70 ns**

**Taxa de transferência:** Quantidade de dados que pode ser transferida da memória para o processador ou (vice-versa) por unidade de tempo. Expressa em bytes por segundo (B/s) ou bits por segundo (bps).
**Ex:** Memória transfere 64 bits (8 bytes) a cada 100 ns. A taxa de transferência é: 
$$\frac{8 \ bytes}{(100*10^{-9})} = 80 \ MBps$$ 
## Tipos físicos

**Características:** 
→ **Memória volátil:** informação se perde quando a energia elétrica é desligada.
- Memória em circuitos integrados podem ser voláteis ou não.
→ **Memória não volátil:** a informação depois de ser gravada, permanece intacta até que seja deliberadamente mudada. Energia elétrica não é necessária para reter a informação.
- Memórias de superfície magnética
- Memória ROM não é apagável (somente leitura.) 

**Tipos:**
**1- Memórias de semicondutor:** 
- Feitas com circuitos eletrônicos
- RAM - (Random access memory) - memória volátil
- ROM - (read only memory) - armazena firmwares - não volátil
- Flash - pendrives, ssds, cartões de memória - não volátil
- EEPROM - memória regravável - usada em microcontroladores

**2- Memórias magnéticas:**
- Usa propriedades magnéticas para armazenar dados
- HD
- Fita magnética - backups e armazenamento

**3- Memórias ópticas**
- Lase para leitura e gravação de dados
- CD
- DVD
- BLU-RAY

**4- Magneto-ópticas**
- Combina propriedades magnéticas e ópticas.
- Disco magneto-óptico(MO) - usado na indústria e arquivamento de dados.

## Hierarquia de memória

**Ranking de memória**

| Tipo                    | Definição                                                            |
| ----------------------- | -------------------------------------------------------------------- |
| Registradores           | Nivel mais alto, memórias mais rápidas dentro do processador         |
| Cache (L1/L2/L3)        | Situada entre o processador e memória principal                      |
| Memória principal (RAM) | Memória externa ao processador e de acesso constante                 |
| Memória externa (Disco) | Memória externa ao processador e secundárias (acesso esporádico)     |
| Fita magnética          | Memória externa ao processador e secundárias (acesso esporádico)     |
| Memória remota (Nuvem)  | Memória externa ao processador e secundárias (acesso esporádico)<br> |

→ Quanto mais alto no ranking, **menor capacidade**, **mais rápida**, **mais cara**. **Maior frequencia de acessos à memória pelo processador!**
→ Quanto mais baixo no ranking, **maior capacidade**, **mais lenta**, **mais barata**.

**Dimensão de projeto:** levar em conta o valor, velocidade e custo.
→ Tempo de acesso: maior custo por bit
→ Maior capacidade: menor custo por bit
→ Maior capacidade: tempo de acesso mais lento

## Organização de memória:

### Memória cache:

→ Memória de acesso extremamente rápido, localizada próximo ao processador. Armazena temporariamente dados e instruções frequentemente acessados, reduzindo o tempo de acesso à memoria principal.

**Características:**
→ Rápida, porem muito cara e de baixa capacidade
→ Volátil
→ Organizada em L1 (mais rápida e menor), L2 e L3 (maior e mais lenta).
→ Técnicas de mapeamento (direto e associativo) e políticas de substituição **LRU (usado menos recentemente)/ FIFO (Primeiro que entra, primeiro que sai)**

**Ex:** Processador I7 tem cache L1 de 32 KB / L2 de 256 KB e L3 de até 12 MB

### Memória principal (RAM):

→ Memória de trabalho do sistema, se armazena dados e instruções que estão sendo usadas no momento. É acessada diretamente pelo processador. 

**Características:**
→ Volátil
→ Maior capacidade que a cache, (mais lenta)
→ Tipos: **DRAM (mais usada - mais barata - mais lenta (armazena o bit em um capacitor e precisa ser constantemente carregada (refresh))) e SRAM (menos usada - mais cara - mais rápida (armazena cada bit em um flip-flop e não precisa de refresh))**
→ Organizada em células com endereções únicos
→ Trabalha com barramentos de dados, endereços e controle

**Ex:** pc tem 16 GB de ram e usa a memória para carregar o SO, aplicativos e arquivos em uso.


### Memória secundária:

→ Dados armazenados de forma permanente, não é acessada diretamente pelo processador, mas via sistema de entrada/saída. Usada para guardar arquivos, programas e o SO.

**Características:**
→ Não volátil
→ Alta capacidade e baixo custo por bit
→ Mais lenta que a RAM e a cache
→ HD / SSD / Discos ópticos / Fitas magnéticas

**Ex:** SSD de 512 GB armazena o SO e documentos.


## RESUMO

![[Pasted image 20251101120326.png]]

**Exercícios:**
Ex 1:
a) ram - acesso aleatório
b) fira magnética - acesso sequencial
c) HD - acesso direto
d) cache associativa - acesso associativo

Ex 2: 
**Cálculo de taxa de transferência:**

**Uma memória transfere 128 bits a cada 200 nanosegundos. Qual é a taxa de**
**transferência em megabytes por segundo (MBps)?**

$$\frac{128}{200*10}$$


8 bit = 1 bytes
128 bits = 16 bytes

$$\frac{16 \ bytes}{200*10^{-9}}= 80 MB/S$$

Ex 3:

**Ordene os seguintes tipos de memória da mais rápida para a mais lenta,
considerando também capacidade e custo por bit: 
• Memória Secundária
• Memória Cache
• Memória Principal (RAM)**

cache → ram → secundária

