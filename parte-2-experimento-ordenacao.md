# Parte 2 — Experimento de Ordenação

*Responsável: [nome de quem fez a Parte 2]*

Programa para comparar experimentalmente os algoritmos **Bubble Sort** e **Quick Sort**, com arrays de 10, 20 e 1.000 elementos.

## Tabela de Resultados

| Tamanho do Array | Bubble Sort — Comparações | Bubble Sort — Trocas | Quick Sort — Comparações | Quick Sort — Movimentações |
|---|---|---|---|---|
| 10 | 45 | 24 | 24 | 19 |
| 20 | 190 | 85 | 86 | 55 |
| 1.000 | 499.500 | 246.388 | 10.982 | 6.230 |

## Respostas do Questionário

**a) Qual algoritmo realizou menos operações para 10 elementos?**
O Quick Sort realizou menos comparações e menos movimentações/trocas no total.

**b) O comportamento permaneceu igual para 20 elementos?**
Sim, o Quick Sort continuou sendo mais eficiente, executando menos da metade das operações do Bubble Sort.

**c) O que aconteceu quando o tamanho aumentou para 1.000 elementos?**
A diferença tornou-se gigantesca. O Bubble Sort disparou para cerca de 499 mil operações no total, enquanto o Quick Sort precisou de apenas cerca de 10 mil operações.

**d) Qual algoritmo apresentou maior crescimento da quantidade de operações?**
O Bubble Sort. Seu número de operações cresceu de forma explosiva (ao quadrado do tamanho do array).

**e) Os resultados experimentais são coerentes com as complexidades teóricas estudadas?**
Sim. O Bubble Sort demonstrou na prática o comportamento quadrático (comparações multiplicam por 100 quando o array cresce 10 vezes), enquanto o Quick Sort manteve um crescimento controlado e muito mais rápido por dividir o problema em partes menores.

**f) Em qual situação você escolheria Bubble Sort?**
Apenas para fins didáticos, protótipos rápidos de teste ou listas extremamente pequenas (menos de 10 a 20 itens) que já estejam quase ordenadas.

**g) Em qual situação você escolheria Quick Sort?**
Para qualquer aplicação real com volume moderado ou grande de dados que precise de ordenação rápida e eficiente na memória.

---

## 💬 Comentários

<!--
Cada integrante deve comentar aqui (mesmo quem não fez esta parte).
Formato sugerido:

**[Seu Nome] — dd/mm:**
Seu comentário aqui.
-->
