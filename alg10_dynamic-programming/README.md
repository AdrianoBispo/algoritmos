![Programação Dinâmica ou DP](../infograficos/Programacao%20Dinamica.png)

A Programação Dinâmica é uma técnica algorítmica com as seguintes características.

- Ela é, em essência, uma otimização sobre a recursão pura. Sempre que encontramos uma solução recursiva com chamadas repetidas para as mesmas entradas, podemos otimizá-la com Programação Dinâmica.
- A ideia é simplesmente armazenar os resultados dos subproblemas para não precisar recalculá-los depois. Essa otimização normalmente reduz a complexidade de tempo de exponencial para polinomial.
- Alguns problemas populares resolvidos com Programação Dinâmica são [números de Fibonacci](https://www.geeksforgeeks.org/dsa/program-for-nth-fibonacci-number/), Diff Utility ([maior subsequência comum](https://www.geeksforgeeks.org/dsa/longest-common-subsequence-dp-4/)), [menor caminho de Bellman–Ford](https://www.geeksforgeeks.org/dsa/bellman-ford-algorithm-dp-23/), [Floyd Warshall](https://www.geeksforgeeks.org/dsa/floyd-warshall-algorithm-dp-16/), [distância de edição](https://www.geeksforgeeks.org/dsa/edit-distance-dp-5/) e [multiplicação de cadeia de matrizes](https://www.geeksforgeeks.org/dsa/matrix-chain-multiplication-dp-8/).

## 🧠 Como estudar Programação Dinâmica?

A Programação Dinâmica é uma técnica de otimização algorítmica baseada em dividir um problema complexo em subproblemas menores, resolvê-los uma única vez e armazenar seus resultados. Antes de começar os exercícios, lembre-se dos 4 passos fundamentais para resolver qualquer problema de DP:

1.  **Identificar se é um problema de DP:** O problema pede um valor ótimo (máximo, mínimo, maior, menor) ou o número total de formas de fazer algo? Ele possui "Sobreposição de Subproblemas" (o mesmo cálculo se repete) e "Subestrutura Ótima" (a solução global depende da solução dos subproblemas)?
    
2.  **Definir o Estado:** O que 
    ```
    dp[i]
    ```
     ou 
    ```
    dp[i][j]
    ```
     significa no mundo real do seu problema? Ex: "O lucro máximo possível até o dia i".
    
3.  **Equação de Transição:** Como o estado atual 
    ```
    dp[i]
    ```
     se relaciona com os estados passados (ex: 
    ```
    dp[i-1]
    ```
    , 
    ```
    dp[i-2]
    ```
    )?
    
4.  **Casos Base e Inicialização:** Qual é a fundação trivial do problema? (Ex: 
    ```
    dp[0] = 0
    ```
     para 0 itens na mochila).

Você pode implementar essas soluções usando a abordagem **Top-Down** (Recursão com Memoization) ou **Bottom-Up** (Iterativo com Tabulação/Arrays). Foque em dominar ambas!

## Conceitos Básicos

- [Introdução](https://www.geeksforgeeks.org/dsa/introduction-to-dynamic-programming-data-structures-and-algorithm-tutorials/)
- [Tabulação vs memorização](https://www.geeksforgeeks.org/dsa/tabulation-vs-memoization/)
- [Passos para resolver um problema de DP](https://www.geeksforgeeks.org/dsa/solve-dynamic-programming-problem/)
