
## Amplificador com polarização da base

- Com o transistor polarizado com o ponto Q no centro da reta de carga
- Possível acoplar uma tensão de corrente alternada CA de baixo valor na base.
- **Resultado:** Produzir uma tensão de corrente alternada CA no coletor.
- **Tensão no coletor tem o mesmo formato da tensão CA da base. POREM AMPLIFICADA**

### Capacitor de acoplamento
- Circuito simples com uma fonte CA, um capacitor e um resistor

![[Pasted image 20260523184929.png]]

O capacitor bloqueia o sinal de corrente continua e transmite o sinal de corrente alternada.

**Capacitor de acoplamento:**
- Acopla (transmite) o sinal CA para o resistor
- Permite acoplar um sinal de CA em um amplificador sem alterar o ponto Q.

**Funcionamento adequado:**
- Reatância deve ser menor que a resistência na frequência mais baixa da fonte CA.
- Ex: frequência da fonte CA variar 20hz a 20khz. ← Capacitor com reatância a 20hz deve ser menor que a resistência.

### Projeto do Acoplamento 

#### $$X_c<0.1*R$$
- Reatância deve ser 10x menor que a resistência na menor frequência de operação.
- Quando a regra é satisfeita: 
**Curto nos capacitores!**

![[Pasted image 20260523185741.png]]

### Conclusões e aproximações:

- Capacitores de acoplamento são aproximados para um curto em CA
- tensão de CC possui frequência zero, a reatância de um capacitor de acoplamento é infinita com essa frequência.

**Aproximações:**
- Análise CC → Capacitor atua como chave aberta
- Análise de CA → capacitor atua como chave fechada

![[Pasted image 20260523190100.png]]


### Dimensionamento do capacitor:

### $$C=\frac{1}{2 \pi fX_c}$$
### $$X_c<0,1R$$ (Em 20hz)


---
## Exemplo:

![[Pasted image 20260523190425.png]]

![[Pasted image 20260523190435.png]]
