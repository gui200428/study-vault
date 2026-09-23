
# Processo de Desenvolvimento de Software — Aula 02

## Categorias de Desenvolvimento de Software

O **Processo de Desenvolvimento de Software** pode ser organizado em diferentes categorias, de acordo com a forma como a especificação e o desenvolvimento do sistema são conduzidos.

O material apresenta três categorias principais: **desenvolvimento clássico/genérico**, **desenvolvimento evolutivo** e **desenvolvimento formal**.

| Categoria | Característica principal |
| --- | --- |
| Clássico/Genérico | Especificação e desenvolvimento são separados |
| Evolutivo | Especificação e desenvolvimento são interligados |
| Formal | Utiliza um modelo matemático transformado até a implementação |

### Desenvolvimento Clássico ou Genérico

A **especificação** e o **desenvolvimento** são tratados como fases distintas e separadas.

**Exemplos:** Modelo Cascata e Modelo Espiral.

**Clássico = fases separadas**

### Desenvolvimento Evolutivo

A **especificação e o desenvolvimento acontecem de forma interligada**, permitindo que o sistema evolua durante sua construção.

**Evolutivo = especifica e desenvolve junto**

### Desenvolvimento Formal

O sistema é inicialmente representado através de um **modelo matemático formal**, que é transformado progressivamente até chegar à implementação.

**Formal = modelo matemático → implementação**

---

# Modelo Cascata

O **Modelo Cascata**, ou **Waterfall**, é um modelo de desenvolvimento **sequencial**, no qual o projeto avança através de fases bem definidas.

A ideia é semelhante à água descendo uma cascata: o desenvolvimento segue predominantemente **em uma direção**, passando de uma etapa para a próxima.

Sua estrutura linear torna o processo relativamente simples de administrar e permite estabelecer prazos e acompanhar o progresso do projeto. Em contrapartida, essa mesma estrutura torna o modelo **pouco flexível para mudanças**.

> **Resumo:** O Modelo Cascata organiza o desenvolvimento em fases sequenciais, concluindo uma etapa antes de avançar para a seguinte.

**Cascata = sequencial + previsível**

---

# Fases do Modelo Cascata

O Modelo Cascata possui as seguintes fases principais:

1. **Análise e definição de requisitos**
2. **Projeto de sistema e software**
3. **Implementação e teste unitário**
4. **Integração e teste do sistema**
5. **Operação e manutenção**

**Detalhamento:**

**Levantamento de requisitos → Planejamento → Modelagem → Desenvolvimento → Teste → Implantação → Manutenção**

---

## Levantamento e Definição de Requisitos

Nesta etapa são identificadas as **necessidades do cliente e dos usuários**.

Entre as atividades apresentadas estão:

- entrevistas com stakeholders;
- documentação dos requisitos;
- análise de viabilidade.

O objetivo é determinar **o que o sistema deverá fazer** antes que sua construção avance.

**Requisitos = o que o sistema precisa fazer**

---

## Planejamento do Sistema ou Produto

Após compreender os requisitos, é realizado o planejamento do projeto.

São definidos elementos como:

- **escopo**;
- cronograma;
- recursos necessários;
- tecnologias utilizadas.

O planejamento estabelece como o projeto deverá ser conduzido.

---

## Projeto e Modelagem

Nesta etapa é definida a estrutura do software antes da implementação.

O material apresenta atividades como:

- desenho da arquitetura;
- modelagem de dados;
- prototipagem.

Enquanto os requisitos definem **o que** deve ser construído, o projeto começa a determinar **como** o sistema será construído.

**Requisitos = o que fazer**  
**Projeto = como fazer**

---

## Implementação e Teste Unitário

A implementação corresponde à **codificação do sistema**.

Durante essa etapa também são realizados **testes unitários**, utilizados para verificar individualmente as unidades ou componentes desenvolvidos.

O objetivo é verificar se cada unidade atende à sua especificação.

---

## Integração e Teste do Sistema

Depois que os componentes individuais são desenvolvidos, eles são integrados e o sistema passa por testes mais amplos.

O material apresenta:

- testes funcionais;
- testes de integração;
- correção de bugs.

Aqui o objetivo deixa de ser apenas verificar componentes isolados e passa a verificar o **funcionamento do sistema integrado**.

**Teste unitário = componente isolado**  
**Teste de integração = componentes trabalhando juntos**

---

## Implantação

A implantação corresponde à disponibilização do sistema para uso.

Pode envolver:

- treinamento dos usuários;
- lançamento do software;
- suporte após o lançamento.

É nessa etapa que o sistema começa efetivamente a ser utilizado no ambiente para o qual foi desenvolvido.

---

## Operação e Manutenção

Após a implantação, o software entra em operação e pode precisar de correções ou adaptações.

A manutenção permite lidar com problemas descobertos posteriormente e com necessidades que aparecem durante a utilização do sistema.

---

# Funcionamento Sequencial do Modelo Cascata

A característica principal do Cascata é que cada fase depende da conclusão da anterior.

Isso facilita a criação de **cronogramas**, documentos e pontos de controle, já que o projeto possui etapas claramente delimitadas.

Por outro lado, quando uma necessidade muda durante o desenvolvimento, o modelo não possui um mecanismo formal e flexível para retornar e reorganizar as etapas anteriores.

O material também destaca que nenhum componente funcional precisa ser entregue ao cliente até que o projeto esteja próximo de sua conclusão. Isso pode aumentar a distância entre usuários e desenvolvedores durante o processo.

**Cascata = termina uma fase → avança para a próxima**

---

# Problemas do Modelo Cascata

Apesar de sua organização simples, o Modelo Cascata apresenta dificuldades quando aplicado a projetos em que existe incerteza ou mudanças frequentes.

## Projetos Reais Nem Sempre São Sequenciais

Projetos reais raramente seguem perfeitamente um fluxo linear.

Embora alterações possam acontecer durante o processo, o Cascata não foi estruturado para trabalhar naturalmente com ciclos constantes de revisão.

Mudanças feitas quando o projeto já avançou podem causar confusão e retrabalho.

---

## Dificuldade em Definir Todos os Requisitos no Início

O Cascata depende fortemente de uma definição inicial dos requisitos.

Porém, muitas vezes o próprio cliente ainda não conhece completamente todas as necessidades do sistema.

Isso torna o modelo menos adequado quando existe muita **incerteza no início do projeto**.

**Cascata funciona melhor quando os requisitos já são conhecidos.**

---

## Software Executável Aparece Tarde

Uma versão executável geralmente só aparece nas etapas mais avançadas do projeto.

Isso significa que o cliente precisa esperar bastante tempo para visualizar um produto funcional.

Caso exista um erro importante nas decisões iniciais, ele pode ser descoberto apenas quando grande parte do projeto já foi desenvolvida.

**Erro descoberto tarde = retrabalho maior**

---

# Vantagens do Modelo Cascata

Apesar de suas limitações, o Cascata ainda pode ser útil em determinados tipos de projeto.

### Estrutura simples

As fases são claramente definidas e organizadas, facilitando o acompanhamento do desenvolvimento.

### Previsibilidade

A existência de etapas, documentos e prazos facilita o planejamento e o controle do projeto.

### Documentação

O modelo é fortemente baseado em **documentação formal**, permitindo registrar os resultados obtidos em cada fase.

### Coordenação de grandes projetos

Segundo Sommerville, o modelo pode ser utilizado em grandes projetos de engenharia desenvolvidos em vários locais.

Sua abordagem orientada por planos facilita a coordenação entre diferentes equipes.

---

# Baseline do Projeto

Uma vantagem apresentada no material é a possibilidade de estabelecer uma **baseline**.

A baseline representa um **conjunto fixo de documentos produzidos como resultado de determinada fase do ciclo de vida**.

Ela serve como uma referência oficial para acompanhar o desenvolvimento do projeto.

> **Resumo:** Baseline é uma referência fixa e documentada do estado do projeto em determinado momento.

**Baseline = referência oficial**

---

# Desvantagens do Modelo Cascata

O Cascata é mais apropriado quando os requisitos estão **bem definidos e sofrem poucas alterações**.

Desvantagens:

- dificuldade de acomodar mudanças nos requisitos;
- pouco ou nenhum feedback natural entre as fases;
- dificuldade para retornar e redefinir etapas anteriores;
- demora para entregar uma versão funcional;
- atrasos em uma etapa podem afetar todo o restante do projeto;
- dependência de requisitos relativamente estáveis;
- pouca flexibilidade;
- dificuldade de reutilização;
- processo excessivamente sincronizado.

O modelo **“não prevê a manutenção”**, apesar de apresentar anteriormente **Operação e Manutenção** como uma das fases do Cascata.

---

# Quando o Modelo Cascata é Adequado

O Cascata é mais indicado quando existe **alta previsibilidade** e os requisitos podem ser definidos com clareza antes do desenvolvimento.

O material cita especialmente ambientes nos quais documentação, controle e previsibilidade são importantes, incluindo setores **regulados**, como aeroespacial e defesa.

**Requisitos estáveis = Cascata funciona melhor**  
**Requisitos mudando sempre = Cascata encontra dificuldades**

---

# Modelo Cascata × Métodos Ágeis

O Cascata e os métodos ágeis possuem abordagens diferentes para organizar o desenvolvimento.

| Aspecto             | Modelo Cascata             | Métodos Ágeis                      |
| ------------------- | -------------------------- | ---------------------------------- |
| Filosofia           | Sequencial e preditiva     | Iterativa e adaptativa             |
| Estrutura           | Fases rígidas e definidas  | Ciclos curtos                      |
| Flexibilidade       | Baixa                      | Alta                               |
| Cliente             | Participação mais limitada | Participação contínua              |
| Entregas            | Principalmente ao final    | Incrementais e frequentes          |
| Riscos              | Podem aparecer mais tarde  | Tratados continuamente             |
| Documentação        | Extensa e formal           | Leve e focada no essencial         |
| Mudanças            | Difíceis após o início     | Adaptadas durante o projeto        |
| Resultado funcional | Aparece mais tarde         | Surge desde os primeiros ciclos    |
| Projeto adequado    | Requisitos estáveis        | Requisitos incertos ou em evolução |

**Cascata = seguir o plano**  
**Ágil = adaptar o plano**

---

# Envolvimento do Cliente

No **Modelo Cascata**, o cliente normalmente possui maior participação no início, durante a definição das necessidades, e no final, quando recebe o produto.

Nos **métodos ágeis**, o cliente participa continuamente dos ciclos de desenvolvimento, avaliando resultados e ajudando a ajustar os requisitos.

Essa participação frequente permite que mudanças sejam incorporadas mais facilmente durante o projeto.

---

# Entrega de Valor

No Cascata, uma versão completa ou utilizável tende a aparecer apenas nas fases finais.

Nos métodos ágeis, o desenvolvimento acontece em **ciclos curtos**, permitindo entregas menores e frequentes.

Isso permite que o usuário visualize resultados funcionais mais cedo.

**Cascata = entrega tardia**  
**Ágil = entregas incrementais**

---

# Mudanças nos Requisitos

No Cascata, mudanças realizadas após o início do desenvolvimento são difíceis de incorporar porque podem exigir alterações em etapas consideradas concluídas.

Nos métodos ágeis, mudanças são consideradas parte natural do desenvolvimento e podem ser incorporadas entre os ciclos.

Por isso:

**Requisitos estáveis → Cascata**  
**Requisitos em evolução → Ágil**

---

# Gestão de Riscos

No Cascata, alguns riscos podem ser identificados apenas nas etapas mais avançadas, principalmente quando o sistema começa a ser integrado e testado.

Nos métodos ágeis, os ciclos curtos e o feedback frequente permitem que problemas sejam identificados e tratados continuamente.

---

# Documentação

O Modelo Cascata utiliza documentação **extensa e formal**.

Isso facilita auditorias, acompanhamento e registro das decisões tomadas ao longo do projeto.

Nos métodos ágeis, a documentação tende a ser **mais leve e focada no essencial**, priorizando também entregas frequentes e interação durante o desenvolvimento.

---

# Exemplos de Uso do Modelo Cascata

O material apresenta o Cascata principalmente em sistemas onde **segurança, estabilidade, documentação e previsibilidade** possuem grande importância.

| Tipo de sistema | Motivo |
| --- | --- |
| Sistemas embarcados | Requisitos rígidos e testes extensivos |
| Sistemas bancários legados | Estabilidade e segurança |
| Sistemas militares e aeroespaciais | Regulamentação, certificações e auditorias |
| Sistemas governamentais | Requisitos legais e documentação formal |
| Infraestrutura crítica | Segurança e previsibilidade |

### Sistemas Embarcados

Exemplos incluem sistemas de controle de **aeronaves, automóveis e equipamentos médicos**.

Nesses sistemas, requisitos rígidos e testes extensivos são importantes.

### Sistemas Bancários Legados

Aplicações de transações, contabilidade e controle de crédito podem utilizar processos mais previsíveis quando mudanças são raras e existe forte preocupação com **estabilidade e segurança**.

### Software Militar e Aeroespacial

São ambientes altamente regulados, que podem exigir:

- certificações;
- auditorias;
- documentação formal.

### Sistemas Governamentais

Sistemas relacionados a gestão pública, previdência e impostos podem possuir exigências legais e burocráticas que favorecem processos mais documentados.

### Infraestrutura Crítica

Sistemas responsáveis por energia, telecomunicações e transporte ferroviário priorizam principalmente **segurança e previsibilidade**.

---

# Exemplos de Uso de Métodos Ágeis

Os métodos ágeis aparecem principalmente em projetos onde existe necessidade de **evolução contínua**, feedback e adaptação.

| Tipo de software | Característica |
| --- | --- |
| Aplicativos móveis | Mudam com o feedback dos usuários |
| Sistemas Web e E-commerce | Recebem novas funcionalidades constantemente |
| Startups | Precisam testar ideias e adaptar rapidamente |
| Sistemas corporativos internos | Evolução e melhoria contínua |
| Jogos digitais | Balanceamento e novas funcionalidades frequentes |

### Aplicativos Móveis

Aplicativos de redes sociais, delivery, saúde ou educação podem alterar seus requisitos conforme recebem **feedback dos usuários**.

### Sistemas Web e E-commerce

Plataformas de vendas, marketplaces e outros sistemas Web normalmente recebem novas funcionalidades e alterações ao longo do tempo.

### Startups de Tecnologia

Startups trabalham frequentemente com **MVPs — Produtos Mínimos Viáveis**, utilizando versões iniciais para testar ideias no mercado.

Nesse contexto, velocidade e capacidade de adaptação são importantes.

### Sistemas Corporativos Internos

Ferramentas como sistemas de gestão, **CRM** e **ERP** podem utilizar desenvolvimento ágil quando estão inseridas em ambientes que exigem melhorias constantes.

### Jogos Digitais

Jogos mobile, multiplayer e plataformas interativas podem utilizar iterações rápidas para realizar:

- balanceamento;
- ajustes;
- inclusão de novas funcionalidades.

**Cascata = estabilidade e previsibilidade**  
**Ágil = mudança e adaptação**


### Tabela resumo 

|Situação / Conceito|Regra / Ideia principal|Lembrete rápido|
|---|---|---|
|**Desenvolvimento Clássico/Genérico**|Especificação e desenvolvimento acontecem em fases separadas|**fases separadas**|
|**Exemplos — Clássico**|Cascata e Espiral|**modelo tradicional**|
|**Desenvolvimento Evolutivo**|Especificação e desenvolvimento acontecem de forma interligada|**especifica + desenvolve junto**|
|**Desenvolvimento Formal**|Parte de um modelo matemático formal que é transformado até chegar à implementação|**modelo matemático → implementação**|

### Modelo Cascata

|Situação / Conceito|Regra / Ideia principal|Lembrete rápido|
|---|---|---|
|**Modelo Cascata / Waterfall**|Modelo sequencial com fases bem definidas|**sequencial**|
|**Funcionamento**|Uma etapa é concluída antes de avançar para a próxima|**termina → avança**|
|**Direção do processo**|Predominantemente linear|**vai pra frente**|
|**Vantagem estrutural**|Facilita planejamento, cronogramas e acompanhamento|**organizado + previsível**|
|**Principal limitação**|Pouca flexibilidade para mudanças|**mudança = problema**|
|**Quando funciona melhor**|Quando requisitos são conhecidos e estáveis|**requisito estável = Cascata**|

### Fases do Modelo Cascata
|Fase|Ideia principal|Lembrete rápido|
|---|---|---|
|**1. Requisitos**|Identificar necessidades do cliente e usuários|**o que fazer**|
|**2. Planejamento**|Definir escopo, cronograma, recursos e tecnologias|**organizar o projeto**|
|**3. Projeto / Modelagem**|Definir arquitetura, dados e estrutura do software|**como fazer**|
|**4. Implementação**|Codificar o sistema|**programar**|
|**5. Teste unitário**|Testar cada componente individualmente|**peça isolada**|
|**6. Integração / teste de sistema**|Testar os componentes trabalhando juntos|**sistema completo**|
|**7. Implantação**|Disponibilizar o sistema para uso|**colocar em produção**|
|**8. Operação e manutenção**|Corrigir, adaptar e evoluir depois da entrega|**manter funcionando**|

### Requisitos × Projeto

|Conceito|Ideia principal|Lembrete rápido|
|---|---|---|
|**Requisitos**|Definem aquilo que o sistema precisa fazer|**O QUE**|
|**Projeto / Modelagem**|Define como o sistema será construído|**COMO**|
|**Levantamento de requisitos**|Pode usar entrevistas, documentação e análise de viabilidade|**entender a necessidade**|
|**Planejamento**|Define escopo, cronograma, recursos e tecnologia|**organizar execução**|

### Testes

|Situação / Conceito|Regra / Ideia principal|Lembrete rápido|
|---|---|---|
|**Teste unitário**|Testa unidades ou componentes individualmente|**isolado**|
|**Teste de integração**|Testa componentes funcionando em conjunto|**juntos**|
|**Teste funcional**|Verifica funções do sistema|**faz o que deveria?**|
|**Correção de bugs**|Problemas encontrados são corrigidos antes da entrega|**achar → corrigir**|

### Funcionamento sequencial do Cascata

|Situação / Conceito|Regra / Ideia principal|Lembrete rápido|
|---|---|---|
|**Dependência entre fases**|Cada fase depende da conclusão da anterior|**uma depois da outra**|
|**Cronogramas**|São facilitados por etapas bem delimitadas|**fácil acompanhar**|
|**Documentação**|Cada etapa tende a gerar registros/documentos|**processo documentado**|
|**Mudança tardia**|Pode exigir retorno a etapas já concluídas|**gera retrabalho**|
|**Entrega funcional**|Normalmente aparece mais perto do fim|**cliente espera mais**|
|**Distância cliente-desenvolvedor**|Pode ser maior durante o processo|**menos feedback contínuo**|

### Problemas do Modelo Cascata

|Situação / Problema|Regra / Ideia principal|Lembrete rápido|
|---|---|---|
|**Projetos reais não são totalmente lineares**|Projetos frequentemente exigem revisões e alterações|**vida real não é reta**|
|**Mudanças**|Não são naturais no Cascata|**mudou? complicou**|
|**Requisitos incompletos**|Cliente pode não conhecer tudo no início|**incerteza = problema**|
|**Produto executável tardio**|Cliente vê o sistema funcionando só mais tarde|**feedback demora**|
|**Erro descoberto tarde**|Pode exigir grande retrabalho|**erro tarde = caro**|
|**Atraso em uma fase**|Pode impactar todas as etapas seguintes|**efeito dominó**|
|**Pouca flexibilidade**|Difícil reorganizar etapas concluídas|**rígido**|

### Vantagens do Cascata

|Vantagem|Ideia principal|Lembrete rápido|
|---|---|---|
|**Estrutura simples**|Fases claras e organizadas|**fácil entender**|
|**Previsibilidade**|Facilita planejamento de prazos e etapas|**planejável**|
|**Documentação**|Produz documentação formal ao longo do projeto|**tudo registrado**|
|**Controle**|Facilita acompanhamento e pontos de controle|**gestão fácil**|
|**Grandes projetos**|Pode facilitar coordenação entre equipes em diferentes locais|**coordenação por plano**|

### Baseline

|Conceito|Ideia principal|Lembrete rápido|
|---|---|---|
|**Baseline**|Conjunto fixo de documentos produzidos ao final de uma fase|**referência oficial**|
|**Função**|Serve para comparar e acompanhar o estado do projeto|**foto oficial do projeto**|
|**Uso**|Ajuda no controle e acompanhamento|**ponto de referência**|

### Desvantagens do Cascata

| Desvantagem                           | Lembrete rápido               |
| ------------------------------------- | ----------------------------- |
| Mudanças difíceis de acomodar         | **pouca flexibilidade**       |
| Pouco feedback entre fases            | **fases isoladas**            |
| Difícil voltar para etapas anteriores | **retorno complicado**        |
| Entrega funcional demora              | **produto aparece tarde**     |
| Atrasos afetam o restante             | **efeito cascata mesmo**      |
| Depende de requisitos estáveis        | **incerteza atrapalha**       |
| Dificuldade de reutilização           | **reutilização limitada**     |
| Processo muito sincronizado           | **uma fase depende da outra** |

### Quando usar Cascata

| Situação                            | Adequação         | Lembrete rápido              |
| ----------------------------------- | ----------------- | ---------------------------- |
| **Requisitos claros e estáveis**    | Boa               | **Cascata funciona bem**     |
| **Mudanças frequentes**             | Ruim              | **Cascata sofre**            |
| **Alta previsibilidade necessária** | Boa               | **controle**                 |
| **Documentação formal obrigatória** | Boa               | **documentação forte**       |
| **Setores regulados**               | Pode ser adequado | **auditoria + certificação** |

### Cascata × Métodos Ágeis

|Aspecto|Cascata|Ágil|
|---|---|---|
|**Filosofia**|Sequencial e preditiva|Iterativa e adaptativa|
|**Estrutura**|Fases rígidas|Ciclos curtos|
|**Flexibilidade**|Baixa|Alta|
|**Cliente**|Participação mais limitada|Participação contínua|
|**Entrega**|Principalmente no final|Frequente e incremental|
|**Mudanças**|Difíceis|Esperadas e adaptadas|
|**Riscos**|Podem aparecer tarde|Tratados continuamente|
|**Documentação**|Extensa e formal|Mais leve e essencial|
|**Resultado funcional**|Aparece tarde|Surge cedo|
|**Requisitos**|Estáveis|Incertos ou em evolução|

### Cliente e entregas

|Situação|Cascata|Ágil|
|---|---|---|
|**Participação do cliente**|Mais forte no início e no final|Contínua|
|**Feedback**|Menos frequente|Frequente|
|**Entrega funcional**|Mais tardia|Mais cedo|
|**Forma de entrega**|Grande entrega ao final|Pequenas entregas frequentes|
|**Mudança de requisitos**|Difícil|Natural entre ciclos|

### Gestão de riscos e documentação

|Aspecto|Cascata|Ágil|
|---|---|---|
|**Riscos**|Alguns podem aparecer apenas mais tarde|Identificados continuamente|
|**Feedback**|Menos frequente|Frequente|
|**Documentação**|Extensa e formal|Leve e focada no essencial|
|**Auditoria**|Facilitada pela documentação|Menos foco em documentação extensa|

### Exemplos de uso do Cascata

|Tipo de sistema|Por que Cascata pode ser usado|Lembrete rápido|
|---|---|---|
|**Sistemas embarcados**|Requisitos rígidos e testes extensivos|**controle + segurança**|
|**Bancários legados**|Estabilidade e segurança|**não pode quebrar**|
|**Militares / aeroespaciais**|Certificações, auditorias e regulamentações|**regulado**|
|**Governamentais**|Exigências legais e documentação formal|**burocracia/documentação**|
|**Infraestrutura crítica**|Segurança e previsibilidade|**risco alto**|

### Exemplos de uso de métodos Ágeis

|Tipo de software|Por que Ágil funciona bem|Lembrete rápido|
|---|---|---|
|**Aplicativos móveis**|Mudam conforme feedback|**usuário muda → app muda**|
|**Web / E-commerce**|Novas funções aparecem constantemente|**evolução contínua**|
|**Startups**|Precisam testar ideias rapidamente|**MVP + adaptação**|
|**Sistemas internos**|Precisam de melhorias frequentes|**evolução constante**|
|**Jogos digitais**|Balanceamento e novas funções contínuas|**itera e ajusta**|

**3 categorias:**  
**Clássico = separa**  
**Evolutivo = junta**  
**Formal = matematiza**

**Cascata = sequencial + previsível + rígido.**

**Fases:**  
**Requisitos → Planejamento → Projeto → Implementação → Testes → Implantação → Manutenção**

**Requisitos = O QUE**  
**Projeto = COMO**

**Unitário = componente sozinho**  
**Integração = componentes juntos**

**Baseline = referência oficial do projeto.**

**Cascata funciona melhor com requisitos estáveis.**

**Mudança frequente = Cascata sofre.**

**Cascata = plano + documentação + previsibilidade.**  
**Ágil = ciclos curtos + feedback + adaptação.**

**Cascata = entrega tarde.**  
**Ágil = entrega incremental.**

**Cascata = seguir o plano.**  
**Ágil = adaptar o plano.**

**Cascata = estabilidade e previsibilidade.**  
**Ágil = mudança e adaptação.**