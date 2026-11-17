## Tabela de Routh (revisão rápida):

**Montando cada elemento:** sempre com as duas linhas de cima.

### $$\text{elemento}=\frac{b_1\cdot a_{k+1}-a_1\cdot b_{k+1}}{b_1}$$

**Sendo:**
- $a$: linha que está duas linhas acima.
- $b$: linha imediatamente acima.
- $a_1$, $b_1$: primeiro elemento (1ª coluna) de cada uma.
- $a_{k+1}$, $b_{k+1}$: elementos da coluna seguinte à que está sendo calculada.

**Leitura:** nº de trocas de sinal na 1ª coluna = nº de polos no semiplano da direita.

**Obs:** dá pra multiplicar ou dividir uma linha inteira por um número positivo pra simplificar as contas. Os sinais não mudam.

**Se o sistema vier em diagrama de blocos:** primeiro achar a função de transferência em malha fechada e usar o denominador dela:

$$T(s)=\frac{G(s)}{1+G(s)}$$

**Dois casos travam a tabela:**
1. Zero só na primeira coluna de uma linha.
2. Linha inteira de zeros.

### Exemplo sem caso especial:
Determinar quantos polos estão no semiplano da esquerda, no da direita e sobre o eixo $j\omega$:

![[Pasted image 20261108153412.png|500]]

**0.** Malha fechada:

$$T(s)=\frac{200}{s^4+6s^3+11s^2+6s+200}$$

**1.** Tabela:

$$\begin{array}{c|ccc}
s^4 & 1 & 11 & 200\\
s^3 & 1 & 1 & \\
s^2 & 1 & 20 & \\
s^1 & -19 & & \\
s^0 & 20 & &
\end{array}$$

- $s^3$ veio $6,\ 6$ → dividido por 6.
- $s^2$ veio $10,\ 200$ → dividido por 10.

**2.** 1ª coluna: $1 \to 1 \to 1 \to -19 \to 20$ → **2 trocas de sinal** (o negativo está na linha $s^1$).

**Resultado:** 2 polos no semiplano da direita e 2 no da esquerda → **instável**. Nenhum polo sobre $j\omega$, porque não apareceu linha de zeros.


## 1. Zero na primeira coluna:

- **O que acontece:** o primeiro elemento de uma linha dá 0 (mas a linha não é toda zero) → a próxima linha precisaria dividir por zero.
- **O que fazer:** trocar o 0 por um épsilon ($\epsilon$) e continuar.

#### Passos:
1. Montar a tabela normalmente até aparecer o 0 na 1ª coluna.
2. Trocar esse 0 por $\epsilon$.
3. Continuar a tabela carregando o $\epsilon$ nas contas.
4. Fazer $\epsilon \to 0$ pelo lado positivo ($\epsilon=+$) ou pelo lado negativo ($\epsilon=-$) e tirar o sinal de cada elemento da 1ª coluna.
5. Contar as trocas de sinal → nº de polos no semiplano da direita.

#### Exemplo:
Determinar a estabilidade de:

### $$T(s)=\frac{10}{s^5+2s^4+3s^3+6s^2+5s+3}$$

**1.** Na linha $s^3$, o primeiro elemento dá $\frac{2\cdot3-1\cdot6}{2}=0$.

**2 e 3.** Troca por $\epsilon$ e segue:

$$\begin{array}{c|ccc}
s^5 & 1 & 3 & 5\\
s^4 & 2 & 6 & 3\\
s^3 & \epsilon & \frac{7}{2} & 0\\
s^2 & \frac{6\epsilon-7}{\epsilon} & 3 & 0\\
s^1 & \frac{42\epsilon-49-6\epsilon^2}{12\epsilon-14} & 0 & 0\\
s^0 & 3 & 0 & 0
\end{array}$$

**4.** Sinais da 1ª coluna:

| Rótulo | 1ª coluna | $\epsilon=+$ | $\epsilon=-$ |
| :----: | :-------: | :----------: | :----------: |
| $s^5$ | $1$ | + | + |
| $s^4$ | $2$ | + | + |
| $s^3$ | $\epsilon$ | + | − |
| $s^2$ | $\frac{6\epsilon-7}{\epsilon}$ | − | + |
| $s^1$ | $\frac{42\epsilon-49-6\epsilon^2}{12\epsilon-14}$ | + | + |
| $s^0$ | $3$ | + | + |

- $s^2$: com $\epsilon$ pequeno fica $\approx -7/\epsilon$ → sinal contrário ao do $\epsilon$.
- $s^1$: com $\epsilon \to 0$ fica $\approx \frac{-49}{-14}$ → sempre positivo.

**5.** Nos dois casos dá **2 trocas de sinal**.

**Resultado:** sistema **instável**, com 2 polos no semiplano da direita.

### Exercício:
Determinar quantos polos estão no semiplano da esquerda, no da direita e sobre o eixo $j\omega$:

![[Pasted image 20261108154027.png|500]]

**0.** Malha fechada:

### $$T(s)=\frac{1}{2s^5+3s^4+2s^3+3s^2+2s+1}$$

**1.** Aparece zero na 1ª coluna da linha $s^3$. A linha toda não é nula → caso do $\epsilon$.

**2 e 3.** Tabela:

$$\begin{array}{c|ccc}
s^5 & 2 & 2 & 2\\
s^4 & 3 & 3 & 1\\
s^3 & \epsilon & \frac{4}{3} & \\
s^2 & \frac{3\epsilon-4}{\epsilon} & 1 & \\
s^1 & \frac{12\epsilon-16-3\epsilon^2}{9\epsilon-12} & & \\
s^0 & 1 & &
\end{array}$$

**4.** Com $\epsilon$ pequeno e positivo, o primeiro elemento da linha $s^2$ fica **negativo**.

**5.** 2 trocas de sinal.

**Resultado:** **instável**, com 2 polos no semiplano da direita. Os demais estão no semiplano da esquerda.

### Alternativa: polinômio recíproco:
**Definição:** escrever os coeficientes do denominador em ordem inversa. Isso gera um polinômio cujas raízes são as recíprocas das do original, e a tabela dele dá a mesma distribuição de polos.

#### Passos:
1. Pegar o denominador de $T(s)$.
2. Reescrever com os coeficientes em ordem inversa.
3. Montar a tabela de Routh do polinômio novo.
4. Ler normalmente: trocas de sinal = polos no semiplano da direita (mesmo resultado do original).

**Obs:** a tabela nova também pode cair em zero na 1ª coluna, mas pode ficar mais fácil de trabalhar.

#### Exemplo (mesmo exercício de cima):
**1 e 2.**

$$2s^5+3s^4+2s^3+3s^2+2s+1 \;\rightarrow\; s^5+2s^4+3s^3+2s^2+3s+2$$

**3.** Tabela (zero na 1ª coluna da linha $s^2$ → $\epsilon$):

$$\begin{array}{c|ccc}
s^5 & 1 & 3 & 3\\
s^4 & 2 & 2 & 2\\
s^3 & 2 & 2 & \\
s^2 & \epsilon & 2 & \\
s^1 & \frac{2\epsilon-4}{\epsilon} & & \\
s^0 & 2 & &
\end{array}$$

**4.** Mesmo resultado: 3 polos no semiplano da esquerda e 2 no da direita → **instável**.

**Comparando:** o $s^1$ ficou $\frac{2\epsilon-4}{\epsilon}$ no lugar de $\frac{12\epsilon-16-3\epsilon^2}{9\epsilon-12}$. As contas ficam bem mais simples.


## 2. Linha inteira de zeros:

- **O que acontece:** uma linha inteira da tabela dá zero → existe um polinômio estritamente **par** (ou estritamente **ímpar**) que é fator do polinômio original.
- **O que fazer:** montar o polinômio par da linha de cima, derivar e usar a derivada no lugar da linha de zeros. É diferente do caso do $\epsilon$.

**Polinômio par:** só tem potências pares de $s$. Ex.: $s^4+5s^2+7$.
→ Só tem raízes **simétricas em relação à origem**, em três situações (ou combinação delas):
- **A:** reais e simétricas.
- **B:** imaginárias e simétricas (sobre o eixo $j\omega$).
- **C:** quadrantais e simétricas.

![[Pasted image 20261108155133.png|400]]

**O que isso muda na tabela:**
- Não apareceu linha de zeros → **não tem raiz sobre $j\omega$** (raízes $j\omega$ são simétricas em relação à origem).
- A linha **imediatamente acima** da linha de zeros é o polinômio par $P(s)$.
- Da linha de $P(s)$ até o fim da tabela → teste **só do polinômio par**.
- Do início da tabela até a linha de $P(s)$ → teste **só do outro fator**.

#### Passos:
1. Montar a tabela até aparecer a linha toda de zeros.
2. Voltar na linha de cima e montar $P(s)$: coeficientes dessa linha, começando na potência do rótulo dela e descendo de 2 em 2.
3. Derivar: $\frac{dP(s)}{ds}$.
4. Substituir a linha de zeros pelos coeficientes de $\frac{dP(s)}{ds}$ (pode simplificar a linha).
5. Terminar a tabela normalmente.
6. **Polinômio par** (da linha de $P(s)$ até $s^0$):
	- trocas de sinal → polos no semiplano da direita;
	- semiplano da esquerda → mesmo número do da direita (simetria);
	- o que sobrar do grau de $P(s)$ → sobre o eixo $j\omega$.
7. **Outro fator** (do início até a linha de $P(s)$):
	- trocas de sinal → polos no semiplano da direita;
	- o resto → semiplano da esquerda;
	- não pode ter raiz sobre $j\omega$.
8. Somar par + outro → total. Tem polo no semiplano da direita → **instável**.

#### Exemplo 1:
Número de polos no semiplano da direita de:

### $$T(s)=\frac{10}{s^5+7s^4+6s^3+42s^2+8s+56}$$

**1.** Tabela até travar:

$$\begin{array}{c|ccc}
s^5 & 1 & 6 & 8\\
s^4 & 1 & 6 & 8\\
s^3 & 0 & 0 & 0
\end{array}$$

- $s^4$ veio $7,\ 42,\ 56$ → dividido por 7.

**2.** $P(s)=s^4+6s^2+8$

**3.** $\frac{dP(s)}{ds}=4s^3+12s+0$

**4.** Linha $s^3$ vira $4,\ 12,\ 0$ → multiplicada por $\frac{1}{4}$ → $1,\ 3,\ 0$.

**5.** Resto da tabela:

$$\begin{array}{c|ccc}
s^5 & 1 & 6 & 8\\
s^4 & 1 & 6 & 8\\
s^3 & 1 & 3 & 0\\
s^2 & 3 & 8 & 0\\
s^1 & \frac{1}{3} & 0 & 0\\
s^0 & 8 & 0 & 0
\end{array}$$

**Resultado:** todos os elementos da 1ª coluna são positivos → **nenhum polo no semiplano da direita**.

#### Exemplo 2:
Quantos polos estão no semiplano da direita, no da esquerda e sobre o eixo $j\omega$:

### $$T(s)=\frac{20}{s^8+s^7+12s^6+22s^5+39s^4+59s^3+48s^2+38s+20}$$

**1.** Tabela até travar:

$$\begin{array}{c|ccccc}
s^8 & 1 & 12 & 39 & 48 & 20\\
s^7 & 1 & 22 & 59 & 38 & 0\\
s^6 & -1 & -2 & 1 & 2 & 0\\
s^5 & 1 & 3 & 2 & 0 & 0\\
s^4 & 1 & 3 & 2 & 0 & 0\\
s^3 & 0 & 0 & 0 & 0 & 0
\end{array}$$

- $s^6$ veio $-10,\ -20,\ 10,\ 20$ → dividido por 10.
- $s^5$ veio $20,\ 60,\ 40$ → dividido por 20.

**2.** $P(s)=s^4+3s^2+2$

**3.** $\frac{dP(s)}{ds}=4s^3+6s+0$

**4.** Linha $s^3$ vira $4,\ 6$ → dividida por 2 → $2,\ 3$.

**5.** Resto da tabela:

$$\begin{array}{c|ccccc}
s^3 & 2 & 3 & 0 & 0 & 0\\
s^2 & 3 & 4 & 0 & 0 & 0\\
s^1 & \frac{1}{3} & 0 & 0 & 0 & 0\\
s^0 & 4 & 0 & 0 & 0 & 0
\end{array}$$

- $s^2$ veio $\frac{3}{2},\ 2$ → multiplicado por 2.

**6.** Polinômio par ($s^4$ até $s^0$): $1,\ 2,\ 3,\ \frac{1}{3},\ 4$ → **0 trocas** → 0 no semiplano da direita → 0 no da esquerda (simetria) → os **4 polos estão sobre $j\omega$**.

**7.** Outro fator ($s^8$ até $s^4$): $1,\ 1,\ -1,\ 1,\ 1$ → **2 trocas** ($s^7 \to s^6$ e $s^6 \to s^5$) → 2 no semiplano da direita e 2 no da esquerda.

**8.** Somando:

| Posição | Par (4ª ordem) | Outro (4ª ordem) | Total (8ª ordem) |
| :------ | :------------: | :--------------: | :--------------: |
| Semiplano da direita | 0 | 2 | 2 |
| Semiplano da esquerda | 0 | 2 | 2 |
| $j\omega$ | 4 | 0 | 4 |

**Resultado:** **instável** por causa dos 2 polos no semiplano da direita.

### Exercício:
Determinar quantos polos estão no semiplano da esquerda, no da direita e sobre o eixo $j\omega$ e concluir sobre a estabilidade em malha fechada:

![[Pasted image 20261108160249.png|600]]

**0.** Malha fechada:

### $$T(s)=\frac{128}{s^8+3s^7+10s^6+24s^5+48s^4+96s^3+128s^2+192s+128}$$

**1.** Tabela até travar:

$$\begin{array}{c|ccccc}
s^8 & 1 & 10 & 48 & 128 & 128\\
s^7 & 1 & 8 & 32 & 64 & \\
s^6 & 1 & 8 & 32 & 64 & \\
s^5 & 0 & 0 & 0 & 0 &
\end{array}$$

- $s^7$ veio $3,\ 24,\ 96,\ 192$ → dividido por 3.
- $s^6$ veio $2,\ 16,\ 64,\ 128$ → dividido por 2.

**2.** Linha de zeros em $s^5$ → volta na $s^6$:

$$P(s)=s^6+8s^4+32s^2+64$$

**3.** $\frac{dP(s)}{ds}=6s^5+32s^3+64s+0$

**4.** Linha $s^5$ vira $6,\ 32,\ 64$ → multiplicada por $\frac{1}{2}$ → $3,\ 16,\ 32$.

**5.** Resto da tabela:

$$\begin{array}{c|cccc}
s^5 & 3 & 16 & 32 & 0\\
s^4 & 1 & 8 & 24 & \\
s^3 & -1 & -5 & & \\
s^2 & 1 & 8 & & \\
s^1 & 3 & & & \\
s^0 & 8 & & &
\end{array}$$

- $s^4$ veio $\frac{8}{3},\ \frac{64}{3},\ 64$ → multiplicado por $\frac{3}{8}$.
- $s^3$ veio $-8,\ -40$ → dividido por 8.
- $s^2$ veio $3,\ 24$ → dividido por 3.

**6.** Polinômio par ($s^6$ até $s^0$): $1,\ 3,\ 1,\ -1,\ 1,\ 3,\ 8$ → **2 trocas** → 2 no semiplano da direita → 2 no da esquerda (simetria) → sobram $6-4=2$ **sobre $j\omega$**.

**7.** Outro fator ($s^8$ até $s^6$): $1,\ 1,\ 1$ → **0 trocas** → nenhum polo no semiplano da direita, os 2 estão no da esquerda.

**8.** Somando:

| Posição | Par (6ª ordem) | Outro (2ª ordem) | Total (8ª ordem) |
| :------ | :------------: | :--------------: | :--------------: |
| Semiplano da direita | 2 | 0 | 2 |
| Semiplano da esquerda | 2 | 2 | 4 |
| $j\omega$ | 2 | 0 | 2 |

**Resultado:** 2 polos no semiplano da direita, 4 no da esquerda e 2 sobre $j\omega$ (de multiplicidade unitária) → **instável** por causa dos polos no semiplano da direita.


## Exercício para fazer:
Usar o critério de Routh-Hurwitz para descobrir quantos polos de $T(s)$ estão no semiplano da direita, no da esquerda e sobre o eixo $j\omega$:

### $$T(s)=\frac{s^3+7s^2-21s+10}{s^6+s^5-6s^4+0s^3-s^2-s+6}$$


## Resumo:

**Zero só na 1ª coluna:** troca por $\epsilon$ → continua a tabela → $\epsilon \to 0$ → conta as trocas de sinal. (Ou usa o polinômio recíproco.)

**Linha toda de zeros:** $P(s)$ da linha de cima → deriva → substitui a linha de zeros → termina a tabela → par (SPD = SPE, o resto em $j\omega$) + outro (SPD + SPE) → soma.

**Sem linha de zeros** → sem polo sobre $j\omega$.
