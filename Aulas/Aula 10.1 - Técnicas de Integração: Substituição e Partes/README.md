# Aula 10.1 – Técnicas de Integração: Substituição e Partes

## 🎯 Objetivos da Aula

* 📌 Revisar e consolidar técnicas de integração por substituição e por partes.
* 📌 Aplicar essas técnicas em problemas reais de física e economia.
* 📌 Interpretar geometricamente e computacionalmente os resultados obtidos.
* 📌 Encerrar o semestre com um panorama das aplicações de integrais.

---

## 🧠 Revisão: Integração por Substituição

### 🧩 Técnica

Seja $u = g(x)$, então:

$\int f(g(x)) \cdot g'(x) \, dx = \int f(u) \, du$

### ✅ Exemplo:

Calcular:
$\int 2x \cdot \cos(x^2) \, dx$

**Solução:**

* Substituir: $u = x^2 \Rightarrow du = 2x \, dx$
* Resultado: $\int \cos(u) \, du = \sin(u) + C = \sin(x^2) + C$

---

## 🧠 Revisão: Integração por Partes

### 🧩 Fórmula

$\int u \, dv = u \cdot v - \int v \, du$

### ✅ Exemplo:

Calcular:
$\int x \cdot \ln(x) \, dx$

**Solução:**

* Escolha: $u = \ln(x), \ dv = x \, dx$
* Deriva: $du = \frac{1}{x}dx, \ v = \frac{x^2}{2}$
* Resultado: $\frac{x^2}{2} \cdot \ln(x) - \int \frac{x^2}{2} \cdot \frac{1}{x} \, dx = \frac{x^2}{2}\ln(x) - \frac{x^2}{4} + C$

---

## 💻 Cálculo em Octave (exemplo)

```octave
pkg load symbolic;
syms x;
assume(x > 0);
f = x*log(x);
int_f = int(f, x);
disp(int_f);
```

---

## 📈 Aplicações

### Física:

* Cálculo de trabalho: $W = \int_a^b F(x) \, dx$

### Economia:

* Receita total: $R = \int_0^x p(q) \, dq$, onde $p(q)$ é o preço por unidade em função da quantidade.

---

## 🧠 Atividade Final

### Parte 1 – Substituição

1. Resolva:

   * a) $\int x \cdot \sqrt{x^2 + 1} \, dx$
   * b) $\int \frac{1}{\sqrt{1 - x^2}} \, dx$

### Parte 2 – Por partes

2. Resolva:

   * a) $\int x \cdot e^x \, dx$
   * b) $\int \ln(x) \, dx$

### Parte 3 – Aplicação computacional

3. Use Octave ou R para resolver o item 2a. Anexe código e resultado.

---

## 📌 Encerramento e Avaliação

* 📝 Cada grupo entrega um arquivo PDF com a resolução das questões.
* 📥 Enviar via Portal do Aluno até o fim da aula.
* 👥 Grupos de até 5 alunos, com RMs identificados.

---

## 📚 Balanço Final do Semestre

* 🔄 Derivadas: comportamento, otimização, crescimento.
* 🧮 Integrais: área, soma contínua, aplicações práticas.
* 🛠 Técnicas: substituição, partes, computação simbólica.

---

🚀 **Parabéns por toda a evolução no semestre! Que venha o próximo desafio!**
