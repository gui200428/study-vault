## Linguagem

### Alfabeto (Σ): 
É um conjunto **finito e não vazio de símbolos** que podem ser usados para formar cadeias.

Exemplos:

- Σ = {0,1}
- Σ = {a,b,c}
- Σ = {α,β,γ,δ,ε}
- Σ = {0,1,...,9,a,b,...,z,A,B,...,Z}


### Cadeia:
Também chamada de **palavra** ou **string**, é uma sequência **finita de símbolos pertencentes a um alfabeto**.

**Exemplo:**  
Para Σ = {0,1}, algumas cadeias possíveis são:

`0`, `00`, `000`, `0000`, `01`, `0100`

**Importante:** uma cadeia só pode usar símbolos que pertencem ao alfabeto definido.

### Comprimento:
**Comprimento de uma cadeia:** é a **quantidade de símbolos** que ela possui. É representado por barras verticais `| |`.

**Exemplos:**
- `|abb| = 3`
- `|aaaa| = 4`

Também existe a **cadeia vazia**, representada por **ε**, que não possui nenhum símbolo.

Logo:

`|ε| = 0`


### Concatenação de cadeias:
Duas cadeias podem ser **juntadas**, formando uma nova cadeia.

**Exemplo:**  
Se `x = auto` e `y = peças`:

`xy = autopeças`

O comprimento da cadeia concatenada é a soma dos comprimentos:

`|xy| = |x| + |y| = 4 + 5 = 9`

Uma cadeia também pode ser concatenada com ela mesma:

- `xx = x²`
- `xxx = x³`

Concatenar uma cadeia com a **cadeia vazia ε** não altera seu conteúdo:

`xε = x`


### Potência de um alfabeto:
**Potência de um alfabeto:** representa o conjunto de **todas as cadeias possíveis com um determinado comprimento**.


**É representada por:**

### $$Σⁿ$$

onde `n` indica o **comprimento das cadeias**.

Exemplo, para `Σ = {0,1}`:

- `Σ¹ = {0,1}`
- `Σ² = {00,01,10,11}`
- `Σ³ = {000,001,010,011,100,101,110,111}`

**Importante:** `Σ` e `Σ¹` não são exatamente a mesma coisa conceitualmente.

- `Σ` é um conjunto de **símbolos**.
- `Σ¹` é um conjunto de **cadeias de comprimento 1**.

Mesmo que apareçam com os mesmos elementos, representam ideias diferentes.