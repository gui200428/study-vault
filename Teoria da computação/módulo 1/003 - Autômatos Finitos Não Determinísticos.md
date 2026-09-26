
## Exemplo:

![[Pasted image 20260926163804.png]]

Neste exemplo, o estado **q0** possui mais de uma possibilidade de transição.

**Ao ler o símbolo `1`, o autômato pode:**
- permanecer em **q0**;
- ir para **q1**.

Isso é o que torna o autômato **não determinístico**.

**No AFD, para cada:**

`estado + símbolo` ← existe **apenas um próximo estado**.

Já no AFND, podem existir **vários próximos estados possíveis** para a mesma entrada.

**Exemplo:**

`q0 + 1 → q0 ou q1`

Como `q2` é um estado final, uma cadeia será aceita se **pelo menos um dos caminhos possíveis** terminar em `q2`.


AFND = uma mesma entrada pode levar o autômato por **mais de um caminho possível**.

### Acompanhando os estados no AFN

Em um **AFN**, como podem existir vários caminhos possíveis, é preciso acompanhar **todos os estados atuais ao mesmo tempo**.

**A cada símbolo lido:**
- é analisado todos os estados em que o autômato pode estar;
- é calculado todas as transições possíveis;
- o conjunto resultante vira o novo conjunto de estados atuais.

Se **pelo menos um dos caminhos** terminar em um estado de aceitação, a cadeia é aceita.
![[Pasted image 20260926164306.png]]


![[Pasted image 20260926164441.png]]

**Primeira leitura:**
Ao ler o primeiro símbolo `1`, existem **duas transições possíveis**:

- `q0 → q0`
- `q0 → q1`
Portanto, após ler o primeiro `1`, o AFND pode estar em:
`{q0, q1}`

![[Pasted image 20260926164600.png]]

**Segunda leitura:**
Após o primeiro `1`, o autômato estava em:
`{q0, q1}`

Agora ele lê o segundo `1`.
**A partir de `q0`:**
- `q0 → q0`
- `q0 → q1`

**A partir de `q1`:**
- não existe transição com `1`
- Caminho é **descartado**.

Portanto, após a segunda leitura, o conjunto de estados continua sendo:
`{q0, q1}`

**Importante:** no AFND, quando um caminho não possui transição para o símbolo lido, ele simplesmente deixa de ser considerado.

![[Pasted image 20260926164845.png]]

**Terceira leitura:**

Antes de ler o último símbolo, o autômato estava em:
`{q0, q1}`

Agora ele lê `0`.

**A partir de `q0`:**
- existe transição com `0` para `q0`

**A partir de `q1`:**
- existe transição com `0` para `q2`

**Portanto, após ler toda a cadeia, o AFND pode estar em:**
`{q0, q2}`

Como `q2` é um **estado de aceitação**, a cadeia `110` é **aceita**.

**Ideia principal:** no AFND, basta que **um dos caminhos possíveis** termine em um estado final para a cadeia ser aceita.

**RESUMINDO:**

**Autômato aceita a entrada:** processar o último símbolo e ele estiver em um dos estados de aceitação.

**Autômato rejeita a entrada:** processar o último símbolo e ele não estiver em um dos estados de aceitação.


## Definição formal de um AFND:

Assim como o AFD, um **Autômato Finito Não Determinístico** também é definido por uma **5-tupla**:

`A = (Q, Σ, δ, S₀, F)`

- **Q**: conjunto finito de estados;
- **Σ**: alfabeto de entrada;
- **δ**: função de transição;
- **S₀**: estado inicial;
- **F**: conjunto de estados finais ou de aceitação.

### Função de transição no AFND:

A principal diferença para o AFD está na função `δ`.

### $$δ: Q × Σ → 2^Q$$
Isso significa que, para um **estado atual + símbolo de entrada**, o resultado pode ser um **conjunto de estados possíveis**.

**Exemplo:**
`δ(q0, 1) = {q0, q1}`

> estando em `q0` e lendo `1`, o autômato pode ir para `q0` **ou** para `q1`.

Também pode acontecer de não existir nenhuma transição:

`δ(q1, 1) = ∅`


### AFD × AFND
- **AFD:** `δ(q0,1) = q1` → um único próximo estado.
- **AFND:** `δ(q0,1) = {q0,q1}` → podem existir vários próximos estados.

**Importante:** `2^Q` representa o conjunto de **todos os subconjuntos possíveis de Q**, porque a função pode retornar zero, um ou vários estados.

![[Pasted image 20260926170051.png]]