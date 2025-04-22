
```c
#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>

typedef int telemento;

typedef struct no
{
    int dado;
    struct no *prox;
} tno;

typedef tno *tpilha;

void criar(tpilha *pp)
{
    *pp = NULL;
}

bool push(tpilha *pp, telemento valor)
{
    tpilha novo;
    novo = (tno *)malloc(sizeof(tno));
    if (novo == NULL)
        return false;
    else
    {
        novo->dado = valor;
        novo->prox = *pp;
        *pp = novo;
        return true;
    }
}

bool pop(tpilha *pp, telemento *valor)
{
    tpilha aux;
    if (*pp == NULL)
        return false;
    else
    {
        aux = *pp;
        *valor = (*pp)->dado;
        *pp = aux->prox;
        free(aux);
        return true;
    }
}

void imprimir(tpilha *pp)
{
    tpilha aux;
    aux = *pp;
    while (aux != NULL)
    {
        printf("Pilha[%d] \n", aux->dado);
        aux = aux->prox;
    }
}

int main()
{
    char input[500];      // armazena o input do usuario
    char inputLimpo[500]; // input tratado, sem espaços ou caracteres especiais.
    int i, j = 0;
    tpilha pilha;
    telemento valorPilha;

    // pega o input do usuario
    printf("Digite um texto:\n> ");
    scanf("%[^\n]", input);

    // tratamento do input, apenas letras minusculas e numeros.
    int len = strlen(input);
    for (i = 0; i < len; i++)
    {
        if (isalnum((unsigned char)input[i]))
        {
            inputLimpo[j++] = tolower((unsigned char)input[i]);
        }
    }
    inputLimpo[j] = '\0';

    // cria a pilha
    criar(&pilha);

    // Empilhamento do input limpo
    for (i = 0; i < j; i++)
    {
        if (!push(&pilha, inputLimpo[i]))
        {
            printf("Erro ao empilhar o caractere %c\n", inputLimpo[i]);
            return 1;
        }
    }

    // Print da pilha
    imprimir(&pilha);

    // verificação do palíndromo // desempilhando e comparando cada caractere com o do input limpo (em ordem inversa)
    bool palindromo = true;
    for (i = 0; i < j; i++)
    {
        if (!pop(&pilha, &valorPilha))
        {
            printf("Erro ao desempilhar\n");
            return 1;
        }
        if (inputLimpo[i] != valorPilha)
        {
            palindromo = false;
            break;
        }
    }

    // resultado
    if (palindromo)
        printf("O texto: [%s] eh um palindromo.\n", input);
    else
        printf("O texto: [%s] nao eh um palindromo.\n", input);

    return 0;
}
```