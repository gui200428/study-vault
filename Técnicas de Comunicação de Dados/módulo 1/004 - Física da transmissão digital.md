
## 1. Conversão do bit para o sinal transmissível

Computadores trabalham com informação digital, representada por **bits 0 e 1**.
Esses bits podem ser representados eletricamente por diferentes níveis de tensão, formando um **sinal digital em banda-base**.

**Problema:**
Transmitir informação por certos meios, principalmente **pelo ar**, não basta simplesmente jogar esses níveis de tensão numa antena. É necessário transformar os dados em um sinal adequada ao meio de transmissão.

**Modulação:**
Para comunicação sem fio, utiliza-se uma **onda portadora**, normalmente senoidal, cuja característica é modificada de acordo com os bits que queremos transmitir.

**Sendo possível mudar:**
- **amplitude**;
- **frequência**;
- **fase**.

**Modulação:** representar os bits através de alterações em uma onda portadora adequada para transmissão.

## 2. FFT — Transformada Rápida de Fourier

A **FFT (Fast Fourier Transform)** é uma técnica usada para analisar **quais frequências existem dentro de um sinal**.
Ela pega um sinal representado no **domínio do tempo** e mostra esse mesmo sinal no **domínio da frequência**.

### Domínio do tempo:
Mostra como o sinal varia ao longo do tempo.
**Exemplo:**
- sobe;
- desce;
- oscila;
- muda de amplitude.

### Domínio da frequência
Mostra **quais frequências compõem aquele sinal** e quanto cada uma contribui.

**A FFT não muda o sinal físico. Ela muda a forma como analisamos o sinal.**
Ela funciona como uma ferramenta para “separar” as componentes de frequência presentes em uma onda.

**Permite visualizar coisas como:**
- frequência da portadora;
- largura de banda ocupada;
- presença de ruído;
- distribuição da energia do sinal.


## 3. Sinal em banda-base

No **NRZ (Non-Return-to-Zero)**, os bits são representados diretamente por níveis de tensão.

**Exemplo:**
- bit **1** → nível alto;
- bit **0** → nível baixo.

Esse sinal ainda não está “carregado” em uma onda senoidal. Ele é um sinal digital direto, por isso é chamado de **banda-base**.

![[Pasted image 20260915023559.png]]

**FFT:**

Quando o sinal é analisado no domínio da frequência, a maior parte da energia fica concentrada nas frequência mais baixas, próximas de 0Hz.

Isso acontece porque o sinal varia relativamente devagar e possui uma componente contínua importante.

**Ideia central:** Sinais em banda-base ocupam principalmente baixas frequências e não utilizam uma portadora de alta frequência.

Para transmissão sem fio, normalmente é necessário modulação (pegar a informação de baixa frequência e deslocá-la para uma faixa adequada à transmissão por antena.)


## 3. Por que não transmitir NRZ diretamente pelo ar?

O sinal **NRZ em banda-base** concentra muita energia em frequências muito baixas.

Para transmitir eficientemente uma onda pelo ar, a antena precisa ter dimensões relacionadas ao **comprimento de onda** do sinal.

**Quanto menor a frequência:**
- maior o comprimento de onda;
- maior teria que ser a antena.
Por esse motivo, sinais próximos de **0 Hz** são impraticáveis para comunicação por rádio.

**Solução:** Modulação:
É usado uma **onda portadora de frequência muito mais alta**,  onda é modificada de acordo com os bits.

**Resumo:** o NRZ funciona bem em conexões físicas e circuitos eletrônicos, mas para transmissão sem fio é necessário deslocar a informação para frequências adequadas ao uso de antenas.

![[Pasted image 20260915024022.png]]


## 4. Modulação: ASK e BPSK

A **modulação** pega os bits da informação e usa esses bits para alterar uma **onda portadora** de alta frequência. Essa portadora é uma onda senoidal que consegue ser transmitida pelo meio.

### ASK - Amplitude Shift Keying
No **ASK**, a informação é representada por mudanças na **amplitude** da portadora.

**Exemplo:**
- bit **1** → portadora presente / amplitude alta;
- bit **0** → portadora ausente ou com amplitude menor.

### BPSK — Binary Phase Shift Keying
No **BPSK**, a amplitude continua praticamente igual, mas a informação é representada por mudanças na **fase** da onda.

**Basicamente:**
- um bit usa uma fase;
- o outro bit usa a fase invertida em **180°**.

**BPSK = muda a fase.**

### RESUMINDO:
A informação digital continua sendo a mesma, mas agora ela está **representada em uma onda adequada para transmissão**.

**Bits + portadora → sinal modulado**

**ASK → altera amplitude**  
**BPSK → altera fase**

![[Pasted image 20260915024526.png]]


## 5. Efeito da modulação no espectro

Antes da modulação, o sinal NRZ fica concentrado em **baixas frequências**, próximo de 0 Hz.
Depois da modulação, esse conteúdo é deslocado para a região da **frequência da portadora**.

![[Pasted image 20260915025313.png]]

**NRZ em banda-base → energia próxima de 0 Hz**
**Sinal modulado em 100 MHz → energia concentrada ao redor de 100 MHz**

Isso permite usar frequências adequadas para transmissão por antenas.

**Resumindo:** a modulação desloca o sinal de banda-base para uma faixa de frequência mais alta e adequada ao meio de transmissão.

## 6. Taxa de bits e largura de banda
Aumentar a **taxa de bits** significa transmitir mais bits no mesmo intervalo de tempo.
Na prática, isso faz o sinal mudar mais rapidamente entre seus níveis.

![[Pasted image 20260915025825.png]]

- **baixa taxa de bits:** pulsos mais largos e lentos;
- **alta taxa de bits:** pulsos mais curtos e mudanças mais rápidas.

Essas mudanças rápidas exigem componentes de frequência mais altas.
**Quanto maior a taxa de bits, maior tende a ser a largura de banda necessária.**

### Relação entre duração do pulso e espectro
Existe uma relação inversa entre o tempo de duração de um pulso e a largura de seu espectro em frequência.
- **Pulsos mais longos no tempo** → espectro mais estreito.
- **Pulsos mais curtos no tempo** → espectro mais largo.
Isso acontece porque mudanças muito rápidas no sinal exigem a presença de componentes de frequência mais altas.

![[Pasted image 20260915030257.png]]

### Aplicando à transmissão de dados

Quando a conexão transmite poucos bits por segundo, os pulsos podem ser mais longos.
Quando a taxa de bits aumenta, cada bit precisa ocupar menos tempo, então os pulsos ficam mais curtos.

**Maior taxa de bits → pulsos mais curtos → maior largura de banda necessária.**

### Analogia da mangueira

Podemos imaginar que:
- a **largura de banda** é como a largura da mangueira;
- os **dados** são como a água passando por ela.
Se a taxa de transmissão é baixa, uma “mangueira estreita” pode dar conta.

Quando tentamos transmitir muitos bits por segundo, precisamos de uma faixa de frequências maior, ou seja, de mais **largura de banda**.
**Quanto maior a taxa de bits, maior tende a ser a largura de banda necessária.**

### Quando a taxa aumenta demais

Se tentamos transmitir muitos bits em pouco tempo, o sinal precisa mudar muito rapidamente.
Essas mudanças rápidas exigem uma faixa maior de frequências.

Se o canal não tiver largura de banda suficiente:
- o sinal pode se deformar;
- os pulsos podem se sobrepor;
- aumenta a chance de erro na recepção.
**Alta taxa de bits exige maior largura de banda para preservar corretamente o sinal.**

---

## Resumo da transmissão digital

### 1. Limite da banda-base

Sinais digitais em **banda-base**, como o NRZ, concentram energia em frequências baixas.

Eles funcionam bem em meios físicos, mas não são adequados para transmissão direta pelo ar em sistemas de rádio.

> **Banda-base = sinal bruto, sem portadora.**

### 2. Modulação

A **modulação** usa uma onda portadora de frequência mais alta para transportar a informação.

Exemplos:

- **ASK:** altera a amplitude;
- **BPSK:** altera a fase.

> **Modulação = adaptar o sinal para uma faixa de frequência adequada à transmissão.**

### 3. Taxa de bits x largura de banda

Quanto maior a taxa de bits, mais rápidas são as mudanças no sinal.

Mudanças mais rápidas exigem uma faixa maior de frequências.

> **Maior taxa de bits → maior largura de banda necessária.**

### Resumo final

**Bits → banda-base → modulação → transmissão**

> **Para transmitir dados mais rápido e por meios como o ar, precisamos representar os bits em frequências adequadas e ocupar mais largura de banda.**

