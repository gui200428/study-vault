
## Problema:

#### Lista com 20 mil pessoas:
- Como encontrar um valor?

## Solução:

### Tabela hash!

- Acesso rápido e direto aos dados
- Remove a necessidade da busca sequencial


## Tabela hash:

**Definição:** é uma estrutura de dados que guarda informações de forma que a busca seja muito rápida.

#### Conceito de chave:valor

**Chave:** identifica unicamente o dado. (Assim como um CPF identifica uma pessoa.)
**Valor:** informação a ser guardada. (Qualquer tipo de dado.)

```java
Chave: "Maria"
Valor: Nota = 10

Chave: "João"
Valor: Nota = 8
```

### Analogia do armário

**Armário:** Um armário com gavetas numeradas de 0 a N-1
**Gaveta:** Cada informação vai para uma gaveta especifica.

**Tabela hash vai direto para o índice.**

## Estrutura real:

A tabela hash é um **array** em que cada posição é chamada de **bucket!**


```json
{
  "0": ["dados_A1", "dados_A2"],
  "1": ["dados_B1"],
  "2": [],
  "3": ["dados_D1", "dados_D2", "dados_D3"],
  "4": ["dados_E1"]
}
```


### Funcionamento:

**Salvar um dado:**
1. **input da chave:** o dado é passada para a tabela hash
2. **função hash:** processa o dado e gera um número
3. **cálculo do índice:** indice = hash(chave)% tamanho
4. **armazenamento:** o dado é guardado na posição calculada.

**Buscar um dado:**
- A busca segue a mesma lógica, calcula o índice e vai direto para a posição.

