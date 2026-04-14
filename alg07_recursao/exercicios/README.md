# Lista de Exercícios - Recursão

Este documento contém uma lista de desafios de programação focados no paradigma de **Recursão**. O objetivo é fortalecer a lógica de programação. Os exercícios são agnósticos de linguagem, ou seja, podem ser implementados na linguagem de sua preferência (C, C++, Java, Python, Javascript, etc.).

Siga o passo a passo lógico descrito em cada problema, prestando muita atenção na identificação do **caso base** (quando a recursão para) e no **passo recursivo** (como o problema é quebrado em partes menores).

<details>
  <summary>🟢 Nível 1 - Fácil</summary>

<p>

### 1\. [Fatorial](https://www.geeksforgeeks.org/dsa/program-for-factorial-of-a-number/ "null")

**Descrição:** O fatorial de um número não negativo 
```
n
```
 (denotado como 
```
n!
```
) é o produto de todos os números inteiros positivos menores ou iguais a 
```
n
```
. **Passo a Passo (Lógica):**

1.  **Caso Base:** Se 
    ```
    n
    ```
     for 0 ou 1, retorne 1.
    
2.  **Passo Recursivo:** Multiplique o número 
    ```
    n
    ```
     pelo resultado da função chamada com 
    ```
    n - 1
    ```
    .
-   **Entrada:** 
    ```
    5
    ```
    
-   **Saída:** 
    ```
    120
    ```
     (Pois 5 \* 4 \* 3 \* 2 \* 1 = 120)

### 2\. [Imprimir de 1 até n](https://www.geeksforgeeks.org/dsa/print-1-to-n-without-using-loops/ "null")

**Descrição:** Imprimir todos os números naturais começando de 1 até um dado número 
```
n
```
, sem utilizar laços de repetição (
```
for
```
, 
```
while
```
). **Passo a Passo (Lógica):**

1.  **Caso Base:** Se 
    ```
    n
    ```
     for 0, encerre a execução (retorne).
    
2.  **Passo Recursivo:** Chame a função recursivamente com 
    ```
    n - 1
    ```
    . _Após_ o retorno da chamada recursiva, imprima o valor atual de 
    ```
    n
    ```
    .
-   **Entrada:** 
    ```
    5
    ```
    
-   **Saída:** 
    ```
    1 2 3 4 5
    ```

### 3\. [Imprimir de n até 1](https://www.geeksforgeeks.org/dsa/print-n-to-1-without-loop/ "null")

**Descrição:** Imprimir todos os números naturais começando do número 
```
n
```
 até chegar ao número 1, sem utilizar laços de repetição. **Passo a Passo (Lógica):**

1.  **Caso Base:** Se 
    ```
    n
    ```
     for 0, encerre a execução.
    
2.  **Passo Recursivo:** _Primeiro_, imprima o valor atual de 
    ```
    n
    ```
    . Depois, chame a função recursivamente com 
    ```
    n - 1
    ```
    .
-   **Entrada:** 
    ```
    5
    ```
    
-   **Saída:** 
    ```
    5 4 3 2 1
    ```

### 4\. [Soma do array](https://www.geeksforgeeks.org/dsa/sum-array-elements-using-recursion/ "null")

**Descrição:** Dado um array (ou vetor) de inteiros, encontre a soma de todos os seus elementos utilizando recursão. **Passo a Passo (Lógica):**

1.  **Caso Base:** Se o tamanho do array for 0, retorne 0.
    
2.  **Passo Recursivo:** Retorne o valor do último elemento do array somado à chamada recursiva que passa o mesmo array, mas com o tamanho reduzido em 1 (
    ```
    tamanho - 1
    ```
    ).
-   **Entrada:** 
    ```
    [1, 2, 3, 4]
    ```
    
-   **Saída:** 
    ```
    10
    ```

### 5\. [Reverter uma string](https://www.geeksforgeeks.org/dsa/reverse-a-string-using-recursion/ "null")

**Descrição:** Inverter os caracteres de uma string utilizando recursão. **Passo a Passo (Lógica):**

1.  **Caso Base:** Se a string for vazia ou tiver tamanho 1, retorne a própria string.
    
2.  **Passo Recursivo:** Pegue o último caractere da string e concatene com a chamada recursiva que recebe o restante da string (excluindo o último caractere).
-   **Entrada:** 
    ```
    "recursao"
    ```
    
-   **Saída:** 
    ```
    "oasrucer"
    ```

### 6\. [Decimal para binário](https://www.geeksforgeeks.org/dsa/decimal-binary-number-using-recursion/ "null")

**Descrição:** Converter um número inteiro da base decimal para a representação binária correspondente. **Passo a Passo (Lógica):**

1.  **Caso Base:** Se 
    ```
    n
    ```
     for 0, retorne 0 (ou encerre a impressão). Se for lidar com string, pode retornar 
    ```
    ""
    ```
    .
    
2.  **Passo Recursivo:** Chame a função recursivamente passando 
    ```
    n / 2
    ```
     (divisão inteira). Em seguida, calcule o resto da divisão (
    ```
    n % 2
    ```
    ) e adicione/imprima ao final do resultado.
-   **Entrada:** 
    ```
    10
    ```
    
-   **Saída:** 
    ```
    1010
    ```

### 7\. [Soma dos dígitos](https://www.geeksforgeeks.org/dsa/sum-digit-number-using-recursion/ "null")

**Descrição:** Encontrar a soma dos dígitos de um número inteiro dado. **Passo a Passo (Lógica):**

1.  **Caso Base:** Se o número for 0, retorne 0.
    
2.  **Passo Recursivo:** Extraia o último dígito utilizando módulo de 10 (
    ```
    n % 10
    ```
    ) e some com o resultado da chamada recursiva passando o número sem o último dígito (divisão inteira por 10: 
    ```
    n / 10
    ```
    ).
-   **Entrada:** 
    ```
    1234
    ```
    
-   **Saída:** 
    ```
    10
    ```
     (Pois 1+2+3+4 = 10)

### 8\. [Mínimo e máximo do array](https://www.geeksforgeeks.org/dsa/recursive-programs-to-find-minimum-and-maximum-elements-of-array/ "null")

**Descrição:** Encontrar o menor e o maior valor dentro de um array de inteiros utilizando recursão. (Você pode fazer duas funções separadas, uma para cada). **Passo a Passo (Lógica para o Mínimo):**

1.  **Caso Base:** Se o tamanho do array for 1, retorne o único elemento.
    
2.  **Passo Recursivo:** Compare o último elemento do array atual com o resultado da chamada recursiva do array reduzido (
    ```
    tamanho - 1
    ```
    ). Retorne o menor dentre os dois.
-   **Entrada:** 
    ```
    [1, 4, 3, -5, -4, 8, 6]
    ```
    
-   **Saída:** Mínimo: 
    ```
    -5
    ```
    , Máximo: 
    ```
    8
    ```

### 9\. [Verificação de palíndromo](https://www.geeksforgeeks.org/dsa/recursive-function-check-string-palindrome/ "null")

**Descrição:** Verificar se uma dada string é um palíndromo (lê-se da mesma forma de trás para frente). **Passo a Passo (Lógica):**

1.  **Caso Base:** Se a string tiver tamanho 0 ou 1, retorne verdadeiro (
    ```
    True
    ```
    ).
    
2.  **Passo Recursivo:** Compare o primeiro e o último caractere. Se forem diferentes, retorne falso (
    ```
    False
    ```
    ). Se forem iguais, chame a função recursivamente passando a substring interior (cortando o primeiro e o último caracteres).
-   **Entrada:** 
    ```
    "radar"
    ```
    
-   **Saída:** 
    ```
    True
    ```
     (Verdadeiro)

</p>

</details>

<details>
  <summary>🟠 Nível 2 - Médio</summary>

<p>

### 10\. [Média do array](https://www.geeksforgeeks.org/dsa/mean-of-array-using-recursion/ "null")

**Descrição:** Calcular a média aritmética dos elementos de um array utilizando recursão. **Passo a Passo (Lógica):**

1.  **Caso Base:** Se o array tiver tamanho 1, retorne o próprio elemento (ou 
    ```
    elemento / tamanho original
    ```
     dependendo de como passar os parâmetros).
    
2.  **Passo Recursivo:** Para calcular recursivamente, pegue a média dos primeiros 
    ```
    n-1
    ```
     elementos, multiplique por 
    ```
    n-1
    ```
     para achar a soma deles, adicione o enésimo elemento, e divida por 
    ```
    n
    ```
    .
-   **Entrada:** 
    ```
    [1, 2, 3, 4, 5]
    ```
    
-   **Saída:** 
    ```
    3
    ```

### 11\. [Duplicatas adjacentes](https://www.geeksforgeeks.org/dsa/recursively-remove-adjacent-duplicates-given-string/ "null")

**Descrição:** Remover recursivamente todos os pares de caracteres iguais adjacentes em uma string até que não haja mais adjacências iguais. **Passo a Passo (Lógica):**

1.  **Caso Base:** Se a string estiver vazia ou contiver apenas 1 caractere, retorne a string.
    
2.  **Passo Recursivo:** Verifique o primeiro e o segundo caracteres. Se forem iguais, pule ambos e chame a recursão para o resto da string. Se forem diferentes, mantenha o primeiro caractere e anexe ao resultado da recursão iniciada a partir do segundo caractere. (Atenção: múltiplas passagens podem ser necessárias se novos pares se formarem).
-   **Entrada:** 
    ```
    "azxxzy"
    ```
    
-   **Saída:** 
    ```
    "ay"
    ```
     (azxxzy -> azzy -> ay)

### 12\. [Troca de moedas](https://www.geeksforgeeks.org/dsa/coin-change-dp-7/ "null")

**Descrição:** Dado um array com valores de diferentes moedas e um valor inteiro (troco), encontre quantas maneiras possíveis existem para dar o troco. Você possui infinitas moedas de cada valor. **Passo a Passo (Lógica):**

1.  **Caso Base:** Se o troco for 0, há 1 maneira (não dar nenhuma moeda). Se o troco for menor que 0 ou se acabarem os tipos de moedas, há 0 maneiras.
    
2.  **Passo Recursivo:** O total de maneiras é a soma de duas situações: (a) Considerar/Incluir a moeda atual (troco diminui, tipos de moeda continuam iguais) + (b) Excluir a moeda atual (troco continua igual, tipos de moeda diminuem).
-   **Entrada:** Moedas: 
    ```
    [1, 2, 3]
    ```
    , Troco: 
    ```
    4
    ```
    
-   **Saída:** 
    ```
    4
    ```
     (Soluções: {1,1,1,1}, {1,1,2}, {2,2}, {1,3})

### 13\. [Binário para Gray](https://www.geeksforgeeks.org/dsa/program-convert-binary-code-equivalent-gray-code-using-recursion/ "null")

**Descrição:** Converter uma string ou número da representação Binária para o Código de Gray correspondente. **Passo a Passo (Lógica):**

1.  **Caso Base:** O primeiro bit do código Gray é sempre igual ao primeiro bit do código binário. Se a string só tiver 1 bit, retorne ele mesmo.
    
2.  **Passo Recursivo:** Para o bit na posição 
    ```
    i
    ```
     do código Gray, faça a operação XOR entre os bits na posição 
    ```
    i
    ```
     e 
    ```
    i-1
    ```
     do código binário. Concatene o resultado com a chamada recursiva para as próximas posições.
-   **Entrada:** 
    ```
    "1010"
    ```
     (Binário)
    
-   **Saída:** 
    ```
    "1111"
    ```
     (Gray)

### 14\. [Maior substring palindrômica](https://www.geeksforgeeks.org/dsa/length-of-longest-palindromic-sub-string-recursion/ "null")

**Descrição:** Encontrar o comprimento da maior substring que forma um palíndromo dentro de uma string original. **Passo a Passo (Lógica):**

1.  **Caso Base:** Se o tamanho da string for 0, retorne 0. Se for 1, retorne 1. Se a string inteira testada for um palíndromo, retorne o tamanho dela.
    
2.  **Passo Recursivo:** Se os extremos não formarem palíndromos com o interior, a maior substring será o máximo entre a chamada recursiva removendo o primeiro caractere e a chamada recursiva removendo o último caractere.
-   **Entrada:** 
    ```
    "babad"
    ```
    
-   **Saída:** 
    ```
    3
    ```
     (As substrings "bab" ou "aba" são as maiores)

### 15\. [Torres de Hanói](https://www.geeksforgeeks.org/dsa/c-program-for-tower-of-hanoi/ "null")

**Descrição:** Mover 
```
n
```
 discos de um pino origem (A) para um pino destino (C), utilizando um pino auxiliar (B), seguindo as regras de que apenas um disco é movido por vez e nunca um disco maior pode ficar sobre um menor. **Passo a Passo (Lógica):**

1.  **Caso Base:** Se 
    ```
    n
    ```
     == 1, mova o disco do pino de origem direto para o destino e retorne.
    
2.  **Passo Recursivo:**
    
      9.   Mova 
          ```
          n-1
          ```
           discos da origem para o auxiliar usando o destino como apoio.
          
      15.   Imprima a movimentação do disco 
          ```
          n
          ```
           da origem para o destino.
          
      21.   Mova 
          ```
          n-1
          ```
           discos do auxiliar para o destino usando a origem como apoio.
-   **Entrada:** 
    ```
    3
    ```
     (Discos)
    
-   **Saída:** Mover disco 1 da haste A para a haste C Mover disco 2 da haste A para a haste B Mover disco 1 da haste C para a haste B Mover disco 3 da haste A para a haste C Mover disco 1 da haste B para a haste A Mover disco 2 da haste B para a haste C Mover disco 1 da haste A para a haste C

### 16\. [Calcular nCr](https://www.geeksforgeeks.org/dsa/program-to-calculate-value-of-ncr-using-recursion/ "null")

**Descrição:** Calcular o número de Combinações de 
```
n
```
 elementos agrupados 
```
r
```
 a 
```
r
```
 usando o triângulo de Pascal (propriedade recursiva). **Passo a Passo (Lógica):**

1.  **Caso Base:** Se 
    ```
    r
    ```
     == 0 ou 
    ```
    r
    ```
     == 
    ```
    n
    ```
    , o resultado é 1. Se 
    ```
    r
    ```
     > 
    ```
    n
    ```
    , o resultado é 0.
    
2.  **Passo Recursivo:** Use a fórmula matemática recursiva: 
    ```
    C(n, r) = C(n-1, r-1) + C(n-1, r)
    ```
    .
-   **Entrada:** 
    ```
    n = 5
    ```
    , 
    ```
    r = 2
    ```
    
-   **Saída:** 
    ```
    10
    ```

### 17\. [Permutações](https://www.geeksforgeeks.org/dsa/write-a-c-program-to-print-all-permutations-of-a-given-string/ "null")

**Descrição:** Imprimir todas as permutações (combinações de ordem de caracteres) possíveis de uma string. **Passo a Passo (Lógica):**

1.  **Caso Base:** Se a posição atual for igual ao último índice da string, imprima a string atual gerada.
    
2.  **Passo Recursivo:** Para cada caractere a partir da posição atual até o fim, troque (swap) o caractere na posição atual com o caractere do loop. Faça a chamada recursiva para a próxima posição. Após voltar da recursão, desfaça a troca (backtracking) para explorar outros caminhos.
-   **Entrada:** 
    ```
    "ABC"
    ```
    
-   **Saída:** 
    ```
    "ABC", "ACB", "BAC", "BCA", "CAB", "CBA"
    ```

### 18\. [Subconjuntos](https://www.geeksforgeeks.org/dsa/backtracking-to-find-all-subsets/ "null")

**Descrição:** Encontrar e imprimir todos os subconjuntos possíveis (Powerset) de um dado array de elementos. **Passo a Passo (Lógica):**

1.  **Caso Base:** Se o índice avaliado atingir o tamanho do array, imprima o subconjunto montado até ali.
    
2.  **Passo Recursivo:** Em cada passo da recursão, você tem duas escolhas: (a) Excluir o elemento do índice atual e avançar para o próximo. (b) Incluir o elemento do índice atual e avançar para o próximo.
-   **Entrada:** 
    ```
    [1, 2, 3]
    ```
    
-   **Saída:** 
    ```
    [], [1], [2], [3], [1, 2], [1, 3], [2, 3], [1, 2, 3]
    ```

### 19\. [Caminhos possíveis em matriz](https://www.geeksforgeeks.org/dsa/print-all-possible-paths-from-top-left-to-bottom-right-of-a-mxn-matrix/ "null")

**Descrição:** Contar (ou imprimir) o número de caminhos possíveis para sair do canto superior esquerdo (0,0) de uma matriz bidimensional 
```
m x n
```
 e chegar ao canto inferior direito (m-1, n-1), sendo permitido mover-se apenas para a Direita ou para Baixo. **Passo a Passo (Lógica):**

1.  **Caso Base:** Se atingir a última linha (
    ```
    m==1
    ```
    ) ou a última coluna (
    ```
    n==1
    ```
    ), só há 1 caminho possível para chegar ao fim (seguir sempre reto). Retorne 1.
    
2.  **Passo Recursivo:** Retorne a soma das duas ações possíveis: mover para a direita (reduzindo colunas da matriz não visitada) + mover para baixo (reduzindo as linhas da matriz não visitada). -> 
    ```
    caminhos(m-1, n) + caminhos(m, n-1)
    ```
    .
-   **Entrada:** Matriz 
    ```
    3 x 3
    ```
     (linhas=3, colunas=3)
    
-   **Saída:** 
    ```
    6
    ```

### 20\. [Combinações de parênteses](https://www.geeksforgeeks.org/dsa/print-all-combinations-of-balanced-parentheses/ "null")

**Descrição:** Dado 
```
n
```
 pares de parênteses, escrever uma função que gere todas as combinações de parênteses bem formados (balanceados). **Passo a Passo (Lógica):**

1.  **Caso Base:** Se o número de parênteses abertos e fechados processados na string atual forem iguais a 
    ```
    n
    ```
    , você encontrou uma solução válida. Imprima a string construída.
    
2.  **Passo Recursivo:** - Se a contagem de parênteses abertos for menor que 
    ```
    n
    ```
    , adicione 
    ```
    (
    ```
     e chame a recursão.
    
      17.   Se a contagem de parênteses fechados for menor que a contagem de abertos, adicione 
          ```
          )
          ```
           e chame a recursão.
-   **Entrada:** 
    ```
    3
    ```
    
-   **Saída:** 
    ```
    "((()))", "(()())", "(())()", "()(())", "()()()"
    ```

</p>

</details>

<details>
  <summary>🔴 Nível 3 - Difícil</summary>

<p>

### 21\. [Ordenar uma fila](https://www.geeksforgeeks.org/dsa/sort-the-queue-using-recursion/ "null")

**Descrição:** Ordenar os elementos de uma estrutura de dados de Fila (Queue) utilizando apenas as operações padrão de fila e recursão. **Passo a Passo (Lógica):**

1.  **Caso Base (Função Principal):** Se a fila estiver vazia, retorne.
    
2.  **Passo Recursivo:** Remova o primeiro elemento (dequeue). Chame a função recursiva para o restante da fila (isso esvaziará tudo). Quando a pilha de chamadas retornar, insira o elemento que foi removido na posição correta utilizando uma **função auxiliar recursiva**.
    
3.  **Lógica da Função Auxiliar de Inserção:** Se a fila está vazia ou o elemento a inserir é menor/maior que o elemento do fim, insira. Caso contrário, remova o elemento do início, chame recursão e re-insira no final.
-   **Entrada:** Fila: 
    ```
    [5, 1, 2, 6, 4]
    ```
     (Frente: 5)
    
-   **Saída:** Fila: 
    ```
    [1, 2, 4, 5, 6]
    ```

### 22\. [Ordenar uma pilha](https://www.geeksforgeeks.org/dsa/sort-a-stack-using-recursion/ "null")

**Descrição:** Ordenar uma Pilha (Stack) de forma crescente recursivamente, sem utilizar laços de repetição ou estruturas de dados extras. **Passo a Passo (Lógica):**

1.  **Caso Base (Função Principal):** Se a pilha estiver vazia, retorne.
    
2.  **Passo Recursivo:** Desempilhe o topo (pop). Ordene recursivamente o restante da pilha. Por fim, chame uma função auxiliar para inserir o elemento desempilhado na pilha já ordenada.
    
3.  **Lógica da Função Auxiliar:** Se a pilha estiver vazia ou o elemento a inserir for maior que o topo atual, insira (push) direto. Senão, desempilhe o topo, insira recursivamente e depois volte o antigo topo.
-   **Entrada:** Pilha: 
    ```
    [30, -5, 18, 14, -3]
    ```
     (Topo: 30)
    
-   **Saída:** Pilha: 
    ```
    [30, 18, 14, -3, -5]
    ```
     (Topo: 30)

### 23\. [Partições palindrômicas](https://www.geeksforgeeks.org/dsa/given-a-string-print-all-possible-palindromic-partition/ "null")

**Descrição:** Dada uma string, imprima todas as maneiras possíveis de cortá-la (particionar) de forma que cada parte isolada seja um palíndromo. **Passo a Passo (Lógica):**

1.  **Caso Base:** Se você consumiu toda a string original (índice inicial atingiu o final da string), imprima a lista de partições geradas.
    
2.  **Passo Recursivo:** Inicie um loop que testa cada corte possível (do índice atual até o final). Se a parte cortada for um palíndromo válido, adicione à lista atual de partições e faça a chamada recursiva para investigar as opções que restam do ponto do corte até a direita da string. Caso contrário, ignore e continue tentando crescer o corte. Retorne no backtracking.
-   **Entrada:** 
    ```
    "nitin"
    ```
    
-   **Saída:** 
    ```
    ["n", "i", "t", "i", "n"], ["n", "iti", "n"], ["nitin"]
    ```

### 24\. [Strings embaralhadas](https://www.geeksforgeeks.org/dsa/check-if-a-string-is-a-scrambled-form-of-another-string/ "null")

**Descrição:** Dadas duas strings (
```
s1
```
 e 
```
s2
```
), determine se 
```
s2
```
 é uma versão "embaralhada" de 
```
s1
```
. Embaralhar permite dividir a string em duas partes e trocar (fazer swap) essas partes (recursivamente). **Passo a Passo (Lógica):**

1.  **Caso Base:** Se as duas strings são iguais, retorne verdadeiro. Se os tamanhos forem diferentes, ou não tiverem as mesmas letras (pode fazer um short-circuit testando os caracteres), retorne falso.
    
2.  **Passo Recursivo:** Particione a string em todos os índices 
    ```
    i
    ```
     (de 1 até o tamanho-1). Para cada partição, a string 
    ```
    s2
    ```
     pode ser obtida trocando a ordem das duas metades originadas de 
    ```
    s1
    ```
     ou sem trocá-las. Faça o teste recursivo dessas duas possibilidades:
    
      17.   (a) Verificar se a parte não trocada corresponde (Ex: 
          ```
          esquerda1 == esquerda2
          ```
           e 
          ```
          direita1 == direita2
          ```
          ).
          
      27.   (b) Verificar se a parte sofreu o swap (Ex: 
          ```
          esquerda1 == direita2
          ```
           e 
          ```
          direita1 == esquerda2
          ```
          ).
-   **Entrada:** 
    ```
    s1 = "great"
    ```
    , 
    ```
    s2 = "rgeat"
    ```
    
-   **Saída:** 
    ```
    True
    ```
     (divida 'great' em 'gr' e 'eat', e troque letras em 'gr' para 'rg')

### 25\. [Problema de quebra de palavras](https://www.geeksforgeeks.org/dsa/word-break-problem-dp-32/ "null")

**Descrição:** Dada uma string contínua e um dicionário de palavras, descubra se é possível dividir essa string em uma sequência de uma ou mais palavras que existam no dicionário. **Passo a Passo (Lógica):**

1.  **Caso Base:** Se a string de entrada ficar vazia, significa que toda a divisão foi feita em blocos válidos. Retorne verdadeiro.
    
2.  **Passo Recursivo:** Gere todas as prefixes (prefixos) da string atual. Verifique no dicionário: se o prefixo gerado estiver presente nele, chame a função de recursão para o sufixo (o restante da string à direita). Se em algum desses recortes toda a string for validada e retornar verdadeiro, retorne verdadeiro.
-   **Entrada:** String: 
    ```
    "ilikesamsung"
    ```
    , Dicionário: 
    ```
    ["i", "like", "sam", "sung", "samsung"]
    ```
    
-   **Saída:** 
    ```
    True
    ```

### 26\. [Problema das N rainhas](https://www.geeksforgeeks.org/dsa/n-queen-problem-backtracking-3/ "null")

**Descrição:** Posicionar 
```
N
```
 rainhas de xadrez num tabuleiro 
```
N x N
```
 de forma que nenhuma delas possa atacar outra (não podem estar na mesma linha, coluna ou diagonal). **Passo a Passo (Lógica via Backtracking):**

1.  **Caso Base:** Se todas as 
    ```
    N
    ```
     rainhas já foram posicionadas com sucesso, salve ou imprima o tabuleiro e retorne verdadeiro.
    
2.  **Passo Recursivo:** Você posicionará as rainhas uma coluna de cada vez. Percorra todas as linhas da coluna em vigência. Para cada linha:
    
      9.   Verifique se a célula atual está a salvo de ataques das rainhas já colocadas.
          
      11.   Se sim, coloque a rainha ali, e chame a função recursivamente para a **próxima coluna**.
          
      13.   Se ao prosseguir a recursão falhar em alocar o restante, remova a rainha da célula atual (Backtrack) e tente a próxima linha.
-   **Entrada:** 
    ```
    4
    ```
     (Tabuleiro 4x4, 4 Rainhas)
    
-   **Saída:** Duas soluções de tabuleiro válidas possíveis (ex: rainhas nas células (0,1), (1,3), (2,0), (3,2)).

### 27\. [Resolvedor de Sudoku](https://www.geeksforgeeks.org/dsa/sudoku-backtracking-7/ "null")

**Descrição:** Dado um grid 
```
9 x 9
```
 parcialmente preenchido, encontrar uma solução que respeite as regras do Sudoku (números de 1 a 9 sem repetir em linhas, colunas ou no bloco de 
```
3 x 3
```
). **Passo a Passo (Lógica via Backtracking):**

1.  **Caso Base:** Percorra o tabuleiro. Se nenhuma célula vazia (denotada frequentemente por 0) for encontrada, você preencheu tudo corretamente, retorne verdadeiro.
    
2.  **Passo Recursivo:** Para a primeira célula vazia encontrada, tente colocar os números de 1 a 9. Para cada número testado:
    
      5.   Valide se as restrições são obedecidas na linha, coluna e bloco.
          
      7.   Se válido, insira na matriz e dispare a função recursivamente. Se essa chamada retornar verdadeiro, ótimo.
          
      9.   Se ela retornar falso depois (indicando que a inserção gerou um impasse futuro), retire o número da célula (coloque 0 de volta / backtrack) e tente o próximo número.
-   **Entrada:** Matriz 
    ```
    9x9
    ```
     com valores preenchidos parciais.
    
-   **Saída:** Matriz 
    ```
    9x9
    ```
     resolvida preenchida inteiramente (verdadeiro), ou falso se for impossível.

### 28\. [Passeio do cavalo](https://www.geeksforgeeks.org/dsa/the-knights-tour-problem/ "null")

**Descrição:** Determinar se é possível que um cavalo do xadrez visite todas as casas de um tabuleiro 
```
N x N
```
 exatamente uma vez, começando de uma posição (0,0). **Passo a Passo (Lógica via Backtracking):**

1.  **Caso Base:** O tabuleiro foi inteiramente visitado? (A variável controlando a contagem de movimentos em sequência é igual ao número de células do tabuleiro: 
    ```
    N*N
    ```
    ). Se sim, a jornada acabou e retorne verdadeiro.
    
2.  **Passo Recursivo:** O cavalo do xadrez tem até 8 movimentos possíveis (formato em L). Para cada movimento:
    
      9.   Verifique se as coordenadas X e Y da próxima jogada resultam num lugar vazio dentro dos limites do tabuleiro.
          
      11.   Se for seguro mover para lá, marque a célula com o número do movimento que está sendo registrado agora.
          
      13.   Faça a chamada recursiva passando para o próximo nível de tentativa do caminho.
          
      15.   Se a chamada recursiva falhar em prosseguir com sucesso, remova o registro da célula e tente a próxima variação dentre as 8 originais.
-   **Entrada:** Tabuleiro 
    ```
    8x8
    ```
    .
    
-   **Saída:** Matriz 
    ```
    8x8
    ```
     onde cada casa está marcada de 0 a 63 representando a ordem percorrida exata que soluciona o problema.

</p>

</details>
