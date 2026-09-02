# Parte 5 — Cálculo da Média Geral

*Responsável: João Victor Lima de Freitas Carvalho*

```c
#define SENSORES 5
#define HORAS 24

int main() {
    float sensores[SENSORES][HORAS];
    float soma_sensor, maior_temp, soma_geral = 0.0, limite;
    int sensor_maior = 0, hora_maior = 0, acima_limite = 0;

    // Inicialização da matriz com valores simulados (15.0 a 35.0 °C)
    srand(time(NULL));
    for (int i = 0; i < SENSORES; i++) {
        for (int j = 0; j < HORAS; j++) {
            sensores[i][j] = 15.0 + ((float)rand() / RAND_MAX) * 20.0;
        }
    }

    // 1. Média de cada sensor, 2. Maior temperatura, 3. Sensor responsável,
    // 4. Horário e 5. Soma geral
    maior_temp = sensores[0][0];
    printf("=== 1. MEDIA DE CADA SENSOR ===\n");
    for (int i = 0; i < SENSORES; i++) {
        soma_sensor = 0.0;
        for (int j = 0; j < HORAS; j++) {
            float temp_atual = sensores[i][j];
            soma_sensor += temp_atual;
            soma_geral += temp_atual;

            // Atualiza o maior valor e seus índices
            if (temp_atual > maior_temp) {
                maior_temp = temp_atual;
                sensor_maior = i;
                hora_maior = j;
            }
        }
        printf("Sensor %d: %.2f °C\n", i + 1, soma_sensor / HORAS);
    }

    // Exibição dos dados consolidados (itens 2, 3, 4 e 5)
    printf("\n=== DETALHES GERAIS ===\n");
    printf("2. Maior temperatura registrada: %.2f °C\n", maior_temp);
    printf("3. Sensor responsável: Sensor %d\n", sensor_maior + 1);
    printf("4. Horário da ocorrência: %d:00h\n", hora_maior);
    printf("5. Média geral (120 medições): %.2f °C\n", soma_geral / (SENSORES * HORAS));

    // 6. Leituras acima de um limite informado pelo usuário
    printf("\n=== 6. VERIFICAÇÃO DE LIMITE ===\n");
    printf("Digite a temperatura limite para verificação (°C): ");
    scanf("%f", &limite);

    for (int i = 0; i < SENSORES; i++) {
        for (int j = 0; j < HORAS; j++) {
            if (sensores[i][j] > limite) {
                acima_limite++;
            }
        }
    }

    printf("Limite informado: %.2f °C\n", limite);
    printf("Quantidade de leituras acima do limite: %d\n", acima_limite);

    return 0;
}
```

## O que o código faz

O código cria uma matriz de 5 sensores por 24 horas, totalizando 120 medições de temperatura:

1. **Preenche a matriz** com temperaturas aleatórias entre 15°C e 35°C.
2. **Calcula a média de cada sensor**, usando suas 24 medições.
3. **Encontra a maior temperatura** registrada.
4. **Identifica qual sensor e qual horário** registraram essa maior temperatura.
5. **Calcula a média geral das 120 medições**, somando todas as temperaturas e dividindo por 5 × 24 = 120.
6. Pede uma **temperatura limite** ao usuário e conta quantas medições ficaram acima dela.

## Explicação — Leituras acima de um limite (loops aninhados)

**Por que são necessários loops aninhados?**
Porque os dados estão organizados em uma matriz bidimensional de sensores e horários. O primeiro `for` (índice `i`) percorre os sensores, enquanto o segundo `for` (índice `j`) percorre as horas de cada sensor. Assim é possível acessar e verificar cada medição individualmente.

**Qual é o papel dos índices [i][j]?**
Indicam a posição exata de cada temperatura dentro da matriz: `i` representa a linha (o sensor) e `j` representa a coluna (o horário da medição).

**Quantas posições da matriz são percorridas?**
A matriz possui 5 linhas (sensores) e 24 colunas (horas). Portanto, são percorridas 5 × 24 = 120 posições — todas as medições de temperatura.

**Qual é a relação entre número de linhas, colunas e quantidade de operações?**
A quantidade de posições percorridas é a multiplicação entre linhas e colunas: para m linhas e n colunas, o algoritmo percorre m × n posições. A complexidade desse percurso é O(m × n).

---

## 💬 Comentários

<!--
Cada integrante deve comentar aqui (mesmo quem não fez esta parte).
Formato sugerido:

**[Seu Nome] — dd/mm:**
Seu comentário aqui.
-->
