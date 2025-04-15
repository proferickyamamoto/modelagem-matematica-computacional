# Aula 06.1- Cálculo Diferencial: Derivadas e Pontos Críticos

## 🎯 Objetivos da Aula

- 📌 Identificar pontos críticos em funções utilizando derivadas.
- 📌 Distinguir entre máximos, mínimos e pontos de inflexão.
- 📌 Aplicar derivadas de 1ª e 2ª ordem para estudo do comportamento de funções.
- 📌 Resolver problemas de otimização com base em análise de derivadas.
- 📌 Utilizar Octave/Scilab ou R para localizar e classificar pontos críticos.

---

## 🧠 Conceito de Ponto Crítico

Um **ponto crítico** de uma função ocorre quando a sua **derivada primeira é nula ou indefinida**:

\$$f'(x) = 0 \quad \text{ou} \quad f'(x) \text{ não existe}\$$

Nesses pontos, a função pode atingir um **valor máximo**, **mínimo** ou apresentar uma **mudança no comportamento da concavidade**.

---

## 📐 Teste da Primeira Derivada

### Passos:
1. Calcule a derivada primeira \$$f'(x) \$$.
2. Encontre os pontos onde \$$f'(x) = 0 \$$.
3. Analise o sinal de \$$f'(x) \$$ antes e depois de cada ponto:
   - Se muda de **positivo para negativo**, temos um **máximo local**.
   - Se muda de **negativo para positivo**, temos um **mínimo local**.

---

## 📈 Teste da Segunda Derivada

### Passos:
1. Calcule \$$f''(x) \$$.
2. Avalie o sinal de \$$f''(x) \$$ nos pontos críticos:
   - \$$f''(x) > 0 \$$: **mínimo local** (concavidade para cima).
   - \$$f''(x) < 0 \$$: **máximo local** (concavidade para baixo).
   - \$$f''(x) = 0 \$$: **inconclusivo** (usar o teste da 1ª derivada ou gráfico).

---

## 🧮 Exemplo:

Seja \$$f(x) = x^3 - 6x^2 + 9x + 1 \$$

1. Derivada primeira:
   \$$f'(x) = 3x^2 - 12x + 9 \$$
   Resolver \$$f'(x) = 0 \$$ → \$$x = 1 \$$ e \$$x = 3 \$$

2. Derivada segunda:
   \$$f''(x) = 6x - 12 \$$
   - \$$f''(1) = -6 \$$ → Máximo local
   - \$$f''(3) = 6 \$$ → Mínimo local

---

## 💻 Código Octave/Scilab

```octave
pkg load symbolic;
syms x;
f = x^3 - 6*x^2 + 9*x + 1;
f1 = diff(f, x);
f2 = diff(f1, x);

% Encontrar raízes da derivada
criticos = double(solve(f1 == 0));

% Classificar os pontos
for i = 1:length(criticos)
    tipo = double(subs(f2, x, criticos(i)));
    if tipo > 0
        fprintf("x = %.2f é um mínimo local\n", criticos(i));
    elseif tipo < 0
        fprintf("x = %.2f é um máximo local\n", criticos(i));
    else
        fprintf("x = %.2f é um ponto inconclusivo\n", criticos(i));
    end
end
```

---

## 🧠 Atividade Prática

### 1. Encontre os pontos críticos das seguintes funções e classifique-os:
- a) \$$f(x) = x^4 - 4x^2 \$$
- b) \$$f(x) = \ln(x^2 + 1) \$$
- c) \$$f(x) = \frac{x}{x^2 + 1} \$$

### 2. Use Octave ou R para:
- Calcular \$$f'(x) \$$ e \$$f''(x) \$$
- Determinar se cada ponto é máximo, mínimo ou ponto de inflexão

---

## 📌 Tarefa para Casa

1️⃣ Resolver os itens 1 e 2 da atividade prática.
2️⃣ Construir um gráfico da função do item (a), mostrando os pontos críticos destacados.
3️⃣ Escrever uma explicação sobre como os testes das derivadas ajudaram na classificação.

---

## 🧭 Próxima Aula

- Aplicações de máximos e mínimos em problemas reais (otimização).
- Estudo de intervalos de crescimento e decrescimento.
- Análise de concavidade e esboço de gráficos.

---

🚀 **Vamos identificar e interpretar os pontos de virada das funções!**

