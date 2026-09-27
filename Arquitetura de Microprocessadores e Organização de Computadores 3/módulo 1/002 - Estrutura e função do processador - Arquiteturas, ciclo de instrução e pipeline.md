# Estrutura e função do processador - Arquiteturas, ciclo de instrução e pipeline

## Arquiteturas CISC e RISC

### CISC (*Complex Instruction Set Computer*)

Usa um conjunto de instruções e um hardware altamente complexos. Opcode e operando são armazenados em posições diferentes na memória. Uma instrução pode realizar mais de uma operação e acessar a memória diretamente. A arquitetura x86 e o 8051 aparecem como exemplos na aula.

No exemplo do 8051, as instruções têm tamanhos diferentes. O **opcode** indica a operação; o operando ou seu endereço pode ocupar outros bytes:

- `CLR A`: um byte, que contém o opcode;
- `MOV A,30h`: dois bytes, com o opcode e o endereço do operando;
- `LJMP 3FB2h`: três bytes, com o opcode e os dois bytes do endereço.

![[Pasted image 20260927165430.png]]

A tabela de instruções aritméticas do 8051 mostra essa variação. Operações como `ADD A,Rn` ocupam um byte, enquanto `ADD A,direct` ocupa dois. A duração também varia: vários exemplos usam 12 períodos do oscilador, `INC DPTR` usa 24 e `MUL AB` e `DIV AB` usam 48.

![[Pasted image 20260927165431.png]]

**Vantagens:**

- simplificação dos programas, pois uma instrução pode fazer mais trabalho;
- compatibilidade com programas feitos para a arquitetura.

**Desvantagens:**

- projeto do processador mais complexo;
- maior dissipação de calor e consumo de energia;
- dificuldade para otimizar o desempenho e a velocidade;
- instruções com durações diferentes.

#### Ciclo de instrução CISC

O diagrama da aula segue esta sequência:

1. Buscar a instrução na memória.
2. Interpretar a operação a ser realizada.
3. Buscar os operandos, se houver.
4. Executar a operação.
5. Repetir o ciclo.

### RISC (*Reduced Instruction Set Computer*)

Usa um conjunto de instruções e um hardware mais simples. Opcode e operando são armazenados na mesma posição na memória. As instruções são projetadas para realizar uma tarefa por vez e, na apresentação da aula, para execução em um ciclo de clock. O projeto prioriza registradores para reduzir acessos à memória. ARM e PIC16F877 são os exemplos mostrados.

Nos formatos do PIC16F877, o opcode e os campos da operação aparecem na mesma palavra de instrução de 14 bits. O formato muda conforme a função:

- operações com registrador de arquivo (*file register*) usam campos como destino `d` e endereço `f`;
- operações de bit usam o número do bit `b` e o endereço `f`;
- operações com literal usam o valor imediato `k`; `CALL` e `GOTO` usam um campo de endereço maior.

![[Pasted image 20260927165432.png]]

A tabela do PIC16F877 separa as instruções nesses grupos. Muitas aparecem com um ciclo, enquanto chamadas e desvios como `CALL` e `GOTO` aparecem com dois.

Obs: o material apresenta como característica do RISC a execução em um único ciclo de clock, porém essa tabela possui instruções com mais de um ciclo.

![[Pasted image 20260927165433.png]]

**Vantagens:**

- desempenho elevado;
- eficiência energética;
- escalabilidade, com mais núcleos e frequências de clock maiores.

**Desvantagens:**

- maior tamanho do código, pois uma tarefa complexa exige mais instruções simples;
- necessidade de otimização do código.

#### Ciclo de instrução RISC

O diagrama da aula mostra:

1. Buscar a instrução na memória.
2. Interpretar a operação a ser realizada.
3. Buscar os operandos, se houver.

A seta retorna à busca. O diagrama não mostra uma caixa separada para a execução.

## Ciclo de instrução e pipeline

**Pipeline:** técnica que sobrepõe no tempo as fases de instruções diferentes. Enquanto uma instrução avança, outra já pode começar. Isso aumenta a quantidade de instruções concluídas ao longo do tempo, mas não diminui o tempo necessário para completar uma instrução isolada.

As fases apresentadas são:

1. **Fetch (IF):** busca da instrução.
2. **Decode (ID):** decodificação da instrução.
3. **Execute (EX):** execução da operação.
4. **Memory Access (MEM):** acesso à memória.
5. **Write-back (WB):** escrita do resultado.

O esquema mostra os componentes usados em cada fase e os registradores que separam os estágios.

![[Pasted image 20260927165434.png]]

### Exemplo da lavanderia

A aula compara o pipeline a uma linha de montagem: lavar, secar, passar e guardar roupas. Cada etapa leva 30 minutos. Sem sobreposição, uma cesta passa pelas quatro etapas antes de começar a próxima; quatro cestas levam 8 horas.

Com as etapas sobrepostas, a segunda cesta pode começar a ser lavada enquanto a primeira está na secadora, e assim por diante. A primeira ainda precisa passar por todas as etapas, mas quatro cestas terminam em 3 horas e 30 minutos.

![[Pasted image 20260927165435.png]]

### Sobreposição das instruções

No exemplo de instruções da aula, cada uma leva 8 ns para percorrer as fases. Sem pipeline, a próxima começa depois da anterior. Com pipeline, a busca da próxima pode começar a cada 2 ns, ocupando um estágio que já ficou livre.

→ O ganho está em manter vários estágios trabalhando ao mesmo tempo, não em encurtar a execução completa de cada instrução.

![[Pasted image 20260927165436.png]]

## Hierarquia de memória

As memórias são organizadas conforme velocidade, capacidade e custo. Do topo para a base da hierarquia mostrada na aula:

1. Registradores;
2. cache L1, L2 e L3;
3. memória principal (RAM);
4. memória externa em disco;
5. memória externa em fita magnética;
6. memória remota na nuvem.

Os registradores ficam no nível mais alto, dentro do processador. A cache fica entre o processador e a memória principal; a RAM é externa ao processador e acessada constantemente. Disco, fita e armazenamento remoto ficam nos níveis inferiores, para acessos mais esporádicos.

Quanto mais alto o nível, **menor a capacidade, maior a velocidade e maior o custo**. Descendo na hierarquia, a capacidade aumenta, mas o acesso fica mais lento e o custo por armazenamento diminui.

![[Pasted image 20260927165437.png]]

## Arquitetura x86

### Evolução apresentada na aula

- **8086 (1978):** deu origem ao x86; processador de 16 bits usado em computadores pessoais. O 8088 (1979) é uma variação com barramento de dados de 8 bits.
- **80286 (1982):** avanços em gerenciamento e proteção de memória, suporte a multitarefas e barramento de 16 bits.
- **80386 (1985):** a aula menciona modos real e protegido, maior eficiência em multitarefas e barramento de 32 bits.
- **80486 (1989):** pipeline de instruções e unidade de ponto flutuante integrada, mantendo os 32 bits.
- **Pentium (1993):** duas unidades de execução para processamento paralelo. A linha do tempo associa o Pentium Pro (1995) a múltiplos núcleos e o Pentium MMX (1996) a instruções multimídia.
- **Pentium II, III e IV (1997 a 2004):** novas instruções e Hyper-Threading.

A aula agrupa os processadores a seguir sob o rótulo **Arquiteturas de 64 bits**.

- **Core (2006):** múltiplos núcleos e novos projetos de microarquitetura. **Core i (2008):** linhas i3, i5 e i7, com melhorias de cache e arquitetura de memória. **Core i9 (2017):** foco em desempenho e maior quantidade de núcleos e threads.

### Organização interna do 8086

O diagrama divide o processador em **BIU** (*Bus Interface Unit*) e **EU** (*Execution Unit*). A BIU faz a interface com a memória, reúne os registradores de segmento e o IP e alimenta uma fila de seis bytes de instruções. A EU recebe as instruções dessa fila e reúne registradores, ULA, controle e flags para executá-las.

Essa separação permite que a BIU busque bytes de instrução enquanto a EU trabalha com os que já foram buscados.

![[Pasted image 20260927165438.png]]

## Arquitetura ARM

ARM significa *Advanced RISC Machine*. A arquitetura é licenciada para outras empresas e é apresentada com foco em baixo consumo de energia, especialmente em dispositivos móveis e sistemas embarcados. A aula cita ARMv9 e divide a família em Cortex-A, Cortex-R e Cortex-M.

### Cortex-A

Voltado a aplicações de alto desempenho, como dispositivos móveis, servidores e computadores pessoais. Pode ter vários núcleos e suporte a 32 e 64 bits. A aula cita instruções **NEON/SIMD** (*Single Instruction, Multiple Data*) e **TrustZone** para proteção de dados e aplicações críticas.

Famílias mostradas: Cortex-A5/A7/A9, A53, A57/A72, A75/A76/A77 e A78.

### Cortex-R

Voltado a aplicações de **tempo real** que exigem alta confiabilidade, como sistemas automotivos e dispositivos médicos. A prioridade é responder com baixa latência e tempo previsível.

- memória *Tightly Coupled*, apresentada no material com a sigla **TMC**, conectada ao núcleo;
- sistema avançado de interrupções;
- dois núcleos em *lockstep*, executando a mesma instrução;
- pipeline determinístico, com tempo de execução previsível.

Famílias mostradas: Cortex-R4, R5, R7 e R8.

### Cortex-M

Voltado a microcontroladores e sistemas que precisam de baixo consumo, custo reduzido e processamento eficiente. Usa um conjunto de instruções simplificado, é apresentado como simples de programar e possui controlador de interrupções embutido **NVIC** (*Nested Vectored Interrupt Controller*).

Famílias mostradas: Cortex-M0/M0+, M1/M3, M4/M7, M23, M33 e M35P.
