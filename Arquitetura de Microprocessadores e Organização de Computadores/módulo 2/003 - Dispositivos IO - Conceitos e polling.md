
![[Pasted image 20251102201406.png]]
**Módulos de entrada e saída:** componentes essenciais. Cada módulo conecta-se ao barramento do sistema e gerencia a comunicação com os periféricos. Utilizando lógica própria para adaptar diferença de velocidade, formato de dados e métodos de operação. Periféricos **não** são conectados diretamente ao barramento devido a problemas de incompatibilidade com o processador. **Os módulos de E/S** atuam como intermediários.

## Dispositivos externos (periféricos):

→ Os periféricos trocam dados com o computador por meio dos módulos de E/S. Os módulos gerenciam sinais de controle, estado e dados entre o sistema e os dispositivos. 

**Classificação dos periféricos:**

**Inteligíveis ao ser humano:** monitores / impressora
**Inteligíveis à máquina:** discos / fitas magnéticas / sensores / atuadores
**Comunicação:** usado para troca de dados com dispositivos remotos. (Ex: módulo wifi usb / módulo Bluetooth)

**Importante:** mesmo que discos e fitas façam parte da hierarquia de memória, são tratados como periféricos por serem controlados por módulos E/S.

**Comunicação:**
→ Periféricos se comunicam com o módulo E/S por meio de sinais de **controle / dados e estado.**

**Sinais de controle:** sinais enviados pela CPU por meio do barramento de controle, definem ações como leitura, escrita ou comandos específicos (ex: movimentar a cabeça de um disco). 

**Dados:** bits trocados entre o periférico e o módulo de E/S.

**Sinais de estado:** indica a condição do dispositivo (Ex: ready / not ready para operar).

**Importante:** cada dispositivo possui uma **lógica de controle** que responde aos comandos do módulo de E/S. Dois componentes são fundamentais para essa comunicação ocorrer:
**Transdutor:** Converte sinais elétricos em outras formas de energia (e vice-versa). (Ex: código interpretado e convertido em sinais para exibição ou execução de funções de controle.)
**Buffer:** Associado ao transdutor, ele tem a função de armazenar temporariamente os dados, com o objetivo de sincronizar a informação e não perder dados.


## Teclado / monitor:

→ Principais meios de interação entre o usuário e o computador. 
**Teclado:** envia caracteres codificados ao computador. Cada caractere possui um código binário único. Ao pressionar uma tecla, o transdutor do teclado converte o sinal físico em código binário, é enviado ao módulo de E/S.
**Monitor:** exibe informações recebidas do sistema. 


## Módulos de E/S

**Função do módulo:**
1. Controle e temporização
2. Comunicação com o processador
3. Comunicação com o dispositivo
4. Buffering de dados
5. Detecção de erros

**Exemplo de funcionamento:**
→ Transferência de dados de um dispositivo externo ao processador.
1- Processador interroga o módulo de E/S para verificar o estado do dispositivo
2- O módulo de E/S retorna o estado do dispositivo.
3- **Dispositivo operacional e pronto para transmitir:** processador solicita a transferência de dados por meio de um comando ao módulo de E/S
4- O módulo de E/S obtém uma unidade de dados (ex: 8 / 16 bits) do dispositivo externo.
5- Os dados são transferidos do módulo de E/S para o processador.


## Comunicação do processador

→ As interações entre o processador e o módulo de E/S envolvem algumas arbitrações de barramento. 
→ O módulo de E/S precisa se comunicar com o processador e com o dispositivo externo.

**Decodificação de comando:** módulo de E/S aceita comandos do processador, enviados como sinais no barramento de controle. (Ex: módulo de E/S para a unidade de disco, aceita comandos como: READ SECTOR, WRITE, SECTOR, SEEK numero de trilha e SCAN ID de registro.)

**Dados:** dados são trocados entre o processador e o módulo de E/S pelo barramento de dados.

**Informações de estado:** os periféricos são muito lentos, é importante conhecer o estado em que se encontra o módulo de E/S (BUSY/READY). (Ex: módulo de E/S esta ocupado processando o comando de E/S anterior, estado: BUSY. Nesse estado, ele não pode processar novas informações e mandar para o processador.).
Existem estados para informar diversas condições de erro.

**Reconhecimento de endereço:** cada dispositivo de E/S possui um endereço. Dessa forma, um módulo de E/S deve reconhecer um endereço exclusivo para cada periférico que controla.


## Buffering

→ Função muito importante para os módulos de E/S, ele serve para lidar com as diferenças de velocidade entre memória/processador e periféricos. Serve como forma de sincronia e impede a perda de informações. 
→ Os dados são armazenados temporariamente em um buffer no módulo de E/S para permitir transferências eficientes.
→ **O módulo de E/S é responsável por detecção e relatório de erros** sendo eles mecânicos, elétricos ou de transmissão. Usa códigos de detecção, como o **bit de paridade**, que verifica se ocorreu alguma alteração nos dados durante a transferência.


## Estrutura do módulo de E/S

→ Os módulos variam em complexidade e quantidade de dispositivo que controlam. Porem seguem uma estrutura básica:

**Sendo:**

- Conectam-se ao computador por linhas de sinal (barramento).
- Possuem **registradores de dados** para armazenar informações. (**Linha de dados**)
- Possuem **registradores de estado / controle** para indicar condições e receber comandos. (**Linha de controle**)
- Possuem lógica para comunicação com o processador e para gerar/interpretar endereços dos dispositivos.
- Possuem circuitos específicos para interface com cada periférico.

→ **Função principal do módulo de E/S:** simplificar a interação do processador com diversos dispositivos, ocultando detalhes de temporização e formato. (Serve como um tradutor, traduzir para o processador o que exatamente ele precisa fazer).

**Tipos:**

- **Controlador de E/S:** simples, exige controle direto do processador (ex: comum em microcomputadores). (Ex: conector HDMI).
- **Canal de E/S:** mais avançado, assume grande parte do processamento e oferece interface de alto nível (usado em mainframes, informações criticas.).


![[Pasted image 20251103115138.png]]


## Polling:

**Definição:** método mais simples que existe para verificar qual módulo esta pronto para uso. Comunicação entre a CPU e dispositivos de de E/S baseado em **consulta ativa**. A CPU verifica periodicamente se um dispositivo está pronto para enviar ou receber dados.

**Funcionamento:**
- CPU executa um loop de verificação: lê o **registrador de estado** do dispositivo e verifica se está pronto. (Ex: bit READY = 1).
- Quando o dispositivo está pronto: CPU realiza a operação (leitura/escrita).
- Repete o processo para todos os dispositivos.


**Vantagens x Desvantagens - Polling:**

**Vantagens:**
- Simples de implementar
- Bom para sistemas com poucos dispositivos / baixa taxa de eventos

**Desvantagens:**
- Ineficiente, a CPU desperdiça ciclos verificando dispositivos ociosos.
- Não é escalável para sistemas com muitos periféricos.
- Pode causar latência em operações criticas.

