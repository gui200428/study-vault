## Visão geral do gerenciamento de memória

Na **uniprogramação**, a memória principal tem uma parte para o sistema operacional (**monitor residente**) e outra para o programa em execução. Na **multiprogramação**, a parte destinada ao usuário é subdividida para acomodar vários processos. O SO faz essa subdivisão dinamicamente: esse é o **gerenciamento de memória**.

Se apenas alguns processos estiverem na memória, em grande parte do tempo todos estarão esperando E/S e o processador ficará ocioso. Por isso, o SO precisa alocar a memória de modo eficiente para manter o máximo possível de processos nela.

### Hierarquia de memórias

A memória ideal para o programador seria **grande, rápida e não volátil**. Na prática, o gerenciador de memória lida com uma hierarquia:

- pequena quantidade de **cache**: rápida e de alto custo;
- quantidade considerável de **memória principal**: velocidade e custo médios;
- gigabytes de **armazenamento em disco**: velocidade e custo baixos.

### Como rodar um programa?

1. Ao receber o comando de execução, o sistema copia o código e os dados do programa objeto do disco para a memória principal.
2. O **PC** aponta para o endereço de memória onde o programa foi escrito.
3. O processador executa as instruções do programa trazidas da memória.

## Sem abstração de memória

Gerenciar a memória sem abstração é trabalhar diretamente com endereços físicos da RAM, sem mecanismos que escondam essa complexidade do programador ou do SO. Isso traz três problemas apresentados na aula:

- processos podem usar o mesmo endereço de memória;
- se a memória toda ficar disponível aos processos de usuário, eles podem prejudicar o SO;
- torna-se difícil executar vários programas simultaneamente, ficando um por vez.

### O que envolve?

- **Endereçamento direto:** o programa ou o sistema precisa saber onde cada dado está na memória física; não há tradução de endereço virtual para físico.
- **Alocação manual:** o sistema ou programa decide onde colocar variáveis e estruturas. Em Assembly, por exemplo, pode definir diretamente o endereço de uma variável.
- **Controle total do uso da memória:** é preciso evitar que processos se sobreponham, lidar com fragmentação e liberar memória manualmente.
- **Segurança e isolamento:** fica mais difícil impedir que um processo acesse a memória de outro, tornando sistemas multitarefa mais vulneráveis.

A aula cita esse uso em sistemas embarcados muito simples sem SO; em *bootloaders* e *firmwares*, antes de carregar uma abstração; e em Assembly ou outras linguagens de baixo nível sem suporte a abstrações.

## Particionamento da memória

Particionar é dividir a memória para manter vários programas carregados. Isso permite **multiprogramação**, com troca de contexto eficiente, e aumenta a utilização do processador.

### Exemplo com 64 MB

A figura acompanha a ocupação de uma memória principal de **64 MB**:

1. Inicialmente, só o SO ocupa **8 MB**, deixando **56 MB** para processos (a).
2. Entram o processo 1 (**20 MB**), o 2 (**14 MB**) e o 3 (**18 MB**), nessa ordem (b–d). Sobram **4 MB**, insuficientes para um quarto processo.
3. Quando nenhum processo na memória está pronto, o SO retira o processo 2. O espaço de **14 MB** deixado por ele permite carregar o processo 4 (e–f).
4. O processo 4 ocupa **8 MB**. Como é menor que o processo 2, fica outro buraco de **6 MB**.
5. Mais tarde, nenhum processo na memória está pronto, mas o processo 2 está **pronto-suspenso**. O SO retira o processo 1, liberando **20 MB**, e traz o processo 2 de volta (g–h).

![[Pasted image 20260927182512.png]]

### Partições fixas

A memória também pode ser dividida em partições de **tamanho fixo**, iguais ou diferentes entre si. Quando um programa é carregado, entra em uma fila para usar uma partição livre. O número de partições determina o **número máximo de processos concorrentes**.

Um esquema compara **partições do mesmo tamanho** (8 M cada) com **partições de tamanhos desiguais** (2, 4, 6, 8, 8, 12 e 16 M); nos dois casos, o SO ocupa 8 M.

O diagrama mostra duas formas de organizar a espera:

- **filas de entrada separadas**, uma para cada partição;
- **fila de entrada única**, da qual os processos podem seguir para uma partição livre.

No exemplo, o SO ocupa até **100 K**; as quatro partições terminam em **200 K, 400 K, 700 K e 800 K**.

![[Pasted image 20260927182513.png]]

## Troca de processos na memória (swapping)

**Swapping** libera espaço quando a RAM está cheia: um processo é movido temporariamente da memória principal para o disco, geralmente para o **espaço de troca (*swap*)**, para que outro possa ser carregado e executado.

1. O sistema identifica a memória sobrecarregada.
2. Um processo inativo ou de menor prioridade sai da RAM e é salvo no disco.
3. Outro processo entra na RAM e executa.
4. Quando necessário, o processo retirado pode voltar à RAM.

O esquema compara o **escalonamento de job simples**, com uma fila de longo prazo no disco, à **troca de processos na memória**, que também usa uma fila intermediária e permite movimentos entre disco e memória principal. Nos dois casos, os jobs e sessões de usuário finalizados saem da memória.

![[Pasted image 20260927182514.png]]

**Vantagens:**

- permite executar mais processos do que caberiam simultaneamente na RAM;
- melhora a utilização da CPU em sistemas multitarefa.

**Desvantagens:**

- a leitura e a escrita no disco podem causar lentidão;
- trocas excessivas podem causar **thrashing**: trocas constantes que degradam o desempenho.

## Paginação

**Paginação** é uma técnica de gerenciamento de memória que permite que os processos utilizem a memória de forma eficiente e segura, mesmo que não estejam completamente carregados na memória RAM.

- **Memória virtual:** espaço de endereçamento lógico do processo, que pode ser maior que a memória física disponível.
- **Página:** unidade fixa da memória virtual; o exemplo da aula é **4 KB**.
- **Quadro (*frame*):** unidade da memória física com o mesmo tamanho de uma página.
- **Tabela de páginas:** mapeia páginas virtuais para quadros físicos.

No diagrama, as páginas **0, 1, 2 e 3** do processo A são colocadas, respectivamente, nos quadros **18, 13, 14 e 15**. Antes, os quadros livres eram **13, 14, 15, 18 e 20**; os quadros **16, 17 e 19** já estavam em uso. Depois, o **20** permanece livre. A tabela guarda esse mapeamento mesmo com as páginas distribuídas pela memória principal.

![[Pasted image 20260927182515.png]]

**Vantagens:**

- elimina a fragmentação externa;
- permite uso eficiente da memória;
- facilita a implementação de memória virtual.

**Desvantagens:**

- muitas falhas de página podem gerar sobrecarga;
- a tradução de endereços pode tornar o acesso à memória mais lento.

**Melhorias comuns:**

- **TLB (*Translation Lookaside Buffer*):** cache de endereços de páginas que acelera a tradução;
- **paginação por demanda:** carrega páginas apenas quando necessário;
- **paginação em múltiplos níveis:** reduz o tamanho da tabela de páginas em espaços de endereçamento grandes.

## Memória virtual

**Memória virtual** simula uma memória maior que a RAM disponível, permitindo executar programas sem carregá-los inteiramente na memória física. Seus objetivos na aula são:

- **isolamento entre processos:** cada processo tem a ilusão de possuir toda a memória para si;
- **execução de programas maiores que a RAM:** o disco funciona como extensão da memória;
- **gerenciamento eficiente:** somente partes necessárias dos programas são carregadas.

O processo gera **endereços lógicos ou virtuais**. O SO traduz esses endereços em físicos usando a **tabela de páginas**. Com **paginação por demanda**, só as páginas necessárias entram na RAM. Se a página solicitada não estiver nela, ocorre uma **falha de página (*page fault*)** e o sistema a busca no disco.

**Vantagens:**

- permite multitarefa eficiente;
- reduz a fragmentação externa;
- melhora a segurança e o isolamento entre processos.

**Desvantagens:**

- muitas falhas de página podem causar lentidão;
- o acesso ao disco é mais lento que o acesso à RAM.

## Translation Lookaside Buffer (TLB)

A **TLB** é uma memória cache especial usada pelo SO e pela **MMU** (*unidade de gerenciamento de memória*) para acelerar a tradução de endereços virtuais em físicos. Sua função é guardar entradas recentes da tabela de páginas. Isso evita consultas repetidas à memória principal e reduz o tempo de acesso.

1. O processo gera um endereço virtual.
2. A MMU verifica se a tradução está na TLB. Se estiver, o acesso à memória física é rápido.
3. Se não estiver (**TLB miss**), a MMU consulta a tabela de páginas na RAM e carrega a entrada na TLB.

A TLB é atualizada dinamicamente conforme o uso dos processos. Suas características apresentadas são:

- **pequena e rápida:** geralmente tem poucas entradas, por exemplo, de **64 a 512**;
- **associatividade:** pode ser totalmente associativa ou por conjunto;
- **substituição:** pode usar **LRU** (*Least Recently Used*) para escolher qual entrada remover.

**Vantagens:**

- aumenta a eficiência da memória virtual;
- reduz o número de acessos à RAM;
- melhora o desempenho geral do sistema.

**Desvantagens:**

- *TLB misses* podem causar lentidão;
- requer cuidado para manter a coerência com a tabela de páginas.

## Segmentação

**Segmentação** divide o espaço de endereçamento de um processo em **segmentos lógicos**, como código, dados e pilha, em vez de blocos fixos como na paginação. O objetivo é refletir a estrutura lógica do programa, facilitando a proteção, o compartilhamento e a organização da memória.

- Cada segmento tem **tamanho variável**.
- O endereço lógico contém o **número do segmento** e um **deslocamento (*offset*)** dentro dele.
- O SO mantém uma **tabela de segmentos**, com **base e limite** de cada segmento.

**Vantagens:**

- facilita a proteção e o isolamento entre partes do programa;
- permite compartilhar segmentos entre processos;
- preserva melhor a estrutura lógica dos programas.

**Desvantagens:**

- pode causar **fragmentação externa**;
- exige uma tradução de endereços mais complexa;
- o material a apresenta como menos eficiente que a paginação em sistemas modernos.

### Comparação com paginação

| Aspecto | Segmentação | Paginação |
| --- | --- | --- |
| Tamanho dos blocos | Variável | Fixo |
| Fragmentação | Externa | Interna |
| Organização lógica | Preservada | Quebrada em páginas |
| Tradução de endereço | Segmento + deslocamento | Página + deslocamento |
