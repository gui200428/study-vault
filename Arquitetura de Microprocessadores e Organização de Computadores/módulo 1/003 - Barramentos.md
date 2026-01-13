#faculdade #aom #resumos 
## Definição:

→ O barramento pode ser definido como um canal de comunicação que interliga os principais componentes do sistema. É composto por diversas trilhas. Cada trilha pode transportar sinais que correspondem a valores binários. 
→ Composto por diversos canais de comunicação ou trilhas.
→ Cada trilha transportam sinais de valores binários 1 e 0.
→ Trilhas do barramento podem transmitir bits ao mesmo tempo em paralelo.

![[Pasted image 20250928173703.png]]

**Barramento do sistema:**
→ Conecta os principais componentes do computador (Processador, memória, e E/S).

**Somente um dispositivo de cada vez pode transmitir/ receber dados pelo barramento**

**Dispositivo de E/S:**
→ Possuem uma interface eletrônica com o barramento **controlador**
→ Gerencia os dispositivos E/S - Acesso do barramento e controle da interface

## Estrutura de barramento

- Barramento de dados
- Barramento de endereçamento
- Barramento de controle

### Barramento de dados:

→ Responsável pela movimentação dos dados entre os módulos do sistema.
→ Movimenta os dados entre os módulos do sistema
→ Podem conter 32/64/128 ou + linhas separadas
→ Cada linha transmite apenas 1 bit por vez
→ Largura do barramento e um parâmetro de desempenho do sistema


### Barramento de endereços

→ Responsável por definir a origem ou destino dos dados. Também é responsável por endereçar portas de entrada e saída.
→ Responsável por designar a origem ou destino dos dados
→ Tamanho determina a capacidade de memória máxima do sistema

**Tamanho do barramento:**

→ Para calcular, basta usar a fórmula:

### $$2^n$$
n= número de bits

![[Pasted image 20250928174739.png]]

**Unidades:**

![[Pasted image 20250928174817.png]]

### Barramento de controle

→ Responsável por controlar o acesso e o uso da linha de dados e endereços.  Transmite dois tipos de sinais: Sinais de comando e sinais de sincronização.
→ **Transmitem 2 tipos de sinais:**
- Comando → especificam operações
- Sincronização → indicam validade dos dados e endereços

## Hierarquia de barramentos múltiplo

→ Muitos dispositivos conectados ao barramento podem prejudicam o desempenho por
duas razões:
- Mais dispositivos → maior tamanho de barramento → atraso no sinal
- Capacidade de transferência de dados do barramentos
Solução → Utilização de múltiplos barramentos

---
### Próximo conteúdo:

[[004 - Portas lógicas]]
