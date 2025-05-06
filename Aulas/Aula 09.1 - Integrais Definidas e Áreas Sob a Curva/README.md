# Aula 09.1: Integrais Definidas e Áreas Sob a Curva

## 🎯 Objetivos da Aula

* 📌 Compreender o conceito de integral definida como área sob a curva.
* 📌 Aplicar o Teorema Fundamental do Cálculo.
* 📌 Utilizar integrais definidas para calcular áreas em intervalos.
* 📌 Resolver problemas práticos de aplicação de integrais definidas.
* 📌 Implementar cálculos em Octave ou R.

---

## 🧠 Conceito de Integral Definida

A **integral definida** representa a **área sob a curva** de uma função contínua $f(x)$ no intervalo $[a, b]$:

$\int_a^b f(x) \, dx$

Se $f(x) \geq 0$, o resultado é a área da região entre o gráfico da função e o eixo $x$. Se a função for negativa em partes, o valor será a diferença algébrica (área negativa).

---

## 📘 Teorema Fundamental do Cálculo

Se $F(x)$ é uma antiderivada de $f(x)$, então:

$\int_a^b f(x) \, dx = F(b) - F(a)$

Essa propriedade permite calcular integrais definidas com rapidez, desde que saibamos a primitiva da função.

---

## 📈 Exemplo Resolvido

Calcular:

$\int_0^2 (3x^2 + 1) \, dx$

**Solução:**

A primitiva de $f(x) = 3x^2 + 1$ é:

$F(x) = x^3 + x$

Aplicando o Teorema Fundamental:

$F(2) - F(0) = (8 + 2) - (0 + 0) = 10$

✅ Resultado: área sob a curva é 10 unidades quadradas.

---

## 💻 Cálculo em Octave

```octave
pkg load symbolic;
syms x;
f = 3*x^2 + 1;
area = int(f, x, 0, 2);
disp(area); % Resultado: 10
```

---

## 🧮 Propriedades da Integral Definida

1. $\int_a^a f(x) \, dx = 0$
2. $\int_a^b f(x) \, dx = -\int_b^a f(x) \, dx$
3. $\int_a^b [f(x) + g(x)] \, dx = \int_a^b f(x) \, dx + \int_a^b g(x) \, dx$
4. $\int_a^c f(x) \, dx + \int_c^b f(x) \, dx = \int_a^b f(x) \, dx$

---

## 📊 Aplicações Comuns

* Cálculo de área de regiões planas.
* Distância total percorrida com velocidade variável.
* Trabalho realizado por força variável.
* Cálculo de consumo acumulado.

---

## 🧠 Atividade Prática

### Parte 1 – Integrais definidas diretas

1. Calcule:

   * a) $\int_1^3 (2x + 1) \, dx$
   * b) $\int_0^\pi \sin(x) \, dx$

### Parte 2 – Interpretação

2. Com base nos resultados acima, descreva:

   * a) O que o valor da integral representa.
   * b) Se a área foi positiva ou negativa.

### Parte 3 – Octave ou R

3. Calcule em software:

   * a) $\int_0^1 x \cdot e^x \, dx$
   * b) $\int_{-1}^1 \frac{x}{1 + x^2} \, dx$

---

## 📌 Tarefa para Casa

1️⃣ Resolver manualmente os itens 1 e 2.
2️⃣ Implementar os cálculos da Parte 3 e entregar com print do código e resultado.

---

## 📚 Próxima Aula

* Técnicas de integração (substituição e partes)
* Integração de funções compostas
* Preparação para aplicações em Física e Economia

---

🚀 **Vamos calcular áreas e interpretar os significados reais das integrais definidas!**
