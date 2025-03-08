# 📌 Aula 02: Introdução a Octave/Scilab e R para Modelagem Matemática

📖 Objetivo da Aula
Nesta aula, vamos explorar as ferramentas Octave/Scilab e R, duas linguagens utilizadas para modelagem matemática e computacional.

📌 Octave/Scilab são alternativas livres ao MATLAB para computação numérica e engenharia.
📌 R é uma linguagem focada em estatística e ciência de dados.

✅ Objetivo: Aprender os conceitos básicos e realizar operações matemáticas essenciais.
🔹 O que são Octave/Scilab e R?
🔹 Octave/Scilab (Alternativas ao MATLAB)
✅ Ferramentas gratuitas para cálculos matemáticos, simulações e engenharia.
✅ Utilizadas em ciência de dados, modelagem estatística e aprendizado de máquina.
✅ Forte em: Álgebra linear, processamento de sinais, gráficos 2D/3D.

🔹 R (Statistical Computing)
✅ Criado para análise estatística e ciência de dados.
✅ Utilizado em modelagem estatística, aprendizado de máquina e manipulação de grandes volumes de dados.
✅ Forte em: Estatística, visualização de dados, aprendizado de máquina.

---
## 📢 Ambas as ferramentas são usadas para modelagem matemática!

📌 Instalando Octave/Scilab e R
🔹 Como instalar Octave?
Baixe o Octave no site oficial:
📎 https://www.gnu.org/software/octave/
Alternativamente, você pode usar Scilab, que tem interface gráfica e é mais próximo do MATLAB:
📎 https://www.scilab.org/download
🔹 Como instalar R?
Baixe o R no site oficial do CRAN:
📎 https://cran.r-project.org/
Para uma interface mais amigável, instale o RStudio:
📎 https://posit.co/download/rstudio-desktop/

---
## 🔹 Primeiros Comandos em Octave/Scilab e R
### 📌 Criando Variáveis e Operações Básicas

✅ Octave/Scilab
```octave
% Definição de variáveis
a = 5;
b = 10;
c = a + b; % Soma
d = a * b; % Multiplicação

% Criando vetores e matrizes
A = [1 2; 3 4]; % Matriz 2x2
B = inv(A); % Inversa da matriz A

% Exibindo resultados
disp(A);
disp(B);
```

✅ R
```r
# Definição de variáveis
a <- 5
b <- 10
c <- a + b  # Soma
d <- a * b  # Multiplicação

# Criando vetores e matrizes
A <- matrix(c(1,2,3,4), nrow=2, byrow=TRUE) # Matriz 2x2
B <- solve(A)  # Inversa da matriz A

# Exibindo resultados
print(A)
print(B)
```
📌 Observação:

No Octave/Scilab, usamos disp() para exibir valores.
No R, usamos print().

### 📌 Trabalhando com Matrizes
Octave/Scilab é altamente otimizado para operações com matrizes.

✅ Criando e Manipulando Matrizes em Octave/Scilab
```octave
A = [1 2; 3 4];  % Matriz 2x2
B = [5 6; 7 8];

C = A + B;  % Soma de matrizes
D = A * B;  % Multiplicação de matrizes
E = A .* B; % Multiplicação elemento a elemento
```
✅ Criando e Manipulando Matrizes em R
```r
A <- matrix(c(1,2,3,4), nrow=2, byrow=TRUE) # Matriz 2x2
B <- matrix(c(5,6,7,8), nrow=2, byrow=TRUE)

C <- A + B  # Soma de matrizes
D <- A %*% B  # Multiplicação de matrizes
E <- A * B  # Multiplicação elemento a elemento
```

---
### 📌 Diferença Importante:
No Octave/Scilab, A * B realiza multiplicação de matrizes.
No R, usamos %*% para multiplicação de matrizes, enquanto A * B realiza multiplicação elemento a elemento.

## 📊 Criando Gráficos Simples
### 📌 Gráficos são fundamentais para visualizar dados matemáticos.

✅ Criando um gráfico no Octave/Scilab
```octave
x = linspace(0, 10, 100); % Vetor de valores entre 0 e 10
y = sin(x); % Função seno

plot(x, y); % Criando gráfico
xlabel('x');
ylabel('y');
title('Gráfico da Função Seno');
grid on;
```

✅ Criando um gráfico no R
```r
x <- seq(0, 10, length=100) # Vetor de valores entre 0 e 10
y <- sin(x) # Função seno

plot(x, y, type="l", col="blue", main="Gráfico da Função Seno", xlab="x", ylab="y")
grid()
```
---
### 📌 Diferenças:

No Octave/Scilab, usamos linspace(), enquanto no R usamos seq().
plot(x, y) funciona em ambas as linguagens, mas no R precisamos definir type="l" para uma linha contínua.
🎯 Exercícios Práticos
Agora que aprendemos os conceitos básicos de Octave/Scilab ou R, tente resolver os seguintes desafios:

1️⃣ Criar uma matriz 3x3 e calcular sua inversa em Octave/Scilab ou R.
2️⃣ Gerar um gráfico de uma função quadrática $$/ 𝑦 = 𝑥^2 − 4𝑥 + 2 /$$
3️⃣ Criar um vetor de 100 números aleatórios e calcular sua média.

📌 Dica: Utilize as funções rand() no Octave/Scilab e runif() no R para gerar números aleatórios.

---
## 📢 Reflexão Final
🔹 Octave/Scilab e R são essenciais para modelagem matemática e computacional.
🔹 Octave/Scilab são poderosos para simulações e engenharia, enquanto R é excelente para estatística e análise de dados.
🔹 A matemática computacional nos permite visualizar e resolver problemas complexos de forma eficiente.

---
## 📌 Tarefa para a próxima aula: Instalar o Octave ou Scilab e R, e resolver os exercícios! 🚀

---
# 📌 Próxima Aula
Na próxima aula, vamos aprofundar no uso dessas ferramentas para resolver equações diferenciais e modelar sistemas reais!

📅 Autor: **Prof Erick Yamamoto**
📚 Disciplina: Modelagem Matemática e Computacional


