# Aula 11.2 – Revisão e Introdução à Álgebra Linear

## 🎯 Objetivos da Aula

- Relembrar conceitos de cálculo e modelagem do primeiro semestre.  
- Apresentar vetores, matrizes e sistemas lineares com base aplicada.  
- Mostrar aplicações em dados e gráficos 3D.  
- Preparar a base para operações com vetores e matrizes nas próximas aulas.

---

## 📘 Fundamento Teórico

### Revisão do primeiro semestre
- **Cálculo diferencial e integral:** limites, derivadas, integrais e suas aplicações.
- **Modelagem:** uso de funções lineares, quadráticas e cúbicas para simular fenômenos.

### Introdução à Álgebra Linear
- Vetores em $\mathbb{R}^2\$ e $\mathbb{R}^3$: definição, magnitude e direção.  
- Matrizes e suas operações básicas — soma, multiplicação, transposição.  
- Sistemas lineares: resolução via eliminação de Gauss e interpretação geométrica (Kaabar, 2014).

### Aplicações Científicas
- **Ciência de dados:** vetores representam atributos ou observações.  
- **Jogos 3D e visualização:** vetores definem posição, movimento e transformação.  
- **Engenharia:** resolução de sistemas para circuitos e estruturas (Boyd & Vandenberghe, 2018).

---

## 🧮 Exemplo Teórico de Cálculo

Considere duas forças vetoriais em \(\mathbb{R}^2\):

\$
\mathbf{F}_1 = \begin{bmatrix} 3 \\ 2 \end{bmatrix}, \quad
\mathbf{F}_2 = \begin{bmatrix} -1 \\ 4 \end{bmatrix}
\$

A força resultante é sua soma:

\$
\mathbf{F}_R = \mathbf{F}_1 + \mathbf{F}_2 = \begin{bmatrix} 2 \\ 6 \end{bmatrix}
\$

Interpretação: resultante de duas componentes perpendiculares.

---

## 💻 Exemplo Prático Aplicado

Em Octave ou R, calcule a soma dos vetores:

**Octave:**
```octave
F1 = [3; 2];
F2 = [-1; 4];
F = F1 + F2;
disp(F);


