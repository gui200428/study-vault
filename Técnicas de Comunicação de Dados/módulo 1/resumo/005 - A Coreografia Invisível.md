A **camada física** transporta sinais por um meio que o slide chama de **caótico**. A **camada de enlace** organiza esses sinais para oferecer à **camada de rede** uma comunicação que pareça ordenada. O slide chama isso de “ilusão da perfeição”; o nível de garantia, porém, depende do serviço usado.

## Níveis de serviço do enlace

| Serviço                          | Garantia apresentada                                 | Exemplo do material |
| -------------------------------- | ---------------------------------------------------- | ------------------- |
| **Sem conexão, sem confirmação** | Baixa sobrecarga; não há confirmação de cada quadro. | Ethernet.           |
| **Sem conexão, com confirmação** | Confirma a recepção, com sobrecarga intermediária.   | Wi-Fi.              |
| **Orientado a conexões**         | Maior confiabilidade, com conexão estabelecida.      | Satélite.           |

## Enquadramento: onde o dado começa?

O sinal chega como uma sequência contínua de bits. O **enquadramento** separa essa sequência em **quadros**, blocos lógicos com limites reconhecíveis. O problema é impedir que um padrão de dados seja confundido com um marcador de limite (**FLAG**).

- **Byte stuffing:** se `FLAG` aparecer nos dados, coloca-se o caractere de escape **ESC** antes dele: `FLAG` nos dados → `ESC FLAG`. Assim, o receptor o interpreta como conteúdo.
- **Bit stuffing:** insere-se um bit `0` após **cinco bits `1` consecutivos**. No exemplo visual do slide, `011111010`, o `0` logo após os cinco `1` é o bit inserido; o receptor o remove.

![[Pasted image 20260927222614.png]]

## Controle de erros: detectar e recuperar

### CRC: detecção por redundância cíclica

O **CRC (Redundância Cíclica)** usa um cálculo para acrescentar informação de verificação ao quadro. No esquema do slide, a mensagem **$M(x)$** é dividida pelo gerador **$G(x)$**; o resto de verificação **$R(x)$** é anexado à mensagem, formando **$M(x)\mid R(x)$**. O desenho apresenta essa ideia sem detalhar a conta. Na recepção, a redundância permite verificar se houve erro causado pelo ruído. **Detectar** um erro não recupera, por si só, o dado alterado.

### ARQ: recuperação por retransmissão

O **ARQ** usa **temporizadores** e **números de sequência**. O transmissor envia um quadro e aguarda confirmação (**ACK**). Se a confirmação não chegar antes do tempo limite, retransmite. O número de sequência identifica o quadro e ajuda a distinguir uma retransmissão de um quadro novo. Assim, **CRC detecta** o problema e **ARQ pode recuperar** por novo envio.

## Controle de fluxo e aproveitamento do canal

### Stop-and-Wait

Para não sobrecarregar o receptor, o transmissor envia **um quadro por vez** e espera o **ACK** antes do próximo. O diagrama mostra o quadro indo do *Transmitter* ao *Receiver* e o ACK voltando enquanto o transmissor permanece bloqueado. É simples, mas o canal fica ocioso durante a espera.

![[Pasted image 20260927222615.png]]

### Piggybacking

Quando há dados no sentido contrário, o **ACK pega carona** nesse tráfego de retorno. Embutir a confirmação no quadro de dados reduz o uso de quadros separados e melhora o aproveitamento da banda.

### Janelas deslizantes

O **Stop-and-Wait** espera a cada quadro. Uma **janela deslizante** permite manter vários quadros em trânsito antes das confirmações, preenchendo melhor o canal. No desenho, a janela cobre os quadros **0, 1 e 2**; quando avança, passa a admitir o próximo quadro da sequência.

![[Pasted image 20260927222616.png]]

### Go-Back-N × retransmissão seletiva

Se o quadro **2** falhar depois do envio de **1 a 5**, as duas estratégias tratam os quadros posteriores de formas diferentes:

| Estratégia | Tratamento de 3, 4 e 5 | Novo envio |
| --- | --- | --- |
| **Go-Back-N** | Descarta os quadros posteriores ao erro. | Retransmite **2, 3, 4 e 5**. |
| **Retransmissão seletiva** | Guarda **3, 4 e 5** em **buffer**. | Retransmite apenas **2**. |

O contraste do slide é **“descarte implacável”** contra **“memória seletiva”**: guardar os quadros corretos evita repeti-los, mas exige buffer e controle.

![[Pasted image 20260927222617.png]]

## Acesso ao meio compartilhado

Quando vários dispositivos compartilham o mesmo meio, transmissões simultâneas podem **colidir**. A subcamada **MAC** coordena o **acesso múltiplo**: quem usa o canal e em que momento.

### CSMA/CD: redes cabeadas

O dispositivo **ouve** o meio, **transmite** quando pode e continua verificando se houve colisão. Se detectar uma, **recua** e tenta novamente após uma espera. No **recuo exponencial** indicado pelo slide, colisões repetidas ampliam a faixa possível de espera antes de uma nova tentativa.

### CSMA/CA: redes sem fio

A estratégia é **evitar** a colisão: ouvir o meio e aplicar **espera aleatória** antes da transmissão. O desenho mostra os nós **A, B e C** disputando o canal e destaca a espera aleatória. Assim, **CD detecta** uma colisão depois que ocorre; **CA procura preveni-la**.

![[Pasted image 20260927222618.png]]

O diagrama final apresenta a **abstração completa** da camada de enlace: uma engenharia invisível que busca garantir a confiança da rede por meio de quatro funções:

- **Acesso ao meio**
- **Enquadramento**
- **Controle de erros**
- **Controle de fluxo**