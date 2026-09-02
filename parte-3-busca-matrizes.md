# Parte 3 — Investigação de Busca em Matrizes

*Responsável: Rhuann Pablo Ferreira Magalhães

**a) Por que encontrar um elemento no início exige menos operações?**
Porque como a busca vai olhando um por um desde o começo, se a gente der a sorte de achar o número logo na primeira posição, o programa já bate o olho, satisfaz a condição e para por ali mesmo. Aí gasta o mínimo de esforço.

**b) O que acontece quando o elemento procurado não existe?**
Nesse caso o algoritmo é obrigado a varrer a matriz inteira, de ponta a ponta, olhando 100% das posições só para ter certeza absoluta de que o valor realmente não estava lá.

**c) Qual é o pior caso da busca sequencial?**
É justamente quando o número não existe ou quando ele fica escondido bem na última coluna da última linha. Nesse caso o programa tem que fazer todas as comparações possíveis.

**d) Como o aumento das dimensões da matriz influencia a quantidade de operações?**
Muda tudo, porque quanto maior a matriz, mais elementos ela guarda. Se a gente pula de uma matriz de 10x10 (100 itens) para uma de 100x100 (10.000 itens), o número de comparações no pior caso dispara na mesma proporção.

**e) Qual a complexidade da busca sequencial em uma matriz com m linhas e n colunas?**
Fica O(m × n) no pior cenário — é necessário passar por cada linha (m) e cada coluna (n), então o tempo de execução depende diretamente da multiplicação do tamanho das duas dimensões.

---

## 💬 Comentários

<!--
Cada integrante deve comentar aqui (mesmo quem não fez esta parte).
Formato sugerido:

**[Seu Nome] — dd/mm:**
Seu comentário aqui.
-->
