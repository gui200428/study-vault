#faculdade #resumos #formulario #calc_dif
# Resumo de Cálculo Diferencial e Integral 2

## 1. Integrais

### 1.1. Integrais Indefinidas (Primitivas)

→ Quando a integral não possui os limites de integração definidos, nesse caso colocamos o resultado somado da **Constante (C)**, também chamada de constante de integração.

#### Regras básicas:
→ Sempre colocar a constante "C" no final, representando a família de todas as primitivas possíveis
Para $n$ inteiro diferente de $-1$ (Regra da Potência):
$$
\int x^n \, dx = \frac{x^{n+1}}{n+1} + C
$$

**Exemplo:**
$$
\int x^2 \, dx = \frac{x^{2+1}}{2+1} + C = \frac{x^3}{3}+C
$$

**Integrais básicas fundamentais:**
1.  **Função Logarítmica Natural**:

    $$ \int \frac{1}{x} \, dx = \ln|x| + C \quad (x \neq 0) $$

2. **Função Exponencial Base e**: 
   $$\int e^x \, dx = e^x + C$$
3. **Função Exponencial com Coeficiente** (Regra do coeficiente exponencial): 
   $$\int e^{ax} dx = \frac{1}{a}e^{ax} + C$$
   **Exemplo**: $$\int e^{3x} dx = \frac{1}{3}e^{3x} + C$$
4. **Função Cosseno** (Primitiva do cosseno): 
   $$\int \cos\, x\, dx = \sin\,x + C$$
5. **Função Seno** (Primitiva do seno): 
   $$\int \sin\, x\, dx = -\cos\,x + C$$

#### Propriedades da Integração (Linearidade da Integral)

1. **Propriedade Aditiva**: 
   $$\int [f(x) + g(x)] \, dx = \int f(x) \, dx + \int g(x) \, dx$$
2. **Propriedade Subtrativa**: 
   $$\int [f(x) - g(x)] \, dx = \int f(x) \, dx - \int g(x) \, dx$$
3. **Propriedade Multiplicativa por Constante**: 
   $$\int c \cdot f(x) \, dx = c \int f(x) \, dx$$
4. **Integral da Função Nula**: 
   $$\int 0 \, dx = C$$ (onde $C$ é uma constante)

### 1.2. Integral Definida (Teorema Fundamental do Cálculo)

A integral definida segue as mesmas regras de cálculo da integral indefinida, porém:
- Em vez de adicionar $+C$, colocam-se os limites de integração.
- Aplica-se o **Teorema Fundamental do Cálculo**: Substitui-se o valor encontrado para cada limite e subtrai-se o valor inferior do valor superior.

**Notação de Barras de Avaliação**: 
$$\int_{a}^{b} f(x)\,dx = \left[ F(x) \right]_{a}^{b} = F(b) - F(a)$$

**Exemplo**:
$$
\int_{2}^{3} e^{3x} \, dx 
= \left[ \frac{e^{3x}}{3} \right]_{2}^{3}
= \frac{e^{9}}{3} - \frac{e^{6}}{3}.
$$

---

## 2. Integração por Partes (Fórmula de Integração por Produto)
→ Famoso chama X de U, e substitui depois :D
→ Esta técnica é ideal para produtos de funções, especialmente quando uma função multiplica outra que seria fácil de integrar.

A **fórmula** de integração por partes (derivada da regra do produto) é:
$$
\int u \, dv = uv - \int v \, du.
$$

**Mnemônico para escolha de u e dv**: ILATE (Inversa, Logarítmica, Algébrica, Trigonométrica, Exponencial)
- Escolha u seguindo a ordem: I → L → A → T → E
- Escolha dv seguindo a ordem inversa: E → T → A → L → I

**Passos**:
1. Escolher quem será $u$ e quem será $dv$.
2. Calcular $du$ **derivando** $u$.
3. **Integrar** $dv$ para encontrar $v$.
4. Aplicar a fórmula: $$\int u \, dv = uv - \int v \, du.$$ 

### Exemplos:

#### (a) $$\int x e^x \, dx$$ (Produto de função algébrica e exponencial)
- Escolha: $u = x$ (função algébrica), então $du = dx$.
- Escolha: $dv = e^x dx$ (função exponencial), então $v = e^x$.
Aplicando a fórmula:
$$
\int x e^x \, dx 
= x e^x - \int e^x \, dx 
= x e^x - e^x + C 
= e^x (x - 1) + C.
$$
![[Pasted image 20250219155520.png]]

#### (b) $$\int \ln(x) \, dx$$ (Função logarítmica)
- Escolha: $u = \ln(x)$ (função logarítmica), então $du = \frac{1}{x} \, dx$.
- Escolha: $dv = dx$ (função mais simples), então $v = x$.
Aplicando a fórmula:
$$
\int \ln(x) \, dx 
= x \ln(x) - \int x \cdot \frac{1}{x} \, dx 
= x \ln(x) - \int 1 \, dx 
= x \ln(x) - x + C.
$$
![[Pasted image 20250219155634.png]]

#### (C) $$\int xe^{3x} \, dx$$ (Produto de função algébrica e exponencial com coeficiente)
![[Pasted image 20250219160123.png]]

#### (D) $$\int 2x^{2} e^{-x} \, dx$$ (Aplicação de integração por partes repetida)
→ Dupla integração por partes:
![[Pasted image 20250219160402.png]]

---

## 3. Integração por Frações Parciais (Decomposição em Frações Parciais)

Usada em casos de frações racionais (polinômio sobre polinômio) onde podemos decompor a fração em parcelas mais simples. Este método é aplicável quando o grau do numerador é menor que o grau do denominador (fração própria).

**Tipos de decomposição:**
1. **Fatores Lineares Distintos**: $(x-a)(x-b)...$, usamos $\frac{A}{x-a} + \frac{B}{x-b} + ...$
2. **Fatores Lineares Repetidos**: $(x-a)^n$, usamos $\frac{A_1}{x-a} + \frac{A_2}{(x-a)^2} + ... + \frac{A_n}{(x-a)^n}$
3. **Fatores Quadráticos Irredutíveis**: $(x^2+px+q)$, usamos $\frac{Ax+B}{x^2+px+q}$

### Exemplo (Caso de fatores lineares distintos)

$$\int \frac{3x}{x^2 - 3x + 2} \, dx.$$

1. **Achar as raízes do polinômio** (Fatoração do denominador):
   $$\Delta = 9-8 = 1; \; x_1=2; \; x_2=1$$

2. **Reescrever a integral com o polinômio fatorado:**
$$\int \frac{3x}{(x-2)(x-1)} \, dx$$

3. **Aplicar o método das frações parciais** (Encontrar forma decomposta):
   $$\frac{3x}{(x - 2)(x - 1)} = \frac{A}{x - 2} + \frac{B}{x - 1}$$

4. **Igualar ao MMC** (Método do Mínimo Múltiplo Comum):
   $$\frac{A(x-1)+B(x-2)}{(x - 2)(x - 1)} = \frac{Ax-A+Bx-2B}{(x - 2)(x - 1)}$$

5. **Agrupar os termos** (Fração parcial encontrada!):
   $$\frac{x(A+B)-A-2B}{(x - 2)(x - 1)}$$

6. **Montar o sistema de equações** (Método dos coeficientes indeterminados):
   $$\frac{3x}{(x - 2)(x - 1)} = \frac{x(A+B)-A-2B}{(x - 2)(x - 1)}$$
  
  $$\begin{cases}A + B = 3 \quad \text{(coeficiente de x)} \\-A - 2B = 0\quad \text{(termo independente)}\end{cases}\quad\Longrightarrow\quad A = 6, \quad B = -3$$

7. **Retornar na integral e substituir A e B**:
   $$\int \frac{A}{x - 2} + \frac{B}{x - 1}$$
   
 $$\int \frac{6}{(x - 2)} + \frac{-3}{(x - 1)}$$
$$\int \frac{6}{(x - 2)} +  \int \frac{-3}{(x - 1)}$$
$$6\int \frac{1}{(x - 2)}dx +  (-3\int \frac{1}{(x - 1)}dx)$$

8. **Resolver as integrais** usando a fórmula da integral logarítmica:
→ Lembrando que:
$$\int \frac{1}{x}dx=\ln|x|+C$$
$$\int \frac{1}{x-a}dx=\ln|x-a|+C \quad \text{(Substituição u = x-a)}$$

![[Pasted image 20250219163258.png]]

## 4. Outras Técnicas de Integração Importantes (Complemento)

### 4.1 Substituição Trigonométrica
Útil para integrais com radicais do tipo $\sqrt{a^2-x^2}$, $\sqrt{a^2+x^2}$ ou $\sqrt{x^2-a^2}$.

### 4.2 Método da Substituição (Mudança de Variável)
**Regra**: Se $u = g(x)$, então:
$$\int f(g(x))g'(x)dx = \int f(u)du$$

### 4.3 Integrais Trigonométricas Básicas
$$\int \tan x \, dx = -\ln|\cos x| + C = \ln|\sec x| + C$$
$$\int \cot x \, dx = \ln|\sin x| + C$$
$$\int \sec x \, dx = \ln|\sec x + \tan x| + C$$
$$\int \csc x \, dx = \ln|\csc x - \cot x| + C$$

---

## 5. Aplicações das Integrais

### 5.1 Cálculo de Áreas
Para área entre uma curva $y = f(x)$ e o eixo $x$ no intervalo $[a,b]$:
$$A = \int_a^b f(x) \, dx$$

### 5.2 Cálculo de Volumes
Volume de sólido de revolução (método dos discos):
$$V = \pi\int_a^b [f(x)]^2 \, dx$$

### 5.3 Comprimento de Arco
$$L = \int_a^b \sqrt{1 + [f'(x)]^2} \, dx$$

---
