## Características gerais

A aula apresenta ideias que acompanharam a evolução da organização dos computadores:

- **Conceito de família:** introduzido pela IBM com o **System/360 (1964)** e seguido pela DEC com o **PDP-8**. Separa a arquitetura da implementação: computadores de uma família mostram a mesma arquitetura ao usuário, mas têm preços e desempenhos diferentes devido às implementações.
- **Unidade de controle microprogramada:** sugerida por **Wilkes (1951)** e introduzida pela IBM na linha **S/360 (1964)**. A microprogramação facilita o projeto e a implementação da unidade de controle e dá suporte ao conceito de família.
- **Memória cache:** introduzida comercialmente no **IBM S/360 Model 85 (1968)**. Sua inclusão na hierarquia de memória melhora consideravelmente o desempenho.
- **Pipeline:** introduz paralelismo na execução de programas de instruções de máquina, que são essencialmente sequenciais. A aula cita o pipeline de instruções e o processamento vetorial como exemplos.
- **Múltiplos processadores:** categoria que abrange diferentes organizações e objetivos.
- **RISC (*Reduced Instruction Set Computer*):** arquitetura com conjunto reduzido de instruções, foco desta aula.

### O que é pipeline?

O pipeline divide a execução de uma instrução em etapas sequenciais. É como a linha de montagem citada na aula: enquanto uma peça é pintada, outra é montada e outra inspecionada. Da mesma forma, instruções diferentes podem ocupar etapas diferentes ao mesmo tempo.

Isso traz três vantagens apresentadas:

- **aumento de desempenho:** várias instruções são processadas simultaneamente;
- **melhor aproveitamento do processador:** reduz o tempo ocioso;
- **execução mais rápida do conjunto:** depois que o pipeline está cheio, uma instrução pode ser concluída a cada ciclo de clock.

### Elementos compartilhados pelos projetos RISC

Os projetos RISC variam, mas a maioria compartilha:

- muitos registradores de propósito geral **e/ou** técnicas de compilador para otimizar seu uso;
- conjunto de instruções simples e limitado;
- ênfase na otimização do pipeline de instruções.

## Execução de instruções em arquiteturas RISC

A aula associa a execução RISC a simplicidade, rapidez, eficiência, desempenho e previsibilidade. As características listadas são:

1. **Instruções de tamanho fixo:** geralmente **32 bits**. O processador sabe onde cada instrução começa e termina, facilitando a decodificação, o controle e o pipeline.
2. **Baixa complexidade das instruções.**
3. **Separação entre operações de memória e processamento:** instruções de carga (*load*) e armazenamento (*store*) ficam separadas das aritméticas e lógicas. Assim, cada estágio do pipeline tem uma função definida.
4. **Uso intensivo de registradores:** a maioria das operações ocorre entre registradores, reduzindo acessos à memória, que é mais lenta. Isso exige um conjunto grande e bem organizado de registradores.
5. **Pipeline profundo e eficiente:** a execução é dividida em vários estágios, como IF, ID, EX, MEM e WB, permitindo instruções diferentes em estágios diferentes ao mesmo tempo.
6. **Baixa latência por instrução:** as instruções simples e rápidas reduzem o tempo de execução; com o pipeline cheio, pode-se concluir uma instrução por ciclo de clock.
7. **Previsibilidade e facilidade de otimização:** a simplicidade facilita o trabalho dos compiladores; o comportamento mais previsível melhora o desempenho em tempo real.
8. **Redução de ciclos por instrução (CPI, *Cycles Per Instruction*):** o CPI tende a ser baixo devido à simplicidade das instruções e à eficiência do pipeline, contribuindo para um alto *throughput* de instruções.

## Operações, operandos e sequência de execução

### Operações efetuadas

As instruções realizam operações básicas e bem definidas:

- **aritméticas:** `ADD`, `SUB`, `MUL`, `DIV`;
- **lógicas:** `AND`, `OR`, `XOR`, `NOT`;
- **comparações:** `SLT` (*Set Less Than*) e `BEQ` (*Branch if Equal*);
- **transferência de dados:** `LW` (*Load Word*) e `SW` (*Store Word*);
- **controle de fluxo:** `J` (*Jump*), `BEQ` e `BNE`.

O material chama essas operações de **atômicas** por atribuir uma tarefa a cada instrução, o que facilita a implementação e a otimização. Também define operação atômica como **indivisível**: ou ocorre completamente ou não ocorre. Isso garante consistência e previsibilidade, especialmente em sistemas concorrentes ou paralelos.

### Operandos usados

**Operando** é o dado, valor ou referência sobre o qual uma instrução atua. A maioria das instruções trabalha com registradores, em vez de acessar diretamente a memória:

- `ADD x1, x2, x3`: soma os valores de `x2` e `x3` e guarda o resultado em `x1`.
- `LW x1, 0(x2)`: carrega em `x1` o valor da memória no endereço contido em `x2`; o endereço é calculado a partir de um registrador.

O uso de registradores reduz o tempo gasto com acessos à memória e melhora o desempenho.

### Sequência de execução

A sequência apresentada divide uma instrução em cinco estágios:

1. **IF (*Instruction Fetch*):** busca a instrução na memória.
2. **ID (*Instruction Decode*):** decodifica a instrução e identifica os operandos.
3. **EX (*Execute*):** realiza a operação aritmética, lógica ou outra.
4. **MEM (*Memory Access*):** acessa a memória, se necessário.
5. **WB (*Write Back*):** escreve o resultado no registrador de destino.

Cada estágio é apresentado com duração de **um ciclo de clock**. O pipeline permite manter múltiplas instruções em estágios diferentes no mesmo instante.

## Exemplos práticos

### Desvio condicional

O primeiro exemplo coloca **5** em `$t0` e **3** em `$t1`. `BNE` salta para `DIFERENTE` quando os valores não são iguais:

```asm
ADD $t0, $zero, 5
ADD $t1, $zero, 3
BNE $t0, $t1, DIFERENTE
ADD $t2, $t2, $t2
DIFERENTE:
ADD $t3, $t3, $t3
```

Com os valores do slide, o desvio ocorre: a instrução sobre `$t2`, indicada para valores iguais, é pulada, e a instrução sobre `$t3`, indicada para valores diferentes, é alcançada.

**Obs**: se os valores fossem iguais, o fluxo também chegaria à instrução após `DIFERENTE`, pois o exemplo não mostra um salto para contorná-la.

### Multiplicação por somas sucessivas

Para calcular **A × B**, o algoritmo começa com `resultado = 0` e soma **A** ao resultado de **1 até B**. No exemplo, **A = 3**, **B = 4** e o resultado final é **12**.

- `x5` guarda A, o multiplicando;
- `x6` guarda B, o multiplicador;
- `x7` é o contador;
- `x8` guarda o resultado.

```asm
addi x5,x0, 3
addi x6,x0, 4
addi x7,x0, 0
addi x8,x0, 0

loop:
    beq x7, x6, fim
    add x8, x8, x5
    addi x7, x7, 1
    jal x0, loop

fim:
    # x8 contém 12
```

O `beq` verifica se o contador chegou a B; `add` acumula A em `x8`; `addi` avança o contador; e `jal x0, loop` retorna ao começo, apresentado no slide como salto sem *link*.

## Execução em função do clock (pipeline simplificado)

O exemplo usa os cinco estágios **IF, ID, EX, MEM e WB**. No **resumo parcial dos ciclos de clock**, a aula mostra:

| Ciclo | Instrução | Estágio |
| ---: | --- | --- |
| 1 | `ADD $t3, $zero, $zero` | IF |
| 2 | `ADD $t3, $zero, $zero` | ID |
| 3 | `ADD $t3, $zero, $zero` | EX |
| 4 | `ADD $t3, $zero, $zero` | MEM |
| 5 | `ADD $t3, $zero, $zero` | WB |
| 6 | `ADD $t2, $zero, $zero` | IF |
| 10 | `BEQ $t2, $t1, FIM` | IF |
| 11 | `BEQ $t2, $t1, FIM` | ID |

### Estimativa de ciclos de clock

Com **5 estágios**, o material considera que cada instrução leva **5 ciclos** para terminar. Na multiplicação com **B = 4**, conta **4 instruções por iteração** (`BEQ`, `ADD`, `ADDI` e `J`) e **4 iterações**: `4 × 4 = 16` instruções dentro do laço. Somadas às **4 instruções `addi` de inicialização**, são **20 instruções**. `FIM` é um rótulo, não uma instrução.

**Obs**: o slide menciona “1 instrução final”, mas na mesma linha diz que `FIM` é apenas um rótulo. O total apresentado permanece **20 instruções**.

**Sem pipeline:** `20 instruções × 5 ciclos = 100 ciclos de clock`.

### Pipeline cheio paralelismo máximo

Quando o **pipeline está cheio**, ocorre o **paralelismo máximo**: a primeira instrução está em **WB**, a segunda em **MEM**, a terceira em **EX**, a quarta em **ID** e a quinta em **IF**. A primeira termina em **5 ciclos**; cada instrução seguinte termina **um ciclo depois** da anterior. Assim, uma nova instrução pode começar e uma pode terminar a cada ciclo.

**Com pipeline:**

$$
\text{Ciclos totais} = \text{número de instruções} + \text{número de estágios} - 1
$$

Usando os números da contagem da aula: **20 + 5 − 1 = 24 ciclos de clock**.

**Obs**: o slide escreve “para **18 instruções** e 5 estágios”, mas substitui **20** na fórmula e chega a **24 ciclos**, como na contagem do slide anterior.

O quadro final distribui as **20 instruções** pelos **24 ciclos**. Nele, as primeiras cinco instruções ocupam, em sequência, WB, MEM, EX, ID e IF; depois o término passa a ocorrer a cada ciclo.

![[Pasted image 20260927184718.png]]

**Obs**: nesse quadro, o salto aparece como `j x0, loop`, enquanto o código anterior usa `jal x0, loop`. O quadro também termina após o salto da quarta iteração, sem mostrar a nova verificação de `beq` que levaria a `fim`.
