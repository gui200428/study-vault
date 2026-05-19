
## Teorema da Amostragem (Nyquist)

**Definição:** Um sinal continuo **limitado em banda** (frequência máxima $f_{max}$) pode ser completamente reconstruído a partir de suas amostras se a frequência de amostragem $f_s$ satisfazer a condição:

### $$f_s >= 2* f_{max}$$
- **Amostrar um sinal:** observar o valor do sinal em instantes discretos no tempo
- **Amostragem incorreta: (aliasing):** o sinal vai aparentar ter outra frequência 
- **Amostrar rápido o suficiente um sinal (acima de nyquist):** preserva a informação. 


### Exemplo:

- Faixa audível para humanos: **até 20kHz**
Reconstrução do sinal: 

Frequência minima de amostragem para que nenhuma informação seja perdida:

### $$fs = 2 * 20kHz = 40kHz$$
**Interpretação:**
- 40kHz é a **frequência de amostragem** mínima para capturar todo o espectro audível sem perda de informação (aliasing).
- 40kHz é a frequência de amostragem mínima teórica. Na prática, é utilizado um valor superior, ex: cd - 44.1kHz para evitar problemas com a frequência de corte.


### Exemplo 2:

- Frequência máxima: 1kHz
- **Frequência de amostragem:** $fs = 2*1kHz = 2kHz$ (limite teórico)
- Para prática, pode utilizar uma frequência maior, desde que acima do limite teórico (5kHz, 10kHz).


## Aliasing:

**Definição:** Ocorre quando um sinal é amostrado com uma frequência menor que a frequência de Nyquist. Isso faz com que componentes de alta frequência apareçam como frequências mais baixas no sinal amostrado. **O sinal pare outro.**

Regra:

### $$fs < 2*fmax = aliasing$$



#### Calculo do sinal visto pelo sistema quando se tem aliasing:

### $$f_{alias}=|f -k*fs|$$

### Consequências do aliasing:

- Distorção irreversível do sinal. 
- Destrói a informação do sinal de forma permanente.
- Erros em sistemas digitais. 


## Anti-aliasing

**Definição:** Conjunto de técnicas para evitar o aliasing durante o processo de amostragem de um sinal contínuo. 
**Principal técnica:** Aplicação de um filtro passa-baixas analógico antes da amostragem.

- Filtro anti-aliasing.

### Função do filtro:

- Remoção de frequências acimas da frequência maxima ($f_{max}$)
- Garante que o sinal seja limitado em banda.
- Atenuar qualquer componente de frequência que seja maior que a **Frequência de Nyquist** ($f_s/2$) do sistema.

### Exemplo Prático: Por que o filtro é necessário?

* **Sinal original:** Composto por duas frequências $\{3\text{ kHz e } 8\text{ kHz}\}$
* **Frequência máxima ($f_{max}$):** $8\text{ kHz}$
* **Frequência de amostragem ($f_s$):** $10\text{ kHz}$
* **Frequência de Nyquist ($f_s/2$):** $5\text{ kHz}$

#### 1. Verificação do Teorema de Nyquist
Para amostrar este sinal sem perdas, a teoria exige que $f_s \ge 2 \cdot f_{max}$. 
Como $10\text{ kHz} < 16\text{ kHz}$, a amostragem é insuficiente. **Haverá aliasing com 8kHz de fmax.**

#### 2. O Problema (Amostragem SEM o filtro)
* A componente de $3\text{ kHz}$ é amostrada corretamente ($3\text{ kHz} < 5\text{ kHz}$).
* A componente de $8\text{ kHz}$ sofre aliasing. Ela é rebatida para uma frequência "fantasma" dentro da banda base:
  $$f_{aliasing} = |f_s - f_{in}| = |10\text{ kHz} - 8\text{ kHz}| = 2\text{ kHz}$$
* **Resultado:** O sinal digitalizado registrará frequências em $3\text{ kHz}$ e $2\text{ kHz}$. O dado original foi permanentemente corrompido.

#### 3. A Solução (Amostragem COM o filtro)
* Aplicamos o filtro passa-baixas com frequência de corte exata na Frequência de Nyquist (**$5\text{ kHz}$**).
* A componente de $8\text{ kHz}$ é barrada pelo filtro *antes* de chegar ao amostrador.
* **Resultado:** O sinal digitalizado registrará apenas a componente de $3\text{ kHz}$. Perde-se a alta frequência original (que já não poderia ser reconstruída com $f_s = 10\text{ kHz}$ de qualquer forma), mas garante-se a integridade do que sobrou, impedindo o surgimento da frequência fantasma.


## Reconstrução de sinais:

**Definição:** Processo de obter novamente um sinal contínuo a partir de amostras digitais.

### Reconstrução ideal

- Ela é feita com o uso de um **filtro passa-baixas ideal** com resposta sinc.

![[Pasted image 20260519201546.png]]

- Perfeitamente possível apenas em teoria.


### Na prática utiliza-se:
- Filtros passa-baixas reais
- Conversores DAC + filtro de reconstrução


### Exemplo Prático – DAC
- Amostras chegam ao DAC
- DAC gera degraus (signal holding)
- Filtro passa-baixas suaviza o sinal
- O sinal reconstruído aproxima o original

### Erros de Reconstrução
- Frequência de amostragem baixa
- Filtros não ideais
- Quantização (ruído adicional)

