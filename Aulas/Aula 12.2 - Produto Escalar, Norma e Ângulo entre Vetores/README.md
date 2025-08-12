# Aula 12.2 – Produto Escalar, Norma e Ângulo entre Vetores

---

## 🎯 Objetivos

* Compreender o conceito e a definição formal de produto escalar.
* Calcular a norma (magnitude) de um vetor.
* Determinar o ângulo entre dois vetores.
* Aplicar os conceitos em situações práticas e computacionais.

---

## 📘 Fundamento Teórico

## ➕ Operações com Vetores

### Soma e Subtração

Para u = \[u1,…,un] e v = \[v1,…,vn]:

* u + v = \[u1+v1, …, un+vn]
* u − v = \[u1−v1, …, un−vn]
  Interpretação geométrica: a soma segue a regra do paralelogramo; a subtração é a soma com o vetor oposto.

### Multiplicação por Escalar

Para α ∈ ℝ:  α·u = \[αu1, …, αun]

* Efeitos: escala o comprimento; preserva direção se α>0; inverte se α<0.
* Norma: ||αu|| = |α|·||u||.

### Combinação Linear e Span

Uma combinação linear de u e v é αu + βv. O conjunto de todas as combinações lineares é o subespaço gerado (span). Em ℝ², duas direções não colineares geram o plano; em ℝ³, três vetores não coplanares geram o espaço. (Axler, 2015; Strang, 2009)

### Propriedades Algébricas (em ℝⁿ)

* Comutatividade: u+v = v+u
* Associatividade: (u+v)+w = u+(v+w)
* Elemento neutro: existe 0 tal que u+0 = u
* Inverso aditivo: u + (−u) = 0
* Distributividade: α(u+v) = αu + αv e (α+β)u = αu + βu

### Exemplo Rápido

Sejam u = \[2, −1, 0], v = \[1, 3, 4], α = 2, β = −1.

* u+v = \[3, 2, 4]
* u−v = \[1, −4, −4]
* 2u = \[4, −2, 0],  −v = \[−1, −3, −4]
* Combinação linear: αu + βv = 2\[2, −1, 0] − \[1, 3, 4] = \[3, −5, −4]

### Código (Octave)

```octave
u = [2, -1, 0];
v = [1, 3, 4];
alpha = 2; beta = -1;

sum_uv = u + v;
diff_uv = u - v;
alpha_u = alpha * u;
minus_v = -v;
comb = alpha*u + beta*v;

printf("u+v = [%g %g %g]
", sum_uv);
printf("u-v = [%g %g %g]
", diff_uv);
printf("2u = [%g %g %g]
", alpha_u);
printf("-v = [%g %g %g]
", minus_v);
printf("2u - v = [%g %g %g]
", comb);
```

### Código (R)

```r
u <- c(2, -1, 0)
v <- c(1, 3, 4)
alpha <- 2; beta <- -1

sum_uv <- u + v
diff_uv <- u - v
alpha_u <- alpha * u
minus_v <- -v
comb <- alpha * u + beta * v

print(list(sum_uv = sum_uv, diff_uv = diff_uv, alpha_u = alpha_u, minus_v = minus_v, comb = comb))
```

### Código (Python)

```python
import numpy as np

u = np.array([2, -1, 0])
v = np.array([1, 3, 4])
alpha, beta = 2, -1

sum_uv = u + v
diff_uv = u - v
alpha_u = alpha * u
minus_v = -v
comb = alpha * u + beta * v

print("u+v =", sum_uv)
print("u-v =", diff_uv)
print("2u =", alpha_u)
print("-v =", minus_v)
print("2u - v =", comb)
```

---

### 🔹 Produto Escalar

Sejam dois vetores em $\mathbb{R}^n$:

$$
\vec{u} = [u_1, u_2, \dots, u_n],\quad \vec{v} = [v_1, v_2, \dots, v_n]
$$

O **produto escalar** (ou interno) é definido por:

$$
\vec{u} \cdot \vec{v} = \sum_{i=1}^n u_i v_i = u_1v_1 + u_2v_2 + \dots + u_nv_n
$$

Se o resultado for:

* Positivo → ângulo agudo entre os vetores
* Zero → vetores ortogonais (perpendiculares)
* Negativo → ângulo obtuso

**Referência:** Axler (2015), Strang (2009), Boyd & Vandenberghe (2018)

---

### 🔹 Norma de um Vetor

A **norma** (ou comprimento, ou magnitude) de um vetor $\vec{v} = [v_1, v_2, ..., v_n]$ é:

$$
\|\vec{v}\| = \sqrt{v_1^2 + v_2^2 + \dots + v_n^2}
$$

---

### 🔹 Ângulo entre Vetores

Usamos a fórmula do cosseno:

$$
\cos(\theta) = \frac{\vec{u} \cdot \vec{v}}{\|\vec{u}\| \cdot \|\vec{v}\|}
$$

Portanto:

$$
\theta = \cos^{-1}\left( \frac{\vec{u} \cdot \vec{v}}{\|\vec{u}\| \cdot \|\vec{v}\|} \right)
$$

**Ângulos comuns:**

* $0^\circ$ → vetores paralelos e mesmos sentidos
* $90^\circ$ → vetores ortogonais
* $180^\circ$ → vetores opostos

---

## 🧮 Exemplo 1: Produto Escalar

$$
\vec{u} = [2, -1],\quad \vec{v} = [1, 3]
$$

$$
\vec{u} \cdot \vec{v} = 2\cdot1 + (-1)\cdot3 = 2 - 3 = -1
$$

Resultado negativo → ângulo obtuso.

---

## 🧮 Exemplo 2: Norma e Ângulo

$$
\vec{u} = [3, 4],\quad \vec{v} = [4, 3]
$$

$$
\|\vec{u}\| = \sqrt{3^2 + 4^2} = 5,\quad \|\vec{v}\| = \sqrt{4^2 + 3^2} = 5
$$

$$
\vec{u} \cdot \vec{v} = 3\cdot4 + 4\cdot3 = 24
$$

$$
\cos(\theta) = \frac{24}{5\cdot5} = 0,96 \Rightarrow \theta \approx 16,26^\circ
$$

---

## 💻 Código em Octave

```octave
u = [2, -1];
v = [1, 3];
produto = dot(u, v)

mod_u = norm(u);
mod_v = norm(v);
angulo_rad = acos(dot(u, v)/(mod_u * mod_v));
angulo_graus = angulo_rad * 180 / pi
```

## 💻 Código em R

```r
u <- c(2, -1)
v <- c(1, 3)
produto <- sum(u * v)
mod_u <- sqrt(sum(u^2))
mod_v <- sqrt(sum(v^2))
angulo_rad <- acos(produto/(mod_u * mod_v))
angulo_graus <- angulo_rad * 180 / pi
print(list(produto = produto, angulo_graus = angulo_graus))
```

## 💻 Código em Python (NumPy)

```python
import numpy as np

u = np.array([2, -1])
v = np.array([1, 3])

produto = np.dot(u, v)
mod_u = np.linalg.norm(u)
mod_v = np.linalg.norm(v)
angulo_rad = np.arccos(produto / (mod_u * mod_v))
angulo_graus = np.degrees(angulo_rad)

print({"produto": int(produto), "angulo_graus": float(angulo_graus)})
```

---

## 🧠 Aplicações

* Física: trabalho $W = \vec{F} \cdot \vec{d}$
* Aprendizado de máquina: similaridade de vetores em sistemas de recomendação
* Computação gráfica: ângulo entre vetores de iluminação e normais

---

## 🏫 Exercício em Sala

1. Dados $\vec{a} = [1, 2]$, $\vec{b} = [3, 0]$:

   * a) Calcule $\vec{a} \cdot \vec{b}$
   * b) Calcule $\|\vec{a}\|$ e $\|\vec{b}\|$
   * c) Determine o ângulo entre eles
2. Interprete o significado geométrico do resultado do item (1c)
3. Teste os resultados no Octave ou R

---

## 🏠 Tarefa para Casa

1. Calcule o produto escalar entre os pares de vetores:

   * a) $[2, 1], [4, -1]$
   * b) $[-3, 5], [2, 2]$
2. Encontre a norma dos vetores:

   * a) $[0, -7]$
   * b) $[1, 2, 2]$
3. Determine o ângulo entre os seguintes vetores:

   * a) $[1, 0], [0, 1]$
   * b) $[2, 2], [1, -1]$
4. Use Octave ou R para validar os cálculos do item 3
5. Escreva um par de vetores reais do seu cotidiano e interprete o ângulo entre eles

---

## 📚 Referências

* Axler, S. *Linear Algebra Done Right*, Springer, 2015
* Strang, G. *Introduction to Linear Algebra*, Wellesley-Cambridge Press, 2009
* Boyd, S. & Vandenberghe, L. *Introduction to Applied Linear Algebra*, Cambridge, 2018

---

**🚀 Exploramos o produto escalar, norma e o ângulo entre vetores! Prepare-se para transformações e projeções nas próximas aulas.**
