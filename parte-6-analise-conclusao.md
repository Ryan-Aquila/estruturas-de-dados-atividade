# Parte 6 — Análise e Conclusão

*Responsável: Matheus Queirós de Souza Araújo*

Os experimentos realizados permitiram observar, na prática, como o tamanho das estruturas de dados influencia diretamente a quantidade de operações executadas pelos algoritmos. Tanto nos testes de ordenação quanto nos percursos de arrays e matrizes, estruturas maiores exigiram uma quantidade maior de comparações, acessos e movimentações.

**1. O aumento do tamanho da estrutura de dados influencia a quantidade de operações?**
Sim. Quanto maior a quantidade de elementos, maior tende a ser a quantidade de operações necessárias para processar a estrutura. Em uma matriz com m linhas e n colunas, um percurso completo precisa acessar m × n posições; nos algoritmos de ordenação, o aumento do número de elementos provoca crescimento na quantidade de comparações e movimentações. Os experimentos com arrays de 10, 20 e 1.000 elementos mostraram claramente essa diferença.

**2. Bubble Sort e Quick Sort crescem da mesma maneira quando o número de elementos aumenta?**
Não. O Bubble Sort possui crescimento quadrático (O(n²)) — para 1.000 elementos foram registradas 499.500 comparações. Já o Quick Sort, em condições médias favoráveis, apresenta complexidade aproximada de O(n log n): no mesmo experimento realizou apenas 10.982 comparações. Quanto maior a estrutura de dados, mais evidente fica a diferença de eficiência entre os dois.

**3. Por que analisar somente o resultado final da ordenação não é suficiente para comparar algoritmos?**
Porque ambos os algoritmos podem produzir corretamente a mesma lista ordenada — observando só o resultado, pareceria que tiveram o mesmo desempenho. A diferença está em como cada um chega ao resultado, por isso é necessário analisar: quantidade de comparações, quantidade de trocas/movimentações, crescimento do número de operações conforme a entrada aumenta, tempo necessário para estruturas maiores e complexidade do algoritmo.

## Conclusão Geral

A escolha de um algoritmo é muito importante, principalmente com grandes quantidades de dados. Os experimentos demonstraram que o aumento do tamanho das estruturas influencia diretamente a quantidade de operações necessárias.

O Bubble Sort, apesar de simples e fácil de entender, apresenta crescimento muito elevado na quantidade de operações, tornando-se pouco eficiente para grandes volumes de dados. O Quick Sort apresentou desempenho muito melhor nos testes, por utilizar uma estratégia de divisão do problema em partes menores.

Os exercícios com arrays e matrizes mostraram ainda que a organização dos dados influencia o processamento: em arrays, percursos simples apresentam crescimento linear O(n); em matrizes, o número de operações depende de linhas × colunas, resultando em O(m × n).

Assim, os experimentos comprovaram que não basta um algoritmo produzir o resultado correto: também é necessário analisar a quantidade de operações e como seu desempenho cresce conforme o volume de dados aumenta.

---

## 💬 Comentários

<!--
Cada integrante deve comentar aqui (mesmo quem não fez esta parte).
Formato sugerido:

**[Seu Nome] — dd/mm:**
Seu comentário aqui.
-->
