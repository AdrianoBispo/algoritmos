# Lista de Exercícios - Algoritmos de Busca por Padrões (Patterns Searching)

Esta lista foi elaborada para fortalecer a lógica de programação e o entendimento de manipulação de strings, matrizes e estruturas de dados avançadas. Os exercícios estão ordenados do nível básico ao avançado, cobrindo desde contagens simples até o uso de estruturas complexas como Árvores de Sufixos.

<details>
    <summary>🟢 Nível 1 - Fácil</summary>
<p>

### 1. Substrings com apenas um Caractere Específico

**Descrição:** Dada uma string e um caractere específico, calcule o número total de substrings formadas exclusivamente por esse caractere.

**Dica de Lógica:** Uma sequência contínua de n caracteres iguais gera n×(n+1)/2 substrings válidas.

**Passo a Passo:**
1. Receba a string e o caractere alvo (ex: 'a')
2. Identifique blocos de sequências consecutivas do caractere
3. Para cada bloco de tamanho n, aplique: n×(n+1)/2
4. Some os resultados de todos os blocos

**Input:** `str = "abbbc"`, `char = 'b'`  
**Output:** `6` (Substrings: "b", "b", "b", "bb", "bb", "bbb")

### 2. Frequência de uma Substring

**Descrição:** Determine a frequência total de uma substring em um texto, considerando sobreposições.

**Dica de Lógica:** Ao encontrar uma correspondência, mova-se apenas um caractere adiante para capturar sobreposições (ex: "aaaa" com padrão "aa").

**Passo a Passo:**
1. Receba o texto principal e o padrão a ser buscado
2. Percorra o texto do índice 0 até `comprimento_texto - comprimento_padrão`
3. Em cada posição, compare a fatia do texto com o padrão
4. Se houver igualdade, incremente um contador

**Input:** `texto = "banana"`, `padrão = "ana"`  
**Output:** `2` (Ocorrências nos índices 1 e 3)

### 3. Verificar se Duas Strings são Rotações

**Descrição:** Verifique se uma string é uma rotação cíclica de outra (ex: "ebad" é rotação de "adeb").

**Dica de Lógica:** Se concatenar uma string com ela mesma, todas as rotações possíveis aparecem como substrings.

**Passo a Passo:**
1. Valide se as duas strings têm o mesmo comprimento
2. Crie uma string temporária: `s1 + s1`
3. Verifique se `s2` está contida nessa concatenação

**Input:** `s1 = "geeks"`, `s2 = "eksge"`  
**Output:** `True` ("eksge" está dentro de "geeksgeeks")

### 4. Substrings com Todas as Vogais

**Descrição:** Conte quantas substrings contêm todas as cinco vogais ('a', 'e', 'i', 'o', 'u') pelo menos uma vez.

**Dica de Lógica:** Problema clássico de "janela deslizante" ou força bruta otimizada.

**Passo a Passo:**
1. Itere sobre a string gerando todas as substrings possíveis
2. Para cada substring, use um conjunto para armazenar caracteres
3. Verifique se as 5 vogais estão presentes
4. Incremente o contador se a condição for satisfeita

**Input:** `str = "aeiouu"`  
**Output:** `2` (Substrings: "aeiou" e "aeiouu")

### 5. Encontrar todas as Ocorrências de um Subarray

**Descrição:** Encontre todos os índices iniciais onde um subarray específico aparece em um array principal.

**Dica de Lógica:** Compare elemento por elemento; arrays podem conter tipos complexos.

**Passo a Passo:**
1. Receba o array de dados e o array padrão (target)
2. Percorra o array principal até que reste espaço suficiente
3. Para cada posição, compare elemento por elemento
4. Salve os índices onde a verificação foi bem-sucedida

**Input:** `arr = [1, 2, 3, 1, 2, 3]`, `padrao = [1, 2]`  
**Output:** `Índices: 0, 3`

</p>
</details>

<details>
    <summary>🟠 Nível 2 - Médio</summary>
<p>

### 6. Busca de Substring de Anagramas

**Descrição:** Encontre todas as ocorrências de um padrão e seus anagramas em um texto.

**Dica de Lógica:** Compare a contagem de frequência dos caracteres em uma janela fixa, em vez de gerar permutações.

**Passo a Passo:**
1. Crie uma tabela de frequência para o padrão
2. Defina uma janela deslizante com o tamanho do padrão
3. Para cada posição, compare as frequências
4. Armazene os índices onde as tabelas forem idênticas

**Input:** `texto = "BACDGABCDA"`, `padrao = "ABCD"`  
**Output:** `Índices: 0, 5, 6`

### 7. Encontrar Padrões "1(0+)1"

**Descrição:** Identifique substrings que começam e terminam com '1', com um ou mais '0's entre eles.

**Dica de Lógica:** Utilize uma máquina de estados simples.

**Passo a Passo:**
1. Percorra a string bit a bit
2. Ao encontrar '1', busque um ou mais '0's
3. Continue avançando enquanto ler '0'
4. Se encontrar outro '1' após '0's, valide o padrão

**Input:** `str = "1001010001"`  
**Output:** `3` (Padrões: "1001", "101", "10001")

### 8. Buscar uma Palavra em uma Grade 2D

**Descrição:** Determine se uma palavra pode ser formada em linha reta em qualquer das 8 direções (horizontal, vertical, diagonais).

**Dica de Lógica:** Cada célula é um ponto de origem; explore 8 vetores de direção.

**Passo a Passo:**
1. Itere por cada célula da matriz
2. Se `grid[i][j]` for igual à primeira letra da palavra
3. Para cada uma das 8 direções, verifique os caracteres subsequentes
4. Confirme que não sai dos limites da matriz

**Input:** `grid = [['G','E'],['S','K']]`, `word = "GE"`  
**Output:** `Encontrado em (0,0)`

### 9. Maior Prefixo que também é Sufixo

**Descrição:** Calcule o tamanho do maior prefixo próprio que também é sufixo da string.

**Dica de Lógica:** Base do algoritmo KMP para evitar re-comparações.

**Passo a Passo:**
1. Use dois ponteiros ou um array de pré-processamento
2. Compare caracteres em posições simétricas
3. Se coincidirem, incremente o tamanho
4. Se falharem, retroceda para a última correspondência válida

**Input:** `str = "ababa"`  
**Output:** `3` (Prefixo "aba" = sufixo "aba")

### 10. Maior Prefixo como Subsequência

**Descrição:** Determine qual o maior prefixo da String A que aparece como subsequência em String B.

**Dica de Lógica:** Subsequências mantêm ordem, mas permitem "pular" caracteres.

**Passo a Passo:**
1. Inicialize um contador para o prefixo de String A
2. Percorra String B caractere por caractere
3. Se o caractere de B corresponder ao prefixo de A, avance
4. O valor final é o comprimento do maior prefixo

**Input:** `s1 = "digger"`, `s2 = "biggerdiagram"`  
**Output:** `3` (Prefixo "dig")

### 11. Contar String em um Array 2D

**Descrição:** Conte todas as ocorrências de uma palavra em uma matriz, onde o caminho pode mudar de direção a cada letra.

**Dica de Lógica:** Use recursão com backtracking; marque células visitadas para evitar loops.

**Passo a Passo:**
1. Para cada célula `(r, c)` que corresponda à primeira letra
2. Inicie uma função recursiva explorando os 4 vizinhos
3. A cada letra coincidindo, avance para a próxima
4. Se chegar ao fim, retorne 1; explore todos os caminhos

**Input:** Matriz com `palavra = "MAGIC"`  
**Output:** `Total de caminhos válidos encontrados`

</p>
</details>

<details>
    <summary>🔴 Nível 3 - Difícil</summary>
<p>

### 12. Busca de Palavras em Ziguezague

**Descrição:** Similar à busca em matriz, mas a palavra pode fazer curvas em qualquer direção sem repetir células.

**Dica de Lógica:** A complexidade é exponencial; o backtracking é essencial.

**Passo a Passo:**
1. Implemente uma busca em profundidade (DFS)
2. Mantenha um registro de células visitadas
3. Explore adjacências; desmarque células ao falhar (backtrack)
4. Retorne coordenadas ou contagem de sucessos

**Input:** Matriz com palavra  
**Output:** `True/False` ou lista de caminhos

### 13. Correspondência de Padrões com Curingas

**Descrição:** Verifique se uma string casa com um padrão contendo '?' (um caractere) e '*' (zero ou mais).

**Dica de Lógica:** Use Programação Dinâmica; o asterisco é o maior desafio.

**Passo a Passo:**
1. Crie uma tabela DP de tamanho `(texto_len+1) × (padrao_len+1)`
2. `dp[0][0]` é verdadeiro (strings vazias casam)
3. Preencha a primeira linha tratando padrões com '*'
4. Para cada célula, processe '?' e '*' adequadamente

**Input:** `texto = "baaabab"`, `padrão = "ba*ab"`  
**Output:** `True`

### 14. Correspondência de Expressões Regulares

**Descrição:** Implemente casamento com '.' (qualquer caractere) e '*' (zero ou mais do elemento precedente).

**Dica de Lógica:** Diferente de Wildcard: 'a*' significa vários 'a's, não caracteres quaisquer.

**Passo a Passo:**
1. Use Programação Dinâmica; `dp[i][j]` indica correspondência
2. Ao encontrar '*', considere dois casos:
     - Ignored: caractere anterior não casa
     - Usado: caractere anterior casa, mantenha padrão ou avance no texto

**Input:** `texto = "aa"`, `padrão = "a*"`  
**Output:** `True`

### 15. Busca de Padrões usandoTrie de Sufixos

**Descrição:** Construa uma Trie com todos os sufixos de um texto para verificar padrões em tempo linear.

**Dica de Lógica:** Inserir sufixos transforma busca de substring em busca de prefixo.

**Passo a Passo:**
1. Gere todos os sufixos: S[0..n], S[1..n], ..., S[n-1..n]
2. Insira cada sufixo em uma Trie padrão
3. Para buscar padrão P, percorra a Trie caractere por caractere
4. Se chegar ao fim de P sem problemas, P existe no texto

**Input:** `texto = "banana"`, `padrão = "nan"`  
**Output:** `True`

### 16. Aplicação de Árvore de Sufixos – Verificação de Substring

**Descrição:** Implemente uma Árvore de Sufixos (Trie comprimida) para buscas ultra-rápidas.

**Dica de Lógica:** Suffix Tree ocupa O(n), enquanto Trie de sufixos ocupa O(n²).

**Passo a Passo:**
1. Estude o Algoritmo de Ukkonen para construção em O(n)
2. Cada nó representa um ponto de ramificação de sufixos
3. As arestas podem conter múltiplos caracteres
4. Para checar substring, percorra as arestas até o fim

**Input:** `texto = "geeksforgeeks"`, `padrão = "for"`  
**Output:** `True`

</p>
</details>

