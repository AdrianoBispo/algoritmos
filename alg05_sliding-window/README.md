![Algoritmo de Janela Deslizante](../infograficos/Algoritmo%20de%20Janela%20Deslizante.png)

A técnica de janela deslizante é uma abordagem algorítmica poderosa usada para resolver problemas com arrays ou listas em que é necessário analisar uma subarray ou subsequência. Ela reduz a complexidade de tempo de problemas que normalmente envolveriam laços aninhados, mantendo uma “janela” de elementos e deslizando-a ao longo do array. A janela pode crescer ou encolher com base em certas condições, o que ajuda a otimizar a solução.

## Por que utilizar a técnica de Janela Flutuante?

O principal objetivo é evitar trabalho redundante. Em abordagens de força bruta, costumamos usar loops aninhados para avaliar todas as subarrays ou substrings possíveis, resultando em uma complexidade de tempo de O(N2) ou até O(N3). A Janela Flutuante reaproveita o trabalho feito na etapa anterior (adicionando o novo elemento que entra na janela e descartando o elemento que sai), reduzindo a complexidade temporal para O(N), ou seja, tempo linear.

### Como identificar um problema de Janela Flutuante?

Geralmente, você pode aplicar esse padrão quando o problema pede para:

1. Encontrar a **maior/menor** sequência, ou o **máximo/mínimo** valor.
    
2. A sequência precisa ser **contígua** (elementos adjacentes, como subarrays ou substrings).
    
3. O problema envolve **Arrays ou Strings**.

### Tipos de Janela

- **Janela Fixa:** O tamanho da janela é estático (ex: "encontre a soma de subarrays de tamanho K"). A janela se move uniformemente uma posição por vez.
    
- **Janela Dinâmica (Tamanho Variável):** O tamanho da janela cresce ou encolhe dependendo de uma condição específica (ex: "encontre a menor subarray cuja soma seja igual ou maior que X").

> Para saber mais: [Sliding Window Technique](https://www.geeksforgeeks.org/dsa/window-sliding-technique/)
