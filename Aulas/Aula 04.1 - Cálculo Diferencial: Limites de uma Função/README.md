# Aula 04.1 - Cálculo Diferencial: Limites de uma Função

## 🎯 Objetivos da Aula
- 📌 Compreender o conceito de **limite de uma função**.
- 📌 Explorar a **notação matemática** e as **propriedades dos limites**.
- 📌 Analisar **limites laterais** e **limites infinitos**.
- 📌 Aplicar os limites para definir a **continuidade de funções**.
- 📌 Resolver exercícios utilizando **Octave/Scilab e R** para análise computacional.

---

## 📌 Introdução ao Conceito de Limite

O limite de uma função descreve **o comportamento da função à medida que a variável independente se aproxima de um determinado valor**.

- **Notação matemática:**

  $$\ \lim_{{x \to a}} f(x) = L \$$

  Isso significa que **quando x se aproxima de a, f(x) se aproxima de L**.

- **Exemplo intuitivo:**
  - Se temos $$\ f(x) = x^2 \$$ , então:

  $$\ \lim_{{x \to 2}} x^2 = 4 \$$
  
  Pois, conforme **x se aproxima de 2**, os valores de $$\ x^2 \$$ se aproximam de **4**.

### 📈 Representação Gráfica do Conceito de Limite
Abaixo, um gráfico que representa como o limite se comporta:

O limite de uma função descreve **o comportamento da função à medida que a variável independente se aproxima de um determinado valor**.

- **Notação matemática:**

  $$\ \lim_{{x \to a}} f(x) = L \$$

  Isso significa que **quando x se aproxima de a, f(x) se aproxima de L**.

- **Exemplo intuitivo:**
  - Se temos $$\ f(x) = x^2 \$$, então:

  $$\ \lim_{{x \to 2}} x^2 = 4 \$$

  Pois, conforme **x se aproxima de 2**, os valores de $$\  x^2 \$$ se aproximam de **4**.

---

## 📊 Limites Laterais
Os **limites laterais** analisam o comportamento da função à esquerda e à direita de um ponto $$\ a \$$.

- **Limite pela esquerda:**

  $$\ \lim_{{x \to a^-}} f(x) \$$

  (Quando x se aproxima de a por valores menores que a).

- **Limite pela direita:**

  $$\ \lim_{{x \to a^+}} f(x) \$$

  (Quando x se aproxima de a por valores maiores que a).

- **Se os limites laterais forem diferentes, o limite não existe!**

- **Exemplo:**
  ![Descrição da imagem](https://github.com/proferickyamamoto/modelagem-matematica-computacional/blob/eadf7c24ae28107bd6f96872345dbfd7d2e9a24f/Aulas/Aula%2004.1%20-%20) ▋

  $$\ \lim_{{x \to 3^-}} f(x) = 4 \neq \lim_{{x \to 3^+}} f(x) = 6 \$$
  
  **Conclusão:** O limite de $$\ f(x) \$$ em $$\ x = 3 \$$ **não existe**.

---

## 🔄 Limites Infinitos e no Infinito

- **Limites infinitos:** Ocorrem quando $$\ f(x) \$$ cresce ou decresce indefinidamente à medida que $$\ x \$$ se aproxima de um ponto.

  $$\ \lim_{{x \to a}} f(x) = \infty \quad \text{ou} \quad \lim_{{x \to a}} f(x) = -\infty\$$

- **Limites no infinito:** Ocorrem quando $$\ x \$$ cresce indefinidamente.

  $$\ \lim_{{x \to \infty}} f(x) = L \$$

- **Exemplo:**

  $$\ \lim_{{x \to \infty}} \frac{1}{x} = 0 \$$
  
  Conforme $$\ x \$$ aumenta, $$\ 1/x \$$ se aproxima de **0**.

---

## 🏗️ Propriedades dos Limites

Sejam $$\  \lim_{{x \to a}} f(x) = L \$$ e $$\ \lim_{{x \to a}} g(x) = M \$$, então:

1️⃣ **Soma/Diferença:**
   $$\ \lim_{{x \to a}} [f(x) \pm g(x)] = L \pm M \$$

2️⃣ **Produto:**
   $$\ \lim_{{x \to a}} [f(x) \cdot g(x)] = L \cdot M \$$

3️⃣ **Quociente:**
   $$\ \lim_{{x \to a}} \frac{f(x)}{g(x)} = \frac{L}{M}, \quad \text{se } M \neq 0 \$$

4️⃣ **Constante multiplicada:**
   $$\ \lim_{{x \to a}} [c \cdot f(x)] = c \cdot L \$$

---

## 📊 Código para Cálculo de Limites
### 🟢 **Em Octave/Scilab**:
```octave
syms x;
f = (x^2 - 4)/(x - 2);
limit(f, x, 2) % Calcula o limite quando x -> 2
```

### 🟢 **Em R**:
```r
library(Ryacas)
x <- Sym("x")
f <- (x^2 - 4)/(x - 2)
Simplify(Limit(f, x, 2))
```

---

## 🏆 Atividade Prática
### 🟢 Fácil
1️⃣ Calcule o limite: $$\ \lim_{{x \to 3}} (x^2 + 2x - 3)) \$$.

### 🟡 Intermediário
2️⃣ Determine os **limites laterais** da função:
   
  ![Intermediário](https://github.com/proferickyamamoto/modelagem-matematica-computacional/blob/eadf7c24ae28107bd6f96872345dbfd7d2e9a24f/Aulas/Aula%2004.1%20-%20C%C3%A1lculo%20Diferencial) ▋

### 🔴 Difícil
3️⃣ Encontre os valores de $$\ a \$$ e $$\ b \$$ para que a função seja contínua em $$\ x = 1 \$$:
   
  ![Difícil](https://github.com/proferickyamamoto/modelagem-matematica-computacional/blob/eadf7c24ae28107bd6f96872345dbfd7d2e9a24f/Aulas/Aula%2004.1%20-%20C%C3%A1lculo%20Diferencial%3A%20Limites%20de%20uma%20Fun%C3%A7%C3%A3o/src/dificil.png)

---

## 📌 Resumo da Aula
- ✅ O conceito de **limite** descreve o comportamento de uma função em torno de um ponto.
- ✅ **Limites laterais** determinam a continuidade de uma função.
- ✅ **Limites infinitos** ajudam a entender o crescimento e decaimento das funções.
- ✅ Utilizamos **Octave/Scilab e R** para cálculos de limites computacionais.

---

## 📌 Tarefa para Casa
1️⃣ Resolva os exercícios propostos.
2️⃣ Use Octave ou R para calcular limites computacionais.
3️⃣ Analise graficamente como a função se comporta perto do ponto avaliado.

---

## 🎯 Próxima Aula
- 📌 **Definição de Derivada**: Conceito e aplicações práticas.
- 📌 **Regras básicas de derivação**.
- 📌 **Cálculo computacional de derivadas** em Octave/Scilab e R.

---

🔥 **Vamos explorar o cálculo diferencial com mais profundidade!** 🚀
