## Implementação da ISA na microarquitetura

**Definição:**  É o processo de tradução e execução onde os comandos de alto nível (a ISA que o programador enxerga) são “quebrados” em passos minúsculos e físicos que os circuitos eletrônicos da CPU conseguem, realizar.
- Um processador não executa diretamente a instrução (ex: ADD, LOAD, JUMP). Ele segue uma sequência de microoperações controladas pelo microcódigo. **As instruções da ISA são como comandos gerais. (Ex: “faça um bolo”). O hardware bruto não entende comandos complexos de uma vez. Ele precisa de uma receita passo a passo. (microcódigo), que diz exatamente qual parte da ALU ativar, qual porta lógica abrir, etc.**

ISA (Instruction set architecture). **E o “contrato” ou o idioma oficial do processador. Camada visível composta pelo comandos (ADD, MOV) e registradores (AX, BX) que o programador ou compilador utilizam para escrever os programas.**

**Relação:**
- Instrução visual ao programador (ISA). **Teoria, o que o processador promete fazer**
- Hardware real que implementa essa instrução. **Microarquitetura (com microcódigo) é a pratica, como o processador foi construído por dentro para cumprir essa promessa.**

**Analogia: A ISA é a “fachada”, painel do carro e o volante, enquanto microarquitetura é o motor do carro. O microcódigo é a mecânica que traduz o giro do volante (instrução da ISA) na ação real.**

## Unidade de controle - tomada de decisões:
**Definição:** A unidade de controle (Control Unit) é o "maestro" da CPU. Ela recebe as instruções decodificadas e gerencia como os sinais e dados vão trafegar fisicamente pelos componentes.

- Registradores. **Gaveta de armazenamento rápido**
- ALU **Onde o cálculo matemático ocorre**
- Barramentos 
- Memória
- Multiplexadores. **Lógicas combinacionais que coordenam com os flags como o circuito vai funcionar.**

## Desempenho e otimização 

- Quando trabalhamos com hardware, entender o funcionamento do microcódigo, vai ajudar com a otimização da aplicação.

### Hazards:
**Definição:** Qualquer situação que **impede** que o **pipeline** continue executando.

**Pipeline:**
1. Busca. **Pega instruções da memória**
2. Decodificação. **Descobre o que a instrução faz e gera o microcódigo**
3. Busca de operandos (OF).
4. Execução. **A ALU faz a conta.**
5. Memoria **Acessa a RAM se necessário**
6. Write-back. **Escreve o o resultado final de volta no registrador**
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
- Técnica / método de projetar a unidade de controle usando microcódigo 
- É o processo de escrever microcódigo 

**Analogia:**
**Microcódigo:** roteiro das cenas (o que deve ser feito).
**Microprogramação:** Técnica de escrever o roteiro (organizar, criar e escrever cenas).


## Ciclos de máquina
→ Uma instrução executa em vários ciclos de máquina. Cada ciclo corresponde a um conjunto de microinstruções.

→ Quanto mais rápido se executa a ação, melhor é o desempenho.

**Exemplo clássico de ciclo de maquina:**

**Pipeline:**
1. Busca de instruções (IF). **Pega instruções da memória**
2. Decodificação (ID). **Descobre o que a instrução faz e gera o microcódigo**
3. Busca de operandos (OF).
4. Execução (EX). **A ALU faz a conta.**
5. Memoria (MEM) **Acessa a RAM se necessário**
6. Write-back (WB. **Escreve o o resultado final de volta no registrador**
**Cada instrução é um ciclo de clock.**


## Controle cabeado vs controle microprogramado:

### Controle cabeado:
- Sinais de controle gerados por lógica combinacional. Se usa portas lógicas para realizar todas as operações.
- Menor flexibilidade.

### Controle microprogramado:
- Sinais gerados por leitura de microinstruções.
- Usado em arquiteturas mais complexas
- Totalmente flexível, permitindo instruções complexas.
- x86

![[Pasted image 20260321194431.png]]

### Exemplo de execução microprogramada:

![[Pasted image 20260321194513.png]]


## Microarquitetura relevante do 8086:

![[Pasted image 20260321194610.png]]


## T - state
→ Leva 1 ciclo de clock para executar cada T-state

![[Pasted image 20260321194735.png]]

### WAIT
- Se a memória ou dispositivo **não estiver pronto** durante o T3, o sinal READY fica desativado.
- Então a CPU insere ciclo de espera.

![[Pasted image 20260321194859.png]]

![[Pasted image 20260325145220.png]]

![[Pasted image 20260325145231.png|668]]

![[Pasted image 20260325145246.png]]
