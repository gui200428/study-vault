**As variações nos parâmetros de um sistema de segunda ordem podem alterar a forma da resposta.**

![[Pasted image 20260917152536.png]]

## Parâmetros de um sistema de segunda ordem:

![[Pasted image 20260917152655.png|697]]

**Valor final (Vf):** Ponto em que a resposta vai parar depois de toda a agitação inicial.
**Tempo de subida (Tr):** Tempo que o sistema leva pra sair de perto do começo e chegar perto do valor final pela primeira vez. 0.1 a 0.9. 
**Sobre-elevação (S):** Quanto a resposta passa do valor que deveria atingir. Pico acima do valor final.
**Tempo de pico (tp):** Tempo que leva até chegar no primeiro pico máximo.
**Período das oscilações:** Tempo entre uma oscilação e a próxima. Ex: distância no tempo entre dois picos consecutivos.
**Frequência:** Quantidade de oscilações que acontecem por segundo.
**Tempo de acomodação (ts):** É o tempo que demora até o sistema para de ficar saindo do valor desejado. Depois do ts, a resposta fica dentro de uma margem aceitável.

**Resumindo:**

Subiu → Passo do ponto → Oscilou → Chegou no ponto desejado

**tr:** quanto demorou para subir
**S:** quanto passou do ponto
**tp:** quando chegou no maior pico
**Ta:** tempo entre oscilações
**ts:** quando estabilizou

+-5% é a “zona de tolerância”

## Tipos de resposta de um sistema de segunda ordem:

![[Pasted image 20260917154536.png]]

**1. Superamortecida**
**2.Criticamente amortecida**
**3. Subamortecida**
**4. Não amortecida - sistema instável**

- **a) Superamortecido**  sobe sem oscilar e chega ao valor final mais lentamente.
- **b) Não amortecido**  oscila continuamente sem a amplitude diminuir.
- **c) Subamortecido**  oscila, mas as oscilações vão diminuindo até estabilizar.
- **d) Criticamente amortecido**  chega ao valor final sem oscilar e mais rápido que o superamortecido.
## Resposta superamortecida

**Característica:** sempre que existir um sistema de segunda ordem com dois polos reais e distintos, o sistema obrigatoriamente será **superamortecido.** 

![[Pasted image 20260917155911.png]]

## Resposta subamortecida

**Característica:** sempre que existir um sistema de segunda ordem com dois polos com parte imaginaria e parte real, o sistema obrigatoriamente será **subamortecida.**

![[Pasted image 20260917160500.png]]


## Resposta não amortecida

**Característica:** sempre que existir um sistema de segunda ordem com polos puramente imaginários, o sistema obrigatoriamente será **instável.**

![[Pasted image 20260917161144.png]]


## Resposta criticamente amortecida


**Característica:** sempre que existir um sistema de segunda ordem com polos reais e iguais, o sistema obrigatoriamente será **criticamente amortecido.**

![[Pasted image 20260917161411.png]]



## Resposta por inspeção: 

**Ao identificar a resposta do sistema, bas substituir nos padrões:**

![[Pasted image 20260917161747.png]]

![[Pasted image 20260917161757.png]]


## Frequência natural ($ω_n$):
É a velocidade com que o sistema naturalmente tenderia a oscilar se não tivesse amortecimento. Diz o quão “rápida” é a oscilação natural do sistema.

## Fator de amortecimento (ζ): 
Indica o quanto as oscilações são reduzidas. Diz o quão rápido o sistema para de oscilar e se estabiliza.


**Exemplo:**

Se $ω_n$ é alto, ela balança mais rápido. Se ζ é baixo, ela fica balançando por bastante tempo. Se ζ é alto, ela para de balançar rapidamente.


## Sistema de segunda ordem - Forma padrão:

### $$G(s)=\frac{ω_n^2}{s^2+2ζω_ns+ω_n^2}$$

**Comparando com:**

### $$G(s)=\frac{b}{s^2+as+b}$$

**Temos:**

#### $$ω_n^2=b$$
#### $$ω_n=\sqrt{b}$$
**e também:**

#### $$2ζω_n = a$$
#### $$ζ=\frac{a}{2ω_n}$$
#### $$ζ=\frac{a}{2\sqrt{b}}$$
## Análise do ζ para descobrir o fator de amortecimento:

![[Pasted image 20260917170311.png]]

