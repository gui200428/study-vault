## Polos dominantes e aproximação por sistemas de segunda ordem

Um sistema pode possuir mais de dois polos e apresentar um comportamento próximo ao de um sistema de segunda ordem. Isso acontece quando um par de polos complexos possui maior influência sobre a resposta transitória.

**Polos dominantes:** polos cuja contribuição demora mais para desaparecer da resposta.

## 1. O que torna um polo dominante?

Cada polo está associado a um termo da resposta no domínio do tempo. Para comparar dois polos reais, temos:

$$
\begin{aligned}
s=-2 &\quad \rightarrow \quad e^{-2t}\\
s=-10 &\quad \rightarrow \quad e^{-10t}
\end{aligned}
$$

O termo $e^{-2t}$ decai mais lentamente que $e^{-10t}$. Portanto, sua contribuição permanece por mais tempo na resposta.

**Regra mental:** quanto mais próximo do eixo imaginário estiver um polo estável, mais lentamente sua contribuição desaparece.

$$
\text{Mais próximo do eixo imaginário}
\;\rightarrow\;
\text{Decaimento mais lento}
$$

**Importante:** a influência de cada termo também depende de sua amplitude. A posição dos polos indica a velocidade de decaimento.

## 2. Polos complexos

Um par de polos complexos conjugados pode ser escrito como:

$$
s=-\sigma\pm j\omega
$$

**Sendo:**

- $-\sigma$: parte real, responsável pelo decaimento da resposta.
- $\omega$: magnitude da parte imaginária, responsável pela frequência angular da oscilação.

Os termos associados a esse par possuem a forma:

$$
e^{-\sigma t}\cos(\omega t)
\qquad \text{e} \qquad
e^{-\sigma t}\sin(\omega t)
$$

**Exemplo:** para o termo abaixo,

$$
e^{-3t}\cos(22{,}16t)
$$

os polos associados são:

$$
s=-3\pm j22{,}16
$$

A parte real $-3$ determina o decaimento, enquanto $22{,}16\ \text{rad/s}$ determina a frequência angular da oscilação.

## 3. Polo proveniente da entrada degrau

Na análise de uma resposta ao degrau unitário, a entrada é representada por:

$$
R(s)=\frac{1}{s}
$$

Por isso, a transformada da saída pode apresentar um polo na origem associado à entrada.

**Exemplo:** considerando a resposta

$$
c(t)=2+3e^{-5t}
$$

sua transformada é:

$$
C(s)=\frac{2}{s}+\frac{3}{s+5}
$$

**Sendo:**

- $2/s$: associado ao termo constante da resposta.
- $3/(s+5)$: associado ao termo transitório, com polo em $s=-5$.

**Importante:** o polo na origem proveniente da entrada degrau não entra na comparação dos polos transitórios. Isso não significa que todo polo na origem venha da entrada; o próprio sistema também pode possuir polos na origem.

## 4. Aproximação por um sistema de segunda ordem

Considere um sistema com um par de polos complexos e um polo real adicional:

$$
\begin{aligned}
p_1&=-\sigma+j\omega\\
p_2&=-\sigma-j\omega\\
p_3&=-a
\end{aligned}
$$

O par complexo produz termos oscilatórios com envoltória $e^{-\sigma t}$. O polo real adicional produz um termo proporcional a $e^{-at}$.

Se a contribuição do polo real desaparecer muito mais rapidamente, podemos considerar uma aproximação que mantenha apenas o par complexo.

$$
\text{Sistema de ordem maior}
\;\approx\;
\text{Sistema de segunda ordem}
$$

## 5. Regra prática das 5 vezes

**Critério:** o polo real adicional deve estar aproximadamente cinco vezes mais afastado do eixo imaginário que a parte real do par dominante.

Para os polos $-\sigma\pm j\omega$ e $-a$, com $\sigma>0$ e $a>0$:

$$
a\gtrsim 5\sigma
$$

**Importante:** usamos a magnitude da **parte real** do par complexo, pois ela determina o decaimento.

**Exemplo:** para o par

$$
p_{1,2}=-2\pm j5
$$

temos:

$$
\sigma=|-2|=2
\qquad \Rightarrow \qquad
5\sigma=5\cdot2=10
$$

Comparando duas possibilidades para o polo adicional:

$$
\begin{aligned}
p_3=-12 &: \quad 12>10
\quad \rightarrow \quad \text{Atende ao critério}\\
p_3=-4 &: \quad 4<10
\quad \rightarrow \quad \text{Não atende ao critério}
\end{aligned}
$$

Essa é uma regra prática. A qualidade da aproximação também depende dos zeros e das amplitudes dos termos da resposta.

## 6. Identificação dos polos no domínio do tempo

Dada uma resposta na forma:

$$
\begin{aligned}
c(t)={}&K_0+K_1e^{-at}\\
&+K_2e^{-\sigma t}\cos(\omega t)\\
&+K_3e^{-\sigma t}\sin(\omega t)
\end{aligned}
$$

identificamos:

$$
\begin{aligned}
K_0 &\quad \rightarrow \quad \frac{K_0}{s}\\
K_1e^{-at} &\quad \rightarrow \quad s=-a\\
e^{-\sigma t}\left[K_2\cos(\omega t)+K_3\sin(\omega t)\right]
&\quad \rightarrow \quad s=-\sigma\pm j\omega
\end{aligned}
$$

O termo constante representa o valor final. Os termos exponenciais e oscilatórios amortecidos descrevem a resposta transitória.

## 7. Passo a passo para verificar a aproximação

1. **Identificar os polos:** observar os termos exponenciais e oscilatórios.
2. **Separar o termo constante:** excluir da comparação o polo proveniente da entrada degrau.
3. **Identificar o par complexo candidato a dominante:** verificar sua parte real.
4. **Aplicar a regra das 5 vezes:** calcular $5\sigma$.
5. **Comparar com o polo real adicional:** verificar se $a\gtrsim5\sigma$.
6. **Concluir:** indicar se a aproximação é justificável pela regra prática.

**Exemplo rápido:** para o par $-3\pm j10$,

$$
5\sigma=5\cdot|-3|=15
$$

O polo real adicional deve estar aproximadamente em $-15$ ou mais à esquerda para atender ao critério.

## 8. Exemplo completo

**Dada a resposta:**

$$
\begin{aligned}
c(t)={}&0{,}003500-0{,}001524e^{-4t}\\
&-0{,}001976e^{-3t}\cos(22{,}16t)\\
&-0{,}0005427e^{-3t}\sin(22{,}16t)
\end{aligned}
$$

Determine se a aproximação por uma resposta de segunda ordem é justificável pela regra das 5 vezes.

**1. Identificar os polos:**

O termo constante corresponde ao valor final. Os termos transitórios fornecem:

$$
\begin{aligned}
e^{-4t}
&\quad \rightarrow \quad p_1=-4\\
e^{-3t}\cos(22{,}16t)\ \text{e}\ e^{-3t}\sin(22{,}16t)
&\quad \rightarrow \quad p_{2,3}=-3\pm j22{,}16
\end{aligned}
$$

**2. Identificar o par candidato a dominante:**

A envoltória $e^{-3t}$ decai mais lentamente que $e^{-4t}$. Portanto, o par complexo é o candidato a dominante:

$$
p_{2,3}=-3\pm j22{,}16
$$

É necessário verificar se o polo real $p_1=-4$ está suficientemente afastado.

**3. Aplicar a regra das 5 vezes:**

$$
\begin{aligned}
\sigma&=|-3|=3\\
5\sigma&=5\cdot3=15\\
a&=|-4|=4
\end{aligned}
$$

Comparando:

$$
4<15
$$

**Conclusão:** a aproximação por segunda ordem **não é justificada pela regra das 5 vezes**, pois o polo real em $s=-4$ não está suficientemente afastado do par complexo.

## 9. Resumo

**Polo dominante:** sua contribuição permanece por mais tempo na resposta transitória.

**Parte real:** determina a velocidade de decaimento.

**Parte imaginária:** determina a frequência angular da oscilação.

**Polo da entrada degrau:** não entra na comparação dos polos transitórios do sistema.

**Regra das 5 vezes:**

$$
\boxed{a\gtrsim5\sigma}
$$

Para um polo adicional $-a$ e um par complexo $-\sigma\pm j\omega$, esse critério ajuda a avaliar se a aproximação de segunda ordem é adequada.