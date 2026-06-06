
**Eng de computação - Guilherme Augusto - 05223-071.**

## Objetivo:

O objetivo principal do programa é percorrer um vetor de bytes, calcular a soma de todos os elementos e armazenar o resultado total na memória. Seguindo os seguintes pontos:

**Função do programa principal:**
- Inicializar os registradores.
- Chamar a macro.
- Armazenar o resultado na memória.

**Função do macro:**
- Percorrer um vetor de bytes.
- Calcular a soma dos elementos.
- Retornar o valor no registrador AL.
- Utilizar SI como ponteiro e CL como contador.

## Descrição da implementação:

Por meio de um algoritmo de varredura linear, estruturado de forma modular, utilizando uma estrutura de repetição para somar cada número do vetor de forma individual. O funcionamento lógico baseia-se nas seguintes etapas:

**Forma como o vetor é percorrido:**  
O registrador de índice atua como um ponteiro de memória, ele é responsável por apontar onde cada item do vetor está localizado. Ele é iniciado com o endereço base do primeiro elemento do vetor. A cada repetição do loop, através de uma macro dedicada (AVANCA), o registrador de índice sofre um incremento, apontando para o próximo endereço de memória referente ao próximo item do vetor.

**Lógica de acumulação:**  
O programa utiliza um registrador principal que atua como acumulador. A cada repetição do loop, o item atual do vetor é lido da memória e somado diretamente a este registrador através de uma macro dedicada (ACUMULA). Dessa forma, o valor total é construído progressivamente a cada ciclo, sem a necessidade de utilizar registradores intermediários.

**Forma como o laço é controlado:**  
O controle da repetição é gerenciado por um registrador que tem a função de atuar como contador. Antes do loop iniciar, esse registrador é carregado com o valor correspondente ao tamanho total do vetor. Ao final de cada iteração, através de uma macro dedicada (DECREMENTA), esse contador sofre um decremento. A estrutura de repetição sempre verifica esse contador e continua a execução, retornando ao inicio do loop, somente se o valor for diferente de zero.

**Forma como o resultado é armazenado:**  
O programa principal atua como um gerenciador de todo o processo, chamando as macros sequencialmente dentro da estrutura de repetição. Assim que o loop termina, o registrador principal contém o valor total da soma. O programa acessa uma variável responsável pelo resultado, alocada na memória de dados. O valor contido neste registrador é transferido e escrito neste endereço de memória, atualizando o valor diretamente na memória de dados.


## Uso dos registradores e da memória:

### Registradores:

| Registrador | Função                                                                                                                                                                                                          |
| ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SI          | Atua como ponteiro de leitura. Tem a função de armazenar o endereço de memória do elemento atual do vetor. É incrementado a cada iteração através da macro AVANCA.                                              |
| DI          | Atua como ponteiro auxiliar. Inicialmente, é definido com o endereço de memória da variável de tamanho. Ao final, é definido com o endereço de memória da variável de resultado para gravar o valor na memória. |
| CL          | Responsável por controlar o número de repetições do programa. É inicializado com o valor do tamanho do vetor e decrementado a cada iteração através da macro DECREMENTA.                                        |
| AL          | Atua como acumulador. É inicializado em zero e guarda o valor total da soma. A cada repetição do loop, recebe a adição do número atual do vetor através da macro ACUMULA.                                       |

### Memória:

A memória foi estruturada de forma sequencial para armazenar os seguintes itens:

| Variável | Função<br>                                                                            |
| -------- | ------------------------------------------------------------------------------------- |
| VETOR    | Bloco de 4 bytes. Armazena o vetor com os 4 itens.                                    |
| TAM      | Bloco de 1 byte. Armazena o tamanho total do vetor.                                   |
| SOMA     | Bloco de 1 byte. Armazena a saída final do programa. Guardando o valor total da soma. |


### Código:

```assembly
; -------- dados --------
VETOR:
    DB 10
    DB 20
    DB 30
    DB 40
TAM:
    DB 4      ; quantidade de elementos no vetor
SOMA:
    DB 0      ; variável para guardar o resultado final

; -------- macro --------
; soma o valor atual da memória (apontado por SI) no registrador AL
MACRO SOMA_VETOR (_)
-> ADD AL, byte [SI] <-

; -------- código principal --------
start:
    ; SI -> aponta para o início do vetor
    MOV SI, OFFSET VETOR

    ; carrega o tamanho do vetor em CL para controlar o laço
    MOV DI, OFFSET TAM
    MOV CL, byte [DI]

    ; zera o acumulador AL antes de começar a somar
    MOV AL, 0

LOOP_SOMA:
    ; chama a macro: acumula o elemento atual do vetor em AL
    SOMA_VETOR (_)      ; AL = AL + byte [SI]

    ; avança o ponteiro para o próximo elemento
    INC SI

    ; decrementa o contador do laço
    DEC CL

    ; se CL ainda não for zero, volta para LOOP_SOMA
    JNZ LOOP_SOMA

    ; fim do laço: guarda o valor total de AL na variável SOMA
    MOV DI, OFFSET SOMA
    MOV byte [DI], AL

    ; para a execução do processador
    HLT
```

## Resultado final

Com a finalização do programa, o estado final da memória tem a seguinte organização:

| Endereço      | Variável | Valor       |
| ------------- | -------- | ----------- |
| 00000 - 00003 | VETOR    | 0A 14 1E 28 |
| 00004         | TAM      | 04          |
| 00005         | SOMA     | 0x64        |

**Estrutura na memória:** 
0a 14 1e 28 04 64 00 00 00 00 00 00 00 00 00 00

O estado final da variável SOMA é 0x64 (100 em decimal), isso significa que o algoritmo percorreu os quatro elementos do vetor (10, 20, 30 e 40) e acumulou suas somas progressivamente no registrador AL. Comprovando que a soma total dos elementos é 100.