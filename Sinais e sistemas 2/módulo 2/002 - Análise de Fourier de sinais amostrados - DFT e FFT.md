
## Análise de Fourier 

**Motivação:** Facilidade da analise de alguns sinais no domínio da frequência do que no tempo.

**Uso:**
- Identificar frequência presentes em um sinal.
- Filtragem.
- Compressão.
- Análise de vibração.


## Revisando:

### Teorema de Nyquist:

### $$fs>=2*f_{max}$$
- Para que não tenha o aliasing, a frequência de amostragem deve ser no mínimo o dobro da frequência máxima.

**Exemplo:**

- $f_s=1000$ Hz
- Sinal real: $f = 900hz$
- **Aliasing!**
- $f_{aliasing} = 1000 - 900 = 100hz$
- O sistema vai enxergar uma frequência menor. 


## DFT - Transformada discreta de Fourier

**Definição:** Transforma um sinal discreto no tempo em um seu espectro discreto de frequência.

$$x[\ n \ ] \ para \ X[ \ k \ ] $$

**Fórmula:**

### $$X[k] = \sum_{n=0}^{N-1} x[n] e^{-j \frac{2\pi}{N} kn}$$
**Sendo:**
- N = número de amostras.
- k = índice de frequência

### Passos de resolução:

1. Abrir o somatório para cada x\[n\]
2. Encontrar a fórmula geradora X\[k\]
3. Encontrar a nova sequencia para k. Dependendo do valor de N.


### Características importantes:

**Complexidade computacional:**
- É o número de operações necessárias para se resolver a DFT
- Cresce proporcionalmente ao quadrado do tamanho da entrada.

### $$O(N^2)$$
- Se o N dobra → o trabalho **quadruplica.**


## FFT - Fast Fourier Transform

**Importante:** A FFT é um algoritmo eficiente para calcular a DFT.

**Complexidade computacional:**
- O número de operações cresce proporcionalmente a N vezes o log na base 2 de N.

### $$O(N \log_2(N))$$
- Muito mais eficiente que a DFT padrão.

**N precisa ser potencia de 2.**

### Decomposição conceitual

- Quando o número de amostras não é uma potencia de 2, é necessário fazer a fatoração das amostras.

**Exemplo:**

Um sinal possui N = 12amostras e será processado por FFT.
a) Mostre como o valor de N pode ser decomposto para aplicação de FFT mista.

**Como N = 12 não é uma potencia de 2, é necessário fatorar em produtos inteiros menores.**

Decomposição:

N = 4 * 3 → 4 sub transformadas de 3 pontos.
N = 3 * 4 → 3 sub transformadas de 4 pontos.
N = 2 * 6 → 2 sub transformadas de 6 pontos.
N = 2 * 2 * 3 → 4 DFTs de tamanho 3

### Relações da frequência na FFT:

**Cada índice k corresponde a uma frequência:**

### $$f_k=\frac{kf_s}{N}$$
**Resolução em frequência:**

### $$\Delta{f} = \frac{f_s}{N}$$

- **Importante:** Quanto amostras, melhor a resolução espectral!


## Vazamento espectral

**Definição:** ocorre quando a frequência do sinal não se enquadra em nenhuma bin da FFT. 

**Exemplo:**
Sinal senoidal puro de frequência de 123,5 hz.

Frequência de amostragem ($f_s$): 1kHz.
Número de amostras (N): 1000

Resolução do sinal: $\Delta{f} = \frac{1000}{1000} = 1Hz$ ← Cada BIn equivale a 1 Hz.

**O sinal 123,5hz não se enquadra em nenhuma BIN**. Ocorre o vazamento espectral, o sinal se divide entre as bins vizinhas de k= 123 e k= 124.


## Janelamento:

**Definição:** Para reduzir o vazamento, o sinal é multiplicado por uma função janela antes da FFT.

### $$x_w[n]=x[n]*w[n]$$
### Tipos de Janelamento:


| Janela     | Característica                         |
| ---------- | -------------------------------------- |
| Retangular | Melhor resolução, mais vazamento       |
| Hanning    | Equilibrio entre resolução e vazamento |
| Hamming    | Atenua melhor os lóbulos laterais      |
| Blackman   | Menor vazamento, pior resolução.       |

Sempre há um compromisso entre: 
- Resolução em frequência
- Vazamento espectral


## Fluxo de análise
- Adquirir o sinal amostrado
- Escolher o trecho de análise
- Aplicar a janela
- Calcular a FFT
- Plotar magnitude do espectro

