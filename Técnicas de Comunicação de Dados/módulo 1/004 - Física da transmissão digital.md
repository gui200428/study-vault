
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


