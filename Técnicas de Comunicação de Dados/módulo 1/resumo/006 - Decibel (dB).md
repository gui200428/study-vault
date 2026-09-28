O ouvido humano e as redes de dados lidam com variações de energia de **1 para mais de 1.000.000**. O **decibel (dB)** usa uma escala **logarítmica** para representar proporções grandes com números manejáveis. O slide chama isso de “comprimir” proporções exponenciais em uma **“escala linear e gerenciável”**: uma mudança **multiplicativa** de potência passa a ser descrita por uma mudança **aditiva** em dB.

O material menciona que o nome homenageia **Bell** e que a unidade surgiu para expressar perda de sinal em linhas telefônicas.

## Fórmula para relação de potências

$$
D_{\mathrm{dB}}=10\log_{10}\!\left(\frac{P_1}{P_2}\right)
$$

- $P_1$ e $P_2$: potências comparadas, na **mesma unidade**; a razão $P_1/P_2$ não tem unidade.
- $\log_{10}$: comprime a razão de potências; o fator **10** corresponde ao prefixo **deci** e produz números práticos em **decibéis**.
- **$0$ dB:** $P_1=P_2$. Valor **positivo:** $P_1>P_2$ (ganho em relação a $P_2$). Valor **negativo:** $P_1<P_2$ (perda).

O dB indica uma **proporção entre dois estados**, não uma potência absoluta isolada. Para interpretar o sinal do resultado, é indispensável saber qual potência ficou no numerador e qual ficou no denominador. Em particular, **0 dB não significa 0 W**: significa que a potência comparada é igual à potência de referência.

## Regras práticas de ganho e perda

| Variação mostrada no slide | Razão aproximada entre potências |
| --- | --- |
| **+10 dB** | **10×** |
| **+3 dB** | **2×** (dobro) |
| **0 dB** | **1×** (igual) |
| **−3 dB** | **1/2** (metade) |
| **−10 dB** | **1/10** |

A regra dos **±3 dB** é uma **aproximação**: aumentar 3 dB praticamente dobra a potência; perder 3 dB praticamente a reduz à metade. Mudanças em dB se somam ao longo de etapas sucessivas porque as razões de potência correspondentes se multiplicam.

**Complemento de cálculo:** invertendo a fórmula da aula, $P_1/P_2=10^{D_{\mathrm{dB}}/10}$. Assim, **+3 dB** corresponde a $10^{0{,}3}\approx1{,}995$ e **−3 dB** a $10^{-0{,}3}\approx0{,}501$. O cálculo mostra por que o slide usa “dobro” e “metade” como regras rápidas.

**Exemplo - potência inicial de 10 mW:**

| Variação | Operação aproximada | Potência final |
| --- | --- | --- |
| **+10 dB** | $10\text{ mW}\times10$ | **100 mW** |
| **+3 dB** | $10\text{ mW}\times2$ | **20 mW** |
| **−3 dB** | $10\text{ mW}\div2$ | **5 mW** |
| **−10 dB** | $10\text{ mW}\div10$ | **1 mW** |

**Complemento - etapas sucessivas:** um ganho de **+10 dB** seguido de uma perda de **−3 dB** resulta em **+7 dB**. Pelas regras aproximadas, a potência é multiplicada por $10\times\frac12=5$; de **10 mW**, chega a cerca de **50 mW**. Assim, **somar os dB** equivale a **multiplicar as razões de potência**. O valor exato seria $10\times10^{7/10}\approx50{,}1$ mW.

## Audição humana na escala em dB

O material descreve a audição como **naturalmente logarítmica** e associa a “compressão” da escala à capacidade de lidar com uma faixa sonora grande sem sobrecarga sensorial. Sua régua apresenta:

| Nível | Referência do slide |
| --- | --- |
| **0 dB** | Limiar da audição. |
| **50 dB** | Conversa normal. |
| **120 dB** | Limiar da dor. |

O texto do slide também fala em um **intervalo dinâmico de 1.000.000** entre o que chama de “silêncio absoluto” e o som mais alto suportável.

**Complemento:** em uma escala sonora com referência definida, **0 dB representa o nível de referência, não ausência física de som**. Aqui, a régua do slide usa como referência o **limiar da audição**.

Obs: a régua identifica **0 dB como limiar da audição**, embora o texto também fale em “silêncio absoluto”. Pela fórmula de **razão de potências** da aula, um intervalo de **1.000.000** corresponderia a $10\log_{10}(10^6)=60$ dB; já **120 dB** corresponderiam a uma razão de $10^{120/10}=10^{12}$. Portanto, os **1.000.000** do slide de audição não explicam a faixa de **0 a 120 dB** como uma mesma razão de potências. O material não define outra grandeza para conciliar os dois valores.

**Complemento para interpretar a diferença:** se os **1.000.000** fossem uma **razão de amplitudes**, e a potência fosse proporcional ao quadrado da amplitude, a razão de potências seria $(10^6)^2=10^{12}$, equivalente a **120 dB**. Isso conciliaria os números, mas o PDF não diz que seu intervalo de 1.000.000 seja de amplitudes.

## Atenuação: meio guiado × espaço livre

| Meio | Mecanismo indicado no material | Valor apresentado |
| --- | --- | --- |
| **Guiado (cabo/fibra)** | O sinal perde uma fração de potência a cada trecho de distância; a perda em dB se acumula ao longo do percurso. | Exemplo: **3 dB/km** na fibra óptica. |
| **Espaço livre** | A energia se espalha **radialmente**; o slide cita a **Lei do Inverso do Quadrado**. | A potência recebida cai cerca de **6 dB** quando a distância **dobra**. |

![[Pasted image 20260927225247.png]]

**Complemento de cálculo:** **3 dB/km** significa mais **3 dB de perda a cada quilômetro**: cada quilômetro seguinte deixa aproximadamente **metade da potência que chegou até ele**. Após **2 km**, a perda acumulada seria **6 dB**, restando aproximadamente **1/4** da potência inicial. No espaço livre ideal, dobrar a distância espalha a energia por uma área **4 vezes maior** e reduz a potência recebida a $1/2^2=1/4$; em decibéis, $10\log_{10}(1/4)\approx-6{,}02$ dB. Os **6 dB** aparecem nos dois exemplos, mas os mecanismos físicos são diferentes.

O slide chama o dB de **“tradutor universal”** entre a percepção sonora, a **“atenuação termodinâmica”** e a potência do sinal: a mesma linguagem logarítmica descreve relações nesses contextos distintos.