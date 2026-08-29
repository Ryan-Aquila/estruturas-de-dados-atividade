# Parte 1 — Pesquisa: Bubble Sort e Quick Sort

*Responsável: [nome de quem fez a Parte 1]*

## Bubble Sort

- **Como funciona:** Percorre a lista comparando itens vizinhos de dois em dois e invertendo suas posições caso estejam fora de ordem.
- **Lógica de ordenação:** O maior elemento vai sendo empurrado ("flutuando") até a última posição a cada rodada.
- **Melhor caso:** Lista já ordenada (precisa de apenas uma checagem geral).
- **Caso médio:** Lista com elementos desordenados aleatoriamente (muitas comparações e trocas).
- **Pior caso:** Lista totalmente invertida (exige o número máximo de repetições e trocas).
- **Vantagens:** Muito simples de programar, consome quase nada de memória extra e preserva a ordem de itens iguais.
- **Limitações:** Extremamente lento para listas médias ou grandes.
- **Uso adequado:** Fins didáticos e listas minúsculas ou que já estejam quase ordenadas.
- **Uso não recomendado:** Qualquer sistema com grande volume de dados ou que precise de velocidade.

## Quick Sort

- **Como funciona:** Escolhe um elemento de referência (pivô) e separa a lista em duas partes: itens menores de um lado e maiores do outro.
- **Lógica de ordenação:** Aplica a mesma divisão sucessivas vezes nas metades menores até que tudo esteja no lugar (Dividir para Conquistar).
- **Melhor caso:** O pivô escolhido divide a lista sempre em partes de tamanho igual.
- **Caso médio:** As divisões ocorrem de forma razoavelmente equilibrada na maioria das listas.
- **Pior caso:** O pivô é sempre o menor ou o maior elemento possível (comum em listas já ordenadas sem pivô aleatório).
- **Vantagens:** Um dos algoritmos mais rápidos do mundo real e não cria cópias da lista inteira na memória.
- **Limitações:** Pode ficar muito lento se a escolha do pivô for ruim e pode alterar a posição original de itens iguais.
- **Uso adequado:** Grandes conjuntos de dados na memória.
- **Uso não recomendado:** Sistemas que não toleram quedas repentinas de performance ou quando a ordem de itens duplicados precisa ser mantida.

## Tabela Comparativa

| Característica | Bubble Sort | Quick Sort |
|---|---|---|
| Princípio de funcionamento | Comparação direta e troca de elementos vizinhos | Divisão da lista em torno de um elemento pivô |
| Melhor caso | Lista já ordenada (1 varredura) | Pivô divide a lista exatamente no meio a cada etapa |
| Caso médio | Dados espalhados aleatoriamente | Pivô divide a lista em partes balanceadas |
| Pior caso | Lista totalmente invertida (decrescente) | Pivô é sempre o maior ou menor elemento |
| Uso de memória | Mínimo (apenas variáveis simples) | Baixo (memória apenas para o fluxo de divisões) |
| Vantagem principal | Simplicidade de código e lógica fácil | Altíssima velocidade para grandes volumes |
| Limitação principal | Lerdeza extrema em listas volumosas | Desempenho cai se o pivô for ruim |
| Aplicação recomendada | Aprendizado e listas quase prontas | Grandes listas de uso geral |

---

## 💬 Comentários

<!--
Cada integrante deve comentar aqui (mesmo quem não fez esta parte).
Formato sugerido:

**[Seu Nome] — dd/mm:**
Seu comentário aqui.
-->
