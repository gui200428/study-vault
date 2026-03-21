## Implementação da ISA na microarquitetura

**Definição:**  É o processo de tradução e execução onde os comandos de alto nível (a ISA que o programador enxerga) são “quebrados” em passos minúsculos e físicos que os circuitos eletrônicos da CPU conseguem, realizar.
- Um processador não executa diretamente a instrução (ex: ADD, LOAD, JUMP). Ele segue uma sequência de microoperações controladas pelo microcódigo. **As instruções da ISA são como comandos gerais. (Ex: “faça um bolo”). O hardware bruto não entende comandos complexos de uma vez. Ele precisa de uma receita passo a passo. (microcódigo), que diz exatamente qual parte da ALU ativar, qual porta lógica abrir, etc.**

ISA (Instruction set architecture). **E o “contrato” ou o idioma oficial do processador. Camada visível composta pelo comandos (ADD, MOV) e registradores (AX, BX) que o programador ou compilador utilizam para escrever os programas.**

**Relação:**
- Instrução visual ao programador (ISA). **Teoria, o que o processador promete fazer**
- Hardware real que implementa essa instrução. **Microarquitetura (com microcódigo) é a pratica, como o processador foi construído por dentro para cumprir essa promessa.**

**Analogia: A ISA é a “fachada”, painel do carro e o volante, enquanto microarquitetura é o motor do carro. O microcódigo é a mecânica que traduz o giro do volante (instrução da ISA) na ação real.**

## Unidade de controle - tomada de decisões:
**Definição:** A unidade de controle recebe informações e gerencia como os dados vão trafegar em:

- Registradores
- ALU
- Barramentos
- Memória
- Multiplexadores. **Lógicas combinacionais que coordenam com os flags como o circuito vai funcionar.**

## Desempenho e otimização 

- Quando trabalhamos com hardware, entender o funcionamento do microcódigo, vai ajudar com a otimização dad aplicação.

### Hazards:
**Definição:** Qualquer situação que **impede** que o **pipeline** continue executando.

**Pipeline:**
1. Busca
2. Decode
3. Execute
## Ciclos de máquina - base para qualquer arquitetura 

- **Microarquitetura:** Instruções menores dentro da arquitetura. Cada comando tem um conjunto de  microinstruções. **Cada comando tem um conjunto de microinstruções**
- **Ciclos de máquina**: Todas as etapas de um pipeline: (fetch, decode, execute, memory, write-back) É a espinha dorsal da execução de qualquer instrução.

## Arquitetura vs Microarquitetura 

### Arquitetura de conjunto de instruções (ISA):
- É o conjunto de instruções visíveis ao programador

### Microarquitetura:
- É a Implementação da ISA pelo hardware.
- Unidade de controle
- Datapath
- Memória de controle
- Pipeline, caches.

**Microcódigo é um mecanismo interno da microarquitetura.**

### Microcódigo
**Definição:** se trata do conjunto de instruções de baixo nível que controla diretamente a execução dos componentes internos do processador 

- Cada instrução da ISA é implementada como uma sequência de microinstruções.

#### Exemplo:

- ISA: ADD R1, R2, R3
- Microinstruções possíveis:
1. Ler R2 no barramento A
2. Ler R3 no barramento B
3. Executar soma na ALU
4. Armazenar resultado em R1

#### Motivo da existência do microcódigo:
- Simplifica a Implementação de conjuntos de instruções complexas
- Permite atualização via firmware.
- Facilita correção de bugs no hardware.

## Microprogramação:
- Tecnica / método de projetar a unidade de controle usando microcódigo 
- É o processo de escrever microcódigo 

**Analogia:**
**Microcódigo:** roteiro das cenas (o que deve ser feito).
**Microprogramação:** Tecnica de escrever o roteiro (organizar, criar e escrever cenas).