# Aula 08.1: Introdução a Integrais Indefinidas

## 🎯 Objetivos da Aula

- 📌 Compreender o conceito de integral indefinida como antiderivada.
- 📌 Aprender as propriedades básicas das integrais.
- 📌 Aplicar integrais em exemplos simples de funções conhecidas.
- 📌 Utilizar Octave/Scilab e R para cálculos simbólicos de integrais.

---

## 🧠 Conceito de Integral Indefinida

A **integral indefinida** de uma função é o processo **inverso** da derivação.

Se:

\$$f'(x) = g(x) \$$

Então:

\$$\int g(x) \, dx = f(x) + C \$$

onde \$$ C \$$ é a **constante de integração** (representa uma família de soluções).

- 📈 A integral indica a "área acumulada" ou "soma contínua" da função.

---

## 📚 Propriedades das Integrais Indefinidas

| Propriedade                  | Descrição |
|-------------------------------|-----------|
| Linearidade                  | \$$\int [af(x) + bg(x)] \, dx = a \int f(x) \, dx + b \int g(x) \, dx \$$ |
| Soma de Integrais             | \$$\int (f(x) + g(x)) \, dx = \int f(x) \, dx + \int g(x) \, dx \$$ |
| Integral de função constante  | \$$\int k \, dx = kx + C \$$ |
| Integral de potência          | \$$\int x^n \, dx = \frac{x^{n+1}}{n+1} + C, \quad n \neq -1 \$$ |
| Integral do inverso           | \$$\int\frac{1}{x} \, dx = \ln{x} + C \$$ |

---

## 🧩 Tabela de Integrais Básicas

| Função \$$ g(x) \$$         | Integral \$$ \int g(x) dx \$$        |
|--------------------------|-------------------------------------|
| \$$0 \$$                  | \$$C \$$                           |
| \$$x^n \$$                | \$$\frac{x^{n+1}}{n+1} + C \$$       |
| \$$\frac{1}{x} \$$        | \$$\ln|x| + C \$$                   |
| \$$e^x \$$                | \$$e^x + C \$$                      |
| \$$\sin(x) \$$            | \$$-\cos(x) + C \$$                 |
| \$$\cos(x) \$$            | \$$\sin(x) + C \$$                  |

---

## 💻 Exemplo de uso no Octave

```octave
pkg load symbolic;
syms x;
f = x^2;
F = integrate(f, x);
disp(F); % Resultado: x^3/3 + C
```

## 💻 Exemplo de uso no R

```r
library(Ryacas)
x <- Sym("x")
Integrate(x^2, x)
```

---

## 📈 Exemplos Resolvidos

### Exemplo 1:
Calcular:

\$$ \int (3x^2 + 2x) \, dx \$$

**Solução:**

\$$ \int 3x^2 \, dx + \int 2x \, dx = x^3 + x^2 + C \$$

### Exemplo 2:
Calcular:

\$$ \int \cos(x) \, dx \$$

**Solução:**

\$$ \sin(x) + C \$$

---

## 🧠 Atividade Prática

### Parte 1 – Integrais diretas
1. Calcule as integrais:
   - a) \$$\int (5x^3 - 4x^2 + 2) \, dx \$$
   - b) \$$\int (e^x + \sin(x)) \, dx \$$

### Parte 2 – Cálculo Computacional
2. Usar Octave ou R para calcular:
   - a) \$$\int \frac{1}{x^2+1} \, dx \$$
   - b) \$$\int x \cdot e^{x^2} \, dx \$$

---

## 📌 Tarefa para Casa

1️⃣ Resolver todas as integrais propostas em papel.  
2️⃣ Implementar as integrais da Parte 2 em Octave ou R e apresentar o print dos códigos.

---

## 📚 Próxima Aula
- Introdução à integral definida
- Cálculo de áreas sob a curva
- Teorema Fundamental do Cálculo

---

🚀 **Começamos a jornada de somar continuamente! Vamos dominar as integrais!**

