import random
import sys
sys.setrecursionlimit(10000)

def bubble_sort(vetor):
    v = vetor.copy()
    comparacoes = 0
    trocas = 0
    n = len(v)
    for i in range(n - 1):
        trocou = False
        for j in range(n - 1 - i):
            comparacoes += 1
            if v[j] > v[j + 1]:
                v[j], v[j + 1] = v[j + 1], v[j]
                trocas += 1
                trocou = True
        if not trocou:
            break
    return comparacoes, trocas

def insertion_sort(vetor):
    v = vetor.copy()
    comparacoes = 0
    movimentacoes = 0
    for i in range(1, len(v)):
        chave = v[i]
        j = i - 1
        while j >= 0:
            comparacoes += 1
            if v[j] > chave:
                v[j + 1] = v[j]
                movimentacoes += 1
                j -= 1
            else:
                break
        v[j + 1] = chave
    return comparacoes, movimentacoes

def selection_sort(vetor):
    v = vetor.copy()
    comparacoes = 0
    trocas = 0
    n = len(v)
    for i in range(n - 1):
        menor = i
        for j in range(i + 1, n):
            comparacoes += 1
            if v[j] < v[menor]:
                menor = j
        if menor != i:
            v[i], v[menor] = v[menor], v[i]
            trocas += 1
    return comparacoes, trocas

def quick_sort(vetor):
    v = vetor.copy()
    contador = {"comparacoes": 0, "movimentacoes": 0}

    def particionar(baixo, alto):
        pivo = v[alto]
        i = baixo - 1
        for j in range(baixo, alto):
            contador["comparacoes"] += 1
            if v[j] <= pivo:
                i += 1
                v[i], v[j] = v[j], v[i]
                contador["movimentacoes"] += 1
        v[i + 1], v[alto] = v[alto], v[i + 1]
        contador["movimentacoes"] += 1
        return i + 1

    def ordenar(baixo, alto):
        if baixo < alto:
            p = particionar(baixo, alto)
            ordenar(baixo, p - 1)
            ordenar(p + 1, alto)

    if len(v) > 1:
        ordenar(0, len(v) - 1)
    return contador["comparacoes"], contador["movimentacoes"]


random.seed(42)

print("=== ETAPA 3 - RESULTADOS (vetores aleatorios) ===")
resultados = {}
for tamanho in [10, 20, 1000]:
    original = [random.randint(1, 10000) for _ in range(tamanho)]
    b = bubble_sort(original)
    ins = insertion_sort(original)
    sel = selection_sort(original)
    q = quick_sort(original)
    resultados[tamanho] = {"bubble": b, "insertion": ins, "selection": sel, "quick": q}
    print(f"\nTamanho {tamanho}:")
    print(f"  Bubble    -> comparacoes={b[0]:>8} | trocas={b[1]:>8}")
    print(f"  Insertion -> comparacoes={ins[0]:>8} | mov={ins[1]:>8}")
    print(f"  Selection -> comparacoes={sel[0]:>8} | trocas={sel[1]:>8}")
    print(f"  Quick     -> comparacoes={q[0]:>8} | mov={q[1]:>8}")

print("\n\n=== DESAFIO ADICIONAL (tamanho=1000: aleatorio vs ordenado vs invertido) ===")
tamanho = 1000
aleatorio = [random.randint(1, 10000) for _ in range(tamanho)]
ordenado = sorted(aleatorio)
invertido = sorted(aleatorio, reverse=True)

for nome, vet in [("Aleatorio", aleatorio), ("Ja ordenado", ordenado), ("Ordem inversa", invertido)]:
    b = bubble_sort(vet)
    ins = insertion_sort(vet)
    sel = selection_sort(vet)
    q = quick_sort(vet)
    print(f"\n{nome}:")
    print(f"  Bubble    -> comparacoes={b[0]:>8} | trocas={b[1]:>8}")
    print(f"  Insertion -> comparacoes={ins[0]:>8} | mov={ins[1]:>8}")
    print(f"  Selection -> comparacoes={sel[0]:>8} | trocas={sel[1]:>8}")
    print(f"  Quick     -> comparacoes={q[0]:>8} | mov={q[1]:>8}")
