# Redes Quiz

Extraído diretamente do atributo interno `data-app-data` do artefato **Redes Quiz** no NotebookLM. O objeto contém exatamente 30 perguntas. A interface pode embaralhar a ordem das alternativas em cada execução; por isso, abaixo a resposta correta está marcada com **✅**.

## 1. Atraso nodal

Um engenheiro de redes precisa calcular o atraso nodal total ($d_{nodal}$) em um roteador de núcleo. O pacote possui $1500$ bytes, o link de saída opera a $1\ Gbps$, o processamento lógico leva $10\ \mu s$ e o buffer está com uma taxa de ocupação que gera um atraso de fila de $20\ \mu s$. Desprezando o atraso de propagação, qual o valor de $d_{nodal}$?

- **✅ $42\ \mu s$**
- $31,2\ \mu s$
- $1512\ \mu s$
- $22,5\ \mu s$

## 2. Resiliência digital e governança de dados

De acordo com a norma ISO/IEC 27002:2022 e as tendências projetadas para 2026, quais elementos são considerados críticos para a resiliência digital e governança de dados em uma infraestrutura moderna? *(Selecione todas as corretas.)*

- **✅ A transição do perímetro físico para a Identidade (IAM) como centro de controle de segurança.**
- **✅ O uso de plataformas de segurança baseadas em IA para mitigar vetores de ataque em milissegundos.**
- **✅ A implementação de micro-segmentação para impedir movimentos laterais em redes com dispositivos IoT.**
- A eliminação completa de logs de autenticação para reduzir a latência de processamento em nuvens multicloud.

## 3. Lei de Shannon-Nyquist

Pela Lei de Shannon-Nyquist, o aumento da taxa de bits em uma transmissão digital exige, matematicamente, uma expansão correspondente na ___ do canal físico para manter a integridade da informação.

**Gabarito:** largura de banda.

## 4. Relay e Gateway no SMTP

No modelo de protocolo SMTP (RFC 5321), qual a diferença fundamental entre a responsabilidade de um “Relay” e a de um “Gateway”?

- **✅ O Gateway pode transformar o conteúdo e cabeçalhos da mensagem ao cruzar domínios de transporte, enquanto o Relay deve apenas adicionar informações de rastreamento.**
- O Relay é responsável pela entrega final ao usuário, enquanto o Gateway apenas encaminha o pacote para o próximo salto IP.
- Sistemas de Gateway não utilizam registros MX do DNS, operando exclusivamente por roteamento estático.
- O Relay altera o caminho de retorno (reverse-path) para seu próprio endereço, enquanto o Gateway mantém o original.

## 5. Atenuação em decibéis

Um sinal sofre uma atenuação de $20\ dB$ ao percorrer um cabo de cobre. Se a potência inicial na fonte era de $100\ mW$, qual será a potência aproximada do sinal ao chegar ao destino?

- **✅ $1\ mW$**
- $10\ mW$
- $0,5\ mW$
- $80\ mW$

## 6. Bufferbloat

Explique o paradoxo do “Bufferbloat” em roteadores e por que o aumento indiscriminado da memória de buffer não resolve problemas de congestionamento.

**Resposta-modelo:** O Bufferbloat ocorre quando buffers excessivamente grandes ocultam o congestionamento da rede ao armazenar pacotes em vez de descartá-los. Isso impede que protocolos de transporte, como TCP, detectem a saturação e reduzam a velocidade, resultando em pacotes que expiram na fila e geram retransmissões redundantes, o que colapsa a fluidez.

## 7. Sinal NRZ e transmissão por rádio

Por que o sinal digital puro (NRZ/banda-base) é considerado inadequado para a transmissão via rádio (wireless)?

- **✅ Porque sua energia concentra-se em $0\ Hz$ (corrente contínua), exigindo antenas de dimensões impraticáveis para propagação.**
- Porque o sinal NRZ é inerentemente imune a ruídos, impossibilitando a modulação por amplitude.
- Porque a Transformada de Fourier (FFT) do sinal NRZ é uma senóide perfeita que interfere no Wi-Fi.
- Porque sinais em banda-base viajam apenas na velocidade da luz no vácuo, perdendo sincronia no ar.

## 8. Reverse-path nulo no SMTP

Em uma transação SMTP, quais condições permitem que um servidor aceite um comando `MAIL FROM` com um reverse-path nulo (`<>`)? *(Selecione todas as corretas.)*

- **✅ No envio de notificações de mensagens não entregues (bounces).**
- **✅ No envio de notificações de status de entrega (DSNs) ou Message Disposition Notifications (MDNs).**
- Quando o cliente deseja ocultar sua identidade por motivos de segurança e privacidade (BCC).
- Para testar a validade de uma caixa postal sem efetivamente entregar dados.

## 9. Controle de fluxo

O controle de fluxo na camada de enlace que permite ao transmissor enviar múltiplos quadros antes de receber uma confirmação, mantendo o “canal preenchido”, é conhecido como ___.

**Gabarito:** janela deslizante.

## 10. Fibra óptica

Sobre a mecânica da fibra óptica, qual fenômeno físico permite que a luz percorra centenas de quilômetros confinada no núcleo do vidro com baixíssima atenuação?

- **✅ Reflexão Total Interna.**
- Indução Eletromagnética de Fótons.
- Amplificação Térmica por Radiação.
- Difração de Shannon.

## 11. Comutação de circuitos e de pacotes

Diferencie a Comutação de Circuitos da Comutação de Pacotes sob a perspectiva de ociosidade e eficiência de recursos.

**Resposta-modelo:** A comutação de circuitos reserva um caminho físico dedicado, garantindo capacidade, mas gerando desperdício total de recursos se não houver tráfego. Já a comutação de pacotes utiliza compartilhamento estatístico e malha dinâmica, permitindo que múltiplos usuários usem o mesmo link conforme a demanda, sendo ideal para tráfego intermitente, embora sem garantias nativas de atraso.

## 12. Migração da ISO 27001

Um auditor de sistemas analisa uma política de segurança baseada na ISO 27001:2022. Qual a data limite (“prazo fatal”) para que organizações migrem seus certificados da versão 2013 para a versão 2022?

- **✅ 31 de outubro de 2025**
- 22 de setembro de 2026
- 1 de janeiro de 2028
- 31 de dezembro de 2029

## 13. IA no Edits do Instagram

Na arquitetura de um app de edição como o “Edits” do Instagram, quais funcionalidades utilizam Inteligência Artificial para facilitar o processo criativo? *(Selecione todas as corretas.)*

- **✅ Animação de imagens estáticas em vídeos.**
- **✅ Recurso de legendagem automática em vários idiomas.**
- Sugestão de insights baseados em dados para otimizar estratégia de conteúdo.
- Ajuste preciso de clipes na linha do tempo por milissegundos.

## 14. Atraso de propagação

Se um bit de dados na camada física viaja em um cabo de fibra óptica a aproximadamente $200.000\ km/s$, qual o atraso de propagação ($d_{prop}$) mínimo para um pacote atravessar uma distância de $4.000\ km$?

- **✅ $20\ ms$**
- $13,3\ ms$
- $40\ ms$
- $2\ ms$

## 15. Início da transação SMTP

Segundo a RFC 5321, o comando SMTP que deve ser utilizado pelo cliente para informar o início de uma transação e fornecer o endereço do remetente para relatórios de erro é o ___.

**Gabarito:** `MAIL FROM`.

## 16. Desvantagem da arquitetura em camadas

Qual é a principal desvantagem da arquitetura em camadas (como o modelo OSI) na engenharia de redes?

- **✅ Overhead de processamento e latência devido à adição sucessiva de cabeçalhos (encapsulamento).**
- Falta de interoperabilidade entre fabricantes de hardware diferentes.
- Dificuldade de manutenção, pois falhas em uma camada afetam obrigatoriamente todas as outras.
- Incapacidade de suportar novos protocolos sem redesenhar toda a arquitetura física.

## 17. CSMA/CA

O protocolo CSMA/CA (Carrier Sense Multiple Access with Collision Avoidance) é utilizado em redes sem fio. Quais características o definem? *(Selecione todas as corretas.)*

- **✅ Uso de espera aleatória (backoff) antes de transmitir para minimizar colisões.**
- **✅ “Paciência matemática”: ouvir o meio e aguardar se estiver ocupado.**
- Capacidade de ouvir a colisão enquanto fala e interromper a transmissão imediatamente.
- Reserva de banda exclusiva via comutação de circuitos lógicos.

## 18. Erro SMTP 550

Um servidor SMTP retorna o código de erro `550` após um comando `RCPT TO`. O que isso indica para o cliente?

- **✅ Uma falha permanente: o endereço de destino não existe ou a entrega foi negada por política.**
- Uma falha temporária: o servidor está sobrecarregado, e o cliente deve tentar novamente mais tarde.
- Que o comando foi aceito, mas o servidor aguarda o início da transferência de dados (`DATA`).
- Um erro de sintaxe no comando SMTP, indicando que o comando não foi reconhecido.

## 19. Media Access Control

Em uma rede multiponto, o desafio crítico de coordenar a fala e evitar colisões de sinais concorrentes exige o uso de protocolos de ___ (Media Access Control).

**Gabarito:** controle de acesso ao meio.

## 20. Endereços MAC e IP

Qual a principal diferença entre o Endereço Físico (MAC) e o Endereço Lógico (IP) em termos de escopo e mutabilidade?

- **✅ O MAC é imutável (gravado no hardware) e tem escopo local, enquanto o IP é hierárquico, mutável e tem escopo global.**
- O MAC é utilizado para roteamento entre diferentes países, enquanto o IP serve apenas para identificação dentro de um switch.
- O endereço IP possui 48 bits e é fixo, enquanto o MAC possui 32 bits e muda a cada conexão Wi-Fi.
- Ambos são identidades lógicas atribuídas por software e mudam dinamicamente via servidor DHCP.

## 21. Fibra óptica em backbones globais

De acordo com o “The Physical Cloud”, por que a fibra óptica é o campeão absoluto para backbones globais em comparação ao cabo de cobre? *(Selecione todas as corretas.)*

- **✅ Imunidade virtual a interferências eletromagnéticas (ruído).**
- **✅ Capacidade teórica colossal de largura de banda (até $30.000\ GHz$).**
- **✅ Fótons podem viajar até $100\ km$ sem necessidade de amplificação mecânica.**
- Custo de instalação inferior para levar o sinal até residências rurais (último quilômetro).

## 22. Modulação e domínio da frequência

O que ocorre com um sinal modulado (ASK ou BPSK) no domínio da frequência, conforme revelado pela Transformada de Fourier?

- **✅ A energia do sinal é “teletransportada” do marco zero ($0\ Hz$) para a frequência da onda portadora (ex.: $100\ MHz$).**
- O sinal é convertido em corrente contínua pura para evitar a distorção por reflexão.
- A largura de banda do sinal é reduzida a zero para economizar espaço no espectro eletromagnético.
- O sinal torna-se uma onda quadrada perfeita de amplitude infinita no vácuo.

## 23. Computação Confidencial

Segundo as previsões da Gartner e da Avalon IT para 2029, o que é a “Computação Confidencial” e qual sua finalidade em infraestruturas não confiáveis?

**Resposta-modelo:** A Computação Confidencial é uma tecnologia que visa proteger os dados não apenas em trânsito ou repouso, mas especificamente “em uso”, ou seja, durante o processamento. Sua finalidade é garantir a resiliência e privacidade em ambientes de nuvem onde a infraestrutura subjacente pode não ser totalmente confiável.

## 24. Link mais rápido e atraso nodal

Um engenheiro decide migrar um link de $1\ Gbps$ para $10\ Gbps$ em um nó que sofre com alta latência. Qual componente específico do atraso nodal será mitigado por essa ação?

- **✅ Atraso de Transmissão ($d_{trans}$)**
- Atraso de Propagação ($d_{prop}$)
- Atraso de Processamento ($d_{proc}$)
- Atraso de Fila ($d_{queue}$)

## 25. Verificação de caixa postal no SMTP

O mecanismo do protocolo SMTP que permite confirmar se um endereço identifica um usuário ou caixa postal sem iniciar uma transação de envio é o comando ___.

**Gabarito:** `VRFY`.

## 26. Bit Stuffing

Qual é a função do “Bit Stuffing” na camada de enlace?

- **✅ Garantir que a sequência de flag (ex.: $01111110$) não apareça acidentalmente nos dados, inserindo um “0” após cinco “1” consecutivos.**
- Aumentar a taxa de bits da rede artificialmente para preencher lacunas de silêncio.
- Criptografar os bits de cabeçalho para proteger contra ataques de espionagem.
- Corrigir erros de paridade inserindo bits redundantes em cada byte.

## 27. Identidades de máquina

No contexto de Governança de TI (ISO 27002), quais são as identidades de máquina que expandiram massivamente a superfície de ataque nas redes modernas? *(Selecione todas as corretas.)*

- **✅ Dispositivos IoT (Internet das Coisas).**
- **✅ Sensores Industriais (OT).**
- **✅ Agentes de Inteligência Artificial.**
- Sistemas de Telefonia Analógica Tradicional.

## 28. Queda de 6 dB

Como a regra “o sinal cai $6\ dB$ sempre que a distância dobra” se aplica à propagação em espaço livre?

- **✅ A energia se espalha radialmente seguindo a Lei do Inverso do Quadrado, resultando em uma perda de $3/4$ da potência original a cada dobra.**
- O sinal ganha potência devido à reflexão na ionosfera, compensando a distância.
- A perda é linear, caindo exatamente $6\ Watts$ a cada quilômetro percorrido.
- A regra aplica-se apenas a cabos de fibra óptica, onde a luz não sofre dispersão radial.

## 29. Half-Duplex

O modo de transmissão bidirecional onde a comunicação ocorre nos dois sentidos, mas nunca simultaneamente (ex.: Walkie-Talkie), é denominado ___.

**Gabarito:** Half-Duplex.

## 30. Zero Trust

Em uma arquitetura Zero Trust (ZTA), qual é o princípio fundamental aplicado a cada solicitação de acesso à rede?

- **✅ Nunca confiar, sempre verificar.**
- Confiar, mas verificar apenas se houver anomalias.
- Confiança total para dispositivos dentro da rede local (LAN).
- Acesso irrestrito baseado exclusivamente no endereço MAC do hardware.
