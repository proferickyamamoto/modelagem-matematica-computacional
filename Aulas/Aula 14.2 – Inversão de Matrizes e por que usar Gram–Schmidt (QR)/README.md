# Aula 14.2 – Inversão de Matrizes e por que usar Gram–Schmidt (QR)

---

## 🎯 Objetivos

* Entender **quando** e **como** uma matriz é invertível e as consequências de sua inversa.
* Comparar métodos: **Gauss–Jordan**, **adjunta** e **fatorações** (LU/QR).
* Compreender **condicionamento** e por que **evitar** calcular $A^{-1}$ explicitamente.
* Justificar o uso de **Gram–Schmidt/QR** para resolver sistemas e **mínimos quadrados** com mais estabilidade.
* Implementar as técnicas em **Octave/Matlab**, **Python (NumPy)** e **R**.

---

## 📘 Fundamentos

### 1) Inversão: definição e existência

Para $A\in\mathbb{R}^{n\times n}$, dizemos que $A$ é **invertível** se existe $A^{-1}$ tal que
$A\,A^{-1}=A^{-1}A=I.$
São equivalentes:

* $\det(A)\neq 0$
* $posto\{(A)}=n$
* O sistema $A\,x=b$ tem **única** solução para todo $b\in\mathbb{R}^n$
* As colunas de $A$ são LI (base de $\mathbb{R}^n$)

**Propriedades úteis:**

* $(AB)^{-1}=B^{-1}A^{-1}$
* $(A^T)^{-1}=(A^{-1})^T$
* $\det(A^{-1})=1/\det(A)$

### 2) Como inverter (teoria x prática)

* **Gauss–Jordan**: resolve $[A\,|\,I] \to [I\,|\,A^{-1}]$. Custo $\mathcal{O}(n^3)$.
* **Adjunta**: $A^{-1}=\tfrac{adj\{(A)}}{\det(A)}$ (bom para prova/2×2/3×3; **impraticável** para $n$ grande).
* **Fatorações**: use **LU**/**QR** para **resolver** $A\,x=b$ sem formar $A^{-1}$.

### 3) Por que **não** usar $\mathbf{inv(A)}$ diretamente?

* **Custo** e **erro numérico**: formar $x=A^{-1}b$ é mais caro e menos estável que resolver $A\,x=b$ por fatoração.
* **Condicionamento**: erro relativo amplificado por $\kappa(A)=\|A\|\,\|A^{-1}\|$. Se $\kappa(A)$ é alto, pequenas perturbações $\Rightarrow$ grandes erros em $x$.
* **Regra de ouro** (Strang; Trefethen & Bau): *nunca* use `inv(A)*b`; prefira $A\\b$ (Octave/Matlab), `solve(A,b)` (NumPy/R).

### 4) Onde entra o **Gram–Schmidt/QR**?

* Para $A\in\mathbb{R}^{m\times n}$ (quadrada ou “alta”), fatoramos $A=QR$ com $Q$ **ortonormal** e $R$ triangular superior.
* Resolver $A\,x=b$: $QRx=b\Rightarrow Rx=Q^T b$ (duas etapas estáveis).
* **Mínimos quadrados** $(m>n)$: evita as **equações normais** $(A^TA)x=A^Tb$, que **pioram** o condicionamento: $\kappa(A^TA)=\kappa(A)^2$.
* **Gram–Schmidt** (melhor, **modificado**) constrói $Q$ e $R$: base ortonormal do espaço das colunas de $A$ $\Rightarrow$ projeções e soluções estáveis.

> **Resumo prático**: Calcular inversa é muitas vezes **didático**; em aplicações, resolva com **LU/QR**. Use **QR/Gram–Schmidt** em mínimos quadrados e quando a estabilidade importa.

---

## 🧮 Exemplo guiado (3×3): Gauss–Jordan x QR

Considere
$A=\begin{bmatrix} 2 & 1 & 0\\ 1 & 3 & 1\\ 0 & 1 & 2\end{bmatrix},\quad b=\begin{bmatrix}1\\2\\3\end{bmatrix}.$

1. **Gauss–Jordan**: obtenha $A^{-1}$ e calcule $x=A^{-1}b$.
2. **QR**: fatorar $A=QR$; resolva $Rx=Q^Tb$. Compare tempo/estabilidade (condição de $A$).

---

## 💻 Código

### Octave/Matlab – Gauss–Jordan, Solve e QR

```octave
% Inversa por Gauss–Jordan (didático)
function Ainv = gauss_jordan_inv(A)
  [n, m] = size(A); assert(n==m, 'A deve ser quadrada');
  AI = [A eye(n)];
  for j = 1:n
    % pivô parcial simples
    [~,p] = max(abs(AI(j:n,j))); p = p + j - 1;
    AI([j p],:) = AI([p j],:);
    % normaliza pivô
    AI(j,:) = AI(j,:) / AI(j,j);
    % zera demais linhas
    for i = 1:n
      if i ~= j
        AI(i,:) = AI(i,:) - AI(i,j)*AI(j,:);
      end
    end
  end
  Ainv = AI(:, n+1:end);
end

A = [2 1 0; 1 3 1; 0 1 2]; b = [1;2;3];
Ainv = gauss_jordan_inv(A);
x_inv = Ainv*b;

% Forma correta/estável
x_solve = A\b;           % usa LU/QR internamente
[Q,R] = qr(A); x_qr = R\(Q'*b);

fprintf('||x_inv - x_solve|| = %g\n', norm(x_inv - x_solve));
condA = cond(A); fprintf('cond(A) = %g\n', condA);
```

### Python (NumPy)

```python
import numpy as np

A = np.array([[2.,1.,0.],
              [1.,3.,1.],
              [0.,1.,2.]])
b = np.array([1.,2.,3.])

# Evitar: x = np.linalg.inv(A) @ b
x_solve = np.linalg.solve(A, b)
Q, R = np.linalg.qr(A, mode='reduced')
x_qr = np.linalg.solve(R, Q.T @ b)

print('x_solve =', x_solve)
print('x_qr    =', x_qr)
print('cond(A) =', np.linalg.cond(A))
```

### R

```r
A <- matrix(c(2,1,0, 1,3,1, 0,1,2), nrow=3, byrow=TRUE)
b <- c(1,2,3)

# Evitar: solve(A) %*% b
x_solve <- solve(A, b)     # resolução estável
qrA <- qr(A)
x_qr <- backsolve(qr.R(qrA), t(qr.Q(qrA)) %*% b)

print(x_solve)
print(x_qr)
print(kappa(A))
```

### Mínimos quadrados: normal vs QR (perigo do condicionamento)

**Python (NumPy)**

```python
import numpy as np
np.random.seed(0)
# colunas quase colineares => mal condicionado
x = np.linspace(0,1,20)
X = np.column_stack([np.ones_like(x), x, x + 1e-4*np.random.randn(len(x))])
y = 2 + 3*x + 0.1*np.random.randn(len(x))

# Equações normais (evitar)
beta_ne = np.linalg.solve(X.T@X, X.T@y)
# QR (preferível)
Q, R = np.linalg.qr(X, mode='reduced')
beta_qr = np.linalg.solve(R, Q.T @ y)

print('cond(X)   =', np.linalg.cond(X))
print('cond(X^T X)=', np.linalg.cond(X.T@X))
print('beta_ne   =', beta_ne)
print('beta_qr   =', beta_qr)
```

---

## 🧠 Por que o **Gram–Schmidt** (QR) é a escolha certa?

* **Ortonormalidade** $\Rightarrow$ projeções simples: $\hat y=QQ^Ty$.
* **Estabilidade**: evita $A^TA$ e seu condicionamento quadrático; sensível a ruído? **Menos** com QR.
* **Generalidade**: resolve $A\,x=b$ (quadrada) e $\min_x\|Ax-b\|$ (retangular) com o **mesmo** esquema $Rx=Q^Tb$.
* **Interpretação geométrica**: Gram–Schmidt constrói uma **base ortonormal** do espaço das colunas – enxergamos projeções e componentes.

> Observação: Em produção, muitas bibliotecas usam **Householder** (ainda mais estável). O **Gram–Schmidt modificado** é uma boa ponte didática.

---

## 🏫 Exercícios em Sala

1. Inverta por **Gauss–Jordan**: $\small A=\begin{bmatrix}1&2&1\\0&1&1\\2&1&0\end{bmatrix}$ e verifique $AA^{-1}=I$.
2. Resolva $A\,x=b$ com (a) `inv(A)*b` e (b) $A\\b$. Compare $\|x_a-x_b\|$ e relate com $\kappa(A)$.
3. Para dados $(x_i,y_i)$, ajuste $y\approx\beta_0+\beta_1x$ com (a) normais e (b) QR. Compare coeficientes e resíduos.

---

## 🏠 Tarefa (10 itens)

1. Demonstre: $(AB)^{-1}=B^{-1}A^{-1}$.
2. Prove: $\det(A^{-1})=1/\det(A)$.
3. Mostre que $\kappa(A)\ge 1$ e interprete.
4. Implemente Gauss–Jordan e teste em matrizes 2×2 e 3×3.
5. Gere uma matriz quase singular e meça erros de `inv(A)*b` vs `solve`.
6. Compare mínimos quadrados por **normais** vs **QR** em um dataset com colunas quase colineares.
7. A partir de $A=QR$, mostre que $Q$ tem colunas ortonormais.
8. Explique por que **equações normais** quadruplicam o condicionamento ($\kappa(A^TA)=\kappa(A)^2$).
9. Use **Gram–Schmidt modificado** para construir $Q,R$ e valide com `qr`.
10. Leitura comentada: Strang (cap. QR) e Trefethen & Bau (caps. 9–11).

---

## 📚 Referências

* **Strang, G.** *Introduction to Linear Algebra*, Wellesley–Cambridge Press.
* **Trefethen, L. N.; Bau, D.** *Numerical Linear Algebra*, SIAM.
* **Golub, G.; Van Loan, C.** *Matrix Computations*, Johns Hopkins.
* **Boyd, S.; Vandenberghe, L.** *Introduction to Applied Linear Algebra*, Cambridge.

---

**✅ Moral da aula:** *Inversa é conceito central, mas em prática resolvemos com **fatoraçõess** (LU/QR). Para estabilidade e mínimos quadrados, **QR/Gram–Schmidt** ganha de longe das equações normais.*
