
## 1. Definição de rede de computadores:

→ É um sistema interconectado projetado com o propósito bidimensional.
→ Compartilhamento de recursos: hardware, software e dados distribuídos.
→ Comunicação de entidades: troca de mensagens e estados em tempo real.

### Termos técnicos da rede:

#### 1. Host:
- É o dispositivo de borda que executa aplicações  de rede.

#### 2. Roteador:
- É o equipamento que encaminha os pacotes de dados entre diferentes redes.

#### 3. Nó:
- Dispositivo com endereço físico conectado à rede.  Ele é capaz de criar receber ou transmitir informações.

#### 4. Enlace
- Meio de comunicação físico ou canal lógico que conecta dispositivos.

#### 5. Protocolo
- conjunto de regras matemáticas e lógicas que governam o formato, a sincronização e o controle de erros.


## 2. Elementos de um sistema de comunicação de dados

Uma comunicação de dados pode ser representada pelo seguinte fluxo:

**Fonte → Transmissor → Meio de transmissão → Receptor → Destino**

### 1. Fonte - DTE:

A fonte é o equipamento que gera os dados que serão enviados.

**Exemplo:** Computador, celular, servidor, sensor.

**DTE (Data terminal equipment):** é o equipamento terminal que produz ou usa os dados.


### 2. Transmissor - DCE:

O transmissor recebe os dados digitais do DTE e os transforma em um sinal adequado ao meio de transmissão.

**Tipo de sinal:** elétrico, óptico, rádio.
→ **Este processo pode envolver codificação ou modulação.**
**Exemplo:** modem.

**DCE (Data communication equipment):** é o responsável por fazer a interface entre o equipamento terminal e o meio de comunicação.


### 3. Meio de transmissão:

É o caminho pelo qual o sinal viaja entre o transmissor e receptor.

**Exemplo:** Cabo de cobre, fibra óptica, ondas de rádio, redes de telecomunicações.

A função dele é simplesmente transportar o sinal de um ponto até outro.


### 4. Receptor - DCE:

O receptor realiza o processo inverso do transmissor. Recebe o sinal vindo do meio e recupera os dados digitais contidos nele.

**Exemplo:** sinal → dados digitais.

O processo pode envolver demodulação e decodificação.


### 5. Destino - DTE:

Equipamento que finalmente recebe e utiliza os dados transmitidos.

**Exemplo:** outro computador recebendo uma mensagem enviada pela rede.

### RESUMINDO:

Computador → Modem → Rede → Modem → Computador

DTE → DCE → Meio de transmissão → DCE → DTE

**DTE:** gera ou consome os dados.
**DCE:** permite que os dados sejam transmitidos pelo meio de comunicação.


## 3. Borda da rede / Núcleo de rede

### Borda da rede:
A borda da rede é onde ficam os dispositivos finais, equipamentos usados diretamente pelas aplicações e pelos usuários.

**Exemplo:** Computadores, celulares, servidores, dispositivos IoT.

É nesses dispositivos que os dados normalmente são criados ou consumidos. Como uma mensagem sendo enviada por um celular. (celular está na borda da rede.)

É onde ocorre o acesso à rede, por meio de Wifi, rede móvel, etc.


### Núcleo da rede:

É formado pelos equipamentos responsáveis por transportar os dados entre diferentes partes da rede.

**Exemplo:** roteadores, switches, enlaces de comunicação entres redes.

O objetivo do núcleo é fazer os dados chegarem da origem até o destino através de vários equipamentos intermediários.

**Funções envolvidas:**

**1- Comutação:** mover dados de uma interface para outra dentro de um equipamento.
**2- Roteamento:**decidir qual caminho os dados devem seguir pela rede.


### Exemplo:

Computador acessando um site:

Computador → roteador → rede do provedor → vários roteadores → servidor.

**O computador e o servidor estão na borda da rede.**

**Os roteadores e enlaces intermediários fazem parte do núcleo da rede.**

### Resumindo:

**Borda de rede:** onde os dados são produzidos e utilizados.
**Núcleo da rede:** onde os dados são transportados e encaminhados.


## 4. Tipos de conexão: Ponto a ponto e multiponto.

### Enlace ponto a ponto.

Em uma conexão ponto a ponto, existe um canal dedicado entre apenas dois dispositivos.

Dispositivo 1 <-> Dispositivo 2

Como o meio é exclusivo, os dois dispositivos não precisam disputar o canal com outros equipamentos.

**Vantagens:**
- Comunicação simplesmente
- Sem disputa pelo meio entre vários dispositivos.
- Desempenho previsível

**Desvantagens:**
- Baixa escalabilidade, conectar muitos dispositivos dessa forma precisaria de vários enlaces individuais. Acaba se tornando caro e complexo de expandir.

### Rede multiponto.

Vários dispositivos compartilham o mesmo meio de transmissão.

A-B-C-D

Todos usam o mesmo canal para transmitir dados.

**Problema:** dois ou mais dispositivos podem tentar transmitir ao mesmo tempo. Exige um mecanismo para organizar o acesso ao meio.

#### Controle de acesso ao meio - MAC

**MAC (Media access control):** define regras para determinar quando cada dispositivo pode utilizar o meio de transmissão.

**Objetivo:**
- Evitar transmissões simultâneas problemáticas.
- Organizar o  acesso ao canal.
- Reduzir ou tratar colisões.
- Melhorar a eficiência da comunicação.

### RESUMINDO:

**Ponto a ponto:**
- Canal exclusivo conecta dois dispositivos.

**Multiponto:**
- Vários dispositivos compartilham o mesmo canal e precisam de mecanismos para coordenar o acesso.
- Quando o meio é compartilhado, surge o problema de decidir quem pode transmitir e quando.


## 5. Modos de transmissão da informação:

### Simples:
Os dados trafegam em **apenas uma direção.**
→ Um dispositivo sempre transmite e o outro sempre recebe.

A → B.

Não existe resposta pelo mesmo canal.

**Exemplo:**
- Transmissão de TV
- Rádio
- Sistemas simples de telemetria.

### Half-duplex
Os dois dispositivos podem transmitir e receber, mas não ao mesmo tempo.

A → B ou A ← B

Os dispositivos precisam se alternar no uso do canal.

**Exemplo:** walkie-talkie

### Full-duplex
Os dois  dispositivos podem transmitir e receber simultaneamente.

A ⇄ B

Não existe a necessidade de esperar o outro terminar de transmitir.

**Exemplo:**
- Ligação telefônica
- Ethernet
- Comunicação entre muitos equipamento de rede atuais.


## 6. Endereçamento: 

Os dispositivos podem ser identificados de formas diferentes dependendo da camada de comunicação.

### Endereço físico - MAC

O endereço MAC identifica uma interface de rede na camada de enlace.
O MAC identifica a interface dentro do enlace local.
Quando um computado envia dados para outro dispositivo da mesma rede, o endereço MAC ajuda a determinar qual interface deve receber as informações.

### Endereço lógico - IP

O endereço IP pertence à camada de rede e é usado para identificar dispositivos e rede de maneira roteável.

**Exemplos:**

IPv4: 192.168.0.1

IPv6: 2001:db8::1

O endereço IP possui uma estrutura hierárquica que permite aos roteadores descobrir **para qual rede os dados devem ser enviados**.


![[Pasted image 20260914150033.png]]

Simplificando:

**IP:** indica o destino final. (onde você está)
**MAC:** indica para quem entregar o quadro **naquele trecho da rede**. (quem você é)



## 7. Latência nodal:

Quando um pacote passa por um nó da rede, como um roteador, ele sofre diferentes tipos de atraso.

O atraso total é:

### $$d_{nodal}=d_{proc}+d_{queue}+d_{trans}+d_{prop}$$
Onde:

- **$d_{proc}$ - atraso de processamento:** tempo gasto pelo equipamento para analisar o pacote e decidir para onde enviá-lo.
- **$d_{queue}$ - atraso de fila:** tempo que o pacote fica esperando na fila antes de ser transmitido. Aumenta quando existe **congestionamento**.
- **$d_{trans}$ - atraso de transmissão:** tempo necessário para colocar todos os bits do pacote no enlace. Depende do **tamanho do pacote** e da **velocidade do link**.
- **$d_{prop}$ - atraso de propagação:** tempo que o sinal leva para percorrer fisicamente o meio até o próximo ponto. Depende principalmente da **distância** e da velocidade de propagação do sinal.


### Diferença importante

Não confundir **transmissão** com **propagação**:

**Transmissão:** quanto tempo demora para colocar os bits no cabo.

$$d_{trans}=\frac{L}{R}$$

onde \(L\) é o tamanho do pacote em bits e \(R\) é a taxa do enlace em bits/s.

**Propagação:** quanto tempo os bits demoram para **viajar pelo cabo**.

$$d_{prop}=\frac{D}{V}$$

onde \(D\) é a distância e \(V\) é a velocidade de propagação do sinal.

**Resumindo:**

**Latência = processamento + fila + transmissão + propagação.**
