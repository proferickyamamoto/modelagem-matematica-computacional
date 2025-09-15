# Aula 15.2 – Sistemas Lineares: Eliminação, RREF e Classificação

## 🎯 Objetivos

* Representar sistemas lineares na forma matricial $A\,x=b$ e na matriz aumentada $[A\,|\,b]$.
* Resolver por **Eliminação Gaussiana** (com pivotamento) e **Gauss–Jordan** (RREF).
* **Classificar** sistemas: solução única, infinitas soluções e incompatível (sem solução) via **posto** (rank) e **Teorema de Rouché–Capelli**.
* Escrever **soluções paramétricas** quando houver variáveis livres.
* (Opcional) Comparar com **Cramer** (2×2/3×3) e **LU**.

---

## 📘 Fundamentos Rápidos

* **Forma matricial:** $A\in\mathbb{R}^{m\times n}$, $x\in\mathbb{R}^n$, $b\in\mathbb{R}^m$.
* **Operações elementares de linha (OEL):** trocas, múltiplos, soma de múltiplos – **preservam** o conjunto de soluções.
* **REF** (forma escalonada) e **RREF** (reduzida): pivôs = primeiras entradas não nulas de cada linha; em RREF os pivôs são 1 e são os únicos não nulos nas suas colunas.
**Teorema de Rouché–Capelli**

Defina r = rank(A) e r' = rank([A|b]).

  * Se r < r' → incompatível (sem solução).
  * Se r = r' = n → solução única.
  * Se r = r' < n → infinitas soluções (n − r variáveis livres).

---

## 🧰 Algoritmos de Resolução

### 1) Eliminação Gaussiana (com pivotamento parcial)

1. Para k=1..min(m,n)−1:

   * Escolha pivô com maior |coef.| na coluna k (linhas k..m) e troque linhas.
   * Zere abaixo do pivô: $L_i \leftarrow L_i - m_{ik} L_k$, com $m_{ik}=a_{ik}/a_{kk}$.
2. Obtenha **U** (triangular superior) e vetor $\tilde b$. Faça **retrossubstituição**.

### 2) Gauss–Jordan (RREF)

* Prossiga a eliminação **acima** dos pivôs e normalize cada pivô para 1 → obtém **RREF** e lê-se a solução diretamente.

### 3) Cramer (2×2/3×3) – opcional

* Se $\det(A)\neq 0$, $x_i = \det(A_i)/\det(A)$. **Só** para sistemas pequenos; não escalável.

---

## 🧮 Exemplo A — Solução Única (3×3)

$$
\begin{cases}
2x + y - z = 8\\
-3x - y + 2z = -11\\
-2x + y + 2z = -3
\end{cases}
\quad\Rightarrow\quad
[A|b]=\begin{bmatrix}
2&1&-1&|&8\\
-3&-1&2&|&-11\\
-2&1&2&|&-3
\end{bmatrix}
$$

**k=1 (pivotamento):** pivô = −3 (L2) → L1↔L2.

Anule abaixo:

• L2 ← L2 − (2/−3)L1 = L2 + (2/3)L1  ⇒  [0, 1/3, 1/3 | 10/3]
• L3 ← L3 − (−2/−3)L1 = L3 − (2/3)L1 ⇒  [0, 5/3, 2/3 | −1/3]

k = 2 (pivotamento na coluna 2): pivô = 5/3 (L3) ⇒ L2 ↔ L3; anule L3 com m = (1/3)/(5/3) = 1/5:
• L3 ← L3 − (1/5)L2  ⇒  [0, 0, 4/15 | 17/5]

Retrossubstituição:
• x3 = (17/5) / (4/15) = (17/5) × (15/4) = 51/4 = 12,75
• Substituindo: x2 = 3,  x1 = 2

Solução: (x1, x2, x3) = (2, 3, −1).

> Nota: frações intermediárias podem variar, mas a solução é única porque det(A) ≠ 0 (posto 3).

---

## 🧮 Exemplo B — Infinitas Soluções (subdeterminado)
\[
\begin{cases}
 x + 2y + z = 1\\
 2x + 4y + 2z = 2\\
 -x - 2y - z = -1
\end{cases}
$$

Observe que L2 = 2·L1 e L3 = −L1 ⇒ **posto** $r=1$ (somente uma equação independente). Como $[A|b]$ tem o mesmo posto $r'=1$ e $n=3$, há **infinitas soluções** com **2 variáveis livres**.

Escolha $y=s$, $z=t$. Da 1ª equação: $x = 1 - 2s - t$.
**Solução paramétrica:** $\boxed{(x,y,z)=(1-2s-t,\ s,\ t)},\ s,t\in\mathbb{R}.$

---

## 🧮 Exemplo C — Sistema Incompatível

$$
\begin{cases}
 x + y = 1\\
 2x + 2y = 3
\end{cases}
\quad\Rightarrow\quad
[A|b]\to\begin{bmatrix}
1&1&|&1\\
0&0&|&1
\end{bmatrix}
$$

Linha $[0\,0\,|\,1]$ ⇒ **contradição** ⇒ **sem solução**.
Pelos postos: $r=1$, $r'=2$ ⇒ $r<r'$ (Rouché–Capelli).

---

## ✍️ Como escrever solução paramétrica

1. Traga o sistema para **RREF**.
2. Identifique **colunas com pivô** (variáveis básicas) e **sem pivô** (variáveis livres).
3. Dê parâmetros ($s,t,\dots$) às livres e **expresse as básicas** em função deles.

---

## ⚠️ Erros Comuns

* Esquecer pivotamento quando o pivô é pequeno/zero → divisões instáveis.
* Trocar sinal ao aplicar OEL.
* Não checar **consistência** (linha do tipo $[0\;0\;\cdots|c]$, $c\ne 0$).
* Confundir **posto** com número de variáveis (lembre: $\#\text{livres}=n-r$).

---

## 🏫 Exercícios em Sala

1. Resolva por **Eliminação Gaussiana**:
   $\begin{cases} 3x+2y-z=1\\ 2x-2y+4z=-2\\ -x+\tfrac12 y - z = 0 \end{cases}$
2. Classifique e resolva (paramétrico, se aplicável):
   $\begin{cases} x+2y+z=0\\ 2x+4y+2z=0\\ -x-2y-z=0 \end{cases}$
3. Dado $A=\begin{bmatrix}1&2&1\\0&1&1\\2&1&0\end{bmatrix}$, encontre **posto(A)**, e resolva $A\,x=b$ para $b=(1,2,3)^T$ (diga se é única, infinita ou incompatível).
4. (RREF) Leve $[A|b]$ à forma reduzida e escreva a solução paramétrica.

---

## 🏠 Tarefa (Lista de 10)

1. Elimine e resolva: $\begin{cases} x+2y- z=4\\ 2x+5y+z=12\\ -x+y+2z=1 \end{cases}$.
2. Classifique por posto: $\begin{cases} x+y+z=1\\ 2x+2y+2z=2\\ x+y+z=0 \end{cases}$.
3. Dê um exemplo 3×3 **incompatível** e mostre a linha contraditória.
4. Escreva a solução geral de $x+2y+3z=0,\ 2x+4y+6z=0$.
5. Use **Cramer** para um sistema 2×2 de sua escolha ($\det\neq 0$) e compare com eliminação.
6. Mostre que o número de variáveis livres é $n-r$ no seu exercício 4.
7. Verifique por multiplicação que sua solução do exercício 1 satisfaz $A\,x=b$.
8. Monte $[A|b]$ e leve à **RREF** para o exercício 2.
9. Explique, em 4 linhas, por que pivotamento melhora a estabilidade.
10. (Desafio) Construa um 4×4 com **posto 2** e descreva o conjunto solução.

---

## 🔎 (Opcional) Verificação computacional

### Octave/Matlab

```octave
A = [3 2 -1; 2 -2 4; -1 0.5 -1];
b = [1; -2; 0];
% resolução estável (não use inv)
x = A\b
rref_form = rref([A b])  % requer pacote da sua instalação
```

### Python (NumPy)

```python
import numpy as np
A = np.array([[3,2,-1],[2,-2,4],[-1,0.5,-1]], float)
b = np.array([1,-2,0.])
print(np.linalg.solve(A,b))
```
**✅ Resultado esperado:** saber levar $[A|b]$ a REF/RREF, classificar por posto e escrever soluções (única, paramétrica ou inexistente), com cuidado às OEL e ao pivotamento.
