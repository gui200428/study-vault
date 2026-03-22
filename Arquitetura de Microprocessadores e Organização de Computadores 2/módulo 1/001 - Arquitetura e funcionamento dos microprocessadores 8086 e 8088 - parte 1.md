
## Revisando:

### Organização

→ Trata de como os recursos do hardware são implementados
→ Trata dos componentes físicos de um computador
→ Tecnologia de memórias, interconexões, interfaces e construção dos dispositivos.

### Arquitetura

→ Trata dos componentes implementados
→ Tamanho das memórias e barramentos
→ Conjunto de instruções e registradores
→ Numero de bits para representação dos dados


## Pipeline

**Definição:** Semelhante a uma linha de montagem de uma fábrica, o pipeline divide a execução de uma instrução em **etapas sequenciais**, possibilitando que sejam executadas **simultaneamente** para diferentes instruções.


**Vantagens do Pipeline:**
- Desempenho melhor, instruções são processadas simultaneamente.
- Melhor aproveitamento do processador, reduz o tempo ocioso.
- Execução mais rápida.

## Execução em função do Clock - Pipeline simplificado

**Cada instrução passa por 5 etapas, divididas em estágios de pipeline:**
- IF (fetch) → Busca a instrução na memória.
- ID (decode) → Decodifica a instrução na memória.
- EX (execute) → Executa a operação.
- MEM (memory) → Acessa a memória (caso necessário).
- WB (Write back) → Escreve o resultado no registrador de destino.

**OBS:** Cada estágio é executado em um ciclo de clock, e múltiplas instruções podem estar em diferentes estágios ao mesmo tempo. Tudo graças ao pipeline!

---

# Arquitetura - Evolução da Família 8086 / 8088

## Processadores antecessores ao 8086/8088

### 1. Intel 4004 (Primeiro Microprocessador).

- Lançado em 1971.
- Primeiro microprocessador comercial.
- Arquitetura de 4 bits.
- Usado em calculadoras.

### 2. Intel 8008 e Expansão.

- Lançado em 1972.
- Melhorou a capacidade computacional - 8 bits!
- Instruções.
-  mais sofisticadas para sistemas experimentais.

### 3. Intel 8080 e Computadores pioneiros

- Lançado em 1974.
- Adotado em computadores pessoais pioneiros.
- Definiu a arquitetura base para futuros chips.


### 4. Intel 8085 - Versão Aprimorada

- Lançado em 1976.
- Integrou o controlador de clock e eficiência elétrica.
- Popular em sistemas embarcados e industriais.



## Motivos para a criação do 8086 / 8088

### 1. Evolução para 16 bits

- Migrar de 8 para 16 bits aumentou a capacidade computacional e o acesso a memória. Superando limitações anteriores

### 2. Pressão competitiva

- Concorrência intensa outros processadores como: Motorola 68000 e Zilog Z80.

### 3. Compatibilidade com o  8080

- A compatibilidade de instruções com o 8080 facilitou e permitiu a migração de softwares antigos para a nova arquitetura.

### 4. Adoção comercial e custo

- O 8088 oferecia uma opção econômica com barramento de 8 bits.


## Comparativo entre o 8086 e 8088:

### 1. 8086:

- Microprocessador de 16 bits.
- Barramento de dados de 16 bits.
- Barramento de endereços de 20 bits.

### 2. 8088:

- Microprocessador de 8 / 16 bits.
- Barramento de dados de 8 bits.
- Barramento de endereços de 20 bits.

**Possuem uma arquitetura interna muito semelhante, porem com interfaces como barramento diferentes.**


## Pinagem:


![[Pasted image 20260319161423.png]]


## Modos Máximos e Mínimos:

**Definição:** São duas configurações de hardware (Selecionadas por um pino físico no chip.) Definem a escala e a arquitetura do sistema em que os microprocessadores vão operar.

### Modo mínimo:
**Definição:** O microprocessador assume o controle total, gera diretamente todos os sinais de controle necessários para ler e escrever na memória e se comunicar com os periféricos.
Foi criado para sistemas pequenos e de processador único.

- Não permite o uso de coprocessador.
- Design da placa mãe fica mais barato e simples, não exige chips extras para gerenciar a comunicação.

### Modo máximo:
**Definição:** O microprocessador “terceiriza” a geração dos sinais de controle. Ele envia apenas sinais de status para um chip externo.. (Controlador de barramento intel 8288). O chip 8288 traduz o status e gera os comandos reais para a memória e periféricos.

- Ao delegar essa função, o processador muda a finalidade de alguns de seus pinos para permitir o suporte a outros processadores trabalhando na mesma placa. (Isso permite conectar um coprocessador matemático - como o 8087.)

### Resumo:

![[Pasted image 20260319162608.png]]


### Esquema do 8088 no modo mínimo e máximo:

![[Pasted image 20260319162714.png]]



## Diagrama funcional do microprocessador:

![[Pasted image 20260319162856.png]]



## Arquitetura interna dos microprocessadores 8086 / 8088:

### 1. Unidades BIU e EU:

- BIU (Bus interface unit): Gerencia operações de memória e barramentos. (Busca as instruções e dados na memória).
- EU (Execution Unit): Executa instruções e contém a ALU (Unidade lógica e Aritmética).
- ALU: Cérebro matemático do processador. Localizado dentro da EU, tem função exclusiva de realizar os cálculos reais que os programas exigem.


### 2. Fila de Pré-busca:

- BIU usa a fila de pré-busca para buscar instruções.
- A EU executa as instruções, criando um pipeline básico.

### 3. Registradores Flexíveis de 16 e 8 bits:

- O registradores principais da EU (AX, BX, CX, DX) têm 16 bits.
- Para maior flexibilidade e compatibilidade com dados de 8 bits, cada um dos registradores podem se subdividir em dois registradores menores.
- Parte alta (H - high) e parte baixa (L - Low). 
- Os modificadores AL ou AH, alteram metades independentes do AX.

### 4. Diferença entre o 8086 e o 8088:

- **8088:** possui barramento externo de 8 bits, reduzindo a taxa de busca e desempenho comparado ao 8086. (Veio como uma solução mais barata ao 8086.)
- **8086:** possui um barramento externo de 16 bits, permitindo um fluxo maior de dados. Possui um desempenho melhor comparado ao 8088.


## Modos de endereçamento e organização dos registradores:

### Principais Modos de Endereçamento:

**Definição:** Diferentes métodos que o processador usa para descobrir onde estão os dados necessários para executar uma instrução.

1. **Imediato:** Dado já vem embutido na própria linha de código da instrução. Não requer busca na memória.
2. **Registrador:** O dado está armazenado dentro de um registrador interno da CPU. 
3. **Direto:** A instrução contém o endereço exato de 16 bits apontando para a posição do dado na memória principal.
4. **Indireto:** A instrução aponta para um registrador, dentro dele está guardado o endereço de memória onde o dado real se encontra.

### Modos Avançados de Endereçamento:

**Definição:** Método que calculam o endereço de memória de forma dinâmica, combinando registradores e valores fixos matematicamente. Servem especificamente para manipular blocos de dados organizados.

1. **Base + Deslocamento / Indexado:** O processador pega um valor de um registrador (Base ou índice) e soma a uma constante (Deslocamento). É uma técnica principal para acessar elementos iterativos em arrays.

2. **Base + índice + Deslocamento:** Método mais flexível. O processador soma três valores: um registrador base, um registrador de índice e uma constante. É uma estrutura fundamental para navegar em dados multidimensionais. (Matrizes / tabelas complexas)


### Organização dos Registradores:

**Definição:** A arquitetura interna do 8086 e 8088 divide seus registradores de 16 bits em grupos especializados, cada um responsável por uma parte do gerenciamento de dados, navegação na memória ou controle de fluxo do programa.

1. **Gerais (AX, BX, CX, DX):** Utilizados como área de trabalho para a ALU, servem para armazenar dados temporários, resultados de contar e contadores de loop.

2. **De segmento (CS, DS, SS, ES):** Utilizados para definir uma mapa da memórias. Eles guardam endereços iniciais dos quatro grandes blocos de 64kb nos quais os programas são divididos: Código (CS), Dados (DS), Pilha/stack (SS), Extra (ES).

3. **Ponteiros e índices (SP, BP, SI, DI):** Trabalham em conjunto com os registradores de segmento. Eles armazenam o “Offset” (Deslocamento), que é a distancia exato do inicio do segmento até o dado específico que se quer acessar.

4. **Controle (IP e FLAGS):** O IP (Instruction Pointer) é o guia do programa, sempre aponta qual é a próxima instrução que deve ser lida. O registrador de **FLAGS** atua como um painel de status da CPU, com bits individuais indicando resultados da última operação.


## Organização da memória - little-endian

**Obs:** 8086/8088 são processadores little-endian.

**Como funciona:** o dado é armazenado na memória do menos significativo → mais significativo. O menos significativo fica armazenado no menor endereço.

### Exemplo prático:

![[Pasted image 20260319172801.png]]



### Little-endian x Big endian:

![[Pasted image 20260319172840.png]]


## Pipeline EU/BIU e fluxo de execução:

### 1. Divisão das unidades EU e BIU

- **BIU:** Gerencia pré-busca e barramentos
- **EU:** Decodifica e executa instruções em paralelo, otimizando desempenho.

### 2. Fluxo de execução no Pipeline:

- Pré-busca das instruções
- Decodificação das instruções
- Execução das instruções
- Atualização das instruções
**Executados em sequencia continua para minimizar tempo ocioso.**


### 3. Diferenças entre 8086 e 8088:

- **8086:** Barramento de 16 bits para pré-busca rápida.
- **8088:** Sofre limitações com barramento de 8 bits.

### 4. Impacto na arquitetura x86:

- A divisão EU/BIU influenciou gerações posteriores, expandindo o paralelismo interno dos processadores x86 e x64.



## Esquema da Unidade de Execução:

![[Pasted image 20260319173543.png]]


## Registradores:

### 1. Registradores de 8bits:
- AL / AH / BL / BH / CL / CH / DL / DH
**Divididos em Low e high!**


### 2. Registradores de 16bits:

- AX=AH:AL
- BX=BH:BL
- CX=CH:CL
-  DX=DH:DL
-  SI,DI,BP
-  SP
-  IP
-  Flags
-  CS,DS,SS,ES

### 3. Registradores de uso específico:

- Ponteiro de instruções: IP
- Ponteiro de pilha: SP
- Flags
- Segmento de código: CS
- Segmento de dados: DS
- Segmento de pilha: SS
- Segmento extra: ES

### 4. Personalidade dos registradores:

- Quase todas as instruções do 8086 / 8088 são simétricas em relação aos registradores.
- Alguns registradores possuem usos preferenciais
- Acumulador: AL ou AX
- Base: BL, BX ou BP
- Contador: CL ou CX
- Dados: DL ou DX
- Índice de fontes: SI
- Índice de destino: DI

### 5. Flags:

- Carry: CF
- Paridade: PF
- Carry Auxiliar: AF
- Zero: ZF
- Sinal: SF
- Trap: TF
- Interrupção: IF
- Direção: DF
- Overflow: OF


### 6. Registradores de segmento:

**Dependendo do tipo de acesso à memória é utilizado um registrado de segment:**

- CS: busca de instruções
- DS: acesso à dados na memória
- SS: Acesso à pilha (Endereçamento indireto por SP ou BP).
- ES: Destino de operações de string

**As instruções podem utilizar um prefixo para utilizar um segmento diferente do default.**



## Sucessores:

### 1. Integração no 80186:

- O 808186 integrou controladores e periféricos. Ideal para sistemas embarcados. Pouco usado em PCs

### 2. Avanços do 80286 e 80386:

- 80286 introduziu modo protegido e gestão de memória.
- 80386 trouxe a arquitetura de 32 bits e paginação ampliada.


### 3. Inovações do 80486 e Pentium:

- 80486 trouxe pipeline e cache L1.
- Pentium introduziu a execução superscalar para múltiplas unidades simultâneas.

### 4. Família Intel core Moderna:

- Múltiplos núcleos
- Eficiência energética
- Pipelines curtos
- Base para CPUs modernas.