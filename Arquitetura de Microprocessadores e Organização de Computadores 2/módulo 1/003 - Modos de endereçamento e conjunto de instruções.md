
## Organização da Memória:

![[Pasted image 20260320165718.png]]


## Relocação:

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


(aula 3 - 11) - teste