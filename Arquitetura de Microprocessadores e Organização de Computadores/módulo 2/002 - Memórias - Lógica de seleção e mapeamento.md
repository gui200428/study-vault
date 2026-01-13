#faculdade #aom #resumos 
## Memória cache - parte 2

→ Memória pequena, rápida e volátil, localizada próximo ao processador, usada para armazenar temporariamente dados e instruções frequentemente acessados. **Objetivo:** reduzir o tempo de acesso à memória principal (RAM).

**Cache hit/miss:**
→ **Exemplo:** processador precisa acessar um valor de uma variável armazenada na RAM. Se o valor estiver na cache, temos um **cache hit**, o acesso será quase instantâneo. Se não estiver, temos um **cache miss**, o sistema precisa buscar na RAM, o que se torna mais lento.


## Princípios fundamentais da memória cache

### Localização de referência

**Localidade temporal:** Os dados que foram acessados recentemente, tem alta probabilidade de serem acessados novamente em breve. 

**Localidade espacial:** Os dados próximos aos que foram acessados recentemente também têm grande probabilidade de serem acessados.

### Mapeamento:

→ Define como os dados da memória principal são colocados na cache.

**Mapeamento direto (1:1):** cada bloco da memória principal é mapeado para uma única linha da cache.
**Mapeamento associativo:** qualquer bloco pode ser armazenado em qualquer linha da cache.
**Mapeamento associativo por conjunto:** a memória cache é dividida em conjuntos, cada bloco pode ir para qualquer linha dentro de um conjunto específico.

**Importante:** a memória principal RAM possui muito mais blocos do que a memória
cache, somente alguns blocos da memória principal estão presentes na cache em um dado momento. Quando uma palavra é acessada, seu bloco é carregado na cache.
**Tag identificador:** serve para identificar qual bloco da memória principal está armazenado em cada linha da cache.


### Política de substituição:
→ Ocorre quando a cache está cheia e um novo dado precisa ser carregado. É necessário substituir um bloco existente. Politica mais comuns de substituição:

**LRU (Least Recently Used):** substitui o bloco menos usado recentemente.
**FIFO (First in, First out):** substitui o bloco mais antigo.
**Random:** escolhe aleatoriamente um bloco para substituir.

### Política de escrita:
→ Define como os dados modificados na cache são atualizados na memória principal:

**Write-through:** toda escrita na cache é imediatamente refletida na memória principal.
**Write-back:** a escrita é feita somente na cache, a memória principal é atualizada posteriormente, quando o bloco for substituído.

### Tamanho e níveis:
→ São as dimensões das memórias cache:

**Cache L1:** muito rápida e pequena, integrada ao núcleo do processador. (32 - 64kb por núcleo).
**Cache L2:** maior que L1 e mais lenta. (256KB - 1MB por núcleo).
**Cache L3:** compartilhada entre os núcleos, maior que L2 e mais lenta. (2 - 32MB por núcleo).


## Operação de leitura da cache e organização:

**Processo:**

1. Processador gera o endereço de leitura (RA) de uma palavra a ser lida.
2. Verifica se a palavra esta na cache
3. **Se estiver:** a palavra é entregue ao processador.
4. **Se não estiver:** o bloco contendo essa palavra é carregado na cache e então a palavra é entregue ao processador.

![[Pasted image 20251102180802.png]]


**Estrutura:**

![[Pasted image 20251102180844.png]]

→ Cache se conecta ao processador por meio da linha de dados, controle e endereçamento.
→ As linhas de dados e endereços se conectam a buffers de dados e endereços, eles servem como forma de sincronizar as informações. Impedindo que nenhuma informação seja perdida ou trocada.
→ Os buffers se conectam ao barramento do sistema, do qual a memória principal é acessada.
→ Quando temos um hit na cache, os buffers de dados e endereço são desativados e a comunicação é apenas entre o processador e a cache. Sem trafego no barramento do sistema.


## Tamanho da cache:

→ Quanto maior a cache, maior o numero de portas de endereçamento. Isso resulta que caches maiores tendem a ser ligeiramente mais lentas que as menores. A área disponível do chip e da placa também são fatores limitantes para o tamanho da cache.

## Função de mapeamento:

→ **Motivação:** como a cache é muito menor que a memória principal, é necessário ter um algoritmo para mapear os blocos da memória principal nas linhas de cache. Também é preciso um meio para determinar qual bloco da memória principal atualmente ocupa uma linha da cache.
**Técnicas usadas para o mapeamento:**
- Direta
- Associativa
- Associativa por conjunto.

### Mapeamento direto:

→ Cada bloco da memória principal tem **uma única linha da cache** onde ele pode ser armazenado. A linha é determinada pela operação de **módulo**

**Dado pela fórmula:**

$$i=j \ mod(m)$$
**Sendo:**
i = número da linha da cache 
j = número do bloco da memória principal
m = número de linhas da cache

→ O número do bloco da memória principal (j) é dividido por m (número de linhas da cache), o resto da divisão indica a linha da cache onde o bloco será armazenado.

**Exemplo:**

cache tem m = 8 linhas (0 - 7)
bloco da memória principal j = 27

![[Pasted image 20251102182940.png]]

→ O bloco 27 é armazenado na linha 3 da cache.

#### Papel da tag na cache:

→ Vários blocos da memória principal podem ser mapeados para a mesma linha da cache.
→ Mas eles não podem estar na mesma linha ao mesmo tempo, um substitui o outro.

**Exemplo:**
→ Memória principal = 64 blocos (0 - 63)
→ Memória cache = 8 linhas (0 - 7)

![[Pasted image 20251102183503.png]]

→ **Importante:** a cache precisa saber **qual bloco está armazenado** em cada linha. Cada linha da cache possui uma **TAG** que guarda o número do bloco da memória principal.

**MUITO IMPORTANTE:** DOIS BLOCOS nunca podem ocupar a mesma linha da cache, a tabela é só uma representação do calculo do bloco para a memória.

Ex: o bloco 35 está na linha 3 da cache e a TAG da linha 3 será 35.


#### HIT / MISS

1. Calcula a linha da cache usando a formula i = j mod(m)
2. Verifica a **TAG** da linha da cache
3. Se a **TAG** corresponde ao bloco desejado, temos um **HIT** (acesso rápido)
4. Se a **TAG** não corresponde → **MISS**, é preciso buscar o bloco na memória principal e substituir o da cache.

#### Vantagens X Desvantagens - Mapeamento direto:

**Vantagens:**
1. Simples de implementar.
2. Rápido para calcular a linha da cache.

**Desvantagens:**
- Conflitos: dois blocos diferentes podem competir pela mesma linha.
- Pode causar **MISS** mesmo com dados frequentemente acessados

#### Teoria do conflito da cache:

![[Pasted image 20251106153057.png]]
**Para que serve a TAG então?** É o crachá do carro que está estacionado. Quando o processador olha para a Linha 0, ele lê a TAG para saber: _"Quem está parado aqui agora? É o 0, o 8 ou o 16?”

### Mapeamento associativo:

→ Qualquer bloco da memória principal pode ser armazenado em qualquer linha da cache. **Oferece flexibilidade máxima.** Diferente do mapeamento direto, onde cada bloco só pode ir para uma linha específica.

#### **Componentes principais da cache associativa:**

**Conjunto de linhas de cache:** cada linha pode armazenar qualquer bloco da memória principal.
**Tag:** identifica qual bloco da memória principal está armazenado
**Dado:** conteúdo do bloco
**Bit de validade (valid bit):** indica se a linha possui dados válidos.

**Exemplo de funcionamento:**
→ Memória principal: 16 blocos (0 - 15)
→ Cache com 4 linhas
→ Qualquer bloco (0 - 15) pode ser armazenado em **qualquer uma das 4 linhas da cache**

1. Processador quer acessar o bloco 5.
2. Verifica a cache **linha por linha** para ver se alguma linha tem a **TAG = 5 e valid bit = 1**
3. Se encontrar: **HIT**
4. Se não encontrar: **MISS**, o bloco 5 é carregado da memória principal para **uma linha livre da cache** (ou substitui outro bloco se a cache estiver cheia).

**Exemplo com tabela:**
![[Pasted image 20251102191918.png]]

→ Processador quer acessar o bloco 12
→ Verifica todas as TAGs
→ Linha 1: tag encontrada → **HIT**


**Substituição de blocos:**
→ Quando a cache está cheia e ocorre um **MISS**. Precisamos substituir um dos blocos.
**Politicas de substituição:**
1. **FIFO:** substitui o bloco mais antigo na cache.
2. **LRU (Least recently used):** substitui o bloco que foi usado há mais tempo (menos usado no momento).
3. **Random:** escolha uma linha aleatoriamente.

#### Definição do valid bit:

**1- Inicialização:**
- SO inicia, cache vazia
- Todos os valid bits são definidos como 0. (nenhum dado é confiável).

**2- Carregamento de um bloco:**
- Após um miss, o bloco da memória principal é carregado na cache.
- Bloco armazenado na cache
- Define o valid bit como 1. (dados são válidos e podem ser usados para o bloco).

**3- Verificação de validade:**
- Ao buscar o dado na cache, o sistema verifica: TAG e valid bit
- Somente se ambas as condições forem verdadeiras, ocorre um **cache hit**

**4- Substituição de bloco**
- Novo bloco carregado em uma linha do cache (por substituição): o valid bit da linha é redefinido para 1
- Linha invalida: valid bit pode ser zerado.

**Exemplo:**

![[Pasted image 20251102192711.png]]

Acessar o bloco 7:
→ TAG não encontrada → **MISS**
→ O bloco 7 será carregado em uma linha (possivelmente na linha 1, que está invalida), valid bit será atualizado para 1.

#### Vantagens X Desvantagens - Mapeamento associativo:

**Vantagens:**
→ Flexibilidade: qualquer bloco pode ir para qualquer linha.
→ Menos conflitos do que mapeamento direto.

**Desvantagens:**
→ Mais complexo: precisa de lógica para busca por **TAGs** e política de substituição.
→ Mais caro: requer comparadores e controle adicional.



### Mapeamento associativo por conjunto:


→ Técnica intermediária entre o **mapeamento direto** e o **mapeamento totalmente associativo**.

**Características:**
→ Cache dividida em **conjuntos.**
→ Cada conjunto possui **várias linhas (vias)**
→ Cada bloco da memória principal é mapeado para **um único conjunto,** mas **pode ocupar qualquer linha dentro desse conjunto.**

**Funcionamento:**
→ Memória principal: 64 blocos
→ Cache: 8 conjuntos, cada um com 2 vias (linhas) → 16 linhas
→ Cada conjunto pode armazenar **2 blocos**.

**Determinar o conjunto onde o bloco será mapeado:**

$$Conjunto= j mod(S)$$
Sendo:
j = número do bloco da memória principal
S = número de conjuntos na cache


**Buscar o bloco dentro das vias do conjunto:**
- Verificar se alguma linha do conjunto tem a **TAG** correspondente ao bloco.
- Se encontrar **HIT**
- Se não encontrar: **MISS** → o bloco é carregado em uma das vias do conjunto (usando uma política de substituição: FIFO / LRU)

**EXEMPLO PRATICO:**

![[Pasted image 20251102193810.png]]

**Ex 1:**
→ Processador que acessar o bloco 18
→ Número de conjuntos: 8

18 mod (8) = 2 → o bloco 18 será mapeado para o **conjunto 2**

→ Processador verifica as vias do conjunto 2, encontra a TAG 18 na via 1 → **HIT**

**Ex 2:**
→ Processador que acessar o bloco 26:

26 mod (8) = 2 → o bloco 26 será mapeado para o **conjunto 2**

→ Processador verifica as vias do conjunto 2, e não encontra a TAG 26 → **MISS**
→ Será necessário **substituir uma das duas vias.**


#### Vantagens X Desvantagens - Mapeamento associativo por conjunto

**Vantagens:**
- Reduz os conflitos em relação ao mapeamento direto.
- Mais eficiente que o mapeamento totalmente associativo em questão de custo e complexidade

**Desvantagens:**
- Mais complexo que o mapeamento direto
- Ainda existe a chance de conflitos dentro de um conjunto



## Exercícios 

**1) Um processador leva 1 ciclo para acessar a cache e 50 ciclos para
acessar a memória principal. Em um programa, 90% dos acessos
resultam em cache hit.**

**a) Qual é o tempo médio de acesso à memória?**

$$T = 0,9 * 1 + 0,1*50=5,9 \ ciclos$$
**b) Se a taxa de cache hit cair para 70%, qual será o novo tempo
médio?**

$$T=0,7*1 +0,3*50=15,7 \ ciclos$$
→ A queda na taxa de hit aumenta significativamente o tempo médio.


**2) Explique por que o mapeamento associativo é mais flexível que o
mapeamento direto, mas também mais caro. Em seguida, cite uma
situação em que o mapeamento associativo seria preferível.**


→ O mapeamento associativo é mais flexível pois ele tem a liberdade de definir um bloco da memória principal a qualquer linha da cache, sem restrições. O mapeamento associativo acaba sendo mais caro pois ele precisa de alguns sistemas adicionais para verificar **todas as tags** e a  política de substituição. O mapeamento associativo é preferível pois a chance de conflitos entre as linhas é bem menor comparado ao mapeamento direto, reduzindo o numero de MISS.

![[Pasted image 20251102195507.png]]


---
### Próximo conteúdo:

[[003 - Dispositivos IO - Conceitos e polling]]




