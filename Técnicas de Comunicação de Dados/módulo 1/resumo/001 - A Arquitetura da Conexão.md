# A Arquitetura da Conexão

## Rede de computadores

Uma rede de computadores é um sistema interconectado projetado com um único **propósito bidimensional**:

- **Compartilhamento de recursos:** hardware, software e dados distribuídos.
- **Comunicação de entidades:** troca sistemática de mensagens e estados em tempo real.

### Vocabulário da rede

- **Host (sistema final):** dispositivo de borda que executa aplicações de rede.
- **Roteador:** equipamento do núcleo que encaminha pacotes entre redes diferentes.
- **Nó:** dispositivo com endereço físico conectado à rede, capaz de criar, receber ou transmitir informações.
- **Enlace (link):** meio físico ou canal lógico que conecta dispositivos adjacentes.
- **Protocolo:** conjunto de regras matemáticas e lógicas que governam formato, sincronização e controle de erros.

## Modelo de comunicação de dados

**Fonte (DTE) → Transmissor (DCE) → Sistema de transmissão → Receptor (DCE) → Destino (DTE)**

- **Fonte — DTE (Equipamento Terminal de Dados):** gera a informação digital original, como um computador.
- **Transmissor — DCE (Equipamento de Terminação de Circuito):** converte os dados para um formato adequado ao meio.
- **Sistema de transmissão:** meio físico e infraestrutura de rede que transportam o sinal.
- **Receptor — DCE:** recebe o sinal do meio e o reconverte em dados digitais lógicos.
- **Destino — DTE:** recebe e processa a informação final.

### Ciclo da comunicação digital

No **domínio superior**, bits, dados e software representam a informação com significado estruturado para a máquina. Na transmissão, a **modulação/codificação** leva essa informação ao **domínio inferior**, o meio físico, onde ela aparece como sinais elétricos, ópticos ou eletromagnéticos: variações de energia no tempo e no espaço. Na recepção, **demodulação/decodificação** recupera a informação lógica.

![[Pasted image 20260927205001.png]]

Obs: no diagrama, “Demodulação/Decodificação” aparece junto às duas setas do lado direito. O modelo de comunicação do próprio material coloca a recuperação dos dados digitais no receptor.

## Borda e núcleo da rede

- **Borda (network edge):** onde ficam as aplicações e os dispositivos que originam ou consomem dados. Requer interfaces de usuário e portas de acesso à rede.
- **Núcleo (network core):** malha de comutadores e roteadores interconectados. Move os dados da origem ao destino por **comutação** e **roteamento**, buscando rapidez e eficiência.

## Arquiteturas de conexão e acesso ao meio

### Enlace ponto a ponto

Conexão dedicada e exclusiva entre dois dispositivos: o canal inteiro fica reservado para eles. **Vantagem:** não há colisões entre vários usuários do meio. **Desvantagem:** a escalabilidade é inviável para redes grandes.

### Rede multiponto

Vários dispositivos compartilham o mesmo meio físico (**broadcast/shared**). Como podem tentar transmitir ao mesmo tempo, são necessários protocolos de **controle de acesso ao meio (MAC)** para coordenar quem transmite e evitar ou tratar colisões de sinais concorrentes.

## Modos de transmissão

| Modo | Direção e uso do canal | Exemplo da aula |
| --- | --- | --- |
| **Simplex** | Unidirecional: o transmissor apenas envia e o receptor apenas recebe. | Telemetria simples. |
| **Half-duplex** | Bidirecional, mas nunca simultâneo: os dispositivos alternam o uso do canal. | Rádios táticos (walkie-talkie). |
| **Full-duplex** | Bidirecional e simultâneo; o canal é dividido lógica ou fisicamente. | Ethernet moderna e telefonia. |

## Endereçamento: identidade e localização

| | Endereço físico (MAC) | Endereço lógico (IPv4/IPv6) |
| --- | --- | --- |
| **Ideia** | “Quem você é”: o slide o descreve como identidade imutável, gravada no hardware de fábrica. | “Onde você está”: identidade hierárquica, roteável e atribuída dinamicamente. |
| **Escopo** | Entrega na rede **local**, na camada de enlace. | Entrega em nível **global** e na internet, na camada de rede. |
| **Formato** | 48 bits, em hexadecimal. | 32 bits no IPv4; 128 bits no IPv6. |

No percurso de um pacote, o material associa o **IP ao destino final** e o **MAC ao próximo salto**.

## Latência nodal

O atraso total em um nó é a soma de quatro atrasos distintos:

$$
d_{nodal} = d_{proc} + d_{queue} + d_{trans} + d_{prop}
$$

| Atraso | Natureza e causa | Como mitigar, segundo a aula |
| --- | --- | --- |
| **Processamento** ($d_{proc}$) | Lógica do roteador: verificar erros no pacote e determinar a rota correta. | Melhorar hardware e CPU do roteador. |
| **Fila** ($d_{queue}$) | Congestionamento no buffer quando a taxa de chegada de pacotes excede temporariamente a taxa de saída. | Aumentar a banda, aplicar QoS ou dimensionar buffers. |
| **Transmissão** ($d_{trans}$) | Tempo para colocar todos os bits do pacote no enlace físico; ligado à largura de banda do enlace. | Instalar links de maior capacidade, por exemplo, migrar de **1 Gbps para 10 Gbps**. |
| **Propagação** ($d_{prop}$) | Tempo de viagem do bit no meio físico; depende da distância e do meio, limitado pelas leis da física e pela velocidade da luz. | Reduzir a distância física até o usuário, por exemplo, com **CDNs** ou **Edge Computing**. |

**Transmissão** é colocar os bits no enlace; **propagação** é o sinal percorrer o meio. Aumentar a capacidade do link atua diretamente no primeiro caso; aproximar o destino atua no segundo.

### Cálculo dos atrasos (complemento)

As fórmulas e o exemplo a seguir foram acrescentados para estudo; não aparecem no PDF desta aula.

$$
d_{trans} = \frac{L}{R}
$$

- $L$ = tamanho do pacote em **bits**.
- $R$ = taxa do enlace em **bps** (bits/s).

$$
d_{prop} = \frac{d}{s}
$$

- $d$ = distância percorrida pelo sinal, em **metros**.
- $s$ = velocidade de propagação, aproximadamente $2 \times 10^8$ **m/s** em cobre ou fibra.

**Exemplo:** um pacote de 1500 bytes tem $1500 \times 8 = 12.000$ bits. Em um link de 100 Mbps:

$$
d_{trans} = \frac{12.000}{100 \times 10^6} = 0{,}00012\ \text{s} = 0{,}12\ \text{ms}
$$

Para 1000 km de fibra ($10^6$ m):

$$
d_{prop} = \frac{10^6}{2 \times 10^8} = 0{,}005\ \text{s} = 5\ \text{ms}
$$

Se o link subir para 1 Gbps, $d_{trans}$ cai para **0,012 ms**, mas $d_{prop}$ continua em **5 ms**. A capacidade do link atua na transmissão; a distância atua na propagação.

## Percurso de um pacote

No exemplo da aula, o pacote sai do **host (borda)** com IP do destino final e MAC do próximo salto. Viaja pelo ar em uma rede **multiponto**, em **half-duplex**, disputando o meio para evitar colisões. Ao chegar ao **roteador (núcleo)**, o sinal físico volta a ser interpretado como bits lógicos. O roteador processa o pacote, pode colocá-lo em fila e o transmite para a fibra de longa distância, onde há atraso de propagação, até seguir ao servidor de destino.

![[Pasted image 20260927205002.png]]
