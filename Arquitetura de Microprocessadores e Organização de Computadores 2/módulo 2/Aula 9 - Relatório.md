
**Eng de computação - Guilherme Augusto - 05223-071.**

## Objetivo:

O objetivo principal do programa é percorrer um vetor de bytes armazenado na memória, identificar quais elementos são pares, empilhá-los na pilha durante a varredura e, após percorrer todo o vetor, desempilhar esses valores acumulando sua soma, armazenando o resultado final na variável SOMA na memória.


## Descrição da implementação:

**Forma como o vetor é percorrido:** 
O registrador de índice SI atua como um ponteiro de memória, sendo responsável por apontar onde cada item do vetor está localizado. Ele é iniciado com o endereço base do primeiro elemento do vetor. A cada repetição do loop, o registrador SI sofre um incremento, apontando para o próximo endereço de memória referente ao próximo item do vetor. O registrador CL controla quantas iterações restam, sendo decrementado a cada passagem até zerar, encerrando a varredura.

**Forma como o laço é controlado:** 
O controle da repetição é gerenciado pelo registrador CL, que tem a função de atuar como contador. Antes do loop iniciar, esse registrador é carregado com o valor correspondente ao tamanho total do vetor, lido diretamente da variável TAM na memória. Ao final de cada iteração, esse contador sofre um decremento. A estrutura de repetição sempre verifica esse contador e continua a execução, retornando ao início do loop, somente se o valor for diferente de zero.

**Forma como o resultado é armazenado:** 
Dentro do loop de varredura, cada elemento atual é carregado e testado quanto à sua paridade por meio da instrução TEST. É utilizada uma lógica de salto condicional: se o valor for ímpar, o programa salta a etapa de empilhamento. Se o valor for par, ele é empilhado na pilha e o registrador CH é incrementado para registrar a quantidade de valores pares encontrados. Após o encerramento da varredura, um segundo loop desempilha cada valor acumulado, somando-os progressivamente no registrador AL. Ao final, o programa acessa a variável SOMA, alocada na memória de dados, e o valor acumulado em AL é escrito neste endereço, atualizando o resultado diretamente na memória de dados.

## Uso dos registradores e da memória:

### Registradores:

| Registrador | Função                                                                                                                                                                                                                          |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SI          | Atua como ponteiro de leitura. Tem a função de armazenar o endereço de memória do elemento atual do vetor. É incrementado a cada iteração do loop de varredura.                                                                 |
| DI          | Após o encerramento do loop de desempilhamento, é definido com o endereço de memória da variável SOMA. Possibilita o acesso à memória para escrever o resultado final.                                                          |
| CL          | Responsável por controlar o número de repetições do programa. É inicializado com o valor do tamanho do vetor e decrementado a cada iteração. No segundo loop, é recarregado com o valor de CH para controlar o desempilhamento. |
| CH          | Atua como contador de valores pares encontrados durante a varredura. É incrementado a cada vez que um elemento par é empilhado, e ao final é transferido para CL para controlar o loop de desempilhamento.                      |
| AL          | Utilizado para carregar o número atual do vetor para teste de paridade e para acumular progressivamente a soma dos valores pares desempilhados, sendo escrito em SOMA ao final.                                                 |
| BX          | Utilizado para receber temporariamente cada valor desempilhado da pilha. O byte baixo BL é somado ao acumulador AL a cada iteração do loop de desempilhamento.                                                                  |

### Memória:

A memória foi estruturada de forma sequencial para armazenar os seguintes itens:

| Variável | Função                                                                                                                             |
| -------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| VETOR    | Bloco de 8 bytes. Armazena o vetor com os 8 itens a serem processados pelo programa.                                               |
| TAM      | Bloco de 1 byte. Armazena o tamanho total do vetor, utilizado para inicializar o contador de iterações.                            |
| SOMA     | Bloco de 1 byte. Armazena a saída final do programa, guardando o resultado da soma de todos os valores pares encontrados no vetor. |

### Código:

```
; -------- dados --------
VETOR:
DB 1
DB 2
DB 3
DB 4
DB 5
DB 6
DB 8
DB 7
TAM:
DB 8
SOMA:
DB 0

; -------- código --------
start:
    ; SI -> início do vetor
    MOV SI, OFFSET VETOR
    ; CL = tamanho do vetor
    MOV DI, OFFSET TAM
    MOV CL, byte [DI]
    ; CH = contador de pares empilhados
    MOV CH, 0

EMPILHA:
    ; carrega elemento atual em AL
    MOV AL, byte [SI]
    MOV AH, 0
    ; testa bit 0: impar -> bit 0 = 1, par -> bit 0 = 0
    TEST AL, 1
    ; se impar, pula o empilhamento
    JNZ IMPAR
    ; empilha o valor par
    PUSH AX
    ; conta mais um par
    INC CH
IMPAR:
    ; avança para o próximo elemento
    INC SI
    DEC CL
    JNZ EMPILHA

    ; CL = quantidade de valores pares a desempilhar
    MOV CL, CH
    ; AL = acumulador da soma
    MOV AL, 0
    ; se nenhum par foi encontrado encerra
    CMP CL, 0
    JZ FIM

DESEMPILHA:
    ; retira valor da pilha para BX
    POP BX
    ; acumula em AL
    ADD AL, BL
    DEC CL
    JNZ DESEMPILHA

FIM:
    ; DI -> endereço de SOMA
    MOV DI, OFFSET SOMA
    ; grava resultado na memória
    MOV byte [DI], AL
    HLT
```


## Resultado final

Com a finalização do programa, o estado final da memória tem a seguinte organização:

| Endereço      | Variável | Valor                   |
| ------------- | -------- | ----------------------- |
| 00000 - 00007 | VETOR    | 01 02 03 04 05 06 08 07 |
| 00008         | TAM      | 08                      |
| 00009         | SOMA     | 14                      |

**Estrutura na memória:**
01 02 03 04 05 06 08 07 08 14 00 00 00 00 00 00

O estado final da variável SOMA é 0x14, que corresponde ao valor decimal 20. Isso significa que o algoritmo percorreu os 8 elementos do vetor, identificou os valores pares (2, 4, 6 e 8), empilhou-os, desempilhou-os e acumulou sua soma. Comprovando que a soma de todos os valores pares presentes no vetor é igual a 20.