
#faculdade #eletronica_2 #resumos 

---
## Esquemático de um transistor NPN

![[Pasted image 20260314163813.png]]

**(a): Sentido convencional**
**(b): Sentido real**

### Correntes do transistor:
- Corrente no emissor ($I_e$)
- Corrente na base ($I_B$)
- Corrente no coletor ($I_c$)

### Características:

→ **Corrente no emissor ($I_E$):** O emissor é a fonte de elétrons principal. Ele possui a maior corrente.
→ **Corrente na base ($I_B$):** Possui um valor aproximadamente igual à corrente do emissor.
→ **Corrente no coletor ($I_c$):** Valor muito menor que a corrente do emissor / coletor.


## Relações:

**1- Lei de Kirchhoff:**
Usando a lei de Kirchhoff em um transistor, encontramos a seguinte relação:

### $$I_E=I_C+I_B$$

**Devido a corrente de base ser baixa, temos as seguintes relações:**

### $$I_C ≈ I_E$$
### $$I_B<<I_C$$


**2- Ganho Alfa corrente coletor (Menos usado)**
Representa a razão entre a corrente do coletor pela corrente do emissor. Como $I_C ≈ I_E$ o resultado de alfa é ligeiramente menor que 1.

### $$\alpha_{cc} = \frac{I_C}{I_E}$$
**3- Ganho Beta (Mais usado)**
Representa a razão entre a corrente do coletor pela corrente da base. Usado em amplificadores, essa expressão dita o quanto uma corrente baixa ($I_C$) consegue controlar uma corrente maior ($I_C$).

### $$\beta{cc}=\frac{I_C}{I_B}$$

OBS: **Não tem unidade de medida.**


## Relações definidas por ($\beta_{CC}$)

![[Pasted image 20260314170328.png]]

