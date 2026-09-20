
## 1. Definição:

→ Sistemas de controle consiste em processos e subsistemas construídos com o objetivo de se conseguir uma saída desejada com um desempenho desejado, dado uma entrada especificada.

![[Pasted image 20260914011405.png]]

Averiguar se a saída é a resposta esperada, baseado na entrada fornecida.


## 2. Tipos de sistema:

### Malha aberta:

→ Sistema de controle que **não verifica o resultado da saída.** A ação de controle acontece sem comparar o resultado obtido com o desejado. 
**Exemplo:** Micro-ondas funcionando por tempo programado.

### Malha fechada:

→ Sistemas de controle que usam **realimentação.** A saída é medida e comparada com o valor desejado, permitindo corrigir erros automaticamente. 
**Exemplo:** ar condicionado mantendo uma temperatura definida.

**Resumindo:** Malha aberta não corrige a saída. Malha fechada mede e corrige.


## 3. Exemplo do elevador:

Dado um elevador, ao entrar nele e selecionar o andar 4 (saída desejada), estando no andar 1, ao analisar o gráfico de desempenho do sistema, temos algo assim:

![[Pasted image 20260914012657.png]]

**Sendo:**
- 4: a saída desejada / valor de referência.
- 1: posição inicial do elevador.
- Resposta transitória: resposta que o sistema demora para chegar na saída desejada.
- Resposta em regime permanente: quando o sistema conseguiu chegar na saída desejada. (saída estabilizada).
- Erro em regime permanente: comparação entre a saída desejada e a saída obtida (estabilizada).

**Dependendo do tipo de aplicação:** é preciso uma resposta transitória mais rápida ou mais lenta, levando em consideração fatores como estabilidade, conforto e segurança.

**Erro do sistema:** valores de **±2% ou ±5%** em torno da resposta final são frequentemente utilizados para determinar quando o sistema entrou em regime permanente.


## 4. Sistema em malha aberta:

→ Não realiza compensação para quaisquer perturbações.
→ Sistema não realiza correções
→ Comandados simplesmente pela entrada.

![[Pasted image 20260914014243.png]]

→ As perturbações influenciam na saída, porem para sistemas de malha aberta, elas não são corrigidas pelo próprio sistema.

→ São sistemas mais baratos de se produzir.


## 5. Sistema em malha fechada (controle com realimentação).

→ Possuem maior exatidão.
→ São sistemas menos sensíveis a ruídos, perturbações e alterações do ambiente.
→ Resposta transitória e erro em regime permanente podem ser controlados.
→ São sistemas mais complexos e mais caros.

![[Pasted image 20260914014740.png]]


## 6. Processo de análise de um sistema de controle.

**Objetivos de análise:**
1. Resposta transitória
2. Resposta em regime permanente e erro.
3. Estabilidade

**Importante:** antes de analisar o desempenho do sistema, é necessário verificar se ele é **estável**. Caso o sistema seja instável, a resposta pode crescer indefinidamente ou apresentar oscilações que não se estabilizam, tornando pouco relevantes as análises de resposta transitória e erro em regime permanente.


## 7. Processo do projeto:

1. Definir o sistema físico e seus requisitos.
2. Criar um diagrama de blocos funcional.
3. Representar o sistema em um esquema.
4. Desenvolver o modelo matemático.
5. Simplificar/reduzir o diagrama de blocos.
6. Analisar, projetar e testar o sistema.


## 8. Estudo da Antena

→ Controle do azimute de uma antena!
→ Potenciômetro que controla toda a estrutura física da antena.

![[Pasted image 20260914021417.png]]

### Diagrama de blocos:

![[Pasted image 20260914021445.png]]


### 2 Respostas para o controle do sistema

![[Pasted image 20260914021643.png]]

**Saída 1:**
- Saída com ganho elevado

**Saída 2:**
- Saída com ganho elevado
- Leva menos tempo para estabilizar
- Sistema mais suave

## 9. Tabela com formas de onda de teste

**Objetivo:** Jogar um sinal conhecido no sistema para analisar a saída.

![[Pasted image 20260914022411.png]]


## 10. Resposta no domínio do tempo

### Função de transferência

**Definição:** é a razão entre as transformadas de Laplace da saída e da entrada do sistema. Considerando as condições iniciais nulas.

![[Pasted image 20260914022710.png]]

### $$G(s)=\frac{Y(S)}{F(S)}$$
### Polos de uma função de transferência: (Nomenclatura: X)
→ São os valores da variável da transformada de Laplace (s), que fazem com que a função de transferência se torna infinita.
→ São os valores de \(s\) que fazem o **denominador** da função de transferência ser igual a zero.
**Exemplo:**

### $$G(s)=\frac{2}{s+3}$$
**Encontrando o polo:**

s+3 = 0
s = -3

**Portanto:**
- O sistema possui um polo em s = -3
- Os polos estão diretamente ligados ao comportamento e à estabilidade do sistema.

### Zeros de uma função de transferência: (Nomenclatura: O)
→ São os valores da variável da transformada de Laplace (s), que fazem com que a função de transferência se torne zero.
→ São os valores de \(s\) que fazem o **numerador** da função de transferência ser igual a zero.

**Exemplo:**

### $$G(s)=\frac{s+2}{s+5}$$
**Encontrando o zero:**

s + 2 = 0
s = -2

**Portanto:**
- O sistema possui um zero em s = -2
- Os zeros influenciam principalmente a forma como o sistema responde à entrada.

### Resumindo:

### $$G(s)=\frac{\color{green}{s+2}}{\color{orange}{s+5}}$$
**Zero:** vem do numerador → s = -2
**Polo:** vem do denominador → s = -5


---

## Exemplo:

![[Pasted image 20260914025003.png]]

Dado o seguinte sistema:

### $$G(s)=\frac{s+2}{s+5}$$
**Entrada:** (entrada degrau)

### $$R(s)=\frac{1}{s}$$
**Função de transferência:**

### $$G(s)=\frac{C(s)}{R(s)}$$

### Primeira etapa: Achar os zeros e polos!

#### 1. Zero do sistema:

s + 2 = 0
s = -2
Zero (O) = -2
#### 2. Polo do sistema:

s + 5 = 0
s = -5
Polo (X) = -5


### Montando a  saída do sistema:

### $$C(s)=R(s)G(s)$$

**Portanto:**

### $$C(s) = \frac{1}{s} * \frac{s+2}{s+5}$$
### $$C(s) = \frac{s+2}{s(s+5)}$$

**Análise:**
- A expressão da saída tem 2 polos:
**s = 0**
**s=-5**

- A expressão da saída tem 1 zero.
**s=-2**

![[Pasted image 20260914025827.png]]


### 3. Converter a saída para o domínio do tempo:

- Resolver por frações parciais:

### $$\frac{s+2}{s(s+5)}=\frac{\frac{2}{5}}{s}+\frac{\frac{3}{5}}{s+5}$$
- Aplicando a transformada inversa de Laplace:

### $$c(t)=\frac{2}{5}+\frac{3}{5}*e^{-5t}$$

### 4. Análise da resposta:

![[Pasted image 20260914030318.png]]

**Interpretação:** o zero \(s=-2\) e o polo \(s=-5\) pertencem ao sistema \(G(s)\). Ao aplicar uma entrada degrau \(R(s)=1/s\), surge também um polo em \(s=0\) na expressão da saída \(C(s)\). O polo \(s=-5\) produz o termo transitório \(e^{-5t}\), que desaparece ao longo do tempo.


### Polos da entrada x polos do sistema

**Ao analisar a saída C(s):**

→ Os polos provenientes da entrada geram a resposta forçada.
→ Para uma entrada degrau, o polo em s = 0 gera a parte constante da resposta, associada ao regime permanente.

→ Os polos provenientes do sistema geram a resposta natural.
→ A resposta natural corresponde à resposta transitória e desaparece ao longo do tempo em sistemas estáveis.

**Resumindo:**

Polo da entrada → resposta forçada → regime permanente
Polos do sistema → resposta natural → resposta transitória



## Frações parciais:

![[Pasted image 20260917144119.png]]

![[Pasted image 20260917144201.png]]
