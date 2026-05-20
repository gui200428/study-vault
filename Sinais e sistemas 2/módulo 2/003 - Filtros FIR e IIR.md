## Motivação do uso dos filtros digitais

- Remoção de ruído
- Separação de bandas de frequência
- Equalização: reforça ou atenua bandas específicas do espectro
- Controle e comunicações
- Processamento em tempo real

![[Pasted image 20260520125032.png]]

## Filtragem:
- Em geral, filtragem é um processo no domínio do tempo (contínuo ou discreto) que resulta do sinal original (mudança no espectro).
- Elimina componentes indesejadas do espectro de frequência.
- Permite que algumas componentes passem e outras não.

## Filtros FIR - Finite Impulse Response
- Dada uma sequência de duração finita com valores diferentes de zero, a saída do filtro FIR será uma sequência de duração finita com valores diferentes de zero.
- Filtros FIR usam blocos operacionais para calcular sua resposta, semelhante a um processo de média.

### Filtro passa - baixas
- Tem o objetivo de remover altas frequências.

### Frequência de corte
- Indica onde o filtro começa a atenuar o sinal

### Normalização da frequência:

### $$ω_c = 2 \pi \frac{fc}{fs}$$
- Momento em que filtro começa a corta em x% da frequência máxima possível.

### Banda de transição:
- Em aplicações reais, o **ganho não cai instantaneamente.** 
- Existe uma região intermediária, a **banda de transição.**

$$\Delta f = 500$$
- Filtro passa até 1kHz.
- 1.5kHz é rejeitado.
**Transição larga** → filtro simples.

### Ordem do FIR

A ordem controla os seguintes pontos:
- Quantos coeficientes
- Quão “afiado” é o filtro
- Atraso introduzido

**Fórmula:**

### $$N \approx \frac{f_s}{\Delta f}$$
**A ordem do filtro é inversamente proporcional a largura de banda.**

**Importante sobre filtros FIR:** eles não possuem realimentação!


### Fase e atraso de filtros FIR

**Atraso em amostras:**

### $$\tau_{amostras}= \frac{N}{2}$$
**Em tempo:**

### $$\tau_{temnpo}=\frac{\tau_{amostras}}{f_s}$$
**O filtro FIR não distorce o sinal! Ele atrasa somente.**

### Estabilidade:

**Todo filtro FIR:**
- Não é recursivo
- Resposta ao impulso finita
- Sempre estável
- Não depende dos coeficientes
- Implementação simples 

## Filtros IIR - Infinite Impulse Response

- É um filtro do tipo recursivo. 


### Banda de transição:

### $$\Delta f = 1kHz$$

Transição larga → filtro simples


### Normalização das frequências
- Filtros digitais não trabalham diretamente em Hz, mas em **frequência digital normalizada.**

### $$ω = 2 \pi \frac{f}{f_s}$$

### Estabilidade:
- Todos os polos devem estar dentro do círculo unitário
- Para o filtro IIR projetado corretamente:  **Filtro estável**
- **Estabilidade precisa ser verificada.**
