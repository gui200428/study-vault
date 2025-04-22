```c
#include<stdio.h>
#include<stdbool.h>
#include<stdlib.h>

typedef int telemento;

typedef struct no{
        int dado;
        struct no * prox;
}tno;

typedef tno * tpilha;

void criar(tpilha * pp){
     *pp = NULL;
}

bool push(tpilha *pp, telemento valor){
     tpilha novo;
     novo = (tno*) malloc(sizeof(tno));
     if(novo == NULL)
       return false;
     else{
          novo->dado = valor;
          novo->prox = *pp;
          *pp = novo;
          return true;    
     }     
}

void imprimir(tpilha *pp){
     tpilha aux;
     aux = *pp;
     while(aux != NULL){
           printf("Pilha[%d] \n", aux->dado);
           aux = aux->prox;              
     }     
}

bool pop(tpilha *pp, telemento * valor){
     tpilha aux;
     if(*pp == NULL)
        return false;
     else{
          aux = *pp;
          *valor = (*pp)->dado;
          *pp = aux->prox; //*pp = (*pp)->prox;
          free(aux);
          return true;     
     }     
}

void main(){
     
     tpilha p;
     tpilha aux;

     telemento op, valor = 0, pegaValor = 0; //telemento é um novo tipo definido para inteiros
     
     criar(&p);
     criar(&aux);
     
     do{
        printf("Entre com 1-Empilhar, 2-Imprimir,3-Pilha Reversa, 4-Desempilhar ou (-1 Sair): ");
        scanf("%d", &op);
        switch(op){
                   case 1: do{
                              printf("Entre com o valor ou (-1 para sair): ");
                              scanf("%d",&valor);
                              if(valor==-1)
                                printf("Saindo...\n");
                              else{
                                   if(push(&p, valor)){
                                      printf("Pilha[%d] \n", p->dado);         
                                   }     
                                   else{
                                        printf("Nao foi possivel alocar memoria! \n");
                                        valor= -1;     
                                   }
                              }                                                                
                           }while(valor!=-1);          
                           break;
                   case 2: printf("Pilha Original: \n");
                           imprimir(&p);
                           printf("Pilha Auxiliar: \n");
                           imprimir(&aux);
                           break;
                    case 3: do{
                              printf("Entre com 1 para desempilhar ou (-1 para sair): ");
                              scanf("%d",&valor);
                              if(valor == -1){
                                 printf("Saindo...\n");                                                
                              }
                              else{
                                   if(valor == 1){
                                      if(pop(&p, &pegaValor)){
                                         printf("Retirado Elemento do topo da pilha: %d \n", pegaValor);        
                                         if(push(&aux, pegaValor)){
                                             printf("Inserido o %d valor na pilha aux! \n", pegaValor);
                                         }
                                         else{
                                             printf("Erro! \n");
                                         }
                                      }
                                      else{
                                           printf("\nPilha Vazia! \n");
                                      }         
                                   }   
                                   else{
                                        printf("Valor Invalido! \n");
                                   }                       
                              }                        
                           }while(valor!=-1);   
                                 break;
                   case 4: do{
                              printf("Entre com 1 para desempilhar ou (-1 para sair): ");
                              scanf("%d",&valor);
                              if(valor == -1){
                                 printf("Saindo...\n");                                                
                              }
                              else{
                                   if(valor == 1){
                                      if(pop(&p, &pegaValor)){
                                         printf("Retirado Elemento do topo da pilha: %d \n", pegaValor);        
                                      }
                                      else{
                                           printf("\nPilha Vazia! \n");
                                      }         
                                   }   
                                   else{
                                        printf("Valor Invalido! \n");
                                   }                       
                              }                        
                           }while(valor!=-1);   
						   break;                
        }               
     }while(op!=-1);
               
     system("PAUSE");     
}
```
