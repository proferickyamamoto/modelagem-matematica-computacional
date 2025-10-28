# Aula – Resolução de Sistemas por Mínimos Quadrados

## 🎯 Objetivos
- Entender quando um sistema **não possui solução exata** e como encontrar a **melhor aproximação**.  
- Aplicar o **método dos Mínimos Quadrados** em sistemas sobredeterminados (m > n).  
- Implementar a solução em **Python**, **Octave** ou **R**.  
- Analisar a geometria e o significado da projeção em subespaços.

---

## 🧠 Introdução

Nem todo sistema linear tem solução exata.

Exemplo:  
\$$
A x = b, \quad A \in \mathbb{R}^{m \times n}, \; m > n
\$$

Quando **m > n**, temos **mais equações do que incógnitas**.  
Normalmente **não existe x** tal que \(A x = b\).  
Mas podemos buscar **x̂** que **minimiza o erro** \(||A x - b||_2\).

👉 Essa é a ideia do **método dos Mínimos Quadrados**.

---

## 📉 Conceito Geométrico

- O vetor \(A x̂\) é a **projeção ortogonal** de \(b\) sobre o espaço coluna de \(A\).  
- O resíduo \(r = b - A x̂\) é **ortogonal** a todas as colunas de \(A\).

Logo:
\[
A^T (b - A x̂) = 0
\]
\[
\Rightarrow A^T A x̂ = A^T b
\]

📘 Esta equação é chamada de **Equação Normal**.

---

## 🧮 Exemplo Numérico

Sistema sobredeterminado:

\[
A =
\begin{bmatrix}
1 & 1 \\
1 & 2 \\
1 & 3
\end{bmatrix},
\quad
b =
\begin{bmatrix}
1 \\ 2 \\ 2
\end{bmatrix}
\]

**Etapas:**
1️⃣ Calcular \(A^T A\) e \(A^T b\)
\[
A^T A =
\begin{bmatrix}
3 & 6 \\
6 & 14
\end{bmatrix},
\quad
A^T b =
\begin{bmatrix}
5 \\ 11
\end{bmatrix}
\]

2️⃣ Resolver:
\[
(A^T A) x̂ = A^T b
\Rightarrow
\begin{bmatrix}
3 & 6 \\
6 & 14
\end{bmatrix}
\begin{bmatrix}
a \\ b
\end{bmatrix}
=
\begin{bmatrix}
5 \\ 11
\end{bmatrix}
\]

3️⃣ Solução:
\[
x̂ =
\begin{bmatrix}
a \\ b
\end{bmatrix}
=
(A^T A)^{-1} A^T b
=
\begin{bmatrix}
0.333 \\ 0.667
\end{bmatrix}
\]

✅ Resultado:
\[
\hat{y} = 0.333 + 0.667 x
\]

---

## 📈 Interpretação

O vetor \(x̂\) representa os **coeficientes da reta de regressão** que melhor ajusta os pontos:
(1,1), (2,2), (3,2)

Gráfico:  
📉 A reta não passa exatamente pelos pontos, mas **minimiza o erro total quadrático**.

---

## 💻 Implementação em Python

```python
import numpy as np

A = np.array([[1,1],
              [1,2],
              [1,3]], dtype=float)
b = np.array([[1],[2],[2]], dtype=float)

# Método dos mínimos quadrados
x_hat = np.linalg.inv(A.T @ A) @ A.T @ b
print("Solução por mínimos quadrados:\n", x_hat)

# Verificação via função pronta
x_np, _, _, _ = np.linalg.lstsq(A, b, rcond=None)
print("Solução com lstsq():\n", x_np)
````

---

## 💻 Implementação em Octave

```octave
A = [1 1; 1 2; 1 3];
b = [1; 2; 2];

x_hat = inv(A'*A) * A' * b
x_oct = A \ b   % método embutido (usa QR)
```

---

## 💻 Implementação em R

```r
A <- matrix(c(1,1, 1,2, 1,3), ncol=2, byrow=TRUE)
b <- c(1,2,2)

x_hat <- solve(t(A) %*% A) %*% t(A) %*% b
x_lm <- lm(b ~ A[,2])
x_hat
summary(x_lm)
```

---

## 📊 Comparativo com LU e QR

| Método            | Tipo de sistema  | Estabilidade  | Custo computacional |
| :---------------- | :--------------- | :------------ | :------------------ |
| LU                | Quadrado         | Boa           | O(n³)               |
| QR                | Retangular (m≥n) | **Melhor**    | O(mn²)              |
| Mínimos Quadrados | Sobredeterminado | Boa           | O(mn²)              |
| SVD               | Qualquer         | **Excelente** | O(mn² + n³)         |

---

## 🧾 Exercícios em Sala

1️⃣ Resolva por mínimos quadrados:
[
A =
\begin{bmatrix}
1 & 1 \
1 & 2 \
1 & 4
\end{bmatrix},
\quad
b =
\begin{bmatrix}
2 \ 3 \ 6
\end{bmatrix}
]

2️⃣ Compare os resultados de (x̂) com o método direto `np.linalg.lstsq(A,b)`.

3️⃣ Plote o gráfico (pontos e reta ajustada).

4️⃣ Teste um caso com ruído:
b = [1.2, 1.9, 3.1]
Como o resultado muda?

---

## 🏠 Tarefa (para casa)

* Explique, com suas palavras, o significado de **projeção ortogonal**.
* Gere um exemplo em que o sistema seja **superdeterminado (m>n)** e outro **subdeterminado (m<n)**, e descreva as diferenças.
* Entregue um pequeno **relatório (PDF)** com:

  * códigos usados,
  * gráficos,
  * e análise em 1 parágrafo.

---

## 📚 Referências

* Strang, G. *Introduction to Linear Algebra*.
* Trefethen & Bau, *Numerical Linear Algebra*.
* Lay, D. *Linear Algebra and Its Applications*.
* MIT OCW – *18.06 Linear Algebra*, Lecture 23: Least Squares Problems.

---

🚀 **Conclusão:**
O método dos **Mínimos Quadrados** fornece uma solução aproximada para sistemas sem solução exata, minimizando o erro entre os dados e o modelo linear — base essencial para **regressão**, **ajuste de curvas** e **aprendizado de máquina**.

