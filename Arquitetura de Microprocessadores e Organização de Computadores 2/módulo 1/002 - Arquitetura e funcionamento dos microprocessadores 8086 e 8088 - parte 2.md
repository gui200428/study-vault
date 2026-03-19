
## Diagrama funcional:

![[Pasted image 20260319175337.png]]

## BIU - (Bus Interface Unit) - “Lado externo da CPU”

**Funções principais:**

1. **Busca de instruções (Fetch):** 
- Lê bytes de instrução da memória usando o CS:IP (Code segment + instruction pointer).
- Armazena os bytes na fila de pré-busca (Instruction queue) de 6 bytes.

2. **Formação de endereços físicos:**
- Converte endereços lógicos segmento:
- Deslocamento em endereço físico: Endereço Físico=Segmento×16 + Desloca
mento
- Usa os registradores de segmento: CS, DS, SS e ES.

3. **Controle de barramento e temporização:**
- Gera sinais para memória e E/S (Ciclos de leitura/ escrita).
- Coordena o acesso ao barramento (Endereços, dados e controle.)

4. **Leituras/escritas de dados:**
- Executa os acessos de dados solicitados pela EU (por exemplo, ler um operando na memoria apontado por DS ou SS.).


**Eventos especiais:**

- Desvios, chamadas, interrupções e mudanças de segmento → esvaziam a fila de pré-busca (flush). A BIU então reinicia a busca a partir do novo CS:IP.
 
- Se a EU consumir a fila mais rápido do que a BIU consegue encher (por exemplo, muitas instruções curtas), ocorre bolha/espera por fetch.


(5 - aula 2).