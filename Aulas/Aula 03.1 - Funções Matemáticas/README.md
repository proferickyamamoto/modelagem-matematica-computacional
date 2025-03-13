# Semana 3: Álgebra Linear e Funções de Diferentes Graus

## 🎯 Objetivos da Aula
- 📌 Introduzir as Funções do 1º, 2º Grau e de múltiplos graus e sua importância na modelagem matemática.
- 📌 Explorar **aplicações reais** dessas funções em diferentes cenários.
- 📌 Resolver problemas computacionais usando **Octave/Scilab e R**.
- 📌 Interpretar **gráficos de funções** e suas propriedades.
- 📌 Implementar modelos matemáticos aplicados à economia, engenharia e ciências de dados.

---

## 📌 Introdução às Funções

### 🔹 Função do 1º Grau
- 📊 Definição: **f(x) = ax + b**, onde:
  - 📈 **a** = coeficiente angular (taxa de variação).
  - 🎯 **b** = coeficiente linear (valor inicial).
- 📉 Representação gráfica: **reta no plano cartesiano**.
- 🏗 **Fundamentos:**
  - Utilizada para representar relações **proporcionais**.
  - Aplicada na análise de crescimento linear e previsões financeiras.
  - Apresenta **inclinação constante**.

### 🔹 Função do 2º Grau
- 📊 Definição: **f(x) = ax² + bx + c**, onde:
  - 📈 **a** = coeficiente de curvatura (define concavidade).
  - 🔼 Se **a > 0**, a parábola é **côncava para cima**.
  - 🔽 Se **a < 0**, a parábola é **côncava para baixo**.
- 📉 Representação gráfica: **parábola**.
- 🏗 **Fundamentos:**
  - Aplicada em **trajetórias físicas**, como o movimento de projéteis.
  - Modela **crescimento acelerado ou decaimento**.
  - Possui um **ponto de máximo ou mínimo**.

### 🔹 Funções de Graus Superiores
- 📊 Definição: **f(x) = aₙxⁿ + aₙ₋₁xⁿ⁻¹ + ... + a₁x + a₀**.
- 📈 Utilizadas para modelar comportamentos **não lineares e complexos**.
- 🏗 **Fundamentos:**
  - Aplicadas em modelagens **econômicas, científicas e engenharia**.
  - Permitem ajustes mais refinados para **dados experimentais**.
  - **Podem ter múltiplas inflexões**, pontos de máximo e mínimo.

---

## 📊 Representação Gráfica das Funções
- 📈 **Função do 1º Grau**: Sempre uma **reta** com inclinação constante.
- 📉 **Função do 2º Grau**: Sempre uma **parábola**, podendo ser côncava para cima ou para baixo.
- 🔄 **Funções de Graus Superiores**: Podem apresentar múltiplas **curvaturas e inflexões**.

---

## 🌍 Aplicações na Vida Real
- 🏡 **Função do 1º Grau:**
  - Modelagem de **valorização e depreciação** de bens.
  - Cálculo de **tarifas lineares** (como consumo de energia e água).
  - Precificação dinâmica no transporte (ex: Uber, táxi).

- 🏀 **Função do 2º Grau:**
  - **Trajetória de objetos**, como bolas em esportes.
  - **Variações de aceleração** em movimentos físicos.
  - Aplicação em **modelos de juros compostos**.

- 📊 **Funções de Graus Superiores:**
  - Modelagem de **crescimento de empresas**.
  - Estudo de tendências econômicas.
  - **Otimização em redes neurais e machine learning**.

---

## 🏆 Atividade Prática
### 🟢 Fácil
- 🏡 Um imóvel atualmente vale **R$ 700.000,00** e valoriza **R$ 50.000,00 por ano**. Qual será o valor após **10 anos**? (Função do 1º grau)

### 🟡 Intermediário
- 🏀 Um jogador arremessa uma bola que segue a função **h(t) = -5t² + 20t + 2**. Determine a altura máxima atingida. (Função do 2º grau)

### 🔴 Difícil
- 📊 Um economista deseja modelar a tendência de crescimento de uma empresa usando uma função cúbica. Como ele pode ajustar a função **f(x) = ax³ + bx² + cx + d** para prever o futuro da empresa?

---

## 🚀 Desafio Extra
- 🎯 Programe um código em **Octave ou R** para calcular e representar graficamente **uma trajetória parabólica** e **uma curva de crescimento cúbica**. Analise como os coeficientes afetam a forma da curva.

---

## 📊 Código no Octave/Scilab
```octave
x = -10:0.1:10;
y1 = 2*x + 3; % Função do 1º grau
y2 = -x.^2 + 4*x + 5; % Função do 2º grau
plot(x, y1, 'r', x, y2, 'b');
xlabel('x'); ylabel('f(x)');
title('Comparação entre funções do 1º e 2º grau');
grid on;
```

## 📈 Código no R
```r
x <- seq(-10, 10, by=0.1)
y1 <- 2*x + 3 # Função do 1º grau
y2 <- -x^2 + 4*x + 5 # Função do 2º grau
plot(x, y1, type='l', col='red', xlab='x', ylab='f(x)', main='Comparação entre funções')
lines(x, y2, col='blue')
grid()
```

---

## 📚 Resumo da Aula
- ✅ As **Funções do 1º e 2º Grau** são essenciais para modelagem matemática e computacional.
- ✅ Aplicamos essas funções para prever valores futuros e modelar movimentos e tendências.
- ✅ Utilizamos **Octave/Scilab e R** para representação computacional e análise gráfica.

---

## 📌 Tarefa para Casa
1. 📝 Resolva os exercícios propostos.
2. 📊 Utilize Octave ou R para **gerar gráficos** com as soluções.
3. 🔎 Analise como **mudanças nos coeficientes** alteram os gráficos das funções.

---

## 🎯 Próxima Aula
- 📌 **Introdução a Sistemas de Equações Lineares**.
- 📌 Resolvendo problemas com múltiplas variáveis.
- 📌 Aplicação em otimização e redes neurais.

---

🔥 **Vamos continuar explorando a matemática aplicada à computação!** 🚀

