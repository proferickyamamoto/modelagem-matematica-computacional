# Aula 05.1 - Cálculo Diferencial: Derivadas

## 🎯 Objetivos da Aula

- 📌 Compreender o conceito de **derivada** de uma função.
- 📌 Entender a interpretação geométrica da derivada como taxa de variação.
- 📌 Calcular derivadas de funções elementares.
- 📌 Aplicar regras de derivadas (soma, produto, quociente e cadeia).
- 📌 Utilizar Octave/Scilab e R para cálculo simbólico de derivadas.

---

## 🧠 Conceito de Derivada

A derivada é uma ferramenta matemática que nos permite entender **como uma quantidade muda em relação a outra**. Por exemplo, se pensamos em um carro em movimento, a derivada da posição em relação ao tempo nos dá a **velocidade** — ou seja, **o quão rápido a posição do carro está mudando**.

### 📘 Definição Leiga:
Imagine que você está subindo uma montanha. A cada passo que você dá, a inclinação do caminho pode aumentar, diminuir ou até ficar plana. A derivada diz exatamente **o quão íngreme está o caminho naquele ponto**. É como uma medida instantânea de "inclinação" — quanto maior, mais íngreme; se for zero, o terreno está plano.


A **derivada** de uma função em um ponto representa a **taxa de variação instantânea** dessa função. É definida como o limite do quociente incremental:

$$\ f'(x) = \lim_{{h \to 0}} \frac{f(x+h) - f(x)}{h}\$$

Essa expressão representa a **inclinação da reta tangente** ao gráfico da função no ponto \$$( x )\$$.

---

## 📐 Interpretação Geométrica

- A derivada representa a **inclinação da reta tangente** ao gráfico da função.
- Se \$$( f'(x) > 0 )\$$, a função está **crescendo** (subindo).
- Se \$$( f'(x) < 0 )\$$, a função está **decrescendo** (descendo).
- Se \$$( f'(x) = 0 )\$$, pode haver um **ponto de máximo, mínimo ou inflexão**.

### 💻 Exemplo de Código para Visualizar Inclinações (Octave)
```octave
pkg load symbolic;
syms x;
f = x^2 - 4*x + 3;
df = diff(f, x);

fplot(f, [-1, 5]);
hold on;

% Pontos para verificar a inclinação
pontos = [1, 2, 3];
cores = {'r', 'g', 'b'};
for i = 1:length(pontos)
    x0 = pontos(i);
    y0 = double(subs(f, x, x0));
    m = double(subs(df, x, x0));
    tangente = m*(x - x0) + y0;
    fplot(tangente, [x0 - 1, x0 + 1], cores{i});
end

legend('Função f(x)', 'Tangente em x=1', 'Tangente em x=2', 'Tangente em x=3');
title('Inclinação da reta tangente em diferentes pontos');
xlabel('x'); ylabel('f(x)');
grid on;
hold off;
```

Este gráfico mostra a função quadrática e retas tangentes em três pontos diferentes. Cada reta tangente mostra a inclinação (positiva, negativa ou zero) da curva naquele ponto específico.

- A derivada representa a **inclinação da reta tangente** ao gráfico da função.
- Se \$$( f'(x) > 0 )\$$, a função está crescendo.
- Se \$$( f'(x) < 0 )\$$, a função está decrescendo.
- Se \$$( f'(x) = 0 )\$$, pode haver um **ponto de máximo, mínimo ou inflexão**.

---

## 📊 Regras de Derivação

1. **Constante:** \$$( f(x) = c \Rightarrow f'(x) = 0 )\$$
2. **Potência:** \$$( f(x) = x^n \Rightarrow f'(x) = n x^{n-1} )\$$
3. **Soma/Diferença:** \$$( (f \pm g)' = f' \pm g' )\$$
4. **Produto:** \$$( (f \cdot g)' = f'g + fg' )\$$
5. **Quociente:** \$$( \left( \frac{f}{g} \right)' = \frac{f'g - fg'}{g^2} )\$$
6. **Cadeia:** \$$( (f(g(x)))' = f'(g(x)) \cdot g'(x) )\$$

---

## 🧮 Exemplos de Derivação

1. \$$( f(x) = 3x^2 \Rightarrow f'(x) = 6x )\$$
2. \$$( f(x) = \sin(x) \Rightarrow f'(x) = \cos(x) )\$$
3. \$$( f(x) = \ln(x) \Rightarrow f'(x) = \frac{1}{x} )$$

---

## 💻 Derivadas no Octave/Scilab

```octave
syms x;
f = 3*x^2 + 2*x + 1;
df = diff(f, x);
disp(df);
```

## 💻 Derivadas no R (com pacote Ryacas)

```r
library(Ryacas)
x <- Sym("x")
f <- 3*x^2 + 2*x + 1
derivada <- Deriv(f, x)
Simplify(derivada)
```

---

## 🧠 Atividade Prática

### 1. Calcule a derivada das seguintes funções:
- a) \$$f(x) = 5x^3 - x^2 + 2x - 7 \$$
- b) \$$f(x) = \frac{x^2 + 1}{x} \$$
- c) \$$f(x) = e^{2x} \cdot \sin(x) \$$

### 2. Interprete o significado da derivada da função \$$f(x) = x^2 \$$ em \$$x = 3 \$$.

### 3. Escreva um script em Octave ou R que calcule e plote a derivada de \$$f(x) = x^3 - 6x^2 + 9x \$$.

---

## 📝 Tarefa para Casa

- Resolver os itens 1 e 2 da atividade prática no caderno.
- Submeter o script do item 3 via portal.
- Estudar as regras de derivação para aplicações futuras em otimização e máximos/mínimos.

---

## 🧭 Próxima Aula

- Aplicando derivadas para encontrar **pontos críticos**.
- **Máximos, mínimos e inflexões** em gráficos.
- Estudo de funções com derivadas de 1ª e 2ª ordem.

---

🚀 **Vamos seguir com o poder das derivadas no mundo real!**

