## 1. Largura de banda x latência

A **camada física** é responsável pela transmissão dos bits através de um meio físico, como:
- Cabos
- Fibra óptica
- Ondas de rádio

### Largura de banda:
Indica quanto dado pode ser transportado em **determinado tempo.**
Quanto maior a largura de banda, maior a quantidade de dados pode ser enviada.

### Latência:
É o **tempo que a informação leva para chegar ao destino.**
Uma conexão pode ter muita largura de banda e ainda assim possui uma latência enorme.

### Exemplo prático: Caminhão.

Ao colocar dezenas de petabytes em disco e transportar tudo fisicamente em um caminhão, consegue mover uma quantidade absurda de dados.
**Ou seja:** capacidade absurda de transferência total, mas péssima latência.
Mandar um único arquivo dessa forma seria inviável, pois ele demoraria horas ou dias para chegar.

Mas para transferir **quantidades gigantescas de dados**, transporte físico pode ser mais eficiente do que transmitir tudo pela Internet.

**Resumindo:** Largura de banda não é a mesma coisa que velocidade de resposta.

**muita largura de banda + muita latência**
ou
**pouca largura de banda + pouca latência**.

## 2. Limite físico da latência:

Nenhum sinal consegue se propagar mais rápido que a velocidade da luz. 
Nos meios usados em redes, o sinal normalmente se propaga mais devagar. Em fibras ópticas, a velocidade é na ordem de 200.000 km/s

Isso implica que existe um **atraso mínimo inevitável** causado simplesmente pela distância entre origem e destino.

**Consequência:**
Mesmo que os roteadores fosse instantâneos, não existissem fila e tivesse largura de banda absurda, a comunicação entre dois lugares distantes ainda demoraria algum tempo.

**Distância física impões um limite mínimo de latência.**

→ Por esse motivo, um servido fisicamente mais próximo tende a oferecer menor latência que um servidor do outro lado do mundo.

**Mesmo com hardware perfeito, parte da latência é inevitável porque o sinal leva tempo para percorrer a distância física.**

## 3. Limite físico de transmissão:

A quantidade máxima de dados que um canal consegue transmitir depende principalmente de dois fatores:

**1. Largura de banda:** quanto espaço o canal tem para transportar informação
**2. Ruído:** interferência que dificultam distinguir corretamente o sinal

Quanto maior a largura de banda e menor o ruído, maior tende a ser a capacidade de transmissão.

Quando o ruído aumenta, fica mais difícil diferenciar o sinal útil das interferências, o que limita a velocidade da comunicação.

**Resumo:** todo meio de transmissão possui um limite físico de capacidade. Não adianta aumentar indefinidamente a velocidade do equipamento se o próprio canal não suporta.

## 4. Atenuação do sinal

À medida que um sinal percorre um meio de transmissão, como um cabo de cobre, ele vai **perdendo potência.**

Essa perda é chamada de **atenuação.**

**Quanto maior a distância percorrida:**
- Mais fraco o sinal tende a ficar.
- Maior a influência de ruídos e interferências.
- Mais difícil pode ficar interpretar os dados corretamente.

Em cabos de cobre, parte da energia do sinal é dissipada em forma de **calor** e também existem outras perdas associadas ao próprio meio.

**Resumo:** quanto maior a distância, maior a atenuação e menor a qualidade do sinal recebido.

## 5. Meios de transmissão:

Cada meio físico possui características diferentes de **largura de banda, alcance, atenuação, imunidade a ruído e custo**.

**Par trançado (cobre):** barato e muito usado em redes locais, mas sofre mais com interferência e atenuação.
**Cabo coaxial:** possui melhor blindagem contra interferências e é usado em aplicações como TV a cabo e alguns acessos de banda larga.
**Fibra óptica:** oferece alta capacidade, longas distâncias e grande imunidade a interferências eletromagnéticas.
**Ar / comunicação sem fio:** utiliza ondas eletromagnéticas; permite mobilidade, mas sofre mais com obstáculos, interferências e condições do ambiente.

**Resumo:** não existe um meio “melhor em tudo”. A escolha depende de distância, velocidade, interferência, custo e aplicação.

## 6. Fibra óptica e reflexão total interna:

![[Pasted image 20260914185143.png]]

A fibra óptica transmite dados usando **pulsos de luz.**

**Composta por:**
- **núcleo:** por onde a luz se propaga;
- **casca/revestimento:** possui propriedades ópticas diferentes e ajuda a manter a luz confinada no núcleo.

A luz permanece dentro da fibra graças ao fenômeno da **reflexão total interna**, fazendo com que o sinal consiga percorrer grandes distâncias com poucas perdas.


**Vantagens da fibra óptica:**
- alta capacidade de transmissão;
- baixa atenuação;
- permite grandes distâncias;
- não sofre interferência eletromagnética.

**Resumo:** a fibra guia a luz pelo seu interior, permitindo transmitir muita informação por longas distâncias com perdas relativamente pequenas.

## 7. Frequência e propagação no ar

Em redes sem fio, a frequência utilizada influencia bastante o comportamento do sinal.

![[Pasted image 20260914185741.png]]
### Frequências mais baixas

**Tendem a:**
- alcançar distâncias maiores;
- atravessar paredes e obstáculos com mais facilidade;
- sofrer menos atenuação no ambiente.
Por outro lado, o espectro disponível costuma ser mais disputado, podendo existir mais **interferência e congestionamento**.

### Frequências mais altas
Podem oferecer **maior capacidade de transmissão**, mas normalmente:
- possuem menor alcance;
- atravessam obstáculos com mais dificuldade;
- são mais sensíveis a bloqueios e às condições do ambiente.
Isso fica bem evidente nas chamadas **ondas milimétricas (mmWave)**.

**Resumo:** frequências mais baixas favorecem alcance e cobertura; frequências mais altas podem favorecer capacidade, mas exigem condições melhores de propagação.

## 8. O problema do último quilômetro.

O **último quilômetro** é o trecho final da rede que liga a infraestrutura da operadora até o usuário.

**Exemplo:**

**Backbone de fibra → central da operadora → casa do usuário**

Mesmo que o backbone tenha capacidade enorme, o desempenho final pode ser limitado pelo trecho que chega até a residência.

**Motivo de por que ele vira um problema:**
Esse trecho pode usar tecnologias mais limitadas, como:
- cobre;
- cabo coaxial;
- redes antigas;
- conexões sem fio com baixa capacidade.
Então uma rede pode ter **100 Gbps no backbone**, mas o usuário receber muito menos porque o acesso final é o ponto mais fraco.

#### Por que não trocar tudo por fibra?
Porque o problema não é só técnico.
Levar fibra até todas as casas envolve:
- obras;
- passagem de cabos;
- postes ou dutos;
- custo de instalação;
- manutenção;
- escala enorme.

**Resumo:** a rede pode ser muito rápida no núcleo, mas o acesso final ao usuário pode limitar todo o desempenho.

## 9. Bufferbloat:

Roteadores e outros equipamentos usam **buffers** para guardar pacotes temporariamente quando o tráfego chega mais rápido do que pode ser enviado.
O problema aparece quando esses buffers são grandes demais.
Em vez de descartar pacotes rapidamente durante um congestionamento, o roteador começa a **acumular uma fila enorme**.

**Resultado:**
- os pacotes continuam chegando;
- ficam muito tempo esperando na fila;
- a latência sobe absurdamente;
- chamadas, jogos e navegação ficam lentos mesmo que a conexão ainda tenha boa velocidade.

**Por que descartar pacotes às vezes ajuda?**
Quando a rede começa a descartar alguns pacotes, protocolos como o **TCP** percebem o congestionamento e reduzem a taxa de envio.
Se o buffer simplesmente guardar tudo, o transmissor pode demorar mais para perceber que a rede está saturada.

**Resumo:** Mais memória de buffer não significa necessariamente melhor desempenho.

---

## 10. Resumo: Limites físicos da comunicação

Nenhum sistema de comunicação consegue fugir completamente das limitações impostas pela física.

**Os principais limites são:**
- **Velocidade da luz:** define o menor atraso possível entre dois pontos.
- **Atenuação:** o sinal perde intensidade conforme percorre o meio.
- **Ruído:** interfere no sinal e limita a quantidade de informação que pode ser transmitida com segurança.

**Existente soluções para reduzir esses problemas usando:**
- melhores meios de transmissão;
- codificação;
- compressão;
- amplificação e regeneração de sinais;
- protocolos mais eficientes.

**Resumo:** toda rede está limitada por distância, propriedades do meio e ruído.

