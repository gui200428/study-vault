
# Desenvolvimento Concorrente e Métodos Formais — Aula 04

## Modelo de Desenvolvimento Concorrente

O **Modelo de Desenvolvimento Concorrente**, também chamado de **Engenharia Concorrente**, permite que diferentes atividades do desenvolvimento ocorram **em paralelo**, em vez de exigir que uma etapa termine completamente antes da próxima começar.

Em todas as fases de um projeto podem existir atividades sendo executadas simultaneamente. O processo é conduzido pelas **necessidades do usuário**, pelas **decisões da gerência** e pelos **resultados das revisões**.

> **Resumo:** No desenvolvimento concorrente, várias atividades do projeto podem acontecer ao mesmo tempo e evoluir de acordo com os eventos do projeto.

**Concorrente = atividades em paralelo**

---

## Características do Desenvolvimento Concorrente

O modelo apresenta três características principais:

### Paralelismo

Várias atividades podem ocorrer **simultaneamente**.

Uma equipe pode estar trabalhando em determinada parte do projeto enquanto outra trabalha em uma atividade diferente.

### Iteratividade

As atividades podem ser **revisadas e modificadas** sempre que necessário.

### Flexibilidade

O processo consegue se adaptar rapidamente a mudanças nos **requisitos** e no ambiente de desenvolvimento.

| Característica | Ideia principal |
| --- | --- |
| Paralelismo | Várias atividades ao mesmo tempo |
| Iteratividade | Atividades podem ser revistas |
| Flexibilidade | Adaptação às mudanças |

---

# Estados das Atividades

No Modelo Concorrente, todas as atividades podem existir ao mesmo tempo, porém cada uma pode estar em um **estado diferente**.

Por exemplo, enquanto ocorre uma comunicação com o cliente, uma atividade de análise pode estar em **“aguardando modificações”**. Quando a comunicação termina, essa atividade pode passar para **“em desenvolvimento”**.

O processo é controlado por **eventos**, que provocam transições entre os estados das atividades.

O material apresenta estados como:

- **em desenvolvimento**;
- pronto;
- em revisão;
- revisão completa;
- controlado.

Assim, o modelo não representa simplesmente uma sequência de fases. Ele representa uma **rede de atividades**, cada uma podendo mudar de estado independentemente das outras.

**Evento → mudança de estado**

> **Resumo:** No Modelo Concorrente, cada atividade possui um estado e eventos fazem essas atividades transitarem entre diferentes estados.

---

# Desenvolvimento Concorrente × Desenvolvimento Sequencial

Em um modelo sequencial, as atividades normalmente seguem uma ordem definida.

No Modelo Concorrente, várias atividades podem permanecer ativas simultaneamente e avançar conforme os eventos do projeto.

**Sequencial = uma etapa depois da outra**  
**Concorrente = várias atividades coexistindo**

Essa organização permite visualizar com maior precisão **o estado atual do projeto**, pois cada atividade pode ser acompanhada individualmente.

---

# Concorrência no Software

O material também relaciona concorrência à criação de sistemas que executam **múltiplas tarefas simultaneamente**.

Esse tipo de comportamento é importante em ambientes como:

- sistemas operacionais;
- servidores Web;
- aplicações em tempo real;
- sistemas cliente/servidor;
- sistemas envolvendo software e infraestrutura.

É importante separar as duas ideias:

**Desenvolvimento concorrente = atividades do projeto em paralelo**  
**Software concorrente = tarefas do sistema executadas simultaneamente**

---

# Vantagens do Desenvolvimento Concorrente

## Redução do Tempo de Desenvolvimento

Como várias atividades podem acontecer simultaneamente, o processo pode ser concluído mais rapidamente.

## Melhoria da Qualidade

As revisões contínuas dos requisitos e o feedback rápido ajudam a identificar problemas durante o desenvolvimento.

## Maior Colaboração

Equipes diferentes podem trabalhar conjuntamente em partes distintas do projeto.

**Concorrência = paralelismo + colaboração + rapidez**

---

# Desvantagens do Desenvolvimento Concorrente

## Complexidade de Gerenciamento

Como várias atividades estão acontecendo ao mesmo tempo, é necessário coordenar corretamente as diferentes equipes.

## Riscos de Integração

Componentes desenvolvidos paralelamente podem apresentar conflitos quando forem integrados.

## Dependência de Ferramentas

O desenvolvimento concorrente pode exigir ferramentas adequadas para organizar, sincronizar e acompanhar as atividades.

---

# Tecnologias Relacionadas à Concorrência

O material apresenta diversas tecnologias que utilizam processamento concorrente ou distribuído.

| Tecnologia | Uso de concorrência |
| --- | --- |
| Apache Cassandra | Replicação, particionamento e processamento distribuído |
| Google Bigtable | Processamento paralelo de grandes volumes de dados |
| Apache Kafka | Processamento paralelo de mensagens |
| Hadoop | Processamento distribuído em clusters |
| Elasticsearch | Indexação e buscas em paralelo |
| Redis | Operações de leitura e escrita concorrentes |
| MongoDB | Leituras e escritas concorrentes |
| Azure Cosmos DB | Replicação e processamento paralelo |
| Amazon DynamoDB | Operações paralelas de leitura e escrita |
| Apache Spark | Processamento paralelo de grandes conjuntos de dados |

Essas tecnologias mostram aplicações práticas de **concorrência, paralelismo e processamento distribuído**.

---

# Exemplos de Sistemas Concorrentes

Diversos sistemas modernos precisam executar muitas operações simultaneamente.

### Netflix

Realiza processamento de recomendações, streaming em diferentes qualidades e gerenciamento de grandes volumes de usuários.

### Uber

Processa simultaneamente solicitações de corridas, cálculo de rotas, preços e alocação de motoristas.

### Spotify

Executa streaming, recomendações e gerenciamento de playlists.

### Amazon

Processa pedidos, estoque, recomendações e pagamentos em paralelo.

### Google Maps

Calcula rotas, atualiza informações de trânsito e processa dados de localização simultaneamente.

Outros exemplos apresentados incluem **Facebook, Slack, Airbnb e Microsoft Teams**.

---

# Métodos Formais

Os **Métodos Formais** utilizam **matemática e lógica** para especificar, desenvolver e verificar sistemas de software e hardware.

O objetivo é criar uma descrição precisa do sistema e utilizar técnicas matemáticas para verificar se ele realmente atende às propriedades desejadas.

São especialmente importantes em sistemas onde erros podem provocar consequências graves, como:

- aeronáutica;
- medicina;
- segurança;
- sistemas financeiros.

> **Resumo:** Métodos Formais utilizam matemática para especificar e verificar rigorosamente um sistema.

**Método Formal = especificação matemática + verificação**

---

# Especificação Formal

Antes da implementação, é criado um **modelo formal da solução**, também chamado de **especificação formal**.

Essa especificação utiliza uma linguagem baseada em notação matemática.

A partir dela, podem ser realizadas análises e provas para verificar se o sistema possui as características desejadas.

**Requisito informal → especificação formal**

---

# Verificação, Validação e Implementação

Com o modelo formal criado, podem ser realizadas diferentes atividades.

### Verificação

São utilizadas **provas matemáticas** para verificar se o modelo possui as propriedades especificadas.

### Análise

O modelo pode ser analisado considerando aspectos como desempenho e possíveis estratégias de implementação.

### Validação

A solução pode ser validada através de **simulações**.

### Implementação

O software é desenvolvido de forma que seja possível demonstrar que a implementação está de acordo com a especificação.

**Verificação = provar propriedades**  
**Validação = avaliar o comportamento**

---

# Processo dos Métodos Formais

O processo apresentado no material pode ser resumido como:

**Definição dos requisitos → Especificação formal → Transformações formais → Programa executável → Integração e testes**

A especificação inicialmente informal ou semiformal é transformada em uma representação matemática detalhada.

O material cita algumas notações formais:

- **VDM**;
- **Z**;
- **B**;
- **Larch**.

Depois, são realizados **refinamentos sucessivos** até chegar ao programa executável.

---

# Preservação da Correção

Durante as transformações formais, cada transformação deve **preservar a correção**.

Isso significa que cada nova representação precisa continuar obedecendo às propriedades definidas na especificação anterior.

Assim, é possível demonstrar que o programa final continua de acordo com a especificação original.

**Especificação → refinamentos → programa correto em relação à especificação**

---

# Cleanroom

Um exemplo apresentado de desenvolvimento baseado em Métodos Formais é o **Cleanroom** desenvolvido pela IBM.

Ele utiliza desenvolvimento incremental, no qual a correção de cada estágio é demonstrada em relação ao estágio anterior.

**Cleanroom = incremental + demonstração de correção**

---

# Vantagens dos Métodos Formais

## Precisão

A utilização de uma linguagem matemática reduz **ambiguidades** nos requisitos e no projeto.

## Confiabilidade

Permite verificar de maneira rigorosa se o software atende às propriedades especificadas.

## Segurança

Problemas potenciais podem ser identificados **antes da implementação**.

**Formal = precisão + confiabilidade + segurança**

---

# Desvantagens dos Métodos Formais

## Complexidade

É necessário conhecimento especializado em **matemática e lógica**.

## Custo

A especificação detalhada, as provas e as verificações podem aumentar o tempo e o custo inicial do projeto.

## Adoção Limitada

Nem todos os sistemas precisam do mesmo nível de rigor fornecido pelos Métodos Formais.

---

# Outros Problemas dos Métodos Formais

O material também apresenta algumas dificuldades práticas.

### Necessidade de Profissionais Especializados

Poucos desenvolvedores possuem preparação suficiente para utilizar Métodos Formais, podendo ser necessário treinamento.

### Dificuldade de Formalizar Alguns Aspectos

Algumas características são mais difíceis de representar matematicamente, como aspectos relacionados à **interface com o usuário**.

### Comunicação com o Cliente

Uma especificação matemática pode ser difícil de compreender para clientes sem conhecimento técnico.

---

# Aplicações dos Métodos Formais

Os Métodos Formais são principalmente utilizados quando **segurança, confiabilidade ou precisão** precisam ser garantidas.

| Aplicação | Necessidade principal |
| --- | --- |
| Sistemas críticos | Segurança e confiabilidade |
| Protocolos de comunicação | Correção e segurança |
| Sistemas financeiros | Precisão e integridade dos dados |

### Sistemas Críticos

Exemplos:

- controle de tráfego aéreo;
- sistemas médicos;
- sistemas de defesa.

### Protocolos de Comunicação

Podem ser utilizados em protocolos de rede e criptografia para verificar propriedades relacionadas à comunicação segura.

### Sistemas Financeiros

Sistemas bancários e transações financeiras precisam garantir **precisão e integridade dos dados**.

---

# Métodos de Especificação Formal

Entre os métodos apresentados estão:

- **Método Z**;
- **Método de Gramáticas de Grafos**.

O Método de Gramáticas de Grafos possui uma representação visual e pode descrever naturalmente comportamentos de **sistemas concorrentes**.

---

# Gramáticas de Grafos

As **Gramáticas de Grafos** utilizam grafos para representar estados, componentes e transformações de um sistema.

O material relaciona esse método às **Redes de Petri** e à especificação e simulação de sistemas concorrentes.

Sua principal característica é permitir uma representação **visual** do comportamento e das transformações do sistema.

**Gramática de Grafos = representação visual do sistema**

---

# Notação Z

A **Notação Z** é uma linguagem de especificação formal originalmente criada para sistemas sequenciais.

Existem extensões que permitem representar também sistemas concorrentes através dos processos que compõem o sistema e da comunicação entre esses processos.

Um caso apresentado no material é o **CICS — Customer Information Control System**, da IBM, no qual a utilização da Notação Z ajudou a aumentar a qualidade e a confiabilidade do código.

A Notação Z pode ser utilizada em sistemas nos quais falhas precisam ser fortemente controladas, como:

- sinalização ferroviária;
- aparelhos médicos;
- sistemas de energia nuclear;
- transações bancárias;
- comunicação;
- processadores;
- definição formal da semântica de outras linguagens.

---

# Métodos Formais em Sistemas Críticos

Os Métodos Formais possuem aplicação importante em sistemas nos quais **segurança e confiabilidade precisam ser garantidas antes da entrada em operação**.

Exemplos incluem:

- eletrônica de aeronaves;
- dispositivos médicos;
- sistemas financeiros;
- sistemas ferroviários;
- sistemas de segurança.

Nesses ambientes, descobrir determinados erros apenas depois da implantação pode ser extremamente caro ou perigoso.

---

# Mitos dos Métodos Formais

O material apresenta sete ideias comuns sobre Métodos Formais que não representam completamente seu funcionamento.

| Mito                                      | Realidade apresentada                                                 |
| ----------------------------------------- | --------------------------------------------------------------------- |
| Garantem um programa perfeito             | Reduzem classes de erros, mas não garantem perfeição                  |
| Servem apenas para provar programas       | Também ajudam principalmente na especificação dos requisitos          |
| Só servem para sistemas críticos          | Outros projetos também podem se beneficiar de melhores especificações |
| Utilizam matemática extremamente complexa | A matemática pode ser aprendida com treinamento adequado              |
| Sempre aumentam o custo                   | Mais esforço inicial pode reduzir problemas e retrabalho posteriores  |
| Clientes não conseguem compreender        | Pode-se manter documentação paralela em linguagem natural             |
| Ninguém utiliza na prática                | Existem aplicações reais em diversas empresas                         |

---

## “Métodos Formais garantem um programa perfeito”

Nenhum método consegue garantir que um programa seja completamente perfeito.

Os Métodos Formais conseguem eliminar determinadas classes de problemas e ajudar a encontrar erros ainda na **especificação**, antes da implementação.

**Formal ≠ perfeição absoluta**

---

## “Métodos Formais servem apenas para provar programas”

A prova matemática é apenas uma parte do processo.

Uma das maiores vantagens está em elaborar uma **especificação rigorosa e validável**, ajudando a definir corretamente os requisitos antes da implementação.

---

## “Somente sistemas críticos se beneficiam”

Sistemas críticos recebem grande benefício da verificação formal, mas outros projetos também podem utilizar Métodos Formais para obter requisitos mais precisos e reduzir ambiguidades.

---

## “Métodos Formais envolvem matemática impossível”

A aplicação exige conhecimento matemático e lógico, mas o material destaca que treinamento em **matemática discreta e notações formais** pode reduzir a dificuldade de aprendizado.

---

## “Métodos Formais sempre aumentam o custo”

Existe maior esforço durante a especificação inicial.

Por outro lado, identificar problemas nessa fase tende a ser menos caro do que corrigir defeitos quando o sistema já está sendo implementado.

**Mais esforço na especificação → menos correções posteriores**

---

## “Métodos Formais são incompreensíveis para os clientes”

O cliente não precisa necessariamente trabalhar diretamente com toda a notação matemática.

O material recomenda manter paralelamente uma documentação em **linguagem natural**, permitindo que o cliente acompanhe o desenvolvimento.

---

## “Ninguém utiliza Métodos Formais em projetos reais”

Existem diversas aplicações reais.

O material cita exemplos como:

- **IBM CICS**;
- sistemas da **Tektronix**;
- projetos da **Praxis**.

---

# Exemplos de Aplicação dos Métodos Formais

O material apresenta diversos sistemas que utilizam ou utilizaram técnicas formais.

### CompCert

Compilador C que utiliza provas formais para verificar que o código produzido preserva o comportamento do código-fonte.

### Microsoft Hyper-V

Métodos Formais são utilizados para verificar propriedades relacionadas ao gerenciamento de hardware e isolamento das máquinas virtuais.

### AWS S2N

Implementação de **TLS**, na qual técnicas formais são utilizadas para verificar propriedades de segurança.

### Airbus A380

Métodos Formais são utilizados na verificação de sistemas relacionados ao controle de voo.

### NASA Mars Rover

São utilizados na verificação do software de controle em ambientes críticos.

### Siemens Rail Automation

Aplicados em sistemas de sinalização ferroviária.

O material também apresenta o **Fuchsia OS**, relacionado à verificação de segurança e correção do kernel.

---

# Desenvolvimento Concorrente × Métodos Formais

Apesar de aparecerem na mesma aula, os dois modelos possuem objetivos diferentes.

| Modelo | Ideia principal |
| --- | --- |
| Desenvolvimento Concorrente | Atividades podem acontecer simultaneamente |
| Métodos Formais | Uso de matemática para especificar e verificar o sistema |

**Concorrente = organizar atividades em paralelo**  
**Formal = provar propriedades matematicamente**


## Tabela resumo — 005 — Desenvolvimento Concorrente e Métodos Formais

## Desenvolvimento Concorrente

| Situação / Conceito             | Regra / Ideia principal                                              | Lembrete rápido                    |
| ------------------------------- | -------------------------------------------------------------------- | ---------------------------------- |
| **Desenvolvimento Concorrente** | Permite executar diferentes atividades do projeto ao mesmo tempo     | **atividades em paralelo**         |
| **Outro nome**                  | Engenharia Concorrente                                               | **Concorrente = paralelo**         |
| **Funcionamento**               | Uma atividade não precisa terminar para outra começar                | **não espera terminar**            |
| **Condução do processo**        | Depende das necessidades do usuário, decisões da gerência e revisões | **eventos influenciam o processo** |
| **Estrutura**                   | Várias atividades coexistem e evoluem durante o projeto              | **rede de atividades**             |
**Concorrente = atividades em paralelo.**


| Característica    | Ideia principal                                            | Lembrete rápido        |
| ----------------- | ---------------------------------------------------------- | ---------------------- |
| **Paralelismo**   | Várias atividades acontecem simultaneamente                | **ao mesmo tempo**     |
| **Iteratividade** | Atividades podem ser revistas e modificadas                | **revisar e melhorar** |
| **Flexibilidade** | Processo se adapta a mudanças nos requisitos e no ambiente | **adaptar**            |
**Paralelismo = simultâneo**  
**Iteratividade = revisar**  
**Flexibilidade = adaptar**

# Estados das atividades

|Situação / Conceito|Regra / Ideia principal|Lembrete rápido|
|---|---|---|
|**Atividades**|Podem existir simultaneamente, mas cada uma em um estado diferente|**mesmo tempo, estados diferentes**|
|**Eventos**|Provocam mudança de estado|**evento → transição**|
|**Em desenvolvimento**|Atividade está sendo executada|**fazendo**|
|**Pronto**|Atividade terminou determinada execução|**pronto**|
|**Em revisão**|Resultado está sendo analisado|**conferindo**|
|**Revisão completa**|Revisão foi concluída|**revisado**|
|**Controlado**|Atividade está em situação controlada|**controlado**|

> **Evento → mudança de estado.**

# Concorrente × Sequencial

|Aspecto|Sequencial|Concorrente|
|---|---|---|
|**Execução**|Uma etapa depois da outra|Várias atividades ao mesmo tempo|
|**Dependência**|Maior ordem entre as fases|Atividades podem coexistir|
|**Visualização**|Fluxo mais linear|Rede de atividades|
|**Mudança**|Menos flexível|Maior capacidade de adaptação|

**Sequencial = uma etapa depois da outra**  
**Concorrente = várias atividades coexistindo**

# Desenvolvimento Concorrente × Software Concorrente

|Conceito|Significado|Lembrete rápido|
|---|---|---|
|**Desenvolvimento concorrente**|Atividades do **projeto** são executadas em paralelo|**projeto paralelo**|
|**Software concorrente**|O **sistema** executa várias tarefas simultaneamente|**programa paralelo**|

**Desenvolvimento concorrente = como o software é desenvolvido.**  
**Software concorrente = como o software executa tarefas.**

# Vantagens do Desenvolvimento Concorrente

|Vantagem|Ideia principal|Lembrete rápido|
|---|---|---|
|**Menor tempo**|Atividades simultâneas podem reduzir o tempo total|**paralelo = mais rápido**|
|**Melhoria da qualidade**|Revisões e feedback ajudam a detectar problemas|**problema aparece cedo**|
|**Colaboração**|Diferentes equipes podem trabalhar juntas|**equipes em paralelo**|

**Concorrência = paralelismo + colaboração + rapidez.**

# Desvantagens do Desenvolvimento Concorrente

|Problema|Ideia principal|Lembrete rápido|
|---|---|---|
|**Gerenciamento complexo**|Muitas atividades simultâneas precisam ser coordenadas|**mais coisas acontecendo = mais controle**|
|**Risco de integração**|Componentes paralelos podem entrar em conflito|**juntar pode dar ruim**|
|**Dependência de ferramentas**|Precisa organizar e sincronizar atividades|**coordenação exige ferramenta**|

# Tecnologias relacionadas à concorrência

|Tecnologia|Uso apresentado|
|---|---|
|**Apache Cassandra**|Replicação, particionamento e processamento distribuído|
|**Google Bigtable**|Processamento paralelo de grandes volumes|
|**Apache Kafka**|Processamento paralelo de mensagens|
|**Hadoop**|Processamento distribuído em clusters|
|**Elasticsearch**|Indexação e buscas paralelas|
|**Redis**|Leituras e escritas concorrentes|
|**MongoDB**|Leituras e escritas concorrentes|
|**Azure Cosmos DB**|Replicação e processamento paralelo|
|**Amazon DynamoDB**|Leituras e escritas paralelas|
|**Apache Spark**|Processamento paralelo de grandes conjuntos de dados|

# Exemplos de Sistemas Concorrentes

|Sistema|Operações simultâneas|
|---|---|
|**Netflix**|Streaming + recomendações + usuários|
|**Uber**|Corridas + rotas + preços + motoristas|
|**Spotify**|Streaming + recomendações + playlists|
|**Amazon**|Pedidos + estoque + pagamento + recomendações|
|**Google Maps**|Rotas + trânsito + localização|


# Métodos Formais

| Situação / Conceito | Regra / Ideia principal                                                         | Lembrete rápido          |
| ------------------- | ------------------------------------------------------------------------------- | ------------------------ |
| **Métodos Formais** | Utilizam matemática e lógica para especificar, desenvolver e verificar sistemas | **matemática + lógica**  |
| **Objetivo**        | Produzir uma descrição precisa e verificar propriedades do sistema              | **especificar + provar** |
| **Uso principal**   | Sistemas em que erros podem causar consequências graves                         | **alto risco**           |
| **Áreas citadas**   | Aeronáutica, medicina, segurança e finanças                                     | **sistemas críticos**    |
**Método Formal = especificação matemática + verificação.**


# Especificação Formal

|Conceito|Ideia principal|Lembrete rápido|
|---|---|---|
|**Especificação formal**|Modelo matemático criado antes da implementação|**modelo antes do código**|
|**Linguagem**|Utiliza notação matemática|**formal = matemática**|
|**Análise**|Permite analisar e provar propriedades|**provar antes de implementar**|
|**Transformação**|Requisito informal é convertido em uma descrição formal|**informal → formal**|

# Verificação × Validação

|Conceito|O que faz|Lembrete rápido|
|---|---|---|
|**Verificação**|Utiliza provas matemáticas para verificar propriedades|**PROVAR**|
|**Análise**|Avalia desempenho e estratégias possíveis|**ANALISAR**|
|**Validação**|Pode usar simulações para avaliar a solução|**COMPORTAMENTO**|
|**Implementação**|Produz software de acordo com a especificação|**transformar em programa**|

**Verificação = provar propriedades**  
**Validação = avaliar comportamento**


# Processo dos Métodos Formais

|Ordem|Etapa|
|---|---|
|**1**|Definição dos requisitos|
|**2**|Especificação formal|
|**3**|Transformações formais|
|**4**|Programa executável|
|**5**|Integração e testes|

Requisitos → Especificação formal → Transformações → Programa → Testes


# Preservação da Correção

|Conceito|Regra / Ideia|Lembrete rápido|
|---|---|---|
|**Transformações formais**|Cada transformação precisa preservar as propriedades anteriores|**não perder a correção**|
|**Refinamento**|A representação fica progressivamente mais próxima do programa|**refinar até virar código**|
|**Resultado**|Programa final permanece de acordo com a especificação inicial|**especificação → programa correto**|

## Cleanroom
|Conceito|Ideia principal|Lembrete rápido|
|---|---|---|
|**Cleanroom**|Exemplo de desenvolvimento baseado em Métodos Formais|**IBM**|
|**Desenvolvimento**|Incremental|**em etapas**|
|**Correção**|Cada estágio é demonstrado correto em relação ao anterior|**correção preservada**|
Cleanroom = incremental + demonstração de correção.

# Vantagens dos Métodos Formais

|Vantagem|Ideia principal|Lembrete rápido|
|---|---|---|
|**Precisão**|Matemática reduz ambiguidades|**menos ambiguidade**|
|**Confiabilidade**|Permite verificar propriedades rigorosamente|**mais confiança**|
|**Segurança**|Problemas podem ser encontrados antes da implementação|**erro encontrado cedo**|

Formal = precisão + confiabilidade + segurança.


# Desvantagens dos Métodos Formais

|Problema|Ideia principal|Lembrete rápido|
|---|---|---|
|**Complexidade**|Exige matemática e lógica|**precisa conhecimento especializado**|
|**Custo inicial**|Especificação e provas exigem mais esforço|**mais caro no começo**|
|**Adoção limitada**|Nem todo projeto necessita desse rigor|**nem tudo precisa disso**|
|**Profissionais especializados**|Poucos desenvolvedores dominam as técnicas|**treinamento**|
|**Interface difícil de formalizar**|Nem todos os aspectos são fáceis de representar matematicamente|**UI é complicada de formalizar**|
|**Cliente**|Notação matemática pode ser difícil de compreender|**cliente pode não entender**|

# Quando usar Métodos Formais

| Aplicação                     | Necessidade principal            | Lembrete rápido              |
| ----------------------------- | -------------------------------- | ---------------------------- |
| **Sistemas críticos**         | Segurança e confiabilidade       | **falha não pode acontecer** |
| **Protocolos de comunicação** | Correção e segurança             | **comunicação correta**      |
| **Sistemas financeiros**      | Precisão e integridade dos dados | **dinheiro exige precisão**  |
# Métodos de Especificação Formal

|Método|Característica|Lembrete rápido|
|---|---|---|
|**Método Z**|Utiliza linguagem formal matemática|**Z = notação formal**|
|**Gramáticas de Grafos**|Representação visual através de grafos|**grafos = visual**|

# Gramáticas de Grafos

|Conceito|Ideia principal|Lembrete rápido|
|---|---|---|
|**Gramáticas de Grafos**|Representam estados, componentes e transformações|**representação visual**|
|**Relação**|Relacionadas a Redes de Petri|**concorrência**|
|**Uso**|Especificação e simulação de sistemas concorrentes|**comportamento do sistema**|

# Notação Z

|Situação / Conceito|Ideia principal|Lembrete rápido|
|---|---|---|
|**Notação Z**|Linguagem de especificação formal|**Z = formal**|
|**Origem**|Criada originalmente para sistemas sequenciais|**começou sequencial**|
|**Extensões**|Também podem representar concorrência|**pode representar processos**|
|**CICS**|Exemplo da IBM usando Notação Z|**Z + IBM**|

# Mitos dos Métodos Formais

| Mito                                   | Realidade                                               | Lembrete rápido                   |
| -------------------------------------- | ------------------------------------------------------- | --------------------------------- |
| **“Garantem programa perfeito”**       | Reduzem erros, mas não garantem perfeição               | **formal ≠ perfeito**             |
| **“Só servem para provar programas”**  | Também ajudam a especificar requisitos                  | **não é só prova**                |
| **“Só servem para sistemas críticos”** | Outros projetos também podem se beneficiar              | **uso não é exclusivo**           |
| **“Matemática é impossível”**          | Pode ser aprendida com treinamento                      | **aprendível**                    |
| **“Sempre aumenta custo”**             | Esforço inicial pode reduzir retrabalho depois          | **gasta antes, economiza depois** |
| **“Cliente nunca entende”**            | Pode existir documentação paralela em linguagem natural | **matemática + linguagem comum**  |
| **“Ninguém usa na prática”**           | Existem aplicações reais                                | **é usado de verdade**            |

# Exemplos reais de Métodos Formais

| Sistema                     | Aplicação                          |
| --------------------------- | ---------------------------------- |
| **CompCert**                | Verificação formal de compilador C |
| **Microsoft Hyper-V**       | Hardware e isolamento de VMs       |
| **AWS S2N**                 | Segurança de implementação TLS     |
| **Airbus A380**             | Sistemas de controle de voo        |
| **NASA Mars Rover**         | Software de controle crítico       |
| **Siemens Rail Automation** | Sinalização ferroviária            |
| **Fuchsia OS**              | Segurança e correção do kernel     |

# Comparação final — Concorrente × Formal

|Modelo|Foco|Palavra-chave|
|---|---|---|
|**Desenvolvimento Concorrente**|Organizar atividades simultaneamente|**PARALELO**|
|**Métodos Formais**|Especificar e verificar matematicamente|**PROVAR**|

**Concorrente = atividades em paralelo.**

**3 características:**  
**Paralelismo = simultâneo**  
**Iteratividade = revisar**  
**Flexibilidade = adaptar**

**Evento → mudança de estado.**

**Sequencial = um depois do outro.**  
**Concorrente = vários ao mesmo tempo.**

**Desenvolvimento concorrente = atividades do PROJETO em paralelo.**  
**Software concorrente = tarefas do SISTEMA em paralelo.**

**Vantagens = rapidez + qualidade + colaboração.**  
**Desvantagens = gerenciamento + integração + ferramentas.**

---

**Método Formal = matemática + lógica + verificação.**

**Requisito informal → especificação formal.**

**Verificação = PROVAR propriedades.**  
**Validação = AVALIAR comportamento.**

**Processo:**  
**Requisitos → Especificação Formal → Transformações → Programa → Testes**

**Cada transformação deve preservar a correção.**

**Cleanroom = incremental + demonstração de correção.**

**Vantagens:**  
**Precisão + confiabilidade + segurança.**

**Desvantagens:**  
**Complexidade + custo inicial + especialistas.**

**Gramática de Grafos = representação visual.**  
**Z = especificação formal.**


> **CONCORRENTE = PARALELO**  
> **FORMAL = MATEMÁTICA / PROVA**