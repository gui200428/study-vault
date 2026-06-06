**Eng de computação - Guilherme Augusto - 05223-071.**

## Objetivo:

O objetivo principal do programa é percorrer um vetor definido por números em DW (2 bytes - 16bits), comparar os elementos para identificar o maior valor dentre eles e armazenar o resultado na memória.

## Descrição da implementação:

Por meio de um algoritmo de varredura linear, utilizando uma estrutura de repetição para verificar cada número do vetor e determinar o valor máximo.

**Forma como o vetor é percorrido:**  
O registrador de índice atua como um ponteiro de memória, ele é responsável por apontar onde cada item do vetor está localizado. Ele é iniciado com o endereço base do primeiro elemento do vetor. Como o vetor é composto por elementos de 16 bits (WORD), cada número ocupa dois bytes na memória. Por esse motivo, a cada repetição do loop, o registrador de índice sofre um incremento de duas unidades (ADD SI, 2), apontando para o próximo endereço de memória referente ao próximo item do vetor.

**Lógica de identificação do maior valor:**  
O programa utiliza um registrador principal que atua como o maior valor encontrado até o momento (inicializado em zero). A cada repetição do loop, o item atual do vetor é lido da memória e comparado com este registrador. Por meio de um salto condicional, se o número lido for menor ou igual ao valor guardado, o programa ignora a atualização e pula para o próximo item do vetor. Se for maior, o registrador principal é atualizado com este novo valor.

**Forma como o laço é controlado:**  
O controle da repetição é gerenciado por um registrador que tem a função de atuar como contador. Antes do loop iniciar, esse registrador é carregado com o valor correspondente ao tamanho total do vetor (lido da memória). Ao final de cada iteração, esse contador sofre um decremento. A estrutura de repetição sempre verifica esse contador e continua a execução, retornando ao inicio do loop, somente se o valor for diferente de zero.

**Forma como o resultado é armazenado:**  
Assim que o loop termina, o registrador principal contém o maior valor do conjunto. O programa acessa uma variável responsável pelo resultado, alocada na memória de dados. O valor de 16 bits contido no registrador principal é transferido e escrito neste endereço de memória, atualizando o valor diretamente na memória de dados e encerrando a execução em seguida.

## Uso dos registradores e da memória:

### Registradores:
| Registrador | Função                                                                                                                                                                                                            |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SI          | Atua como ponteiro de leitura. Tem a função de armazenar o endereço de memória do elemento atual do vetor. É incrementado em 2 unidades a cada iteração.                                                          |
| DI          | Atua como ponteiro auxiliar. Inicialmente, é definido com o endereço de memória da variável de tamanho. Ao final, é definido com o endereço de memória da variável de resultado para gravar o valor na memória. |
| CL          | Responsável por controlar o número de repetições do programa. É inicializado com o valor do tamanho do vetor e decrementado a cada iteração.                                                                      |
| AX          | Atua como o maior valor encontrado até o momento. Guarda este valor durante o loop e, ao final da execução, tem seu conteúdo transferido diretamente para a memória de dados.                                     |
| BX          | Utilizado para carregar o número atual do vetor para comparação. Guarda temporariamente o valor de 16 bits lido da memória para ser comparado com o registrador principal.                                        |

### Memória:
A memória foi estruturada de forma sequencial para armazenar os seguintes itens:

| Variável | Função                                                                                                |
| -------- | ----------------------------------------------------------------------------------------------------- |
| VALORES  | Bloco de memória. Armazena o vetor com os itens de entrada, onde cada elemento ocupa 2 bytes (WORD).  |
| TAM      | Bloco de 1 byte. Armazena o tamanho total do vetor.                                                   |
| MAIOR    | Bloco de 2 bytes. Armazena a saída final do programa. Guardando o maior valor encontrado no conjunto. |
### Código:

```assembly
; ----- dados -----
VALORES:
    DW 10
    DW 50
    DW 20
    DW 40
TAM:
    DB 4
MAIOR:
    DW 0

; ----- código -----
start:
    ; SI -> início do vetor
    MOV SI, OFFSET VALORES
    
    ; CL = tamanho do vetor
    MOV DI, OFFSET TAM
    MOV CL, byte [DI]
    
    ; AX guardará o maior valor encontrado. 
    ; Inicializa com 0 (assumindo valores positivos).
    MOV AX, 0

LOOP_MAX:
    ; Carrega o elemento atual do vetor (WORD) em BX
    MOV BX, word [SI]
    
    ; Compara o MAIOR valor salvo (AX) com o NOVO valor (BX)
    CMP AX, BX
    
    ; Se AX já for Maior ou Igual a BX, pula a atualização
    JGE NEXT
    
    ; Se AX for menor, atualiza AX com o novo maior valor (BX)
    MOV AX, BX

NEXT:
    ; Avança o ponteiro do vetor em 2 bytes
    ADD SI, 2
    
    ; Decrementa o contador do laço
    DEC CL
    
    ; Se o contador não for zero, repete o laço
    JNZ LOOP_MAX

    ; Fim do laço: armazena o maior valor (AX) na variável MAIOR na memória
    MOV DI, OFFSET MAIOR
    MOV word [DI], AX
    
    HLT
```

## Resultado final

Com a finalização do programa, o estado final da memória tem a seguinte organização: 

| Endereço      | Variável | Valor                   |
| ------------- | -------- | ----------------------- |
| 00000 - 00007 | VALORES  | 0A 00 32 00 14 00 28 00 |
| 00008         | TAM      | 04                      |
| 00009 - 0000A | MAIOR    | 32 00                   |

**Estrutura na memória:**
0A 00 32 00 14 00 28 00 04 32 00 00 00 00 00 00 00

O estado final da variável MAIOR é 0x0032 (armazenado como 32 00 devido ao padrão Little Endian), isso significa que o algoritmo percorreu os dados e identificou o valor máximo. Comprovando que 50 (0x0032) é o maior número presente no conjunto.