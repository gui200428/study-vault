
## Organização da Memória:

![[Pasted image 20260320165718.png]]


## Realocação:

**Definição:** É o conflito que ocorre em sistemas multitarefa quando o programador (ou compilador) precisa gerar referência de memória para um programa, mas não faz a menor ideia de em qual parte física da RAM esse programa será efetivamente carregado.

- Em um sistema multitarefa, várias tarefas (programas / processos)são carregadas na memória ao mesmo tempo. Como a memória é compartilhada, **cada tarefa é carregada em um endereço inicial diferente,** dependendo do que está livre naquele momento.

- **Referências quebradas:** O código de um programa é cheio de chamadas para endereços de memória (onde fica o inicio do programa, onde estão armazenadas as variáveis, vetores, ou para onde um comando de desvio deve pular).

- **O problema:** Se um programa for escrito usando endereços fixos (absolutos)e o sistema operacional o carregar em um lugar diferente do esperado, todas as referências apontarão para o lugar errado, causando o travamento do sistema.

### O problema da realocação (Relocation problem):

**Definição:** é o desafio de fazer com que um programa funcione perfeitamente em qualquer lugar da memória RAM, ja que em computadores modernos, não sabemos com antecedência qual ponto estará livre para o programa.

- Se o compilador gerar endereços fixos (absolutos), o programa só funciona se fosse carregado exatamente em um endereço específico.
- **Isso é inviável em sistema multitarefa!**

### 1. Solução parte 1: Gerar código com endereços relativos:
**Definição:** Técnica de compilar o programa usando “distâncias” em vez de  “coordenadas fixas”, tornando o código independente e capaz de se adaptar a qualquer região da memória.

- **A solução mais usada é fazer com que o compilador e o linker não gerem endereços absolutos, e sim Endereços relativos!** No lugar de apontar para um local fixo na memória física, as referências do código apontam para uma distância a partir da posição da instrução.

- **Em vez de gravar no código um endereço como: JUMP 2000, o compilador gerar algo como: JUMP (PC + offset).** O programa troca um comando fixo para algo dinâmico. Ele faz isso usando o PC (Program Counter, equivalente ao IP do 8086) somando a um deslocamento (offset).

- **Ou seja, o desvio é calculado em relação ao endereço atual, não como um endereço fixo da memória.** Isso garante que, não importa qual bloco da memória o programa seja jogado.

- **Esse tipo de programa é chamado de: Código realocável (relocatable code). É um código que pode ser realocado para qualquer posição da memória sem deixar de funcionar.**  

### 2. Solução parte 2: Realocação durante a carga:
**Definição:** Técnica onde o sistema operacional (por meio do loader) ajusta fisicamente as referências de memória do programa no exato momento em que ele é colocado na RAM, corrigindo os valores baseados na posição real que ele vai ocupar.

- **Mesmo usando endereços relativos, ainda existe casos em que o programa precisa saber o endereço absoluto.** (Ex: início da área de dados, endereço base do stack, ponteiros para vetores grandes, chamadas entre módulos). Apesar de os endereços relativos ajudarem muito, eles não resolvem tudo. Algumas estruturas críticas precisam saber a coordenada exata na memória física para funcionarem e se comunicarem corretamente.

- Nesses casos, o linker/loader faz: **Realocação durante o carregamento (load-time relocation).** O programa não tenta adivinhar onde vai ficar durante a programação. Ele deixa essa referências absolutas “em aberto”, e um componente do sistema operacional chamado **loader** resolve essa pendência apenas na hora da execução.

- **Quando o programa é carregado, o sistema operacional: Escolhe um endereço-base (Ex: 0x2000), procura no executável todos os pontos que precisam ser ajustados, Soma esse endereço-base aos valores internos do programa.** O sistema operacional faz um trabalho de “busca e substituição” matemático. Ele acha um campo livre na RAM (endereço-base) e varre o código do programa atualizando todas as referências, somando esse valor base a elas.

- **Exemplo:** Se o programa foi escrito esperando começar no endereço 0: Variável X está no offset 120. E o sistema operacional decide carregar o programa no endereço 2000: Endereço real de X é = 2000 + 120 = 2120. O loader modifica o programa na hora do carregamento. Isso também é parte do processo chamado relocation. (**O compilador cria o programa com a ilusão de que ele será o único a rodar no computador, começando do zero. O loader desfaz essa ilusão, pegando a posição física inicial de verdade (2000) e somando à distância interna da variável (120), encontrando o campo exato (2120) na memória.**)

### Em resumo:

#### Sem relocação:
- O programa assume que começa em um endereço fixo.
- Só funciona se carregado exatamente naquele endereço.

#### Com relocação:
- O código é gerado usando endereços relativos sempre que possível.
- O loader ajusta os poucos endereços absolutos no momento da carga.
- O programa funciona em qualquer lugar da memória.


## Segmentação:
**Definição:** é uma técnica de gerenciamento de memória onde o espaço lógico de um programa é dividido em blocos (segmentos), garantindo que o sistema saiba exatamente onde cada programa começa e até onde ele tem permissão de ir.

- **Associa-se a cada área de memória um valor de base e um valor de limite.** Em vez de jogar o programa “solto” na RAM, o sistema define uma cerca para ele, marcando exatamente onde a parte dele começa (base) e qual é o tamanho máximo dessa parte. (limite).

- **Base= endereço inicial, limite= endereço máximo ou tamanho.** A “base” aponta para o primeiro byte do segmento na memória física. O “limite” dita a quantidade de bytes que pertencem a ele, criando uma fronteira.

- **Todas as tarefas são codificadas assumindo que sua área de memória começa em 0.** Voltando a “ilusão” criada pelo compilador para gerar o “código realocável”: para facilitar a programação, o código é gerado como se ele fosse o dono absoluto da memória, usando endereços relativos a partir do 0.

- **Quando a tarefa é selecionada para executar, base e limite são carregados pelo Sistema operacional em registradores especiais na CPU.** Na hora do carregamento, o sistema operacional acorda o hardware e insere as coordenadas reais para que o processador possa trabalhar.

**→ A execução prática da segmentação, onde o hardware do processador traduz os endereços em tempo real e atua como um “guarda”, bloqueando acessos não autorizados.**

- **Endereço físico = offset + base**. Essa é a tradução matemática final, o processador pega a distância interna que o programa pediu (offset/deslocamento) e soma com a coordenada de inicio real do segmento (base) para achar o ponto correto na RAM

- **Soma feita por hardware a cada acesso à memória.** Esse cálculo não é feito pelo software, o próprio circuito eletrônico da CPU faz a conta fisicamente, em frações de segundo, toda vez que precisa ler ou escrever algo.

- **Endereços são verificados quanto ao limite. Uma tarefa não pode acessar a área das outras.** Antes de fazer a leitura, o hardware confere se o offset é maior que o “limite” estipulado. Se for maior, a CPU bloqueia o acesso na mesma hora. É isso que protege o computador e gera o **segmentation fault (falha de segmentação)** quando um programa tenta invadir o espaço do outro.

- **O selector e descrito de segmento são controlados pelo Sistema operacional.** O SO é o responsável  por gerenciar a memória. Ele é responsável por criar o “descritor” (documento que contém o endereço base e o limite do segmento) e fornece o “seletor” (um tipo de chave / índice que aponta para o documento.)

- **O offset é controlado pelo programa de aplicação.** O programa só tem liberdade de movimento dentro do seu próprio espaço. Ele solicita dados usando apenas o offset, navegando estritamente dentro da área que o sistema operacional já designou para ele.

- **Proteção: Usualmente o descript de segment tem alguns bits associados que são utilizados para determinar as características de proteção do segment. Permissões de leitura, escrita, execução.** Além de definir onde o segmento começa e termina, o descritor funciona como um cartão de accesso. Esses bits de proteção (Access rights) definem a finalidade daquele bloco: se é apenas para ler dados, se pode alterar/escrever, ou se contém código que pode rodar. Se um programa tentar escrever em um segmento marcado apenas como leitura, o hardware da CPU intercepta e bloqueia a ação.

- **Cache de descript de segment.** Toda vez que o processador vai acessar a memória, ele precisa checar a base, o limite e as permissões. Fazer isso buscando as regras na memória RAM o tempo todo, deixaria o computador lento. Por esse motivo, a CPU guarda os descritores do segmentos que estão em uso dentro da cache. Isso permite que a verificação de segurança aconteça na velocidade do processador, sem atrasar o sistema.

**Obs: Essa dinâmica de segurança em que o programa não pode mexer no descritor, só no offset, é o que impede que um vírus simples ou um programa travado corrompa o sistema operacional.**


### O que é um cache descritor de segmento? (Papel das tabelas GDT/LDT)
**Definição:** O “descritor” funciona como o cartão de acesso, definem as permissões. É armazenado na cache para acesso rápido.

- Nos processadores x86, cada segmento (código, dados, pilha, etc.) é definida por um **descritor** armazenado nas tabelas de segmento: GDT (Global Descriptor Table) e LDT (Local Descript Table). **O sistema Operacional guarda todas essas fichas cadastrais em grandes arquivos (tabelas) na memória RAM. A GDT é a tabela geral (regrais do sistema inteiro), e a LDT é a tabela local (regras específicas de um programa individual).**

- Cada descritor contém informações como: Endereço base do segmento, tamanho do segmento (limit), privilégios (ring 0-3) e bits de controle e proteção. **Essa ficha tem tudo o que o hardware precisa saber para liberar o acesso: onde o campo começa (base), qual é o limite do campo (limit), nível de segurança exigido (Ring 0 para o núcleo do SO, Ring 3 para o usuário comum) e o que pode ser feito lá (apenas ler, ou ler e escrever).**

- Sempre que o processador precisa acessar a memória via segmentação, ele precisa dessas informações. **A CPU é “cega”. Antes de buscar a varável X que o seu programa pediu, ela é obrigada a ler essa ficha cadastral para descobrir o endereço físico real.**

### O problema: acessa o descritor na RAM é muito lento!
**Definição:** É o gargalo de desempenho massivo que aconteceria se a CPU fosse obrigada a ir até a RAM para ler a “ficha cadastral”. (na GDT ou LDT) antes de poder ler o dado real que o programa solicitou.

- Para obter o descritor correspondente a um seletor de segmento, o processador precisaria: 
1. Ler o seletor de segmento do registrador (ex: CS, DS, SS, ES, FS, GS)
2. Usar o seletor como índice na GDT ou LDT
3. Acessar a memória para buscar o descritor.
- **Sem o cache, a CPU teria que parar tudo, olhar para o registrador (como o DS), usar o valor que está lá como índice para procurar a linha correta lá na tabela da RAM, ler as regras, e só depois fazer o cálculo matemático da segmentação.**

- Isso significa **pelo menos 1 ou 2 acessos à memória** toda vez que um endereço segmentado fosse utilizado, isso seria extremamente lento. **A memória RAM é absurdamente mais lenta que a CPU. Se para cada variável ou linha de código que o programa fosse ler, o processador precisasse fazer 2 ou 3 viagens à RAM, o desempenho do computado despencaria. 

→ **Basicamente: GDT fica na RAM (lenta), então a CPU copia os descritores mais usados para o cache interno (muito rápido).**

### Solução: Cache de Descritor de Segmento!

- Para evitar esse problema, cada registrador de segmento (CS, DS, etc.) tem internamente:
1. Um seletor (parte visível ao programador)
2. Um cache de descritor de segmento (parte interna, invisível).
- **Na prática, os registradores de segmento são divididos em duas partes. A primeira é o “seletor”, que é o índice que o programa enxerga e manipula. A segunda é o “cache” (registrador “sombra”), que o programador não vê e nem consegue alterar, mas que o hardware usa para guardar fisicamente a “ficha cadastral” completa dentro da própria CPU.**

- O cache guarda:
1. Base de segmento
2. Limit
3. Tipo de privilégios
4. Flags de proteção,
- **Quando o sistema operacional carrega um número no seletor (visível), o processador vai rapidamente até a tabela na RAM (GDT/LDT), copia todas essas informações críticas de localização e segura e as armazena na cache.**

- Quando o CPU faz um acesso à memória, **ele usa diretamente esse cache,** sem tocar na GDT ou LDT. **Grande ganho de desempenho, como as informações ja estão na cache, a CPU resolve tudo instantaneamente. Só fará o acesso as tabelas na RAM (GDT/LDT) novamente se o programa trocar de segmento. (se alterar o valor do seletor no registrador CS, DS, etc.)**

### Resumo: Cache de Descritor de Segmento:

- **O cache de descritor de segmento:**

- Armazena localmente as informações do descritor (base, limite, permissões).
- Evita que o processador tenha que buscar o descritor na GDT/LDT o tempo todo.
- Aumenta o desempenho de forma significativa.
- Só é atualizado quando um **novo seletor de segmento** é carregado no registrador.


## Segmentação no 8086/8088


![[Pasted image 20260321161039.png]]


## Conjunto de instruções x86
**Definição:** É o “dicionário” fundamental que os processadores da família intel/AMD entendem. Trata-se do catálogo de comandos embutidos no hardware que dita exatamente o que a CPU consegue fazer com os dados.

- O x86 é uma arquitetura CISC (Complex Instruction Set Computer), criada originalmente pela intel. **A arquitetura x86 tem instruções “grandes”. Uma única instrução CISC pode fazer várias coisas ao mesmo tempo, como ler um dado da memória, fazer a soma e já guardar o resultado na RAM.**

- Seu conjunto de instruções é extenso, evoluindo ao longo de décadas (8086 -> 80286 -> 80386 -> Pentium -> x86-64/AMD64). **O grande ponto do x86 é a retrocompatibilidade. Um processador moderno, como um intel Core i9 de 64 bits ainda entende exatamente os mesmo comandos básicos das arquiteturas antigas 8086 de 16 bits.**

- As instruções podem ser divididas em **categorias:**
1. Instruções de transferência de dados. **Movem informações entre registradores e a memória (EX: comando MOV).**
2. Instruções Aritméticas. **Matemática básica, como soma, subtração e multiplicação. (Ex: ADD, SUB).**
3. Instruções lógicas / de bits. **Operações booleanas e deslocamento de bits. (Ex: AND, OR, SHL).**
4. Instruções de controle de fluxo. **Mudam o rumo do programa, fazendo saltos ou loops de repetição. (Ex: JMP, LOOP).**
5. Instruções de comparação e testes. **Comparam valores para ajudar o processador a tomar decisões (Ex: CMP).**
6. Instruções de manipulação de strings. **Lidam com sequências longas de bytes ou textos na memória.**
7. Instruções de manipulação de processador. **Controlam o hardware e as flags diretamente.**
8. Instruções de ponto flutuante (x87). **Um conjunto separado focado apenas em matemática complexa com números decimais (virgula).**
9. Extensões multimídia / SIMD. **Comandos modernos (como SSE e AVX) feitos para processar grandes blocos de dados de áudio, video e gráficos de uma vez só.**
10. Instruções do modo x86-64 (AMD64). **Comando exclusivos que aproveitam a capacidade total dos processadores atuais de 64 bits.**


### 1. Instruções de transferência de dados:
**Definição:** movem dados entre registradores, memória e constantes.

**Exemplos:**

$$MOV AX, BX$$

$$PUSH \ EAX$$
$$LEA RAX, [RBX+4]$$
![[Pasted image 20260321163221.png|342]]


### 2. Instruções aritméticas:
**Definição:**operações com inteiros e flags

![[Pasted image 20260321163317.png|342]]


### 3. Instruções Lógicas / de Bits:
**Definição:** manipulam bits.

![[Pasted image 20260321163408.png|342]]

### 4. Instruções de controle de fluxo:
**Definição:** Contem saltos condicionais e incondicionais.

**Saltos incondicionais:**
- JMP

**Saltos condicionais (dependem de flags):**
- JE, JNE
- JG, JL, JGE, JLE
- JC, JNC
- JO, JNO
- JZ, JNZ

**Chamadas e retornos:**
- CALL
- RET

### 5. Instruções de comparação e testes
**Definição:** Manipulam flags sem alterar operandos:

![[Pasted image 20260321163713.png|342]]


### 6. Instruções de manipulação de Strings
**Definição:** Trabalham com sequência de bytes/palavras e podem usar REP.

- MOVSB, MOVSW, MOVSD, MOVSQ
- STOSB, STOSW, STOSD, STOSQ
- LODSx
- SCASx
- CMPSx
- Prefixos: REP, REPE, REPNE
### 7. Instruções de Manipulação de processador:

- NOP
- HLT
- CPUID
- STI, CLI
- IN, OUT (I/O por portas)

### 8. Instruções de ponto flutuante (x87):

- Registradores: ST(0)...ST(7)
- FADD, FSUB
- FMUL, FDIV
- FLD, FST
- FCOM

### 9. Extensões multimídia / SIMD

Incluem MMX, SSE, AVX, AVX2, AVX-512.

- Exemplos:
- MMX: PADDW, PMULLW
- SSE: MOVAPS, ADDPS, SUBPS
- AVX: versões com prefixo V → VADDPS, VMULPS
- AVX-512: VPADDQ, VPMULLD, etc.

### 10. Instruções do modo x86-64 (AMD64)

- Novos registradores: R8-R15
- Novos modos de endereçamento
- Versões estendidas de MOV, arithmetic, shifts, etc.

