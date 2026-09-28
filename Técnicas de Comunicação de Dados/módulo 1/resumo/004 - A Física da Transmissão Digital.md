A aula liga **pulsos elétricos** dos circuitos a **ondas transmissíveis pelo ar a longas distâncias**. O caminho é analisar o conteúdo em frequência do sinal, usar uma **portadora** para a transmissão sem fio e entender por que taxas maiores exigem mais **largura de banda**.

## Dos bits ao espectro de frequências

Dentro da máquina, os bits podem aparecer como **níveis de tensão**: o exemplo do slide usa **+1 V para `1`** e **−1 V para `0`**. São pulsos descritos no **domínio do tempo**, isto é, pela variação do sinal ao longo do tempo. Para transmiti-los pelo ar, a aula contrasta esses níveis diretos com **ondas oscilantes contínuas**.

A **Transformada Rápida de Fourier (FFT)** funciona como um “prisma matemático”: recebe o sinal no domínio do tempo e mostra, no **domínio da frequência**, quais frequências o compõem e como sua energia está distribuída. No desenho: **1. entrada temporal → 2. FFT → 3. saída em frequência**. A FFT é uma forma de **analisar** o sinal; a **modulação** é o processo usado adiante para prepará-lo para o rádio.

![[Pasted image 20260927223623.png]]

## Banda-base e limite da transmissão direta pelo ar

O **NRZ** é o sinal bruto em **banda-base**: níveis lógicos `0` e `1`, sem portadora senoidal de alta frequência. O slide o descreve como uma variação lenta, sem oscilação autônoma, e desenha as variações no tempo e, abaixo, um espectro com pico junto de **0 Hz**. Afirma que **“toda a energia”** fica em 0 Hz, associando esse ponto à **corrente contínua**.

![[Pasted image 20260927223624.png]]

O material considera o NRZ adequado aos **circuitos internos de uma placa-mãe**, mas impraticável para comunicação sem fio direta. Para uma onda de frequência **nula ou extremamente baixa** se propagar eficientemente pelo ar, ele fala em antenas **quilométricas/continentais**. Por isso, o problema da aula é levar os dados a frequências adequadas a antenas portáteis.

Obs: o próprio gráfico temporal mostra transições entre níveis. Portanto, o NRZ do exemplo não contém **somente** 0 Hz; o desenho enfatiza a concentração nas frequências baixas. **0 Hz exato** representa a componente contínua, enquanto o exemplo de antenas enormes se refere às frequências muito baixas.

## Modulação: dados sobre uma portadora

A **modulação** usa uma **onda senoidal portadora de alta frequência** para transportar a informação da onda quadrada. O slide compara duas maneiras de representar os bits:

| Técnica | O que muda na portadora | Representação do slide |
| --- | --- | --- |
| **ASK** | **Amplitude**. | Onda presente/grande para `1`; linha reta para `0`. |
| **BPSK** | **Fase**. | A onda continua, mas inverte a fase quando a informação do desenho passa de `0` para `1`. |

![[Pasted image 20260927223625.png]]

Na comparação pela **FFT**, os **dados brutos NRZ** aparecem com pico próximo de **0 Hz** e o slide diz que “ficam presos no cabo elétrico”. O sinal **modulado (ASK/BPSK)** aparece com o pico deslocado para uma frequência de portadora, **100 MHz** no exemplo, deixando o marco **0 Hz** vazio no esquema. Assim, o material associa a modulação à transmissão pelo ar com **antenas portáteis**. Os picos isolados do desenho são uma representação esquemática da mudança de faixa.

![[Pasted image 20260927223626.png]]

## Taxa de bits, duração do pulso e largura de banda

Aumentar a **taxa de bits** (bits/s) significa colocar mais dados no **mesmo intervalo de tempo**. No **cenário A** do slide, há poucas transições longas; no **cenário B**, muitas transições curtas e abruptas. Ao comprimir pulsos no tempo, o sinal passa a exigir **componentes de frequência mais altas** e o espectro se **alarga** (largura de banda espectral em Hz).

O gráfico seguinte compara **conexão lenta**, com espectro estreito e concentrado nas baixas frequências, e **conexão rápida**, com energia espalhada por uma faixa maior. É a relação central da aula: **pulsos mais curtos no tempo → espectro mais largo em frequência → maior largura de banda exigida**.

![[Pasted image 20260927223627.png]]

**Complemento de cálculo:** a duração disponível por bit pode ser estimada por $T_b=1/R_b$, com $T_b$ em segundos e $R_b$ em bits/s. Assim, **1 Mbps** dá **1 µs/bit**, enquanto **10 Mbps** dá **0,1 µs/bit**. Isso mostra a compressão temporal; o PDF não fornece uma fórmula para calcular a largura de banda exata a partir de $R_b$.

### A analogia da mangueira

O slide compara o **espectro eletromagnético** a uma **mangueira** e os dados a uma **válvula**. Em baixa velocidade, a válvula abre e fecha lentamente: os “pacotes de água” fluem intactos e uma **tubulação estreita** (pouca largura de banda) basta. Em velocidade alta, a operação rápida numa tubulação fina produz, na figura, **resistência extrema** e **informação destruída/misturada**; uma tubulação mais larga representa a **vasta largura de banda** e o **“fluxo perfeito”**.

Obs: essa é uma analogia do slide para a limitação de faixa de frequências; resistência hidráulica não é o mecanismo físico que altera um sinal elétrico ou de rádio.

## As três regras apresentadas no fechamento

1. **Limite da banda-base:** o slide situa a energia do NRZ em 0 Hz. Esses sinais são apresentados como ágeis para **curtas distâncias dentro do hardware**, mas **fisicamente incapazes de propagação atmosférica direta**.
2. **Modulação:** ASK e BPSK transferem a energia do **marco zero para frequências carreadoras elevadas**, permitindo a comunicação sem fio.
3. **“Lei de Shannon-Nyquist”:** o material usa esse nome para resumir a relação inversa entre **tempo e frequência** e a necessidade de **mais espectro** ao elevar a taxa de transmissão.
