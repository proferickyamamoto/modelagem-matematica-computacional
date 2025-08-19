# Aula 13.2: Projeção, Ortogonalidade e Decomposição
---

## 🎯 Objetivos

* Entender projeção de vetores sobre vetores e subespaços.
* Compreender ortogonalidade, bases ortonormais e o teorema da projeção.
* Relacionar projeção com **mínimos quadrados** (regressão linear).
* Implementar projeções e Gram–Schmidt em Octave, R e Python.

---

## 🔁 Relembrando (Aula 02)

* Produto escalar: $u\cdot v = \sum_i u_i v_i$
* Norma: $\|v\| = \sqrt{v\cdot v}$
* Ângulo: $\cos\theta = \dfrac{u\cdot v}{\|u\|\,\|v\|}$

---

## 📘 Fundamento Teórico

### 1) Projeção de um vetor sobre outro (reta)

Para vetores não nulos $u, v \in \mathbb{R}^n$:

$\operatorname{proj}_u(v) = \frac{v\cdot u}{u\cdot u}\,u$

Decomposição ortogonal de $v$:

$ v = v_{\parallel} + v_{\perp},\quad v_{\parallel} = \operatorname{proj}_u(v),\; v_{\perp} = v - v_{\parallel},\;\text{com}\; v_{\perp}\perp u.$

### 2) Projeção sobre um subespaço (colunas de A)

Seja $A\in\mathbb{R}^{n\times k}$ de posto completo (colunas LI). A projeção ortogonal de $b\in\mathbb{R}^n$ sobre $\mathcal{C}(A)$ é:
$$\hat b = P_A b,\quad P_A = A(A^T A)^{-1}A^T.$$
Propriedades: $$P_A$$ é **simétrica** e **idempotente** ($P_A^2=P_A$). O resíduo $r=b-\hat b$ é ortogonal a $$\mathcal{C}(A)$: $A^T r=0$$.

### 3) Ortogonalidade, bases ortonormais e Gram–Schmidt

* Conjunto ortogonal: vetores mutuamente ortogonais (produto escalar zero). Se não nulos → LI.
* Base ortonormal: vetores unitários e ortogonais. Facilita projeções e coordenadas.
* **Gram–Schmidt**: dado $(v_1,\dots,v_k)$, constrói base ortonormal $(q_1,\dots,q_k)$:
  $u_1=v_1,\; q_1=\frac{u_1}{\|u_1\|},\quad u_j=v_j-\sum_{i=1}^{j-1}(v_j\cdot q_i)q_i,\; q_j=\frac{u_j}{\|u_j\|}.$

### 4) Melhor aproximação e mínimos quadrados

O **Teorema da Projeção** garante que $\hat b=P_Ab$ é o ponto de $\mathcal{C}(A)$ mais próximo de $b$. Em regressão linear, $\hat y = X\hat\beta$, com $\hat\beta=(X^TX)^{-1}X^Ty$.

---

## 🧮 Exemplos Rápidos

**Ex. 1 (reta em $\mathbb{R}^2$):** $u=(2,1),\; v=(3,4)$.
$v_{\parallel} = \dfrac{v\cdot u}{u\cdot u}\,u = \dfrac{3\cdot2+4\cdot1}{2^2+1^2}\,(2,1) = \dfrac{10}{5}(2,1)=(4,2)$.
$v_{\perp} = v-v_{\parallel} = (3,4)-(4,2)=(-1,2)$ e $v_{\perp}\cdot u=0$.

**Ex. 2 (projeção via matriz):** $A=\begin{bmatrix}1\\1\\0\end{bmatrix}$, subespaço gerado pela coluna.
$P_A=A(A^TA)^{-1}A^T\Rightarrow A^TA=[2],\; (A^TA)^{-1}=[1/2]$,
$P_A=\tfrac{1}{2}\begin{bmatrix}1\\1\\0\end{bmatrix}[1\;1\;0]=\tfrac12\begin{bmatrix}1&1&0\\1&1&0\\0&0&0\end{bmatrix}.$

---

## 💻 Código – Projeção e Gram–Schmidt

### Octave/Matlab

```octave
function vp = proj_u(v, u)
  vp = (dot(v,u)/dot(u,u)) * u;
endfunction

% Exemplo
u = [2;1]; v = [3;4];
vp = proj_u(v,u);
vr = v - vp;  % componente ortogonal

% Projeção sobre colunas de A
A = [1;1;0]; A = reshape(A,3,1); % 3x1
P = A*inv(A'*A)*A';
b = [2;0;1];
hatb = P*b; r = b - hatb;  % A'*r ~ 0

% Gram–Schmidt (clássico)
function [Q,R] = gramschmidt(V)
  [n,k] = size(V);
  Q = zeros(n,k); R = zeros(k,k);
  for j=1:k
    v = V(:,j);
    for i=1:j-1
      R(i,j) = Q(:,i)'*v;
      v = v - R(i,j)*Q(:,i);
    end
    R(j,j) = norm(v);
    Q(:,j) = v / R(j,j);
  end
endfunction
```

### R

```r
proj_u <- function(v, u) {
  drop((sum(v*u)/sum(u*u)) * u)
}

u <- c(2,1); v <- c(3,4)
vp <- proj_u(v,u); vr <- v - vp

A <- matrix(c(1,1,0), nrow=3)
P <- A %*% solve(t(A)%*%A) %*% t(A)
b <- c(2,0,1)
hatb <- P %*% b; r <- b - hatb  # t(A)%*%r ~ 0

gram_schmidt <- function(V){
  V <- as.matrix(V); n <- nrow(V); k <- ncol(V)
  Q <- matrix(0,n,k); R <- matrix(0,k,k)
  for(j in 1:k){
    v <- V[,j]
    for(i in 1:(j-1)){
      R[i,j] <- sum(Q[,i]*v)
      v <- v - R[i,j]*Q[,i]
    }
    R[j,j] <- sqrt(sum(v*v))
    Q[,j] <- v/R[j,j]
  }
  list(Q=Q,R=R)
}
```

### Python (NumPy)

```python
import numpy as np

def proj_u(v, u):
    v = np.asarray(v, float); u = np.asarray(u, float)
    return (np.dot(v,u)/np.dot(u,u)) * u

u = np.array([2.0, 1.0]); v = np.array([3.0, 4.0])
vp = proj_u(v, u); vr = v - vp

A = np.array([[1.0],[1.0],[0.0]])
P = A @ np.linalg.inv(A.T @ A) @ A.T
b = np.array([2.0,0.0,1.0])
hatb = P @ b; r = b - hatb   # A.T @ r ≈ 0

# Gram–Schmidt (clássico)
def gram_schmidt(V):
    V = np.array(V, float)
    n, k = V.shape
    Q = np.zeros((n,k)); R = np.zeros((k,k))
    for j in range(k):
        v = V[:,j].copy()
        for i in range(j):
            R[i,j] = Q[:,i] @ v
            v -= R[i,j] * Q[:,i]
        R[j,j] = np.linalg.norm(v)
        Q[:,j] = v / R[j,j]
    return Q, R
```

---

## 🧠 Aplicações

* **Regressão linear (mínimos quadrados):** $\hat y = X\hat\beta$ é a projeção de $y$ em $\mathcal{C}(X)$.
* **Computação gráfica:** separar componente **difusa** ($\parallel$) e **especular** ($\perp$) via projeções.
* **Sinais:** filtragem por decomposição em bases ortogonais (Fourier, wavelets).

---

## 🏫 Exercícios em Sala

1. Calcule $\operatorname{proj}_u(v)$ para $u=(1,2,2), v=(3,0,1)$; ache $v_{\perp}$ e verifique ortogonalidade.
2. Dado $A = \begin{bmatrix}1&0\\1&1\\0&1\end{bmatrix}$, construa $P_A$ e verifique se $P_A^2=P_A$ e $P_A^T=P_A$.
3. Aplique Gram–Schmidt em $(1,1,0)^T, (1,0,1)^T$ e normalize.
4. Explique por que o resíduo de mínimos quadrados é ortogonal às colunas de $A$.

---

## 🏠 Tarefa para Casa

1. Para $u=(2,-1,2)$ e $v=(0,3,1)$: compute $\operatorname{proj}_u(v)$, decomponha $v$ e calcule $\|v_{\perp}\|$.
2. Dado $A=\begin{bmatrix}1&1\\1&-1\\0&1\end{bmatrix}$, forme $P_A$ e comprove simetria e idempotência.
3. Implemente Gram–Schmidt modificado e compare com o clássico (condicionamento).
4. Gere dados $(x_i,y_i)$ e ajuste $y\approx\beta_0+\beta_1 x$ via $\hat\beta=(X^TX)^{-1}X^Ty$; plote pontos e reta.
5. (Desafio) Em $\mathbb{R}^3$, projete $b$ no plano $x+y+z=0$ e calcule a distância de $b$ ao plano.

---

## 📚 Referências

* Boyd, S.; Vandenberghe, L. *Introduction to Applied Linear Algebra*, Cambridge, 2018.
* Strang, G. *Introduction to Linear Algebra*, Wellesley–Cambridge, 4ª ed.
* Axler, S. *Linear Algebra Done Right*, Springer.

---

**🚀 Na próxima aula:** Transformações lineares, matrizes de rotação/escala e mudança de base.
