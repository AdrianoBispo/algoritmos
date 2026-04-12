![O Paradigma Dividir para Conquistar](../infograficos/O%20Paradigma%20Dividir%20para%20Conquistar.png)

# Introdução ao algoritmo de dividir e conquistar

****Dividir e conquistar**** é uma técnica de resolução de problemas usada para dividir o problema principal em subproblemas, resolvê-los individualmente e depois combiná-los para obter a solução do problema original. Ela é especialmente útil quando o problema pode ser dividido em subproblemas independentes. Se houver subproblemas sobrepostos, usamos [Programação Dinâmica](https://www.geeksforgeeks.org/competitive-programming/dynamic-programming/).

## Funcionamento do algoritmo de dividir e conquistar

O algoritmo de dividir e conquistar pode ser dividido em três etapas: ****Dividir****, ****Conquistar**** e ****Mesclar****.

![Working-of-Divide-and-Conquer-Algorithm](https://media.geeksforgeeks.org/wp-content/uploads/20240501171531/Working-of-Divide-and-Conquer-Algorithm.webp "Clique para ampliar")

A imagem acima mostra o funcionamento usando o exemplo de [Merge Sort](https://www.geeksforgeeks.org/dsa/merge-sort/), que é usado para ordenação.

### ****1. Dividir:****

-   Quebrar o problema original em subproblemas menores.
-   Cada subproblema deve representar uma parte do problema geral.
-   O objetivo é dividir o problema até que não seja mais possível subdividi-lo.

No Merge Sort, dividimos o array de entrada em duas metades. Observe que a etapa de divisão no Merge Sort é simples, mas no [Quick Sort](https://www.geeksforgeeks.org/dsa/quick-sort-algorithm/), a divisão é crítica. No Quick Sort, particionamos o array em torno de um pivô.

### ****2. Conquistar:****

-   Resolver cada um dos subproblemas menores individualmente.
-   Se um subproblema for pequeno o suficiente (o chamado “caso base”), resolvemos diretamente, sem recursão adicional.
-   O objetivo é encontrar soluções independentes para esses subproblemas.

No Merge Sort, a etapa de conquista consiste em ordenar as duas metades individualmente.

### 3. Mesclar:

-   Combinar os subproblemas para obter a solução final do problema todo.
-   Depois que os subproblemas menores são resolvidos, combinamos suas soluções recursivamente para obter a solução do problema maior.
-   O objetivo é montar a solução do problema original mesclando os resultados dos subproblemas.

No Merge Sort, a etapa de mesclagem consiste em unir duas metades ordenadas para criar um único array ordenado. Observe que essa etapa é crítica no Merge Sort, mas no Quick Sort a mesclagem não faz nada, pois as duas partes já ficam ordenadas in place e a parte esquerda contém todos os elementos menores (ou iguais) que a parte direita.

## Características do algoritmo de dividir e conquistar

Esse algoritmo consiste em quebrar um problema em partes menores e mais gerenciáveis, resolver cada parte individualmente e depois combinar as soluções para resolver o problema original. Suas características são:

-   ****Divisão do problema****: a primeira etapa é quebrar o problema em subproblemas menores e mais fáceis de gerenciar. Essa divisão pode ser feita recursivamente até que os subproblemas fiquem simples o suficiente para serem resolvidos diretamente.
-   ****Independência dos subproblemas****: cada subproblema deve ser independente dos outros, ou seja, resolver um não deve depender da solução de outro. Isso permite processamento paralelo ou execução concorrente, o que pode gerar ganhos de eficiência.
-   ****Conquista de cada subproblema****: uma vez divididos, os subproblemas são resolvidos individualmente. Isso pode envolver aplicar a mesma abordagem recursivamente até que fiquem simples o suficiente, ou usar outro algoritmo ou técnica.
-   ****Combinação das soluções****: após resolver os subproblemas, suas soluções são combinadas para obter a solução do problema original. Essa combinação deve ser relativamente eficiente e direta.

## ****Exemplos de algoritmo de dividir e conquistar****

****1. Merge Sort:****

Podemos usar dividir e conquistar para ordenar o array em ordem crescente ou decrescente, dividindo-o em subarrays menores, ordenando esses subarrays e depois mesclando os arrays ordenados para obter o array original ordenado.

> Leia mais sobre [Merge Sort](https://www.geeksforgeeks.org/dsa/merge-sort/)

****2. Quicksort:****

É um algoritmo de ordenação que escolhe um elemento pivô e reorganiza os elementos do array de modo que todos os elementos menores que o pivô vão para a esquerda e todos os maiores vão para a direita. Por fim, o algoritmo ordena recursivamente os subarrays à esquerda e à direita do pivô.

> Leia mais sobre [Quick Sort](https://www.geeksforgeeks.org/dsa/quick-sort-algorithm/)

## Análise de complexidade do algoritmo de dividir e conquistar

> T(n) = aT(n/b) + f(n), onde n = tamanho da entrada, a = número de subproblemas na recursão, n/b = tamanho de cada subproblema. Assume-se que todos os subproblemas têm o mesmo tamanho. f(n) = custo do trabalho feito fora da chamada recursiva, incluindo o custo de dividir o problema e de mesclar as soluções. Consulte [Complexidade de tempo da recursão](https://www.geeksforgeeks.org/dsa/how-to-analyse-complexity-of-recurrence-relation/) para detalhes.

## Aplicações do algoritmo de dividir e conquistar

Alguns algoritmos clássicos que seguem essa estratégia são:

-   [****Busca binária****](https://www.geeksforgeeks.org/dsa/binary-search/) é um algoritmo eficiente para encontrar um elemento em um array ordenado, dividindo repetidamente o intervalo de busca pela metade. Ele compara o valor-alvo com o elemento do meio e reduz a busca para a metade esquerda ou direita, conforme a comparação.
-   [****Quicksort****](https://www.geeksforgeeks.org/dsa/quick-sort-algorithm/) é um algoritmo de ordenação que escolhe um pivô e reorganiza os elementos do array de modo que os menores fiquem à esquerda e os maiores à direita. Depois, ordena recursivamente os subarrays à esquerda e à direita.
-   [****Merge Sort****](https://www.geeksforgeeks.org/dsa/merge-sort/) também é um algoritmo de ordenação. Ele divide o array em duas metades, ordena-as recursivamente e, por fim, mescla as duas metades ordenadas.
-   [****Par mais próximo de pontos****](https://www.geeksforgeeks.org/dsa/closest-pair-of-points-using-divide-and-conquer-algorithm/) é o problema de encontrar o par de pontos mais próximo em um conjunto de pontos no plano x-y. O problema pode ser resolvido em O(n^2) calculando a distância entre todos os pares, mas a abordagem de dividir e conquistar resolve em O(N log N).
-   [****Algoritmo de Strassen****](https://www.geeksforgeeks.org/dsa/strassens-matrix-multiplication/) é um algoritmo eficiente para multiplicar duas matrizes. Um método simples usa 3 laços aninhados e tem custo O(n^3). O algoritmo de Strassen multiplica duas matrizes em O(n^2.8974).
-   [****Algoritmo de transformada rápida de Fourier (FFT) de Cooley–Tukey****](https://en.wikipedia.org/wiki/Cooley%E2%80%93Tukey_FFT_algorithm) é o algoritmo mais comum para FFT. Trata-se de um algoritmo de dividir e conquistar que funciona em O(N log N).
-   [****Algoritmo de Karatsuba para multiplicação rápida****](https://www.geeksforgeeks.org/dsa/karatsuba-algorithm-for-fast-multiplication-using-divide-and-conquer-algorithm/) realiza a multiplicação de duas strings binárias em O(n<sup>1,59</sup>), onde n é o comprimento da string binária.

## Vantagens do algoritmo de dividir e conquistar

-   ****Resolução de problemas difíceis:**** a técnica de dividir e conquistar é uma ferramenta conceitual para resolver problemas complexos, como o quebra-cabeça das Torres de Hanói. Ela exige quebrar o problema em subproblemas, resolvê-los individualmente e depois combinar os resultados.
-   ****Eficiência do algoritmo:**** a abordagem de dividir e conquistar frequentemente ajuda a descobrir algoritmos eficientes. Ela é a base de algoritmos como Quick Sort, Merge Sort e transformadas rápidas de Fourier.
-   ****Paralelismo:**** normalmente, esses algoritmos são usados em máquinas multiprocessadas com memória compartilhada, onde a comunicação entre processadores não precisa ser planejada com antecedência, porque subproblemas distintos podem ser executados em processadores diferentes.
-   ****Acesso à memória:**** esses algoritmos fazem uso eficiente de cache. Como os subproblemas são pequenos o suficiente para caber no cache e não depender da memória principal, o desempenho melhora. Algoritmos que usam cache de forma eficiente são chamados de cache oblivious.

## ****Desvantagens do algoritmo de dividir e conquistar****

-   ****Sobrecarga:**** dividir o problema em subproblemas e depois combinar as soluções pode exigir mais tempo e recursos. Essa sobrecarga pode ser significativa em problemas pequenos ou com solução simples.
-   ****Complexidade:**** dividir um problema em subproblemas menores pode aumentar a complexidade da solução geral, especialmente quando os subproblemas dependem uns dos outros e precisam ser resolvidos em uma ordem específica.
-   ****Dificuldade de implementação:**** alguns problemas são difíceis de dividir em subproblemas menores ou exigem um algoritmo complexo para isso. Nesses casos, implementar uma solução de dividir e conquistar pode ser desafiador.
-   ****Limitações de memória:**** ao trabalhar com grandes conjuntos de dados, a memória necessária para armazenar os resultados intermediários pode se tornar um fator limitante.

## ****Exemplos Práticos****

-   [Raiz quadrada de um inteiro](https://www.geeksforgeeks.org/dsa/square-root-of-an-integer/)
-   [Máximo e mínimo usando o mínimo de comparações](https://www.geeksforgeeks.org/dsa/maximum-and-minimum-in-an-array/)
-   [Frequência em array de intervalo limitado](https://www.geeksforgeeks.org/dsa/find-frequency-of-each-element-in-a-limited-range-array-in-less-than-on-time/)
-   [Problema do ladrilhamento](https://www.geeksforgeeks.org/dsa/tiling-problem-using-divide-and-conquer-algorithm/)
-   [Contagem de inversões](https://www.geeksforgeeks.org/dsa/inversion-count-in-array-using-merge-sort/)
-   [Problema do skyline](https://www.geeksforgeeks.org/dsa/the-skyline-problem-using-divide-and-conquer-algorithm/)
-   [Buscar em uma grade ordenada por linha e coluna](https://www.geeksforgeeks.org/dsa/search-in-a-row-wise-and-column-wise-sorted-2d-array-using-divide-and-conquer-algorithm/)
-   [Alocar o número mínimo de páginas](https://www.geeksforgeeks.org/dsa/allocate-minimum-number-pages/)
-   [Exponenciação modular](https://www.geeksforgeeks.org/dsa/modular-exponentiation-power-in-modular-arithmetic/)
