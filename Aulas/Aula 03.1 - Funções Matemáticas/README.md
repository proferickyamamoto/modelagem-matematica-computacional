# Semana 3: Álgebra Linear e Função do 1º Grau

## 🎯 Objetivos da Aula
- 📌 Introduzir a Função do 1º Grau e sua importância na modelagem matemática.
- 📌 Explorar **aplicações reais** da função linear em diferentes cenários.
- 📌 Resolver problemas computacionais usando **Octave/Scilab e R**.
- 📌 Interpretar **gráficos de funções lineares** e suas propriedades.
- 📌 Implementar modelos matemáticos aplicados à economia e engenharia.

---

## 📌 Introdução à Função do 1º Grau
- 📊 Definição: **f(x) = ax + b**, onde:
  - 📈 **a** = coeficiente angular (taxa de variação).
  - 🎯 **b** = coeficiente linear (valor inicial).
- 📉 Representação gráfica: **reta no plano cartesiano**.

---

## 📊 Representação Gráfica da Função Linear
- 📈 A **inclinação 'a'** determina a direção da reta:
  - 🔼 **Se 'a > 0'**, a função é **crescente**.
  - 🔽 **Se 'a < 0'**, a função é **decrescente**.
- 🎯 O coeficiente **'b'** define o ponto onde a reta cruza o **eixo y**.

---

## 🌍 Aplicações na Vida Real
- 🏡 **Valorização e depreciação** de bens (exemplo: imóveis e veículos).
- 💰 **Modelagem de custos e receitas** de empresas.
- 📊 **Previsão de crescimento ou queda** de clientes em negócios.
- 🚕 **Tarifa dinâmica de transporte** (Uber, Táxi, etc.).

---

## 🏆 Atividade Prática
### 🟢 Fácil
- 🏡 Um imóvel atualmente vale **R$ 700.000,00** e valoriza **R$ 50.000,00 por ano**. Qual será o valor após **10 anos**?

### 🟡 Intermediário
- 🚗 Um carro novo custa **R$ 100.000,00** e perde **R$ 5.000,00 por ano**. Qual será o valor após **8 anos**?

### 🔴 Difícil
- 📊 Uma empresa A tem **5150 clientes** e perde **150/mês**. Uma concorrente B tem **2000 clientes** e ganha **200/mês**. Após quantos meses a empresa B superará a A?

---

## 🚀 Desafio Extra
- 🎯 Programe um código em **Octave ou R** para calcular e representar graficamente um **modelo de depreciação** para um carro e um **modelo de crescimento** para uma empresa. Qual deles atinge o limite primeiro?

---

## 📊 Código no Octave/Scilab
```octave
t = 0:1:10;
V = 700000 + 50000 * t;
plot(t, V);
xlabel('Anos'); ylabel('Valor do Imóvel');
title('Valorização do Imóvel ao Longo do Tempo');
grid on;
```

## 📈 Código no R
```r
t <- seq(0, 10, by=1)
V <- 700000 + 50000 * t
plot(t, V, type='l', col='blue', xlab='Anos', ylab='Valor do Imóvel',
     main='Valorização de um Imóvel')
grid()
```

---

## 📚 Resumo da Aula
- ✅ A **Função do 1º Grau** é essencial para modelagem matemática e computacional.
- ✅ Aplicamos a função para prever valores futuros e modelar custos.
- ✅ Utilizamos **Octave/Scilab e R** para representação computacional.

---

## 📌 Tarefa para Casa
1. 📝 Resolva os exercícios propostos.
2. 📊 Utilize Octave ou R para **gerar gráficos** com as soluções.
3. 🔎 Analise como **mudanças nos parâmetros** alteram os gráficos.

---

## 🎯 Próxima Aula
- 📌 **Introdução a Sistemas de Equações Lineares**.
- 📌 Resolvendo problemas com múltiplas variáveis.
- 📌 Aplicação em otimização e redes neurais.

---

🔥 **Vamos continuar explorando a matemática aplicada à computação!** 🚀


