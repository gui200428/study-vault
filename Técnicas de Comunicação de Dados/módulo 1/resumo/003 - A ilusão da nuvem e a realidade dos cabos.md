# A ilusão da nuvem e a realidade dos cabos

## Largura de banda e latência

**Capacidade/largura de banda** indica quanto dado pode ser transportado; **latência** é o tempo até o dado chegar. Uma não garante a outra.

O exemplo do **Amazon Snowmobile** usa uma caminhonete cheia de HDs: capacidade de **100 PB** e largura de banda equivalente a **mais de 70 Gbps sustentados**. Em volume, é excelente. Mas o trânsito leva **dias**, o slide fala em **milhares de horas**, enquanto uma comunicação interativa exige **milissegundos**. Por isso, transportar muitos dados fisicamente pode ser eficiente sem servir para respostas rápidas.

![[Pasted image 20260927213501.png]]

## Limite físico da propagação

Nenhum bit se propaga mais rápido que a luz. No **vácuo**, o material usa **300.000 km/s**; em **fibra de vidro e cobre**, cerca de **200.000 km/s** (redução de um terço). A interação com o material reduz a velocidade de propagação. Mesmo com equipamentos melhores, a distância entre **São Paulo e Nova Iorque** impede que o **ping** seja zero.

**Complemento de cálculo:** para estimar só o atraso de propagação, use

$$
d_{prop}=\frac{d}{s}
$$

onde $d$ é a distância e $s$ a velocidade de propagação. Em **1.000 km** de fibra, com $s \approx 2\times10^8$ m/s, o sinal leva aproximadamente **5 ms apenas na ida**. Isso é um piso físico, antes dos outros atrasos da rede.

**Exemplo adicional (fora do PDF):** tomando cerca de **7.700 km** entre São Paulo e Nova Iorque e a mesma velocidade na fibra, $d_{prop}\approx 38{,}5$ ms **na ida**. O mínimo teórico de ida e volta seria, portanto, **~77 ms** de propagação. O ping real costuma ser maior porque o percurso efetivo e os demais atrasos da rede se somam a esse piso.

## Limite de taxa pela largura de banda e pelo ruído

O slide apresenta a regra de Shannon para a **taxa máxima** de dados no canal:

$$
\text{Taxa máxima}=B\log_2(1+S/N)
$$

- **Taxa máxima:** capacidade de dados do canal, em **bits/s**.
- $B$: largura da faixa de frequências do canal, em **Hz**.
- $S/N$: razão entre potência do sinal e potência do ruído, em escala **linear**.

**Exemplo ADSL da aula:** linha telefônica com $B=1$ MHz e SNR de **40 dB**. O slide apresenta um limite de aproximadamente **13 Mbps**.

Para elevar esse limite, é preciso ampliar $B$ ou melhorar a relação sinal/ruído. Aqui **largura de banda** é medida em **Hz**; nos exemplos de transporte, o termo também aparece para a **taxa em bits/s**.

### Complemento de cálculo

Para usar na fórmula o SNR em escala linear, a conversão de dB é $\mathrm{SNR}_{dB}=10\log_{10}(S/N)$. Assim, $S/N=10^{40/10}=10^4$ e:

$$
\text{Taxa máxima}=10^6\log_2(1+10^4)\approx 13{,}29\times10^6\ \text{bits/s}=13{,}29\ \text{Mbps}
$$

Obs: o título do slide fala em “velocidade”, mas a fórmula e o exemplo calculam a **taxa máxima de dados**, não a velocidade de propagação do sinal.

### Complemento: Shannon e Nyquist (fora do PDF)

A fórmula de **Shannon** acima considera o **ruído**. Para um canal **ideal sem ruído**, o limite de **Nyquist** é:

$$
\text{Taxa máxima}=2B\log_2 V
$$

Aqui $B$ é a largura de banda em **Hz** e $V$ é o número de níveis distintos de sinal. O material 003 não apresenta Nyquist; esta comparação serve para distinguir as hipóteses das duas fórmulas.

## Atenuação no cobre

**Atenuação** é a perda de energia do sinal ao percorrer o meio. No cobre, parte da energia elétrica se dissipa como calor; interferências externas também prejudicam a recepção. A distância torna o sinal mais fraco e reduz a taxa que a linha consegue sustentar.

No gráfico da **central telefônica**, o eixo horizontal é a **distância em km** e o vertical é a **largura de banda potencial/velocidade em Mbps**. O sinal começa no máximo no **km 0**, passa por uma **zona verde** de boa recepção e ruído administrável em **1–2 km**, e o desenho marca o **fim do sinal no km 5**.

![[Pasted image 20260927213502.png]]

## Meios de transmissão

| Meio | Espectro/banda apresentado | Ruído ou atenuação | Aplicações da aula |
| --- | --- | --- | --- |
| **Par trançado (cobre)** | Estreito: cerca de **1 MHz a centenas de MHz**. | Muito suscetível a interferências; pode funcionar como “antena acidental”. | Telefonia, ADSL, LAN local. |
| **Cabo coaxial** | Médio: até **6 GHz**. | Blindagem contra micro-ondas e motores. | TV a cabo, banda larga residencial compartilhada. |
| **Fibra óptica** | Colossal: **25.000 a 30.000 GHz**. | O slide a descreve como virtualmente imune a ruído, pela luz confinada. | Backbones globais de dados. |
| **Ar (espectro eletromagnético)** | Compartilhado e altamente regulado. | Obstáculos e clima, como chuva e paredes, absorvem o sinal. | Wi-Fi, 5G, satélite. |

### Reflexão total interna na fibra

A luz fica confinada no interior da fibra por **reflexão total interna**. O material associa isso à grande capacidade e à eficiência energética: cita **~25.000 GHz** como largura teórica de uma única banda de fibra e **100 km** percorridos pelos fótons antes de precisarem de **“amplificação mecânica”**, expressão usada no slide. O cobre, na comparação apresentada, perderia o sinal nos primeiros quilômetros.

![[Pasted image 20260927213503.png]]

**Complemento sobre a fibra (fora do PDF):** para ocorrer reflexão total interna, o **índice de refração do núcleo deve ser maior que o da casca**, e a luz deve atingir a interface acima do ângulo crítico. A fibra **monomodo** conduz um modo de propagação; a **multimodo**, vários. Os **~25.000 GHz** citados são uma largura de banda **teórica**, não uma taxa de dados diretamente disponível: na prática, a multiplexação por comprimentos de onda (**WDM**) e os limites dos equipamentos ópticos e eletrônicos condicionam a capacidade utilizável.

### Frequência e propagação no ar

- **Sub-5 GHz** (Wi-Fi antigo, 4G): atravessa barreiras com mais facilidade, mas o espectro está congestionado.
- **Frequências milimétricas** (exemplo de **60 GHz**, 5G avançado): oferecem banda muito grande, citada para **4K/8K descompactado**, mas sofrem com portas, paredes e tempestades.

O contraste da aula é entre **penetração com espectro disputado** e **alta capacidade com maior sensibilidade a obstáculos**.

## Gargalo do “último quilômetro”

O **backbone** do exemplo tem capacidade abundante de **100 Gbps ou mais**, mas a central/nó óptico precisa distribuir essa capacidade aos usuários por trechos finais de **DSL, coaxial e cobre**. Esses acessos criam o **gargalo físico**: a capacidade no núcleo não elimina a limitação do caminho até a residência.

Trocar o backbone é viável, mas levar fibra a cada casa exige escavar ruas e jardins. O material apresenta o último quilômetro como barreira **econômica**, além de tecnológica.

![[Pasted image 20260927213504.png]]

## Bufferbloat: congestionamento escondido na fila

**Cenário A - ideal no slide:** pacotes excedentes são descartados cedo. A rede percebe a perda, reduz o envio **imediatamente** e mantém a fluidez.

**Cenário B - bufferbloat:** aumentar a memória do roteador não acelera o enlace físico. O buffer acumula pacotes, esconde o congestionamento, faz pacotes vencerem na fila e leva as máquinas a enviar cópias redundantes. É o **colapso por acúmulo**.

![[Pasted image 20260927213505.png]]

## Limites que permanecem

- **Velocidade da luz:** define o atraso mínimo de propagação.
- **Atenuação do material:** desgasta a energia do sinal ao longo do caminho.
- **Lei de Shannon:** limita a taxa de dados diante do ruído.

O slide chama de **“sweet spot da engenharia”** o ponto de equilíbrio entre esses três limites.

Mesmo que a engenharia **fatie, comprima e codifique** os dados, a comunicação continua submetida à distância, às propriedades do meio e ao ruído.
