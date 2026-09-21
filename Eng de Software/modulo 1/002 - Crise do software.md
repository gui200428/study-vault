# Engenharia de Software I — Aula 01

## Crise do Software

A **Crise do Software** surgiu principalmente nas décadas de **1960 e 1970**, quando a complexidade dos sistemas começou a crescer mais rápido do que a capacidade das equipes de desenvolver e manter esses sistemas.

A falta de **metodologias formais**, ferramentas adequadas e planejamento resultava em projetos atrasados, custos maiores do que o previsto e softwares de baixa qualidade.

A resposta para esses problemas foi o surgimento da **Engenharia de Software**.

> **Versão curta:** A Crise do Software representa os problemas causados pela dificuldade de desenvolver softwares cada vez mais complexos de forma organizada e previsível.

### Principais problemas da Crise do Software

Segundo Pressman, os principais problemas encontrados no desenvolvimento de software eram:

- **estimativas de prazo e custo imprecisas**;
- **produtividade insuficiente** para acompanhar a demanda;
- **qualidade de software inadequada**;
- **dificuldade de manutenção** dos sistemas existentes.

**Prazo e custo = difíceis de prever**  
**Produtividade = não acompanha a demanda**  
**Qualidade = abaixo do esperado**  
**Manutenção = difícil e cara**

---

# Problemas Associados à Crise do Software

Os problemas da crise não estavam relacionados apenas ao código. O material destaca três fatores principais.

## Falhas das Pessoas Responsáveis pelo Desenvolvimento

Um dos problemas estava relacionado à própria organização das equipes.

Era comum existir:

- gerentes com pouca experiência ou conhecimento sobre desenvolvimento de software;
- profissionais com pouco treinamento formal em novas técnicas;
- **resistência a mudanças**.

Esses fatores dificultavam a adoção de melhores métodos de desenvolvimento.

---

## Próprio Caráter do Software

O software é um elemento **lógico**, e não físico.

Diferentemente de um produto industrial, seu sucesso não depende da fabricação de milhares de unidades físicas, mas da qualidade de uma mesma entidade lógica.

Outro ponto importante é que:

**Software não se desgasta fisicamente, mas se deteriora.**

Essa deterioração acontece principalmente conforme o sistema sofre alterações, correções e adaptações ao longo do tempo.

**Hardware = físico**  
**Software = lógico**

---

# Mitos do Software

Os **mitos do software** são ideias consideradas verdadeiras dentro do desenvolvimento de software, mas que não correspondem à realidade do processo.

Essas falsas percepções podem causar problemas de **planejamento**, comunicação e desenvolvimento.

O material divide os mitos em três grupos:

| Tipo de mito | Relacionado a |
| --- | --- |
| Gerenciamento | Gestão do projeto e da equipe |
| Clientes | Requisitos e mudanças solicitadas |
| Profissionais | Trabalho de desenvolvimento |

---

# Mitos de Gerenciamento

## “Já temos um manual com padrões e procedimentos”

Ter documentação ou um manual de desenvolvimento não significa automaticamente que a equipe possui tudo o que precisa.

É necessário verificar se o material:

- realmente é utilizado;
- é conhecido pelos profissionais;
- acompanha as práticas modernas;
- possui informações completas.

**Ter padrão ≠ aplicar o padrão**

---

## “Temos computadores modernos, então temos boas ferramentas”

Possuir computadores modernos ou equipamentos de última geração **não garante software de qualidade**.

A qualidade depende também de métodos, processos, ferramentas adequadas e conhecimento técnico.

---

## “Se o projeto está atrasado, basta adicionar mais programadores”

Adicionar pessoas a um projeto atrasado não necessariamente acelera o desenvolvimento.

Novos integrantes precisam entender o projeto, receber informações e se integrar à equipe, aumentando inicialmente o esforço de comunicação e coordenação.

O material destaca que pessoas podem ser adicionadas, mas isso deve acontecer de forma **planejada**.

**Mais pessoas ≠ automaticamente mais velocidade**

---

# Mitos dos Clientes

## “Uma definição geral dos objetivos é suficiente”

Começar o desenvolvimento apenas com uma ideia geral do sistema pode gerar problemas posteriormente.

Uma definição inicial adequada deve detalhar aspectos como:

- domínio da informação;
- funções;
- desempenho;
- interfaces;
- restrições do projeto;
- critérios de validação.

Uma definição inicial ruim é apontada como uma das principais causas de fracasso no desenvolvimento de software.

> **Versão curta:** Quanto melhor os requisitos forem definidos no início, menor a chance de problemas durante o desenvolvimento.

---

## “Mudanças são fáceis porque software é flexível”

O software pode ser alterado, mas isso não significa que qualquer mudança seja simples ou barata.

Quanto mais tarde uma mudança é solicitada, **maior tende a ser seu custo**.

### Custo relativo das mudanças

| Fase | Custo relativo |
| --- | ---: |
| Definição | **1x** |
| Desenvolvimento | **1,5x a 6x** |
| Manutenção | **60x a 100x** |

Uma mudança realizada durante a definição tende a ser muito mais simples do que uma alteração realizada quando o sistema já está funcionando e precisa ser mantido.

**Mudança cedo = mais barata**  
**Mudança tarde = mais cara**

---

# Fases e Custos

O material também apresenta a seguinte distribuição:

| Fase | Percentual apresentado | Principais atividades |
| --- | ---: | --- |
| Definição | 10% a 15% | Requisitos, viabilidade e planejamento |
| Desenvolvimento | 15% a 30% | Arquitetura, interface, código, testes e documentação |
| Manutenção | 60% a 80% | Correções, adaptações, melhorias e novas funções |

A **manutenção** pode representar a maior parcela dos esforços relacionados ao software.

---

# Mitos dos Profissionais

## “Quando o programa estiver funcionando, o trabalho acabou”

Colocar o programa em funcionamento não encerra o desenvolvimento.

O material indica que grande parte do esforço relacionado ao software acontece **depois da primeira entrega ao cliente**, principalmente devido à manutenção e evolução do sistema.

---

## “Só consigo avaliar a qualidade quando o programa estiver funcionando”

Um programa executando corretamente representa apenas uma parte do software.

A qualidade também pode ser analisada por outros elementos produzidos durante seu desenvolvimento e manutenção.

---

## “O único produto entregue é o programa funcionando”

O software não é composto apenas pelo código executável.

Uma **configuração de software** pode incluir:

- programa;
- modelos;
- documentos;
- planos;
- elementos de suporte.

**Software ≠ somente código**

---

## “Engenharia de Software só cria documentação”

O objetivo da Engenharia de Software não é produzir documentação desnecessária.

Seu objetivo é ajudar na criação de um **produto de qualidade**, reduzindo problemas e **retrabalho**.

**Engenharia de Software = qualidade + organização + menos retrabalho**

---

# Engenharia de Software

A **Engenharia de Software** surgiu como resposta aos problemas observados durante a Crise do Software.

Segundo a definição apresentada pelo IEEE, consiste na aplicação de uma abordagem:

- **sistemática**;
- **disciplinada**;
- **mensurável**;

para o desenvolvimento, operação e manutenção do software.

Ela envolve três elementos fundamentais:

**Métodos + Ferramentas + Procedimentos**

### Métodos

Definem técnicas utilizadas para **projetar e construir** o software.

### Ferramentas

Auxiliam a execução das atividades de desenvolvimento.

### Procedimentos

Organizam a forma como métodos e ferramentas são utilizados durante o processo.

> **Versão curta:** Engenharia de Software aplica métodos, ferramentas e procedimentos de forma sistemática para desenvolver e manter software com qualidade.

---

# Aplicações do Software

O material apresenta diferentes aplicações e categorias de software.

| Categoria | Ideia principal |
| --- | --- |
| Inteligência Artificial | Resolve problemas utilizando algoritmos não numéricos |
| Web | Aplicações acessadas por meio de um navegador |
| Computação Ubíqua | Relacionada à computação distribuída integrada ao ambiente |
| Software Aberto | Disponibiliza o código-fonte para visualização e modificação |

## Software de Inteligência Artificial

Utiliza **algoritmos não numéricos** para resolver problemas que não são facilmente tratados por computação ou análise direta.

**IA = resolver problemas complexos**

---

## Software Web

São aplicações executadas ou acessadas através de um **browser**.

**Web = navegador**

---

## Software de Computação Ubíqua

Está relacionado à utilização de software em ambientes de **computação distribuída**, permitindo que a computação esteja presente em diferentes dispositivos e contextos.

**Ubíqua = distribuída**

---

## Software Aberto

Disponibiliza seu **código-fonte**, permitindo que ele seja visualizado e modificado.

**Aberto = código-fonte acessível**

---

# Problemas de Desenvolvimento Atualmente

Alguns dos problemas associados à antiga Crise do Software ainda aparecem no desenvolvimento moderno, embora de formas diferentes.

## Gerentes sem Conhecimento Técnico

No passado, era comum utilizar modelos de gestão baseados em indústrias físicas para administrar projetos de software.

Atualmente, o problema pode aparecer quando gestores analisam apenas **prazos e entregas**, sem considerar fatores técnicos como:

- complexidade do sistema;
- arquitetura;
- débito técnico;
- limitações da equipe.

---

## Falta de Treinamento

No passado, muitos programadores aprendiam desenvolvimento de maneira empírica, sem metodologias ou padrões consolidados.

Atualmente, novas linguagens, frameworks, ferramentas de nuvem e tecnologias de IA surgem rapidamente.

Isso pode criar uma diferença entre:

**usar ferramentas modernas**  
e  
**aplicar corretamente os fundamentos da Engenharia de Software**.

---

## Resistência a Mudanças

No passado, havia resistência à adoção de documentação, testes formais e padrões de projeto.

Atualmente, essa resistência também pode aparecer na adoção de práticas como:

- DevOps;
- automação de testes;
- refatoração contínua;
- novas formas de gestão ágil.

Manter um processo apenas porque **“sempre foi feito assim”** pode impedir a evolução do desenvolvimento.

---

# Software Legado

Um **software legado** é um sistema desenvolvido há muitos anos e que continua sendo modificado para acompanhar mudanças nos requisitos de negócio e nas plataformas computacionais.

Esses sistemas podem apresentar problemas como:

- baixa qualidade;
- documentação inexistente ou incompleta;
- poucos casos de teste;
- falta de controle adequado de mudanças.

Mesmo apresentando essas dificuldades, muitos sistemas legados continuam executando **funções essenciais para o negócio**, tornando sua substituição difícil.

> **Versão curta:** Software legado é um sistema antigo que continua sendo usado e modificado porque ainda executa funções importantes.

**Legado = antigo + ainda necessário**

---

# Falhas de Software

Falhas de software podem provocar consequências muito maiores do que simplesmente um programa fechar ou apresentar uma mensagem de erro.

Dependendo do sistema afetado, uma falha pode interromper serviços, comunicações, operações empresariais e infraestrutura.

Um exemplo apresentado é a falha global envolvendo uma **atualização da CrowdStrike**, que afetou computadores Windows e provocou problemas em voos, bancos, telecomunicações, mídia e serviços de saúde.

Outro exemplo é a interrupção da **Starlink em 2025**, atribuída no material a uma falha em serviços internos essenciais de software da rede.

---

# Causas de Falhas

## Erros de Código

**Bugs** podem surgir durante o desenvolvimento, testes ou manutenção.

Eles podem causar travamentos ou comportamentos inesperados.

---

## Vulnerabilidades de Segurança

Falhas de segurança podem permitir que pessoas não autorizadas explorem o sistema para acessar dados ou recursos.

---

## Atualizações Defeituosas

Uma atualização implementada de forma inadequada pode introduzir novos erros ou interromper funcionalidades que anteriormente funcionavam.

---

## Conflitos de Software

Programas diferentes podem entrar em conflito entre si, provocando instabilidade no sistema.

---

## Falhas de Hardware

Uma falha de hardware não é diretamente um defeito do software, mas pode afetar sua execução e provocar erros ou comportamentos inesperados.

---

# Prevenção e Mitigação de Falhas

Algumas práticas ajudam a reduzir a ocorrência e o impacto de falhas.

## Segurança

Manter ferramentas de segurança e antivírus atualizados ajuda na identificação de ameaças e softwares maliciosos.

## Atualizações

Aplicar atualizações regularmente permite corrigir vulnerabilidades e problemas já identificados.

## Testes Rigorosos

O software deve ser testado antes de sua disponibilização para identificar e corrigir erros.

**Testar antes = corrigir antes**

## Monitoramento

O acompanhamento constante do funcionamento do software ajuda a identificar padrões de erro e detectar problemas antes que provoquem interrupções maiores.

## Backup

Realizar **backups periódicos** permite recuperar informações importantes caso uma falha provoque perda de dados.