# Lista de Exercícios

Esta lista foi elaborada para fortalecer a lógica de programação e o entendimento de manipulação de strings, matrizes e estruturas de dados avançadas. Os exercícios estão ordenados do nível básico ao avançado, cobrindo desde contagens simples até o uso de estruturas complexas como Árvores de Sufixos.

<details>
  <summary>Problemas Fáceis</summary>
<p>


### 1\. Substrings com apenas um Caractere Específico (Substrings with only Given Character)

**Descrição:** Dada uma string e um caractere específico, o objetivo é calcular o número total de substrings que podem ser formadas utilizando exclusivamente esse caractere. **Dica de Lógica:** Este problema utiliza conceitos de análise combinatória. Se você encontrar uma sequência contínua de n caracteres iguais, qualquer subsegmento dessa sequência também será válido. **Passo a Passo:**

1.  Receba a string e o caractere alvo (ex: 'a').
    
2.  Percorra a string e identifique blocos de sequências consecutivas do caractere.
    
3.  Para cada bloco de tamanho n, aplique a fórmula de soma de progressão aritmética: 2n×(n+1)​. Isso ocorre porque existem n substrings de tamanho 1, n−1 de tamanho 2, até 1 substring de tamanho n.
    
4.  Acumule os resultados de todos os blocos encontrados para obter o total final. **Input:** 
    ```
    str = "abbbc"
    ```
    , 
    ```
    char = 'b'
    ```
     15.*Output:** 
    ```
    6
    ```
     (As substrings são: "b", "b", "b", "bb", "bb", "bbb")

### 2\. Frequência de uma Substring (Frequency of a Substring)

**Descrição:** Determine a frequência total de uma substring (padrão) dentro de um texto base. Considere se o problema permite ou não sobreposição (neste caso, considere que permite). **Dica de Lógica:** Ao encontrar uma correspondência, não pule o padrão inteiro para a próxima busca; mova-se apenas um caractere adiante para capturar sobreposições como em "aaaa" com padrão "aa". **Passo a Passo:**

1.  Receba o texto principal e o padrão a ser buscado.
    
2.  Utilize um laço que percorra o texto do índice 0 até 
    ```
    comprimento_texto - comprimento_padrão
    ```
    .
    
3.  Em cada posição, compare a fatia (slice) do texto com o padrão.
    
4.  Se houver igualdade, incremente um contador. **Input:** 
    ```
    texto = "banana"
    ```
    , 
    ```
    padrão = "ana"
    ```
     19.*Output:** 
    ```
    2
    ```
     (Ocorrências nos índices 1 e 3)

### 3\. Verificar se Duas Strings são Rotações (Check if Two Strings Rotations)

**Descrição:** Verifique se uma string é uma rotação cíclica de outra. Por exemplo, "ebad" é uma rotação de "adeb". **Dica de Lógica:** Uma propriedade interessante das rotações é que, se você concatenar uma string com ela mesma, todas as rotações possíveis aparecerão como substrings dessa nova string. **Passo a Passo:**

1.  Valide se as duas strings possuem o mesmo comprimento. Se forem diferentes, a rotação é impossível.
    
2.  Crie uma string temporária resultante da concatenação da primeira string com ela mesma (
    ```
    s1 + s1
    ```
    ).
    
3.  Verifique se a segunda string (
    ```
    s2
    ```
    ) está contida nesta string temporária. **Input:** 
    ```
    s1 = "geeks"
    ```
    , 
    ```
    s2 = "eksge"
    ```
     21.*Output:** 
    ```
    True
    ```
     (Pois "eksge" está dentro de "geeksgeeks")

### 4\. Substrings com Todas as Vogais (Substrings with all Vowels)

**Descrição:** Identifique e conte quantas substrings contêm todas as cinco vogais ('a', 'e', 'i', 'o', 'u') pelo menos uma vez em qualquer ordem. **Dica de Lógica:** Este é um problema clássico de "janela deslizante" (sliding window) ou força bruta otimizada. A substring pode ter outros caracteres, mas as 5 vogais são obrigatórias. **Passo a Passo:**

1.  Itere sobre a string gerando todas as combinações de substrings possíveis.
    
2.  Para cada substring, utilize um conjunto (Set) ou uma tabela de frequência para armazenar os caracteres encontrados.
    
3.  Verifique se as 5 vogais básicas estão presentes no conjunto.
    
4.  Incremente o contador se a condição for satisfeita. **Input:** 
    ```
    str = "aeiouu"
    ```
     11.*Output:** 
    ```
    2
    ```
     ("aeiou" e "aeiouu")

### 5\. Encontrar todas as Ocorrências de um Subarray (Find all Occurrences of a Subarray)

**Descrição:** Aplique a lógica de busca de padrões a estruturas de dados numéricas. Encontre todos os índices iniciais onde um subarray específico aparece em um array principal. **Dica de Lógica:** Embora similar a strings, lembre-se que arrays podem conter tipos complexos, então a comparação deve ser exata elemento por elemento. **Passo a Passo:**

1.  Receba o array de dados e o array padrão (target).
    
2.  Percorra o array principal até que reste espaço suficiente para o padrão.
    
3.  Para cada posição, inicie uma comparação interna. Se encontrar uma divergência, interrompa a verificação atual e passe para o próximo índice.
    
4.  Salve os índices onde a verificação interna foi concluída com sucesso. **Input:** 
    ```
    arr = [1, 2, 3, 1, 2, 3]
    ```
    , 
    ```
    padrao = [1, 2]
    ```
     15.*Output:** 
    ```
    Índices: 0, 3
    ```

</p>
</details>

<details>
  <summary>Problemas Médios</summary>
<p>


### 6\. Busca de Substring de Anagramas (Anagram Substring Search)

**Descrição:** Encontre todas as ocorrências de um padrão e seus anagramas em um texto. Um anagrama é uma permutação dos caracteres do padrão original. **Dica de Lógica:** Em vez de gerar todas as permutações (que seria ineficiente), compare a contagem de frequência dos caracteres em uma janela fixa do tamanho do padrão. **Passo a Passo:**

1.  Crie uma tabela de frequência (ou array de 256 posições para ASCII) para o padrão.
    
2.  Defina uma janela deslizante no texto principal com o mesmo tamanho do padrão.
    
3.  Para cada posição da janela, compare a tabela de frequência da janela atual com a do padrão.
    
4.  Se as tabelas forem idênticas, armazene o índice inicial da janela. **Input:** 
    ```
    texto = "BACDGABCDA"
    ```
    , 
    ```
    padrao = "ABCD"
    ```
     15.*Output:** 
    ```
    Índices: 0, 5, 6
    ```

### 7\. Encontrar todos os Padrões de “1(0+)1” (Find all the patterns of “1(0+)1”)

**Descrição:** Identifique substrings que começam e terminam com '1' e possuem apenas caracteres '0' entre eles, sendo obrigatória a presença de ao menos um '0'. **Dica de Lógica:** Este problema pode ser resolvido com uma máquina de estados simples: procurando por um '1', depois por um ou mais '0's e, finalmente, outro '1'. **Passo a Passo:**

1.  Percorra a string bit a bit.
    
2.  Ao encontrar um '1', entre em um estado de busca por '0'.
    
3.  Continue avançando enquanto ler '0'. Se ler algo diferente de '0' ou '1', aborte a sequência atual.
    
4.  Se encontrar outro '1' imediatamente após um ou mais '0's, valide o padrão e recomece a busca a partir deste novo '1'. **Input:** 
    ```
    str = "1001010001"
    ```
     11.*Output:** 
    ```
    3
    ```
     ("1001", "101", "10001")

### 8\. Buscar uma Palavra em uma Grade 2D (Search a Word in a 2D Grid)

**Descrição:** Dada uma matriz de caracteres (grade), determine se uma palavra específica pode ser formada seguindo em linha reta em qualquer uma das 8 direções (horizontal, vertical e as 4 diagonais). **Dica de Lógica:** Pense em cada célula como um ponto de origem. Se a primeira letra coincide, você tem 8 vetores de direção para explorar. **Passo a Passo:**

1.  Itere por cada linha e coluna da matriz.
    
2.  Se 
    ```
    grid[i][j]
    ```
     for igual à primeira letra da palavra:
    
3.  Para cada uma das 8 direções (combinações de deslocamento em x e y de -1, 0, 1):
    
4.  Verifique se os caracteres subsequentes da palavra existem naquela direção sem sair dos limites da matriz. **Input:** 
    ```
    grid = [['G','E'],['S','K']]
    ```
    , 
    ```
    word = "GE"
    ```
     19.*Output:** 
    ```
    Encontrado em (0,0)
    ```

### 9\. Maior Prefixo que também é Sufixo (Longest prefix which is also suffix)

**Descrição:** Calcule o tamanho do maior prefixo próprio da string que também é um sufixo dela. Um prefixo próprio não pode ser a string inteira. **Dica de Lógica:** Este é o coração do algoritmo KMP (array LPS). Ele ajuda a evitar re-comparações desnecessárias. **Passo a Passo:**

1.  Use dois ponteiros ou um array de pré-processamento.
    
2.  Compare o caractere no índice 
    ```
    i
    ```
     com o caractere no índice 
    ```
    len
    ```
    .
    
3.  Se coincidirem, incremente o tamanho do prefixo/sufixo.
    
4.  Se falharem, retroceda o ponteiro de prefixo para a última posição de correspondência válida conhecida. **Input:** 
    ```
    str = "ababa"
    ```
     19.*Output:** 
    ```
    3
    ```
     (O prefixo "aba" é igual ao sufixo "aba")

### 10\. Maior Prefixo como Subsequência (Max length prefix as Subsequence)

**Descrição:** Dadas duas strings, determine qual o maior prefixo da String A que aparece como uma subsequência (não necessariamente contígua) na String B. **Dica de Lógica:** Diferente de substrings, subsequências mantêm a ordem relativa mas permitem "pular" caracteres no meio. **Passo a Passo:**

1.  Inicialize um contador para rastrear o progresso no prefixo da String A.
    
2.  Percorra a String B caractere por caractere.
    
3.  Se o caractere atual de B for igual ao caractere apontado no prefixo de A, incremente o contador e passe para o próximo caractere de A.
    
4.  O valor final do contador após percorrer B é o comprimento do maior prefixo. **Input:** 
    ```
    s1 = "digger"
    ```
    , 
    ```
    s2 = "biggerdiagram"
    ```
     15.*Output:** 
    ```
    3
    ```
     (O prefixo "dig" de "digger" pode ser formado com letras de "biggerdiagram" na ordem d-i-g)

### 11\. Contar String em um Array 2D (Count string in a 2D array)

**Descrição:** Conte todas as ocorrências de uma palavra em uma matriz de caracteres, onde o caminho pode mudar de direção (cima, baixo, esquerda, direita) a cada letra. **Dica de Lógica:** Use recursão com backtracking. Para evitar loops infinitos (usar a mesma célula duas vezes na mesma palavra), marque temporariamente as células visitadas. **Passo a Passo:**

1.  Para cada célula 
    ```
    (r, c)
    ```
     na matriz que corresponda à primeira letra da palavra:
    
2.  Inicie uma função recursiva que explora os 4 vizinhos.
    
3.  A cada passo bem-sucedido (letra coincide), continue para a próxima letra da palavra.
    
4.  Se chegar ao fim da palavra, retorne 1. Caso contrário, explore todos os caminhos e some os resultados. **Input:** 
    ```
    matriz
    ```
    , 
    ```
    palavra = "MAGIC"
    ```
     19.*Output:** 
    ```
    Total de caminhos válidos encontrados
    ```

</p>
</details>

<details>
  <summary>Problemas Difíceis</summary>
<p>


### 12\. Busca de Palavras em Ziguezague (Word Search with Zig-Zag)

**Descrição:** Similar à busca em matriz, mas com a regra de que a palavra pode "fazer curvas" em qualquer direção a cada caractere, sem nunca repetir uma célula já usada na formação daquela palavra específica. **Dica de Lógica:** A complexidade aqui é exponencial. O backtracking é essencial para explorar todas as ramificações de caminhos possíveis a partir de um ponto inicial. **Passo a Passo:**

1.  Implemente uma busca em profundidade (DFS).
    
2.  Mantenha um registro de células visitadas (pode ser uma matriz booleana ou alterando o caractere original temporariamente).
    
3.  Explore as adjacências. Se o caminho falhar, desmarque a célula atual (backtrack) para permitir que outros caminhos a utilizem.
    
4.  Retorne todas as coordenadas ou a contagem de sucessos. **Input:** 
    ```
    grid
    ```
    , 
    ```
    palavra
    ```
     15.*Output:** 
    ```
    True/False ou Lista de Caminhos
    ```

### 13\. Correspondência de Padrões com Curingas (Wildcard Pattern Matching)

**Descrição:** Verifique se uma string casa com um padrão que contém caracteres especiais: '?' (um caractere qualquer) e '\*' (zero ou mais caracteres quaisquer). **Dica de Lógica:** O asterisco é o maior desafio, pois ele pode representar uma string vazia, um caractere, ou muitos. Isso sugere uma abordagem de Programação Dinâmica. **Passo a Passo:**

1.  Crie uma tabela DP de tamanho 
    ```
    (texto_len+1) x (padrao_len+1)
    ```
    .
    
2.  ```
    dp[0][0]
    ```
     é verdadeiro (strings vazias casam).
    
3.  Preencha a primeira linha tratando padrões que começam com '\*'.
    
4.  Para cada 
    ```
    dp[i][j]
    ```
    :
    
      20.   Se 
          ```
          padrao[j-1]
          ```
           for '?' ou igual ao 
          ```
          texto[i-1]
          ```
          , herde o valor de 
          ```
          dp[i-1][j-1]
          ```
          .
          
      34.   Se for '_', o resultado é verdadeiro se 
          ```
          dp[i-1][j]
          ```
           (considerando '_' como um ou mais) ou 
          ```
          dp[i][j-1]
          ```
           (considerando '\*' como vazio) for verdadeiro. **Input:** 
          ```
          texto = "baaabab"
          ```
          , 
          ```
          padrão = "ba*ab"
          ```
           50.*Output:** 
          ```
          True
          ```

### 14\. Correspondência de Expressões Regulares (Regular Expression Matching)

**Descrição:** Implemente o casamento de expressões regulares simplificado com '.' (qualquer caractere único) e '_' (zero ou mais do elemento precedente). **Dica de Lógica:** A diferença crucial para o Wildcard é que 
```
a*
```
 significa vários 'a's, não vários caracteres quaisquer. O '_' modifica o caractere anterior. **Passo a Passo:**

1.  Use Programação Dinâmica. O estado 
    ```
    dp[i][j]
    ```
     indica se 
    ```
    texto[0...i]
    ```
     casa com 
    ```
    padrão[0...j]
    ```
    .
    
2.  Quando encontrar um '\*', você tem dois casos:
    
      17.   O caractere antes do '\*' não casa com o texto atual: ignore o par 
          ```
          caractere*
          ```
           (pule 2 posições no padrão).
          
      23.   O caractere antes do '_' casa: você pode ignorá-lo ou manter o padrão no '_' e avançar no texto. **Input:** 
          ```
          texto = "aa"
          ```
          , 
          ```
          padrão = "a*"
          ```
           31.*Output:** 
          ```
          True
          ```

### 15\. Busca de Padrões usando uma Trie de todos os Sufixos (Pattern Searching using a Trie of all Suffixes)

**Descrição:** Construa uma Trie (árvore de prefixos) contendo todos os sufixos de um texto. Use essa estrutura para verificar a existência de qualquer padrão no texto em tempo linear em relação ao tamanho do padrão. **Dica de Lógica:** Inserir todos os sufixos transforma uma busca de substring em uma busca de prefixo dentro da Trie, o que é extremamente rápido. **Passo a Passo:**

1.  Para uma string S, gere todos os sufixos: S\[0..n\],S\[1..n\],...,S\[n−1..n\].
    
2.  Insira cada um desses sufixos em uma Trie padrão.
    
3.  Para buscar um padrão P, percorra a Trie caractere por caractere de P.
    
4.  Se você conseguir chegar ao fim de P sem cair em um nó nulo, P existe no texto original. **Input:** 
    ```
    texto = "banana"
    ```
    , 
    ```
    padrão = "nan"
    ```
     15.*Output:** 
    ```
    True
    ```

### 16\. Aplicação de Árvore de Sufixos 1 – Verificação de Substring (Suffix Tree Application 1 – Substring Check)

**Descrição:** Implemente uma Árvore de Sufixos (uma Trie de sufixos comprimida onde arestas podem conter múltiplos caracteres) para realizar buscas ultra-rápidas. **Dica de Lógica:** Árvores de sufixos são estruturas poderosas. Enquanto a Trie de sufixos pode ocupar O(n2) de espaço, a Suffix Tree ocupa apenas O(n). **Passo a Passo:**

1.  Estude o Algoritmo de Ukkonen para construir a árvore em tempo O(n).
    
2.  Cada nó representa um ponto de ramificação onde sufixos divergem.
    
3.  Para checar uma substring, percorra os caracteres seguindo as arestas. Como uma aresta pode ter "apple", se sua busca for "app", você a encontrará no meio da aresta.
    
4.  Se a substring for totalmente consumida durante o percurso, retorne sucesso. **Input:** 
    ```
    texto = "geeksforgeeks"
    ```
    , 
    ```
    padrão = "for"
    ```
     15.*Output:** 
    ```
    True
    ```

</p>
</details>
