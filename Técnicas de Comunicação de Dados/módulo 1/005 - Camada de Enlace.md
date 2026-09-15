
## 1. Função da Camada de Enlace

A **camada física** apenas transporta sinais pelo meio, mas esse meio pode sofrer:
- ruído;
- interferência;
- distorção;
- perdas;
- erros de transmissão.

A **camada de enlace** fica acima da camada física e tenta transformar essa comunicação bruta em algo mais organizado e confiável para a camada de rede.

Ela faz isso usando mecanismos como:
- organização dos dados em **quadros (frames)**;
- detecção de erros;
- controle de acesso ao meio;
- identificação local por endereços MAC.

**Resumo:** a camada física transporta sinais; a camada de enlace organiza e controla essa transmissão para entregar dados de forma mais confiável.


## 2. Tipos de serviço da Camada de Enlace
A camada de enlace pode oferecer diferentes níveis de confiabilidade.

### 1. Sem conexão e sem confirmação
Os quadros são enviados **sem estabelecer uma conexão antes** e sem esperar confirmação de recebimento. Se um quadro for perdido ou corrompido, a própria camada de enlace não necessariamente tenta recuperá-lo.

### 2. Sem conexão, mas com confirmação
Ainda não existe uma conexão lógica permanente entre os dispositivos, porém cada quadro pode receber uma **confirmação de recebimento (ACK)**.
Se a confirmação não chegar, o quadro pode ser retransmitido.
Isso é útil em meios mais sujeitos a erros, como redes sem fio.

**Exemplo**: **Wi-Fi**, que possui confirmações na camada de enlace.

> **Envia → espera ACK → se necessário, retransmite.**

### 3. Orientado à conexão
Antes de transmitir os dados, é estabelecida uma **conexão lógica** entre os dispositivos.

Essa modalidade pode oferecer mecanismos mais fortes de:
- controle;
- ordenação;
- confirmação;
- retransmissão;
- confiabilidade.

> **Primeiro estabelece a conexão, depois transmite com maior controle.**

É mais robusto, mas também possui **maior overhead**.


### RESUMINDO:
**menos controle → menor overhead**
**mais controle → maior confiabilidade, mas maior custo de comunicação**

## 3. Problema 1: Onde o dado começa?

### Enquadramento
A camada física entrega uma sequência contínua de bits. 
**O problema é**: como o receptor sabe onde começa e onde termina cada conjunto de dados?
A camada de enlace resolve isso organizando os bits em **quadros (frames)**.

> **Enquadramento = dividir o fluxo contínuo de bits em blocos identificáveis chamados quadros.**

Cada quadro pode conter, por exemplo:
- cabeçalho;
- dados;
- informações de controle;
- verificação de erro.

### Sem enquadramento, o receptor veria algo como:

101101001010111010

mas não saberia onde termina uma mensagem e começa outra. Com framing, a informação passa a ser interpretada em blocos:
`[ quadro 1 ] [ quadro 2 ] [ quadro 3 ]`

### RESUMINDO:
> **A camada física vê bits; a camada de enlace organiza esses bits em quadros.**


## 4. Byte Stuffing e Bit Stuffing

Quando usamos padrões especiais para marcar os limites de um quadro, pode acontecer de esse mesmo padrão aparecer **dentro dos dados**. É necessário distinguir conteúdo de marcador de controle.

### Byte Stuffing
No **byte stuffing**, se um byte especial como `FLAG` aparecer dentro dos dados, é inserido antes dele um caractere de escape, normalmente `ESC`.

Exemplo:

`... FLAG ...`

vira:

`... ESC FLAG ...`

O receptor entende que aquele `FLAG` faz parte dos dados e não marca o fim do quadro.

> **Byte stuffing = insere ESC antes de bytes especiais.**


### Bit Stuffing
No **bit stuffing**, a proteção acontece bit a bit.

> depois de **cinco bits 1 consecutivos**, o transmissor insere automaticamente um `0`.

Então:

`11111`

vira:

`111110`

O receptor reconhece esse `0` extra e o remove.

> **Bit stuffing = insere bits extras para evitar que os dados imitem o padrão de controle.**


### RESUMO:
> **Stuffing serve para impedir que os próprios dados sejam confundidos com os delimitadores do quadro.**

## 5. Problema 2: Ruído.

### Redundância cíclica (CRC):

Durante a transmissão, o sinal pode sofrer ruído e alguns bits podem ser alterados.
Para detectar esse tipo de erro, a camada de enlace pode usar o **CRC**.

**Ideia:**
1. o transmissor pega os dados;
2. faz um cálculo com um valor conhecido chamado **gerador**;
3. obtém um pequeno resultado de verificação;
4. acrescenta esse resultado ao quadro;
5. o receptor repete a verificação quando os dados chegam.
Se o resultado não bater, significa que **provavelmente houve erro na transmissão**.

### Importante
O CRC serve principalmente para **detectar erros**.
Ele não corrige automaticamente o conteúdo alterado.

> **CRC = adiciona redundância aos dados para verificar se eles chegaram íntegros.**

**Dados + CRC → transmissão → verificação no receptor**

Se a verificação falhar, o quadro pode ser descartado ou retransmitido, dependendo do protocolo.


## ARQ - Automatic Repeat reQuest
O **ARQ** é um mecanismo de recuperação de erros baseado em **retransmissão**.

**Funcionamento:**
1. o transmissor envia um quadro;
2. espera uma confirmação do receptor;
3. se a confirmação não chegar dentro de um tempo limite, o transmissor entende que houve algum problema;
4. então o quadro é enviado novamente.
#### Temporizador
O transmissor inicia um **timer** depois de enviar o quadro.

Se o tempo acabar sem confirmação:

> **timeout → retransmissão**

### Números de sequência

Os quadros recebem **números de sequência** para que o receptor consiga distinguir:
- um quadro novo;
- uma retransmissão;
- um quadro duplicado.
Isso evita processar o mesmo dado duas vezes.

### Ideia principal
> **CRC detecta o erro. ARQ ajuda a recuperar usando retransmissão.**

**envia → espera ACK → deu timeout? retransmite**

## 6. Problema 3: receptores sobrecarregados.
No **Stop-and-Wait**, o transmissor envia **um quadro por vez**.
Depois de enviar, ele para e espera uma confirmação do receptor:

**ACK (Acknowledgment)**

O fluxo fica assim:
**envia quadro → espera ACK → recebeu ACK → envia o próximo**

Isso evita que o receptor receba dados mais rápido do que consegue processar.

### Vantagem
É simples e fácil de controlar.
### Desvantagem
Pode desperdiçar bastante tempo, porque o transmissor fica **parado esperando o ACK** antes de continuar.

Em enlaces de alta latência, isso pode reduzir muito o desempenho.

**Resumo:** Stop-and-Wait controla o fluxo enviando um quadro por vez e esperando confirmação antes do próximo.

## 7. Piggybacking
No **piggybacking**, a confirmação de recebimento (**ACK**) não é enviada sozinha.
Se o receptor também tiver dados para mandar no sentido contrário, ele **aproveita esse próprio quadro de dados para carregar o ACK junto**.

Em vez de:

**A → dados → B**  
**A ← ACK ← B**

podemos ter:

**A ← dados + ACK ← B**

### Vantagem
Isso reduz a quantidade de quadros separados circulando na rede e melhora o aproveitamento do enlace.
> **Piggybacking = “pegar carona” no tráfego de volta para enviar a confirmação.**

### Importante
Se não houver dados para enviar no sentido contrário dentro de um tempo razoável, o ACK precisa ser enviado sozinho mesmo.

Então a ideia é:

**tem tráfego de volta? embute o ACK nele.**  
**não tem? manda o ACK separado**

## 8. Janela Deslizante - Resolver lentidão do stop and wait

No **Stop-and-Wait**, o transmissor envia um quadro e fica parado esperando o ACK.
A **janela deslizante** melhora isso permitindo que vários quadros sejam enviados **antes de receber todas as confirmações**.

Exemplo:

janela de tamanho 3:

**0, 1 e 2** podem ser enviados sem esperar.

Quando o quadro **0** é confirmado, a janela “desliza” e passa a permitir:

**1, 2 e 3**

e assim por diante.

### Vantagem

Mantém o canal ocupado por mais tempo e melhora bastante o aproveitamento da rede.

> **Janela deslizante = vários quadros podem ficar “em voo” ao mesmo tempo.**

### Ideia principal

Quanto maior a janela, menos o transmissor precisa parar esperando ACK.

Isso é especialmente útil em enlaces com **alta latência**, onde Stop-and-Wait desperdiçaria muito tempo.

**Stop-and-Wait:** 1 quadro por vez  
**Janela deslizante:** vários quadros antes de esperar confirmações

## 10. Go-Back-N x Retransmissão Seletiva

Quando vários quadros são enviados em sequência e um deles dá erro, existem duas estratégias comuns:

### Go-Back-N

Se um quadro for perdido ou chegar com erro, o transmissor **volta até aquele ponto e retransmite ele e todos os quadros seguintes**.

Exemplo:

se o quadro **2** falhou:

**2, 3, 4 e 5** podem ser retransmitidos.

É mais simples de implementar, mas pode desperdiçar banda retransmitindo quadros que já tinham chegado corretamente.

> **Go-Back-N = deu erro? volta e manda tudo dali pra frente de novo.**

### Retransmissão Seletiva

Na retransmissão seletiva, apenas os quadros que realmente deram erro são enviados novamente.

Os quadros recebidos corretamente depois dele podem ser **guardados em buffer** até o quadro faltante chegar.

Exemplo:

se o quadro **2** falhou, mas **3, 4 e 5** chegaram:

- 3, 4 e 5 ficam armazenados;
- somente o **2** é retransmitido.

> **Retransmissão seletiva = só reenviar o que deu errado.**

### Comparando

**Go-Back-N:** mais simples, mas menos eficiente.  
**Retransmissão seletiva:** mais eficiente, mas exige mais controle e memória.

A ideia central do slide é exatamente essa:

> **Go-Back-N sacrifica banda para simplificar. Retransmissão seletiva usa buffer para evitar retransmissões desnecessárias.**

## 11. Problema 4: Meio compartilhado.

![[Pasted image 20260915035532.png]]

