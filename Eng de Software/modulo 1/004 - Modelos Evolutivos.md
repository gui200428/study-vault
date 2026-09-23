# Modelos Evolutivos, Incremental, Espiral e Prototipação — Aula 03

## Modelos Evolutivos

Os **Modelos Evolutivos** desenvolvem o software de forma gradual, partindo de uma versão inicial e evoluindo conforme novas informações e requisitos são descobertos.

As ideias e necessidades do sistema vão sendo materializadas à medida que o produto evolui, permitindo que o cliente participe do desenvolvimento e avalie versões anteriores ao produto final.

Entre suas principais vantagens estão:

- antecipar parte do produto para avaliação do cliente;
- manter comunicação entre desenvolvedores e usuários;
- identificar e solucionar problemas durante a evolução do sistema;
- antecipar o treinamento dos usuários.

> **Resumo:** Modelos Evolutivos constroem o software gradualmente, utilizando versões anteriores para orientar sua evolução.

**Evolutivo = desenvolver + avaliar + evoluir**

---

## Funcionamento dos Modelos Evolutivos

O desenvolvimento ocorre em **ciclos**, que possuem etapas de avaliação e planejamento.

Ao final de cada ciclo, os resultados obtidos ajudam a determinar como a próxima etapa será conduzida.

Diferentemente de um modelo puramente linear, existe maior possibilidade de **iteração**, permitindo revisar e aperfeiçoar o sistema durante seu desenvolvimento.

Os modelos evolutivos podem combinar características do **Modelo Cascata** e da **Prototipagem**, além de considerar elementos como a **Análise de Riscos**.

Um ciclo pode envolver:

**Planejamento → Análise → Projeto → Prototipação → Avaliação**

Entre os modelos evolutivos apresentados estão:

- **Modelo Espiral**;
- **Prototipação**.

---

# Modelo Iterativo e Incremental

O **Modelo Incremental** constrói e entrega o software em **partes**, chamadas de **incrementos** ou módulos.

Já a característica **iterativa** representa a repetição de ciclos de desenvolvimento, permitindo aproveitar o conhecimento obtido nas versões anteriores.

Assim, o Modelo Iterativo e Incremental desenvolve o sistema através de **ciclos repetidos** e adiciona novas partes ao software progressivamente.

**Iterativo = repetir e melhorar**  
**Incremental = adicionar partes**

> **Versão curta:** O sistema é desenvolvido aos poucos, em vários ciclos, e cada incremento adiciona novas funcionalidades até chegar à versão final.

---

## Funcionamento do Desenvolvimento Incremental

No desenvolvimento incremental, o sistema é dividido em partes que podem ser implementadas e entregues separadamente.

Por exemplo, um sistema dividido em quatro módulos poderia entregar:

- módulo de cadastro;
- módulo de vendas;
- outros módulos em entregas posteriores.

Em cada nova versão, podem ser realizadas **alterações de design** e adicionadas novas funcionalidades.

A ideia principal é que cada incremento entregue uma parte **funcional do sistema final**, e não apenas uma demonstração.

**Incremento = parte funcional do produto final**

---

## Ciclo de Cada Incremento

Cada incremento passa pelo ciclo de desenvolvimento necessário para produzir uma versão funcional.

Processo envolvendo atividades:

**Requisitos → Análise → Projeto → Implementação → Testes → Implantação**

Depois, um novo ciclo começa para produzir o próximo incremento.

Cada etapa gera um sistema funcional, mesmo que ele ainda não possua todos os requisitos previstos para a versão final.

Isso permite desenvolver primeiro um subconjunto dos requisitos e ampliar o sistema progressivamente.

---

## Especificação, Desenvolvimento e Validação

No Modelo Incremental, as atividades de **especificação**, **desenvolvimento** e **validação** podem ocorrer de maneira intercalada.

Uma implementação inicial é apresentada aos usuários, recebe comentários e continua evoluindo através de novas versões.

Existe, portanto, um **feedback rápido** entre as atividades.

O desenvolvimento incremental é uma parte importante das **abordagens ágeis**, principalmente em sistemas de negócios, e-commerce e sistemas pessoais.

---

# Vantagens do Modelo Incremental

Uma das principais vantagens é que o cliente **não precisa esperar o sistema inteiro ficar pronto** para começar a utilizá-lo.

O primeiro incremento deve priorizar os requisitos mais importantes, permitindo que uma parte útil do sistema seja entregue rapidamente.

Além disso:

- os primeiros incrementos podem ajudar o cliente a descobrir novos requisitos;
- a experiência de uso pode orientar os próximos incrementos;
- existe menor risco de fracasso completo do sistema;
- erros podem ficar limitados a uma parte menor do projeto.

**Incremental = entrega funcional mais cedo**

---

# Desvantagens do Modelo Incremental

O modelo depende da possibilidade de **dividir o sistema em partes**, o que nem sempre é possível.

Também podem surgir dificuldades na integração entre os incrementos desenvolvidos.

Outro problema é o crescimento do escopo. Como o cliente acompanha as entregas e utiliza versões intermediárias, pode solicitar novas funcionalidades que não estavam previstas inicialmente.

Isso pode aumentar o custo do produto final e dificultar negociações relacionadas ao projeto.

O modelo é especialmente aplicável quando os requisitos podem ser **particionados** em partes relativamente independentes.

**Requisitos particionáveis = bom cenário para Incremental**

---

# Tipos de Incrementos

Tipos de incrementos:

| Tipo        | Característica                                                           |
| ----------- | ------------------------------------------------------------------------ |
| Evolutivo   | A versão anterior é aproveitada e aperfeiçoada                           |
| Descartável | O produto daquela etapa é descartado e outro é criado                    |
| Operacional | Protótipos esclarecem requisitos enquanto o produto final é desenvolvido |

### Evolutivos

Os resultados produzidos em uma etapa são **aproveitados na etapa seguinte**.

O produto vai sendo continuamente aperfeiçoado.

### Descartáveis

O que foi produzido é utilizado para aprendizado ou avaliação e depois é **descartado**.

Uma nova versão pode então ser construída a partir do conhecimento obtido.

### Operacional

Os requisitos são esclarecidos utilizando protótipos enquanto o produto final é desenvolvido paralelamente.

---

# Exemplos do Modelo Incremental

Um exemplo apresentado é o desenvolvimento de um **processador de texto**.

As funcionalidades poderiam ser entregues da seguinte maneira:

| Release | Funcionalidades                            |
| ------- | ------------------------------------------ |
| 1º      | Arquivos, edição e produção de documentos  |
| 2º      | Recursos mais sofisticados de edição       |
| 3º      | Verificação sintática e gramatical         |
| 4º      | Recursos avançados de disposição de página |

Cada release amplia as capacidades existentes até formar o produto completo.

Outro exemplo são sistemas **ERP**, nos quais diferentes módulos podem ser desenvolvidos separadamente:

- financeiro;
- recursos humanos;
- estoque;
- vendas.

A empresa pode começar a utilizar os primeiros módulos antes que o sistema esteja totalmente concluído.

Aplicações Web e Mobile também podem começar com recursos básicos, como **cadastro, login, feed ou carrinho**, recebendo posteriormente incrementos como pagamentos, notificações e chat.

---

# Modelo Espiral de Boehm

O **Modelo Espiral** foi proposto por **Boehm em 1988**.

É um modelo de processo de software **orientado a riscos**, no qual o desenvolvimento é representado através de uma espiral.

Cada **volta da espiral representa uma fase do processo de software**.

Ao contrário de modelos com uma sequência fixa de fases, os ciclos da espiral são definidos de acordo com as necessidades do projeto.

Por exemplo:

- uma volta pode avaliar a **viabilidade**;
- outra pode trabalhar os **requisitos**;
- outra pode tratar do **projeto do sistema**.

> **Resumo:** O Modelo Espiral desenvolve o sistema em ciclos, utilizando a análise de riscos para decidir como o projeto deve continuar.

**Espiral = ciclos + riscos**

---

# Riscos no Modelo Espiral

A principal característica que diferencia o Espiral dos outros modelos apresentados é o reconhecimento **explícito dos riscos**.

As mudanças são tratadas como possíveis consequências dos riscos existentes no projeto, e atividades de **Gerenciamento de Riscos** são realizadas continuamente para reduzi-los.

Cada alternativa de desenvolvimento é avaliada considerando os objetivos do projeto e seus possíveis riscos.

Esses riscos podem ser estudados utilizando:

- análise mais detalhada;
- prototipação;
- simulação;
- coleta de informações.

O objetivo de cada ciclo é **minimizar ou eliminar riscos antes de continuar**.

---

# Etapas do Modelo Espiral

Cada volta da espiral é dividida em quatro setores principais.

## Definição de Objetivos

São identificados:

- objetivos da fase;
- restrições do produto e do processo;
- riscos;
- alternativas possíveis;
- estratégias para lidar com esses riscos.

É definido **o que aquela volta da espiral pretende alcançar**.

---

## Avaliação e Redução de Riscos

Os riscos identificados são avaliados e são realizadas atividades para reduzi-los.

Por exemplo, caso exista o risco de os requisitos estarem incorretos ou incompletos, pode ser desenvolvido um **protótipo** para compreender melhor o sistema.

---

## Desenvolvimento e Validação

Depois da análise dos riscos, é escolhido um modelo de desenvolvimento adequado à situação.

O próprio Modelo Espiral pode utilizar outros modelos dentro de seus ciclos.

Exemplo: possibilidade de utilizar o **Modelo Cascata** quando determinado risco estiver relacionado à integração de subsistemas.

---

## Planejamento

O projeto é revisado e é tomada a decisão sobre a continuidade para uma nova volta da espiral.

Caso o projeto continue, são elaborados os planos da próxima etapa.

**Objetivos → Riscos → Desenvolvimento → Planejamento → novo ciclo**

---

# Atividades do Modelo Espiral

O material também organiza o desenvolvimento em algumas atividades gerais.

### Comunicação com o Cliente

Estabelece a comunicação necessária entre desenvolvedores e cliente.

### Planejamento

Define recursos, tempo e outras informações do projeto.

### Engenharia

Produz representações e soluções para a aplicação.

### Construção e Release

Envolve:

- construção;
- testes;
- instalação;
- documentação;
- treinamento;
- suporte ao usuário.

### Avaliação do Cliente

O cliente avalia o que foi produzido e fornece **feedback**, que será utilizado nos próximos ciclos.

---

# Vantagens do Modelo Espiral

## Gerenciamento de Riscos

É especialmente adequado para projetos que possuem muitos riscos ou incertezas.

A análise de riscos acontece durante todo o desenvolvimento.

## Projetos Grandes e Complexos

O material recomenda o modelo principalmente para **projetos grandes e complexos**.

## Flexibilidade dos Requisitos

Mudanças nos requisitos podem ser incorporadas durante os ciclos.

## Participação do Cliente

O cliente consegue acompanhar versões e representações do sistema antes da conclusão completa do projeto.

**Espiral = alto controle de riscos + maior flexibilidade**

---

# Desvantagens do Modelo Espiral

O Modelo Espiral possui algumas limitações importantes.

### Complexidade

É mais complexo do que outros modelos de desenvolvimento.

### Custo

Sua aplicação pode ter um custo elevado, tornando-o pouco adequado para **projetos pequenos**.

### Dependência da Análise de Riscos

O sucesso do modelo depende fortemente de uma boa identificação e análise dos riscos.

Isso exige profissionais com conhecimento e experiência nessa atividade.

### Dificuldade de Estimar o Tempo

Como o número de ciclos pode não ser conhecido no início do projeto, é mais difícil prever precisamente quanto tempo o desenvolvimento levará.

---

# Exemplos de Uso do Modelo Espiral

O modelo é apresentado principalmente em sistemas **grandes, complexos ou de alto risco**.

| Tipo de sistema | Motivo |
| --- | --- |
| Sistemas hospitalares | Validação, testes e conformidade |
| Sistemas governamentais | Muitos stakeholders e requisitos variáveis |
| Sistemas aeroespaciais e de defesa | Segurança e confiabilidade críticas |

### Sistemas Hospitalares e de Saúde

Podem envolver:

- prontuários eletrônicos;
- apoio à decisão clínica;
- integração com equipamentos médicos.

Esses sistemas exigem validação rigorosa, testes contínuos e conformidade com normas e legislações.

### Sistemas Governamentais

Sistemas tributários, plataformas de serviços públicos e controle de fronteiras podem possuir muitos stakeholders e requisitos que mudam ao longo do tempo.

### Sistemas Aeroespaciais e de Defesa

Exigem fatores como:

- alta confiabilidade;
- segurança crítica;
- integração com hardware complexo.

O Modelo Espiral permite analisar riscos técnicos e operacionais antes de avançar para os próximos ciclos.

---

# Prototipação

A **Prototipação** consiste na criação de uma representação do software que será desenvolvido.

O protótipo permite compreender melhor o sistema antes que o produto final seja completamente construído.

Uma de suas principais funções é auxiliar na **identificação e validação dos requisitos**.

> **Resumo:** Prototipação cria uma versão preliminar do sistema para compreender e validar melhor os requisitos.

**Protótipo = experimentar antes de construir o produto final**

---

# Quando Utilizar Prototipação

A prototipação é especialmente útil quando o cliente sabe os **objetivos gerais** do sistema, mas ainda não consegue definir claramente todos os detalhes relacionados a:

- entradas;
- processamento;
- saídas;
- interface;
- funcionamento.

O protótipo funciona como um mecanismo para ajudar cliente e desenvolvedor a descobrir esses requisitos.

É importante que ambos entendam desde o início **qual é a finalidade do protótipo**.

---

# Processo de Prototipação

O processo apresentado no material pode ser representado como:

**Coleta e refinamento de requisitos → Projeto rápido → Construção do protótipo → Avaliação pelo cliente → Refinamento do protótipo**

Esse ciclo pode se repetir até que os requisitos estejam suficientemente compreendidos.

Depois disso, o desenvolvimento segue para a **engenharia do produto final**.

**Construir → avaliar → refinar**

---

# Vantagens da Prototipação

Uma das principais vantagens é que os requisitos **não precisam estar completamente definidos no início**.

Eles podem ser descobertos ou modificados durante o desenvolvimento.

A prototipação também:

- facilita a compreensão do sistema pelo usuário;
- aumenta o envolvimento do usuário;
- permite validar funcionalidades e interfaces;
- possibilita testar rapidamente aspectos do ambiente de desenvolvimento;
- ajuda a avaliar desempenho e interação com banco de dados.

Ela permite que ideias abstratas sejam transformadas em algo que o usuário consegue **visualizar e experimentar**.

---

# Desvantagens da Prototipação

Um dos riscos é começar a construir o protótipo cedo demais, sem analisar suficientemente o problema e a situação existente.

Também pode ocorrer o desenvolvimento de funcionalidades inadequadas ou desnecessárias durante sucessivas alterações do protótipo.

Outro problema é a expectativa criada no usuário.

Como o cliente consegue visualizar uma versão funcionando, ele pode acreditar que:

- praticamente qualquer mudança pode ser implementada facilmente;
- o produto final já está quase pronto;
- não deveria existir grande demora depois da demonstração.

Na prática, o protótipo pode ainda estar muito distante de uma aplicação completa e pronta para produção.

**Protótipo funcional ≠ produto final pronto**

---

# Formas de Prototipação

O material apresenta três formas gerais:

### Protótipo Descartável

É utilizado principalmente para representar a interação entre usuário e sistema.

Pode ser criado em papel ou em ferramentas simples e depois ser descartado.

### Protótipo com Algumas Funções

Implementa somente algumas funcionalidades que o sistema deverá possuir.

Serve para validar partes específicas antes do desenvolvimento completo.

### Prototipação Evolucionária

O protótipo apresenta superficialmente as funcionalidades desejadas e passa por **refinamentos sucessivos**.

Nesse caso, ele evolui gradualmente à medida que o sistema é desenvolvido.

---

# Níveis de Fidelidade dos Protótipos

Os protótipos também podem ser classificados pelo quanto se parecem com o sistema final.

| Fidelidade | Característica principal |
| --- | --- |
| Baixa | Representação simples e rápida |
| Média | Interface mais próxima do produto final |
| Alta | Interface e interação muito próximas do sistema real |

---

## Protótipos de Baixa Fidelidade

Também conhecidos como **wireframes**, são representações simples do sistema.

Podem ser feitos com papel e lápis ou utilizando ferramentas digitais.

Seu objetivo é representar rapidamente:

- organização da interface;
- características básicas;
- fluxo de utilização;
- ideias iniciais.

São baratos, rápidos de produzir e úteis principalmente para discutir os requisitos da interface com os usuários.

**Baixa fidelidade = estrutura e ideia**

Exemplos de ferramentas citadas no material incluem **Pencil, Balsamiq, OmniGraffle, InVision Freehand e Figma**.

---

## Protótipos de Média Fidelidade

Também chamados de **mockups**, são visualmente mais próximos do sistema final.

Normalmente são produzidos com ferramentas computacionais e podem simular a interação da interface.

Não precisam utilizar as mesmas tecnologias que serão usadas no produto definitivo.

Permitem apresentar de maneira mais clara:

- telas;
- elementos visuais;
- organização da interface;
- algumas interações.

**Média fidelidade = aparência + alguma interação**

O material cita ferramentas como **FlutterFlow, Sketch e Axure RP**.

---

## Protótipos de Alta Fidelidade

Os protótipos de **Alta Fidelidade** possuem interface e comportamento muito próximos do sistema final.

Podem utilizar as mesmas tecnologias de software e hardware previstas para o produto.

Algumas partes reais do sistema já podem estar implementadas, oferecendo alto nível de **interatividade e realismo**.

Por serem mais completos:

- exigem maior conhecimento técnico;
- possuem custo maior;
- demandam mais tempo de desenvolvimento.

**Alta fidelidade = próximo do produto real**

O material cita ferramentas como **Figma, Adobe XD, InVision, Bootstrap Studio e Pingendo**.

---

# Comparação dos Níveis de Fidelidade

| Característica | Baixa | Média | Alta |
| --- | --- | --- | --- |
| Semelhança com sistema final | Baixa | Média | Alta |
| Interação | Pouca ou nenhuma | Simulada | Próxima da real |
| Custo | Baixo | Intermediário | Alto |
| Velocidade de criação | Alta | Média | Menor |
| Uso principal | Explorar ideias | Validar interface | Simular produto real |

**Wireframe = estrutura**  
**Mockup = aparência**  
**Alta fidelidade = experiência próxima do real**

---

# Criação e Teste de um Protótipo

O material apresenta alguns passos que podem ser utilizados durante a criação e avaliação de um protótipo:

1. identificar os **stakeholders**;
2. escolher tarefas que o usuário realizará;
3. esboçar a interface;
4. representar elementos como menus, páginas, caixas de diálogo e mensagens;
5. realizar **testes de usabilidade**;
6. utilizar representantes dos stakeholders durante a avaliação.

O objetivo é verificar se a proposta realmente atende às necessidades dos usuários antes da implementação completa.

---

# Exemplos de Uso da Prototipação

A prototipação é bastante útil em aplicações nas quais a **experiência do usuário** possui grande importância.

### Aplicativos Mobile e Web

Pode ser utilizada em:

- redes sociais;
- aplicativos de delivery;
- plataformas de streaming.

Os protótipos ajudam a testar **fluxos de navegação, layout e funcionalidades** antes da implementação definitiva.

### Sistemas Educacionais

Pode ser utilizada antes do desenvolvimento completo para:

- testar a usabilidade com alunos e professores;
- validar a organização dos conteúdos;
- avaliar fóruns, quizzes e dashboards.

---

# Espiral × Prototipação Evolutiva × Desenvolvimento Ágil

Os três podem trabalhar com evolução e feedback, mas possuem **focos diferentes**.

| Modelo | Foco principal sobre riscos |
| --- | --- |
| Espiral | Analisa riscos formalmente em todos os ciclos |
| Prototipação Evolutiva | Reduz o risco de requisitos incorretos por meio da validação com o usuário |
| Desenvolvimento Ágil | Reduz riscos através de entregas curtas e feedback constante |

### Modelo Espiral

Possui abordagem **explicitamente orientada a riscos**, com uma etapa formal de análise de riscos em cada ciclo.

### Prototipação Evolutiva

Reduz principalmente o risco de desenvolver o sistema com **requisitos incorretos**, já que o usuário avalia continuamente os protótipos.

### Desenvolvimento Ágil

Utiliza ciclos curtos e feedback frequente para reduzir riscos relacionados ao desenvolvimento, ao mercado e às entregas.

**Espiral = analisar riscos**  
**Prototipação = validar requisitos**  
**Ágil = entregar e receber feedback rapidamente**




### Tabela resumo

|Situação / Conceito|Regra / Ideia principal|Lembrete rápido|
|---|---|---|
|**Modelos Evolutivos**|Software é construído gradualmente e evolui conforme surgem novas informações|**desenvolver + avaliar + evoluir**|
|**Participação do cliente**|Cliente consegue avaliar versões antes do produto final|**feedback durante o desenvolvimento**|
|**Funcionamento**|Desenvolvimento acontece em ciclos|**não é linear**|
|**Iteração**|Permite revisar e melhorar versões anteriores|**faz → avalia → melhora**|
|**Vantagens**|Antecipar produto, manter comunicação, identificar problemas cedo e antecipar treinamento|**feedback cedo**|
|**Ciclo típico**|Planejamento → Análise → Projeto → Prototipação → Avaliação|**ciclo de evolução**|
|**Modelos apresentados**|Espiral e Prototipação|**evolução em ciclos**|

### Iterativo × Incremental

|Situação / Conceito|Regra / Ideia principal|Lembrete rápido|
|---|---|---|
|**Modelos Evolutivos**|Software é construído gradualmente e evolui conforme surgem novas informações|**desenvolver + avaliar + evoluir**|
|**Participação do cliente**|Cliente consegue avaliar versões antes do produto final|**feedback durante o desenvolvimento**|
|**Funcionamento**|Desenvolvimento acontece em ciclos|**não é linear**|
|**Iteração**|Permite revisar e melhorar versões anteriores|**faz → avalia → melhora**|
|**Vantagens**|Antecipar produto, manter comunicação, identificar problemas cedo e antecipar treinamento|**feedback cedo**|
|**Ciclo típico**|Planejamento → Análise → Projeto → Prototipação → Avaliação|**ciclo de evolução**|
|**Modelos apresentados**|Espiral e Prototipação|**evolução em ciclos**|

### Modelo Incremental

|Situação / Conceito|Regra / Ideia principal|Lembrete rápido|
|---|---|---|
|**Modelo Incremental**|Sistema é dividido em partes entregues separadamente|**software aos poucos**|
|**Cada incremento**|Entrega uma parte funcional do sistema|**funciona de verdade**|
|**Nova versão**|Pode adicionar funções e modificar design|**vai aumentando**|
|**Ciclo de incremento**|Requisitos → Análise → Projeto → Implementação → Testes → Implantação|**mini ciclo completo**|
|**Resultado**|Cada ciclo produz uma versão funcional|**funciona mesmo incompleto**|
|**Feedback**|Especificação, desenvolvimento e validação podem se intercalar|**feedback rápido**|
|**Ágil**|Desenvolvimento incremental é importante em abordagens ágeis|**entregas pequenas e frequentes**|

### Vantagens do Incremental

| Vantagem                     | Ideia principal                                        | Lembrete rápido                      |
| ---------------------------- | ------------------------------------------------------ | ------------------------------------ |
| **Entrega antecipada**       | Cliente não precisa esperar o sistema inteiro          | **usa antes de terminar**            |
| **Prioridade**               | Primeiro incremento contém requisitos mais importantes | **mais importante primeiro**         |
| **Descoberta de requisitos** | Uso das versões ajuda a descobrir novas necessidades   | **cliente aprende usando**           |
| **Menor risco**              | Menor chance de fracasso completo                      | **erro fica mais localizado**        |
| **Feedback**                 | Experiência de uso orienta próximos incrementos        | **versão anterior ensina a próxima** |

### Desvantagens do Incremental

|Problema|Ideia principal|Lembrete rápido|
|---|---|---|
|**Divisão do sistema**|Nem todo sistema pode ser facilmente dividido|**precisa particionar**|
|**Integração**|Incrementos diferentes podem ser difíceis de integrar|**juntar pode dar ruim**|
|**Crescimento de escopo**|Cliente pode pedir funções novas a cada entrega|**escopo cresce**|
|**Custo**|Novas solicitações podem aumentar custo final|**mais pedidos = mais custo**|
|**Melhor cenário**|Requisitos relativamente independentes|**requisitos particionáveis**|

### Tipos de Incrementos

|Tipo|Característica|Lembrete rápido|
|---|---|---|
|**Evolutivo**|Versão anterior é aproveitada e melhorada|**aproveita**|
|**Descartável**|Versão é usada para aprender e depois descartada|**usa → aprende → joga fora**|
|**Operacional**|Protótipos ajudam a esclarecer requisitos enquanto produto final é desenvolvido|**protótipo + produto paralelo**|

### Exemplos do Incremental

| Exemplo                  | Como funciona                                                | Lembrete rápido                     |
| ------------------------ | ------------------------------------------------------------ | ----------------------------------- |
| **Processador de texto** | Funções são adicionadas release após release                 | **cada release aumenta capacidade** |
| **ERP**                  | Financeiro, RH, estoque e vendas podem ser módulos separados | **módulos independentes**           |
| **Web / Mobile**         | Cadastro/login primeiro; pagamento, chat etc. depois         | **MVP → novas funções**             |

## Modelo Espiral

|Situação / Conceito|Regra / Ideia principal|Lembrete rápido|
|---|---|---|
|**Modelo Espiral**|Criado por **Boehm em 1988**|**Boehm + 1988**|
|**Característica principal**|Modelo orientado a riscos|**RISCO é o centro**|
|**Funcionamento**|Desenvolvimento ocorre em voltas/ciclos|**cada volta = fase**|
|**Sequência**|Não possui uma sequência fixa de fases|**ciclo depende da necessidade**|
|**Objetivo**|Usar análise de riscos para decidir como continuar|**analisar antes de avançar**|

**Espiral = ciclos + riscos.**

### Riscos no Espiral

|Situação / Conceito|Regra / Ideia principal|Lembrete rápido|
|---|---|---|
|**Risco explícito**|Riscos são analisados formalmente em todos os ciclos|**risco sempre presente**|
|**Gerenciamento de riscos**|Acontece continuamente|**identificar → reduzir**|
|**Alternativas**|São avaliadas de acordo com objetivos e riscos|**comparar opções**|
|**Como estudar riscos**|Análise, protótipo, simulação e coleta de informações|**investigar o risco**|
|**Objetivo do ciclo**|Minimizar ou eliminar riscos antes de continuar|**reduzir risco → avançar**|

### 4 etapas do Modelo Espiral

|Etapa|Ideia principal|Lembrete rápido|
|---|---|---|
|**1. Definição de objetivos**|Define objetivos, restrições, riscos e alternativas|**o que queremos?**|
|**2. Avaliação e redução de riscos**|Analisa e tenta reduzir os riscos encontrados|**o que pode dar errado?**|
|**3. Desenvolvimento e validação**|Escolhe e aplica um modelo adequado|**construir/testar**|
|**4. Planejamento**|Decide se haverá novo ciclo e planeja a próxima volta|**próxima volta**|

**Objetivos → Riscos → Desenvolvimento → Planejamento → novo ciclo**


### Atividades do Espiral

|Atividade|Função|Lembrete rápido|
|---|---|---|
|**Comunicação com cliente**|Manter contato cliente ↔ desenvolvedor|**conversar**|
|**Planejamento**|Recursos, tempo e informações|**organizar**|
|**Engenharia**|Criar soluções e representações|**projetar**|
|**Construção e release**|Construção, testes, instalação, documentação, treinamento e suporte|**entregar**|
|**Avaliação do cliente**|Cliente avalia e gera feedback|**avaliar → novo ciclo**|

### Vantagens do Espiral

|Vantagem|Ideia principal|Lembrete rápido|
|---|---|---|
|**Gerenciamento de riscos**|Riscos são tratados continuamente|**principal vantagem**|
|**Projetos complexos**|Adequado para projetos grandes e complexos|**grande + arriscado**|
|**Flexibilidade**|Mudanças podem entrar nos ciclos|**aceita mudança**|
|**Participação do cliente**|Cliente acompanha versões antes do final|**feedback constante**|

**Espiral = alto controle de riscos + maior flexibilidade.**


### Desvantagens do Espiral

|Problema|Ideia principal|Lembrete rápido|
|---|---|---|
|**Complexidade**|Mais complexo que outros modelos|**difícil gerenciar**|
|**Custo**|Pode ser caro|**ruim para projeto pequeno**|
|**Dependência de especialistas**|Precisa de boa análise de riscos|**risco mal analisado = problema**|
|**Tempo difícil de prever**|Número de ciclos pode ser desconhecido|**quantas voltas? ninguém sabe**|

### Quando usar Espiral

| Tipo de sistema           | Motivo                                        | Lembrete rápido        |
| ------------------------- | --------------------------------------------- | ---------------------- |
| **Hospitalar**            | Validação, testes e conformidade              | **risco alto**         |
| **Governamental**         | Muitos stakeholders e requisitos variáveis    | **muita complexidade** |
| **Aeroespacial / Defesa** | Segurança, confiabilidade e hardware complexo | **risco crítico**      |
> **Espiral = projetos grandes + complexos + alto risco.**


# Prototipação

|Situação / Conceito|Regra / Ideia principal|Lembrete rápido|
|---|---|---|
|**Prototipação**|Cria uma representação preliminar do software|**versão antes da versão**|
|**Objetivo principal**|Compreender e validar requisitos|**descobrir o que realmente precisa**|
|**Protótipo**|Permite experimentar antes do produto final|**testar ideia**|
|**Quando usar**|Quando objetivos gerais são conhecidos, mas detalhes ainda não|**requisito nebuloso**|
|**Cliente**|Ajuda cliente e desenvolvedor a descobrir requisitos|**ver ajuda a entender**|

## Processo de Prototipação

|Ordem|Etapa|
|---|---|
|**1**|Coleta e refinamento de requisitos|
|**2**|Projeto rápido|
|**3**|Construção do protótipo|
|**4**|Avaliação pelo cliente|
|**5**|Refinamento do protótipo|
|**6**|Engenharia do produto final|

**Construir → avaliar → refinar.**


## Vantagens da Prototipação

|Vantagem|Lembrete rápido|
|---|---|
|Requisitos podem estar incompletos no início|**descobrir depois**|
|Facilita compreensão do sistema|**usuário consegue visualizar**|
|Maior envolvimento do usuário|**feedback**|
|Valida funcionalidades e interfaces|**testa antes de construir**|
|Permite testar ambiente e tecnologias|**experimentar cedo**|
|Ajuda a avaliar desempenho e banco de dados|**validar comportamento**|

## Desvantagens da Prototipação

| Problema                      | Ideia principal                                          | Lembrete rápido                             |
| ----------------------------- | -------------------------------------------------------- | ------------------------------------------- |
| **Começar cedo demais**       | Pode faltar análise suficiente do problema               | **protótipo sem entender problema**         |
| **Funções desnecessárias**    | Alterações sucessivas podem adicionar coisas inadequadas | **escopo maluco**                           |
| **Expectativa do cliente**    | Cliente pode achar que produto está quase pronto         | **“já tá funcionando, termina amanhã né?” * |
| **Mudanças parecem fáceis**   | Protótipo pode dar impressão falsa de simplicidade       | **protótipo engana**                        |
| **Protótipo ≠ produto final** | Pode faltar robustez e preparação para produção          | **funcionar ≠ estar pronto**                |

## Formas de Prototipação

|Tipo|Característica|Lembrete rápido|
|---|---|---|
|**Descartável**|Feito para aprender/avaliar e depois descartado|**faz → aprende → joga fora**|
|**Algumas funções**|Implementa apenas partes específicas|**testa só uma parte**|
|**Evolucionária**|Protótipo é refinado até evoluir junto com o sistema|**protótipo cresce**|

## Fidelidade dos Protótipos

| Fidelidade | Característica                                 | Lembrete rápido          |
| ---------- | ---------------------------------------------- | ------------------------ |
| **Baixa**  | Representação simples e rápida                 | **estrutura**            |
| **Média**  | Visual próximo do produto final                | **aparência**            |
| **Alta**   | Interface e interação próximas do sistema real | **experiência realista** |

## Baixa Fidelidade — Wireframe

|Situação|Regra / Ideia|
|---|---|
|**Nome**|Wireframe|
|**Objetivo**|Representar estrutura e fluxo|
|**Interação**|Pouca ou nenhuma|
|**Custo**|Baixo|
|**Velocidade**|Alta|
|**Uso**|Explorar ideias e requisitos|


## Média Fidelidade — Mockup

| Situação             | Regra / Ideia                             |
| -------------------- | ----------------------------------------- |
| **Nome**             | Mockup                                    |
| **Objetivo**         | Mostrar aparência mais próxima do produto |
| **Interação**        | Pode ser simulada                         |
| **Tecnologia final** | Não precisa usar a mesma                  |
| **Uso**              | Validar telas, elementos e organização    |

## Alta Fidelidade

|Situação|Regra / Ideia|
|---|---|
|**Semelhança**|Muito próxima do produto final|
|**Interação**|Próxima da real|
|**Tecnologia**|Pode usar tecnologia real do produto|
|**Custo**|Alto|
|**Tempo**|Maior|
|**Conhecimento técnico**|Maior|

## Comparação rápida — fidelidade

|Característica|Baixa|Média|Alta|
|---|---|---|---|
|**Semelhança**|Baixa|Média|Alta|
|**Interação**|Pouca/nenhuma|Simulada|Próxima da real|
|**Custo**|Baixo|Médio|Alto|
|**Criação**|Rápida|Média|Mais lenta|
|**Uso**|Explorar ideias|Validar interface|Simular produto real|

**Wireframe = estrutura**  
**Mockup = aparência**  
**Alta fidelidade = experiência próxima do real**


# Espiral × Prototipação Evolutiva × Ágil

|Modelo|Foco principal|Lembrete rápido|
|---|---|---|
|**Espiral**|Analisa riscos formalmente em todos os ciclos|**ANALISAR RISCOS**|
|**Prototipação Evolutiva**|Evita requisitos incorretos através da validação|**VALIDAR REQUISITOS**|
|**Ágil**|Reduz riscos com ciclos curtos e feedback|**ENTREGAR + FEEDBACK**|

**Evolutivo = desenvolver + avaliar + evoluir.**

**Iterativo = repetir e melhorar.**  
**Incremental = adicionar partes.**

**Incremento = parte FUNCIONAL do produto final.**

**Incremental = entrega cedo + feedback rápido + requisitos particionáveis.**

**Tipos de incremento:**  
**Evolutivo = aproveita**  
**Descartável = joga fora**  
**Operacional = protótipo + produto**

---

**Espiral = Boehm, 1988.**

**Espiral = ciclos + RISCOS.**

**4 etapas:**  
**Objetivos → Riscos → Desenvolvimento → Planejamento → novo ciclo.**

**Espiral funciona melhor em projeto grande, complexo e arriscado.**

---

**Prototipação = experimentar antes de construir.**

**Processo:**  
**Requisitos → projeto rápido → protótipo → cliente avalia → refina.**

**Protótipo funcional ≠ produto final pronto.**

**Descartável = joga fora.**  
**Evolucionário = vai virando o produto.**

**Wireframe = estrutura.**  
**Mockup = aparência.**  
**Alta fidelidade = quase real.**


**Incremental = entregar partes**  
**Espiral = controlar riscos**  
**Prototipação = validar requisitos**  
**Ágil = feedback rápido**