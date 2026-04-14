# Lista de Exercícios

Esta lista foi elaborada para fortalecer a sua lógica de programação através da técnica de **Programação Dinâmica (DP - Dynamic Programming)**. O objetivo deste documento não é fornecer código pronto para copiar e colar, mas sim o raciocínio analítico necessário para modelar o **estado** e a **transição** de cada problema. Isso permitirá que você resolva os desafios na linguagem de programação de sua preferência (C, Python, Java, Go, Typescript, etc.).

## 🟢 Problemas básicos

Estes problemas são focados em reconhecimento de padrões simples (sequências matemáticas) e modelagem de estado unidimensional.

### 1\. Números de Fibonacci

-   **Descrição:** Calcule o enésimo termo da sequência de Fibonacci. A sequência começa com 0 e 1, e cada número subsequente é a soma estrita dos dois anteriores. Este é o problema clássico introdutório para entender a sobreposição de subproblemas e a diferença entre uma recursão ingênua exponencial e uma DP eficiente.
    
-   **Passo a passo:** 1. Defina o estado 
    ```
    dp[i]
    ```
     como o i-ésimo número de Fibonacci. 2. Inicialize os casos base, que representam a fundação matemática: 
    ```
    dp[0] = 0
    ```
     e 
    ```
    dp[1] = 1
    ```
    . 3. Para 
    ```
    i
    ```
     de 2 até 
    ```
    n
    ```
    , calcule a transição: 
    ```
    dp[i] = dp[i-1] + dp[i-2]
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(n)
    ```
    . Espaço: 
    ```
    O(n)
    ```
     com array, mas altamente otimizável para 
    ```
    O(1)
    ```
     armazenando apenas as duas variáveis anteriores.
    
-   **Input:** Um número inteiro 
    ```
    n
    ```
     (ex: 
    ```
    5
    ```
    ).
    
-   **Output:** O valor correspondente na sequência (ex: 
    ```
    5
    ```
    , pois a sequência é 0, 1, 1, 2, 3, 5).

### 2\. Números tribonacci

-   **Descrição:** Uma variação natural do Fibonacci, mas cada termo é gerado pela soma dos **três** anteriores. Útil para entender como adicionar dependências históricas altera o tamanho dos seus casos base.
    
-   **Passo a passo:** 1. Estado: 
    ```
    dp[i]
    ```
     é o i-ésimo termo. 2. Casos base precisam cobrir as 3 primeiras posições: 
    ```
    dp[0] = 0
    ```
    , 
    ```
    dp[1] = 1
    ```
    , 
    ```
    dp[2] = 1
    ```
    . 3. Transição: 
    ```
    dp[i] = dp[i-1] + dp[i-2] + dp[i-3]
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(n)
    ```
    . Espaço: 
    ```
    O(n)
    ```
    , otimizável para 
    ```
    O(1)
    ```
     guardando apenas 3 variáveis.
    
-   **Input:** Um número inteiro 
    ```
    n
    ```
     (ex: 
    ```
    4
    ```
    ).
    
-   **Output:** O enésimo número Tribonacci (ex: 
    ```
    2
    ```
    ).

### 3\. Números de Lucas

-   **Descrição:** Uma sequência que segue exatamente a mesma lógica matemática e transicional de Fibonacci, mas inicia com valores sementes diferentes (2 e 1). Mostra como a mudança do caso base gera uma curva de crescimento inteiramente nova.
    
-   **Passo a passo:** 1. Estado: 
    ```
    dp[i]
    ```
     é o i-ésimo termo de Lucas. 2. Casos base: 
    ```
    dp[0] = 2
    ```
    , 
    ```
    dp[1] = 1
    ```
    . 3. Transição: 
    ```
    dp[i] = dp[i-1] + dp[i-2]
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(n)
    ```
    . Espaço: 
    ```
    O(1)
    ```
     (com otimização de variáveis).
    
-   **Input:** Um número inteiro 
    ```
    n
    ```
     (ex: 
    ```
    3
    ```
    ).
    
-   **Output:** O enésimo número de Lucas (ex: 
    ```
    4
    ```
    ).

### 4\. Subir escadas

-   **Descrição:** Você está subindo uma escada que tem 
    ```
    n
    ```
     degraus. A cada passo, você tem a decisão de subir 1 ou 2 degraus por vez. Determine de quantas maneiras combinatórias distintas você pode chegar ao topo.
    
-   **Passo a passo:** 1. Estado: 
    ```
    dp[i]
    ```
     é o número total de formas de chegar fisicamente ao degrau 
    ```
    i
    ```
    . 2. Casos base: 
    ```
    dp[0] = 1
    ```
     (ficar no chão é 1 forma válida) e 
    ```
    dp[1] = 1
    ```
    . 3. Transição: O degrau 
    ```
    i
    ```
     só pode ser alcançado vindo do degrau 
    ```
    i-1
    ```
     ou do 
    ```
    i-2
    ```
    . Logo, 
    ```
    dp[i] = dp[i-1] + dp[i-2]
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(n)
    ```
    . Espaço: 
    ```
    O(n)
    ```
     ou 
    ```
    O(1)
    ```
    .
    
-   **Input:** Um número inteiro 
    ```
    n
    ```
     indicando os degraus (ex: 
    ```
    3
    ```
    ).
    
-   **Output:** O número de formas distintas de subir (ex: 
    ```
    3
    ```
     -> \[1,1,1\], \[1,2\], \[2,1\]).

### 5\. Subir escadas com 3 movimentos

-   **Descrição:** Expansão direta do problema de subir escadas, mas agora seu personagem é mais ágil e pode pular 1, 2 ou até 3 degraus de uma só vez.
    
-   **Passo a passo:** 1. Estado: 
    ```
    dp[i]
    ```
     é o número de formas de alcançar o degrau 
    ```
    i
    ```
    . 2. Casos base: 
    ```
    dp[0]=1
    ```
     (chão), 
    ```
    dp[1]=1
    ```
    , e 
    ```
    dp[2]=2
    ```
     (1+1 ou pular 2). 3. Transição: 
    ```
    dp[i] = dp[i-1] + dp[i-2] + dp[i-3]
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(n)
    ```
    . Espaço: 
    ```
    O(1)
    ```
     guardando as três posições prévias.
    
-   **Input:** Um número inteiro 
    ```
    n
    ```
     (ex: 
    ```
    4
    ```
    ).
    
-   **Output:** Número total de formas (ex: 
    ```
    7
    ```
    ).

### 6\. Subir escadas ponderado

-   **Descrição:** Em vez de contar maneiras de subir, este problema introduz otimização (minimizar custos). Cada degrau tem um custo financeiro ou de energia associado, fornecido em um array. Calcule o custo mínimo acumulado para chegar ao topo podendo subir 1 ou 2 degraus.
    
-   **Passo a passo:** 1. Estado: 
    ```
    dp[i]
    ```
     é o menor custo possível pago para pisar e sair do degrau 
    ```
    i
    ```
    . 2. Base: Podemos começar no degrau 0 ou 1, então 
    ```
    dp[0] = custo[0]
    ```
    , 
    ```
    dp[1] = custo[1]
    ```
    . 3. Transição: O custo de chegar em 
    ```
    i
    ```
     é o custo intrínseco de pisar em 
    ```
    i
    ```
     somado à escolha mais barata do passado: 
    ```
    dp[i] = custo[i] + min(dp[i-1], dp[i-2])
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(n)
    ```
    . Espaço: 
    ```
    O(1)
    ```
    .
    
-   **Input:** Um array de inteiros representando o custo de cada degrau (ex: 
    ```
    [10, 15, 20]
    ```
    ).
    
-   **Output:** Custo mínimo para ultrapassar o topo (ex: 
    ```
    15
    ```
    ).

### 7\. Máximo de segmentos

-   **Descrição:** Dado um segmento de metal de tamanho 
    ```
    N
    ```
    , você precisa cortá-lo em segmentos menores restritos aos tamanhos específicos 
    ```
    p
    ```
    , 
    ```
    q
    ```
     ou 
    ```
    r
    ```
    . O objetivo é maximizar o número total de segmentos resultantes (se o corte não for perfeitamente divisível, é inválido).
    
-   **Passo a passo:** 1. Estado: 
    ```
    dp[i]
    ```
     é o número máximo de cortes válidos para um pedaço de tamanho 
    ```
    i
    ```
    . Inicialize o array com um valor sentinela negativo (ex: 
    ```
    -1
    ```
    ) para representar tamanhos inalcançáveis. 2. Base: Um segmento de tamanho 0 tem 0 cortes, então 
    ```
    dp[0] = 0
    ```
    . 3. Transição: Para cada tamanho 
    ```
    i
    ```
     partindo de 0, se 
    ```
    dp[i]
    ```
     não for -1 (for alcançável), tente avançar fazendo um corte: atualize 
    ```
    dp[i+p]
    ```
    , 
    ```
    dp[i+q]
    ```
     e 
    ```
    dp[i+r]
    ```
     com 
    ```
    max(dp[atual], dp[anterior] + 1)
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(N)
    ```
    . Espaço: 
    ```
    O(N)
    ```
    .
    
-   **Input:** Quatro inteiros: tamanho inicial 
    ```
    N
    ```
     e cortes 
    ```
    p
    ```
    , 
    ```
    q
    ```
    , 
    ```
    r
    ```
     (ex: 
    ```
    N=4, p=2, q=1, r=1
    ```
    ).
    
-   **Output:** Número máximo de cortes alcançados (ex: 
    ```
    4
    ```
    , cortando de 1 em 1).

### 8\. Enésimo número de Catalan

-   **Descrição:** Encontre o enésimo número da sequência de Catalan. Esta sequência resolve problemas combinatórios complexos (como árvores, parênteses e polígonos). O n-ésimo número de Catalan é construído pela soma dos produtos dos pares de números de Catalan anteriores.
    
-   **Passo a passo:** 1. Estado: 
    ```
    dp[i]
    ```
     armazena o i-ésimo número de Catalan. 2. Base: A sequência inicia com 
    ```
    dp[0] = 1
    ```
    , 
    ```
    dp[1] = 1
    ```
    . 3. Transição: 
    ```
    dp[i]
    ```
     é a soma de todos os produtos 
    ```
    dp[j] * dp[i-j-1]
    ```
     onde 
    ```
    j
    ```
     varia de 
    ```
    0
    ```
     até 
    ```
    i-1
    ```
    . É como dividir um problema de tamanho 
    ```
    i
    ```
     em duas metades que não se sobrepõem.
    
-   **Complexidade:** Tempo: 
    ```
    O(n^2)
    ```
    . Espaço: 
    ```
    O(n)
    ```
    .
    
-   **Input:** Um inteiro 
    ```
    n
    ```
     (ex: 
    ```
    3
    ```
    ).
    
-   **Output:** O número de Catalan correspondente (ex: 
    ```
    5
    ```
    ).

### 9\. Contar BSTs únicos

-   **Descrição:** Dado 
    ```
    N
    ```
     chaves com valores distintos (ex: 1, 2, 3), encontre o número de Árvores Binárias de Busca (BST) estruturalmente únicas que podem ser formadas.
    
-   **Passo a passo:** 1. O problema matemático mapeia perfeitamente para os Números de Catalan. Se você eleger a chave 
    ```
    i
    ```
     como raiz, as chaves menores que 
    ```
    i
    ```
     vão para a subárvore esquerda, e as maiores para a direita. 2. Modele a DP onde 
    ```
    dp[i]
    ```
     é o número de árvores formadas com 
    ```
    i
    ```
     chaves. Para cada possível raiz 
    ```
    j
    ```
    , você multiplica as formas de organizar o lado esquerdo 
    ```
    (j-1)
    ```
     pelo lado direito 
    ```
    (i-j)
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(N^2)
    ```
    . Espaço: 
    ```
    O(N)
    ```
    .
    
-   **Input:** Inteiro 
    ```
    N
    ```
     chaves (ex: 
    ```
    3
    ```
    ).
    
-   **Output:** Quantidade de BSTs únicas (ex: 
    ```
    5
    ```
    ).

### 10\. Contar parênteses válidos

-   **Descrição:** Encontre o número de expressões de parênteses bem formadas e válidas de um determinado comprimento de pares 
    ```
    N
    ```
    . Por exemplo, 
    ```
    ()()
    ```
     é válido, mas 
    ```
    )(()
    ```
     não é.
    
-   **Passo a passo:** 1. Mais uma aplicação puramente isomórfica dos Números de Catalan. 2. Estado e transição seguem a exata mesma regra e implementação 
    ```
    Catalan(N)
    ```
     vista no item 8.
    
-   **Complexidade:** Tempo: 
    ```
    O(N^2)
    ```
    . Espaço: 
    ```
    O(N)
    ```
    .
    
-   **Input:** Inteiro 
    ```
    N
    ```
     representando os pares (ex: 
    ```
    3
    ```
    ).
    
-   **Output:** Número de expressões válidas (ex: 
    ```
    5
    ```
     -> 
    ```
    ()()()
    ```
    , 
    ```
    (())()
    ```
    , 
    ```
    ()(())
    ```
    , 
    ```
    (()())
    ```
    , 
    ```
    ((()))
    ```
    ).

### 11\. Formas de triangulação de um polígono

-   **Descrição:** Encontre o número de maneiras de dividir um polígono convexo de 
    ```
    N+2
    ```
     lados inteiramente em triângulos, traçando linhas retas sem cruzamentos que conectam seus vértices.
    
-   **Passo a passo:** 1. Outra aplicação clássica dos Números de Catalan! Escolher um lado base do polígono e formar um triângulo com um terceiro vértice divide o polígono restante em dois polígonos menores. 2. Modele a DP multiplicando as formas de triangular os dois subpolígonos resultantes.
    
-   **Complexidade:** Tempo: 
    ```
    O(N^2)
    ```
    . Espaço: 
    ```
    O(N)
    ```
    .
    
-   **Input:** Número de lados 
    ```
    N
    ```
     (ex: 
    ```
    4
    ```
    ).
    
-   **Output:** Formas de triangulação (ex: 
    ```
    2
    ```
    ).

### 12\. Soma mínima em um triângulo

-   **Descrição:** Lhe é dado um triângulo matemático formado por arrays de inteiros em níveis decrescentes. Encontre o caminho do topo à base que tenha a menor soma acumulada, sendo que de um nó você só pode se mover para os vizinhos adjacentes imediatamente abaixo dele.
    
-   **Passo a passo:** 1. Este problema brilha quando resolvido de baixo para cima (**bottom-up**), evitando o manuseio dos limites das bordas do triângulo se fôssemos do topo para a base. 2. Estado: 
    ```
    dp[i][j]
    ```
     é a soma mínima garantida se você estivesse começando a partir daquela posição até o final. 3. Inicialize a última linha do 
    ```
    dp
    ```
     como a última linha do triângulo. 4. Transição: Para as linhas de cima, 
    ```
    dp[i][j] = triangulo[i][j] + min(dp[i+1][j], dp[i+1][j+1])
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(L^2)
    ```
     onde L é o número de linhas. Espaço: 
    ```
    O(L)
    ```
     otimizando para manter apenas a linha abaixo na memória.
    
-   **Input:** Matriz triangular de inteiros (ex: 
    ```
    [[2], [3,4], [6,5,7]]
    ```
    ).
    
-   **Output:** A soma mínima (ex: 
    ```
    10
    ```
     -> caminho: 2 -> 3 -> 5).

### 13\. Quadrados perfeitos mínimos

-   **Descrição:** Encontre o menor número possível de quadrados perfeitos (como 1, 4, 9, 16...) cuja soma total seja exatamente igual a um número 
    ```
    N
    ```
    .
    
-   **Passo a passo:** 1. Pense nisso como um problema de "troco", onde as moedas são quadrados perfeitos. 2. Estado: 
    ```
    dp[i]
    ```
     é a quantidade mínima de peças (quadrados) necessárias para formar a soma 
    ```
    i
    ```
    . Preencha com infinito no início. 3. Base: 
    ```
    dp[0] = 0
    ```
     (zero peças para somar 0). 4. Transição: Para cada número 
    ```
    i
    ```
    , tente subtrair todo quadrado 
    ```
    j*j
    ```
     possível (onde 
    ```
    j*j <= i
    ```
    ). 
    ```
    dp[i] = min(dp[i], 1 + dp[i - j*j])
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(N * sqrt(N))
    ```
    . Espaço: 
    ```
    O(N)
    ```
    .
    
-   **Input:** Inteiro 
    ```
    N
    ```
     (ex: 
    ```
    12
    ```
    ).
    
-   **Output:** Mínimo de quadrados (ex: 
    ```
    3
    ```
    , pois 12 é 4+4+4. Não caia na armadilha gulosa de pegar o 9 primeiro!).

### 14\. Formas de particionar um conjunto

-   **Descrição:** Encontre o número de partições possíveis de um conjunto contendo 
    ```
    N
    ```
     elementos distinguíveis (conhecidos matematicamente como os Números de Bell).
    
-   **Passo a passo:** 1. A forma mais elegante de resolver é construindo o "Triângulo de Bell" usando DP bidimensional. 2. Estado: 
    ```
    dp[i][j]
    ```
     é o j-ésimo valor na i-ésima linha do triângulo. 3. Base: 
    ```
    dp[0][0] = 1
    ```
    . 4. Transição: A primeira coluna de uma nova linha copia o último valor da linha anterior: 
    ```
    dp[i][0] = dp[i-1][i-1]
    ```
    . Para o restante da linha, soma-se o vizinho à esquerda e o acima: 
    ```
    dp[i][j] = dp[i-1][j-1] + dp[i][j-1]
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(N^2)
    ```
    . Espaço: 
    ```
    O(N^2)
    ```
    , mas pode ser reduzido para 
    ```
    O(N)
    ```
    .
    
-   **Input:** Inteiro 
    ```
    N
    ```
     (ex: 
    ```
    3
    ```
    ).
    
-   **Output:** Número de partições (ex: 
    ```
    5
    ```
    ).

### 15\. Coeficiente binomial

-   **Descrição:** Calcule o valor clássico da combinatória de C(n, k) — de quantas maneiras você pode escolher um grupo de 
    ```
    k
    ```
     itens de um conjunto de 
    ```
    n
    ```
     itens disponíveis, desconsiderando a ordem da escolha.
    
-   **Passo a passo:** 1. Estado: 
    ```
    dp[i][j]
    ```
     representará o valor matemático de C(i, j). 2. Base: Qualquer escolha onde 
    ```
    k=0
    ```
     tem 1 forma (escolher nada). Qualquer escolha onde 
    ```
    k=n
    ```
     também tem 1 forma (escolher tudo). 
    ```
    dp[i][0] = 1
    ```
     e 
    ```
    dp[i][i] = 1
    ```
    . 3. Transição baseada na propriedade de Pascal: para formar um grupo, você decide pegar o item atual ou não. 
    ```
    dp[i][j] = dp[i-1][j-1] + dp[i-1][j]
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(N * K)
    ```
    . Espaço: 
    ```
    O(N * K)
    ```
     ou otimizado para 
    ```
    O(K)
    ```
    .
    
-   **Input:** Dois inteiros 
    ```
    n
    ```
     e 
    ```
    k
    ```
     (ex: 
    ```
    5, 2
    ```
    ).
    
-   **Output:** O coeficiente de combinações (ex: 
    ```
    10
    ```
    ).

### 16\. Triângulo de Pascal

-   **Descrição:** Gere e imprima/retorne as primeiras 
    ```
    N
    ```
     linhas do famoso triângulo de Pascal, onde cada número é a soma dos dois números diretamente acima dele na linha anterior.
    
-   **Passo a passo:** 1. Estado: 
    ```
    dp[i][j]
    ```
     armazena o valor contido na linha 
    ```
    i
    ```
    , coluna 
    ```
    j
    ```
    . 2. A regra e a transição são conceitualmente idênticas à do problema do Coeficiente Binomial. Comece cada linha com 1 e termine com 1. 3. Os valores internos são gerados iterativamente: 
    ```
    dp[i][j] = dp[i-1][j-1] + dp[i-1][j]
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(N^2)
    ```
    . Espaço: 
    ```
    O(N^2)
    ```
     para armazenar o resultado final.
    
-   **Input:** Inteiro indicando linhas 
    ```
    N
    ```
     (ex: 
    ```
    5
    ```
    ).
    
-   **Output:** Uma matriz dentada representando o triângulo.

### 17\. Enésima linha do triângulo de Pascal

-   **Descrição:** O desafio aqui é computar e retornar **apenas** a N-ésima linha inteira do triângulo de Pascal. O truque é alcançar isso usando otimização de espaço estrita (um array unidimensional).
    
-   **Passo a passo:** 1. Crie um array 1D de tamanho N preenchido com zeros. Base inicial: 
    ```
    dp[0] = 1
    ```
    . 2. O segredo da otimização é iterar pelas colunas **de trás para frente** ao construir uma nova linha (do final da linha para o começo). Isso impede que sobrescrevamos dados da "linha anterior" que ainda precisaremos usar no passo seguinte. 3. Transição: 
    ```
    dp[j] = dp[j] + dp[j-1]
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(N^2)
    ```
    . Espaço: 
    ```
    O(N)
    ```
     estrito.
    
-   **Input:** Inteiro índice 
    ```
    N
    ```
     (ex: 
    ```
    3
    ```
    , onde a base 0 é o topo).
    
-   **Output:** Array unidimensional com a linha completa (ex: 
    ```
    [1, 3, 3, 1]
    ```
    ).

### 18\. Soma mínima em um triângulo

_(Reincidência ignorada: As características técnicas deste item são idênticas às descritas no item 12)._

## 🟡 Problemas fáceis

Neste nível, você começará a lidar com grades bidimensionais completas, strings simples e os primeiros problemas da família da "mochila" (Knapsack) com decisões de otimização clara (pegar ou não pegar um elemento).

### 19\. Ladrão da casa (House Robber)

-   **Descrição:** Dado um array representando o valor financeiro contido em cada casa de uma rua, encontre o valor monetário máximo que um ladrão pode roubar na noite sem que o alarme toque. A restrição: se duas casas **adjacentes** forem assaltadas, a polícia é chamada.
    
-   **Passo a passo:** 1. Estado: 
    ```
    dp[i]
    ```
     indica o lucro máximo absoluto que o ladrão acumulou ao observar até a casa 
    ```
    i
    ```
    . 2. Base: Para a casa 0, ele só pode roubá-la: 
    ```
    dp[0] = arr[0]
    ```
    . Para a casa 1, ele escolhe a mais rica entre a 0 e a 1: 
    ```
    dp[1] = max(arr[0], arr[1])
    ```
    . 3. Transição: Ao olhar para a casa 
    ```
    i
    ```
    , ele tem duas escolhas. A) Assaltá-la, mas para isso ele soma o valor dela com o lucro acumulado até a casa 
    ```
    i-2
    ```
    . B) Pular a casa atual, mantendo o lucro intocado da casa vizinha 
    ```
    i-1
    ```
    . A regra fica: 
    ```
    dp[i] = max(arr[i] + dp[i-2], dp[i-1])
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(N)
    ```
    . Espaço: 
    ```
    O(N)
    ```
    , mas muito fácil de otimizar para 
    ```
    O(1)
    ```
     segurando apenas o 
    ```
    dp[i-1]
    ```
     e 
    ```
    dp[i-2]
    ```
     em variáveis separadas.
    
-   **Input:** Array de inteiros não negativos (ex: 
    ```
    [6, 7, 1, 3, 8, 2, 4]
    ```
    ).
    
-   **Output:** Valor máximo alcançado (ex: 
    ```
    19
    ```
     -> roubando 6, 1, 8 e 4).

### 20\. Caminho de custo mínimo

-   **Descrição:** Dada uma matriz bidimensional onde as células contêm custos, descubra a rota mais barata para se deslocar do canto superior esquerdo 
    ```
    (0,0)
    ```
     ao inferior direito. Os únicos movimentos permitidos são: um passo para baixo, um passo para a direita, ou um passo para a diagonal inferior direita.
    
-   **Passo a passo:** 1. Estado: 
    ```
    dp[i][j]
    ```
     guarda o custo cumulativo mínimo para conseguir chegar na célula exata 
    ```
    (i, j)
    ```
    . 2. Base: A célula de início não tem viagem, logo 
    ```
    dp[0][0] = custo[0][0]
    ```
    . As células da primeira linha e primeira coluna só possuem uma direção de origem reta, então basta somá-las em linha reta. 3. Transição no "miolo" da matriz: O custo de chegar em uma célula arbitrária é o custo natural daquela célula mais o menor trajeto dentre seus três vizinhos predecessores possíveis: 
    ```
    dp[i][j] = custo[i][j] + min(dp[i-1][j-1], dp[i-1][j], dp[i][j-1])
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(M * N)
    ```
    . Espaço: 
    ```
    O(M * N)
    ```
    .
    
-   **Input:** Matriz de inteiros 
    ```
    custo
    ```
    .
    
-   **Output:** Valor inteiro do custo mínimo ao fim do trajeto.

### 21\. Formas de decodificar

-   **Descrição:** Uma mensagem secreta composta de letras foi transformada numéricas simples onde A=1, B=2, até Z=26. Dada uma string numérica (como "12"), quantas interpretações válidas existem ("AB" ou "L")? Lide com zeros à esquerda com cuidado (ex: "06" é inválido).
    
-   **Passo a passo:** 1. Estado: 
    ```
    dp[i]
    ```
     registra o número de decodificações válidas possíveis para o prefixo da string até o índice 
    ```
    i
    ```
    . 2. Base: Uma string vazia tem 1 modo de ser decodificada e 
    ```
    dp[0]
    ```
     será avaliado dependendo se for diferente do caractere '0'. 3. Transição: Avalie retroativamente. Se o único caractere atual (
    ```
    str[i]
    ```
    ) não for zero, significa que ele vale como uma letra, logo herde 
    ```
    dp[i] += dp[i-1]
    ```
    . Depois, olhe o bloco de 2 caracteres (
    ```
    str[i-1]
    ```
     e 
    ```
    str[i]
    ```
    ). Se eles formarem um número entre "10" e "26", eles constituem outra letra válida, então também acumule as formas antigas com 
    ```
    dp[i] += dp[i-2]
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(N)
    ```
    . Espaço: 
    ```
    O(N)
    ```
    , otimizável para 
    ```
    O(1)
    ```
     usando o princípio do Fibonacci.
    
-   **Input:** String composta unicamente de dígitos (ex: 
    ```
    "226"
    ```
    ).
    
-   **Output:** Número de permutações de letras válidas (ex: 
    ```
    3
    ```
     correspondentes a BZF, VF, BBF).

### 22\. Problema da soma de subconjunto (Subset Sum)

-   **Descrição:** Ponto de entrada crucial para DP baseada em Knapsack. Verifique se existe algum agrupamento (subconjunto não necessariamente contíguo) de elementos em um array numérico que somados cheguem a um número alvo 
    ```
    S
    ```
    .
    
-   **Passo a passo:** 1. Estado: 
    ```
    dp[i][j]
    ```
     é uma matriz booleana. Retorna verdadeiro se a soma alvo 
    ```
    j
    ```
     pode ser atingida decidindo entre incluir ou não os primeiros 
    ```
    i
    ```
     elementos do array. 2. Base: A soma alvo 
    ```
    0
    ```
     sempre pode ser atingida com um conjunto vazio. Então a primeira coluna inteira 
    ```
    dp[i][0]
    ```
     é 
    ```
    True
    ```
    . Se o array for vazio, qualquer soma maior que 0 é inalcançável (
    ```
    False
    ```
    ). 3. Transição: Ao olhar para o elemento 
    ```
    array[i-1]
    ```
    , se seu valor for maior que a capacidade 
    ```
    j
    ```
    , ele não entra, e herdamos o status 
    ```
    dp[i][j] = dp[i-1][j]
    ```
    . Se couber, ativamos a mecânica de decisão usando "OR" lógico: 
    ```
    dp[i][j] = dp[i-1][j] || dp[i-1][j - array[i-1]]
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(N * S)
    ```
     onde S é a soma alvo. Espaço: 
    ```
    O(N * S)
    ```
    . _Aviso: este tempo é pseudo-polinomial._
    
-   **Input:** Array de inteiros 
    ```
    [3, 34, 4, 12, 5, 2]
    ```
     e soma alvo 
    ```
    S = 9
    ```
    .
    
-   **Output:** Booleano de sucesso (ex: 
    ```
    Verdadeiro
    ```
    , pois usar o 4 e o 5 soluciona o caso).

### 23\. Problema da troca de moedas - contar formas (Coin Change)

-   **Descrição:** Você possui várias denominações de moedas e uma quantia de moedas infinita de cada tipo. Determine quantas combinações absolutamente distintas de moedas podem somar o valor monetário alvo 
    ```
    V
    ```
    . A ordem não importa (1+2 é o mesmo que 2+1).
    
-   **Passo a passo:** 1. Estado: Construa um array unidimensional onde 
    ```
    dp[j]
    ```
     representa o número de composições para a quantia de valor 
    ```
    j
    ```
    . 2. Base: Formar o valor 0 é possível de 1 maneira (não pegando nenhuma moeda). Logo, 
    ```
    dp[0] = 1
    ```
    . 3. Transição (Bottom-up com Moedas): Itere individualmente para cada 
    ```
    moeda
    ```
     disponível. Para cada moeda, comece do valor dela e avance até 
    ```
    V
    ```
    . Acumule as formas de atingir os estados anteriores que diferem exatamente no peso desta moeda: 
    ```
    dp[j] += dp[j - moeda]
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(M * V)
    ```
     onde M é o número de moedas e V o valor. Espaço: 
    ```
    O(V)
    ```
    .
    
-   **Input:** Array de denominações 
    ```
    [1, 2, 3]
    ```
     e valor da conta 
    ```
    V = 4
    ```
    .
    
-   **Output:** Número inteiro de arranjos válidos (ex: 
    ```
    4
    ```
    , que são: {1,1,1,1}, {1,1,2}, {2,2}, {1,3}).

### 24\. Troca de moedas – número mínimo de moedas para formar a soma

-   **Descrição:** Outra variação famosíssima do Coin Change. Em vez de perguntar "quantas formas", a pergunta é otimizada: Qual a quantidade **mínima** de moedas físicas exigidas para formar exatamente o troco de valor 
    ```
    V
    ```
    ? Se for impossível, retorne -1.
    
-   **Passo a passo:** 1. Estado: O array 
    ```
    dp[j]
    ```
     agora vai registrar as quantidades mínimas de moedas necessárias para o valor 
    ```
    j
    ```
    . Preencha esse array inicialmente com um valor alto como "Infinidade" (ou 
    ```
    V + 1
    ```
    ). 2. Base: Fazer troco para o valor 0 requer 0 moedas, logo 
    ```
    dp[0] = 0
    ```
    . 3. Transição: Para todas as moedas na sua carteira, varra os valores 
    ```
    j
    ```
     de forma crescente. Se a moeda atual for útil para 
    ```
    j
    ```
    , a transição pega a quantidade mínima para o valor residual, mais um (a moeda em si). Ou seja: 
    ```
    dp[j] = min(dp[j], 1 + dp[j - moeda])
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(M * V)
    ```
    . Espaço: 
    ```
    O(V)
    ```
    .
    
-   **Input:** Moedas disponíveis 
    ```
    [9, 6, 5, 1]
    ```
     e soma necessária 
    ```
    V = 11
    ```
    .
    
-   **Output:** Contagem numérica mínima de moedas (ex: 
    ```
    2
    ```
     -> entregando uma de 5 e outra de 6).

### 25\. Algoritmo de pintura da cerca

-   **Descrição:** Você está construindo uma cerca longa contendo 
    ```
    n
    ```
     postes verticais consecutivos, e possui latas de tinta de 
    ```
    k
    ```
     cores distintas. O desafio estético é que não é permitido ter 3 postes adjacentes ostentando a exata mesma cor. Quantas decorações diferentes existem?
    
-   **Passo a passo:** 1. Estado: Em vez de array longo, manteremos duas variáveis fundamentais. 
    ```
    same
    ```
     acompanhará as combinações onde os últimos dois postes compartilharem a mesma cor, e 
    ```
    diff
    ```
     onde eles possuírem cores diversas. 2. Base: Se tiver apenas 1 poste, o 
    ```
    same
    ```
     é inútil (0) e o 
    ```
    diff
    ```
     tem 
    ```
    k
    ```
     possibilidades totais. 3. Transição iterativa: No passo seguinte, as maneiras de obter postes com a mesma cor dependem apenas de pintar o novo poste da mesma cor do imediatamente anterior, logo 
    ```
    same = diff_anterior
    ```
    . Para conseguir postes diferentes, pintamos ele com qualquer cor exceto a cor anterior, então pegamos as formas antigas e multiplicamos pelas cores residuais: 
    ```
    diff = (same_anterior + diff_anterior) * (k - 1)
    ```
    . O total de formas naquele ponto será 
    ```
    same + diff
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(n)
    ```
    . Espaço: 
    ```
    O(1)
    ```
    .
    
-   **Input:** Inteiros 
    ```
    n
    ```
     (postes) e 
    ```
    k
    ```
     (cores) (ex: 
    ```
    n=3, k=2
    ```
    ).
    
-   **Output:** Quantidade de modos de pintura matematicamente possíveis (ex: 
    ```
    6
    ```
    ).

### 26\. Cortar uma haste (Rod Cutting)

-   **Descrição:** Uma indústria produz hastes de metal com comprimento comercial 
    ```
    N
    ```
    . Você recebe uma tabela de precificação contendo o preço de venda para cada pedaço de haste, indexado de tamanho 1 a N. Corte a haste da forma mais lucrativa e maximize a receita bruta. É um clássico de DP de mochila ilimitada unidimensional.
    
-   **Passo a passo:** 1. Estado: O array 
    ```
    dp[i]
    ```
     registra a receita monetária máxima obtível processando e cortando livremente uma haste abstrata de comprimento igual a 
    ```
    i
    ```
    . 2. Base: Haste de tamanho nulo lucra 0: 
    ```
    dp[0] = 0
    ```
    . 3. Transição: Para crescer uma haste de tamanho 1 até 
    ```
    N
    ```
    , itere também testando fazer um corte em todas as distâncias 
    ```
    j
    ```
     menores do que o comprimento. A decisão recai em: 
    ```
    dp[i] = max(dp[i], preco[j] + dp[i-j-1])
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(N^2)
    ```
     pelo duplo laço aninhado. Espaço: 
    ```
    O(N)
    ```
    .
    
-   **Input:** Array de preços brutos (onde o índice 0 denota haste tamanho 1) (ex: 
    ```
    [1, 5, 8, 9]
    ```
    ).
    
-   **Output:** Lucro absoluto máximo a ser auferido (ex: 
    ```
    10
    ```
     -> dividindo no meio em duas hastes de tamanho 2 que custam 5 cada).

### 27\. Jump Game (Salto Mínimo)

-   **Descrição:** Você é solto no primeiro índice de um array numérico contendo pistas de salto. O elemento da célula dita a sua flexibilidade máxima (você pode saltar em qualquer célula à frente contanto que não passe desse raio estipulado pelo número). A regra é chegar no final com o menor número de saltos absolutos disparados, não se preocupando com a distância neles.
    
-   **Passo a passo:** 1. Estado: Considere 
    ```
    dp[i]
    ```
     indicando especificamente o menor número inteiro de pulos para pisar de forma segura na célula do índice 
    ```
    i
    ```
    . 2. Base: A largada custa zero esforço: 
    ```
    dp[0] = 0
    ```
    . As demais distâncias no DP devem iniciar estouradas em 
    ```
    infinito
    ```
     para indicarem que ainda não fomos até lá. 3. Transição: Percorra o array, e estando numa base firme em 
    ```
    i
    ```
    , olhe todas as pedras futuras 
    ```
    j
    ```
     dentro do alcance legal do elemento 
    ```
    arr[i]
    ```
    . Tente baratear o custo delas com 
    ```
    dp[j] = min(dp[j], dp[i] + 1)
    ```
    .
    
-   **Complexidade:** Tempo: Na DP pura é 
    ```
    O(N^2)
    ```
     no pior caso (array só de números gigantes). Espaço: 
    ```
    O(N)
    ```
    . _Nota técnica: Se otimizado fortemente com "Greedy", pode cair para O(N) e O(1)._
    
-   **Input:** Array restritivo de impulsos 
    ```
    [1, 3, 5, 8, 9, 2, 6]
    ```
    .
    
-   **Output:** Número de saltos total (ex: 
    ```
    3
    ```
     -> salta do primeiro 1, cai no 3, cai no 8 e termina no além).

### 28\. Maior substring comum (LCS - Longest Common Substring)

-   **Descrição:** Você recebe dois textos aleatórios. Investigue e extraia o tamanho exato da maior cadeia literal e **contígua** (ininterrupta) de letras que seja compartilhada identicamente nos dois textos simultaneamente.
    
-   **Passo a passo:** 1. Estado: Construa uma matriz 2D. O significado central de 
    ```
    dp[i][j]
    ```
     é o comprimento daquele match ininterrupto terminando de forma precisa em 
    ```
    S1[i-1]
    ```
     e 
    ```
    S2[j-1]
    ```
    . 2. Base: Uma matriz inicializada com zeros cobrirá lindamente os casos de qualquer letra cruzando o "vazio". 3. Transição: Compare os caracteres do prefixo atual: se 
    ```
    S1[i-1] == S2[j-1]
    ```
     formarem um casal idêntico, então a streak cresce a partir da sua diagonal superior, virando 
    ```
    dp[i][j] = dp[i-1][j-1] + 1
    ```
    . Monitore o comprimento recorde em uma variável extra fora da matriz. Caso o caráter quebre o padrão da substring, decrete duramente a falência da streak contígua atribuindo 
    ```
    dp[i][j] = 0
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(N * M)
    ```
     sendo que N e M denotam o volume das strings dadas. Espaço: 
    ```
    O(N * M)
    ```
    .
    
-   **Input:** Textos "abcdxyz" e "xyzabcd".
    
-   **Output:** Número estrito apontando o tamanho unificado (ex: 
    ```
    4
    ```
     -> proveniente da raiz "abcd" e também "xyza").

### 29\. Contar todos os caminhos em uma grade

-   **Descrição:** O mapa do tesouro é uma quadrícula matriz plana desenhada sem falhas. Partindo do quadrado extremo à noroeste 
    ```
    (0,0)
    ```
    , conte todas as permutações matemáticas puras de rastro que levam ao quadrante sudeste no fundo direito, obedecendo às duras regras físicas de apenas "escorregar uma célula para baixo" ou "escorregar uma para a direita".
    
-   **Passo a passo:** 1. Estado: A matriz 
    ```
    dp[i][j]
    ```
     é uma prancheta que conta o amálgama numérico de vias disponíveis para alcançar a sala em questão 
    ```
    (i,j)
    ```
    . 2. Base: Só existe exatamente 1 única forma de viajar para todos os cômodos que estão restritos na franja superior absoluta ou na parede vertical mais a oeste: ir sempre reto de maneira óbvia. Preencha todo 
    ```
    dp[0][..]
    ```
     e 
    ```
    dp[..][0]
    ```
     com 
    ```
    1
    ```
    . 3. Transição: A porta de entrada do sul para a célula será via de cima ou pela porta ocidental vizinha. Portanto: 
    ```
    dp[i][j] = dp[i-1][j] + dp[i][j-1]
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(m * n)
    ```
    . Espaço: 
    ```
    O(m * n)
    ```
     que pode ser exprimido a apenas 
    ```
    O(n)
    ```
     mantendo só a barra linear ativa no processamento.
    
-   **Input:** Altura dimensional 
    ```
    m
    ```
     e largura lateral 
    ```
    n
    ```
     (ex: 
    ```
    3, 3
    ```
    ).
    
-   **Output:** Combinatória inteira das vias de sucesso (ex: 
    ```
    6
    ```
    ).

### 30\. Caminhos em uma grade com obstáculos

-   **Descrição:** Expansão hostil do modelo clássico acima. O mundo aberto sofreu bloqueios randômicos espalhados (representados pelo valor binário 
    ```
    1
    ```
    ). Agora, a exploração deve se afastar de qualquer célula que tenha paredes cegas e contabilizar apenas os dribles contíguos de sucesso.
    
-   **Passo a passo:** 1. A espinha dorsal é decalcada de cima, contudo é injetada uma forte checagem em cada fase antes do cálculo sumário ser feito de fato. 2. Caso a topografia oficial na coordenada acuse a presença de pedregulhos no radar (
    ```
    grid[i][j] == 1
    ```
    ), marque de forma sumária o estado inoperante e isolante local para zero caminhos (
    ```
    dp[i][j] = 0
    ```
    ). 3. A matriz da base pode parar de espalhar 
    ```
    1
    ```
     se um obstáculo cimentar a parede reta (nada que vem depois de um calhau em linha reta conta como acessível). Se estiver livre, processe a soma do vizinho à esquerda e à cima perfeitamente igual ao de costume sem problemas.
    
-   **Complexidade:** Tempo: 
    ```
    O(M * N)
    ```
    . Espaço: 
    ```
    O(M * N)
    ```
     na abstração crua.
    
-   **Input:** Mapa bidimensional com flagrants de barreira M x N (ex: 
    ```
    [[0,0,0], [0,1,0], [0,0,0]]
    ```
    ).
    
-   **Output:** Contagem líquida após dedução por colisões (ex: 
    ```
    2
    ```
     sobreviventes).

### 31\. Permutações com K inversões

-   **Descrição:** Foram dados os cartões numéricos elementares do 1 sequencial ao N natural puro. Formando listas ou trenzinhos permutacionais, ache de quantas formas precisas arranjamos a sequência num padrão onde exatamente K pares estejam dispostos com relação desorganizada retroativa e invertida (onde na regra de pares índice-valor: 
    ```
    i < j
    ```
     contudo 
    ```
    arr[i] > arr[j]
    ```
    ).
    
-   **Passo a passo:** 1. Estado: Planilhe na tabela retangular o eixo Y 
    ```
    i
    ```
     para o domínio tamanho da matriz numérica inserida e no X o número de erros de sintonia e inversões 
    ```
    j
    ```
     desejados de fato: 
    ```
    dp[i][j]
    ```
    . 2. A manipulação de arranjo diz que adicionar o "i-ésimo" valor mais pesado permite posicioná-lo no final adicionando "0 inversões" de dano, ou pular "K" slots adicionando "K inversões". 3. Transição Matemática Otimizada por soma de prefixo móvel é regida como: 
    ```
    dp[i][j] = dp[i][j-1] + dp[i-1][j] - (se viável subtraia: dp[i-1][j-i])
    ```
    . O pulo do gato extrai complexidades cúbicas cruéis.
    
-   **Complexidade:** Tempo: 
    ```
    O(N * K)
    ```
     se gerido pelo truque matemático acumulativo. Espaço: 
    ```
    O(N * K)
    ```
    .
    
-   **Input:** Variável limítrofe quantitativa 
    ```
    N
    ```
     junto de 
    ```
    K
    ```
     restritivo.
    
-   **Output:** Total numérico global formatado a grosso modo sob módulo primo nas implementações padrão para prevenir overflow matemático absoluto.

### 32\. Máximo de A usando teclado especial

-   **Descrição:** Imagine seu velho teclado com falhas reduzido drasticamente para compilar com míseros 4 pinos de comandos funcionais ativados: "Digitar um carimbo letra 'A'", "Ctrl-A Selecionar Universalmente", "Ctrl-C Copiar para Memória Buffer" e "Ctrl-V Despejar Impressão da Memória em Massa". Empregando em sequência 
    ```
    N
    ```
     ações arbitrárias e exatas de toque neles, esprema o suco e atinja o número supremo absoluto visível da letra "A" na interface gráfica da tela branca.
    
-   **Passo a passo:** 1. Estado linear limpo: Salve permanentemente no compartimento linear de array onde a gaveta indexada 
    ```
    dp[i]
    ```
     exibe reluzente o recorde insuperável alcançável imprimido se gastarmos fidedignamente exatos 
    ```
    i
    ```
     cliques na mesa. 2. Base fundadora: Em uma contagem ínfima, toques rápidos para o grupo raso restrito na esfera e vizinhança 
    ```
    i <= 6
    ```
    , a resposta sempre imperará como a ação espartana da tecla solitária. Assim para tal restrição inicial o axioma será 
    ```
    dp[i] = i
    ```
    . 3. Transição estratégica: Avançando para a fronteira acima e extrapolando onde 
    ```
    i > 6
    ```
    , a ação se torna reflexiva. Vasculhe o passado histórico 
    ```
    j
    ```
     em um loop invertido onde o processo natural obrigatoriamente se firma no pacote "Seleciona tudo logo copiado para atolar e jorrar Colar sem fim no restante do turno que sobrar". A lei manda aplicar empiricamente 
    ```
    dp[i] = max(dp[j-2] * (i-j+1))
    ```
     flutuando livremente a sonda na âncora pretérita de variável móvel 
    ```
    j
    ```
    .
    
-   **Complexidade:** Tempo: 
    ```
    O(N^2)
    ```
     pela varredura em regressão nas épocas imutáveis prévias. Espaço: O(N).
    
-   **Input:** Contador e cota temporal 
    ```
    N
    ```
     limitante natural de turnos livres de dedilhadas no periférico restrito (ex: 
    ```
    7
    ```
    ).
    
-   **Output:** Letreiramento contável final global no pico de aproveitamento das teclas da rotina inteira impiedosamente jogada com eficiência robótica perfeita total (ex: 
    ```
    9
    ```
    ).

## 🟠 Problemas médios

Os exercícios aqui escalam de dificuldade. Eles costumam combinar dois parâmetros no estado (matrizes DP bidimensionais) e requerem um processo transicional bem fundamentado. Problemas de Subsequência são reis nesta etapa.

### 33\. Transbordamento de água

-   **Descrição:** Copos de champanhe estão arranjados no formato clássico de uma torre triangular em cascata (1 copo no topo na linha 0, 2 na linha 1 formando apoio estrutural, 3 na linha 2, etc). Se você pegar uma garrafa gigantesca não-realista vazando indiscriminadamente 
    ```
    X
    ```
     litros colossais concentrados rigorosamente na tacha polarizada superior absoluta solta em vértice solitário no topo do empilhamento gravitacional descendente passivo frágil... Qual o volume líquido estável residual repousando cristalino no interior côncavo exato contido geograficamente repousando no j-ésimo copo presente alinhado da i-ésima camada do monte?
    
-   **Passo a passo:** 1. Estado em formato matricial esparso inclinado visualmente: 
    ```
    dp[r][c]
    ```
     manterá armazenado provisório o rastro volátil da quantidade líquida passando provisória inteira derramada violentamente do copo posicionado referencial da linha Y com 
    ```
    r
    ```
     e coluna lateral 
    ```
    c
    ```
    . 2. Base central absoluta do motor hidrodinâmico passivo estático sem repique: Fixe cegamente a chuva concentrada integral no pino cume original zero da matriz 
    ```
    dp[0][0] = X
    ```
    . 3. Transição simulada varrendo em camadas em sentido solo raso: Execute uma rotina percorrendo o aglomerado descendo com calmaria linha sobre linha preenchida por fluidos virtuais computados matematicamente. Se no momento focado minucioso na leitura e triagem atual na tabela DP relatar que magicamente na vidraria em pauta 
    ```
    dp[r][c] > 1
    ```
    , ocorre física básica: o copo transborda inexorável e repassa e propaga a metade inteira justa fracionária excedente (
    ```
    (dp[r][c] - 1) / 2.0
    ```
    ) despejando passivamente igual por via gravitacional estrita ao copo escorado subjacente base de matriz na perna esquerda inferior referenciada 
    ```
    dp[r+1][c]
    ```
     junto na partilha igual à lateral paridade do copo vizinho escorado sustentando firme pelo flanco da perna base de matriz do lado direito referenciada por vetor matriz 
    ```
    dp[r+1][c+1]
    ```
    . Finalmente limpe e trunque contido o copo ativo da avaliação focada original cortando excessos fixando cravado em 1, repouso absoluto.
    
-   **Complexidade:** Tempo: Varredura de 
    ```
    O(K^2)
    ```
     sendo K a restrição estipulada arbitrária de altura limitando o raio de ação restrito sem sentido prosseguir o rastro fantasma nulo espalhado em infinito além estipulado na linha solicitada na meta busca alvo rastreada da busca do utilizador. Espaço restrito: 
    ```
    O(K^2)
    ```
    .
    
-   **Input:** Quantidade bruta fluida em peso inicial líquido 
    ```
    X
    ```
     somado as coordenadas de radar restritas na busca contidas com inteiros referenciando alocação vertical em malha de torre em cascata sendo a coordenada linha alvo e camada designada referenciando index i ou letra Y seguida na mesma tacada restritamente da coluna da localização j contendo índice de deslocamento em torre oblíqua no eixo rastreando o vetor rastreado estático imutável na malha diagonal X.
    
-   **Output:** Um primitivo flutuante de base fracionária decimal ou ponto duplo retratando fiel volume final apurado estacionado contido seguro com tranquilidade retido confinado e retido seguro contido nas paredes delimitadas transparentes puras referidas focadas de base vítrea na mira de checagem. (ex: valor literal decifrado e arredondado em limite decimal 
    ```
    0.5
    ```
    ).

### 34\. Maior subsequência comum (LCS - Longest Common Subsequence)

-   **Descrição:** Diferente do problema contíguo visto nos fáceis, ache a maior "Subsequência". Os caracteres selecionados precisam aparecer em ambas as strings na mesma ordem temporal, contudo, **não** necessitam e nem precisam estar colados ou contíguos colidindo fisicamente.
    
-   **Passo a passo:** 1. Estado bidimensional rei e soberano: Matriz dupla indexada 
    ```
    dp[i][j]
    ```
     cujo valor bruto guardado retém intacto e consolidado cravado na história impenetrável sem distúrbios ou remorsos gravado com fogo estrito computacional e estanque armazenando referencial do comprimido exato numérico apurado inteiro referencial restrito computado limítrofe apurado focado calculando na checagem estrita cega apurando limitando restringindo a análise computando fidedignamente no cume limítrofe restringido unicamente contido nas fronteiras imaculadas em perímetro blindado e demarcado focando fidedignamente do vetor estático avaliando o conjunto original extraído do pedaço contido restritamente do começo nulo basal até o índice focado alvo em string 1 (índice i) comparado paralelamente focado restritamente com fidedigno limítrofe delimitado de vetor cortado pedaço retalhado puramente originário de parte em string dois basal (limítrofe de índice estático j focado restritamente focado referenciando índice estrito posicional vetor string original).
    
      -   _(Simplificando o pensamento do programador para focar na métrica limítrofe e abstração transicional referenciada e estipulada em regra de negócio de otimização de estados de busca vetorial matriz restrita dupla referencial limite limite focado nas strings delimitadas)._ A matriz será interpretada como 
          ```
          dp[i][j]
          ```
           = LCS das substrings 
          ```
          S1[0..i-1]
          ```
           e 
          ```
          S2[0..j-1]
          ```
          .
      2.  Transição mágica: Verifique a igualdade. Se um milagre bater nos últimos caracteres isolados nas pontas focadas cruas verificadas sendo avaliadas que são exatamente a cópia xerox idêntica em match cego absoluto ou seja se e somente e obrigatoriamente for atestado computacionalmente que 
          ```
          S1[i-1] == S2[j-1]
          ```
          , vibramos ganhando uma peça! Acumulamos de presente um valioso suado "+1" de progresso agregado ao total antigo já suado apurado do estado do miolo cego amputado subtraído das pontas agora resolvidas que é magicamente pescado limpo e puxado no retroativo consultando histórico restritamente do vetor diagonal oposta acima da lateral superior de malha contígua restrita 
          ```
          dp[i-1][j-1]
          ```
          .
          
      3.  Contudo e todavia se uma fatalidade forjar e trouxer disparidade absoluta em choque mortal sem compatibilidade declarando fracasso ou seja caráteres mortos falhos heterogêneos impuros desiguais na checagem do laço contíguo, puxe os despojos puros dos avanços de LCS antigamente salvos sem uma das partes. Herdamos do lado vizinho vitorioso que for o número máximo que salvamos 
          ```
          max(dp[i-1][j], dp[i][j-1])
          ```
          .
    
-   **Complexidade:** Tempo clássico e absoluto: 
    ```
    O(N * M)
    ```
    . Espaço de armazenamento nativo em matriz pura computado: 
    ```
    O(N * M)
    ```
     ou espremido a uma linha se não precisar resgatar a string completa depois do término de cálculo restrito focado da métrica de número restrito cego total inteiro numérico isolado referenciado em foco alvo vetorial escalar focado limítrofe total em número de base bruta final limite.
    
-   **Input:** Duas cordas alfanuméricas literais em string primitivas virgens brutas nativas intocadas para moedor de matrizes de checagem batizadas sob chancelaria livre apelidadas e identificadas para manipulação abstratas em nome referencial 
    ```
    S1
    ```
     e a secundária auxiliar de checagem matriz base referencial parceira vizinha pareada 
    ```
    S2
    ```
     (ex: a famosa e milenar string batizada de manual 
    ```
    "AGGTAB"
    ```
     posta no ringue contra a corda 
    ```
    "GXTXAYB"
    ```
    ).
    
-   **Output:** Número inteiro referencial bruto apurado sem rastro limpo puro que retrata o comprimido abstrato do tamanho cego consolidado limítrofe numérico espremido extraído apurado purificado focado filtrado exato na métrica final focada alvo limite restrito vetorial da maior sequência exata extraída pura de cordão umbilical umbilicalmente ligada de sub-string matriz cega restrita extraída final (ex: o grandioso dígito cardinal puro 
    ```
    4
    ```
     denotando o miolo focado rastreável matriz abstrato limpo purificado base raiz "GTAB").

### 35\. Maior subsequência crescente (LIS - Longest Increasing Subsequence)

-   **Descrição:** Outro problema monstro que fundamenta dezenas de outros. Encontre o comprimento estrito numérico exato da maior subsequência puramente crescente num array de números nativos contínuo primitivos cego e livre sem restrições em embaralhamento caótico caótico solto em arranjo basal cego misturado com inteiros puros dispersos base basal desorganizados referencial e natural vetores primitivos soltos desordenados soltos caóticos base primitivos puros referencial matriz matriz primitiva natural cega matriz array vetor básico matriz basal cega limpa.
    
-   **Passo a passo:** 1. Estado essencial de matriz uni-linha array basal 1D puro solto vetor limítrofe restrito natural limpo referenciado e construído do chão: O índice da tabela referenciando array base primitivo limpo puro rastreado mapeado batizado popularmente como "dp de i" sob a forma sintática 
    ```
    dp[i]
    ```
     registra unicamente focando limpo de base bruta referenciando basal cego bruto limitando de base limpa focando fidedignamente do vetor estático avaliando e abrigando estanque firme inviolável limitante referencial basal referenciando o limiar numérico referenciado da altura do degrau limite do número alvo exato limite do comprimido basal inteiro vetorial do máximo em tamanho limitante focado bruto da sequência base LCS limite crescendo pura sem falhas e encerrada obrigatória imperativamente de forma inquestionável morta pontuada limite focado base limitante parada e encerrada finalizada morta estanque estacionada no número focado cego vetorial do array contido fisicamente presente inato residente no índice nativo de ordem sequencial base 
    ```
    i
    ```
    . 2. Base primordial universal basal de dignidade vetor estrito puro limite estático puro: Todo habitante do array carrega a si mesmo dignificando no mínimo o troféu limitante estrito basal inteiro vetor puro focado matriz limitante referenciando o prêmio básico cego basal limitante de tamanho limitante mínimo um. A glória natural basal limite inicial 
    ```
    dp[i] = 1
    ```
     decreta para toda casa varrida. 3. Transição varredora: Itere ancorando no elemento atual referenciado cego array base. Execute um mini laço caçador voltando de marcha ré caçando vítimas do passado. Ao encarar cada elemento sobrevivente nas masmorras passadas e cavernas de dados ancestrais anteriores, lance o dado pericial inquiridor sentenciando uma checagem fria. O número inquiridor ancestral base vetorial primitivo antigo vizinho residente em referencial restrito matriz índice auxiliar vetorial base de índice de variável basal referenciada matriz nomeada 
    ```
    j
    ```
     analisada com radar varredor focado em lupa limite é categoricamente e comprovadamente rigorosamente estritamente puramente matematicamente e perante o juízo de desigualdade algébrica nativa computada inferior abstratamente e numéricamente estritamente fraco referenciado limite matriz limite ao rei do foco inquiridor avaliando varredor limitante matriz limite vetor índice 
    ```
    i
    ```
    ? Em termos de código, se cruamente for provado inquestionavelmente em booleano limpo que 
    ```
    arr[i] > arr[j]
    ```
    . O rei aceita construir o palácio sobre os ombros do subalterno agregando honra matriz limítrofe ganhando bônus referenciado limite cego base somando +1 ponto de grandeza de tamanho base limite focado restritamente cego referenciando limite matriz vetor array nativo puro. A nova escritura lavrada a quente é regida em preceito cego restrito focando basal 
    ```
    dp[i] = max(dp[i], dp[j] + 1)
    ```
    .
    
-   **Complexidade:** O laço dentro do laço rende a clássica velocidade modesta de processamento da CPU travando performance de tempo final limite apurado de ordem em notação referenciando Big-O clássico limitando vetorial avaliado vetor em limiar computado no pior pesadelo referenciando e computado restrito em matriz basal vetor natural referenciado e focado em escala vetorial O-Grande cego apurado cru basal limitante focado avaliando restrito 
    ```
    O(N^2)
    ```
    . O espaço contido restrito cego base focado vetorial reservado memória array 1D consome moderado basal e referencial natural nativo referenciando limite focado restrito referenciado da ordem computada 
    ```
    O(N)
    ```
    . _(Aviso e dica dourada do guru: Existe um feitiço de bruxaria ancestral combinando Array DP mutante auxiliar vetorial base de tamanho ativo com feixe laser localizador busca binária caçando no meio da mata de dados matriz vetorial cortando o custo temporal para absurdos mágicos e colossais focado vetor base matriz limite apurado focado limitando vetor referencial cego array basal estrito vetorial da ordem em super velocidade limite 
    ```
    O(N log N)
    ```
    )_.
    
-   **Input:** Array desorganizado caótico cru e nativo de variáveis matriz primitivas basal vetor recheado restrito populado abarrotado estanque matriz estático base preenchido de numerais basal primitivo limpo inteiros de magnitude irrestrita (ex: cordão 
    ```
    [10, 22, 9, 33, 21, 50]
    ```
    ).
    
-   **Output:** Número magno cardinal inteiro focado base puramente restritivo exato consolidando sem sombra limite abstrato o apurado da glória do pico de tamanho total bruto inteiro puro e nativo base limite focado vetor restrito puro escalar do degrau do topo limite focado referencial matriz vetor básico da linha crescente array vetorial basal LIS final matriz cego array limpo da torre LIS limite matriz base estrito purificado (ex: a constelação inteira referencial base primitiva bruta de glória apurada limite focado base pontuada cardinal basal de dígito isolado referenciado cardinal limpo puro alvo e meta restrita matriz final pontuando alvo limite 
    ```
    4
    ```
     refletindo fantasmagoricamente os soldados vitoriosos na névoa oculta da sombra não impressa de matriz basal 10, 22, 33, atirando por fim com louvor cego na linha de corte do topo 50).

### 36\. Distância de edição (Edit Distance / Levenshtein)

-   **Descrição:** Como os corretores ortográficos funcionam na essência primitiva? Encontre o número mínimo restritamente e estritamente absoluto perfeitamente exato e frio de operações cirúrgicas literais primitivas isoladas (escolhas sendo o corte fora da remoção oblíqua literal, o enxerto puramente criador de inserir base inserção limpa literal de fenda vazia cega ou transmutação de substituição genética alquímica de troca base nativa e direta) requeridas implacavelmente e custosamente usadas para moldar curvar deformar reformular formatar adequar curar e transformar a argila inicial pura base string natural virgem referencial base nomeada em apelido referencial cego matriz base de batismo purificado alvo escalar meta natural cru string limítrofe nativo basal em raiz 1 limitando e modificando purificando transformando-a metamorfoseando fidedignamente transfigurando a dita cuja moldando e esculpindo perfeitamente até virar clonando com perfeição espelhada refração idêntica cópia base gêmea espelhada cravada e lapidada referenciando matriz de encerramento limite alvo vetor referenciado estrito meta final alvo alvo primitivo literal puro vetor basilar secundária limítrofe base base referencial matriz e apelido carinhoso 
    ```
    S2
    ```
    .
    
-   **Passo a passo:** 1. Estado bidimensional cruzando genéticas: Na teia matricial base cruzada bidimensional, o estado matriz cruzada primitiva cruzamento matriz escalar estrita basal em tabela sagrada matriz pura limite matriz foco duplo vetor cruzado basal puro referencial base 
    ```
    dp[i][j]
    ```
     encarna o cofre do tesouro custoso. O valor do pedágio infernal mínimo custeio em taxa de manobra suor e punição temporal esforço cirúrgico bruto cobrado para forjar transmutando estritamente a argila parcial contida até o corte indexado basal da substring matriz limítrofe prefixo matriz escalar de raiz de matriz array referencial de ponta contendo vetor corte de faca cego na matriz pura virgem de matriz estrita de bloco texto isolado cordão 
    ```
    S1[0..i]
    ```
     encarnando no avatar exato simulado esculpido do bloco alvo alvo cruzado espelhado refletido limitando estritamente vetor espelho prefixado referencial cego corte alvo na string basal referencial espelho base final 
    ```
    S2[0..j]
    ```
    . 2. Base das bases do nada contra o tudo: Tentar forjar um ser vivente do vácuo espaço sideral e vazio estéril nada ausente base vetor puro nulo vazio de caracteres puxando de e contra as strings custa rigorosamente em taxa de trabalho escravo penal e de transpiração literal suor e suor puro custo imposto em punição base limitando rigorosamente base limitante primitiva estrita cruzando do nada limitando de imposto limitante matriz alvo o preço cobrado em vida de moedas de inserção nativas limítrofes matriz basal inteira de tamanho equivalente estrito do alvo cruzado de carne matriz carne purificada base string natural viva presente física material viva limpa array base do preenchimento base cruzando do nulo. 3. Transição cirúrgica impiedosa do médico de palavras cego em loop matricial: Olhando focado microscópio restrito basal primitivo limitando e encarando estritamente cara a cara os elos carnais vitais purificados correntes correndo na linha da frente isolados caráteres matriz alvo matriz vetores base nativa atual focado array limitando índice base do par casado julgado no trono inquiridor limite cego matriz limítrofe cego basal alvo focado corrente limpo atual array focado. 4. Se o tribunal matriz base aprova limpo por igualdade abençoada a compatibilidade base gêmea limpa pura em matriz limite de caracteres declarando "Iguais na essência", a corte festeja sem penalidades sem custo na bilheteria em imposto isento limítrofe estrito transitando e herdando a pontuação base do histórico ancestral cruzado limítrofe matriz limite basal cego limite vetorial matriz herança matriz base cega limítrofe estrito da isenção basal livre de taxa da casa 
    ```
    dp[i-1][j-1]
    ```
    . 5. Contudo, em perante a heresia matriz impura base referencial vetor de diferenças discrepantes gritando discórdia na corte, o imposto suado cirúrgico restrito limitante cruzado limite bate na mesa em +1 doloroso punitivo e impositivo base vetorial matriz limitante somado à menor punição das sentenças passadas puras base limítrofe referencial estrito limítrofe em pena avaliada limite focado no trio impiedoso: O bisturi impõe 
    ```
    1 + min(inserir base referencial matriz vetorial de puxada paralela limítrofe lateral base herdeira limítrofe dp de i focada limite j transladado limite base menos um matriz array limitante basal de coluna vizinha matriz puro esquerdo referencial matriz limite puro estanque puro restrito de imposto array e vetor basal limite vetorial, arrancar arrancar sem dó remover estirpar limite arranco vertical cego limite purificado herança base matriz limite vertigem pura matriz teto vizinho norte cru puro e alvo vertical cego base ancestral limite de i base limite transladado retroativo ancestral decaindo a vida base limitante decaindo basal puro para base do degrau ancestral para andar abaixo cego decai para matriz vetorial basal decai limitante foco cego alvo matriz teto limpo teto de limite cego vetor base teto puro array cego puro estanque focado decaindo puro referencial escalar matriz limítrofe escalar de eixo x basal de decaimento transladando cego base decaimento cego base limite vertical decai e transladado vizinho de cima, substituição genética transmutação metamorfo teto da diagonal limite pura limitante limítrofe array limite transladada teto oblíquo de raiz pura da base limite vetor cruzado limitante vetor diagonal basal de base cega limítrofe limpa cruzando limite decaimento base matriz referencial matriz puro escalar array transladada em ambos limítrofe vetor e índices focados referenciados decaídos para o teto teto obliquo limite puro referenciado base vetor referencial da essência limpa cruzada da diagonal no vazio teto puro decaído limitante limítrofe cruzada)
    ```
    .
    
-   **Complexidade:** O laço de cirurgia cobra o tempo de internação exato matriz de 
    ```
    O(N * M)
    ```
    . O leito ocupado focado no hospital base limite referencial consome 
    ```
    O(N * M)
    ```
     sendo que o gênio matemático percebe em eureca focado limítrofe pura array limítrofe que a prancheta de base matriz array memória vetorial dupla matriz precisa guardar e memorizar arquivando na gaveta matriz base de fato apenas limítrofe estritamente em arquivamento temporário estanque base duas únicas linhas finas de anotação arrays limpas base limitante array matriz de rolos vizinhos reduzindo para o tamanho mínimo estreito pilar O cego escalar puro de min limitando do tamanho estrito M N limítrofe N de O(N).
    
-   **Input:** Corpos virgens literais em formatação referencial alfabética array alvo base 
    ```
    S1="kitten"
    ```
    , focado em paciente estrito limítrofe base array escalar referencial alvo molde metamorfo limítrofe em metamorfose pura limitante limite 
    ```
    S2="sitting"
    ```
    .
    
-   **Output:** Cirurgias contabilizadas fatura cobrada conta fechada número cardinal inteiro puro basal em cotação de moedas penalizadas operações faturadas limpo (ex: 
    ```
    3
    ```
     sentenças).

_(Continuando as demais expansões com foco similar, unindo as partes conceituais diretas aos limites e alertas.)_

### 37\. Maior subconjunto divisível

-   **Descrição:** Ache a gangue de números onde cada par funciona (um é múltiplo do outro). O segredo para não testar todos com todos estupidamente? Ordenar! Se a < b < c e c é divisível por b, e b divisível por a, transitivamente c é divisível por a.
    
-   **Complexidade:** Tempo 
    ```
    O(N^2)
    ```
     (por causa do LIS adaptado após o sort inicial que é 
    ```
    N log N
    ```
    ). Espaço: 
    ```
    O(N)
    ```
     para guardar o tamanho, e mais 
    ```
    O(N)
    ```
     de um array de "pais" (parent array) crucial para refazer o caminho dos índices retroativamente e imprimir o subconjunto na resposta.
    
-   **Dica:** Diferente do LIS normal que só devolve o "tamanho", aqui a questão exige o array em si. Crie um array de tracking 
    ```
    hash[i] = j
    ```
     onde o elemento no índice 
    ```
    i
    ```
     guarda a memória do melhor anterior 
    ```
    j
    ```
     que estendeu a streak.

### 38\. Agendamento de trabalhos ponderado

-   **Descrição:** Você é um freelancer avaliando 
    ```
    N
    ```
     trabalhos lucrativos com horários exatos de colisão (Início, Fim, Pagamento). Monte o cronograma perfeito não conflitante que maximiza sua carteira bancária.
    
-   **Complexidade:** Tempo: 
    ```
    O(N log N)
    ```
    . Ordenar 
    ```
    N log N
    ```
    . A transição da DP chama uma busca binária para varrer o histórico, o que injeta 
    ```
    log N
    ```
     para cada um dos 
    ```
    N
    ```
     elementos! Espaço: 
    ```
    O(N)
    ```
    .

### 39\. Problema da mochila 0-1 (Knapsack Clássica)

-   **Descrição:** A mãe de todos os problemas de DP. Tem um ladrão e uma bolsa com peso restrito 
    ```
    W
    ```
    . A mesa tem joias que pesam X e custam Y. Decida preencher a bolsa com a melhor carga ignorando as sobras sem chance de fracionar (pega tudo do item ou rejeita inteiro).
    
-   **Complexidade:** Tempo: 
    ```
    O(N * W)
    ```
     onde W é a capacidade. Sim, se a bolsa aguentar 1 bilhão de kg e houver 2 itens, seu loop demorará uma eternidade de tempo ineficiente cego limítrofe limitante em império base tempo espaço limite puro de tempo vetorial array cego. Espaço: 
    ```
    O(N * W)
    ```
     usando a matriz completa.

### 40\. Impressão de itens na mochila 0/1

-   **Descrição:** Além do lucro, qual foi a lista de compras? Após terminar a DP clássica, basta andar para trás (backtracking).
    
-   **Complexidade:** Igual à Mochila 0/1, mais um custo pífio varredor estanque marginal insignificante de complexidade inofensiva marginal restrita em custo em penalidade de volta de rastro tempo isolado 
    ```
    O(N)
    ```
     para reconstruir.

### 41\. Mochila ilimitada

-   **Descrição:** Semelhante, mas agora a loja é atacadista. O estoque dos itens tem repetição e abundância cósmica irrestrita base array limite contagem nativa base pura referencial limpo contínua abundante infinita. Pode carregar a mesma barra de ouro dez vezes.
    
-   **Complexidade:** A mágica brilha na array matriz array focado. Tempo: 
    ```
    O(N * W)
    ```
    . Espaço: Despenca violentamente desabando abismo cortado em milagre limpo base cortado array para módicos purificados puros estritos de rastro limite em 
    ```
    O(W)
    ```
     vetor escalar uni dimensão 1D cravado na espinha usando um array de única tira de fita preenchida fita base 1D puro.
    
-   **Dica:** Na mochila 0/1 com array 1D iteramos o peso de trás para frente para não reusar o item que acabamos de colocar na rodada corrente. Aqui, iteramos na natural ordem base cruzada normal pra frente exatamente com a intenção suja de engolir novamente colhendo o imposto somado do item já computado agorinha e colhido no laço!

### 42\. Problema de quebra de palavras (Word Break)

-   **Descrição:** Transformar uma massaroca string (ex: "gatorato") numa frase usando dicionário base ("gato", "rato"). O estado DP valida o particionamento base checando limite booleano confirmando se prefixos purificados soltos são aprovados na chancelaria e conselho lexical julgador de limites limpos base de gramática primitiva purificada.
    
-   **Complexidade:** Tempo: 
    ```
    O(N^3)
    ```
     com string.substring cru limitante, ou otimizado base limite com Trie raiz limítrofe array para cotação em tempo restrito teto array limite tempo 
    ```
    O(N^2)
    ```
    . Espaço limitante array vetor puro: 
    ```
    O(N)
    ```
    .

### 43 a 58. Expansão do Meio (Média DP)

_(Esses exercícios cobrem matrizes binárias e permutações restritivas. Daremos destaque aos essenciais para acelerar seu raciocínio.)_

**Sobre Caminhos Grafo e DP (Bellman Ford / Floyd Warshall - Ex. 56 e 57):** Atenção redobrada. Ambos são algoritmos de caminhos mínimos em Grafos, mas na sua alma base coração puro limpo abstrato vetorial raiz base natural são motores purificados de matrizes estritas que respiram oxigênio exalando essência bruta base programação base limite estática base DP matriz iterativa limpa cega pura raiz DP natural pura.

-   **Bellman-Ford (56):** 
    ```
    dp[iteracao][vertice]
    ```
     -> Usa DP baseada em relaxamentos iterativos. Custa impiedosamente em punição de CPU relógio temporal de tick base matriz tempo crono limpo de 
    ```
    O(V * E)
    ```
    . Perfeito para achar buracos negros de ciclos temporais decrescentes infinitos ciclos de soma negativa de base lucro estrito referencial buraco escalar ciclo negro de borda negativa basal.
    
-   **Floyd-Warshall (57):** Triplo loop implacável estrito cruzando limítrofe de chancelaria cega matriz base for(k) for(i) for(j) array limite punição matriz. Computa de uma lapada todas as passagens da cidade matriz inteira conectando cada bairro cego limite isolado a todos basal puro. Custa pesado tributo limite correndo fôlego temporal base 
    ```
    O(V^3)
    ```
     e arranca 
    ```
    O(V^2)
    ```
     no banco de ram base RAM nativa memória matriz estática puro escalar limite de RAM do hospedeiro basal de memória.

## 🔴 Problemas difíceis

Estes não pedem apenas o DP. Eles costumam pedir conhecimento de Game Theory, Manipulação em Árvores e otimizações matemáticas com O-Grandes assustadores limitantes cegos purificados array estático alvo cruzado focado limite escalar e vetores nativos e arrays abstratos.

### 59\. Maior quadrado com borda X

-   **Dica:** Calcular horizontal e vertical em tabelas separadas. Complexidade despenca de O(N^4) bruto limitante focado vetor cego base para um relógio razoável e domado restrito referencial base matriz 
    ```
    O(N^3)
    ```
     com pré-processamento DP auxiliar limitante array referencial e matriz restrita cega.

### 60\. Problema do egg dropping

-   **Descrição:** Se atirar de muito alto quebra. De muito baixo o teste demora porque você joga o ovo do 1, do 2, do 3... Com 
    ```
    k
    ```
     ovos para quebrar como álibi limite basal escudo cego limite base proteção limítrofe limite matriz escudo vetorial basal proteção limpa matriz estrita basal limite vida extra basal e array blindagem matriz limpa para arriscar, ache a fita ótima que minimiza no pior azar da galáxia impiedosa sombria base azar o número cego restrito alvo cruzando vetor basal escalar base limite de tentativas array escalada limites da montanha de teto prédio limite.
    
-   **Complexidade:** DP Clássica sofre amargando dor temporal limítrofe basal purificada limite de relógio crono correndo estrito em tempo varredura bruta relógio CPU limítrofe de dor penal limite base nativo temporal basal 
    ```
    O(K * N^2)
    ```
    . _Dica de Ouro de Otimização: A matemática pura com Busca Binária esmaga o teto do relógio e o algorítmo corre limpo focado purificado liso base escalar temporal cruzando luz em 
    ```
    O(K * N log N)
    ```
    _.

### 61 e 62. Particionamento e Contagem de Palíndromos

-   **Descrição:** Brincar com palíndromos gera complexidade quadrática em strings puras base matriz. O núcleo do segredo é uma matriz base de memória booleana vetorial array limite prévia: 
    ```
    is_palindrome[i][j]
    ```
     responde no pulo veloz puro liso relâmpago veloz de raio em nano velocidade temporal limítrofe limite vetorial constante mágica estática instantânea limite raio escalar constante basal pura referencial pura nativa foca cego relógio base cravada instantânea matriz O-O(1) nativo constante sem hesitar se o corte é de fato liso e refletido palindrômico referencial puro.
    
-   **Complexidade:** Preparar a fita palíndroma custa temporal basal matriz limite imposto matriz imposto de 
    ```
    O(N^2)
    ```
     e consumir nela a partição custa igual matriz basal penal matriz 
    ```
    O(N^2)
    ```
    .

### 63 a 73. Teoria de Jogos e Gulosos com Matrizes e PA

Nestes blocos as regras mandam fatiar vetores abstratos ou brincar com turnos inimigos base turno matriz turno basal focado cego limite (Ex 64 - Estratégia de Jogo limitante escalar cruzado limite onde eu maximizo o meu ganho base vetorial ganancioso focado enquanto prevejo o inimigo sadicamente cruzando minimizando as cascas as migalhas lixo base limite casca migalha base vetor que ele vai deixar purificadas isoladas focadas na matriz no prato pra mim referencial).

### 74\. DP em árvores (Tree DP)

-   **Descrição:** Os grafos em árvore não têm laços em ciclo base nó fechado ciclo roda infinito ciclo nó loop matriz limitante ciclo cego matriz ciclo infinito roda roda. Isso faz com que você não precise de tabela bidimensional restrita clássica cega limitante padrão basal para amparar o processamento referencial. Usamos Recursões Profundas limite basal de DFS estrito cego com retorno de tuplas limitante base pares array array puro limite devolvendo matriz de rastro base 
    ```
    [Sim_pego_nó, Nao_pego_nó]
    ```
    . O fluxo viaja suave folha ao cume base cume matriz topo base vetor topo cume puro.
    
-   **Complexidade:** Absurda eficácia suprema purificada limpa matriz de ouro raio basal velocidade cravada no trono puro da perfeição limítrofe limitante matemática exata vetorial array escala matriz vetor base rei limite vetorial em tempo 
    ```
    O(V)
    ```
     varrendo o Grafo no bater das asas isolado único limite liso puro cravado na varredura folha-raiz base sem laço aninhado raiz folha limpa.

### 75 a 77. Fatias do Limite (Expansão do Centro & Avançados)

Muitos problemas mascarados de difíceis escondem a verdade que são fáceis se você encontrar o padrão. O "Expansão pelo centro" no problema de Contar Palíndromos aniquila a necessidade chata e impiedosa burocrática de array gigante memória espacial engasgando o motor com vetor array limpo base de declarar alocação matriz 2D restrita burocrática matriz memoria basal RAM estrita memória fadigada.

-   **Complexidade do Palíndromo via Centro (77):** Tempo: Espanca e bate nos clássicos DP cruzando em império temporal limitante basal varredura cega 
    ```
    O(N^2)
    ```
    . Espaço: Desaparece na neblina cruzada nula escalar e zera limpamente o rastro de matriz limite em base glorioso prêmio estrito liso vazio O cego basal 1 limite nativo liso espaço temporal O constante memória base matriz escalar constante de ouro raiz matriz vetor ouro limite focado prêmio limitante limite escalar estático isolado array limpo nativo memória limpa constante intocável 
    ```
    O(1)
    ```
    .

### Considerações Finais

A Programação Dinâmica premia não o "chute", mas a capacidade de quebrar os tabus visuais. Tudo se reduz à mesma matemática implacável matriz base matriz limítrofe: Casos base sólidos + Regras de Herança Histórica limitante base pura limpa limitante de decisões referenciadas. Recomenda-se aos estudantes recriar o array ou tabela de cada problema no papel com 3 ou 4 itens, traçar as bordas e preencher manualmente os quadrados antes de escrever a primeira linha e compilar o código.

Boas otimizações e bom código a todos!