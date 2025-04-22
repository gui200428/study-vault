#faculdade #resumos #formulario #circuitos
# Resumo de Circuitos Elétricos

Este documento reúne definições, leis e exemplos sobre circuitos elétricos, incluindo conceitos de carga, corrente, tensão, potência, resistência, leis de Kirchhoff, tipos de fontes e associações de resistores.

---

## 1. Grandezas Fundamentais

### 1.1 Carga (q)
- Unidade: Coulomb (C)  
- Define a quantidade de eletricidade.
$$
q(t) = \int_{t_0}^{t} i\;dt 
$$

### 1.2 Corrente (i)
- Unidade: Ampère (A)  
- Definição: Representa a taxa de variação da carga elétrica ao longo do tempo.
 $$
i = \frac{dq}{dt}
$$
### 1.3 Tensão (V) → (DDP)
- Unidade: Volt (V)  
- Definição:  É a diferença de potencial elétrico entre dois pontos.
- Fórmula básica quando existe **resistência**: 
$$V = R \cdot i$$
 - Outras formas de achar a tensão, quando temos o **trabalho**:
 1. Por derivada:
$$V = \frac{dW}{dq}$$
2. Por variação:
$$\Delta V = \frac{\Delta W}{\Delta q}$$
### 1.4 Potência (P)
- Unidade: Watt (W)  
- Definição: é a velocidade que se consome ou absorve energia.
- Para qualquer circuito: a somatória de potencias fornecidas e absorvidas é igual a 0.
- **Fórmulas**:

1. Corrente por tensão:
$$P = i \cdot V$$
2. Derivada do trabalho em função do tempo:
$$P = \frac{dW}{dt}$$
1. **Potência dissipada por um resistor (consumida)**:
  - Quando se tem a corrente (i):
  $$P = i^2 \cdot R$$

- Quando se tem a tensão (V):
$$P = \frac{V^2}{R}$$

### 1.5 Resistência (R)
- Unidade: Ohm ($\Omega$)  
### 1.6 Leis de Ohm
- **Primeira lei de ohm**:
- Relação fundamental:  
  $V = R \cdot i \quad \Longleftrightarrow \quad R = \frac{V}{i}$

- **Segunda lei de ohm**:
- Cálculo da resistência de objetos cilíndricos (fio/condutor):
$$R = \rho \,\frac{L}{A}$$
  onde:
  - $\rho$ é a resistividade do material,
  - $L$ é o comprimento do condutor,
  - $A$ é a área da seção transversal.

- Cálculo da resistência de objetos não cilíndricos:
$$R = \int_{0}^{l} \,\frac{\rho}{A(l)}$$

---

## 2. Associação de Resistores

### 2.1 Resistores em Série
- Resistência Equivalente:  
  $$R_\text{eq} = R_1 + R_2 + \cdots + R_n$$
- A mesma corrente percorre todos os resistores, mas a tensão se divide.
- Características:
  - Tensão se divide
  - Corrente igual em todos os resistores

### 2.2 Resistores em Paralelo
- Resistência Equivalente:  
  $$\frac{1}{R_\text{eq}} = \frac{1}{R_1} + \frac{1}{R_2} + \cdots + \frac{1}{R_n}$$
- **Para resistores de mesmo valor:** $$R_\text{eq} = \frac{R}{n}$$ 
- A tensão é a mesma em todos os ramos, mas a corrente se divide.
- Características:
  - Tensão igual em todos os ramos
  - Corrente se divide

### 2.3 Linearidade
- Proporcional à tensão e corrente
- Gradiente constante

---

## 3. Tipos de Fontes

### 3.1 Fontes Ideais
- **Fonte de Tensão Constante**: Mantém tensão fixa independente da corrente (idealmente).
- **Fonte de Corrente Constante**: Fornece uma corrente fixa independente da tensão (idealmente).
- **Fonte Alternada**: Varia a tensão (e corrente) no tempo, geralmente de forma senoidal.

### 3.2 Fontes Reais
- **Fonte de tensão real**: $V = V_0 + R_i \cdot i$ (onde $R_i$ é a resistência interna)
- **Fonte de corrente real**: Melhor $R_i$ alto

### 3.3 Transformação de Fontes
- Fonte de tensão para fonte de corrente: $i = \frac{V}{R}$
- Fonte de corrente para fonte de tensão: $V = R \cdot i$

### 3.4 Associação de Fontes
- **Fontes de tensão em série**: Somar tensões
- **Fontes de tensão em paralelo**: Requer resistências internas iguais
- **Fontes de corrente em paralelo**: Somar correntes
- **Fontes de corrente em série**: Requer resistências internas iguais

---

## 4. Leis de Kirchhoff

### 4.1 LKC (Lei das Correntes)
- Em um nó de um circuito, a soma das correntes que entram é igual à soma das correntes que saem:
  $\sum i_\text{entrada} = \sum i_\text{saída} \quad \Longrightarrow \quad \sum i = 0$

### 4.2 LKT (Lei das Tensões)
- Em qualquer malha fechada de um circuito, a soma algébrica das tensões é zero:
  $\sum V = 0$

### 4.3 Aplicação em Circuitos
- Para aplicar LKC: Selecione nós estratégicos
- Para aplicar LKT: Selecione malhas independentes
- Convenção: Define-se uma direção de percurso para cada malha

---

## 5. Divisor de Tensão (Série)
Em um circuito em série, a tensão total $V_\text{T}$ se divide proporcionalmente às resistências:

$V_1 = \frac{R_1}{R_1 + R_2 + \cdots + R_n} \cdot V_\text{T}$
$V_2 = \frac{R_2}{R_1 + R_2 + \cdots + R_n} \cdot V_\text{T}$
$\dots$

### 5.1 Contribuições de Fontes
- **Para fontes de tensão**: Aplicar contribuição de cada fonte separadamente e somar
- **Para fontes de corrente**: Calcular tensão em cada resistor

---

## 6. Divisor de Corrente (Paralelo)
Em um circuito em paralelo, a corrente total $i_\text{T}$ se divide entre os ramos proporcionalmente ao inverso das resistências:

$i_1 = \frac{R_\text{eq}}{R_1} \cdot i_\text{T}$
$i_2 = \frac{R_\text{eq}}{R_2} \cdot i_\text{T}$
$\dots$

onde 
$R_\text{eq} = \left( \frac{1}{R_1} + \frac{1}{R_2} + \dots + \frac{1}{R_n} \right)^{-1}$

### 6.1 Aplicações Práticas
- Determinar a corrente em um ramo específico
- Calcular tensão nos terminais a partir da corrente total

---

## 7. Análise de Circuitos Complexos

### 7.1 Método das Malhas
1. Identificar as malhas independentes
2. Aplicar LKT para cada malha
3. Resolver o sistema de equações resultante

### 7.2 Método dos Nós
1. Identificar os nós independentes
2. Aplicar LKC para cada nó
3. Substituir as relações tensão-corrente
4. Resolver o sistema de equações resultante

### 7.3 Circuito Simplificado vs. Circuito Real
- Em circuitos simplificados: $V = R \cdot i$
- Em circuitos reais: Considerar resistências internas das fontes

---

## 8. Exemplos de Cálculo

### 8.1 Exemplo 1: Associação em Série
- **Dados**: Dois resistores em série: $R_1 = 15\,\Omega$ e $R_2 = 5\,\Omega$.
- **a) Resistência Equivalente**  
  $R_\text{eq} = R_1 + R_2 = 15 + 5 = 20\,\Omega$
- **b) Corrente Total** (se houver uma tensão aplicada $V$)  
  $i_\text{eq} = \frac{V}{R_\text{eq}}$
  (Se, por exemplo, $V = 12\,\text{V}$, então $i_\text{eq} = \frac{12}{20} = 0{,}6\,\text{A}$)
- **c) Potência Dissipada**  
  $P_\text{total} = V \cdot i_\text{eq} = i_\text{eq}^2 \cdot R_\text{eq} = \frac{V^2}{R_\text{eq}}$

### 8.2 Exemplo 2: Associação em Paralelo
- **Dados**: Dois resistores em paralelo, cada um de $12\,\Omega$, ligados a uma fonte de $12\,\text{V}$.
- **a) Resistência Equivalente**  
  $\frac{1}{R_\text{eq}} = \frac{1}{12} + \frac{1}{12} = \frac{2}{12} = \frac{1}{6} \quad\Longrightarrow\quad R_\text{eq} = 6\,\Omega$
- **b) Corrente Total**  
  $i_\text{T} = \frac{V_\text{T}}{R_\text{eq}} = \frac{12}{6} = 2\,\text{A}$
- **c) Potência Total**  
  $P_\text{total} = V_\text{T} \cdot i_\text{T} = 12 \times 2 = 24\,\text{W}$

### 8.3 Exemplo 3: Circuito com Fonte de Tensão
- **Dados**: Fonte de 24V com resistores $R_1 = 2\Omega$ e $R_\text{eq} = 20\Omega$
- **a) Calcular corrente**  
  $i = \frac{V}{R_\text{total}} = \frac{24V}{22\Omega} = 1.09A$
- **b) Calcular tensão em $R_\text{eq}$**  
  $V_{R_\text{eq}} = i \cdot R_\text{eq} = 1.09A \cdot 20\Omega = 21.8V$

### 8.4 Exemplo 4: Aplicação LKT
- **Dados**: Circuito com fonte de tensão 24V e resistores
- **Sistema de equações**:
  - $2i_1 + i_c - 2 = 0$
  - $2i_1 - 28.3i_c = 0$
- **Solução**: $i_c = 0.13A$

### 8.5 Exemplo 5: Circuito com Fonte de Corrente
- **Dados**: Fonte de corrente 5A com resistor 10Ω
- **Cálculo de tensão**:
  $V = R \cdot i = 10\Omega \cdot 5A = 50V$

### 8.6 Exemplo 6: Circuito com Fonte de Tensão e Resistores em Paralelo
- **Dados**: Fonte 50V, resistores 10Ω e 50Ω em paralelo
- **Resistência equivalente**:
  $\frac{1}{R_\text{eq}} = \frac{1}{10} + \frac{1}{50} = \frac{5 + 1}{50} = \frac{6}{50} \Rightarrow R_\text{eq} = \frac{50}{6} \approx 8.33\Omega$
- **Corrente total**:
  $i_\text{T} = \frac{V}{R_\text{eq}} = \frac{50V}{8.33\Omega} = 6A$

### 8.7 Exemplo 7: Circuito com Resistores em Paralelo
- **Dados**: Resistores 30Ω, 10Ω, 15Ω em paralelo
- **Resistência equivalente**:
  $\frac{1}{R_\text{eq}} = \frac{1}{30} + \frac{1}{10} + \frac{1}{15} = \frac{1 + 3 + 2}{30} = \frac{6}{30} = \frac{1}{5} \Rightarrow R_\text{eq} = 5\Omega$

### 8.8 Exemplo 8: Transformação de Fonte
- **Dados**: Transformar fonte de tensão 12V com resistor 2Ω
- **Fonte de corrente equivalente**:
  $i = \frac{V}{R} = \frac{12V}{2\Omega} = 6A$

---

## 9. Outras Observações Importantes

### 9.1 Componentes Básicos
- **Condutância (G)**: Inversa da resistência $(G = 1/R)$, medida em Siemens (S).
- **Indutância (L)**: Medida em Henry (H).
- **Capacitância (C)**: Medida em Farad (F).

### 9.2 Considerações Práticas
- **Polaridade e Sentido de Corrente**: Sempre observar o sentido convencional da corrente (do potencial maior para o menor) e a polaridade dos elementos para aplicação correta das Leis de Kirchhoff.
- **Ponto de Potencial**: Escolhe-se normalmente um ponto de referência (terra ou 0 V) para facilitar a análise das tensões no circuito.
- **Análise de Malhas**: Numerar as malhas e aplicar LKT em cada uma.
- **Superposição**: Analisar contribuições separadas de cada fonte.

### 9.3 Efeito de Resistência Interna
- Resistência interna alta em fonte de corrente: melhor desempenho
- Resistência interna baixa em fonte de tensão: melhor desempenho
- Quando $R_i$ é alterado: fonte real de tensão para fonte real de corrente

### 9.4 Cálculo de Alimentação
- **Pilhas em série**: Dividir tensão total pelo valor nominal de cada pilha
- **Fontes em paralelo**: Soma das correntes
- **Transformação de fontes**: Facilita a análise de circuitos complexos

---

## 10. Problemas Práticos e Exercícios

### 10.1 Problema: Cálculo de Corrente
- Circuito com resistor de 1005Ω e fonte de 10V
- Corrente fornecida: $i = \frac{V}{R_\text{eq}} = \frac{10V}{1005\Omega} = 0.00995A$

### 10.2 Problema: Potência
- Calcular quantidade de fontes de corrente 1A em paralelo para fornecer 160W
- $P = R \cdot i^2 = 10\Omega \cdot i^2$
- $160W = 10\Omega \cdot i^2 \Rightarrow i = 4A$
- Número de fontes de 1A necessárias: 4 fontes

### 10.3 Problema: Divisor de Tensão
- Circuito com fonte 15V e resistores $R_2$ e 300Ω em paralelo
- Determinar $R_2$ para que a tensão seja 15V em $R_1$
- Associação em paralelo: $R_\text{eq} = \frac{R_2 \cdot 300}{R_2 + 300}$
- Corrente: $i = \frac{15V}{300 + R_2}$
- Resolvendo: $R_2 = 300\Omega$

---

## 11. Fórmulas Mais Usadas

1. $i = \frac{dq}{dt}$  
2. $V = \frac{dW}{dq}$  
3. $P = \frac{dW}{dt} = i \cdot V = i^2 R = \frac{V^2}{R}$  
4. $R = \rho \,\frac{L}{A}$  
5. $V = R \cdot i$ (Lei de Ohm)  
6. **Série**: $R_\text{eq} = \sum R_i$  
7. **Paralelo**: $\frac{1}{R_\text{eq}} = \sum \frac{1}{R_i}$  
8. **LKC**: $\sum i = 0$ em um nó
9. **LKT**: $\sum V = 0$ em uma malha
10. **Divisor de tensão**: $V_1 = \frac{R_1}{R_1 + R_2} \cdot V_\text{total}$
11. **Divisor de corrente**: $i_1 = \frac{R_\text{eq}}{R_1} \cdot i_\text{total}$

---

### Referencias:
![[p1-r1.jpg]]
![[p1-r2.jpg]]
![[p2-r1.jpg]]![[p2-r2.jpg]]