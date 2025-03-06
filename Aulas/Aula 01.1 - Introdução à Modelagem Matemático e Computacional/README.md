# 📌 Aula 01: Introdução à Modelagem Matemática e Computacional

## 📖 Objetivo
Nesta aula, vamos explorar os fundamentos da **Modelagem Matemática e Computacional**, entender sua importância na computação e apresentar exemplos práticos de aplicação.

---

## 🔍 O que é Modelagem Matemática?
Modelagem matemática é o **processo de representar um fenômeno do mundo real usando equações matemáticas**. Essas equações podem ser usadas para simular e prever o comportamento de sistemas complexos.

### 🎯 Exemplos de Modelagem na Computação:
✅ **Inteligência Artificial** – Redes neurais e aprendizado de máquina usam álgebra linear e estatística.  
✅ **Simulações Físicas** – Animações, gráficos de jogos e efeitos especiais usam equações diferenciais.  
✅ **Ciência de Dados** – Modelos estatísticos para análise de grandes volumes de dados.  
✅ **Epidemiologia** – Modelos matemáticos preveem a propagação de doenças.  

---

## 🏗️ Tipos de Modelagem Matemática

### 🔹 **Modelagem Determinística**
- Baseia-se em equações exatas.
- Produz sempre o mesmo resultado para os mesmos dados de entrada.
- Exemplo: Cálculo do movimento de um projétil usando as leis de Newton.

### 🔹 **Modelagem Estocástica**
- Usa **probabilidades** para lidar com incertezas.
- O resultado pode variar mesmo para os mesmos dados iniciais.
- Exemplo: Predição de preços no mercado financeiro.

---

## 📊 Exemplo Prático: Modelo SIR para Epidemias
Vamos modelar a propagação de uma doença em uma população usando o **Modelo SIR (Suscetíveis, Infectados, Recuperados)**.

### 🔢 Equações do Modelo:
$$\ 
\frac{dS}{dt} = - \beta S I 
\$$

$$\ 
\frac{dI}{dt} = \beta S I - \gamma I
\$$
$$\ 
\frac{dR}{dt} = \gamma I
\$$

Onde:  
- **S (Suscetíveis):** Indivíduos saudáveis que podem ser infectados.  
- **I (Infectados):** Indivíduos que têm a doença e podem transmiti-la.  
- **R (Recuperados):** Indivíduos que se recuperaram e não podem mais ser infectados.  
- **β (beta):** Taxa de transmissão da doença.  
- **γ (gamma):** Taxa de recuperação da doença.

### 📌 Código em Python:
```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import odeint

# Modelo SIR
def sir_model(y, t, beta, gamma):
    S, I, R = y
    dSdt = -beta * S * I
    dIdt = beta * S * I - gamma * I
    dRdt = gamma * I
    return [dSdt, dIdt, dRdt]

# Parâmetros do modelo
beta = 0.3  # Taxa de transmissão
gamma = 0.1  # Taxa de recuperação
y0 = [0.99, 0.01, 0]  # População inicial

# Tempo da simulação
t = np.linspace(0, 100, 1000)

# Resolvendo a equação diferencial
sol = odeint(sir_model, y0, t, args=(beta, gamma))

# Plotando os resultados
plt.figure(figsize=(10, 5))
plt.plot(t, sol[:, 0], 'b', label='Suscetíveis')
plt.plot(t, sol[:, 1], 'r', label='Infectados')
plt.plot(t, sol[:, 2], 'g', label='Recuperados')
plt.xlabel('Tempo')
plt.ylabel('Fração da População')
plt.legend()
plt.title('Modelo SIR de Propagação de Doenças')
plt.show()
```
---
### 🎯 Reflexão Final
Como podemos modificar esse modelo para incluir vacinação?
Como diferentes valores de β (taxa de transmissão) e γ (taxa de recuperação) afetam a propagação da doença?
Como a modelagem matemática pode ser aplicada em outros problemas computacionais, como previsão do clima ou inteligência artificial?
🚀 Próximos Passos
Na próxima aula, vamos aprender como usar MATLAB e R para resolver modelos matemáticos e aplicar esses conceitos de forma prática.

---
### 📌 Tarefa: Deixe o ambiente do Python no VSCode ou utilize o [Google Colab](https://colab.research.google.com/) em seu computador para a próxima aula!

---
📝 Autor: **Prof. Erick Toshio Yamamoto**
📅 Data: 06/03/2025
📌 Disciplina: Modelagem Matemática e Computacional
