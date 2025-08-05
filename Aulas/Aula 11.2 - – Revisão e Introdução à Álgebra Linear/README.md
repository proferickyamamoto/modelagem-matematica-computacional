# Aula 11.2 – Revisão e Introdução à Álgebra Linear

---

## 🎯 Objetivos

* Relembrar conteúdos do 1º semestre: funções, limites, derivadas, integrais.
* Iniciar o estudo de vetores e matrizes em ℝ² e ℝ³.
* Compreender aplicações reais da álgebra linear.

---

## ✍️ Revisão do 1º Semestre

### Cálculo:

* **Limite**: aproximação de uma função em torno de um ponto. Base para definição de continuidade e derivada. (\[Stewart, 2013])
* **Derivada**: taxa de variação; inclinação da tangente. Utilizada para modelar crescimento, velocidade, taxa de variação de sinais.
* **Integral**: área sob a curva; soma acumulada. Relaciona-se com a derivada por meio do Teorema Fundamental do Cálculo.

### Modelagem:

* **Funções do 1º e 2º grau** aplicadas a crescimento, queda e trajetórias. Fundamentais na modelagem de fenômenos físicos e econômicos.
* **Cálculo de variação e otimização**: aplicação direta da derivada e das condições de máximos e mínimos locais.

### Softwares:

* Octave/Scilab e R para cálculos e visualizações. Ferramentas importantes para computação simbólica, gráficos e solução numérica de sistemas.

---

## 📘 Introdução à Álgebra Linear

A Álgebra Linear é o ramo da matemática que estuda vetores, espaços vetoriais, transformações lineares e sistemas lineares de equações. Sua importância está no fato de ser a linguagem matemática fundamental para diversas áreas da ciência e engenharia. (\[Boyd & Vandenberghe, 2018]; \[Strang, 2009])

### Conceitos iniciais:

* **Vetor**: entidade com magnitude e direção, representada como um ponto ou segmento orientado no espaço. Pode ser visualizado como um elemento de ℝⁿ.

  * Exemplo: $\vec{v} = [3, 4]$ → vetor em ℝ²
* **Matriz**: uma tabela de números reais dispostos em linhas e colunas. Representa transformações lineares ou coeficientes de sistemas.
* **Sistema linear**: conjunto de equações lineares que compartilham incógnitas. Representado como $A \cdot x = b$, onde A é uma matriz, x um vetor de incógnitas e b o vetor de resultados.

### Aplicações:

* **Física**: representação de forças, deslocamentos, velocidade, aceleração.
* **Computação**: manipulação de imagens, gráficos vetoriais, realidade aumentada.
* **Ciência de Dados**: vetores como representações de dados; matrizes como estruturas de entrada para modelos de aprendizado de máquina.

---

## 🧠 Exemplo Teórico de Vetores

Dados dois vetores:

* $F_1 = [3, 2]$
* $F_2 = [-1, 4]$

**Soma vetorial:**

$$
F_R = F_1 + F_2 = [3 + (-1), 2 + 4] = [2, 6]
$$

Essa soma representa a resultante de duas forças aplicadas em direções diferentes. A operação de soma vetorial é fundamental para combinar efeitos físicos em diferentes dimensões. (\[Kaabar, 2014])

---

## 📊 Exemplo Computacional (Octave/R)

### Octave:

```octave
F1 = [3; 2];
F2 = [-1; 4];
F_resultante = F1 + F2;
disp(F_resultante);
```

### R:

```r
F1 <- c(3, 2)
F2 <- c(-1, 4)
F_resultante <- F1 + F2
print(F_resultante)
```

---

## 🏫 Exercício em Sala

1. Calcule:

   * a) $A = [4, -2]$
   * b) $B = [-1, 3]$
   * c) $A + B$ e $A - B$
2. Modele uma situação real com vetores (ex: deslocamento, velocidade).
3. Teste os vetores em Octave ou R e discuta a interpretação.

---

## 🏠 Tarefa para Casa (Lista com 10 atividades)

1. Defina vetor e matriz com exemplos reais.
2. Calcule a soma: $[2, 3] + [5, -1]$
3. Calcule a diferença: $[7, -4, 2] - [1, 3, 5]$
4. Resolva um sistema 2x2 via substituição.
5. Represente uma matriz 2x3 e calcule sua transposta.
6. Modele uma regressão linear simples via sistema normal.
7. Use Octave para multiplicar duas matrizes 2x2.
8. Escreva um vetor coluna e vetor linha e faça seu produto.
9. Interprete o significado físico de um vetor nulo.
10. Crie um problema real que envolva vetores em ℝ².

---

## 📙 Referências

* Boyd, S. & Vandenberghe, L. *Introduction to Applied Linear Algebra*, Cambridge University Press, 2018.
* Kaabar, M. K. A. *A First Course in Linear Algebra*, ArXiv preprint arXiv:1807.09352, 2014.
* Axler, S. *Linear Algebra Done Right*, Springer.
* Stewart, J. *Cálculo*, Volume 1, Cengage Learning, 7ª edição.
* Strang, G. *Introduction to Linear Algebra*, Wellesley-Cambridge Press, 4th ed., 2009.

---

## 📅 Próxima Aula

* Produto escalar, norma e ângulo entre vetores.
* Interpretações geométricas e simulações computacionais.

---

**🚀 Vamos iniciar a jornada com vetores e matrizes!**
