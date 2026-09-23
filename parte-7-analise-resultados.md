# Parte 7 — ANÁLISE DE ALGORITMOS DE ORDENAÇÃO

*Responsável: Ryan Áquila Damasceno Vieira 

## Etapa 3 — Tabela de Resultados

| Tamanho | Bubble Comp. | Bubble Trocas | Insertion Comp. | Insertion Mov. | Selection Comp. | Selection Trocas | Quick Comp. | Quick Mov. |
|---|---|---|---|---|---|---|---|---|
| 10 | 44 | 19 | 27 | 19 | 45 | 7 | 29 | 19 |
| 20 | 189 | 84 | 99 | 84 | 190 | 16 | 58 | 43 |
| 1.000 | 499.122 | 239.681 | 240.670 | 239.681 | 499.500 | 992 | 10.385 | 5.850 |

## Etapa 4 — Análise dos Resultados

**a) Qual algoritmo realizou o menor número de comparações para 10 elementos?**
O Insertion Sort, com apenas 27 comparações — bem abaixo dos outros três, que ficaram na faixa de 29 a 45.

**b) Qual algoritmo realizou menos trocas ou movimentações?**
O Selection Sort, com apenas 7 trocas. Isso acontece porque ele só troca uma vez por rodada (troca o menor elemento encontrado direto pro lugar certo), enquanto os outros movimentam elementos várias vezes durante o processo.

**c) O comportamento observado para 10 elementos permaneceu semelhante quando o tamanho aumentou para 20?**
Sim, a ordem de desempenho se manteve parecida: Insertion Sort continuou com menos comparações (99) e Selection Sort com menos trocas (16). A única mudança visível é que o Quick Sort já passou a se destacar mais em comparações (58, bem abaixo do Bubble e do Selection).

**d) O que aconteceu com a quantidade de operações quando o vetor passou para 1.000 elementos?**
A diferença ficou enorme. Bubble Sort e Selection Sort dispararam para perto de 500 mil comparações cada, o Insertion Sort ficou pela metade disso (240.670), e o Quick Sort continuou bem contido, com pouco mais de 10 mil comparações — quase 50 vezes menos que os algoritmos quadráticos.

**e) Bubble, Insertion e Selection têm complexidade O(n²), mas apresentaram exatamente a mesma quantidade de operações?**
Não. Embora os três cresçam na mesma ordem de grandeza (quadrática), os números concretos são bem diferentes: em 1.000 elementos, Selection e Bubble ficaram bem próximos em comparações (499.500 e 499.122, porque ambos sempre percorrem basicamente todos os pares), mas o Insertion Sort teve praticamente metade disso (240.670), já que ele para de comparar assim que encontra a posição correta do elemento, sem precisar varrer o restante da lista.

**f) Qual algoritmo apresentou maior crescimento no número de operações?**
O Selection Sort e o Bubble Sort, os dois com crescimento quadrático "cheio" — cresceram quase exatamente na proporção de n², já que praticamente sempre fazem todas as comparações possíveis independente da entrada.

**g) Como o comportamento experimental do Quick Sort se diferenciou dos demais?**
Ele foi disparado o mais eficiente com dados aleatórios (10.385 comparações contra quase 500 mil dos algoritmos quadráticos), mas se mostrou muito sensível à organização inicial dos dados — ao rodar o desafio adicional com um vetor **já ordenado**, o número de comparações do Quick Sort saltou para 499.500 (igual ao pior caso do Selection Sort!), porque o pivô escolhido (último elemento) passou a ser sempre o maior valor, quebrando a divisão equilibrada que o deixa rápido.

**h) Os resultados encontrados são coerentes com as complexidades teóricas estudadas?**
Sim. Bubble, Insertion e Selection confirmaram o comportamento O(n²): o número de operações cresce proporcionalmente ao quadrado do tamanho da entrada. O Quick Sort confirmou o comportamento O(n log n) no caso médio (dados aleatórios), mas também confirmou na prática o pior caso O(n²) quando o pivô é mal escolhido, como no teste com o vetor já ordenado.

**i) Qual dos quatro algoritmos você escolheria para ordenar milhares de pedidos na central de distribuição?**
O Quick Sort, mas com uma ressalva importante: usando uma escolha de pivô melhor (por exemplo, aleatório ou pela mediana de três valores), em vez de sempre pegar o último elemento. Isso porque o experimento mostrou que, com dados variados (a situação mais comum numa central de distribuição real), ele é disparado o mais rápido — só é preciso evitar o cenário em que os pedidos já chegam parcialmente ordenados, que é justamente o ponto fraco dessa implementação simples.

## Desafio Adicional (0,5) — Vetor aleatório vs. já ordenado vs. ordem inversa

*Teste realizado com vetor de 1.000 elementos.*

| Cenário | Bubble Comp. | Bubble Trocas | Insertion Comp. | Insertion Mov. | Selection Comp. | Selection Trocas | Quick Comp. | Quick Mov. |
|---|---|---|---|---|---|---|---|---|
| Aleatório | 499.094 | 246.827 | 247.819 | 246.827 | 499.500 | 991 | 11.300 | 6.199 |
| Já ordenado | 999 | 0 | 999 | 0 | 499.500 | 0 | 499.500 | 500.499 |
| Ordem inversa | 499.500 | 499.455 | 499.499 | 499.455 | 499.500 | 520 | 479.388 | 240.428 |

**A organização inicial dos dados interfere na quantidade de operações realizadas por todos os algoritmos da mesma maneira?**

Não, cada algoritmo reage de um jeito bem diferente à organização inicial:

- **Bubble Sort e Insertion Sort** amam um vetor já ordenado: caem de ~500 mil comparações para apenas 999 (praticamente O(n), já que só precisam de uma passada pra confirmar que está tudo certo) — mas sofrem muito com a ordem inversa, atingindo o teto de quase 500 mil operações, o pior caso absoluto dos dois.
- **Selection Sort é praticamente imune** à organização dos dados: ficou em 499.500 comparações nos três cenários, porque ele sempre varre o vetor inteiro procurando o menor elemento, não importa se já está ordenado ou não. Só o número de trocas varia.
- **Quick Sort é o mais sensível de todos**: teve ótimo desempenho no vetor aleatório (11.300 comparações), mas no vetor já ordenado explodiu para 499.500 comparações — virou o pior caso, porque o pivô fixo (último elemento) deixou de dividir a lista de forma equilibrada.

Isso mostra na prática que a complexidade teórica O(n²) ou O(n log n) descreve um **comportamento médio ou de pior caso**, mas o resultado real depende muito de como os dados chegam. Isso reforça a resposta do item (i): pra um sistema real, vale a pena tratar casos especiais (como usar um pivô aleatório no Quick Sort) para não cair no pior cenário justamente quando os dados já vêm parcialmente organizados.

---

## 💬 Comentários

<!--
Cada integrante deve comentar aqui (mesmo quem não fez esta parte).
Formato sugerido:

**[Seu Nome] — dd/mm:**
Seu comentário aqui.
-->
