# 🐜 Ant Colony Optimization (ACO) - Problema do Caixeiro Viajante

**Resolução do Problema do Caixeiro Viajante (PCV) utilizando a meta-heurística de Otimização por Colônia de Formigas.**

Este projeto aplica a Inteligência de Enxames (Swarm Intelligence) inspirada no comportamento biológico das formigas para encontrar a menor rota possível que visite um conjunto de cidades e retorne ao ponto de partida. A meta-heurística ACO oferece uma excelente solução aproximada para o PCV, combatendo o problema da explosão combinatória das soluções de força bruta (O(n!)).

---

## 🔗 Links Rápidos

*   ▶️ **[Apresentação em Vídeo do Projeto](https://drive.google.com/file/d/1YjW_ZgfCuRx68O-hoGTG7DHKmfTtPOwg/view)**
*   💻 **[Testar Código no Google Colab](https://colab.research.google.com/drive/1uAyNXAW8ColWoMdEHYDS7jyuSpnMREEW)**

---

## 🧠 Como Funciona o Algoritmo (Intuição Biológica)

O algoritmo é inspirado na forma como as formigas reais encontram caminhos curtos entre a colônia e uma fonte de alimento. Elas forrageiam aleatoriamente, mas deixam um rastro químico (feromônio) no chão. Caminhos mais curtos são percorridos mais rapidamente, acumulando mais feromônio e atraindo mais formigas, o que reforça aquela rota até que a colônia convirja para o caminho ótimo.

No nosso código, a transição de uma cidade para outra é definida de forma probabilística baseada em dois fatores:
1.  **Feromônio ($\tau$):** O rastro deixado pelas "formigas artificiais" ao longo das iterações.
2.  **Heurística ($\eta$):** A atratividade do caminho (inversamente proporcional à distância: $\eta = 1/d$).

A cada iteração, os feromônios evaporam ligeiramente (para evitar convergência prematura para um caminho ruim) e recebem novos depósitos baseados na qualidade das rotas encontradas.

---

## ⚙️ Parâmetros Utilizados no Modelo

O projeto permite ajustes dinâmicos para observar como a colônia se comporta. A configuração padrão do script é:

*   **Iterações:** `200` (Critério de parada)
*   **Quantidade de Formigas:** `5`
*   **$\alpha$ (Alfa):** `1.0` (Peso da influência do feromônio)
*   **$\beta$ (Beta):** `1.0` (Peso da influência da heurística/distância)
*   **Taxa de Evaporação ($\rho$):** `0.4` (Taxa em que o rastro desaparece ao fim de uma iteração)
*   **Constante $Q$:** `100` (Quantidade de feromônio depositada)

O código contém um mecanismo de parada antecipada: se todas as rotas convergirem para o mesmo caminho na mesma iteração, o algoritmo finaliza antes do limite máximo.

---

## 📊 Visualização e Resultados

O código foi desenvolvido em um **Jupyter Notebook** (`.ipynb`). Ao final da execução, o algoritmo retorna as métricas de desempenho no terminal:
*   Melhor tour encontrado (lista de vértices).
*   Custo total da distância percorrida.
*   Número de iterações até a convergência.
*   Tempo computacional total de execução.

Além disso, utilizando a biblioteca `matplotlib.pyplot`, o script plota automaticamente um grafo exibindo todas as cidades no plano cartesiano e destacando a melhor rota conectando os vértices.

---

## 📂 Estrutura do Repositório

*   `notebooks/Caixeiro_Viajante_ACO.ipynb`: Script completo em Python contendo o modelo matemático, loop de otimização e a renderização do gráfico de saída.
*   `docs/Meta-Heurística Ant Colony Optimization.pdf`: Apresentação teórica detalhando a evolução histórica do ACO (Marco Dorigo), a matemática da tomada de decisão probabilística e comparações do modelo.
