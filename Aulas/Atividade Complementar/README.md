# Atividade Prática – Comparativo entre LU Parcial e LU Completo

## 🎯 Objetivos
- Compreender as diferenças entre **pivotamento parcial (PA = LU)** e **pivotamento completo (PAQ = LU)**.  
- Avaliar **estabilidade numérica**, **tempo de execução** e **erro residual** de cada método.  
- Desenvolver autonomia para implementar e comparar algoritmos de **fatoração LU**.

---

## 📘 Descrição da Atividade

Nesta atividade, você e seu grupo deverão:

1. Implementar ou adaptar funções para **LU com pivotamento parcial e completo**.  
2. Aplicar ambas as fatorações sobre as **mesmas matrizes de teste**.  
3. Resolver o sistema **Ax = b** em cada caso.  
4. Gerar uma **análise comparativa** de resultados.

---
## 🧮 Matrizes de Teste

### ✅ Matriz 1 – Bem condicionada

$$\[
A_1 =
\begin{bmatrix}
4 & 2 & 3 \\
2 & 2 & 2 \\
0 & 1 & 1
\end{bmatrix}, \quad
b_1 =

\begin{bmatrix}
1 \\ 2 \\ 3
\end{bmatrix}
\]$$

### ⚠️ Matriz 2 – Mal condicionada

A2 = [[1e-10, 1, 1],
      [1,      1, 2],
      [1,      2, 3]]
b2 = [1, 2, 3]
---

## 💻 Passo a Passo no Código

### 1️⃣ Funções base
Use ou adapte o código fornecido em aula para fatoração LU.

```python
def lu_pivot_parcial(A):
    # Implementação com pivotamento de linhas (PA = LU)
    # ...
    return P, L, U

def lu_pivot_completo(A):
    # Implementação com pivotamento de linhas e colunas (PAQ = LU)
    # ...
    return P, L, U, Q

2️⃣ Resolução de Ax = b

import numpy as np, time

# Exemplo de teste
A = np.array([[4,2,3],[2,2,2],[0,1,1]], float)
b = np.array([1,2,3], float)

# Parcial
t1 = time.time()
P, L, U = lu_pivot_parcial(A)
y = np.linalg.solve(L, P @ b)
x_parcial = np.linalg.solve(U, y)
t1 = time.time() - t1

# Completo
t2 = time.time()
P, L, U, Q = lu_pivot_completo(A)
y = np.linalg.solve(L, P @ b)
z = np.linalg.solve(U, y)
x_completo = Q @ z
t2 = time.time() - t2

3️⃣ Métricas para Comparação

erro_parcial = np.linalg.norm(A @ x_parcial - b)
erro_completo = np.linalg.norm(A @ x_completo - b)
dif = np.linalg.norm(x_parcial - x_completo)

print(f"Erro Parcial: {erro_parcial:.2e}")
print(f"Erro Completo: {erro_completo:.2e}")
print(f"Diferença entre soluções: {dif:.2e}")
print(f"Tempo Parcial: {t1:.5f}s  |  Tempo Completo: {t2:.5f}s")


---

📈 Análise Esperada

> Discussão (mínimo 5 linhas):
Explique o comportamento observado nos testes.

Qual método apresentou maior estabilidade?

Houve diferença de tempo?

Quando o pivotamento completo é realmente necessário?





---

🧾 Entrega

🧑‍🤝‍🧑 Grupos de até 4 alunos.

📥 Entregar relatório em PDF com:

Códigos e prints dos resultados.

Tabela comparativa (como a acima).

Conclusão textual.


⏱ Prazo: até o final da aula.

📤 Entregar pelo Portal do Aluno, com nomes e RMs no cabeçalho.



---

🧮 Avaliação (0–10 pontos)

Critério	Peso

Implementação correta e funcional	4 pts
Análise comparativa clara	4 pts
Organização e apresentação do relatório	2 pts



---

📚 Referências

Strang, G. Introduction to Linear Algebra.

Trefethen & Bau, Numerical Linear Algebra.

Golub & Van Loan, Matrix Computations.

MIT OpenCourseWare – 18.06 Linear Algebra (Lecture 22 – Full Pivoting).
