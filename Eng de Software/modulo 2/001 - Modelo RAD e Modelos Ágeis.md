## Modelo RAD (Rapid Application Development)

O **RAD — Rapid Application Development**, também chamado de **Desenvolvimento Rápido de Aplicação**, é um modelo de processo **iterativo e incremental** que enfatiza um ciclo de desenvolvimento **extremamente curto: entre 60 e 90 dias**.

Ou seja, junta as duas ideias vistas no módulo 1: repete ciclos para melhorar (iterativo) e vai entregando partes do sistema (incremental). A diferença é que tudo isso precisa caber num prazo bem apertado.

### Características

- **Alta velocidade de entrega** → conseguida pela **reutilização de componentes pré-existentes**.
- **Prototipagem rápida** → permite **validação contínua com o cliente**.
- **Iterações curtas** → com **feedback constante**.
- **Equipe multidisciplinar** → com **envolvimento direto do cliente**.

![[Pasted image 20261024213105.png|550]]

O ciclo começa com **análise e projeto rápido** (*analysis and quick design*), entra nos **ciclos de protótipo** (*build → demonstrate → refine*: constrói, mostra para o cliente e refina) e só depois segue para **testes** e **implementação**.

> **Resumo:** RAD = desenvolvimento iterativo e incremental, muito rápido (60 a 90 dias), apoiado em reuso de componentes e protótipos validados com o cliente.

**RAD = rápido + reuso + protótipo**  
**RAD = 60 a 90 dias**

---

## Fases do RAD

De acordo com alguns autores, o processo RAD se divide em **5 fases**:

1. **Modelagem de Negócio:** modela o fluxo de informações entre as funções de negócio, levantando os **processos suportados pelo sistema**. Responde:
   - Que informação direciona o processo de negócio?
   - Que informação é gerada?
   - Quem a gera?
   - Para onde vai a informação?
   - Quem a processa?
2. **Modelagem dos Dados:** responde a um conjunto de questões específicas relevantes a qualquer aplicação. O fluxo definido na modelagem de negócio é **refinado** para extrair os **principais objetos de dados**: a composição de cada um, onde costumam ficar, a relação entre eles e a relação entre os objetos e os processos que os transformam.
3. **Modelagem do Processo:** os objetos de dados são **transformados** para conseguir o fluxo necessário para implementar uma função do negócio. Aqui são criadas as descrições de processamento para **adicionar, modificar, descartar ou recuperar** um objeto de dados.
4. **Geração da Aplicação:** usa **técnicas de quarta geração**, **reutiliza componentes** de programa existentes quando possível (ou cria componentes reusáveis) e usa **ferramentas automatizadas** para facilitar a construção.
5. **Teste e Modificação:** como o RAD enfatiza o reuso, muitos componentes **já estão testados** → o tempo total de teste diminui. Mas os **componentes novos** precisam ser testados e **todas as interfaces** devem ser exaustivamente exercitadas.

**Negócio → Dados → Processo → Geração da aplicação → Teste e modificação**

Cada grande função do sistema pode ficar com uma **equipe RAD separada**, e cada equipe passa por essas 5 fases em paralelo dentro da janela de 60 a 90 dias. No fim, as partes são integradas para formar o todo.

![[Pasted image 20261024213412.png|550]]

**Obs:** a Modelagem de Negócio olha para o **fluxo de informação** (quem gera, para onde vai, quem processa); a Modelagem dos Dados olha para os **objetos de dados** (composição e relações); a Modelagem do Processo olha para as **operações sobre esses objetos** (adicionar, modificar, descartar, recuperar).

**Negócio = fluxo de informação**  
**Dados = objetos de dados**  
**Processo = operações sobre os objetos**

---

## RAD segundo Stephen E. Cross (SEI)

Segundo **Stephen E. Cross**, diretor do **SEI — Software Engineering Institute da Carnegie Mellon**, uma forma mais eficiente de abordar o RAD é dividi-lo em **6 passos**:

1. Projeto e análise baseado no **cenário**;
2. Projeto e análise de **arquitetura**;
3. Especificação de componentes com o **máximo de reuso**;
4. **Desenvolvimento rápido** dos módulos remanescentes;
5. **Testes frequentes com o usuário final**;
6. Campo com **ferramentas de suporte** para permitir a evolução.

A proposta de Stephen é **disciplinar o RAD**, que muitas vezes é criticado pela sua suposta **informalidade**, a ponto de conseguir atingir níveis de **CMMI — Capability Maturity Model Integration**.

**Obs:** no slide está escrito "Carneggie Mellow"; o nome correto da universidade é **Carnegie Mellon**.

| Visão | Quantidade | Lembrete rápido |
|---|---|---|
| **Alguns autores** | **5 fases** | **Negócio → Dados → Processo → Geração → Teste** |
| **Stephen E. Cross (SEI)** | **6 passos** | **Disciplinar o RAD → chegar ao CMMI** |

---

## Vantagens do RAD

- Permite o **desenvolvimento rápido** e/ou a **prototipagem** de aplicações.
- Ciclo de desenvolvimento **extremamente curto** (entre 60 e 90 dias).
- Cada função principal pode ir para uma **equipe RAD separada** e depois ser integrada ao todo.
- **Criação e reutilização de componentes**.
- Usado principalmente para **aplicações de sistemas de informação**.
- **Comprar pode economizar recursos** se comparado a desenvolver.
- Desenvolvimento conduzido em um **nível mais alto de abstração**.
- **Visibilidade mais cedo** → por causa dos protótipos.
- **Maior flexibilidade** → os desenvolvedores podem reprojetar praticamente à vontade.
- **Grande redução de codificação manual** → uso de *wizards* e ferramentas.
- **Envolvimento maior do usuário**.
- **Provável custo reduzido** → tempo é dinheiro, e ainda tem o reuso.
- **Aparência padronizada** → APIs e componentes reutilizáveis deixam a aparência consistente.

---

## Desvantagens do RAD

- Se a aplicação **não puder ser modularizada** de modo que cada função principal fique pronta em **menos de 3 meses**, o RAD não é aconselhável.
- Em projetos **grandes (mas escaláveis)**, exige gente suficiente para montar o número certo de equipes → **alto custo com a equipe**.
- O **envolvimento do usuário tem que ser ativo**.
- Exige **comprometimento da equipe** do projeto.
- Não é aconselhável quando os **riscos técnicos são altos**, quando se está **testando novas tecnologias** ou quando o software exige **alto grau de interoperabilidade** com programas já existentes.
- **Falta de prazo** pode reduzir a qualidade → exige desenvolvedores mais habilidosos e mais suporte da gerência e dos clientes.
- **Desenvolver pode economizar recursos** se comparado a comprar.
- **Custo do conjunto de ferramentas** e do hardware para rodar a aplicação.
- **Mais difícil de acompanhar o projeto** → não existem os **marcos clássicos** (como as fases bem separadas do Cascata).
- **Menos eficientes**.
- **Perda de precisão científica** → falta de métodos formais.
- Pode acidentalmente levar ao **retorno das práticas caóticas** no desenvolvimento.
- **Funções reduzidas** → por causa do reuso e do ***timeboxing*** (ciclos de desenvolvimento muito curtos).
- **Funções desnecessárias** → o componente reutilizado pode trazer coisas que o sistema não precisa.
- **Problemas legais**.
- **Requisitos podem não se encaixar** → conflitos entre desenvolvedores e clientes.
- **Padronização** → aparência diferente entre módulos e componentes.
- **Sucessos anteriores são difíceis de reproduzir**.

**Obs:** no slide, o balão de "timeboxing" cobre parte do item "Requisitos podem não se ... desenvolvedores e clientes". O "encaixar" e o "conflitos entre" foram deduzidos pelo contexto; vale confirmar com a professora se esse item cair.

**Obs:** "comprar economiza" aparece nas vantagens e "desenvolver economiza" aparece nas desvantagens. Não é erro de digitação: são os dois lados da mesma escolha. Comprar componentes prontos pode sair mais barato, mas em alguns casos desenvolver sairia mais barato do que comprar.

**Obs:** "aparência padronizada" também aparece dos dois lados: componentes reutilizáveis deixam a aparência consistente (vantagem), mas misturar componentes de origens diferentes pode deixar módulos com aparência diferente (desvantagem).

**Timeboxing = ciclos de desenvolvimento muito curtos**

---

## Quando usar o RAD:

### O RAD é apropriado quando

- A aplicação é do tipo **"standalone"** → **Exemplo:** programas para capturar telas de câmeras de segurança.
- Pode-se usar **classes pré-existentes (APIs)**.
- A **performance não é o mais importante**.
- A **distribuição do produto é pequena**.
- O **escopo do projeto é restrito**.
- O sistema pode ser **dividido em vários módulos independentes**, ou seja, as restrições de tempo do projeto demandam um escopo de escala.
- A aplicação pode ser **modularizada** de forma que cada grande função fique pronta em **menos de 3 meses**.
- A **tecnologia necessária tem mais de um ano** de existência.
- Cada grande função pode ser **alocada para uma equipe distinta** e depois integrada ao todo.

### O RAD deve ser evitado quando

- A aplicação precisa **interagir com outros programas**.
- Existem **poucos plug-ins e componentes** disponíveis.
- **Performance é essencial**.
- O desenvolvimento **não pode tirar vantagem de ferramentas de alto nível**.
- A distribuição do produto será em **grande escala**.
- Para construir **sistemas operacionais** → confiabilidade exigida alta demais.
- **Jogos de computador** → performance exigida muito alta.
- **Riscos tecnológicos muito altos** porque a tecnologia foi recém-lançada.
- O sistema **não pode ser modularizado**.

As duas listas são praticamente espelhos uma da outra:

| Critério | Usar RAD | Evitar RAD |
|---|---|---|
| **Integração** | Aplicação *standalone* | Precisa interagir com outros programas |
| **Componentes** | Dá para usar APIs/classes prontas | Poucos plug-ins e componentes |
| **Performance** | Não é o mais importante | É essencial (ex.: jogos) |
| **Distribuição** | Pequena | Grande escala |
| **Modularização** | Módulos independentes, cada função em < 3 meses | Não pode ser modularizado |
| **Tecnologia** | Tem mais de 1 ano | Recém-lançada, risco alto |
| **Ferramentas** | — | Não dá para usar ferramentas de alto nível |
| **Confiabilidade** | — | Exigida alta demais (ex.: sistema operacional) |

**RAD bom = pequeno + isolado + modular + tecnologia madura**  
**RAD ruim = performance crítica + integração + tecnologia nova**

---

## Modelos Ágeis

Segundo **Wazlawick (2013)**, os princípios dos **Modelos Ágeis** foram colocados no **Manifesto Ágil**, assinado por **17 pesquisadores** da área, entre eles **Martin Fowler**, **Alistair Cockburn** e **Robert Martin**.

### Valores do Manifesto Ágil

O Manifesto começa assim: "Nós estamos descobrindo formas melhores de desenvolver software fazendo e ajudando outros a fazer". A partir disso, chegaram a **4 valores**:

| Valoriza mais | Do que | Lembrete rápido |
|---|---|---|
| **Indivíduos e interações** | Processos e ferramentas | **PESSOAS** |
| **Software funcionando** | Documentação compreensível | **FUNCIONAR** |
| **Colaboração do cliente** | Negociação de contrato | **CLIENTE JUNTO** |
| **Responder às mudanças** | Seguir um plano | **MUDANÇA** |

**Obs:** o slide traz "documentação **compreensível**". A tradução mais comum do Manifesto é "documentação **abrangente**" (muita documentação, não documentação fácil de entender). Na prova pode aparecer qualquer uma das duas.

Isso **não significa** que os Modelos Ágeis desprezam processos, ferramentas, documentação, contratos e planos. Segundo **Wazlawick (2013)**, esses elementos passam a ter **mais sentido e mais valor** quando indivíduos, interações, software funcionando, colaboração do cliente e resposta às mudanças também são considerados importantes.

→ Processo bem estruturado não adianta se as pessoas não o seguem; software bem documentado não adianta se não satisfaz os requisitos ou não funciona.

> **Resumo:** os itens da esquerda têm prioridade, mas os da direita continuam tendo valor, e valem mais quando os da esquerda são respeitados.

**Ágil ≠ sem documentação/plano**  
**Ágil = pessoas + software funcionando + cliente + mudança**

### Os 12 princípios do Manifesto Ágil

O Manifesto é complementado por **12 princípios**:

1. A maior prioridade é **satisfazer o cliente** com entrega contínua e adiantada de software com valor agregado.
2. **Aceitar mudanças de requisitos**, mesmo no fim do desenvolvimento → o cliente pode tirar vantagens competitivas.
3. Entregar frequentemente **software funcionando**, de poucas semanas a poucos meses, preferindo a menor escala de tempo.
4. Pessoas de negócio e desenvolvedores trabalham **diariamente em conjunto** por todo o projeto.
5. Construir projetos em torno de **indivíduos motivados**, dando ambiente e suporte e **confiando neles para fazer o trabalho**.
6. O método mais eficiente e eficaz de transmitir informação para e dentro da equipe é a **conversa face a face**.
7. **Software funcionando é a medida primária de progresso.**
8. Desenvolvimento **sustentável**: patrocinadores, desenvolvedores e usuários conseguem manter um **ritmo constante indefinidamente**.
9. Atenção contínua à **excelência técnica** e ao bom *design* aumenta a agilidade.
10. **Simplicidade:** a arte de maximizar a quantidade de **trabalho não realizado** é essencial.
11. As melhores arquiteturas, requisitos e *designs* surgem de **times auto-organizáveis**.
12. Em intervalos regulares, a equipe **reflete** sobre como ficar mais **eficaz** e **ajusta** seu comportamento.

**Obs:** o princípio 10 confunde: "maximizar o trabalho não realizado" quer dizer **não fazer o que não precisa ser feito**, e não trabalhar menos.

**Obs:** o valor "software funcionando" e o princípio 7 andam juntos: no ágil, progresso se mede por software rodando, não por documento entregue.

---

## Principais Modelos Ágeis

### Scrum

O **Scrum** é uma estrutura baseada em **sprints** (ciclos curtos de trabalho), com **papéis definidos**: **Product Owner**, **Scrum Master** e **Time de Desenvolvimento**.

![[Pasted image 20261024214950.png|500]]

O fluxo é: os itens do **Product Backlog** são selecionados para o **Sprint Backlog**, que é desenvolvido durante a **Sprint** (no diagrama, de **30 dias**, com um ciclo menor de **24h** dentro dela) e gera uma **entrega incrementada ao software**.

**Product Backlog → Sprint Backlog → Sprint → Entrega incrementada**

**Scrum = sprints + papéis**

### Kanban

O **Kanban** foca na **visualização do fluxo de trabalho** e na **limitação de tarefas em andamento**.

A visualização é feita num quadro com colunas, em que as tarefas vão passando de uma para a outra:

**To Do → Doing → Done**

**Kanban = quadro + fluxo + limitar o que está em andamento**

### Extreme Programming (XP)

O **XP** enfatiza **boas práticas de engenharia**, como **testes automatizados**, **integração contínua** e **programação em pares**.

![[Pasted image 20261024215238.png|500]]

No ciclo do XP, os **requisitos** viram **stories (histórias)** que alimentam o **Release Planning** (planejamento de entrega). Os **Spikes** ajudam a gerar as **estimativas**. Depois vêm as **iterações**, que terminam no **Acceptance Test** (teste de aceitação, montado a partir dos cenários de teste). Com a **aprovação do cliente**, o software vira uma **release**, sempre em **entregas pequenas** (*small releases*).

**Stories → Release Planning → Iteration → Acceptance Test → Small releases**

**XP = qualidade de código + práticas de engenharia**

**Obs:** o título do slide está "Expreme Programming"; o correto é **Extreme Programming**.

### Lean

O **Lean** é inspirado na **manufatura enxuta** e busca **eliminar desperdícios** e **maximizar valor**.

![[Pasted image 20261024215611.png|400]]

Funciona num ciclo: a **ideia** é usada para **construir** um **MVP** (produto mínimo viável), o MVP é **medido** gerando **dados**, e com os dados a equipe **aprende** e volta para uma nova ideia.

**Ideia → Construir → MVP → Medir → Dados → Aprender → Ideia**

**Lean = eliminar desperdício + maximizar valor**

---

## Scrum × Kanban × XP

| Característica | Scrum | Kanban | XP (Extreme Programming) |
|---|---|---|---|
| **Principal foco** | Gestão de projeto e entregas em ciclos | Fluxo contínuo e eficiência de processos | Práticas de engenharia e qualidade de código |
| **Métrica de ritmo** | Sprints fixas (*time-boxed*) | Fluxo contínuo (*Pull system*) | Iterações curtas (geralmente 1-2 semanas) |
| **Mudanças de escopo** | **Não permitidas** durante a Sprint atual | **Permitidas a qualquer momento** no Backlog | **Bem-vindas** em cada iteração |
| **Métricas chave** | Velocity (pontos por sprint) | Lead Time e Cycle Time | Cobertura de testes e taxa de defeitos |

O que mais confunde é a mudança de escopo: no Scrum a sprint em andamento fica **travada**; no Kanban não existe sprint, então dá para mudar o backlog **a qualquer hora**; no XP a mudança entra **a cada nova iteração**.

**Scrum = gerencia em sprints**  
**Kanban = controla o fluxo**  
**XP = cuida do código**  
**Lean = corta desperdício**

---

## Revisão rápida:

| Conceito | Ideia principal | Lembrete rápido |
|---|---|---|
| **RAD** | Rapid Application Development / Desenvolvimento Rápido de Aplicação; iterativo e incremental | **rápido + reuso + protótipo** |
| **Prazo do RAD** | Ciclo extremamente curto | **60 a 90 dias** |
| **Características do RAD** | Entrega rápida por reuso, prototipagem rápida, iterações curtas, equipe multidisciplinar com cliente | **reuso + protótipo + feedback** |
| **5 fases do RAD** | Modelagem de negócio, dos dados, do processo, geração da aplicação, teste e modificação | **Negócio → Dados → Processo → Geração → Teste** |
| **Geração da aplicação** | Técnicas de 4ª geração, reuso de componentes, ferramentas automatizadas | **gera com ferramenta** |
| **Teste no RAD** | Componentes reutilizados já testados → menos tempo; novos componentes e interfaces testados exaustivamente | **reuso encurta o teste** |
| **Stephen E. Cross (SEI)** | RAD em 6 passos para disciplinar o modelo e chegar ao CMMI | **6 passos → CMMI** |
| **Equipes RAD** | Cada função principal vai para uma equipe e depois tudo é integrado | **dividir para correr** |
| **Limite de modularização** | Cada função principal precisa ficar pronta em < 3 meses | **< 3 meses** |
| **Vantagens-chave do RAD** | Rapidez, reuso, protótipos cedo, flexibilidade, menos codificação manual, mais envolvimento do usuário | **rápido e visível** |
| **Desvantagens-chave do RAD** | Custo de equipe, usuário precisa ser ativo, sem marcos clássicos, falta de métodos formais, risco de caos | **rápido mas bagunçável** |
| **Timeboxing** | Ciclos de desenvolvimento muito curtos | **prazo fechado** |
| **Comprar × desenvolver** | Comprar pode economizar (vantagem); desenvolver pode economizar (desvantagem) | **depende do caso** |
| **Manifesto Ágil** | Wazlawick (2013): 17 pesquisadores (Fowler, Cockburn, Robert Martin) | **17 assinaturas** |
| **4 valores** | Indivíduos, software funcionando, colaboração do cliente, responder às mudanças | **pessoas + funcionar + cliente + mudança** |
| **Leitura dos valores** | Itens da direita continuam valendo; ganham valor quando os da esquerda são respeitados | **Ágil ≠ sem documentação** |
| **12 princípios** | Complementam o Manifesto | **12** |
| **Princípio 7** | Software funcionando é a medida primária de progresso | **progresso = software rodando** |
| **Princípio 10** | Simplicidade: maximizar o trabalho não realizado | **não fazer o desnecessário** |
| **Scrum** | Sprints + Product Owner, Scrum Master e Time de Desenvolvimento | **sprint travada** |
| **Kanban** | Visualização do fluxo e limite de tarefas em andamento | **To Do → Doing → Done** |
| **XP** | Testes automatizados, integração contínua, programação em pares | **qualidade de código** |
| **Lean** | Manufatura enxuta: eliminar desperdícios, maximizar valor | **Ideia → MVP → Dados → Aprender** |
| **Ritmo: Scrum / Kanban / XP** | Sprints fixas (*time-boxed*) / fluxo contínuo (*Pull system*) / iterações curtas (1-2 semanas) | **sprint × fluxo × iteração** |
| **Mudança de escopo** | Scrum: não durante a sprint / Kanban: a qualquer momento no backlog / XP: bem-vinda a cada iteração | **trava × livre × por iteração** |
| **Métricas-chave** | Scrum: Velocity (pontos por sprint) / Kanban: Lead Time e Cycle Time / XP: cobertura de testes e taxa de defeitos | **pontos × tempo × testes** |

| Situação | Palavra-chave | Pergunta mental |
|---|---|---|
| **Usar RAD** | **PEQUENO E MODULAR** | Dá para dividir em funções de < 3 meses, sem performance crítica e com tecnologia madura? |
| **Evitar RAD** | **CRÍTICO OU INTEGRADO** | É SO, jogo, tecnologia nova, distribuição grande ou precisa conversar com outros programas? |
| **Scrum** | **SPRINT** | Trabalha em ciclos fixos com papéis definidos e escopo travado na sprint? |
| **Kanban** | **FLUXO** | Foca em visualizar o quadro e limitar o que está em andamento, sem ciclo fixo? |
| **XP** | **PRÁTICAS DE ENGENHARIA** | Fala de testes automatizados, integração contínua ou programação em pares? |
| **Lean** | **DESPERDÍCIO** | Fala em eliminar desperdício, manufatura enxuta ou ciclo construir-medir-aprender? |
