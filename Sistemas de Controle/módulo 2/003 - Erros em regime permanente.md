## Erro em regime permanente:

**Definição:** diferença entre a entrada e a saída, para uma entrada de teste, quando $t \to \infty$.

→ É a terceira especificação de um sistema de controle, junto com resposta transitória e estabilidade. O projeto é um compromisso entre as três.

**Só vale para sistema estável:** num sistema instável a resposta natural não some, então não existe regime permanente. As fórmulas de erro aplicadas num sistema instável dão um resultado errado.
→ **Sempre verificar a estabilidade primeiro** (Routh-Hurwitz).


## Entradas de teste:

| Entrada | Interpretação física | $r(t)$ | $R(s)$ |
| :------ | :------------------- | :----: | :----: |
| Degrau | Posição constante | $1$ | $\frac{1}{s}$ |
| Rampa | Velocidade constante | $t$ | $\frac{1}{s^2}$ |
| Parábola | Aceleração constante | $\frac{1}{2}t^2$ | $\frac{1}{s^3}$ |

- **Degrau:** testa se o sistema consegue se posicionar num alvo parado. Ex.: antena apontando para um satélite em órbita geoestacionária.
- **Rampa:** testa se o sistema consegue rastrear um alvo com velocidade constante. Ex.: satélite cruzando o céu com velocidade angular constante.
- **Parábola:** testa se o sistema consegue rastrear um alvo acelerando. Ex.: míssil.


## Lendo o erro no gráfico:

![[Pasted image 20261108201537.png|400]]

**(a) Degrau:**
- Saída 1 chega no valor da entrada → **erro nulo**.
- Saída 2 estabiliza abaixo da entrada → **erro finito** ($e_2(\infty)$).

**(b) Rampa:**
- Saída 1 encosta na entrada → **erro nulo**.
- Saída 2 fica paralela à entrada, com uma distância fixa → **erro finito**.
- Saída 3 tem inclinação diferente da entrada → a distância só cresce → **erro infinito**.


## Fontes de erro:

- Muitos erros vêm de **fontes não lineares**: folga em engrenagens, motor que só se move quando a tensão passa de um limiar.
- Aqui só entram os erros que vêm da **configuração do sistema** e do **tipo de entrada**.

![[Pasted image 20261108202214.png|450]]

Com $E(s)=R(s)-C(s)$ e entrada degrau: **o erro diminui conforme K aumenta**.


## Calculando o erro com T(s):

![[Pasted image 20261108203046.png|500]]

(a) representação geral, com $T(s)$ / (b) realimentação unitária, com $G(s)$.

**Montando $E(s)$ pela representação geral:**

$$E(s)=R(s)-C(s) \qquad C(s)=R(s)T(s)$$

### $$E(s)=R(s)\,[1-T(s)]$$

**Teorema do Valor Final:** dá o valor de uma função quando $t \to \infty$ direto pela transformada de Laplace.

### $$e(\infty)=\lim_{t\to\infty}e(t)=\lim_{s\to 0}sE(s)$$

#### Passos:
1. Pegar $R(s)$ da entrada (tabela de entradas).
2. Montar $E(s)=R(s)[1-T(s)]$.
3. Multiplicar por $s$ e fazer $s \to 0$.

#### Exemplo:
Erro em regime permanente para $T(s)=\frac{5}{s^2+7s+10}$ com entrada degrau unitário.

**1.** $R(s)=\frac{1}{s}$

**2.**

$$E(s)=\frac{1}{s}\left[1-\frac{5}{s^2+7s+10}\right]=\frac{s^2+7s+5}{s(s^2+7s+10)}$$

**3.**

$$e(\infty)=\lim_{s\to0}s\cdot\frac{s^2+7s+5}{s(s^2+7s+10)}=\frac{5}{10}=\frac{1}{2}$$


## Calculando o erro com G(s) (realimentação unitária):

Escrever o erro em função de $G(s)$ (malha aberta) em vez de $T(s)$ ajuda mais na análise e no projeto.

$$E(s)=R(s)-C(s) \qquad C(s)=E(s)G(s)$$

$$E(s)=\frac{R(s)}{1+G(s)}$$

### $$e(\infty)=\lim_{s\to0}\frac{sR(s)}{1+G(s)}$$

**Para cada entrada:**

**Degrau** $\left(R(s)=\frac{1}{s}\right)$:

$$e_{degrau}(\infty)=\lim_{s\to0}\frac{s(1/s)}{1+G(s)}=\frac{1}{1+\lim\limits_{s\to0}G(s)}$$

**Rampa** $\left(R(s)=\frac{1}{s^2}\right)$:

$$e_{rampa}(\infty)=\lim_{s\to0}\frac{s(1/s^2)}{1+G(s)}=\lim_{s\to0}\frac{1}{s+sG(s)}=\frac{1}{\lim\limits_{s\to0}sG(s)}$$

**Parábola** $\left(R(s)=\frac{1}{s^3}\right)$:

$$e_{parábola}(\infty)=\lim_{s\to0}\frac{s(1/s^3)}{1+G(s)}=\lim_{s\to0}\frac{1}{s^2+s^2G(s)}=\frac{1}{\lim\limits_{s\to0}s^2G(s)}$$

**Obs:** a amplitude da entrada multiplica o numerador:
- $5u(t)$ → $R(s)=\frac{5}{s}$ → numerador 5.
- $5tu(t)$ → $R(s)=\frac{5}{s^2}$ → numerador 5.
- $5t^2u(t)$ → $R(s)=\frac{10}{s^3}$ → numerador 10 (porque $5t^2 = 10\cdot\frac{1}{2}t^2$).

#### Passos:
1. Verificar a estabilidade.
2. Ver a entrada e pegar a fórmula certa (degrau, rampa ou parábola), com a amplitude no numerador.
3. Calcular o limite de $G(s)$, $sG(s)$ ou $s^2G(s)$ com $s \to 0$.
4. Ler o resultado:
	- limite **infinito** → erro **0**;
	- limite **finito** → erro **finito**;
	- limite **zero** → erro **infinito**.

#### Exemplo 1:
Erros para $5u(t)$, $5tu(t)$ e $5t^2u(t)$, com realimentação unitária e:

### $$G(s)=\frac{120(s+2)}{(s+3)(s+4)}$$

**Degrau:** $\lim\limits_{s\to0}G(s)=\frac{120\cdot2}{3\cdot4}=20$

$$e_{degrau}(\infty)=\frac{5}{1+\lim\limits_{s\to0}G(s)}=\frac{5}{1+20}=\frac{5}{21}$$

**Rampa:**

$$e_{rampa}(\infty)=\frac{5}{\lim\limits_{s\to0}sG(s)}=\frac{5}{0}=\infty$$

**Parábola:**

$$e_{parábola}(\infty)=\frac{10}{\lim\limits_{s\to0}s^2G(s)}=\frac{10}{0}=\infty$$

#### Exemplo 2:
Mesmas entradas, com:

### $$G(s)=\frac{100(s+2)(s+6)}{s(s+3)(s+4)}$$

**Degrau:**

$$e_{degrau}(\infty)=\frac{5}{1+\lim\limits_{s\to0}G(s)}=\frac{5}{\infty}=0$$

**Rampa:** $\lim\limits_{s\to0}sG(s)=\frac{100\cdot2\cdot6}{3\cdot4}=100$

$$e_{rampa}(\infty)=\frac{5}{100}=\frac{1}{20}$$

**Parábola:**

$$e_{parábola}(\infty)=\frac{10}{\lim\limits_{s\to0}s^2G(s)}=\frac{10}{0}=\infty$$

**Comparando:** o $s$ no denominador de $G(s)$ fez o erro ao degrau virar 0 e o erro à rampa virar finito.

### Exercício:
Sistema com realimentação unitária. **Verificar a estabilidade dos sistemas.**

$$G(s)=\frac{10(s+20)(s+30)}{s(s+25)(s+35)}$$

**A)** Erro para $15u(t)$, $15tu(t)$ e $15t^2u(t)$:

- **Degrau:** $\lim\limits_{s\to0}G(s)=\infty$ → $e_{degrau}(\infty)=0$
- **Rampa:** $\lim\limits_{s\to0}sG(s)=\frac{10\cdot20\cdot30}{25\cdot35}=\frac{6000}{875}$ → $e_{rampa}(\infty)=\frac{15}{6000/875}=2{,}1875$
- **Parábola:** $\lim\limits_{s\to0}s^2G(s)=0$ → $e_{parábola}(\infty)=\infty$

**B)** Repetir para:

$$G(s)=\frac{10(s+20)(s+30)}{s^2(s+25)(s+35)(s+50)}$$


## Constantes de erro estático:

**Definição:** são os limites que aparecem no denominador das fórmulas de erro. Servem como especificação de desempenho do erro em regime permanente.

| Constante | Fórmula | Entrada | Erro |
| :-------- | :-----: | :------ | :--: |
| **Posição** $K_p$ | $\lim\limits_{s\to0}G(s)$ | Degrau, $u(t)$ | $\frac{1}{1+K_p}$ |
| **Velocidade** $K_v$ | $\lim\limits_{s\to0}sG(s)$ | Rampa, $tu(t)$ | $\frac{1}{K_v}$ |
| **Aceleração** $K_a$ | $\lim\limits_{s\to0}s^2G(s)$ | Parábola, $\frac{1}{2}t^2u(t)$ | $\frac{1}{K_a}$ |

→ **Quanto maior a constante, menor o erro.**

**interpretação** de $K_p$, $K_v$ e $K_a$ para identificar o tipo (seção de interpretação mais abaixo).

#### Passos:
1. Calcular $K_p$, $K_v$ e $K_a$ com $s \to 0$.
2. Jogar cada uma na fórmula do erro da entrada correspondente.

#### Exemplo 1:
Calcular as constantes e o erro para degrau, rampa e parábola, com realimentação unitária e:

### $$G(s)=\frac{500(s+2)(s+5)}{(s+8)(s+10)(s+12)}$$

$$K_p=\lim_{s\to0}G(s)=\frac{500\times2\times5}{8\times10\times12}=5{,}208 \quad\rightarrow\quad e(\infty)=\frac{1}{1+K_p}=0{,}161$$

$$K_v=\lim_{s\to0}sG(s)=0 \quad\rightarrow\quad e(\infty)=\frac{1}{K_v}=\infty$$

$$K_a=\lim_{s\to0}s^2G(s)=0 \quad\rightarrow\quad e(\infty)=\frac{1}{K_a}=\infty$$

#### Exemplo 2:
Mesmo pedido, com:

### $$G(s)=\frac{500(s+2)(s+5)(s+6)}{s(s+8)(s+10)(s+12)}$$

$$K_p=\lim_{s\to0}G(s)=\infty \quad\rightarrow\quad e(\infty)=\frac{1}{1+K_p}=0$$

$$K_v=\lim_{s\to0}sG(s)=\frac{500\times2\times5\times6}{8\times10\times12}=31{,}25 \quad\rightarrow\quad e(\infty)=\frac{1}{31{,}25}=0{,}032$$

$$K_a=\lim_{s\to0}s^2G(s)=0 \quad\rightarrow\quad e(\infty)=\frac{1}{K_a}=\infty$$


## Tipos de sistema:

| Entrada | Erro | Tipo 0 | Tipo 1 | Tipo 2 |
| :------ | :--: | :----- | :----- | :----- |
| Degrau, $u(t)$ | $\frac{1}{1+K_p}$ | $K_p=$ constante → erro $\frac{1}{1+K_p}$ | $K_p=\infty$ → erro $0$ | $K_p=\infty$ → erro $0$ |
| Rampa, $tu(t)$ | $\frac{1}{K_v}$ | $K_v=0$ → erro $\infty$ | $K_v=$ constante → erro $\frac{1}{K_v}$ | $K_v=\infty$ → erro $0$ |
| Parábola, $\frac{1}{2}t^2u(t)$ | $\frac{1}{K_a}$ | $K_a=0$ → erro $\infty$ | $K_a=0$ → erro $\infty$ | $K_a=$ constante → erro $\frac{1}{K_a}$ |


## Interpretando $K_p$, $K_v$ e $K_a$ → tipo do sistema:

**Ideia:** cada tipo tem **uma única constante finita** (nem 0, nem $\infty$). Ela diz o tipo:

### $$K_p \text{ finito} \rightarrow \text{Tipo 0} \qquad K_v \text{ finito} \rightarrow \text{Tipo 1} \qquad K_a \text{ finito} \rightarrow \text{Tipo 2}$$

| | $K_p$ | $K_v$ | $K_a$ |
| :-- | :--: | :--: | :--: |
| **Tipo 0** | **finito** | $0$ | $0$ |
| **Tipo 1** | $\infty$ | **finito** | $0$ |
| **Tipo 2** | $\infty$ | $\infty$ | **finito** |

**Padrão:** na ordem $K_p \rightarrow K_v \rightarrow K_a$, as constantes **antes** da finita são $\infty$ e as **depois** são $0$.

**Ligando constante e erro:**
- constante $= \infty$ → erro $= 0$ (a saída chega na entrada);
- constante finita → erro finito (a saída fica a uma distância fixa);
- constante $= 0$ → erro $= \infty$ (a saída se afasta cada vez mais).

**Na prática, por tipo:**
- **Tipo 0:** segue degrau com erro finito; não segue rampa nem parábola (erro $\infty$).
- **Tipo 1:** segue degrau com erro 0; segue rampa com erro finito; não segue parábola.
- **Tipo 2:** segue degrau e rampa com erro 0; segue parábola com erro finito.

**Obs:** nos exemplos dá pra ver o tipo direto no denominador de $G(s)$: sem $s$ isolado → tipo 0 (Exemplo 1 das constantes); com $s$ → tipo 1 (Exemplo 2 das constantes); com $s^2$ → tipo 2 (item B do exercício de G(s)).

#### Passos (dada uma especificação, ex.: "$K_p = X$"):
1. Considerar o sistema **estável** (as constantes só fazem sentido em sistema estável).
2. Ver **qual constante** foi dada com valor finito → isso dá o **tipo** (tabela acima).
3. A constante dada também diz a **entrada de teste**: $K_p$ → degrau, $K_v$ → rampa, $K_a$ → parábola.
4. Calcular o **erro por unidade** da entrada: $\frac{1}{1+K_p}$, $\frac{1}{K_v}$ ou $\frac{1}{K_a}$.
5. Se pedirem as outras: as constantes antes da dada são $\infty$ (erro 0) e as depois são $0$ (erro $\infty$).

#### Exemplo:
Que informações estão contidas na especificação $K_p = 1000$?

**1.** O sistema é estável.

**2.** $K_p$ é finito → **Tipo 0**, porque só o Tipo 0 tem $K_p$ finito. Tipos 1 e 2 têm $K_p=\infty$.

**3.** Foi dado $K_p$ → a entrada de teste é um **degrau**.

**4.** Erro por unidade do degrau:

$$e(\infty)=\frac{1}{1+K_p}=\frac{1}{1+1000}=\frac{1}{1001}$$

**5.** Como é Tipo 0: $K_v=0$ e $K_a=0$ → erro $\infty$ para rampa e parábola.

#### Exercício 1:
Sistema com realimentação unitária e função de transferência à frente:

### $$G(s)=\frac{1000(s-8)}{(s+7)(s+9)}$$

**a.** Determinar o tipo do sistema, $K_p$, $K_v$ e $K_a$.
**b.** Usar o item **a** para achar os erros para degrau, rampa e parábola.

**Resposta:**
- **a.** O sistema em malha fechada é estável. Tipo 0, com $K_p=127$, $K_v=0$ e $K_a=0$.
- **b.** $e_{degrau}(\infty)=7{,}8\times10^{-3}$, $e_{rampa}(\infty)=\infty$, $e_{parábola}(\infty)=\infty$.

Leitura: $K_p$ finito e $K_v=K_a=0$ → Tipo 0. Erro no degrau: $\frac{1}{1+127}\approx7{,}8\times10^{-3}$.

**Obs:** com $(s-8)$ no numerador a conta dá $K_p=\frac{1000\cdot(-8)}{7\cdot9}\approx-127$ e a malha fechada fica instável. A resposta bate com $(s+8)$.

#### Exercício 2:
Determinar $K$ para ter um erro de 10% em regime permanente:

### $$G(s)=\frac{K(s+5)}{s(s+6)(s+7)(s+8)}$$

**Leitura:** tem um $s$ no denominador → Tipo 1 → o erro finito é o da **rampa** → usa $K_v$.

$$e(\infty)=\frac{1}{K_v}=0{,}1 \quad\rightarrow\quad K_v=10$$

$$K_v=\lim_{s\to0}sG(s)=\frac{5K}{6\cdot7\cdot8}=10$$

$$K=672$$

Aplicando Routh-Hurwitz, o sistema é estável com esse ganho.


## Exercício (faixa de K):
Sistema com realimentação unitária e função de transferência à frente:

$$G(s)=\frac{K(s+20)}{s(s+2)(s+3)}$$

Determinar a faixa de valores de $K$ que torna o sistema estável.

**Resposta:** $0 < K < 2$


## Usando o MATLAB:
Testar a estabilidade, calcular as constantes de erro estático e os erros (Exemplo 2 das constantes):

```matlab
numg=500*poly([-2 -5 -6]);      % numerador de G(s)
deng=poly([0 -8 -10 -12]);      % denominador de G(s)
G=tf(numg,deng);                % cria G(s)

T=feedback(G,1);                % cria T(s)
polos=pole(T)                   % polos em malha fechada (estabilidade)

Kp=dcgain(G)                    % Kp = G(s) para s=0
erp=1/(1+Kp)                    % erro para degrau

numsg=conv([1 0],numg);         % numerador de sG(s)
densg=poly([0 -8 -10 -12]);     % denominador de sG(s)
sG=tf(numsg,densg);
sG=minreal(sG);                 % cancela o s em comum
Kv=dcgain(sG)                   % Kv = sG(s) para s=0
erp=1/Kv                        % erro para rampa

nums2g=conv([1 0 0],numg);      % numerador de s^2G(s)
dens2g=poly([-8 -10 -12]);      % denominador de s^2G(s)
s2G=tf(nums2g,dens2g);
s2G=minreal(s2G);               % cancela o s em comum
Ka=dcgain(s2G)                  % Ka = s^2G(s) para s=0
erp=1/Ka                        % erro para parábola
```


## Resumo:

**Calcular o erro:** verifica estabilidade → pega $R(s)$ → $e(\infty)=\lim\limits_{s\to0}\frac{sR(s)}{1+G(s)}$ → limite.

**Constantes:** $K_p=\lim G$ (degrau), $K_v=\lim sG$ (rampa), $K_a=\lim s^2G$ (parábola). Maior constante → menor erro.

**Interpretar:** constante finita → tipo ($K_p$ → 0, $K_v$ → 1, $K_a$ → 2) → entrada de teste → erro por unidade. Antes da finita: $\infty$ (erro 0). Depois: 0 (erro $\infty$).
