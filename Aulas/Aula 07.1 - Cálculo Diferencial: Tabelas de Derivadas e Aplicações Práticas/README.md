# Aula 07.1: Tabelas de Derivadas e Aplicações Práticas

## 🎯 Objetivos das Aulas

- 📌 Apresentar as principais derivadas conhecidas utilizadas em cálculo.
- 📌 Interpretar o comportamento gráfico das funções com base em suas derivadas.
- 📌 Aplicar derivadas em problemas de crescimento, movimento e otimização.
- 📌 Utilizar tabelas para facilitar o reconhecimento e cálculo de derivadas.
- 📌 Resolver problemas práticos com auxílio de software computacional (Octave ou R).

---

## 🧮 Tabela de Derivadas Fundamentais

| Função $$f(x)$$                | Derivada $$f'(x)$$                |
|-------------------------------|-----------------------------------|
| $$c$$ (constante)            | $$0$$                             |
| $$x^n$$                      | $$nx^{n-1}$$                      |
| $$\sqrt{x}$$                 | $$\frac{1}{2\sqrt{x}}$$          |
| $$\frac{1}{x}$$              | $$-\frac{1}{x^2}$$                |
| $$e^x$$                      | $$e^x$$                           |
| $$a^x$$                      | $$a^x \ln(a)$$                    |
| $$\ln(x)$$                  | $$\frac{1}{x}$$                   |
| $$\log_a(x)$$              | $$\frac{1}{x\ln(a)}$$            |
| $$\sin(x)$$                | $$\cos(x)$$                       |
| $$\cos(x)$$                | $$-\sin(x)$$                      |
| $$\tan(x)$$                | $$\sec^2(x)$$                     |
| $$\sec(x)$$                | $$\sec(x)\tan(x)$$               |
| $$\csc(x)$$                | $$-\csc(x)\cot(x)$$              |
| $$\cot(x)$$                | $$-\csc^2(x)$$                    |

---

## 🧩 Tabela de Regras de Derivação

| Regra                                 | Fórmula                                                        |
|--------------------------------------|----------------------------------------------------------------|
| Soma ou Diferença                    | $$(f \pm g)' = f' \pm g'$$                                   |
| Produto                              | $$(fg)' = f'g + fg'$$                                        |
| Quociente                            | $$\left( \frac{f}{g} \right)' = \frac{f'g - fg'}{g^2}$$     |
| Cadeia (composição)                 | $$(f(g(x)))' = f'(g(x)) \cdot g'(x)$$                        |

---

## 💡 Aplicações Comuns de Derivadas

1. **Velocidade e aceleração:** derivada da posição e da velocidade, respectivamente.
2. **Crescimento populacional:** modelado por funções exponenciais e logarítmicas.
3. **Máximos e mínimos de lucros, área, custo, etc.:** utilizados em problemas de otimização.
4. **Taxas relacionadas:** exemplo clássico: volume e raio em uma esfera ou cone.

---

## 📈 Exemplos Resolvidos

### Exemplo 1: Derivada de função trigonométrica composta
Seja $$f(x) = \sin(3x)$$.
- Aplicamos a regra da cadeia:
$$f'(x) = \cos(3x) \cdot 3 = 3\cos(3x)$$

### Exemplo 2: Derivada de função logarítmica
Seja $$f(x) = \ln(x^2 + 1)$$
- Usando regra da cadeia:
$$f'(x) = \frac{1}{x^2 + 1} \cdot 2x = \frac{2x}{x^2 + 1}$$

### Exemplo 3: Derivada de produto
Seja $$f(x) = x^2 \cdot \ln(x)$$
- Usamos a regra do produto:
$$f'(x) = 2x\ln(x) + x^2 \cdot \frac{1}{x} = 2x\ln(x) + x$$

---

## 💻 Exemplo de uso no Octave

```octave
pkg load symbolic;
syms x;
f = x^2 * log(x);
f_derivada = diff(f, x);
disp(f_derivada);
```

---

## 🧠 Atividade Prática

### Parte 1 – Derivadas com base na tabela
1. Calcule a derivada de:
   - a) $$f(x) = \sqrt{x} + \ln(x)$$
   - b) $$f(x) = \frac{1}{x^2} + e^x$$
   - c) $$f(x) = \tan(x) \cdot \ln(x)$$

### Parte 2 – Aplicações práticas
2. Um carro tem sua posição descrita por $$s(t) = 5t^2 + 2t$$. Determine a velocidade e a aceleração em função do tempo.

3. Uma empresa tem receita dada por $$R(x) = -2x^2 + 400x$$. Qual o número de unidades que maximiza a receita?

---

## 📌 Tarefa para Casa

1️⃣ Resolver todas as derivadas da Parte 1 no caderno.  
2️⃣ Implementar no Octave os itens 2 e 3 da Parte 2.  
3️⃣ Justificar cada etapa com base nas regras da tabela de derivadas.

---

## 📚 Próxima Aula
- Integrais indefinidas: antiderivadas básicas
- Propriedades da integral
- Interpretação gráfica da área sob a curva

---

🚀 **Derivadas são a chave para entender como tudo muda! Vamos dominar isso com prática!**

