#faculdade #aom #resumos 
## E/S Programada vs E/S por interrupção

### E/S programada - Polling

→ Método em que o processador precisa verificar continuamente o status do módulo de E/S. Ele é ineficiente, pois consome tempo e degrada o desempenho do sistema, fazendo com que o processador fique ocioso durante a espera pelo módulo.


### E/S por interrupção
→ Método em que o processador envia o comando de E/S e **continua executando outras tarefas.** Quando o módulo de E/S estiver pronto, ele **interrompe a tarefa atual do processador**. O processador salva todo o estado da tarefa atual nos registradores. O processador passa a realizar a transferência de dados do módulo E/S. Quando acaba, ele restaura os dados salvos no registrador e volta a atividade anterior.

**Resumindo:**
1. Processador envia o comando de E/S
2. Processador continua executando outras tarefas
3. Módulo E/S **sinaliza** e interrompe o processo atual do processador
4. O processador **salva o contexto** da tarefa atual
5. O processador **executa a transferência de dados**
6. O processador **restaura o contexto da tarefa anterior**

**Limitações:**
→ Apesar de ser melhor que o polling, **cada palavra de dados** passa pelo processador, o que pode consumir tempo em operações maiores.


## Pilha

→ Área da memória organizada no formato **LIFO (last in, first out)**. Ultimo dado que entra é o primeiro a sair.
→ Usado para armazenar dados temporários:
- Endereço da próxima instrução
- Estado do processador
- Conteúdo dos registradores

**Usada quando ocorrem interrupções no processamento**
- Processador pausa o programa atual e executa a rotina de tratamento
- Processador salva o contexto atual do programa na pilha (Garantindo que volte exatamente de onde parou).
- Depois que a interrupção é tratada, os dados são **restaurados da pilha**, possibilitando a continuidade do programa sem perda de informações.


## Processamento de interrupção - de forma detalhada

→ Ocorre quando um dispositivo de E/S conclui uma operação, enviando um **sinal de interrupção** para o processador. 

**1- Sinal de interrupção:** dispositivo de E/S envia um sinal de interrupção ao processador

**2- Finalização da instrução atual:** o processador termina a instrução atual

**3- Reconhecimento da interrupção:** processador detecta a interrupção, confirma ao dispositivo o recebimento do sinal, dispositivo remove o sinal

**4- Salvamento do contexto:** processador salva o estado atual (conteúdo dos registradores, PSW e contador de programa) na pilha. A pilha armazena essas informações usando o método LIFO (ultimo que entra primeiro que sai). Ela é importante para não acontecer perda de informações.

**5- Desvio para a rotina de tratamento:** O endereço da rotina é carregado no contador de programa

**6- Execução da rotina:** rotina salva os registradores, processa a interrupção, verifica o status do dispositivo e transmite dados se preciso.

**7- Restauração do contexto:** registradores, PSW e contador de programa são restaurados da pilha. (Usando o método lifo)

**8- Retorno ao programa original:** processador volta a executar as instruções do programa original. Exatamente de onde parou.


**Pilha:** permite que o contexto do programa não seja perdido. Permitindo que o processador volte a executar as informações do programa exatamente de onde parou.

## Aspecto de projeto - implementação

**Desafios:**
1. Identificar qual dispositivo gerou a interrupção.
2. Definir qual das interrupções será atendida primeiro (prioridade).

**Técnicas para identificação do dispositivo:**

→ **Múltiplas linhas de interrupção:** cada linha indica um grupo de dispositivos. Implementação simples, porem limitada ao número de pinos.
**Prioridade:** prioridade pela linha.

→ **Verificação por software:** Processador consulta cada módulo para descobrir quem pediu a interrupção. Implementação lenta.
**Prioridade:** ordem de varredura define a prioridade.

→ **Daisy chain (interrupção vetorizada):** Verificação por hardware.  Um sinal percorre os dispositivos em cadeia até o requisitante, que envia um envia um vetor (endereço) ao processador.
Quando o sinal chega no dispositivo, ele manda o id único para o processador ler.
**Prioridade:** ordem física na cadeia define prioridade.

→ **Arbitragem de barramento (vetorizada):** O dispositivo precisa ganhar o controle do barramento para enviar o vetor ao processador.
**Prioridade:** usa o esquema de prioridade.


## Desvantagens da E/S programada e por interrupção


**E/S programada - polling:**
- Processador fica totalmente ocupado com a transferência de dados, impede que ele execute outras tarefas simultaneamente.
- Desperdício de ciclos do processador.

**E/S por interrupção**
- Depende do processador para realizar as transferências, diminuição da taxa de transferência.

**Desvantagens em comum:**
- Baixa taxa de transferência, a velocidade da transferência de dados é limitada pelo capacidade do processador de testar e atender os dispositivos de E/S
- Alto uso do processador, o processador precisa executar várias instruções para gerenciar cada transferência de E/S. Consumindo tempo e recursos que poderiam ser usados em outras tarefas.

**Solução:**
→ Para grandes volumes de dados, podemos usar o DMA (acesso direto à memória). Permite a transferência de dados diretamente entre a memória e os dispositivos de E/S. Sem envolver o processador.


## Função do DMA

→ O DMA é um módulo que permite a transferência de dados entre a memória e dispositivos de E/S **sem envolver o processador diretamente.**

**Funcionamento:**
→ Processador envia ao DMA:
- Tipo de operação
- Endereço do dispositivo de E/S
- Endereço inicial na memória
- Quantidade de dados a transferir

1. DMA realiza a transferência **diretamente pela memória,** uma palavra por vez.
2. Quando acaba, o DMA envia uma **interrupção** ao processador para informar que terminou.


**Roubo de ciclo - DMA**
1. DMA suspende temporariamente o processador para usar o barramento e transferir dados
2. **Essa interrupção não é tradicional,** o processador não salva o estado, apenas é pausado por um ciclo.

**Vantagens:**
- Processador liberado para outras tarefas
- Maior eficiência, o DMA é muito mais eficiente que E/S programada ou por interrupção.


## Configurações possíveis para o DMA:

**1. DMA compartilhando o barramento com todos os módulos** - Método simples, mas pouco eficiente. 

**2. DMA com caminho direto para módulos de E/S** - reduz uso do barramento do sistema.

**3. DMA com barramento dedicado de E/S** - melhora a escalabilidade e eficiência

