# Lista de Exercícios - Algoritmo de Backtracking

Bem-vindo(a) à sua jornada de domínio em Algoritmos de Backtracking! Esta lista foi elaborada para focar no fortalecimento da sua lógica de programação e na sua capacidade de resolver problemas complexos de otimização e busca.

Você pode implementar as soluções na linguagem de programação de sua preferência (C, C++, C#, Java, Kotlin, Javascript/Typescript, Python, PHP, Go, Ruby, etc.). Concentre-se em entender a **transição de estado**, como os dados são modificados na ida da recursão e como devem ser restaurados no retorno.

### Dicas Gerais de Debugging em Backtracking

Entender a lógica de ida e volta (backtracking) é como aprender a andar de bicicleta: depois que o conceito "clica", problemas que pareciam impossíveis viram combinações de decisões e validações.

**Seu código falhou ou entrou em Loop? Pergunte-se:**

1.  **Minha base case (condição de parada) está correta?**
    Se ela estiver errada (ou ausente), o algoritmo pode entrar em loop, causar estouro de pilha (Stack Overflow) ou estourar limite de tempo.
    
2.  **Estou desfazendo o estado corretamente no retorno?**
    Toda escolha feita na ida deve ser desfeita na volta. Exemplos: remover item da lista, desmarcar `visited`, restaurar célula na matriz.
    
3.  **Estou salvando cópia ou referência?**
    Em Python e Java, listas e arrays são estruturas por referência. Ao salvar uma solução parcial, grave uma cópia (por exemplo, `minha_lista.copy()`), não a referência original.
    
4.  **Estou podando galhos inviáveis cedo?**
    A árvore de busca cresce de forma exponencial. Sem poda (checagens antecipadas), o código tende a ficar lento e pode gerar TLE (Time Limit Exceeded).

Treine com frequência, desenhe a árvore de estados no papel antes de codar e valide casos simples manualmente. Em backtracking, raciocínio vem antes de implementação.

<details>
  <summary>🟢 Nível 1 - Fácil</summary>

<p>
Nesta seção, o foco está em entender a mecânica básica de inclusão/exclusão e a navegação simples em árvores de decisão.

### 1\. [Encontrar todos os subconjuntos](https://www.geeksforgeeks.org/dsa/backtracking-to-find-all-subsets/ "null")

**Descrição:** Dado um conjunto de números inteiros, gere todos os subconjuntos possíveis (também conhecido como conjunto das partes ou _Power Set_). **Intuição:** Este é o padrão clássico de "Pegar ou Não Pegar". Para cada elemento, a árvore de decisão se bifurca. **Passo a Passo:**

1.  Crie uma função recursiva que receba o índice atual do array original e o subconjunto temporário construído até o momento.
    
2.  No estado atual, você tem duas bifurcações: incluir o elemento atual no subconjunto temporário ou seguir sem ele.
    
3.  Chame a recursão para o próximo índice (avançando na árvore).
    
4.  Quando o índice for igual ao tamanho do array de entrada (condição de parada), adicione uma _cópia_ do subconjunto temporário à lista de respostas. **Dica de Implementação:** Sempre adicione uma cópia (ou clone) da lista temporária ao resultado final. Se você passar a referência original, ela será modificada nos próximos passos e todas as suas respostas ficarão vazias. **Complexidade:** Tempo O(2N) e Espaço O(N) (devido à pilha de recursão), onde N é o número de elementos.
-   **Input:** 
    `[1, 2]`
    
-   **Output:** 
    `[], [1], [2], [1, 2]`

### 2\. [Verificar string soma](https://www.geeksforgeeks.org/dsa/check-given-string-sum-string/ "null")

**Descrição:** Verifique se uma string de dígitos numéricos pode ser dividida de forma que o terceiro número subsequente seja sempre a soma dos dois números imediatamente anteriores. **Intuição:** Como não sabemos o tamanho de cada número na string, precisamos testar dinamicamente comprimentos diferentes para os dois primeiros blocos numéricos. **Passo a Passo:**

1.  Itere com dois loops iniciais para escolher os comprimentos dos dois primeiros números da string (prefixos).
    
2.  Com os dois primeiros números definidos (por exemplo, "12" e "24"), calcule a soma ("36") e verifique se esse exato resultado aparece imediatamente após eles na string original.
    
3.  Use recursão para verificar o restante da string usando o segundo número como novo "primeiro" e a soma atual como "segundo".
    
4.  Se chegar ao final da string de forma exata, retorne verdadeiro. Se o número não bater, faça o backtrack e tente outros comprimentos no loop inicial. **Dica de Implementação:** Cuidado com strings grandes que podem ultrapassar o limite de inteiros de 32 ou 64 bits da sua linguagem. Em Python isso é gerenciado automaticamente, mas em Java ou C++, pode ser necessário usar bibliotecas numéricas como 
    `BigInteger`
     ou fazer a soma caractere por caractere.
-   **Input:** 
    `"122436"`
    
-   **Output:** 
    `True`
     _(Pois 12 + 24 = 36 e consome a string perfeitamente)_

### 3\. [Todos os caminhos entre dois vértices](https://www.geeksforgeeks.org/dsa/count-possible-paths-two-vertices/ "null")

**Descrição:** Em um grafo direcionado, conte o número total de caminhos válidos e únicos de um vértice de origem até um vértice de destino. **Intuição:** Uma simples busca em profundidade (DFS) que, ao invés de parar quando acha o destino, registra um sucesso e continua buscando outras rotas, voltando atrás nos nós visitados. **Passo a Passo:**

1.  Receba o nó atual e marque-o como 
    `visitado`
     em um array ou HashSet booleano para evitar loops infinitos.
    
2.  Se o vértice atual for exatamente o destino desejado, incremente sua variável global ou contador de caminhos.
    
3.  Para cada vértice adjacente (vizinho) que ainda _não_ foi visitado, chame a recursão passando esse vizinho como o novo vértice atual.
    
4.  **Backtrack:** Ao retornar da recursão, desmarque o vértice atual do conjunto de visitados. Isso é crucial para que este nó possa ser visitado novamente a partir de um caminho inicial diferente. **Complexidade:** O pior caso em grafos densos pode chegar a O(V!) caminhos, onde V é o número de vértices.
-   **Input:** 
    `Grafo: 0->1, 0->2, 1->2, 2->3`
    , 
    `Origem: 0`
    , 
    `Destino: 3`
    
-   **Output:** 
    `2`
     _(Os únicos caminhos possíveis são: 0->1->2->3 e 0->2->3)_

### 4\. [Todos os subconjuntos distintos](https://www.geeksforgeeks.org/dsa/find-distinct-subsets-given-set/ "null")

**Descrição:** Dado um conjunto de números que pode conter elementos duplicados, retorne todos os subconjuntos distintos possíveis (sem repetições lógicas). **Intuição:** Derivado do problema 1, mas precisamos de uma lógica para podar galhos da árvore que gerariam conjuntos idênticos. **Passo a Passo:**

1.  **Passo Fundamental:** Ordene o array de entrada primeiro. Isso garante que elementos duplicados fiquem estritamente adjacentes (ex: 
    `[2, 1, 2]`
     vira 
    `[1, 2, 2]`
    ).
    
2.  Inicie a recursão passando o índice atual.
    
3.  Ao iterar pelas opções num laço 
    `for`
    , pule a chamada recursiva (faça um 
    `continue`
    ) se o elemento atual for igual ao anterior (
    `arr[i] == arr[i-1]`
    ) e o anterior não for o próprio índice inicial daquela profundidade recursiva.
    
4.  Armazene o valor na lista temporária, chame a recursão para 
    `i + 1`
    , e faça o backtrack removendo o último elemento adicionado.
-   **Input:** 
    `[1, 2, 2]`
    
-   **Output:** 
    `[], [1], [2], [1, 2], [2, 2], [1, 2, 2]`
     _(Note que \[2\] aparece apenas uma vez)_

### 5\. [Caminho de comprimento maior que k a partir de uma origem](https://www.geeksforgeeks.org/dsa/find-if-there-is-a-path-of-more-than-k-length-from-a-source/ "null")

**Descrição:** Em um grafo ponderado (com pesos nas arestas), verifique se existe _algum_ caminho a partir de um vértice de origem cujo peso total percorrido seja estritamente maior que um valor 
`k`
. **Intuição:** Uma DFS focada em acumular o peso. A poda ocorre automaticamente assim que a condição é satisfeita, encerrando o algoritmo precocemente. **Passo a Passo:**

1.  Mantenha um vetor ou mapa booleano para registrar os nós visitados na ramificação atual da rota.
    
2.  Na função recursiva, receba o nó atual e o valor 
    `k`
     restante. Se 
    `k`
     for menor ou igual a 0, você já ultrapassou o objetivo; retorne 
    `True`
     imediatamente.
    
3.  Para cada vizinho não visitado, subtraia o peso da aresta entre eles do valor 
    `k`
     e chame a recursão.
    
4.  **Backtrack:** Se a chamada recursiva retornar 
    `False`
     (não conseguiu passar de 
    `k`
     por aquele caminho), desmarque o vizinho e tente explorar as outras arestas adjacentes.
-   **Input:** 
    `Grafo ponderado`
    , 
    `Origem: 0`
    , 
    `k: 50`
    
-   **Output:** 
    `True`
     ou 
    `False`

### 6\. [Todos os caminhos de uma origem para um destino](https://www.geeksforgeeks.org/dsa/find-paths-given-source-destination/ "null")

**Descrição:** Variação do Problema 3. Em vez de apenas contar, você deve salvar e imprimir as listas exatas contendo a sequência de nós percorrida. **Intuição:** Ao invés de um inteiro contador, você carregará uma estrutura de dados de estado (lista) durante a DFS. **Passo a Passo:**

1.  Mantenha uma lista/array que atue como a trilha de migalhas de pão do seu caminho atual.
    
2.  Ao entrar no nó, adicione-o ao final da lista e marque-o como visitado.
    
3.  Se atingir o destino, crie uma cópia profunda (deep copy) da lista atual e adicione-a à resposta final.
    
4.  Caso contrário, para cada vizinho não visitado, faça a chamada recursiva.
    
5.  **Backtrack:** Na saída da função recursiva, dê um 
    `pop()`
     (remova) no último nó da lista e desmarque-o como visitado, restaurando o estado para a função chamadora.
-   **Input:** 
    `Grafo: 0->1, 0->2, 1->3, 2->3`
    , 
    `Origem: 0`
    , 
    `Destino: 3`
    
-   **Output:** 
    `[[0, 1, 3], [0, 2, 3]]`

</p>

</details>

<details>
  <summary>🟠 Nível 2 - Médio</summary>

<p>
Aqui, o estado armazenado fica mais complexo e as condições de poda tornam-se essenciais para a performance do algoritmo.

### 7\. [Guerra dos sexos (Tug of war)](https://www.geeksforgeeks.org/dsa/tug-of-war/ "null")

**Descrição:** Dado um conjunto de N pessoas com diferentes pesos, divida-os em duas equipes (subconjuntos) de forma que a diferença total de peso entre as duas equipes seja a mínima possível. A regra de ouro: as equipes devem ter o mesmo número de pessoas (ou diferir por 1 se N for ímpar). **Intuição:** Precisamos testar permutações e combinações dividindo em dois grupos simulados. A profundidade da recursão é 
`N`
 (cada elemento deve ir para o Grupo 1 ou Grupo 2). **Passo a Passo:**

1.  Crie variáveis para rastrear o elemento atual (
    `index`
    ), os itens do Grupo 1, itens do Grupo 2 e a soma corrente de cada grupo.
    
2.  Para o elemento atual, tente adicioná-lo ao Grupo 1. Antes de adicionar, verifique se o tamanho do Grupo 1 não excede 
    `Teto(N/2)`
    . Se for válido, adicione-o e avance recursivamente.
    
3.  Ao retornar da chamada (Backtrack), remova-o do Grupo 1.
    
4.  Faça a mesma tentativa adicionando o elemento ao Grupo 2, e chame a recursão. Remova-o no backtrack.
    
5.  Quando atingir o final do array, calcule a diferença absoluta de pesos. Se for menor que a melhor diferença global já vista, atualize sua configuração final. **Complexidade:** Sem otimizações de Programação Dinâmica, a força bruta em backtracking leva O(2N).
-   **Input:** 
    `[3, 4, 5, -3, 100, 1, 89, 54, 23, 20]`
    
-   **Output:** 
    `Equipe 1: [4, 100, 1, 23, 20] (Soma: 148), Equipe 2: [3, 5, -3, 89, 54] (Soma: 148)`

### 8\. [Problema das 8 rainhas](https://www.geeksforgeeks.org/dsa/8-queen-problem/ "null")

**Descrição:** Posicione 8 rainhas em um tabuleiro de xadrez 8x8 tradicional de modo que nenhuma delas consiga se atacar. Lembre-se que rainhas movem-se na horizontal, vertical e diagonais infinitamente. **Intuição:** Preencher a matriz de forma ingênua seria gerar 64!/(8!⋅56!) combinações. Usando a lógica de que cada rainha deve estar obrigatoriamente em uma coluna diferente, reduzimos para testar linha por linha em cada coluna. **Passo a Passo:**

1.  A função recursiva processará o tabuleiro coluna por coluna (índice da coluna).
    
2.  Na coluna atual, itere sobre as 8 linhas. Para cada célula (linha, coluna), use uma função auxiliar 
    `is_safe()`
     para ver se há alguma rainha à esquerda na mesma linha, ou nas diagonais superiores e inferiores à esquerda (não precisamos checar a direita pois ainda não colocamos rainhas lá).
    
3.  Se a casa for segura, coloque 
    `1`
     ou 'Q' na matriz e avance recursivamente chamando 
    `resolve_rainhas(coluna + 1)`
    .
    
4.  **Backtrack:** Se posicionar a rainha ali retornar 
    `False`
     lá na frente, retorne o valor da célula para 
    `0`
     e tente a linha de baixo. **Complexidade:** Otimizado, testa no máximo 88 estados, parando muito antes via poda de diagonais.
-   **Input:** 
    `(Nenhum)`
    
-   **Output:** 
    `(Matriz gráfica onde 'Q' são as posições válidas e '.' são vazias)`

### 9\. [Soma combinacional](https://www.geeksforgeeks.org/dsa/combinational-sum/ "null")

**Descrição:** Encontre todas as combinações únicas de números em um array de candidatos que somem exatamente a um valor 
`target`
. Uma característica vital é que o mesmo número pode ser utilizado repetidas vezes. **Intuição:** Diferente da construção de subconjuntos onde andamos sempre para frente, aqui podemos escolher ficar no mesmo índice numérico e extraí-lo várias vezes até estourar o limite. **Passo a Passo:**

1.  O primeiro passo crucial é remover duplicatas e ordenar o array de candidatos para evitar gerar respostas espelhadas/redundantes.
    
2.  Na recursão, passe o array, o 
    `target`
     atualizado, o índice atual e a lista temporária.
    
3.  Se o 
    `target`
     for exatamente 0, copie a lista para os resultados. Se for menor que 0, apenas dê 
    `return`
     para acionar a poda/backtrack.
    
4.  Para o passo indutivo, você tem duas escolhas exclusivas:
    
      21.   Adicionar o candidato atual na lista, subtrair seu valor do target, e chamar a recursão _sem alterar o índice_ (permitindo usá-lo de novo).
          
      23.   Não adicionar o candidato e chamar a recursão incrementando o índice para 
          `i + 1`
          .
-   **Input:** 
    `Array: [2, 3, 6, 7]`
    , 
    `Target: 7`
    
-   **Output:** 
    `[[2, 2, 3], [7]]`

### 10\. [Algoritmo de Warnsdorff para o passeio do cavalo](https://www.geeksforgeeks.org/dsa/warnsdorffs-algorithm-knights-tour-problem/ "null")

**Descrição:** O "Knight's Tour" exige que o cavalo do xadrez visite todas as 64 casas sem repetir nenhuma. O Backtracking puro demora séculos para tabuleiros grandes. A Heurística de Warnsdorff resolve isso guiando as decisões da árvore inteligentemente. **Intuição:** Sempre mova o cavalo para a casa adjacente que tiver o _menor número de movimentos válidos futuros_. É uma estratégia gulosa acoplada ao backtracking. **Passo a Passo:**

1.  A partir de uma célula, em vez de tentar qualquer um dos 8 movimentos em ordem fixa, calcule o "grau" de cada destino válido (quantos saltos válidos aquela casa possui).
    
2.  Ordene as escolhas de destino com base nesse grau (do menor para o maior).
    
3.  Mova para a casa com menor grau. Isso força o cavalo a visitar bordas e cantos do tabuleiro primeiro, evitando ficar preso no centro sem saída no final do jogo.
    
4.  Faça o backtrack tradicional caso se encontre num beco sem saída (grau 0) antes do salto 64.
-   **Input:** 
    `Posição inicial: (2,2)`
    
-   **Output:** 
    `Matriz 8x8 contendo a sequência de números de 1 a 64 mapeando o caminho completo.`

### 11\. [Caminhos da célula do canto até a célula do meio em um labirinto](https://www.geeksforgeeks.org/dsa/find-paths-from-corner-cell-to-middle-cell-in-maze/ "null")

**Descrição:** Imagine uma matriz quadrada de tamanho ímpar (ex: 9x9). Cada célula contém um número indicando a _distância exata_ que você deve saltar a partir dela em linha reta. Começando nos cantos, você deve chegar ao exato meio da matriz. **Intuição:** Diferente de grafos adjacentes onde se avança de 1 em 1 bloco, o cálculo de coordenadas é elástico (ex: salto do tipo 
`linha + valor_celula`
). **Passo a Passo:**

1.  Crie uma matriz booleana de 
    `visitados`
    .
    
2.  O passo recursivo começa lendo o valor 
    `n = matriz[linha][coluna]`
    .
    
3.  Se a célula for a central (coordenadas 
    `N/2, N/2`
    ), armazene e imprima o caminho percorrido.
    
4.  Calcule as quatro novas posições saltando exatamente 
    `n`
     casas para Norte (
    `linha - n`
    ), Sul (
    `linha + n`
    ), Leste (
    `coluna + n`
    ) e Oeste (
    `coluna - n`
    ).
    
5.  Se uma nova posição estiver dentro dos limites do grid e não foi visitada, adicione à lista, marque e faça a recursão.
    
6.  **Backtrack:** Desfaça a visita e remova o elemento da trilha no final.
-   **Input:** 
    `Matriz quadrada NxN de inteiros`
    
-   **Output:** 
    `A sequência de coordenadas saltadas.`

### 12\. [Maior número possível com no máximo K trocas](https://www.geeksforgeeks.org/dsa/find-maximum-number-possible-by-doing-at-most-k-swaps/ "null")

**Descrição:** Dado um número enorme armazenado em formato de string, e um inteiro 
`K`
, seu objetivo é encontrar o maior número possível realizando, no máximo, 
`K`
 trocas (swaps) de posições de qualquer par de dígitos. **Intuição:** Tratar dígitos como caracteres. O backtracking testará trocar um número pequeno inicial por um número grande localizado mais ao fim da string. **Passo a Passo:**

1.  Inicie salvando a string de entrada original em uma variável global 
    `valor_maximo`
    .
    
2.  A recursão recebe a string atual e a quantidade restante de trocas 
    `K`
    . Se 
    `K == 0`
    , apenas retorne.
    
3.  Crie um loop aninhado iterando comparando o caractere no índice 
    `i`
     com o de índice 
    `j`
     (
    `j > i`
    ).
    
4.  Se o dígito em 
    `j`
     for maior que o dígito em 
    `i`
    , faça o _swap_ entre eles na string.
    
5.  Verifique se a string gerada é numericamente maior que 
    `valor_maximo`
     e atualize-o se sim.
    
6.  Chame a recursão decremetando 
    `K`
     em 1.
    
7.  **Backtrack:** Desfaça o _swap_ para que o loop teste trocar 
    `i`
     com o próximo valor de 
    `j`
    . **Dica de Implementação:** Sempre que atualizar o máximo, use funções de comparação de strings padrão (
    `compareTo`
     ou operadores 
    `>`
    , já que elas garantem a comparação lexicográfica correta para strings do mesmo tamanho).
-   **Input:** 
    `String: "129814999", K: 4`
    
-   **Output:** 
    `"999984211"`

### 13\. [Rato em um labirinto com múltiplos saltos permitidos](https://www.geeksforgeeks.org/dsa/rat-in-a-maze-with-multiple-steps-jump-allowed/ "null")

**Descrição:** O labirinto não contém 1s e 0s, mas números positivos. Um número 
`X`
 numa casa significa que o rato pode escolher saltar 1, 2, ..., ou até 
`X`
 espaços para a direita ou para baixo. O alvo é o canto inferior direito. **Intuição:** A ramificação não é apenas direcional, mas também envolve _força_ do pulo. **Passo a Passo:**

1.  A função parte de 
    `(0,0)`
    . Verifique a condição de vitória: linha e coluna estarem na última posição.
    
2.  Leia o valor da célula: 
    `saltos_max = labirinto[l][c]`
    . Se for 0, é um beco sem saída.
    
3.  Crie um loop de 
    `i = 1`
     até 
    `saltos_max`
    .
    
4.  Primeiro, tente pular 
    `i`
     posições para a direita: chame a recursão para 
    `(l, c + i)`
    . Se retornar verdadeiro, repasse a vitória.
    
5.  Se falhar, faça o backtrack (o código continuará no loop) e tente pular 
    `i`
     casas para baixo 
    `(l + i, c)`
    .
    
6.  Se todos os saltos possíveis falharem, retorne 
    `Falso`
    .
-   **Input:** 
    `[[2, 1, 0, 0], [3, 0, 0, 1], [0, 1, 0, 1], [0, 0, 0, 1]]`
    
-   **Output:** 
    `Matriz visual indicando as pegadas do caminho que obteve sucesso.`

### 14\. [N rainhas em espaço O(n)](https://www.geeksforgeeks.org/dsa/n-queen-in-on-space/ "null")

**Descrição:** Otimização arquitetural do problema 8. Resolva N Rainhas sem alocar matrizes 2D para o tabuleiro, economizando drasticamente alocação de memória usando apenas um array unidimensional de tamanho 
`N`
. **Intuição:** Sabemos que cada linha só comporta 1 rainha. Então um array 
`tab[4] = [1, 3, 0, 2]`
 significa que na linha 0 a rainha está na coluna 1; na linha 1, coluna 3, etc. **Passo a Passo:**

1.  Crie um array de tamanho 
    `N`
    . Inicie o backtracking recebendo o índice da linha atual.
    
2.  A verificação de segurança 
    `is_safe()`
     itera sobre as linhas já preenchidas antes da atual (ou seja, até 
    `linha - 1`
    ).
    
3.  Uma posição 
    `(linha_atual, col_tentativa)`
     é atacada se bater coluna: 
    `tab[linha_anterior] == col_tentativa`
    .
    
4.  É atacada na diagonal se a diferença de X for igual a diferença de Y: 
    `abs(tab[linha_anterior] - col_tentativa) == abs(linha_anterior - linha_atual)`
    .
    
5.  Com a verificação rápida, avance o backtracking registrando o valor da coluna no array. **Complexidade:** Espaço cai de O(N2) para O(N) real.
-   **Input:** 
    `N = 4`
    
-   **Output:** 
    `[1, 3, 0, 2]`

## 🔵 Problemas Padrão (Clássicos)

Estes são os "Hello World" avançados do Backtracking. São amplamente cobrados em exames de seleção corporativos de big techs.

### 15\. [Permutações de uma string](https://www.geeksforgeeks.org/dsa/write-a-c-program-to-print-all-permutations-of-a-given-string/ "null")

**Descrição:** Dada uma string (ou um array de caracteres), produza e imprima todas as reordenações possíveis (permutações) desses caracteres de forma única. **Intuição:** Fixamos um caractere na primeira posição e permutamos o resto; depois fixamos o segundo caractere, permutamos o resto, etc. Fazemos isso trocando referências in-place (no próprio lugar). **Passo a Passo:**

1.  A função base recebe a string convertida para Array, um ponteiro esquerdo 
    `L`
     (inicial 0) e o ponteiro direito 
    `R`
     (último índice).
    
2.  Se 
    `L == R`
    , imprima o array atual, pois a permutação chegou no fim.
    
3.  Se não, inicie um loop 
    `i`
     indo de 
    `L`
     até 
    `R`
    .
    
4.  Faça o _Swap_ (troca) entre o caractere no índice 
    `L`
     e no índice 
    `i`
    . Isso equivale a colocar 
    `i`
     na frente.
    
5.  Chame recursivamente avançando: 
    `permutar(arr, L + 1, R)`
    .
    
6.  **Backtrack:** Desfaça o _Swap_ entre 
    `L`
     e 
    `i`
     para retornar a string ao estado original antes do laço avançar para o próximo caractere. **Complexidade:** Tempo O(N⋅N!).
-   **Input:** 
    `"ABC"`
    
-   **Output:** 
    `"ABC", "ACB", "BAC", "BCA", "CAB", "CBA"`

### 16\. [Problema do passeio do cavalo Clássico](https://www.geeksforgeeks.org/dsa/the-knights-tour-problem/ "null")

**Descrição:** Determinar a ordem exata para um cavalo saltar e cobrir todo um tabuleiro NxN sem repetições. Diferente do problema 10, aqui você programará a base bruta do backtracking sem heurísticas de otimização, essencial para tabuleiros menores ou acadêmicos. **Intuição:** Uma DFS exaustiva tentando todas as 8 direções de forma cega até esbarrar no limite ou preencher as 64 casas. **Passo a Passo:**

1.  Inicialize uma matriz 
    `NxN`
     com 
    `7.1`
     representando casas não visitadas. Registre a origem com 
    `0`
     (movimento zero).
    
2.  Declare dois arrays para as coordenadas dos saltos em L (X: 
    `[2, 1, -1, -2, -2, -1, 1, 2]`
    , Y: 
    `[1, 2, 2, 1, -1, -2, -2, -1]`
    ).
    
3.  Para cada passo da recursão, tente os 8 movimentos fazendo um 
    `for`
    .
    
4.  Valide o próximo salto: deve estar dentro de 0 e N-1 e a célula de destino deve ser 
    `33.1`
    .
    
5.  Se válido, insira o número do salto atual na matriz e chame recursão.
    
6.  **Backtrack:** Se falhar em encontrar solução a partir dali, volte a célula para 
    `41.1`
    .
-   **Input:** 
    `Origem em (0,0)`
    
-   **Output:** 
    `Matriz resolvida com os pulos sequenciais.`

### 17\. [Rato em um labirinto](https://www.geeksforgeeks.org/dsa/rat-in-a-maze/ "null")

**Descrição:** Um rato quer fugir de um labirinto. A matriz é feita de 
`1`
 (caminho livre) e 
`0`
 (parede de bloqueio). Ele pode se mover D (baixo), L (esquerda), R (direita) e U (cima). Imprima todos os caminhos que levam ao canto oposto inferior direito. **Intuição:** Devemos tentar as direções na ordem Lexicográfica para que a resposta seja impressa em ordem alfabética (D -> L -> R -> U). **Passo a Passo:**

1.  Verificação básica: se a origem 
    `(0,0)`
     ou destino for parede (
    `0`
    ), aborte imediatamente.
    
2.  Inicie a DFS acumulando uma string de caminho (ex: 
    `"DDR"`
    ).
    
3.  Na posição atual, se chegou no destino, guarde o caminho na lista de retornos.
    
4.  Para mover, altere o valor da célula atual temporariamente para 
    `0`
     (ou marque em uma matriz de visitados paralela) para impedir que o rato ande em círculos e caia em _stack overflow_.
    
5.  Tente mover para Baixo, Esquerda, Direita e Cima. Anexe a respectiva letra na chamada recursiva.
    
6.  **Backtrack:** Restaure a célula atual para 
    `1`
     (ou desmarque de visitado) e retorne.
-   **Input:** 
    `[[1,0,0,0], [1,1,0,1], [1,1,0,0], [0,1,1,1]]`
    
-   **Output:** 
    `["DDRDRR", "DRDDRR"]`

### 18\. [Problema das N rainhas (Busca Exaustiva)](https://www.geeksforgeeks.org/dsa/n-queen-problem-backtracking-3/ "null")

**Descrição:** Versão generalizada e flexível para descobrir uma única configuração segura de 
`N`
 rainhas num tabuleiro 
`N x N`
. **Intuição:** Diferente da versão otimizada com array 1D, esta abordagem serve de base teórica trabalhando diretamente na matriz bidimensional para fins didáticos. **Passo a Passo:**

1.  Passe o índice da coluna por parâmetro.
    
2.  Para achar onde depositar na coluna 
    `C`
    , itere por todas as linhas 
    `L = 0`
     até 
    `N-1`
    .
    
3.  Verifique usando loops a linha para trás e ambas diagonais para a esquerda até o limite 0.
    
4.  Assinale matriz\[L\]\[C\] = 1, e chame recursivamente 
    `resolver(C + 1)`
    .
    
5.  Apague e limpe a célula (
    `= 0`
    ) no backtrack. **Dica de Implementação:** A verificação se a rainha é atacada pode ser substituída pelo uso de arrays de hash ou bitmask para saber se certa diagonal já está tomada em tempo O(1).
-   **Input:** 
    `N = 4`
    
-   **Output:** 
    `[[0, 1, 0, 0], [0, 0, 0, 1], [1, 0, 0, 0], [0, 0, 1, 0]]`

### 19\. [Quebra-cabeça criptográfico de soma de palavras](https://www.geeksforgeeks.org/dsa/solving-cryptarithmetic-puzzles/ "null")

**Descrição:** Resolva o famoso puzzle "SEND + MORE = MONEY". Cada letra do alfabeto representa um algarismo distinto de 
`0`
 a 
`9`
. Letras iguais são algarismos iguais. Não há zeros à esquerda nos números resultantes. **Intuição:** Precisamos encontrar o mapeamento perfeito (Permutação) combinando caracteres únicos aos dígitos de 0 a 9 validando contra uma equação matemática. **Passo a Passo:**

1.  Faça a extração das letras únicas de todas as palavras envolvidas e coloque num array (no máximo 10).
    
2.  Crie um array booleano de 
    `0`
     a 
    `9`
     marcando quais números numéricos já foram usados, e um mapa 
    `letra -> valor`
    .
    
3.  Na recursão, avance pelas letras únicas. Para a letra no índice atual, teste atribuir os números de 0 a 9 que não estiverem em uso.
    
4.  Preencha o mapa, marque o dígito como usado e recursione.
    
5.  Quando todas as letras tiverem um valor, monte os números inteiros correspondentes às palavras base e ao resultado. Se A + B == C, você achou a solução. Imprima e finalize.
    
6.  **Backtrack:** Desvincule o dígito da letra e desmarque do array numérico antes da próxima iteração de valor.
-   **Input:** 
    `"SEND", "MORE", "MONEY"`
    
-   **Output:** 
    `S:9, E:5, N:6, D:7, M:1, O:0, R:8, Y:2`

### 20\. [Problema da soma de subconjunto (Subset Sum)](https://www.geeksforgeeks.org/dsa/subset-sum-problem/ "null")

**Descrição:** Indicar com precisão se dentro de um array numérico é possível selecionar um grupo de itens cuja soma exata alcance um valor alvo (
`target`
). **Intuição:** Em essência é um problema que tem raízes em Programação Dinâmica (Knapsack 0/1), mas o algoritmo por backtracking puro é a fundação para entendê-lo. **Passo a Passo:**

1.  A cada nó da árvore de recursão, observe o elemento sob o índice atual.
    
2.  Você pode subtrair o valor dele do alvo global 
    `target`
     (ação de incluí-lo) e avançar, ou pode deixá-lo no array ignorado e apenas avançar o índice mantendo o alvo intocado.
    
3.  Se o alvo passar a ser exatamente 0, solte um grito de vitória (retorne verdadeiro) em cadeia.
    
4.  Se o limite de itens do array acabar, ou se o alvo se tornar estritamente negativo, você desceu num galho ruim. Retorne falso, o que forçará o último galho a reverter a escolha (backtrack). **Complexidade:** O(2N). Em grandes arrays isso expira o tempo limite, necessitando a memoização (DP).
-   **Input:** 
    `Array: [3, 34, 4, 12, 5, 2], Target: 9`
    
-   **Output:** 
    `True`
     _(Atingido combinando 4 e 5)_

### 21\. [Problema de coloração m de grafos](https://www.geeksforgeeks.org/dsa/m-coloring-problem/ "null")

**Descrição:** Determinar se um grafo (mapa de conectividade) pode ser inteiramente colorido distribuindo no máximo 
`m`
 cores entre seus vértices, com a rígida lei de que nenhum vértice vizinho (adjacente) tenha a mesma cor. (Teorema das quatro cores de mapas se origina daqui). **Intuição:** Assim como no Sudoku, testamos valores possíveis (cores) em células vazias (nós do grafo) garantindo restrições laterais de forma incremental. **Passo a Passo:**

1.  Inicie um array unidimensional de "cor" inicializado com 0.
    
2.  Processaremos vértice a vértice recursivamente, controlando por um parâmetro de nó a processar 
    `u`
    .
    
3.  Para o vértice atual 
    `u`
    , teste cores de 1 até 
    `m`
    .
    
4.  Uma cor é segura se, olhando na matriz/lista de adjacência, não há aresta de 
    `u`
     para 
    `v`
     em que 
    `cor[v]`
     já seja igual à cor testada.
    
5.  Em cenário seguro, atribua 
    `cor[u] = c`
     e acione a recursão para 
    `u + 1`
    .
    
6.  **Backtrack:** Apague a cor se for impossível prosseguir para os vizinhos: 
    `cor[u] = 0`
    .
-   **Input:** 
    `Matriz de Adjacência do Grafo V=4, m = 3`
    
-   **Output:** 
    `True (As cores válidas aplicadas por nó, ex: [1, 2, 3, 2])`

### 22\. [Ciclo hamiltoniano](https://www.geeksforgeeks.org/dsa/hamiltonian-cycle/ "null")

**Descrição:** Descubra e prove se existe em um grafo arbitrário pelo menos uma rota (ciclo) que visite rigidamente todos os vértices exatamente uma vez, retornando fatalmente ao nó de início que originou a viagem. Usado em bases para o "Problema do Caixeiro Viajante" sem pesos. **Intuição:** Uma DFS rigorosa onde o caminho acumulado não apenas precisa atingir o tamanho V, mas o nó da ponta final tem que possuir uma via física que o religue com a origem primária. **Passo a Passo:**

1.  Fixe o nó inicial (ex: vértice 0) no array temporário do seu percurso.
    
2.  Busque recursivamente qual o próximo candidato na vizinhança que ainda não conste no array histórico.
    
3.  Se o candidato passar no teste de pureza (inédito na viajem atual), anexe e desça uma camada na árvore de decisões.
    
4.  Quando o número de itens na lista alcançar o total de vértices globais, faça uma varredura final verificando se a matriz de conexões afirma haver uma aresta ligando o último integrante da lista até o elemento da cabeça da lista.
    
5.  **Backtrack:** Descarte o vértice das anotações se os retornos abaixo disserem que se chegou num precipício e suba de volta.
-   **Input:** 
    `Matriz de Adjacência Boolean/Binária`
    
-   **Output:** 
    `Caminho circular, por exemplo: [0, 1, 2, 4, 3, 0]`

### 23\. [Sudoku Solver Exaustivo](https://www.geeksforgeeks.org/dsa/sudoku-backtracking-7/ "null")

**Descrição:** Projetar o cérebro clássico para resolver Sudokus automaticamente e instantaneamente. Preencha uma matriz de 9 por 9 lacunas parcialmente abastecidas, obedecendo às sagradas leis: cada linha, coluna e os 9 mini-quadrados internos (3x3) devem exibir algarismos únicos e não repetidos na faixa entre 1 e 9. **Intuição:** Buscar a primeira lacuna vazia, tentar um número. Se não violar a matriz atual, injete. Se quebrar na frente, passe o apagador no bloco e tente com o próximo algarismo numérico. Pura elegância em tentativa e erro cego. **Passo a Passo:**

1.  Tenha uma função primária de radar de vazios. Se rodar na matriz iterativamente da esquerda à direita e cima a baixo e não topar com nenhum 
    `0`
    , vitória declarada.
    
2.  Nos loops da célula vazia flagrada no radar, submeta os números possíveis girando de 1 a 9 no laço.
    
3.  Regra de checagem tripla para validez em bloco: varrer a linha corrente da lacuna de x a 9, a coluna, e calcular a coordenada raiz local do sub-grid 3x3 
    `[linha - linha % 3][coluna - coluna % 3]`
     vasculhando as 9 células dali.
    
4.  Aprovado nos testes? Grave o valor, efetue chamada de empilhamento recursiva e aguarde o booleano de resposta.
    
5.  **Backtrack:** Chumbou a resposta? Faça 
    `grade[row][col] = 0`
     para despovoar.
-   **Input:** 
    `Matriz 9x9 com valores parciais e marcadores 0 ou -1.`
    
-   **Output:** 
    `A grade matemática resolutamente concluída e polida.`

### 24\. [Quebra-cabeça magnético](https://www.geeksforgeeks.org/dsa/magnet-puzzle/ "null")

**Descrição:** Jogo intrigante de lógica que simula física magnética simples. Você dispõe de blocos retangulares de dominó de dimensão 2x1 ou 1x2 emparelhados sobre uma tábua. Tente preenchê-los com polos positivos 
`+`
 e negativos 
`-`
, observando limitações cruciais de volume marginais e da repulsão inerente no qual polos idênticos polarizados nunca deverão partilhar contato horizontal e vertical em lajotas separadas. **Intuição:** Uma fusão mental do sistema Sudoku e restrições de Coloração. Você deve avaliar regras para o dominó atual, suas margens coladas e regras esqueléticas da borda inteira. **Passo a Passo:**

1.  As iterações do avanço de Backtracking esquadrinham casa por casa dentro das limitações matriciais primárias.
    
2.  Identifique o formato de bloco da casa lida. Quando topar com espaço virgem, experimente posicionar padrões polarizados binários emparelhados de 
    `[+ -]`
     , de reflexão invertida 
    `[- +]`
     ou deliberar pelo vazio e oco neutro de 
    `[X X]`
    .
    
3.  Dispare averiguação perimetral adjacente de checagem. Dois elementos positivos encostados causam curto circuito lógico.
    
4.  Alcançando o destino das coordenadas, faça balanço contábil sumariando cargas horizontais e cargas longitudinais de preenchimento comparando contagens limites indicadas para resolver o enigma de sucesso.
    
5.  **Backtrack:** Limpe os polos colocados se ocorrer um conflito de regras ou falha de contagem nas margens.
-   **Input:** 
    `Matriz esqueleto representativa de blocos L/R/T/B, Arrays de restrições das fileiras.`
    
-   **Output:** 
    `Placa visual texturizada recheada e carimbada nos padrões + -.`

### 25\. [Remover parênteses inválidos para máxima string válida](https://www.geeksforgeeks.org/dsa/remove-invalid-parentheses/ "null")

**Descrição:** Extraído string impura em que as pontuações e encerramentos parênteses desbalanceados provocam falhas gramaticais e lógicas. Elimine unicamente o quantitativo exigido de falhas que for absolutamente necessário, mas faça em _múltiplas variações de combinações perfeitas diferentes_ com peso igual mínimo para purificar o texto base de origem. **Intuição:** Para não testar combinações infinitas cegamente gerando Timeout Limits, nós calculamos na largada exatos números numéricos brutos do que sobra. Backtracking então funciona "apagando e deletando string" na quantidade pré estipulada gerando galhos de variantes filtradas de ramificação. **Passo a Passo:**

1.  A priori, submeta a palavra bruta a um cálculo Stack em Pilha ou contador básico de controle para flagrar e definir número integral mínimo alvo de erros extras flutuantes em carência na sua estrutura desbalanceada (Ex: 2 fechamentos a mais).
    
2.  Na função autônoma, use um laço For interativo de remoções fatiando a string atual em substrings e tirando cirurgicamente parêntese da variável. Cada remoção re-chama uma ramificação deduzindo contagem permitida flutuante no argumento passado e avançando checagens balanceadoras de balanço lógico de gramática.
    
3.  Ao findar cortes zerando limite de margem de eliminação, rode balanceamento nativo simples (verificação normal). Adicione resgates limpos finalísticos ao Hashset local a fim de repelir espelhamento ou impressões de repetições gráficas espúrias redundantes à tela de exibição.
-   **Input:** 
    `"()())()"`
    
-   **Output:** 
    `Coleção Arrays de formatação: ["()()()", "(())()"]`

</p>

</details>

<details>
  <summary>🔴 Nível 3 - Difícil</summary>

<p>
As restrições multiplicam-se e os tempos de cálculo de força bruta implodiriam sua RAM se as técnicas de poda não forem inteligentemente estruturadas. Requerem paciência analítica apurada de alto nível acadêmico de raciocínio.

### 26\. [Conjunto potência em ordem lexicográfica rigorosa](https://www.geeksforgeeks.org/dsa/powet-set-lexicographic-order/ "null")

**Descrição:** Semelhante à descoberta de partes e frações de conjuntos, com a restrição vital de que os resultados consolidados exibidos globalmente na tela não fiquem aleatoriamente impressos e flutuantes, mas sim impecavelmente listados nos ditames estritos lexicográficos sem ter a trapaça de re-organizar um array global na saída tardiamente. A própria árvore molda a ordem. **Intuição:** Se impormos a organização forçada alfabética previamente aos componentes unitários básicos de entrada e depois mesclarmos isso à descida top-down da árvore perfeitamente progressiva, o resultado orgulhosamente herdará formatação alfabética de tabela. **Passo a Passo:**

1.  Ordene os caracteres alfabéticos primários da string de entrada inicial. ("CBA" deve tornar-se "ABC").
    
2.  No esqueleto do Backtracking que trafega recebendo o referencial base da string corrente somada em passos passados, logo nas chamadas base acione comando autônomo visual e jogue para tela impressões flutuantes a toda visita atômica da estrutura para captar progressos e raízes parciais formadas na descida sem esperar chegar na folha limite.
    
3.  Desça engajando um loop dinâmico englobando os próximos índices numéricos disponíveis à frente. Anexe concatenando de modo linear.
    
4.  Chame recursão acoplada para desbravar filiais.
    
5.  **Backtrack:** Execute estrito procedimento Pop no stack cortando e extirpando caractere mais a direita aliviando variável de estado recuando na ramificação permitindo testagem de laço lateral vizinho engatar avanço lateral para montagens.
-   **Input:** 
    `"abc"`
    
-   **Output:** 
    `"a", "ab", "abc", "ac", "b", "bc", "c"`

### 27\. [Problema de quebra de palavras usando backtracking (Word Break DP/Backtracking)](https://www.geeksforgeeks.org/dsa/word-break-problem-using-backtracking/ "null")

**Descrição:** Você detém e comanda em posse dicionários limitados locais contendo listagens restritas limitadas verborrágicas com significados. E possui texto sequencial colado unificado desprovido de qualquer espaçamento métrico. Sua tarefa crítica exige desconstruir segmentando este rolo compressores de palavra reconstituindo as demarcações separatórias exatas originárias recriando frases gramaticais com base no livro interno seu referencial limitante de dicionário. Descubra _todas_ frases plausivelmente inteligíveis no idioma do repositório. **Intuição:** Em vez de pular posições aleatórias, checamos porciones fatiadas de tamanho métrico progressivamente de comprimento N crescente comparativas da esquerda pra direita, batendo na enciclopédia HashSet se bater ressonância extraímos corte recursivo do excedente residual em resquícios laterais direitos sobrantes. **Passo a Passo:**

1.  Capture e encapsule base local enciclopédia como em variáveis globais ou estrutura Hashset acelerada referencial nativa contendo tempos assintóticos em consultas O(1) contínuos para desempenho analítico instantâneo veloz e furioso de comparações.
    
2.  Na função diretiva base, abrace toda e ampla e integral sequencial de texto de parâmetro original recebida virgem sem fatiamento inicial como referencial base primário inicializador em chamadas matriz. Avance por progressão gradual laço dinâmico variando limites finais para ir aumentando fatias e sufixos de fatiamento incrementado para gerar pedaços progressivos alvos (
    `prefixo`
    ).
    
3.  Condicional estrito base: se o atual prefixo montado e recortado local coincidir no banco Hashset léxico, aglomere isto gravando linear na corrente temporária variável textual de memória.
    
4.  Avance por ramificação injetando string amputada do pedaço subtraído como base analítica da subseção residual remanescente do miolo da palavra. Quando se extinguirem totalmente fragmentos do string sem defeitos ressalvas e falhas métricas, armazene vitoriosamente a frase global inteira ao resguardo estrutural global numérico lista final de resposta matriz de frases.
    
5.  **Backtrack:** Loop de avanço ignora progressos efêmeros caso ramificações parciais implodam por estagnação sintática nas sobras numéricas retrocedendo blocos cortados ampliando o escopo métrico prefixo original das chamadas em loop subjacente até colapsos finalísticos resolutivos.
-   **Input:** 
    `Dicionário: {"i", "like", "sam", "sung", "samsung"}, String: "ilikesamsung"`
    
-   **Output:** 
    `"i like sam sung" e "i like samsung"`

### 28\. [Partição de um conjunto em K subconjuntos de soma numéricamente iguais de volumes equilibrados](https://www.geeksforgeeks.org/dsa/partition-set-k-subsets-equal-sum/ "null")

**Descrição:** Dada array genérica de variados números irregulares flutuantes positivos limitados inteiros de valores independentes. Apure metodologicamente de forma pericial com extrema e refinada eficácia técnica pericial se estes referidos volumes massivos esparsos aceitam alocações subdivididas com simetrias lógicas dividindo precisamente os materiais numéricos base formadores de alocação matriz em total e unicamente N quantitativos em 
`K`
 conjuntos. Requisito crucial imperativo é prescrever exigência absoluta inegociável restritiva da obrigação para totalização global aritmética ponderada e apurada perimetral idêntica e semelhanças idênticas numéricas das somas agregadas em volumes brutos equivalentes. **Intuição:** Descobrirmos matematicamente precocemente alvo volume teto. Após alvo base montado e imposto, geramos backtracking multidimensional rastreando buckets numéricos com contadores visitados simulando acúmulo individual em lotes sequenciais exaurindo itens. **Passo a Passo:**

1.  Teste profilático eliminatório cego e frio: Somatório total acumulado bruto perimetral dividido pela demanda fracional global solicitada limitadora por K tem sobras resíduos métricos percentuais modulados decimais em fracionamento? Resto diferente zero aborta tentativa imediatamente por inviabilidades operacionais primárias e lógicas inoperáveis da natureza matemática real. A base para cada bucket se consagra então pelo resultado métrico alvo de Soma/K.
    
2.  Inicie mapeamento local boolean array controlando o "já fui utilizado e fatiado", de tamanho N vetorial numérico equivalente atrelado estrito ao grupo e pacote numérico.
    
3.  Recursões se norteiam parametrizadas com controle restrito indexador referencial de pacotes finalizados completos.
    
4.  Para as consolidações atuais de peso volumétrico de subgrupo preenchido com for-loops. Iteramos agregando e somando até estourar estritamente o teto paramétrico alvo estabelecido inicial restritivo numérico preceito da balança.
    
5.  Quando o bucket subgrupo exaurir espaço ou completar alvo milimétrico preciso volumétrico igual, desponta gatilho acionador para recursão pular gerando e instaurando novo processo recriado indexador global numérico do zero em montagem alocando restrições contíguas e independentes iteradas buscando bucket limpo K remanescente para o novo subgrupo preenchendo as sobras restantes base em novo bloco sequencial numérico indexado até contabilidade totalizante exaurir lotes numéricos batendo número original total pacotes alvos referencial.
    
6.  **Backtrack:** Desmarcar visitados, subtrair as adições do peso se bater limite restritivo impedindo fluxo limpo resolutivo global.
-   **Input:** 
    `Array: [2, 1, 4, 5, 6], K: 3`
    
-   **Output:** 
    `True / False lógico booleano de confirmação resolutiva (Pois [2,4]=6, [1,5]=6, [6]=6 e satisfaz simetria lógica).`

### 29\. [Maior rota exploratória tortuosa extensiva possível em complexidades atreladas à matriz esburacada com obstáculos impeditivos limitadores focados perigosos](https://www.geeksforgeeks.org/dsa/longest-possible-route-in-a-matrix-with-hurdles/ "null")

**Descrição:** Transmutação e adaptação lógica invertida reconfigurando problemáticas focadas inversas tradicionais normais corriqueiras em algoritmos DFS e BFS baseados de trajetos curtos mínimos e simplórios resolutivos rápidos. Agora requisição impõe explorar exaurir e sugar ao máximo prolongamentos infinitos e torções em caminhos complexos originários pontuais esquadrinhados do começo A indo sinuoso longínquo Z mas imperativamente escapando restritivamente de bloqueios sólidos marcados fixos do tipo estáticos mapeados. E proibições terminantes inibem taxativas de recriar passos visitando duplos e espelhos repetitivas pegadas anteriores marcadas sob rastros prévios sujos para fugir ciclagens e looping temporais ininterruptos circulares infinitos contínuos lógicos travando execuções processuais atrelados às máquinas sem fim e propósito. **Intuição:** Diferente da Busca em Largura (BFS) nativa criada pela ciência focada exclusiva dedicada restritiva projetada achando o curtíssimo trecho pontual minimizando progressões rasas, uma busca de longínquas distâncias máximas é NP-Hard puro exigindo testagem de todos os micro ramais sem atalhos simplórios até atingir metas alvos finais baseadas comparando profundidades de pilha acumulativas gravando globais temporais variáveis de registros numéricos restritivos de estagnação superlativa numéricas máximas. **Passo a Passo:**

1.  Eleja variável numérica estática em escopo abrangente amplo externo isolado da máquina e ambiente (
    `max_distancia`
    ) estipulada referencial zerada limitadora inicial e mínima basal métrica base zero ou infinitamente sub zero decrescente isolada neutra paramétrica para reconfiguração temporal incremental cíclica numérico variável global expansiva gradativa lógica.
    
2.  Invoque chamadas parametrizadas controlando X direcional temporal, Y direcional coordenado limitativo de base esquadrinhado e acumulativo paramétrico profundidade limitadora flutuante métrica incremental acumulativa rastreadora base dimensional numérica (
    `distancia_atual`
    ).
    
3.  Avance na cruz testando normativas limítrofes, evitando zeros, evitando rastros. Se OK carimbe o bloco provisório. Adicione distância.
    
4.  Quando coordenadas colidirem no alvo limite referenciado paramétrico desejado meta atingida alvejada resolvida, pare o passo comparando e engolindo se maior substituindo 
    `max_distancia`
    . Não congele a máquina numéricas em vitórias precoces ilusórias efêmeras contínuas primárias de acertos isolados! Devolva a execução cega continuativa e fluida em devoluções recursivas para o motor tentar alternativas secundárias torcendo percursos extensivos base subjacente exaurindo árvore ramificada galhos colaterais laterais estendendo testagens infinitas prolongando exaustivas rastreando extremas variações extensas completas e integrativas.
    
5.  **Backtrack:** Marcar matriz como destrancada ilesa virgem para os algoritmos parentais testarem acessos por vias transversas e alternantes cruzamentos cruzados secundários interligados intersecionistas abertos longitudinais alternativos limpos originais não poluídos corrompidos ou modificados nas bases fundamentais referenciados base numérico rastreados temporais base de referencial limitativos processuais base raiz ramificada e esquadrinhados recursivamente do zero de novo de ramificação para novas alocações espaciais originais reconfigurados na estrutura.
-   **Input:** 
    `Matriz Binária 3x10 restrita (1 livre, 0 parede bloqueios impeditivos fechados restritos obstruções), Origem parametrizada inicial básica e basal raiz núcleo fixada coordenada referencial numéricas pontuais, Destino focal direcionado limitativo pontual e referencial almejado alvo coordenado parametrizado base métrico alocado referencial estruturado espaciais posicional de cruzamento e localização geográfica matemática X Y coordenados limitantes alvo base meta alocada limite final referenciado coordenado geográfico de espaço limitante focal pontuais numéricas.`
    
-   **Output:** 
    `Valor escalar inteiro absoluto matemático único base restritivo indicando comprimento referencial total acumulativo do trajeto longo e tortuoso percorrido extenso restritivo limite sem bater caminhos inviabilizados trancados e fechados restritivos exaurido e limpo.`

### 30\. [Rota segura mais curta em um caminho minado com bombas](https://www.geeksforgeeks.org/dsa/find-shortest-safe-route-in-a-path-with-landmines/ "null")

**Descrição:** O campo de jogo esconde minas letais (
`0`
). Pior do que isso, qualquer quadrado imediatamente acima, abaixo, à direita ou à esquerda de uma mina ganha o status de "perigo iminente", tornando-se instantaneamente fatal (você explode se pisar). Seu desafio é encontrar a rota de sobrevivência mais curta cruzando todo o campo desde _qualquer_ bloco liberado da primeira coluna à esquerda até escapar por _qualquer_ bloco ileso isolado salvo contínuo da extrema coluna limítrofe à direita. **Intuição:** Um problema complexo que exige um pré-processamento duplo da matriz para identificar ameaças antes de invocar o pesado algoritmo DFS para traçar rotas e tentar otimizar por poda as piores distâncias inviabilizadas baseadas comparando lógicas métricas mínimas globais parciais temporais de referência. **Passo a Passo:**

1.  A priori, crie matriz gêmea espelhada e iterativa correndo com laços estritos toda matriz para identificar e isolar numericamente contornando todo '0' e contaminando as células perimetrais cruzadas laterais para bloqueios inoperáveis inativadas trancadas fechadas limítrofes isolando limites impenetráveis lógicas processuais matemáticas mortais limitadas base.
    
2.  Incorpore variável de salvaguarda 
    `min_dist`
     iniciada com máximo.
    
3.  Inválido começar de destino solitário ou pontos únicos isolados engessados arbitrários pré parametrizado isolado fixo como padrão clássicos padronizados limitantes restritivos base. Invés, use laços rodando a primeira coluna da esquerda, acionando dezenas de instâncias filiais raízes independentes matriz isoladas iteradas buscando inícios prósperos independentes recursivas e separadas nas testagens múltiplas base e limites pontuais iterados de forma sequencial iterativos múltiplos e processuais de checagem raiz recursivas rastreadores sequenciais iniciais pontuais iniciais de base múltiplos testes varredura primários base de explorações exauridos iterativamente múltiplos alocados iniciais sequenciais.
    
4.  Para cada, DFS traça avanços. Otimização Poda Suprema Base Mestra: Se no desenrolar a caminhada o passos 
    `dist_atual`
     excederem a 
    `min_dist`
     previamente achada, aborte galho impiedosamente por ineficiência métrica temporária lógica matemática processual cortando árvore.
    
5.  Achando fim direita atualiza e anota registro numérico mínimo global métrico paramétrico referenciado base alvo.
    
6.  **Backtrack:** Restaure visitados nas voltas.
-   **Input:** 
    `Matriz de jogo recheado de perigos (0 mina explosiva / 1 passagem verde fluida liberada permitida transitáveis limpas)`
    
-   **Output:** 
    `Valor numeral quantificável demonstrando caminhos diretos menores possíveis, ou aviso string flutuante declarativo taxativo resolutivo restritivo limitativo conclusivo texto verbal comunicativo visual informando impraticabilidade impeditiva de trânsito isolante fechado impossibilidade "Rota não existe e travada base".`

### 31\. [Todas as partições palindrômicas exaustivas textuais fragmentadas fatiadas segmentadas disjuntas base paramétricas](https://www.geeksforgeeks.org/dsa/print-palindromic-partitions-string/ "null")

**Descrição:** Dada amálgama palavra base primária sequencial alfabética textual coesa concatenada amarrada linear compacta unificada estruturada unificada limítrofe basal, retalhe fragmentando em sub blocos segmentando os resquícios partes derivados extraindo porções geracionais base paramétricas cortadas menores. Imperativo restritivo crucial lei inquebrável mandatória estrutural lógica absoluta exige impiedosamente imperiosa paramétrica regra limitante que _cada único e exclusivo pedaço originário geracional subtraído derivativo pedaço resíduo_ da segmentação resulte invariavelmente constituindo formar palavras ou caracteres lidos inversamente idênticos iguais matematicamente chamados Palíndromos inegociáveis perimetrais isolados perfeitamente balanceados simétricos textuais lógicos absolutos parametrizados base simétricas lógicos textuais perfeitos alinhados paramétricos de reflexão numérico visuais coesos lógicos restritivos base textuais simétricas perimetral. **Intuição:** DFS caminha pela string construindo um prefixo fatiado iterativamente temporal gradativo limitador paramétrico incremental variável. Se esse bloco prefixo for palíndromo perfeito lógicos estrito, processa as ramificações filhas remanescentes base parametrizadas no resto inexplorado de string residuais cortados derivativos sequencial remanescentes processuais e repetindo processos limpos cíclicos base até sumir toda base limítrofe alvo exaurindo o material bruto total originário massivo inicial restrito limítrofe e contínuo base string original amarrada processuais originais e sequenciais absolutos base cortados. **Passo a Passo:**

1.  Variáveis locais englobadas armazenando 
    `indice`
     de acompanhamento temporal limite paramétrico base métrica e o balde temporal listado vetorial agregador de resquícios partes blocos acumulador paramétricos listas geracionais de fragmentos recolhidos isolados limpos sequencialmente cortados derivados agrupados lista parcial derivativa base.
    
2.  Na lógica laço estrita geracional base referencial for-loop variando encabeçando engatando limite paramétrico limite final variando da partida base inicial local iterada do índice base até bater fronteira final de len string textuais limite métricos da variável massiva limitante total global textual paramétrico final limite de comprimento estrito e absoluto estagnado da matriz original limite numéricos textuais base limítrofe parametrizadas métricos e limite finais texto de tamanhos paramétricas base string texto limite métricos numérico comprimento limite global.
    
3.  Fatie substring temporário referenciado extraído recortado fatiamento gerado 
    `s[indice...i]`
    . Acione ferramenta método booleano acessório secundário paramétrico isolado função paralela acessória independente externa isolada verificação e checagem lógica matemática de balança simétrica verificador "Ispalindromo" simétricos base reflexivo testando igualdades extremidades inversas limitadoras base parametrizadas iterativas lógicas base verificador teste.
    
4.  Ao bater verdadeiro ok na verificação, armazene e pendure galho no seu bucket parcial limite temporal array iterativo derivativos acumulador temporais listas listas resquícios pedaços agregador fragmentos residuais lista fatias cortadas base e acione espelho mergulho recursivo mandando a sobra 
    `s[i+1...FIM]`
     limites métricos residuais alvos limites base numéricos métricos alvos inexplorados cortes sequenciais em novos limites mergulho árvore de execução testando bases e ramificações base subjacentes varreduras testando limites inferiores profundos limites ramificados base sequenciais testadores rastreadores varredura arvore e teste sequenciais limites profundidade rastreadora de base inexplorada rastreamento.
    
5.  Fim encerramento sucesso se índice comer engolir e absorver mastigando todo tamanho length de string referencial atingindo limites finalísticos fronteiriços esgotando estourando esgotando superando margens limite engolindo textuais total final engolido total mastigados fronteiras globais do tamanho da base engolindo strings engolida absorvendo limítrofes exaurido finalístico engolido limites totais length margem limite base textuais exaurindo totais texto engolindo estourando. Grave a lista no referencial mestre acumulador respostas.
    
6.  **Backtrack:** Expulse elimine delete remova arranque fora expurgue subtraia expulse descasque resgate reverta estoure e faça pop no último bloco fragmentado agregado adicionado colado aglutinado inserido enfiado somado empilhado jogado alocado no balde listas agregador temporais parciais antes de rodar fechar girar trancar laço de loop geracional de avanço contínuo sequenciais forçando e forçando induzindo o loop esticar espichar aumentar alargar tracionar engolir dilatar estender fatiar abranger crescer abarcar o prefixo temporal inicial numéricos marginais métricas margens numéricas textuais métricas parametrizadas teste limites progressivos expansivas no seu próprio fluxo avanço limitantes.
-   **Input:** 
    `"nitin"`
    
-   **Output:** 
    `Combinações lógicas restritas listadas derivadas listadas: ["n", "i", "t", "i", "n"], ["n", "iti", "n"], ["nitin"]`

### 32\. [Impressão e visualização gráfica desenhada estrita absoluta visual texturizada de todas ramificadas das totais soluções parciais múltiplas e totais geradas do quebra cabeça e do enigma e do problema de posicionamento tático agressivo bélico das N rainhas N-Queens (Exaustivo All Solutions Visual Render Generator Solver Script Algorithm Backtracking Output Text Array Based Output)](https://www.geeksforgeeks.org/dsa/printing-solutions-n-queen-problem/ "null")

**Descrição:** Tradicional restritivo das Rainhas do tabuleiro. Contudo modificado. E diferente radical e fundamentalmente diametralmente do convencional e focado e direcionado exclusivamente excludente estrito de dar abort e parada súbita travamento freio fechamento corte ao deparar se acidentando com deparando encontrando apenas e somente um único acerto solitário exclusivo unitário válido isolado de repouso configurado do tabuleiro. O seu mandato e objetivo e regra imperiosa exige compelição imposição e a ordem de jamais e nunca não interromper fechar encerrar parar frear cessar trancar de cavoucar rastrear fatiar cavar e dissecar exaurindo secando chupando drenando esvaziando escavando a infinita e grandiosa pesada massiva profunda imensa pesada árvore matemática referencial. Sua tela console e terminal log console e tela render deve piscar transbordar desenhar renderizar preencher jorrar e transbordar grafismos tabelas matrizes de formatações desenhadas alfanuméricos com literalmente todos os gabaritos resolvidos universais paramétricos limitantes estritamente matematicamente e logicamente precisos exatos verídicos corretos base do setup N fornecido. **Intuição:** Uma leve torção alteração e ajuste mecânico estrutural alterado no miolo interno do encerramento motor booleano base condicional primitivo original da estrutura de base condicional lógica algorítmica. Remover estipular apagar extrair suprimir e deletar o comando imperativo condicional excludente paralisante "Retornar True Imediato Freio Interrupção Finalístico Abrupto Abortivo Cortador Limitador Interrompedor Exclusivo Parada Seca Stop e Retorno Positivo Unitário Unitário". Substituindo, trocando alterando modificando isso injetando enxertando colando agregando mesclando um condicional novo registrador agregador armazenador copista duplicador clonador de lista temporária enviando transferindo engolindo absorvendo inserindo enviando colando guardando cópia profunda idêntica integral inteiriça profunda limpa gêmea espelhada exata fiel base matriz clone e mandando forçando cuspindo enviando exigindo e ejetando impelindo e empurrando um cirúrgico "Return False Simulado Falso Falso Enganoso Negativo Revertido Negativo Truncador Desistente Falseado Provocador de Queda de Quebra Induzida Falha Induzida Falseando Enganando Retorno Falso Enganoso", disparando destravando desatando liberando forçando desencadeando ativando induzindo deflagrando proposital e calculadamente provocando matematicamente o Backtracking Forçado retrocesso recuo da chamada do frame processual retornando passos passados iterados anteriores de laço estritos paramétricos recursivos sequenciais ramificadores laços rastreadores varredura processuais varrendo esquadrinhando base. **Passo a Passo:**

1.  Mesmas matrizes primitivas base regras matriz lógicas seguranças check regras is\_safe diagonais e horizontais regras N rainhas.
    
2.  Descida de colunas paramétrica iterativa limitante processual de índice avanço recursivo limite avanço colunas indexação indexado.
    
3.  Chegada em vitória: 
    `if coluna == N`
    . Matriz estourou de acertos preenchimentos vitórias.
    
4.  Nesse if vitórias base: Registre matriz copie clona duplicata gêmea deep array cópia passe referencial limite referências armazene adicione adicione anexe guarde colete reserve junte consolide matriz global master de base paramétrica global lista mestre matriz listadas de resposta listadas absolutas bases mestras referencial listas array de resultados limite array resultado final paramétricos respostas consolidadas base finais absolutas guardadas mestre.
    
5.  Em seguida execute implacável retorne FALSE retorne ZERO retorne FALLBACK falso retorne NULO falso induzindo gatilhos destrutivos. A máquina acha erro e volta rastrear caminhos esquecidos.
    
6.  **Backtrack:** Limpezas tradicionais corriqueiras limpando lixo apagando trilhas.
-   **Input:** 
    `N = 4 parametrizado limite base`
    
-   **Output:** 
    `Arrays renderizadas em tabelas matriz formato strings duplas distintas respostas exatas consolidadas. Solução 1 e Solução 2 impressas de 4x4 N4 limítrofes paramétricas base.`

### 33\. [As totais extensivas múltiplas absolutas infinitas de variação todas subsequências comuns mais longas sequenciais e contínuas entre palavras LCS de cadeias textuais (LCS DP + Print All Backtracking em Ordem Estrutural e Lexicográfica Ordem de Alfabeto Formatadas e Classificadas Limpas e Processuais)](https://www.geeksforgeeks.org/dsa/print-longest-common-sub-sequences-lexicographical-order/ "null")

**Descrição:** O embrião primitivo original matriz problema base formador LCS (Maior Fragmento Subsequente Comum Textuais Alfabético Linear Direcional Contínuo Direcional Coeso Linear Textual Alfanuméricos Embutidos Amarrados Coesos Linear Textuais Comuns Combinadas Cruzadas Direcionais Comum Alfanumérico Sequencial Extensivo) focado e cobrado foca restritivamente apenas encontrar baseando se em programação de memoização e programação processuais e cálculos teóricos de memórias temporais base numéricas processuais base programação paramétricas em matriz base teóricas teóricos dinâmicas DP extrair extraindo achando encontrando buscando calculando exclusivamente meramente isoladamente e numericamente número base escalar restritivo tamanho limitador base numéricos absolutos comprimento limites numéricos matemáticos métrico absoluto numérico do limite do acerto final base numéricos matemáticos absolutos tamanho escalar métrico matriz máximo possível numéricos máximos LCS métricos limite valor length de LCS acerto tamanho textuais limites. E não os caminhos em si. Aqui não. Aqui o terror habita o reino processual. Você deve ir mergulhar retornar explorar reconstruir cavar recuperar extrair ressuscitar buscar minerar imprimir listar resgatar reaver gerar e expor formatadas a luz do sol todas as exatas e puras sequências fragmentos resquícios alfabéticas derivadas LCS cruzadas combinações exatas geradoras palavras lógicas formatadas estritas listadas agrupadas alfabeticamente arranjadas formatadas organizadas lexicograficamente limpas agrupadas lexicográficas formatadas arrumadas matriz lista consolidadas respostas organizadas listadas exatas precisas formatadas limpas. **Intuição:** Uma belíssima dança e união entre a deusa de cálculos absolutos Programação Dinâmica Matrizes base (DP Matrix Builder Limit base tabelas) que constrói os caminhos numéricos como bússola mágica guiadora balizadora orientadora e mestre cartógrafo balizando base referências guiando e os cães batedores farejadores selvagens incansáveis rastreadores do motor e rastreio e escavadeira do mecanismo Backtracking desbravadores rastreadores que usa a bússola para achar voltando pra trás todos os rios trilhas cruzamentos intersecções e desmembramentos ramificações que chegam batem caem escoam descem sobem resultam dão no mesmo numéricos idênticos limites pontuais de mesma exata idênticas perfeitas métricas numéricas alvos idênticas matrizes tamanhos perfeitas iguais métricas de destino referências totais absolutas matemáticas matriz de valor matriz absolutas matriz numéricas exatas tamanhos iguais valores métricos e destino DP alvo máximos finais. **Passo a Passo:**

1.  Roda constrói edifica molda forja ergue a bruta Tabela Matriz Matemática Bidimensional M por N de tamanho limitadores baseando DP LCS limitadora e rastreadora clássicas matemáticas e numéricas absolutas com regras bases LCS base e clássicas de construções tradicionais processuais dinâmicas tradicionais lógicas tradicionais algorítmicas básicas matriz DP bases processuais lógicas e tabelas matriciais tradicionais base matriz preenchidas métricas.
    
2.  Chame invoca acione rode dispare instancie inicie inicialize deflagre o motor Recursivo reverso chamando focado de ponta a ponta chamando limites M e N limites iterativos e a matriz guia.
    
3.  Se char bate em S1\[M\] == S2\[N\] (casou cruzamento uniu juntou bateu engatou anexou cruzou chocou), inclua colete agarre o char na string texto e recursão diagonal m-1 n-1 e mande descer diagonal chamando limítrofes matriz diagonais descida diagonais matriz e recuos diagonais e envios varreduras chamadas diagonais matriz referencial descer rastreando matriz decrescente diagonal mergulho matriz mergulho rastreador bases chamadas recursões decrescente decrescentes diagonais varreduras limitadoras.
    
4.  Divergiu não bateu falso diferente? Observe mire compare analise investigue pondere valores de DP esquerda base (L) e DP acima topo base (T). Se L > T vá esquerda L mergulhe na esquerda L vá desça pra L matriz chame rastreie desça na matriz. Se T > L suba pro T teto topo chame L matriz topo vá e suba.
    
5.  Se L == T (Empatados valores iguais caminhos mágicos ramificados múltiplos rotas duplicatas), Bifurque separe divida ramifique multiplique triplique crie chamadas galhos simultâneos filiais chame crie e desça lance e desça e rastreie ambos os dois independentes varreduras duas buscas nos dois em L esquerda base e T topo separadas gerando e testando independentes exaustivas varreduras criando ramos galhos galhos abrindo dividindo caminhos independentes matriz e lógicas independentes bases e rastreadoras matrizes lógicas independentes arvore de buscas ramos divididos bifurcadas processuais separadamente ramificadas duplas base varreduras separadas lógicas independentes rastreamentos separados varreduras duplas paralelas buscas sequenciais varreduras lógicas paralelas bifurcadas chamadas separadas.
    
6.  Guardar e empilhar agrupar listar hash set hash table agrupar e jogar arrays lists e organizar formatar lexicamente listas listagens ordem formato strings.
-   **Input:** 
    `"abcabcaa", "acbacba"`
    
-   **Output:** 
    `["ababa", "abaca", "abcba", "acaba", "acaca", "acbca"]`

</p>

</details>
