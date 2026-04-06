# Greedy Algorithms (Algoritmos Gananciosos)

Algoritmos gananciosos são uma classe de algoritmos que fazem escolhas localmente ótimas a cada passo, na esperança de encontrar uma solução globalmente ótima.

-   Em cada passo do algoritmo, fazemos uma escolha que parece a melhor no momento. Para isso, às vezes ordenamos o array para conseguir a próxima melhor escolha com rapidez. Também podemos usar uma fila de prioridade para obter o próximo item ótimo.
-   Depois de fazer uma escolha, verificamos as restrições, quando houver, e seguimos selecionando até encontrar a solução.
-   Algoritmos gananciosos nem sempre produzem a melhor solução. Por exemplo, em problemas de troco e mochila 0/1, a melhor solução costuma vir da Programação Dinâmica.
-   Alguns exemplos clássicos em que a estratégia gananciosa fornece a melhor solução são [Mochila fracionária](https://www.geeksforgeeks.org/dsa/fractional-knapsack-problem/), [algoritmo de Dijkstra](https://www.geeksforgeeks.org/dsa/dijkstras-shortest-path-algorithm-greedy-algo-7/), [algoritmo de Kruskal](https://www.geeksforgeeks.org/dsa/kruskals-minimum-spanning-tree-algorithm-greedy-algo-2/), [codificação Huffman](https://www.geeksforgeeks.org/dsa/huffman-coding-greedy-algo-3/) e [algoritmo de Prim](https://www.geeksforgeeks.org/dsa/prims-minimum-spanning-tree-mst-greedy-algo-5/).

## ****Noções básicas****

-   [Introdução](https://www.geeksforgeeks.org/dsa/introduction-to-greedy-algorithm-data-structures-and-algorithm-tutorials/)
-   [Estrutura geral](https://www.geeksforgeeks.org/dsa/greedy-algorithms-general-structure-and-applications/)

## ****Problemas fáceis****

-   [Mochila fracionária](https://www.geeksforgeeks.org/dsa/fractional-knapsack-problem/)
-   [Custo mínimo para reduzir o array a tamanho 1](https://www.geeksforgeeks.org/dsa/minimum-cost-make-array-size-1-removing-larger-pairs/)
-   [Rotações mínimas para cadeado circular](https://www.geeksforgeeks.org/dsa/minimum-rotations-unlock-circular-lock/)
-   [Máximo de números compostos para formar n](https://www.geeksforgeeks.org/dsa/split-n-maximum-composite-numbers/)
-   [Menor subconjunto com soma maior](https://www.geeksforgeeks.org/dsa/smallest-subset-sum-greater-elements/)
-   [Distribuir cookies](https://www.geeksforgeeks.org/dsa/assign-cookies/)
-   [Comprar o máximo de ações](https://www.geeksforgeeks.org/dsa/buy-maximum-stocks-stocks-can-bought-th-day/)
-   [Soma máxima de diferenças consecutivas](https://www.geeksforgeeks.org/dsa/maximize-sum-consecutive-differences-circular-array/)
-   [Custo mínimo e máximo para comprar tudo](https://www.geeksforgeeks.org/dsa/find-minimum-maximum-amount-buy-n-candies/)
-   [Número mínimo de notas para uma soma dada](https://www.geeksforgeeks.org/dsa/find-number-currency-notes-sum-upto-given-amount/)
-   [Soma máxima igual em três pilhas](https://www.geeksforgeeks.org/dsa/find-maximum-sum-possible-equal-sum-three-stacks/)

## ****Problemas médios****

-   [Seleção de atividades](https://www.geeksforgeeks.org/dsa/activity-selection-problem-greedy-algo-1/)
-   [Jump Game](https://www.geeksforgeeks.org/dsa/minimum-number-jumps-reach-endset-2on-solution/)
-   [Sequenciamento de tarefas](https://www.geeksforgeeks.org/dsa/job-sequencing-problem/)
-   [Fração egípcia](https://www.geeksforgeeks.org/dsa/merging-intervals/)
-   [Mesclar intervalos sobrepostos](https://www.geeksforgeeks.org/dsa/merging-intervals/)
-   [Número mínimo de termos de Fibonacci com soma K](https://www.geeksforgeeks.org/dsa/minimum-fibonacci-terms-sum-equal-k/)
-   [Plataformas mínimas](https://www.geeksforgeeks.org/dsa/minimum-number-platforms-required-railwaybus-station/)
-   [Custo mínimo para conectar n cordas](https://www.geeksforgeeks.org/dsa/connect-n-ropes-minimum-cost/)
-   [Número máximo de trens](https://www.geeksforgeeks.org/dsa/maximum-trains-stoppage-can-provided/)
-   [Particionar de 1 a n em dois grupos com diferença mínima](https://www.geeksforgeeks.org/dsa/divide-1-n-two-groups-minimum-sum-difference/)
-   [Cortar papel no menor número de quadrados](https://www.geeksforgeeks.org/dsa/paper-cut-minimum-number-squares/)
-   [Diferença mínima em grupos de tamanho dois](https://www.geeksforgeeks.org/dsa/minimum-difference-between-groups-of-size-two/)
-   [Máximo de clientes satisfeitos](https://www.geeksforgeeks.org/dsa/maximum-number-customers-can-satisfied-given-quantity/)
-   [Vértices iniciais mínimos para percorrer a matriz com restrições](https://www.geeksforgeeks.org/dsa/minimum-initial-vertices-traverse-whole-matrix-given-conditions/)
-   [Maior número palindrômico por permutação de dígitos](https://www.geeksforgeeks.org/dsa/largest-palindromic-number-permuting-digits/)
-   [Menor número com n dígitos e soma dos dígitos](https://www.geeksforgeeks.org/dsa/find-smallest-number-with-given-number-of-digits-and-digit-sum/)
-   [Maior subsequência lexicográfica](https://www.geeksforgeeks.org/dsa/lexicographically-largest-subsequence-every-character-occurs-least-k-times/)

## ****Problemas difíceis****

-   [Minimizar a diferença máxima de altura](https://www.geeksforgeeks.org/dsa/minimize-the-maximum-difference-between-the-heights/)
-   [Tornar o máximo igual com k atualizações](https://www.geeksforgeeks.org/dsa/maximum-elements-can-made-equal-k-updates/)
-   [Minimizar o fluxo de caixa entre amigos](https://www.geeksforgeeks.org/dsa/minimize-cash-flow-among-given-set-friends-borrowed-money/)
-   [Custo mínimo para cortar uma placa em quadrados](https://www.geeksforgeeks.org/dsa/minimum-cost-cut-board-squares/)
-   [Custo mínimo para processar m tarefas com custo de troca](https://www.geeksforgeeks.org/dsa/minimum-cost-to-process-m-tasks-where-switching-costs/)
-   [Tempo mínimo para concluir todos os trabalhos com restrições](https://www.geeksforgeeks.org/dsa/find-minimum-time-to-finish-all-jobs-with-given-constraints/)
-   [Minimizar a diferença máxima entre as alturas das torres](https://www.geeksforgeeks.org/dsa/minimize-the-maximum-difference-between-the-heights/)
-   [Número mínimo de arestas para inverter e criar um caminho da origem ao destino](https://www.geeksforgeeks.org/dsa/minimum-edges-reverse-make-path-source-destination/)
-   [Maior cubo formado ao deletar o mínimo de dígitos de um número](https://www.geeksforgeeks.org/dsa/find-largest-cube-formed-deleting-minimum-digits-number/)
-   [Reorganizar caracteres para que não haja adjacentes iguais](https://www.geeksforgeeks.org/dsa/rearrange-characters-string-no-two-adjacent/)
-   [Reorganizar uma string para que caracteres iguais fiquem a pelo menos d posições de distância](https://www.geeksforgeeks.org/dsa/rearrange-a-string-so-that-all-same-characters-become-at-least-d-distance-away/)

## ****Algoritmos gananciosos clássicos****

-   [Problema de seleção de atividades](https://www.geeksforgeeks.org/dsa/activity-selection-problem-greedy-algo-1/)
-   [Problema de sequenciamento de tarefas](https://www.geeksforgeeks.org/dsa/job-sequencing-problem/)
-   [Codificação Huffman](https://www.geeksforgeeks.org/dsa/huffman-coding-greedy-algo-3/)
-   [Decodificação Huffman](https://www.geeksforgeeks.org/dsa/huffman-decoding/)
-   [Problema de conexão de água](https://www.geeksforgeeks.org/dsa/water-connection-problem/)
-   [Trocas mínimas para balancear parênteses](https://www.geeksforgeeks.org/dsa/minimum-swaps-bracket-balancing/)
-   [Fração egípcia](https://www.geeksforgeeks.org/dsa/greedy-algorithm-egyptian-fraction/)
-   [Policiais pegam ladrões](https://www.geeksforgeeks.org/dsa/policemen-catch-thieves/)
-   [Problema de encaixe de prateleiras](https://www.geeksforgeeks.org/dsa/fitting-shelves-problem/)
-   [Atribuir ratos a buracos](https://www.geeksforgeeks.org/dsa/assign-mice-holes/)

## ****Problemas gananciosos em arrays****

-   [Subconjunto de produto mínimo de um array](https://www.geeksforgeeks.org/dsa/minimum-product-subset-array/)
-   [Maximizar a soma do array após K negações usando ordenação](https://www.geeksforgeeks.org/dsa/maximize-array-sum-after-k-negations-using-sorting/)
-   [Soma mínima do produto de dois arrays](https://www.geeksforgeeks.org/dsa/minimum-sum-product-two-arrays/)
-   [Soma mínima das diferenças absolutas de pares de dois arrays](https://www.geeksforgeeks.org/dsa/minimum-sum-absolute-difference-pairs-two-arrays/)
-   [Incremento/decremento mínimo para tornar o array não crescente](https://www.geeksforgeeks.org/dsa/minimum-incrementdecrement-to-make-array-non-increasing/)
-   [Ordenar array com reversão em torno do meio](https://www.geeksforgeeks.org/dsa/sorting-array-reverse-around-middle/)
-   [Soma das áreas de retângulos possíveis para um array](https://www.geeksforgeeks.org/dsa/sum-area-rectangles-possible-array/)
-   [Maior array lexicográfico com no máximo K trocas consecutivas](https://www.geeksforgeeks.org/dsa/largest-lexicographic-array-with-at-most-k-consecutive-swaps/)
-   [Partição em duas subarrays de comprimentos k e (N – k) com diferença máxima de somas](https://www.geeksforgeeks.org/dsa/partition-into-two-subarrays-of-lengths-k-and-n-k-such-that-the-difference-of-sums-is-maximum/)

## ****Problemas gananciosos em sistema operacional****

-   [Algoritmo First Fit em gerenciamento de memória](https://www.geeksforgeeks.org/dsa/program-first-fit-algorithm-memory-management/)
-   [Algoritmo Best Fit em gerenciamento de memória](https://www.geeksforgeeks.org/dsa/program-best-fit-algorithm-memory-management/)
-   [Algoritmo Worst Fit em gerenciamento de memória](https://www.geeksforgeeks.org/dsa/program-worst-fit-algorithm-memory-management/)
-   [Escalonamento Shortest Job First](https://www.geeksforgeeks.org/dsa/program-for-shortest-job-first-or-sjf-cpu-scheduling-set-1-non-preemptive/)
-   [Escalonamento de tarefas com duas tarefas permitidas por vez](https://www.geeksforgeeks.org/dsa/job-scheduling-two-jobs-allowed-time/)
-   [Algoritmo ótimo de substituição de páginas](https://www.geeksforgeeks.org/dsa/optimal-page-replacement-algorithm/)

## ****Problemas gananciosos em grafos****

-   [Árvore geradora mínima de Kruskal](https://www.geeksforgeeks.org/dsa/kruskals-minimum-spanning-tree-algorithm-greedy-algo-2/)
-   [Árvore geradora mínima de Prim](https://www.geeksforgeeks.org/dsa/prims-minimum-spanning-tree-mst-greedy-algo-5/)
-   [Árvore geradora mínima de Boruvka](https://www.geeksforgeeks.org/dsa/boruvkas-algorithm-greedy-algo-9/)
-   [Algoritmo de menor caminho de Dijkstra](https://www.geeksforgeeks.org/dsa/dijkstras-shortest-path-algorithm-greedy-algo-7/)
-   [Algoritmo de Dial](https://www.geeksforgeeks.org/dsa/dials-algorithm-optimized-dijkstra-for-small-range-weights/)
-   [Custo mínimo para conectar todas as cidades](https://www.geeksforgeeks.org/dsa/minimum-cost-connect-cities/)
-   [Introdução ao problema de fluxo máximo](https://www.geeksforgeeks.org/dsa/max-flow-problem-introduction/)
-   [Número de componentes cíclicos simples em um grafo não direcionado](https://www.geeksforgeeks.org/dsa/number-of-simple-cyclic-components-in-an-undirected-graph/)

## ****Algoritmo ganancioso aproximado para NP-completo****

-   [Cobertura de conjunto](https://www.geeksforgeeks.org/dsa/greedy-approximate-algorithm-for-set-cover-problem/)
-   [Empacotamento em bins](https://www.geeksforgeeks.org/dsa/bin-packing-problem-minimize-number-of-used-bins/)
-   [Coloração de grafos](https://www.geeksforgeeks.org/dsa/graph-coloring-set-2-greedy-algorithm/)
-   [K-centers](https://www.geeksforgeeks.org/dsa/greedy-approximate-algorithm-for-k-centers-problem/)
-   [Superstring mais curta](https://www.geeksforgeeks.org/dsa/shortest-superstring-problem/)
-   [Problema do caixeiro viajante usando MST](https://www.geeksforgeeks.org/dsa/approximate-solution-for-travelling-salesman-problem-using-mst/)

## ****Greedy para casos especiais de DP****

-   [Problema da mochila fracionária](https://www.geeksforgeeks.org/dsa/fractional-knapsack-problem/)
-   [Número mínimo de moedas necessárias](https://www.geeksforgeeks.org/dsa/greedy-algorithm-to-find-minimum-number-of-coins/)
