![Algoritmo de Backtracking](../infograficos/Algoritmo%20de%20Backtracking.png)

## O que é Backtracking?

O backtracking (ou "tentativa e erro com retrocesso") é uma técnica algorítmica refinada para resolver problemas recursivamente. Em vez de gerar todas as soluções possíveis e depois testá-las (força bruta pura), o backtracking constrói uma solução candidata passo a passo. Assim que o algoritmo determina que a candidata atual não pode levar a uma solução válida (violando as restrições do problema), ele descarta essa opção ("volta atrás" ou faz o _backtrack_) e tenta o próximo caminho possível.

Imagine estar em um labirinto: você escolhe um caminho, segue até o fim. Se der em um beco sem saída, você volta até a última bifurcação e tenta um caminho diferente. Isso é o backtracking na prática!

### Árvore de Espaço de Estados e Poda (Pruning)

Todo problema de backtracking pode ser visualizado como uma grande **Árvore de Espaço de Estados**. A raiz é o estado inicial vazio, os ramos são as escolhas que você faz, e as folhas são as soluções completas (válidas ou inválidas). A grande magia do backtracking está na **Poda (Pruning)**: a capacidade de interromper a descida em um galho da árvore assim que percebemos que ele não trará frutos. Isso transforma algoritmos com complexidades astronômicas, como O(n!) ou O(2n), em soluções executáveis na prática.

## Links de Referências

1. [Introdução](https://www.geeksforgeeks.org/dsa/introduction-to-backtracking-2/)
2. [Backtracking vs Branch and Bound](https://www.geeksforgeeks.org/dsa/difference-between-backtracking-and-branch-n-bound-technique/)
