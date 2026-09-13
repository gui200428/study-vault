## Trabalhos de um sistema operacional:

### 1- Criar abstrações:

- Eliminar a necessidade de gerenciar detalhes de baixo nível, como gerenciamento de processos e de arquivos e memória virtual.

### 2- Gerenciamento de recursos:

- Define quais recursos devem ser dispostos a determinados serviços.
- Gerencia o uso de CPU e memória.
- Determina por quanto tempo estes recursos vão ser usados.

**Funcionamento:** Aplicação demanda por serviços e o sistema operacional coordena o hardware para entregar o resultado esperado.


## Organização por fronteiras:

![[Pasted image 20260910152253.png]]

## Revisão de arquitetura:

### 1. CPU:
- É a unidade central de processamento.
- Executa instruções determinadas pelo software.

### 2. Memória:
- Volátil 
- Guarda informações para uso do software.
- Rápida

### 3. Dispositivos de entrada e saída
- São dispositivos que tem a função de captar ou entregar informações e fornecer ao hardware ou ao usuário.
- Movimentam dados entre o computador e dispositivos e sinalizam eventos.

### 4. Barramento:
- Transportam informações entre os componentes de um computador.
- Dados, endereços e sinais.

## Ciclo da CPU:

### 1. Buscar a próxima instrução
### 2. Decodificar a instrução
### 3. Executar a operação
### 4. Registrar o resultado final da operação


## Interrupções:
![[Pasted image 20260910153230.png]]


## Proteções do sistema:

### 1. Modo do usuário:

- Programas que rodam neste modo, tem privilégios limitados. 
- Não podem executar instruções que podem danificar o sistema.
- Não podem acessar qualquer região da memória.

### 2. Modo kernel

- Núcleo do sistema.
- Pode configurar dispositivos, gerenciar a memória e interrupções.
- Tem permissão de executar instruções destrutivas  para o sistema.


## Mecanismos de hardware que permitem o bom funcionamento do SO:

### 1. Timer
- Gera sinais periódicos e limita o tempo de CPU

### 2. Modo de execução:
- Separa privilégios

### 3. Interrupções:
- sinaliza eventos à CPU

### 4. MMU
- Unidade de gerenciamento da memória. 
-  Traduz e protege endereços

![[Pasted image 20260910153957.png]]

![[Pasted image 20260910154307.png]]


## Multiprogramação esconde a espera de E/S.

- Enquanto um job espera, outro job pode usar a CPU.
![[Pasted image 20260910154616.png]]

![[Pasted image 20260910154642.png]]

## O contexto muda a prioridade do projeto.

![[Pasted image 20260910154729.png]]


## Tempo real - Tipos:

### 1. Tempo real rígido (hard):

Perder o prazo pode causar falha inaceitável.
Ex: controle de airbag.

### 2. Tempo real flexível (soft):

Atrasos degradam a qualidade, porem não tornam o sistema necessariamente inválido.

---

## Pergunta de estudo:

## 1. O que é um sistema operacional:

- É um software básico que controla o hardware e oferece serviços para os programas.
- Sem um sistema, cada programa teria que controlar diretamente todos os dispositivos, como memória e dispositivos de entrada e saída.
- O sistema operacional simplifica o uso da máquina com as abstrações.
- O sistema operacional evita o conflito entre programas, gerenciando o bom funcionamento entre eles e evita o conflito entre dois programas tentando usar os mesmos recursos ao mesmo tempo.

![[Pasted image 20260910155352.png]]

**Abstrair significa esconder detalhes sem esconder a função.**


![[Pasted image 20260910155930.png]]

![[Pasted image 20260910160003.png]]

![[Pasted image 20260910160032.png]]

![[Pasted image 20260910160050.png]]


---

## Comandos do lab:

![[Pasted image 20260910160340.png]]


