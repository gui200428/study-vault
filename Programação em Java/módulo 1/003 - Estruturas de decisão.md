#faculdade #resumos #java 
## If/ else

**Formas de representar o if/else**

Linear:

```java
if(condicao) System.out.println("Executa a linha");
else System.out.println("Executa esta outra linha");
```


Estruturada:

```java
if(condicao){
	System.out.println("Executa a linha");
} else {
	System.out.println("Executa esta outra linha");
}
```


Else com condição:

```java
if(condicao){
	System.out.println("Executa a linha");
} else if(condicao2){
	System.out.println("Executa esta outra linha");
} else {
	System.out.println("Executa esta outra linha");
}
```


## Operadores:


```java
== <- Igualdade de variaveis primitivas

!= <- Diferença de variaveis primitivas

equals <- Compara valores de objetos

< <- menor que
<= <- menor ou igual
> <- maior que
>= <- maior ou igual
```


# Operadores Lógicos

|Operador|Nome|Avaliação|Descrição da Diferença|
|:-:|:--|:-:|:--|
|`&&`|**E Lógico (AND)**|Curto-circuito (Short-circuit)|Avalia a segunda condição **somente se** a primeira for `true`. Mais eficiente e seguro.|
|`&`|E Lógico e Bitwise (AND)|Completa|**Sempre avalia ambas** as condições, independente do resultado da primeira. Menos comum.|
|`\|`|**OU Lógico (OR)**|Curto-circuito (Short-circuit)|Avalia a segunda condição **somente se** a primeira for `false`. Mais utilizado para operação "OU".|
|`\|`|OU Lógico e Bitwise (OR)|Completa|**Sempre avalia ambas** as condições, independente do resultado da primeira.|
|`^`|**OU Exclusivo (XOR)**|Completa|Retorna `true` apenas se as condições forem **diferentes** (uma `true`, outra `false`).|
|`!`|**NÃO Lógico (NOT)**|-|Inverte o valor booleano: `true` → `false` e `false` → `true`.|

---

## Observações

- **Curto-circuito**: Mais eficiente pois pode parar a avaliação antecipadamente
- **Completa**: Sempre avalia todas as condições, independente do resultado
- **XOR**: Útil quando você precisa que apenas uma condição seja verdadeira


---
### Próximo conteúdo:

[[004 - Estruturas de decisão]]
