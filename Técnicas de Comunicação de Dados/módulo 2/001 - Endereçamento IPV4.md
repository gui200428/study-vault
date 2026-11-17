
## Introdução:

Para que qualquer dispositivo tenha acesso a internet, o dispositivo precisa ter um endereço rastreável: o endereço IP.

Cada interface conectada recebe um endereço ip. O endereço IP indica em qual rede o dispositivo está.

### IPV4

- O IPV4 é o mais utilizado no mundo
- Esgotado! Não existe mais endereços ip para todos os dispositivos existentes na internet hoje.

→ O IPV4 foi projetado para ser descrito com 32 bits.

Quantidade de endereços possíveis: $2^{32} = 4294967296$ 

$$11111111.11111111.11111111.11111111$$
### Redes privadas:

Prefixos de rede:
192.168.x.x
10.x.x.x
172.x.x.x


**São redes privadas que não acessam a internet por si só. Dependem de um gateway para acessar a internet.**


## Estrutura do endereço IPV4:

- É dividido 4 octetos
- Cada octeto tem 8 bits
- Todos os octetos formam 32 bits.
- Cada octeto vai de 0 a 255.

![[Pasted image 20261114155308.png]]


**Sem um endereço, sem acesso a internet!**


## Analogia com o endereço postal

- O IP pode ser comparado a um endereço postal. Uma parte diz o bairro (rede) e outra diz a casa (host).
- Ajuda a entender quem é a maquina e como chegar até ela.


## Binário e decimal

- Cada parte do octeto vale uma potência de  2.
- Feito em binário para a maquina entender.

![[Pasted image 20261114155932.png]]


## Estrutura do IPV4

- O IPV4 mostra quem é a rede e quem é o dispositivo dentro da rede.

![[Pasted image 20261114160429.png]]

**Definição da rede IP:**
- Exige que o primeiro e o último endereços sejam reservados.

→ **Neste exemplo:**
**Primeiro endereço:** 192.168.10.0 ← Define a própria rede
**Último endereço:** 192.168.10.255 ← Define o broadcast que responde por todos os endereços.
**Endereços dedicados para hosts nesta rede:** $2^{8} - 2 = 254$

**Problema da saturação da rede:** Falta de escalabilidade, só existe 254 endereços disponíveis para hosts nessa rede.


## Exemplo de IP da UNIARA:

Máquina apresenta o IP 10.4.5.18
Notação usada:

**10:** representa que é uma rede privada.
**4:** representa que é a unidade 4
**5:** representa que é o lab 5
**18:** representa que é a máquina 18 do lab


## Máscara de SUB-REDE

- É um número de 32 bits que divide o endereço IP em duas partes: **rede** (bits 1) e host(bits 0).  
- Fazendo a operação AND com os bits do IP e os bits da MÁSCARA, o computador obtém o endereço da **rede** que pertence,

![[Pasted image 20261114162828.png]]

### Uso prático:
O computador usa a máscara para decidir se o **destino está na mesma rede que ele.**
- Se (IP_origem **AND** máscara) == (IP_destino AND máscara), o destino está na mesma rede e o computador entrega direto.
- Se forem diferentes, o destino está em outra rede e ele manda o pacote para o **gateway (roteador).**

### Outro uso:
- A máscara também mostra **quantos endereços cabem na rede**. Os bits **0** são a parte de host, então quanto mais zeros, mais endereços.

$$\underbrace{11111111.11111111.11111111}_{\text{rede (24 bits)}}.\underbrace{00000000}_{\text{host (8 bits)}}$$
**255.255.255.0**

Sobra **1 octeto (8 bits)** para os hosts: 2⁸ = **256 endereços**, de .0 a .255.

Mas só **254 são utilizáveis**, porque dois são reservados:

- **.0**: endereço da **rede**
- **.255**: endereço de **broadcast**



## Notação CIDR

- É uma forma de escrever a máscara de modo abreviado: coloca-se /n depois do IP, onde n é a quantidade de bits 1 da máscara (bits de rede). Os 32 − n bits restantes são de host. Exemplo: 192.168.10.25/24 → máscara 255.255.255.0, com 24 bits de rede e 8 de host.

![[Pasted image 20261114164817.png]]


## Classes de endereço:
Classes de endereço são o modelo antigo de divisão do IPv4, em que a máscara era definida pelo valor do 1º octeto do IP. Classe A (1 a 126) usa máscara /8, classe B (128 a 191) usa /16 e classe C (192 a 223) usa /24. As classes D (multicast) e E (experimental) não são usadas para hosts. O 127 não aparece em nenhuma classe porque é reservado para loopback (127.0.0.1 = a própria máquina). Esse modelo desperdiçava muitos endereços e por isso foi substituído pelo CIDR, que permite qualquer tamanho de máscara.


![[Pasted image 20261114165716.png]]

**Para descobrir a classe, olhe só o primeiro número do IP e veja em qual faixa ele cai.**

Exemplos:  
10.0.0.5 → começa com 10, que está entre 1 e 126 → classe A → máscara 255.0.0.0  
172.16.4.20 → começa com 172, que está entre 128 e 191 → classe B → máscara 255.255.0.0  
192.168.10.25 → começa com 192, que está entre 192 e 223 → classe C → máscara 255.255.255.0

Ou seja, no modelo de classes o próprio IP já dizia qual era a máscara, sem precisar informar ela separadamente.

### Multicast
- Envia a mesma informação de uma vez para um grupo de destinos, e só quem entrou no grupo recebe. É diferente do broadcast, que envia para todos da rede, e do unicast, que envia para um único destino. Usa os endereços da classe D (224.0.0.0 a 239.255.255.255). Exemplos: transmissão de vídeo/IPTV e protocolos de roteamento, como o OSPF (224.0.0.5).

## Endereços especiais

### 1. APIPA (link-local):
- IPs com o prefixo: 169.x.x.x
- Indica que a máquina não encontrou um DHCP
**DHCP:** máquina que da endereço automático para quem entra em contato com ela.

### 2. Broadcast:
- Todos os bits de host em 1: .255
- Manda a mensagem para todos os hosts na rede.

### 3. Endereço de rede:
- Todos os bits de host em 0: .0
- Identifica a própria rede.

### 4. Loopback:
- Identifica a própria máquina.
- Não é roteavel.

## Endereços privados:

- São as faixas de IP que não tem a capacidade de acessar a internet por conta própria e dependem de um roteador.
- O roteador troca o IP privado por um IP público
- Na internet só é visto o IP público.
- Essa troca de IP privado por público se chama NAT (Network Address Translation).
- Existem porque não há IPv4 público suficiente para todos os dispositivos. Assim, uma casa ou empresa inteira usa um único IP público.

![[Pasted image 20261114171717.png]]


## Quantos hosts cabem?

Duas fórmulas resolvem a maioria dos exercícios:

- **Hosts úteis = 2^h − 2**, onde h é a quantidade de bits de host (os zeros da máscara). O −2 desconta a rede e o broadcast.
- **Sub-redes = 2^s**, onde s é a quantidade de bits emprestados da parte de host para criar sub-redes.

**Como achar o d a partir da quantidade de hosts:**

- Teste valores de h até 2^h − 2 ser maior ou igual ao que foi pedido.
- O prefixo é 32 − h.

**Exemplo: preciso de 50 hosts.**

- h = 5 → 2^5 − 2 = 30 → não basta
- h = 6 → 2^6 − 2 = 62 → basta
- Prefixo: 32 − 6 = **/26**


## Dividindo em sub-redes

**Dividir uma rede é pegar bits de host emprestados para a parte de rede. Cada bit emprestado dobra o número de sub-redes e corta o tamanho de cada uma pela metade.**

Exemplo: dividir 192.168.10.0/24 em 4 sub-redes.

- 2^s = 4 → s = 2 bits emprestados
- Novo prefixo: /24 + 2 = **/26** (máscara 255.255.255.192)
- Bloco: 256 − 192 = **64**
- As sub-redes começam em .0, .64, .128 e .192

Cada sub-rede vai do seu início até o início da próxima menos 1:

- O primeiro endereço é a **rede**
- O último é o **broadcast**
- Os do meio são os **hosts úteis**

Ex.: na sub-rede .64, a rede é .64, o broadcast é .127 e os hosts úteis vão de .65 a .126.