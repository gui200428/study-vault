#faculdade #resumos #eletronica 
## Definição:

→ Conversão de energia radiante em energia elétrica.
Aplicações:
1- Sensoriamento: Medir a irradiância de um ambiente
2- Geração de energia: aplicação em potência, converter o máximo de energia radiante em energia elétrica.

**Para estas aplicações, é usado o fotodiodo!**


## Funcionamento:

→ Deve ser implementado na **polarização reversa**
→ Quando não está submetido à uma certa potência radiante, não existe corrente que passa pelo circuito
→ Quando submetido à uma potência radiante, a **corrente de saturação reversa** aumenta e se torna um valor relevante.
→ Transdutor que relaciona as duas grandezas físicas com uma resposta linear.

![[Pasted image 20251028165722.png]]


## Capacidades:

→ Pode medir a potência radiante (W) ou a irradiância ($W/m^2$) de um ambiente.

![[Pasted image 20251028170823.png]]



---

## Resumo melhor:

### Itens:

**Potencia radiante (P):** Quantidade total de energia (W) que atinge a superfície do sensor.
→ **Unidade:** $W$
**Irradiância (E):** Densidade da potência radiante, a potência dividida pela área.
→ **Unidade:** $W/m^2$
### $$E = \frac{P_{rad}}{A}$$

### Função do fotodiodo
→ Transdutor que transforma **potencia radiante** que atinge o sensor em uma corrente elétrica.

### Sensibilidade
→ É a sensibilidade que o sensor possui
**Unidade:** $A/W$
### $$S = \frac{i}{P_{rad}}$$
**Sendo:**
$i$ = fotocorrente - a corrente gerada pelo fotodiodo (A)
Prad = potencia radiante. (W)


## Para exercícios:

→ Na maior parte dos exercicios, não é fornecido a potência radiante (P), mas a irradiância (E) e a área (A). Podemos relacionar a fórmula da sensibilidade com a fórmula da potencia radiante

#### Formula 1:

### $$i = S * P_{rad}$$
#### Formula 2:

### $$P_{rad} = E * A$$
#### Resultado:

### $$i = S * E * A$$
**Sendo:**
i = fotocorrente (A)
S = sensibilidade do sensor (A/W)
E = irradiância ($W/m^2$)
A = área do sensor ($m^2$)

**IMPORTANTE:** A maior parte dos exercícios da a área em $mm^2$, é preciso converter para $m^2$

### $$1 mm^2 = 1*10^{-6} m^2$$

## Relação dos circuitos:

Microcontroladores leem tensão e não fotocorrente, para isso é usado um resistor para converter a fotocorrente em uma tensão de saída.

### $$V_{saida} = R*i$$

→ O diodo trabalha na posição reversa. Isso permite que a corrente aumente com a luz.
→ Dependência de cor (λ): a sensibilidade (S) muda drasticamente dependendo do comprimento de onda (cor) da luz. Uma sensibilidade de 0,88 A/W para 480 nm(azul), não é a mesma para uma luz vermelha.

→ **Corrente de escuro:** Uma pequena corrente que aparece quando não se tem luz.


---
### Próximo conteúdo:

