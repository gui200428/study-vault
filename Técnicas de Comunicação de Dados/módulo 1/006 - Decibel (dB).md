
## Por que usar decibéis?

Em telecomunicações e redes, podemos lidar com diferenças enormes de potência.

Por exemplo, um sinal pode ser:

- 10 vezes maior;
- 1.000 vezes maior;
- 1.000.000 de vezes maior.

Escrever e comparar essas proporções diretamente fica pouco prático.

O **decibel (dB)** resolve isso usando uma **escala logarítmica**.

### Ideia principal

Em vez de representar diferenças enormes com números gigantes, o dB transforma essas proporções em valores bem menores e mais fáceis de comparar.

> **Decibel = forma logarítmica de representar uma relação entre grandezas.**

Isso é muito útil para representar:

- ganho;
- perda;
- atenuação;
- relação sinal-ruído.

### Exemplo intuitivo

Uma diferença de:

**1 para 1.000.000**

é enorme em escala linear.

Em uma escala logarítmica, essa variação pode ser representada de forma muito mais compacta.

## 2. Escala logarítmica do decibel

O decibel usa uma **escala logarítmica**.

Isso significa que grandes variações de potência podem ser representadas por números relativamente pequenos.

Em vez de trabalhar com valores como:

**1 → 10 → 100 → 1.000 → 1.000.000**

o dB representa essas diferenças de forma muito mais compacta.

### Por que isso ajuda?

Porque em telecomunicações os sinais podem sofrer:

- ganhos muito grandes;
- perdas sucessivas;
- atenuações enormes;
- diferenças de potência em várias ordens de grandeza.

A escala em dB torna essas comparações mais fáceis de interpretar e combinar.

> **Ideia principal:** o dB transforma relações multiplicativas muito grandes em uma escala mais compacta e manejável.

**dB serve pra representar diferenças enormes de forma pequena e prática.**

## 3. Fórmula do decibel

Quando estamos comparando **potências**, usamos:

### $$dB = 10 \log_{10}\left(\frac{P_1}{P_2}\right)$$

**Sendo:**
- **\(P_1\)** e **\(P_2\)** são duas potências que queremos comparar;
- a divisão \(P_1/P_2\) cria uma **razão**;
- o logaritmo comprime essa razão;
- o resultado é expresso em **decibéis**.

### Como interpretar

- **0 dB** → as duas potências são iguais;
- **dB positivo** → \(P_1\) é maior que \(P_2\);
- **dB negativo** → \(P_1\) é menor que \(P_2\).

### Ideia principal

> **O dB não diz uma potência sozinho; ele diz quantas vezes uma potência é maior ou menor que outra, usando uma escala logarítmica.**

E esse `10` da fórmula aparece porque aqui estamos comparando **potência**.

Se ele não fez conta em aula, eu não iria além disso. O que vale guardar é:

**razão entre potências → logaritmo → dB**.

## 4. Regra prática dos 3 dB

Quando estamos falando de **potência**:

- **+3 dB ≈ dobro da potência**
- **−3 dB ≈ metade da potência**

Exemplo:

Se um sinal tem potência de **10 mW**:

- +3 dB → aproximadamente **20 mW**
- −3 dB → aproximadamente **5 mW**

### Ideia principal

> **Cada aumento de 3 dB praticamente dobra a potência. Cada redução de 3 dB praticamente corta a potência pela metade.**

Isso é ótimo pra fazer estimativas rápidas sem ficar usando logaritmo toda hora.

### Observação

É uma aproximação, mas bem próxima:

- +3 dB ≈ ×2
- −3 dB ≈ ÷2

![[Pasted image 20260915042409.png]]

## 5. Decibéis na prática
Como o dB usa escala logarítmica, **somar ou subtrair dB corresponde a multiplicar ou dividir a potência**.


![[Pasted image 20260915042522.png]]

### Exemplos
Se um sinal tem potência de **10 mW**:
- +10 dB → **100 mW**
- +3 dB → aproximadamente **20 mW**
- −3 dB → aproximadamente **5 mW**
- −10 dB → **1 mW**

> **Ideia principal:** em dB, mudanças aditivas representam mudanças multiplicativas na potência.

## 6. Decibéis e audição humana

A audição humana consegue perceber uma faixa enorme de intensidades sonoras.

Por isso, o nível sonoro costuma ser representado em **decibéis (dB)**, usando uma escala logarítmica.

Exemplos aproximados:

- **0 dB** → referência próxima ao limiar da audição;
- **50–60 dB** → conversa normal;
- **120 dB** → região próxima ao limiar da dor.

> **Ideia principal:** a escala em dB permite representar uma faixa gigantesca de intensidades com números relativamente pequenos.

### Importante

**0 dB não significa ausência de som.**  
Significa apenas que o nível está igual ao **valor de referência** usado naquela escala.

esse aqui é bem útil porque junta **atenuação + dB + diferença entre meio guiado e espaço livre**.

## 7. Atenuação em meios guiados e no espaço livre

### Meios guiados

Em meios como **cabos e fibras**, o sinal perde potência conforme percorre a distância.

Essa perda costuma ser expressa em:

**dB por unidade de distância**

Exemplo:

**3 dB/km** significa que, a cada quilômetro, o sinal sofre mais 3 dB de atenuação.

> **Em meios guiados, a atenuação costuma crescer com a distância percorrida.**

### Espaço livre

Em transmissões sem fio, a energia da onda se espalha pelo espaço à medida que se afasta da antena.

Por isso, a potência recebida diminui com a distância.

No modelo ideal de espaço livre:

> **quando a distância dobra, a potência recebida cai aproximadamente 6 dB.**

Isso vem do fato de a potência se espalhar por uma área cada vez maior.

### Ideia principal

**Cabo/fibra:** perda acumulada ao longo do meio.  
**Sem fio:** perda principalmente porque a energia se espalha pelo espaço.

## 8. Decibel como linguagem comum

O **decibel (dB)** é usado em várias áreas porque permite representar grandes variações de forma compacta.

Ele pode aparecer em contextos como:

- **som e audição**;
- **ganho e perda de sinal**;
- **atenuação em cabos e fibras**;
- **potência recebida em sistemas sem fio**;
- **relação sinal-ruído**.

A vantagem é que todos esses fenômenos podem ser expressos usando a mesma escala logarítmica.

> **Ideia principal:** o dB é uma forma padronizada de representar relações de ganho, perda e intensidade em sistemas muito diferentes.

