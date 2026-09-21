
# Modelo de Desenvolvimento Baseado em Componentes — Aula 05

## Modelo Baseado em Componentes

O **Modelo de Desenvolvimento Baseado em Componentes**, também chamado de **CBD — Component-Based Development** ou **CBSE — Component-Based Software Engineering**, é uma abordagem em que o sistema é construído a partir da combinação de **partes independentes, reutilizáveis e bem definidas**, chamadas de componentes.

A ideia principal é evitar reconstruir tudo do zero sempre que uma funcionalidade já existe e pode ser reaproveitada.

> **Versão curta:** O sistema é montado pela combinação de componentes reutilizáveis que possuem funções bem definidas.

**Componente = bloco reutilizável de software**

---

## Relação com Orientação a Objetos

O material relaciona o desenvolvimento baseado em componentes ao **Paradigma de Orientação a Objetos**.

Em orientação a objetos, uma **classe** encapsula dados e algoritmos responsáveis por manipular esses dados.

Essas classes podem ser organizadas e reutilizadas como componentes durante o desenvolvimento de diferentes sistemas.

O modelo também pode utilizar uma abordagem **iterativa**, aproveitando ideias do **Modelo Espiral**.

Durante cada iteração, a equipe verifica se já existe algum componente reutilizável disponível ou se um novo componente precisa ser criado.

**OO = encapsulamento**  
**Componentes = reutilização**

---

# Biblioteca de Componentes

Uma organização pode manter uma **biblioteca de componentes reutilizáveis**.

Durante o desenvolvimento de um novo sistema, essa biblioteca é consultada para verificar se alguma funcionalidade já existe.

Caso exista:

**componente existente → reutilização**

Caso não exista:

**novo componente → desenvolvimento → inclusão na biblioteca**

Assim, o desenvolvimento de um projeto também pode aumentar o conjunto de componentes disponíveis para projetos futuros.

---

# Origem dos Componentes

Os componentes podem ser:

- desenvolvidos internamente pela organização;
- adquiridos de terceiros;
- obtidos gratuitamente;
- disponibilizados como código aberto.

---

## Componentes Internos

São componentes desenvolvidos pela própria organização.

Podem ser utilizados inicialmente em um projeto e posteriormente reaproveitados em outros sistemas.

---

## Componentes de Terceiros

Um componente pode ser adquirido de uma empresa ou fornecedor externo.

O material apresenta o conceito de **COTS — Commercial Off-The-Shelf**.

Um COTS é um produto de software **pronto para uso**, adquirido no mercado, diferente de um software desenvolvido especificamente sob encomenda.

**COTS = componente comercial pronto**

---

## Componentes Gratuitos e Open Source

Também existem componentes disponibilizados gratuitamente na Internet.

Componentes **open source** disponibilizam seu código-fonte e podem permitir modificações, desde que sejam respeitadas as condições definidas pela licença.

**Open Source = código disponível + regras da licença**

---

# O que é um Componente?

Um **componente de software** é uma unidade:

- autônoma;
- reutilizável;
- substituível;
- responsável por uma funcionalidade específica.

Ele interage com outros componentes através de **interfaces bem definidas**.

> **Versão curta:** Um componente é uma parte independente do software que executa uma função específica e pode ser integrada a outros componentes.

**Componente = função específica + interface definida + reutilização**

---

## Exemplos de Componentes

Exemplos apresentados no material:

- módulo de autenticação;
- serviço de envio de e-mails;
- componente de pagamento;
- serviço de cálculo de impostos.

Um sistema de comércio eletrônico, por exemplo, pode reutilizar um componente responsável pelo **cálculo de impostos**, sem precisar implementar toda essa lógica novamente.

---

# Atividades do Desenvolvimento Baseado em Componentes

O modelo é organizado em quatro atividades principais:

**Qualificação → Adaptação → Combinação → Evolução**

---

## Qualificação dos Componentes

A **qualificação** consiste em analisar se um componente existente é adequado para ser utilizado no sistema.

É necessário verificar se ele atende às necessidades e requisitos do projeto.

**Qualificar = verificar se serve**

---

## Adaptação dos Componentes

Mesmo quando um componente pode ser reutilizado, ele pode precisar de ajustes para funcionar corretamente dentro do novo sistema.

A adaptação modifica ou configura o componente de acordo com o contexto em que será utilizado.

**Adaptar = ajustar para o sistema**

---

## Combinação dos Componentes

Depois de selecionados e adaptados, os componentes são **integrados** para formar o sistema.

Essa etapa depende das interfaces disponibilizadas por cada componente.

**Combinar = integrar componentes**

---

## Evolução do Sistema

Depois de construído, o sistema pode continuar evoluindo.

Componentes podem ser:

- atualizados;
- substituídos;
- modificados;
- adicionados.

A reutilização permite que novas funcionalidades sejam incorporadas sem necessariamente reconstruir o sistema inteiro.

---

# Componentes na Engenharia de Software Moderna

Embora o CBSE tenha se consolidado principalmente entre o final da década de **1990 e os anos 2000**, seus princípios aparecem em várias arquiteturas e tecnologias atuais.

O material destaca principalmente:

- **microsserviços**;
- interfaces baseadas em componentes;
- Design Systems;
- gerenciadores de dependências.

---

# Microsserviços

A **Arquitetura de Microsserviços** expande a ideia de componentes para serviços independentes.

Um sistema maior é dividido em pequenos serviços que possuem responsabilidades específicas e podem ser desenvolvidos e implantados separadamente.

Por exemplo, um sistema pode possuir serviços independentes para:

- autenticação;
- pagamentos;
- notificações;
- catálogo;
- processamento de pedidos.

Esses serviços normalmente se comunicam através de **APIs**.

**Microsserviço = componente independente em forma de serviço**

---

# Front-end Baseado em Componentes

No desenvolvimento de interfaces, aplicações podem ser construídas através da combinação de pequenos componentes reutilizáveis.

Exemplos:

- botão;
- formulário;
- menu;
- modal;
- card;
- carrossel.

Frameworks citados no material incluem:

- **React**;
- Next.js;
- Angular;
- Vue.

Uma alteração feita em um componente reutilizado pode ser refletida em todas as partes do sistema que utilizam aquele componente.

**Interface = composição de componentes visuais**

---

# Design Systems

Um **Design System** mantém componentes visuais padronizados que podem ser reutilizados em diferentes partes de um sistema ou até em vários produtos da organização.

Por exemplo, uma empresa pode manter versões padronizadas de:

- botões;
- campos;
- cards;
- menus;
- componentes de navegação.

Isso ajuda a manter **consistência visual e reutilização** entre aplicações.

---

# Gerenciadores de Dependências

Gerenciadores de dependências facilitam a distribuição e utilização de componentes produzidos por terceiros.

O material apresenta exemplos como:

| Ecossistema | Gerenciador |
| --- | --- |
| JavaScript / Node.js | npm |
| Java | Maven |
| .NET | NuGet |
| Python | pip |

Essas ferramentas permitem instalar e gerenciar bibliotecas e componentes reutilizáveis de maneira padronizada.

**Gerenciador de dependências = distribui e organiza componentes**

---

# Containers e Componentes

No back-end e na infraestrutura, componentes podem ser empacotados dentro de **containers**.

O material cita tecnologias como:

- **Docker**;
- Kubernetes.

Um serviço de autenticação ou pagamento, por exemplo, pode funcionar isoladamente dentro de seu próprio container.

### Docker

É utilizado para **empacotar componentes e aplicações em containers**.

### Kubernetes

É utilizado para **orquestrar containers** em ambientes distribuídos.

**Docker = empacota**  
**Kubernetes = orquestra**

---

# Platform Engineering

O material também relaciona o desenvolvimento baseado em componentes à **Engenharia de Plataforma — Platform Engineering**.

Nesse modelo, organizações mantêm plataformas internas que fornecem componentes e configurações de infraestrutura prontas para os desenvolvedores.

Assim, tarefas repetitivas podem ser reutilizadas sem que cada equipe precise configurar toda a infraestrutura novamente.

---

# Low-Code e No-Code

Plataformas **Low-Code** e **No-Code** também utilizam fortemente a ideia de componentes.

O usuário pode construir aplicações combinando elementos previamente desenvolvidos, como:

- gráficos;
- tabelas;
- formulários;
- integrações com APIs.

Exemplos apresentados:

- OutSystems;
- Microsoft Power Apps;
- Mendix.

**Low-Code / No-Code = montar sistemas com componentes prontos**

---

# Componentes e Inteligência Artificial

O material relaciona o desenvolvimento moderno com IA à reutilização de componentes e bibliotecas existentes.

Ferramentas de programação assistida e agentes podem gerar código e combinar elementos disponíveis em repositórios como **npm** ou **Maven**.

Nesse cenário, o material destaca um aumento da importância da **arquitetura do sistema**, garantindo que os componentes utilizados sejam integrados corretamente, com segurança e desempenho.

---

# Padrões e Tecnologias de Componentes

O material apresenta algumas tecnologias históricas e modernas relacionadas ao desenvolvimento baseado em componentes.

| Tecnologia | Ideia principal |
| --- | --- |
| COM | Componentes reutilizáveis da Microsoft |
| DCOM | Componentes distribuídos |
| CORBA | Comunicação entre objetos distribuídos |
| JavaBeans | Componentes Java reutilizáveis |
| EJB | Componentes Java para aplicações empresariais |
| .NET Components | Componentes do ecossistema .NET |
| Web Services | Comunicação entre sistemas |
| Microsserviços | Serviços pequenos e independentes |

---

# COM e DCOM

**COM — Component Object Model** é uma tecnologia da Microsoft criada para permitir a construção de componentes reutilizáveis capazes de interagir entre si.

**DCOM — Distributed Component Object Model** estende esse conceito para ambientes distribuídos.

**COM = componentes**  
**DCOM = componentes distribuídos**

---

# CORBA

**CORBA — Common Object Request Broker Architecture** é um padrão que permite que componentes escritos em diferentes linguagens e executados em diferentes computadores trabalhem juntos.

Ele permite realizar chamadas remotas de operações em objetos distribuídos através de uma rede.

> **Versão curta:** CORBA permite comunicação entre componentes distribuídos, mesmo quando utilizam tecnologias diferentes.

---

# JavaBeans e Enterprise JavaBeans

**JavaBeans** são componentes reutilizáveis escritos em Java.

O **Enterprise JavaBeans — EJB** é uma especificação utilizada em aplicações empresariais Java.

Os componentes EJB podem implementar **lógica de negócio** e utilizar serviços fornecidos pelo ambiente, como:

- transações;
- segurança;
- acesso a dados.

---

# Componentes .NET

O ecossistema **.NET** possui diferentes tipos de componentes.

Eles podem fazer parte:

- do runtime;
- das bibliotecas;
- de frameworks;
- da interface gráfica.

O material cita, por exemplo, componentes utilizados no **ASP.NET Core**.

---

# Web Services

Os **Web Services** permitem a comunicação e transferência de dados entre sistemas ou plataformas diferentes.

Podem utilizar protocolos e padrões como:

- **SOAP**;
- REST.

Eles permitem que funcionalidades sejam disponibilizadas para outros sistemas através da rede.

---

# Microsserviços

Os **Microsserviços** dividem uma aplicação grande em serviços menores, independentes e especializados.

Cada serviço possui uma função específica e normalmente se comunica com os demais através de **APIs**.

**Aplicação grande → vários serviços pequenos**

---

# Ferramentas Relacionadas a Componentes

O material apresenta algumas ferramentas utilizadas no desenvolvimento baseado em componentes:

| Ferramenta | Função |
| --- | --- |
| Docker | Empacotar componentes em containers |
| Kubernetes | Orquestrar componentes distribuídos |
| GitHub / GitLab | Versionar e armazenar componentes |
| Swagger / OpenAPI | Documentar APIs |

---

# Exemplo de Sistema de E-commerce

Um sistema de e-commerce pode ser dividido em componentes como:

- autenticação;
- catálogo de produtos;
- carrinho de compras;
- processamento de pagamentos;
- notificações.

Cada componente pode ser desenvolvido ou integrado separadamente.

Essa divisão facilita:

- manutenção;
- escalabilidade;
- reutilização.

---

# Utilização dos Componentes

Os componentes podem existir em diferentes camadas de uma aplicação.

| Camada | Exemplo | Função |
| --- | --- | --- |
| Interface | Botões, modais, carrosséis e formulários | Padronizar a interface e reutilizar código |
| Serviços de terceiros | Stripe / PayPal | Processamento de pagamentos |
| Infraestrutura / SDK | Firebase / Auth0 | Autenticação |
| Recursos nativos | Google Maps / Apple Maps | Mapas e navegação |

Isso mostra que um componente não precisa ser apenas uma classe ou parte interna do código.

Ele pode representar desde um pequeno elemento visual até um serviço externo inteiro.

---

# Exemplos Práticos

## Netflix

O material apresenta a Netflix como exemplo de uso de componentes tanto no **front-end** quanto no **back-end**.

Na interface, elementos como:

- carrosséis;
- thumbnails;
- player;
- botões;

podem ser tratados como componentes reutilizáveis.

No back-end, diferentes funcionalidades podem ser divididas em serviços independentes, como:

- recomendações;
- pagamentos;
- autenticação;
- streaming.

---

## Spotify

O Spotify é apresentado utilizando componentes de interface padronizados, como:

- player;
- barra de progresso;
- playlists;
- botão de curtir.

Também utiliza componentes e SDKs existentes para funções como áudio, autenticação e pagamentos.

---

## Uber

O Uber utiliza componentes e serviços de terceiros para evitar desenvolver tudo internamente.

Exemplos apresentados:

- Google Maps API / Mapbox para mapas e localização;
- Twilio para envio de mensagens.

A própria interface também pode ser dividida em componentes independentes, como seletor de veículos, valor da corrida e informações do motorista.

---

## Airbnb

O Airbnb utiliza bibliotecas e sistemas visuais baseados em componentes.

Elementos como:

- card de acomodação;
- calendário;
- filtros;
- avaliação por estrelas;

podem ser tratados como componentes independentes.

Uma alteração realizada em um componente reutilizado pode atualizar automaticamente as diferentes partes da aplicação que dependem dele.

---

# Ideia Central do Desenvolvimento Baseado em Componentes

O objetivo do modelo é construir sistemas através da **composição e reutilização de partes já existentes**, sempre que possível.

Em vez de pensar:

**“Como implementar tudo novamente?”**

a abordagem procura primeiro responder:

**“Já existe um componente que resolve essa parte?”**

Assim:

**Qualificar → Adaptar → Combinar → Evoluir**

O resultado é uma abordagem centrada em **reutilização, modularidade e integração**.

> **Versão curta:** Desenvolvimento Baseado em Componentes significa construir software combinando partes independentes e reutilizáveis através de interfaces bem definidas.

**Componente = construir uma vez, reutilizar quando fizer sentido**
