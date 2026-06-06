
**Eng de computação - Guilherme Augusto - 05223-071.**

## Objetivo:

O objetivo principal do programa é percorrer um vetor de números, verificar quais números são menores que o valor limite definido, contar quantos números atendem a essa condição e armazenar o total na memória.

## Descrição da implementação:

Por meio de um algoritmo de varredura linear, utilizando uma estrutura de repetição para verificar cada número do vetor de forma individual. 

**Forma como o vetor é percorrido:**
O registrador de índice atua como um ponteiro de memória, ele é responsável por apontar onde cada item do vetor esta localizado. Ele é iniciado com o endereço base do primeiro elemento do vetor. A cada repetição do loop, o registrador de índice sofre um incremento, apontando para o próximo endereço de memória referente ao próximo item do vetor.

**Forma como o laço é controlado:**
O controle da repetição é gerenciado por um registrador que tem a função de atuar como contador. Antes do loop iniciar, esse registrador é carregado com o valor correspondente ao tamanho total do vetor. Ao final de cada iteração, esse contador sofre um decremento. A estrutura de repetição sempre verifica esse contador e continua a execução, retornando ao inicio do loop, somente se o valor for diferente de zero.

**Forma como o resultado é armazenado:**
Dentro do loop, o elemento atual é carregado e comparado com o valor limite. É utilizada uma lógica de salto condicional invertida: se o valor for maior ou igual ao limite, o programa salta a etapa de contagem. Se o valor for menor, o programa acessa uma variável responsável pela contagem, alocada na memória de dados. O valor contido neste endereço de memória é lido e incrementado em 1 e reescrito no mesmo endereço, atualizando o valor de RESULT diretamente na memória de dados.

## Uso dos registradores e da memória:

### Registradores:

| Registrador | Função                                                                                                                                           |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| SI          | Atua como ponteiro de leitura. Tem a função de armazenar o endereço de memória do elemento atual do vetor. É incrementado a cada iteração        |
| DI          | Após as inicializações, é definido com o endereço de memória da variável result. Possibilita o acesso à memória para ler e atualizar a contagem. |
| CL          | Responsável por controlar o número de repetições do programa. É inicializado com o valor do tamanho do vetor e decrementado a cada iteração.     |
| AL          | Utilizado para carregar o número atual do vetor para comparação e carregar temporariamente o valor de result da memória para ser incrementado.   |
| BL          | Guarda o valor de referência (limite) de forma estática durante o loop. Evita a necessidade de ler o limite da memória a cada comparação.        |

### Memória:
A memória foi estruturada de forma sequencial para armazenar os seguintes itens:

| Variável | Função                                                                                                      |
| -------- | ----------------------------------------------------------------------------------------------------------- |
| VETOR    | Bloco de 5 bytes. Armazena o vetor com os 5 itens.                                                          |
| TAM      | Bloco de 1 byte. Armazena o tamanho total do vetor.                                                         |
| LIMITE   | Bloco de 1 byte. Armazena o valor de limite.                                                                |
| RESULT   | Bloco de 1 byte. Armazena a saída final do programa. Guardando a contagem dos valores menores que o limite. |

### Código:

```
; ----- dados -----
VETOR:
    DB 3
    DB 10
    DB 7
    DB 2
    DB 15
    
TAM:
    DB 5
    
LIMITE:
    DB 5
    
RESULT:
    DB 0
; ----- código -----
start:
    ; SI -> início do vetor
    MOV SI, OFFSET VETOR
    ; CL = tamanho do vetor
    MOV DI, OFFSET TAM
    MOV CL, byte [DI]

    ; RESULT = 0
    MOV DI, OFFSET RESULT
    MOV AL, 0
    MOV byte [DI], AL
    ; carrega LIMITE em BL
    MOV DI, OFFSET LIMITE
    MOV BL, byte [DI]
    ; DI volta para RESULT
    MOV DI, OFFSET RESULT
LOOP_VER:
    MOV AL, byte [SI]
    CMP AL, BL          ; AL-BL. Se AL=BL, ZF = 1
    JGE NEXT            ; Jump if Greater or Equal
    MOV AL, byte [DI]
    INC AL
    MOV byte [DI], AL
NEXT:
    INC SI
    DEC CL
    JNZ LOOP_VER
    HLT
```

## Resultado final

Com a finalização do programa, o estado final  da memória tem a seguinte organização: 


| Endereço      | Variável | Valor          |
| ------------- | -------- | -------------- |
| 00000 - 00004 | VETOR    | 03 0A 07 02 0F |
| 00005         | TAM      | 05             |
| 00006         | LIMITE   | 05             |
| 00007         | RESULT   | 0x02           |

**Estrutura na memória:**
03 0a 07 02 0f 05 05 02

O estado final da variável RESULT é 0x02, isso significa que o algoritmo percorreu os dados e contabilizou dois incrementos. Comprovando que só existem dois números menores que o limite 5.