O material organiza as aulas 4 a 6 em três pilares:

- **Pilar 1 - Logística dos Dados (Aula 4):** comutação e arquiteturas lógicas.
- **Pilar 2 - Governança Global (Aula 5):** IAB, IETF e ISO.
- **Pilar 3 - O Grande Projeto (Aula 6):** modelos OSI e TCP/IP.
## Comutação e caminho dos dados

### Circuitos × pacotes

| | Comutação de circuitos | Comutação de pacotes |
| --- | --- | --- |
| **Caminho** | Dedicado entre origem e destino. | Malha dinâmica; dados fragmentados em pacotes. |
| **Uso dos recursos** | Capacidade garantida, mas os recursos ficam reservados mesmo na ociosidade. | Compartilhamento estatístico dos recursos. |
| **Exemplo da aula** | Telefonia clássica (PSTN). | Internet. |

Na comutação de circuitos, a reserva dá previsibilidade, mas pode desperdiçar capacidade. Na de pacotes, os dados divididos percorrem uma rede de recursos compartilhados.

### Temporização da transmissão

O diagrama acompanha os dados do **Host A** até o **Host B**, passando por um **nó de comutação**. O tempo cresce de cima para baixo.

- **Atraso de estabelecimento (setup delay):** sinalização de ida e volta para preparar a comunicação antes do envio dos dados.
- **Atraso de transmissão:** tempo para colocar os dados no enlace; aparece na espessura temporal da faixa de dados.
- **Atraso de propagação:** tempo para o sinal percorrer o meio entre os pontos; aparece no deslocamento da faixa ao longo do tempo.
- **Armazenar e retransmitir / atraso de processamento:** etapa indicada no nó antes de seguir ao Host B.

Transmissão e propagação são atrasos diferentes: colocar os dados no enlace não é o mesmo que o sinal percorrer a distância.

![[Pasted image 20260927211001.png]]

### Datagramas × circuitos virtuais

São duas formas de organizar a **comutação de pacotes**:

- **Datagramas:** cada pacote é roteado de forma independente. Não há fase de estabelecimento; a rota pode mudar diante de falhas. **Exemplo:** protocolo IP.
- **Circuitos virtuais:** um caminho **lógico** é preestabelecido. O encaminhamento usa **rótulos nas tabelas de roteamento** e pode dar suporte à **Qualidade de Serviço (QoS)**.

O caminho preestabelecido do circuito virtual é **lógico**; na comutação de circuitos, o material fala em **caminho dedicado**.

![[Pasted image 20260927211002.png]]

## Arquiteturas lógicas de distribuição

- **Cliente-servidor:** os clientes se relacionam com um servidor central. Essa concentração pode criar **gargalo de tráfego** e **ponto único de falha**.
- **Peer-to-Peer (P2P):** os participantes se conectam entre si, distribuindo as trocas. O material destaca **alta escalabilidade** e **resiliência distribuída**.

## Interoperabilidade e padronização

Sistemas proprietários, protocolos fechados e hardware incompatível fragmentam a rede em **silos**. A **padronização** fornece regras comuns para que sistemas diferentes se conectem: é a base da **interoperabilidade** global.

### Organizações citadas

| Organização | Papel apresentado na aula |
| --- | --- |
| **IAB** (Internet Architecture Board) | Supervisão estratégica e arquitetural da Internet. |
| **IETF** (Internet Engineering Task Force) | Engenharia tática, resolução de problemas de curto prazo e criação de **RFCs**, com foco em TCP/IP. |
| **ISO** (International Organization for Standardization) | Organização global que vai além de TI; padrões internacionais rigorosos e modelos teóricos de referência. |

### Evolução de uma tecnologia até virar padrão

1. **Inovação proprietária:** solução inicial para um problema tecnológico.
2. **Adoção de mercado:** soluções isoladas passam a competir.
3. **Padronização:** consenso da engenharia; exemplo da aula: **IEEE 802.11 para Wi-Fi**.
4. **Comoditização e escala:** o padrão vira fundamento para a próxima camada de inovações.

## Abstração e encapsulamento em camadas

**Axioma fundamental da abstração:** a **camada N fornece serviços para a camada N+1**, ocultando os detalhes mecânicos e lógicos da própria implementação.

**Encapsulamento:** os dados do usuário (**payload**) recebem informações de controle em camadas sucessivas. O desenho mostra o payload envolvido pelo **cabeçalho da camada superior** e, depois, pelo **cabeçalho da camada inferior**.

### Vantagens e custos da divisão em camadas

| Vantagens | Desvantagens |
| --- | --- |
| **Modularidade:** manutenção isolada de cada camada. | **Overhead de processamento:** o slide associa cabeçalhos excessivos à redução da banda útil. |
| **Isolamento de falhas:** erros contidos na própria camada. | **Duplicação de funções:** por exemplo, controle de erros no Enlace e no Transporte. |
| **Interoperabilidade global.** | **Aumento da latência** ao atravessar a pilha. |

## Modelo OSI e arquitetura TCP/IP

### As sete camadas do OSI

Da camada superior para a inferior:

| Grupo apresentado | Camadas OSI | Papel |
| --- | --- | --- |
| **Suporte ao usuário** | **7. Aplicação; 6. Apresentação; 5. Sessão** | Semântica e interface. |
| **Elo de ligação** | **4. Transporte** | Confiabilidade fim a fim. |
| **Suporte à rede** | **3. Rede; 2. Enlace; 1. Física** | Mecânica e lógica do tráfego. |

### SAP, SDU, PDU e entidades pares

- **SAP (Service Access Point):** ponto de acesso ao serviço na fronteira entre camadas.
- **SDU (Service Data Unit):** dados entregues por uma camada à outra para serem transportados.
- **PDU (Protocol Data Unit):** unidade formada quando a camada acrescenta seu **cabeçalho (H)** à SDU: **PDU = H + SDU**.
- **Entidades pares (peer entities):** entidades da mesma camada em dispositivos diferentes; entre elas ocorre uma **comunicação lógica**.

O diagrama mostra a SDU recebendo um cabeçalho para formar a PDU, que segue em direção à camada inferior.

![[Pasted image 20260927211003.png]]

### Correspondência OSI × TCP/IP

| OSI | TCP/IP |
| --- | --- |
| Aplicação + Apresentação + Sessão | **Aplicação** |
| Transporte | **Transporte** |
| Rede | **Internet** |
| Enlace + Física | **Acesso à Rede** |

O material caracteriza o **OSI** como modelo **teórico de referência primoroso** e o **TCP/IP** como arquitetura **empírica e pragmática** que construiu a Internet.

![[Pasted image 20260927211004.png]]

## A conexão em ação

No fluxo final do material, o **Host A (cliente)** envia um **datagrama** por sua pilha TCP/IP. Ele atravessa uma malha de **roteadores de vários fabricantes**, operando sob normas **IETF/RFC**, até chegar ao **Host B (servidor)**. O exemplo reúne comutação de pacotes, interoperabilidade e as camadas de **Aplicação, Transporte, Internet e Acesso à Rede** nos dois hosts.

![[Pasted image 20260927211005.png]]
