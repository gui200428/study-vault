
## 1. Comutação de Circuitos X Comutação de Pacotes

Existem diferentes formas de transportar dados por uma rede. Duas das principais são a comutação de circuitos e a comutação de pacotes.

### Comutação de circuitos:

É estabelecido um **caminho dedicado entre origem e destino antes da comunicação começar.**

![[Pasted image 20260914154228.png]]

Enquanto a conexão estiver ativa, parte dos recurso da rede fica reservado para aquela comunicação.

**Exemplo:**

**Telefonia tradicional:**
- Caminho previamente estabelecido.
- Recursos reservados para a conexão
- Capacidade mais previsível
- Nenhuma disputa pelos recursos reservados.

**Problema:** o recurso continua reservado **mesmo quando não está ocorrendo nenhuma transmissão.** (Ex: durante alguns segundos de silêncio em uma ligação, o circuito continua existindo.)

**Circuito dedicado:** previsibilidade maior, mas possibilidade de desperdício de recursos.

### Comutação de pacotes:

Os dados são divididos em **pacotes menos,** que são enviados pela rede utilizando recursos compartilhados.

**Modelo usado pela internet.**

Normalmente não existe um canal físico reservado exclusivamente para uma comunicação.

![[Pasted image 20260914154732.png]]

**Vários usuários podem usar os mesmos enlaces ao mesmo tempo.**

**Multiplexação estatística:** a capacidade do enlace é utilizada conforme os dispositivos realmente precisam transmitir.

**Características:**
- Recursos compartilhados.
- Melhor aproveitamento da capacidade da rede.
- Adequada para tráfego irregular ou em rajadas.
- Pacotes podem enfrentar filas e congestionamento.

**Pacotes compartilhados:** maior eficiência, mas atraso pode variar.


![[Pasted image 20260914155109.png]]


### RESUMINDO:

**Comutação de circuitos:** recursos são reservados.
**Comutação de pacotes:** recursos da rede são compartilhados conforme a demanda.

## 2. Temporização na transmissão:

Durante a transmissão de dados, existem alguns atrasos até a informação chegar ao destino.

**Principais:**
**Atraso de estabelecimento:** tempo usado para preparar a conexão antes da transmissão.
**Atraso de transmissão:** tempo para enviar os dados para o meio de comunicação.
**Atraso de propagação:** tempo que o sinal leva para percorrer o caminho até o próximo equipamento.
**Atrasos de processamento:** tempo gasto pelos dispositivos intermediários para receber, analisar e encaminhar os dados.


### RESUMINDO:
A transmissão não é instantânea: vários pequenos atrasos se acumulam ao longo do caminho.



## 3. Datagramas X Circuitos virtuais:

Na **comutação de pacotes** existem duas formas comuns de organizar o encaminhamento dos dados:

### Datagramas:

Cada pacote é tratado **de forma independente.**

O roteador analisa o destino de cada pacote e decide para onde enviar.

**Pontos principais:**
- Não precisa estabelecer caminho prévio.
- Cada pacote pode, em teoria, seguir uma rota diferente.
- Tolera melhor mudanças e falhas na rede.
- Modo clássico usado pelo IP

**Datagrama:** cada pacote se vira sozinho.


### Circuitos virtuais:

Antes da transmissão, é criado um **caminho lógico** entre origem e destino.
Depois disso, os pacotes seguem esse caminho usando identificadores, como **rótulos**, em vez de recalcular toda a rota a cada salto.

**Características:**
- Caminho lógico pré-estabelecido.
- Equipamentos mantêm informações sobre o circuito.
- Encaminhamento mais previsível.
- Pode facilitar mecanismos de qualidade de serviço.

**Circuito virtual:** os pacotes seguem um trilho lógico previamente definido.

### RESUMINDO:

**Datagrama:** sem caminho fixo, cada pacote é encaminhado individualmente.
**Circuitos virtuais:** caminho lógico definido antes, e os pacotes seguem esse caminho.


![[Pasted image 20260914160550.png]]


## 3. Arquiteturas lógicas de distribuição em rede.

### Cliente-servidor:

Vários clientes se conectam a um **servidor central,** que oferece algum serviço ou recurso.

![[Pasted image 20260914161245.png]]

**Exemplos:**
- Sites
- E-mail
- Banco de dados
- Jogos online

**Vantagens:**
- Controle centralizado
- Gerenciamento mais simples
- Dados e regras concentrados em um só lugar

**Desvantagens:**
- O servidor pode virar gargalo
- Se o servidor falhar, o serviço pode ficar indisponível.

**Cliente-servidor:** muitos clientes dependem de um servidor central.

### Peer-to-Peer P2P

Os dispositivos podem se comunicar diretamente entre si.

![[Pasted image 20260914161517.png]]

Cada  participante pode atuar tanto como cliente quanto como servidor.

**Exemplos:**
- Rede torrent
- Compartilhamento distribuído de arquivos.
- Redes descentralizadas

**Vantagens:**
- Melhor distribuição de carga
- Maior escalabilidade
- Não depende necessariamente de um único ponto central

**Desvantagens:**
- Gerenciamento mais complexo
- Controle e segurança podem ser mais difíceis

**P2P:** Os próprios participantes compartilham recursos entre si.


### RESUMINDO:

**Cliente-servidor:** centralizado.
**P2P:** distribuído.

## 4. Interoperabilidade e padronização:

Em redes, equipamentos e sistemas de fabricantes diferentes precisam conseguir **se comunicar entre si.**

**Problema:** se cada empresa criasse seus próprios protocolos fechados e incompatíveis, vários sistemas isolados seriam criados.
**Solução:** padronização, definição de regras comuns para a comunicação.

### Interoperabilidade:

Capacidade de diferentes sistemas, dispositivos e softwares funcionarem juntos, independente de fabricante.

**Exemplo:** Um notebook de uma marca consegue se comunicar a um roteador de outra porque ambos seguem padrões compatíveis.

#### Vantagem dos padrões:
- Compatibilidade entre equipamentos
- Comunicação entre diferentes fabricantes
- Expansão das redes
- Redução de dependências de tecnologias proprietárias

**Exemplo de padrões e protocolos comuns:**
- Wifi
- IP
- TCP
- HTTP

**resumindo:** padrões funcionam como uma linguagem comum entre equipamentos diferentes.


## 5. Organizações de padronização da Internet:


### IETF - Internet Engineering Task Force

A IETF desenvolve e padroniza muitos dos protocolos usados na internet.

Publica documentos chamados RFCs que descrevem padrões, protocolos e boas práticas. 

**Exemplo de tecnologias tratadas pela IETF:**
- IP
- TCP
- DNS
- HTTP
- SMTP
**IETF:** desenvolve padrões técnicos da internet.

### IAB - Internet Architecture Board

A IAB atua em um nível mais arquitetural, acompanhando a evolução técnica da internet e ajudando a manter sua organização e coerência.

Possui relação de supervisão e orientação sobre as atividades ligadas à IETF.

**IAB:** visão e orientação arquitetural da internet.

### ISO - International Organization for Standardization

A ISO é uma organização internacional de padronização que atua em diversas áreas, não somente em computação. 
Em redes, ficou especialmente conhecida pelos modelos OSI, usado como referência para organizar as funções de comunicação em camadas.

**ISO:** cria padrões internacionais. Em redes, destaque para o modelo OSI.


### RESUMINDO:

**IETF:** cria padrões e protocolos da internet
**IAB:** orientação e arquitetura da internet
**ISO:** padronização internacional em várias áreas

## 6. Processo de evolução de padrões:

Uma tecnologia geralmente passa por algumas etapas:

**1. Inovação proprietária:** alguém cria uma solução para resolver um problema.
**2. Adoção de mercado:** várias empresas começam a usar soluções semelhantes.
**3. Padronização:** surge um consenso técnico e são definidas regras comuns.
**4. Escala:** o padrão se torna amplamente utilizado e passa a servir de base para novas tecnologias.

**Exemplo:**
O WIFI foi padronizado pela família IEE 802.11.

Isso permite que dispositivos de fabricantes diferentes possam se conectar entre si seguindo as mesmas regras.

**Resumindo:** a padronização transforma soluções isoladas em tecnologias compatíveis e amplamente usadas.

**inovação → adoção → padrão → escala**

## 7. Abstração e Encapsulamento de dados

Em uma arquitetura em camadas, cada camada oferece serviços para a camada acima **sem precisar mostrar como tudo funciona internamente.**

**Abstração:** a camada de cima usa o serviço da camada de baixo sem precisar conhecer todos os detalhes da implementação.

### Encapsulamento:
Quando os dados descem pelas camadas da rede, cada camada pode adicionar suas próprias informações de controle, normalmente em um cabeçalho.

**Exemplo:**

Dados do usuário  
↓  
Cabeçalho da camada superior + dados
↓  
Cabeçalho da camada inferior + cabeçalho anterior + dados

Os cabeçalhos carregam informações necessárias para a comunicação. Como:
- Endereços
- Controle
- Identificação de protocolo
- Informação de entrega

**No destino:** ocorre o processo inverso, cada camada remove e interpreta seu próprio cabeçalho até chegar novamente aos **dados originais.**

**Encapsulamento:** cada camada adiciona informações aos dados antes de passá-los adiante.

### RESUMINDO:
**Abstração:** cada camada esconde seus detalhes internos.
**Encapsulamento:** cada camada envolve os dados com suas próprias informações.

## 8. Vantagens e desvantagens da arquitetura em camadas:

A organização da comunicação em camadas facilita muito o projeto da rede.

**Vantagens:**
- **Modularidade**: cada camada pode ser alterada ou atualizada com menor impacto nas outras.
- **Facilidade de manutenção**: problemas ficam mais fáceis de localizar.
- **Interoperabilidade**: sistemas diferentes conseguem se comunicar seguindo os mesmos padrões e interfaces.

**Desvantagens:**
- **Overhead:** cada camada pode adicionar cabeçalhos e informações extras aos dados.
- **Duplicação de funções:** algumas tarefas podem aparecer em mais de uma camada.
- **Maior processamento:** os dados precisam atravessar várias camadas até serem enviados ou recebidos.

**Resumindo:** dividir a rede em camadas melhora organização, manutenção e compatibilidade, mas adiciona custo de processamento e informações extras.


## 9. Modelo OSI
Organiza a comunicação de rede em 7 camadas. Cada camada possui uma função especifica e utiliza os serviços da camada abaixo.


![[Pasted image 20260914170023.png]]


### 7 - Aplicação: 
É a camada mais próxima do usuário e dos programas.

**Exemplo:** HTTP, FTP, SMTP, DNS.
**Aplicação:** serviços de rede usados pelos programas.


### 6. Apresentação:
Cuida da forma como os dados são representados.

**Pode envolver:**
- Conversão de formatos
- Codificação
- Criptografia
- Compressão

**Apresentação:** formato dos dados


### 5. Sessão:
Controla a comunicação entre aplicações, criando, mantendo e encerrando sessões.

**Sessão:** organiza o diálogo entre aplicações.

### 4. Transporte:
Cuida da comunicação **fim a fim** entre os dispositivos.

**Pode oferecer:**
- Controle de erros
- Controle de fluxo
- Confiabilidade
- Divisão dos dados em partes menores.
**Exemplo:** TCP e UDP

**Transporte: entrega entre origem e destino.**

### 3. Rede:
Responsável pelo endereçamento lógico e roteamento.

Onde entra o IP e a escolha do caminho pela rede.

**Rede:** para onde os dados devem ir.

### 2. Enlace:
Cuida da comunicação dentro de um **enlace ou rede local.**
**Trabalho com:**
- Endereço MAC
- Quadros
- Controle de acesso ao meio
- Detecção de alguns erros
**Enlace:** comunicação entre dispositivos no mesmo trecho da rede.


### 1. Física:
Responsável por transmitir os **bits fisicamente.**

**Pontos envolvidos:**
- Cabos
- Conectores
- Sinais elétricos
- Fibra óptica
- Ondas de rádio

**Física:** transportar 0 e 1 pelo meio.

### RESUMINDO:

**Aplicação → Apresentação → Sessão → Transporte → Rede → Enlace → Física**

As camadas superiores lidam mais com **aplicações e dados,** enquanto as inferiores lidam mais com **transporte, endereçamento e meio físico.**

## 10. SAP, SDU e PDU no modelo OSI:

Quando uma camada recebe dados da camada superior, ela adiciona suas próprias informações de controle antes de passar os dados para a camada inferior.

### SDU - Service Data Unit
É o  dado recebido da camada superior. 
Basicamente, para uma camada, a SDU é basicamente: “o conteúdo que ela precisa transportar”.

### PDU - Protocol Data Unit
Quando a camada pega a SDU e adiciona seu próprio cabeçalho, o resultado vira uma **PDU**.

**PDU = Header + SDU**

A PDU é a unidade de dados que aquela camada utiliza para se comunicar logicamente com a **mesma camada no outro dispositivo**.

### SAP - Service Access Point:
O **SAP** é o ponto/interface pelo qual uma camada acessa os serviços da camada abaixo.
**SAP = ponto de acesso entre camadas.**

### Entidades pares - Peer entities:
São entidades que pertencem à **mesma camada**, mas estão em dispositivos diferentes.

**Exemplo:**
**Camada de Transporte do computador A ↔ Camada de Transporte do computador B**
Elas parecem “conversar diretamente”, mas na prática os dados descem pelas camadas, atravessam a rede e depois sobem no outro dispositivo.

### RESUMINDO:
**SDU:** dados recebidos da camada superior.  
**PDU:** SDU + informações adicionadas pela camada.  
**SAP:** interface entre duas camadas.  
**Peer entities:** mesmas camadas em dispositivos diferentes

**SDU entra → a camada adiciona cabeçalho → vira PDU.**

## 11. Modelo OSI x TCP/IP

O modelo **OSI** possui **7 camadas** e é usado principalmente como **modelo de referência** para entender e organizar a comunicação em redes.

O modelo **TCP/IP** é a arquitetura utilizada na prática pela Internet.

![[Pasted image 20260914171924.png]]

No modelo TCP/IP de 4 camadas:

- **Aplicação** → reúne as camadas de Aplicação, Apresentação e Sessão do OSI.
- **Transporte** → corresponde aproximadamente à camada de Transporte do OSI.
- **Internet** → corresponde à camada de Rede.
- **Acesso à Rede** → reúne Enlace e Física.

 **OSI é um modelo conceitual para entender redes. TCP/IP é a arquitetura que efetivamente sustenta a Internet.**

## 12. Fluxo de uma comunicação na Internet

Quando um cliente envia dados para um servidor, a informação:

**Aplicação → Transporte → Internet → Acesso à Rede**

Depois, os dados atravessam vários roteadores até chegar ao destino, onde sobem novamente pelas camadas.

Durante esse caminho, os roteadores analisam principalmente as informações da **camada de internet,** como endereço IP, para decidir o próximo salto.

A Internet consegue conectar equipamentos de fabricantes diferentes porque todos seguem **protocolos e padrões comuns**, como os definidos pela IETF.

**Resumindo:** os dados descem pela pilha TCP/IP no emissor, atravessam a rede passando por roteadores e sobem pela pilha no receptor.


![[Pasted image 20260914172326.png]]

