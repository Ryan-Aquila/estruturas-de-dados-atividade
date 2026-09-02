# Parte 1 — Pesquisa: Bubble Sort e Quick Sort

*Responsável: Ryan Áquila Damasceno Vieira*

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


import random

for tamanho in [10, 20, 5000]:
    lista_original = [random.randint(1, 5000) for _ in range(tamanho)]

    # --- BUBBLE SORT ---
    lista_bubble = list(lista_original)
    comparacoes_bubble = 0
    trocas_bubble = 0

    for etapa in range(tamanho):
        for posicao in range(tamanho - etapa - 1):
            comparacoes_bubble += 1
            if lista_bubble[posicao] > lista_bubble[posicao + 1]:
                # Inverte a posicao dos vizinhos
                lista_bubble[posicao], lista_bubble[posicao + 1] = lista_bubble[posicao + 1], lista_bubble[posicao]
                trocas_bubble += 1

    # --- QUICK SORT ---
    lista_quick = list(lista_original)
    comparacoes_quick = 0
    movimentacoes_quick = 0

    tarefas_pendentes = [(0, tamanho - 1)]

    while tarefas_pendentes:
        inicio, fim = tarefas_pendentes.pop()

        if inicio < fim:
            pivo = lista_quick[fim]
            indice_menores = inicio - 1

            for ponteiro in range(inicio, fim):
                comparacoes_quick += 1
                if lista_quick[ponteiro] <= pivo:
                    indice_menores += 1
                    lista_quick[indice_menores], lista_quick[ponteiro] = lista_quick[ponteiro], lista_quick[indice_menores]
                    movimentacoes_quick += 1

            # Posiciona o pivo no lugar correto
            lista_quick[indice_menores + 1], lista_quick[fim] = lista_quick[fim], lista_quick[indice_menores + 1]
            movimentacoes_quick += 1

            # Agenda a ordenacao das sublistas da esquerda e da direita
            posicao_pivo = indice_menores + 1
            tarefas_pendentes.append((inicio, posicao_pivo - 1))
            tarefas_pendentes.append((posicao_pivo + 1, fim))

    print(f"Array {tamanho}: Bubble({comparacoes_bubble} comp, {trocas_bubble} trocas) | Quick({comparacoes_quick} comp, {movimentacoes_quick} mov)")
---

## 💬 Comentários

Cada integrante deve comentar aqui (mesmo quem não fez esta parte).
Formato sugerido:

Ryan Áquila Damasceno Vieira 
Seu comentário aqui.
--> A tabela comparativa ficou bem clara pra visualizar as diferenças de complexidade entre os dois algoritmos O Bubble Sort é tipo aquele jeito "manual" de organizar as coisas comparando uma por uma, enquanto o Quick Sort já é mais esperto porque divide o problema em pedaços menores.
