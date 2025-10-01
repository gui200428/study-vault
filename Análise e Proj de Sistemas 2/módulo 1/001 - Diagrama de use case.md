## Elementos:

![[Pasted image 20250930225401.png]]

## Como montar:


→ O diagrama deve mostrar o fluxo de operações com seus devidos relacionamentos
→ O agentes (autores) e suas relações, indicando que parte do sistema eles devem acessar
→ Diagrama de visão geral do projeto


#### 1- Começar com o sistema - Retângulo gigante
→ Tudo que acontecer dentro do aplicativo, deve ser representado dentro do retângulo

#### 2- Ator
→ Colocar a pessoa que vai interagir com o sistema
→ Objetos externos, devem ser colocados fora do sistema

**Tipos de atores:**
Ator primário: inicia a utilização do sistema (deve ir na esquerda do retangulo)
Ator secundário: reage as ações do ator primário (deve ir na direita do retangulo)


#### 3- Casos de uso
→ Forma oval que representa a ação
→ Deve começar com um verbo (Fazer / Consultar)
→ Seguir uma ordem lógica Ex Fazer login → consultar saldo

#### 4- Relacionamento

**Inclusão:**
→ Ligar um caso de uso que depende de outro
→ Seta pontilhada
→ Inevitável, vai acontecer!

![[Pasted image 20250930232122.png]]

**Extensão:**
→ Relacionamento que nem sempre vai ocorrer
→ Ex: Erro de login
→ Extensão do caso base
→ Pode acontecer

![[Pasted image 20250930232347.png]]

**Generalização:**
→ Casos que podem acontecer derivados do caso primário
→ Representado com seta continua voltado para o caso primário

![[Pasted image 20250930232604.png]]

### Fonte:

https://www.youtube.com/watch?v=ab6eDdwS3rA