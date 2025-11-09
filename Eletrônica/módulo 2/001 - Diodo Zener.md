
## Regulação de tensão

**Revisando o divisor de tensão:**

→ Circuito usado para reduzir a tensão com relação a uma entrada.

![[Pasted image 20251016093052.png]]


**Problema:** O circuito somente divide a tensão em um valor proporcional a entrada. Se a tensão de entrada variar, a tensão de saída também vai variar.

**Solução:** Um componente que consiga regular a tensão e entregar um valor **fixo** mesmo com a variação da entrada. Desde que a tensão de entrada seja superior a tensão de saída.


## Diodo Zener

**Polarização reversa:**

![[Pasted image 20251109181224.png]]
**Comportamento:**

→ **Tensão de polarização reversa inferior à tensão do diodo Zener (Vz):** o diodo se comporta como um circuito aberto e a tensão de saída será igual a entrada.

→ **Tensão de polarização reversa superior à tensão do diodo Zener (Vz):** o diodo entra em condução e se comporta como uma fonte de tensão Vz. Tensão de saída igual a Vz e a tensão excedente fica no resistor.

#### Gráfico:

![[Pasted image 20251016095143.png]]


#### Características:

→ A tensão de Zener (Vz) é um valor próximo da região de ruptura, ela pode ser dimensionada com maior flexibilidade. Ela é um parâmetro que depende do modelo.

![[Pasted image 20251016095651.png]]

→ Qualquer modelo de diodo Zener suporta um nível máximo de potência, isso implica que para “manter” uma tensão Vz, existe um limite de corrente suportável pelo diodo Zener.

![[Pasted image 20251016095839.png]]

#### Utilidade:

→ Diodos Zener podem ser usados para circuitos de proteção contra surtos de tensão.
→ A tensão de saída é limitada pela tensão de Zener.

![[Pasted image 20251016095948.png]]


### Transient Voltage Suppression(Transorb) :

→ Uma variação do diodo Zener, usado para proteção contra surtos de tensão.
→ Pode ser fabricado de forma bidirecional, permitindo limitar a tensão positiva e negativa de uma fonte de corrente alternada.


![[Pasted image 20251016100329.png]]
