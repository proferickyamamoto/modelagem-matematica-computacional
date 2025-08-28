# Aula 15.2 – Sistemas Lineares e Eliminação Gaussiana

---

## 🎯 Objetivos

* Entender a formulação de **sistemas lineares** na forma matricial $A x = b$.
* Aplicar **operações elementares de linha** e a **Eliminação Gaussiana** com pivotamento parcial.
* Classificar sistemas: solução **única**, **infinitas** soluções ou **incompatível**.
* Resolver sistemas via **retrossubstituição** e interpretar resultados com **posto (rank)** e **escalonamento**.
* Implementar o método em **Octave/Matlab**, **Python (NumPy)** e **R**.

---

## 📘 Fundamentos

### Forma matricial e matriz aumentada

Dado $A\in\mathbb{R}^{n\times n}$ (ou $m\times n$), $x\in\mathbb{R}^n$ e $b\in\mathbb{R}^m$:
$A x = b$
Matriz **aumentada**: $[A\,|\,b]$.

### Operações elementares (preservam o conjunto de soluções)

1. Troca de duas linhas.
2. Multiplicação de uma linha por escalar não nulo.
3. Soma de múltiplo de uma linha a outra.

### Escalonamento e classificação

* **Forma escalonada (REF)** e **reduzida (RREF)**.
* Critério com **posto**:

  * Se $\operatorname{posto}(A)=\operatorname{posto}([A|b])=n$ → **solução única**.
  * Se $\operatorname{posto}(A)=\operatorname{posto}([A|b])<n$ → **infinitas soluções** (parâmetros livres).
  * Se $\operatorname{posto}(A)<\operatorname{posto}([A|b])$ → **incompatível**.

---

## 🧰 Eliminação Gaussiana (com pivotamento parcial)

Para $k=1,\dots,\min(m,n)-1$:

1. **Pivoteamento:** escolha $p\in\{k,\dots,m\}$ que maximize $|a_{pk}|$; troque L$k$↔L$p$.
2. **Anulação abaixo do pivô:** para $i=k+1,\dots,m$, defina $m_{ik}=a_{ik}/a_{kk}$ e faça
   $\text{L}_i \leftarrow \text{L}_i - m_{ik}\,\text{L}_k$.
   Ao final, obtenha matriz **triangular superior** $U$ (ou **REF**) e vetor $\tilde b$. Resolva $U x = \tilde b$ por **retrossubstituição**.

> **Observações numéricas**: Pivotamento reduz erros quando o pivô é pequeno; evita divisão por valores próximos de zero e melhora a estabilidade.

---

## 🧮 Exemplo completo (3×3)

$$
A=\begin{bmatrix}2&1&-1\\-3&-1&2\\-2&1&2\end{bmatrix},\quad b=\begin{bmatrix}8\\-11\\-3\end{bmatrix},\quad [A|b]=\begin{bmatrix}2&1&-1&|&8\\-3&-1&2&|&-11\\-2&1&2&|&-3\end{bmatrix}.
$$

**k=1 (pivoteamento):** maior |coef.| na coluna 1 é 3 (linha 2) ⇒ troque L1↔L2.

$$
\begin{bmatrix}-3&-1&2&|&-11\\2&1&-1&|&8\\-2&1&2&|&-3\end{bmatrix}
$$

Anule abaixo do pivô:

* L2 ← L2 − (2/−3)L1 = L2 + (2/3)L1 ⇒ $[0,\,1/3,\,1/3\,|\,10/3]$
* L3 ← L3 − (−2/−3)L1 = L3 − (2/3)L1 ⇒ $[0,\,5/3,\,2/3\,|\,−1/3]$

**k=2 (pivoteamento na coluna 2):** maior |coef.| é $5/3$ (linha 3) ⇒ troque L2↔L3.
Anule L3 com fator $m=(1/3)/(5/3)=1/5$:

* L3 ← L3 − (1/5)L2 ⇒ $[0,\,0,\,4/15\,|\,17/5]$.

**Retrossubstituição**:

* $x_3 = (17/5)/(4/15) = 51/4 = 12{,}75$
* Substitua em L2 e L1 ⇒ **solução** $x = (2,\,3,\,-1)^T$.

> *Nota:* As frações intermediárias dependem das permutas; a solução final é única quando $\det(A)\neq 0$.

---

## 💻 Código (implementações educacionais)

### Octave/Matlab

```octave
function x = gauss_pivot(A, b)
  A = [A b(:)];
  [m, n] = size(A); % n = cols = m+1 para quadrada
  n = n - 1;
  for k = 1:n-1
    [~, p] = max(abs(A(k:end, k))); p = p + k - 1;
    A([k p], :) = A([p k], :);
    for i = k+1:m
      m_ik = A(i,k)/A(k,k);
      A(i, k:end) = A(i, k:end) - m_ik * A(k, k:end);
    end
  end
  x = zeros(n,1);
  for i = n:-1:1
    x(i) = (A(i,end) - A(i,i+1:n)*x(i+1:n)) / A(i,i);
  end
end

A = [2 1 -1; -3 -1 2; -2 1 2];
b = [8; -11; -3];
sol = gauss_pivot(A,b)
```

### Python (NumPy)

```python
import numpy as np

def gauss_pivot(A, b):
    A = A.astype(float)
    b = b.astype(float)
    m, n = A.shape
    M = np.hstack([A, b.reshape(-1,1)])
    for k in range(min(m,n)-1):
        p = k + np.argmax(np.abs(M[k:, k]))
        M[[k, p]] = M[[p, k]]
        for i in range(k+1, m):
            m_ik = M[i, k] / M[k, k]
            M[i, k:] -= m_ik * M[k, k:]
    x = np.zeros(n)
    for i in range(n-1, -1, -1):
        x[i] = (M[i, -1] - M[i, i+1:n] @ x[i+1:n]) / M[i, i]
    return x

A = np.array([[2.,1.,-1.],
              [-3.,-1., 2.],
              [-2., 1., 2.]])
b = np.array([8., -11., -3.])
print(gauss_pivot(A,b))  # [ 2.  3. -1.]
```

### R

```r
gauss_pivot <- function(A, b){
  A <- as.matrix(A); b <- as.numeric(b)
  m <- nrow(A); n <- ncol(A)
  M <- cbind(A, b)
  for(k in 1:(min(m,n)-1)){
    p <- k-1 + which.max(abs(M[k:m, k]))
    tmp <- M[k,]; M[k,] <- M[p,]; M[p,] <- tmp
    for(i in (k+1):m){
      m_ik <- M[i,k]/M[k,k]
      M[i, k:ncol(M)] <- M[i, k:ncol(M)] - m_ik * M[k, k:ncol(M)]
    }
  }
  x <- numeric(n)
  for(i in n:1){
    x[i] <- (M[i,n+1] - sum(M[i,(i+1):n] * x[(i+1):n])) / M[i,i]
  }
  x
}

A <- matrix(c(2,1,-1, -3,-1,2, -2,1,2), 3, byrow=TRUE)
b <- c(8,-11,-3)
print(gauss_pivot(A,b))  # 2 3 -1
```

---

## 🧠 Interpretação & Boas Práticas

* Prefira **solve/A\b** (usa fatorações) em vez de formar $A^{-1}$ explicitamente.
* Se $m>n$ (sistema sobredeterminado), use **QR** (Gram–Schmidt/Householder) para mínimos quadrados.
* Verifique **condicionamento** ($\kappa(A)$) quando resultados forem sensíveis a ruído/erros.

---

## 🏫 Exercícios em Sala

1. Escalone e resolva $\begin{cases}x+y+z=6\\2x+3y+7z=20\\-x+4y+z=9\end{cases}$ com pivotamento.
2. Classifique (única/infinitas/incompatível):
   $\begin{cases}x+2y=3\\2x+4y=6\end{cases}$,
   $\begin{cases}x+2y=3\\2x+4y=7\end{cases}$.
3. Construa um sistema 3×3 com **posto 2** e descreva o conjunto solução.

---

## 🏠 Tarefa (10 itens)

1. Reproduza o exemplo em sala mostrando cada operação de linha e as matrizes intermediárias.
2. Implemente eliminação **sem** pivotamento e mostre um caso onde falha (ou gera grande erro).
3. Gere sistemas aleatórios 4×4 e compare `inv(A)%*%b` com `solve(A,b)` (ou QR).
4. Para um sistema 3×3 **incompatível**, mostre a linha do tipo $[0\;0\;0\,|\,c]$.
5. Para um sistema com **infinitas soluções**, identifique variáveis livres e escreva a solução paramétrica.
6. Compare custo/tempo entre sua implementação e `solve`/`\` da linguagem.
7. Verifique numericamente que **posto** = número de pivôs.
8. Crie um sistema mal condicionado e estime $\kappa(A)$.
9. Resolva um sistema 5×5 com sua função de pivotamento.
10. (Bônus) Escreva uma rotina que retorne também $L$ e $U$ a partir das operações aplicadas.

---

**✅ Resultado:** Compreendemos como montar $[A|b]$, escalonar com pivotamento, classificar e resolver sistemas, e implementamos o método em três linguagens.
