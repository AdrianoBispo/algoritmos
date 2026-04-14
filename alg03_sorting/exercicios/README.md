# Lista de Exercícios - Algoritmos de Ordenação

Bem-vindo à lista de exercícios práticos de Algoritmos de Ordenação! Este documento foi criado e cuidadosamente estruturado para ajudar você a fortalecer sua lógica de programação e sua capacidade de resolução de problemas algorítmicos.

A ordenação (Sorting) é um dos tópicos mais fundamentais da Ciência da Computação. Muitas vezes, um problema que parece impossível ou que exige uma complexidade de tempo ineficiente (como $O(n^2)$ ou $O(n^3)$) pode ser drasticamente otimizado para $O(n log n)$ ou até $O(n)$ simplesmente ordenando os dados primeiro. A ordenação é a porta de entrada para técnicas mais avançadas, como _Busca Binária (Binary Search)_, _Algoritmos Gulosos (Greedy Algorithms)_, _Dois Ponteiros (Two Pointers)_ e _Janela Deslizante (Sliding Window)_.

**Como usar esta lista:** Você pode implementar essas soluções na linguagem de programação de sua preferência (C, C++, Java, Python, JavaScript, C#, Ruby, Go, etc.). Não se apresse em olhar o código pronto na internet. Leia a descrição, entenda a regra de negócio e siga o **"Passo a Passo Sugerido"** para desenhar a estrutura do seu algoritmo mentalmente ou no papel. Preste muita atenção na seção de **"Dicas e Casos Extremos"** e tente atingir a **"Complexidade Esperada"** em suas submissões.

<details>
  <summary>🟢 Nível 1 - Fácil</summary>

<p>

Esses problemas focam em aplicar a ordenação direta para revelar padrões nos dados e introduzem o pensamento guloso (Greedy) básico.

### 1\. Triângulo de Perímetro Máximo (Maximum Perimeter Triangle)

**Descrição:** Dado um array de inteiros positivos representando o comprimento de varetas disponíveis, o objetivo é encontrar o triângulo com o maior perímetro possível que pode ser formado usando exatamente três dessas varetas. Lembre-se da desigualdade triangular: a soma de dois lados deve ser sempre maior que o terceiro lado. **Conceito Chave:** Algoritmos Gulosos (Greedy) combinados com ordenação linear. **Passo a Passo Sugerido:**

1.  Ordene o array de forma decrescente (do maior para o menor). Fazer isso garante que os primeiros três elementos válidos que encontrarmos formarão automaticamente o maior perímetro possível.
    
2.  Percorra o array verificando janelas de três elementos consecutivos: considere 
    ```
    l1 = A[i]
    ```
    , 
    ```
    l2 = A[i+1]
    ```
    , e 
    ```
    l3 = A[i+2]
    ```
    .
    
3.  Para formar um triângulo válido, verifique a condição matemática: 
    ```
    l2 + l3 > l1
    ```
    . (Não precisamos testar 
    ```
    l1 + l2 > l3
    ```
     porque, como o array está ordenado decrescentemente, 
    ```
    l1
    ```
     já é garantidamente o maior lado da trinca).
    
4.  O primeiro trio que satisfizer essa condição será a sua resposta final. Interrompa o loop e retorne os valores.
-   **Dicas e Casos Extremos:** O que acontece se o array tiver menos de 3 elementos? Sua função deve lidar com isso (ex: retornando nulo ou um array vazio). E se nenhuma trinca formar um triângulo (ex: 
    ```
    [100, 2, 1]
    ```
    )? Retorne um indicador de falha.
    
-   **Complexidade Esperada:** Tempo O(NlogN) devido à ordenação. Espaço O(1).
    
-   **Entrada:** 
    ```
    [6, 1, 6, 5, 8, 4]
    ```
    
-   **Saída:** 
    ```
    [8, 6, 6]
    ```
     (Perímetro = 20)

### 2\. Maximizar a Soma após K Negações (Maximize sum after K negations)

**Descrição:** Dado um array e um número 
```
K
```
, você deve realizar uma operação exata 
```
K
```
 vezes: escolher um elemento e multiplicá-lo por 
```
-1
```
. Seu objetivo é que, ao final das 
```
K
```
 operações, a soma total dos elementos do array seja a maior possível. **Conceito Chave:** Abordagem Gulosa (Greedy) minimizando perdas. **Passo a Passo Sugerido:**

1.  Ordene o array em ordem crescente. Isso colocará todos os números negativos no início do array, do "mais negativo" para o "menos negativo".
    
2.  Itere pelo array. Se o número atual for negativo e você ainda tiver operações disponíveis (
    ```
    K > 0
    ```
    ), multiplique o número por 
    ```
    9.1
    ```
     (transformando-o em positivo) e decremente 
    ```
    K
    ```
    .
    
3.  Se você esgotar os números negativos e 
    ```
    K
    ```
     ainda for maior que 0: se 
    ```
    K
    ```
     for par, multiplicar o mesmo número por -1 e depois por -1 novamente o devolve ao original (ignore). Se 
    ```
    K
    ```
     for ímpar, você _deve_ negativar um número. Encontre o menor número absoluto no array atual e inverta o sinal dele.
    
4.  Por fim, some todos os elementos do array modificado e retorne o total.
-   **Dicas e Casos Extremos:** Arrays com zeros são excelentes: se sobrar um 
    ```
    K
    ```
     ímpar após negativar todos os negativos, aplique o 
    ```
    -1
    ```
     ao zero, pois não há perda na soma final.
    
-   **Complexidade Esperada:** Tempo O(NlogN) para ordenação. Espaço O(1).
    
-   **Entrada:** 
    ```
    array = [-2, 0, 5, -1, 2]
    ```
    , 
    ```
    K = 4
    ```
    
-   **Saída:** 
    ```
    10
    ```
     (Array final: 
    ```
    [2, 0, 5, 1, 2]
    ```
    )

### 3\. Soma da Diferença Absoluta Mínima (Sum of minimum absolute difference)

**Descrição:** Para cada elemento individual em um array, encontre a diferença absoluta mínima entre ele e qualquer outro elemento presente no array. O resultado final deve ser a soma de todas essas diferenças mínimas individuais. **Conceito Chave:** Propriedade de adjacência em arrays ordenados. **Passo a Passo Sugerido:**

1.  Ordene o array em ordem crescente. A sacada aqui é que a diferença mínima para qualquer número 
    ```
    X
    ```
     estará sempre em um de seus vizinhos imediatos (à esquerda ou à direita).
    
2.  Para o primeiro elemento (índice 
    ```
    0
    ```
    ), a diferença mínima será obrigatoriamente em relação ao segundo elemento (índice 
    ```
    1
    ```
    ). Calcule e guarde.
    
3.  Para o último elemento (índice 
    ```
    n-1
    ```
    ), a diferença mínima será em relação ao penúltimo (índice 
    ```
    n-2
    ```
    ). Calcule e guarde.
    
4.  Para os elementos do meio (
    ```
    i
    ```
     indo de 
    ```
    1
    ```
     até 
    ```
    n-2
    ```
    ), calcule a distância para a esquerda (
    ```
    A[i] - A[i-1]
    ```
    ) e para a direita (
    ```
    A[i+1] - A[i]
    ```
    ). Adicione o menor valor entre essas duas distâncias ao seu somatório total.
    
5.  Retorne a soma acumulada.
-   **Dicas e Casos Extremos:** Certifique-se de usar valor absoluto (função 
    ```
    abs()
    ```
    ) nas subtrações.
    
-   **Complexidade Esperada:** Tempo O(NlogN). Espaço O(1).
    
-   **Entrada:** 
    ```
    [4, 1, 5]
    ```
    
-   **Saída:** 
    ```
    5
    ```
     (Diferenças: 1->3; 4->1; 5->1. Soma = 5)

### 4\. Ordenar em Forma de Onda (Sort in waveform)

**Descrição:** Organize os elementos de um array de forma que ele represente graficamente uma "onda", com picos e vales alternados: 
```
arr[0] >= arr[1] <= arr[2] >= arr[3] <= arr[4]...
```
 **Conceito Chave:** Permutação de elementos adjacentes. **Passo a Passo Sugerido:**

1.  Ordene o array inteiro em ordem crescente.
    
2.  Percorra o array utilizando um loop saltando de 2 em 2 posições (índices 
    ```
    i = 0, 2, 4, 6...
    ```
    ).
    
3.  Em cada iteração, troque o elemento atual 
    ```
    A[i]
    ```
     com o elemento adjacente à sua direita 
    ```
    A[i+1]
    ```
    .
    
4.  Ao fazer isso sucessivamente, o maior número da dupla sobe e o menor desce, criando o padrão de onda.
-   **Dicas e Casos Extremos:** Não tente acessar o índice 
    ```
    i+1
    ```
     no último elemento caso o array tenha tamanho ímpar, ou você receberá um erro de limite de índice.
    
-   **Complexidade Esperada:** Tempo O(NlogN) usando ordenação. (Nota: existe solução O(N) verificando vizinhos locais).
    
-   **Entrada:** 
    ```
    [10, 5, 6, 3, 2, 20, 100, 80]
    ```
    
-   **Saída:** 
    ```
    [10, 5, 20, 6, 100, 10, 80, 2]
    ```
     _(Múltiplas respostas válidas)_

### 5\. Problema da Distribuição de Chocolate (Chocolate Distribution Problem)

**Descrição:** Dado um array onde cada elemento representa a quantidade de chocolates dentro de um pacote, e um número 
```
M
```
 que representa a quantidade de estudantes. Distribua um pacote para cada estudante de forma que a diferença entre o estudante que recebe mais e o que recebe menos chocolates seja a menor possível. **Conceito Chave:** Janela Deslizante (Sliding Window) em dados ordenados. **Passo a Passo Sugerido:**

1.  Ordene o array de pacotes em ordem crescente. Isso agrupará pacotes com quantidades semelhantes.
    
2.  Defina uma variável 
    ```
    min_diff
    ```
     para guardar a diferença mínima (inicie com um valor máximo, como infinito).
    
3.  Deslize uma janela de tamanho exato 
    ```
    M
    ```
     sobre o array. O loop vai de 
    ```
    i = 0
    ```
     até 
    ```
    i + M - 1 < tamanho
    ```
    .
    
4.  Para cada janela, a diferença é o último elemento da janela 
    ```
    A[i + M - 1]
    ```
     menos o primeiro elemento 
    ```
    A[i]
    ```
    .
    
5.  Atualize 
    ```
    min_diff
    ```
     se a diferença desta janela for menor.
-   **Complexidade Esperada:** Tempo O(NlogN). Espaço O(1).
    
-   **Entrada:** 
    ```
    array = [7, 3, 2, 4, 9, 12, 56]
    ```
    , 
    ```
    M = 3
    ```
    
-   **Saída:** 
    ```
    2
    ```
     (A janela ideal é 
    ```
    [2, 3, 4]
    ```
    . Diferença: 4 - 2 = 2)

### 6\. Par com a Diferença Dada (Pair with the given difference)

**Descrição:** Dado um array de inteiros e um número alvo 
```
N
```
, verifique se existe algum par de elementos distintos no array cuja diferença absoluta seja exatamente igual a 
```
N
```
. **Conceito Chave:** Dois Ponteiros (Two Pointers) unidirecionais. **Passo a Passo Sugerido:**

1.  Ordene o array em ordem crescente.
    
2.  Inicialize dois ponteiros no início do array: 
    ```
    esq = 0
    ```
     e 
    ```
    dir = 1
    ```
    .
    
3.  Enquanto o ponteiro 
    ```
    dir
    ```
     for menor que o tamanho do array, calcule 
    ```
    diff = A[dir] - A[esq]
    ```
    .
    
4.  Analise os casos:
    
      25.   Se 
          ```
          diff == N
          ```
           e 
          ```
          esq != dir
          ```
          , retorne 
          ```
          Verdadeiro
          ```
          .
          
      39.   Se 
          ```
          diff < N
          ```
          , a diferença está pequena. Avance o ponteiro da frente: 
          ```
          dir++
          ```
          .
          
      49.   Se 
          ```
          diff > N
          ```
          , a diferença está grande. Avance o ponteiro de trás: 
          ```
          esq++
          ```
          .
    
5.  Retorne 
    ```
    Falso
    ```
     se o loop terminar.
-   **Complexidade Esperada:** Tempo O(NlogN). Espaço O(1).
    
-   **Entrada:** 
    ```
    array = [5, 20, 3, 2, 5, 80]
    ```
    , 
    ```
    N = 78
    ```
    
-   **Saída:** 
    ```
    Verdadeiro
    ```
     (O par é 2 e 80)

</p>

</details>

<details>
  <summary>🟠 Nível 2 - Médio</summary>

<p>

A partir daqui, os problemas exigem combinações de técnicas. A ordenação será apenas o primeiro passo para preparar o terreno para algoritmos mais complexos.

### 7\. Soma de Trio (3sum)

**Descrição:** Encontre se existem três elementos no array cuja soma seja exatamente igual a um valor alvo 
```
X
```
. **Conceito Chave:** Fixação de variável com Dois Ponteiros convergentes. **Passo a Passo Sugerido:**

1.  Ordene o array em ordem crescente.
    
2.  Utilize um loop 
    ```
    for
    ```
     externo para fixar o primeiro elemento da trinca no índice 
    ```
    i
    ```
    .
    
3.  Para achar os outros dois números, utilize dois ponteiros: 
    ```
    esq = i + 1
    ```
     e 
    ```
    dir = tamanho - 1
    ```
    .
    
4.  Calcule a soma: 
    ```
    soma = A[i] + A[esq] + A[dir]
    ```
    .
    
5.  Se 
    ```
    soma == X
    ```
    , retorne 
    ```
    Verdadeiro
    ```
    .
    
6.  Se 
    ```
    soma < X
    ```
    , precisamos de valores maiores, faça 
    ```
    esq++
    ```
    .
    
7.  Se 
    ```
    soma > X
    ```
    , passamos do valor, faça 
    ```
    dir--
    ```
    .
-   **Dicas e Casos Extremos:** Para não retornar trincas duplicadas (se o problema exigir todas elas), pule os elementos adjacentes idênticos.
    
-   **Complexidade Esperada:** Tempo O(N2).
    
-   **Entrada:** 
    ```
    array = [1, 4, 45, 6, 10, 8]
    ```
    , 
    ```
    X = 22
    ```
    
-   **Saída:** 
    ```
    Verdadeiro
    ```
     (Trio formado por: 4, 8 e 10)

### 8\. Índice H (H Index)

**Descrição:** O Índice H é o maior número 
```
h
```
 tal que um pesquisador tenha publicado pelo menos 
```
h
```
 artigos que receberam 
```
h
```
 ou mais citações. **Conceito Chave:** Ordenação reversa e cruzamento de índice vs. valor. **Passo a Passo Sugerido:**

1.  Ordene o array de citações em ordem **decrescente**.
    
2.  Itere pelo array com um índice 
    ```
    i
    ```
     começando de 
    ```
    0
    ```
    . (
    ```
    i + 1
    ```
     representa a quantidade de artigos avaliados).
    
3.  Verifique se o artigo atual (posição 
    ```
    i
    ```
    ) tem citações 
    ```
    >= i + 1
    ```
    .
    
4.  Enquanto for verdadeiro, continue iterando.
    
5.  Quando a condição falhar, o índice H será exatamente o valor atual de 
    ```
    i
    ```
    .
-   **Complexidade Esperada:** Tempo O(NlogN).
    
-   **Entrada:** 
    ```
    [3, 0, 6, 1, 5]
    ```
    
-   **Saída:** 
    ```
    3
    ```
     (O array ordenado decrescente é 
    ```
    [6, 5, 3, 1, 0]
    ```
    . O índice para no 3).

### 9\. Trio com a Soma Mais Próxima (Triplet with closest sum)

**Descrição:** Dado um array e um valor alvo 
```
X
```
, encontre três elementos cuja soma seja a mais próxima possível de 
```
X
```
. Retorne a soma desses três elementos. **Conceito Chave:** Rastreamento da diferença mínima contínua com Dois Ponteiros. **Passo a Passo Sugerido:**

1.  Ordene o array em ordem crescente.
    
2.  Inicialize 
    ```
    menor_diferenca
    ```
     com infinito e 
    ```
    soma_mais_proxima
    ```
     com 0.
    
3.  Fixe um elemento no índice 
    ```
    i
    ```
     e posicione 
    ```
    esq = i + 1
    ```
     e 
    ```
    dir = tamanho - 1
    ```
    .
    
4.  Calcule 
    ```
    soma_atual
    ```
     e sua diferença absoluta para 
    ```
    X
    ```
    .
    
5.  Se a diferença for menor que a guardada, atualize 
    ```
    menor_diferenca
    ```
     e 
    ```
    soma_mais_proxima
    ```
    .
    
6.  Se 
    ```
    soma_atual < X
    ```
    , avance 
    ```
    esq++
    ```
    . Se for maior, recue 
    ```
    dir--
    ```
    .
-   **Complexidade Esperada:** Tempo O(N2).
    
-   **Entrada:** 
    ```
    array = [-1, 2, 1, -4]
    ```
    , 
    ```
    X = 1
    ```
    
-   **Saída:** 
    ```
    2
    ```
     (-1 + 2 + 1 resulta em 2, distância de 1 unidade para o alvo).

### 10\. K Elementos Mais Frequentes (K most occurring elements)

**Descrição:** Encontre os 
```
K
```
 elementos que aparecem com a maior frequência dentro de um array. **Conceito Chave:** Tabelas de Dispersão (Hash Maps) com Ordenação ou Filas de Prioridade (Heaps). **Passo a Passo Sugerido:**

1.  Varra o array e construa um mapa (HashMap) contando a frequência de cada número.
    
2.  Transfira para uma lista de pares 
    ```
    (número, frequência)
    ```
    .
    
3.  Ordene essa lista de forma decrescente baseada na frequência.
    
4.  Retorne os números dos 
    ```
    K
    ```
     primeiros pares.
-   **Complexidade Esperada:** Tempo O(NlogN) com ordenação completa, ou O(NlogK) usando uma Max-Heap.
    
-   **Entrada:** 
    ```
    array = [3, 1, 4, 4, 5, 2, 6, 1]
    ```
    , 
    ```
    K = 2
    ```
    
-   **Saída:** 
    ```
    [1, 4]
    ```
     (Ambos possuem frequência 2).

### 11\. Mesclar Intervalos Sobrepostos (Merge Overlapping Intervals)

**Descrição:** Dado um conjunto de intervalos de tempo, mescle todos os intervalos que se sobrepõem, retornando um novo conjunto contíguo. **Conceito Chave:** Algoritmos de varredura (Line Sweep). **Passo a Passo Sugerido:**

1.  Ordene a matriz de intervalos baseando-se estritamente no **tempo de início** de cada um.
    
2.  Crie uma lista 
    ```
    resultado
    ```
     e adicione o primeiro intervalo.
    
3.  Inicie um loop a partir do segundo intervalo. Compare o início do atual com o término do último na lista 
    ```
    resultado
    ```
    .
    
4.  Se houver sobreposição (início do atual <= término do último), atualize o término do último intervalo para ser o maior entre os dois.
    
5.  Se não houver, apenas adicione o intervalo atual ao resultado.
-   **Complexidade Esperada:** Tempo O(NlogN).
    
-   **Entrada:** 
    ```
    [[1,3], [2,6], [8,10], [15,18]]
    ```
    
-   **Saída:** 
    ```
    [[1,6], [8,10], [15,18]]
    ```

### 12\. Formar o Maior Número (Form the Largest Number)

**Descrição:** Dado um array de números inteiros positivos, junte-os lado a lado para formar a maior string numérica possível. **Conceito Chave:** Sobrescrita do comparador padrão de ordenação (Custom Comparator). **Passo a Passo Sugerido:**

1.  Converta todos os inteiros do array para 
    ```
    String
    ```
    .
    
2.  Crie uma regra de ordenação customizada: Dadas duas strings 
    ```
    X
    ```
     e 
    ```
    Y
    ```
    , compare as concatenações 
    ```
    XY
    ```
     e 
    ```
    YX
    ```
    . Se 
    ```
    XY > YX
    ```
    , 
    ```
    X
    ```
     deve vir antes.
    
3.  Ordene o array de strings usando esse comparador de forma decrescente.
    
4.  Concatene todos os elementos. Trate o caso especial onde o array possui apenas zeros retornando "0".
-   **Complexidade Esperada:** Tempo O(NlogN).
    
-   **Entrada:** 
    ```
    [3, 30, 34, 5, 9]
    ```
    
-   **Saída:** 
    ```
    "9534330"
    ```

### 13\. Ordenar Array de 0s, 1s e 2s (Sort array of 0s, 1s and 2s)

**Descrição:** Problema da Bandeira Nacional Holandesa. Ordene um array composto apenas por 0s, 1s e 2s em uma única passagem (O(N)), sem algoritmos tradicionais. **Conceito Chave:** Múltiplos ponteiros particionando dados localmente (In-place). **Passo a Passo Sugerido:**

1.  Use três ponteiros: 
    ```
    baixo = 0
    ```
    , 
    ```
    meio = 0
    ```
    , e 
    ```
    alto = tamanho - 1
    ```
    .
    
2.  Itere enquanto 
    ```
    meio <= alto
    ```
    .
    
3.  Se 
    ```
    A[meio] == 0
    ```
    : Troque os valores de 
    ```
    baixo
    ```
     e 
    ```
    meio
    ```
    . Avance ambos (
    ```
    baixo++
    ```
    , 
    ```
    meio++
    ```
    ).
    
4.  Se 
    ```
    A[meio] == 1
    ```
    : Já está no meio, apenas avance (
    ```
    meio++
    ```
    ).
    
5.  Se 
    ```
    A[meio] == 2
    ```
    : Troque 
    ```
    meio
    ```
     com 
    ```
    alto
    ```
    . Recue o 
    ```
    alto--
    ```
    . (Atenção: não avance o 
    ```
    meio
    ```
    , o número recém-trazido precisa ser avaliado).
-   **Complexidade Esperada:** Tempo estrito de O(N). Espaço O(1).
    
-   **Entrada:** 
    ```
    [0, 1, 2, 0, 1, 2]
    ```
    
-   **Saída:** 
    ```
    [0, 0, 1, 1, 2, 2]
    ```

### 14\. K-ésimo Menor/Maior Elemento (K’th Smallest/Largest)

**Descrição:** Encontre qual seria o K-ésimo menor ou maior elemento em um array desordenado. **Conceito Chave:** Ordenação Parcial, Heaps ou QuickSelect. **Passo a Passo Sugerido:**

1.  **Solução Básica:** Ordene o array em ordem crescente. O K-ésimo menor estará no índice 
    ```
    K - 1
    ```
    . (Tempo O(NlogN)).
    
2.  **Solução com Min/Max Heap:** Mantenha uma Fila de Prioridade de tamanho K. Ao iterar pelo array, vá atualizando a Heap. (Tempo O(NlogK)).
    
3.  **Solução Ótima (QuickSelect):** Algoritmo baseado no QuickSort que particiona o array buscando apenas o lado em que o elemento K-ésimo deve estar. (Tempo médio O(N)).
-   **Entrada:** 
    ```
    array = [7, 10, 4, 3, 20, 15]
    ```
    , 
    ```
    K = 3
    ```
     (3º menor)
    
-   **Saída:** 
    ```
    7
    ```

### 15\. Contagem de Inversões (Inversion Count)

**Descrição:** Uma inversão ocorre se um par 
```
(i, j)
```
 obedece 
```
i < j
```
, mas o valor 
```
A[i] > A[j]
```
. Qual a quantidade total de inversões no array? **Conceito Chave:** Algoritmo de Divisão e Conquista (Merge Sort modificado). **Passo a Passo Sugerido:**

1.  Adapte o algoritmo Merge Sort. A contagem total será a soma das inversões da metade esquerda + direita + as contadas durante o _Merge_.
    
2.  Durante a junção (Merge) de duas listas ordenadas temporárias (
    ```
    L
    ```
     e 
    ```
    R
    ```
    ):
    
3.  Se 
    ```
    L[i] <= R[j]
    ```
    , copie e avance, sem inversão.
    
4.  Se 
    ```
    L[i] > R[j]
    ```
    , você achou uma inversão! Como 
    ```
    L
    ```
     está ordenada, todos os elementos restantes de 
    ```
    L
    ```
     também serão maiores que 
    ```
    R[j]
    ```
    .
    
5.  Some 
    ```
    (tamanho de L - i)
    ```
     ao seu contador.
-   **Complexidade Esperada:** Tempo de O(NlogN). Espaço O(N).
    
-   **Entrada:** 
    ```
    [8, 4, 2, 1]
    ```
    
-   **Saída:** 
    ```
    6
    ```

### 16\. Número Mínimo de Plataformas (Minimum Platforms Required)

**Descrição:** Dados horários de chegada e partida de trens, encontre o número mínimo de plataformas necessárias para que nenhum trem espere. **Conceito Chave:** Algoritmo Sweep Line (Linha de Varredura). **Passo a Passo Sugerido:**

1.  Ordene os horários de chegada e de partida independentemente em ordem crescente.
    
2.  Posicione 
    ```
    i = 1
    ```
     (próxima chegada) e 
    ```
    j = 0
    ```
     (próxima partida). Contadores: 
    ```
    plataformas = 1
    ```
    , 
    ```
    max_plat = 1
    ```
    .
    
3.  Em loop: se a chegada 
    ```
    [i]
    ```
     for <= partida 
    ```
    [j]
    ```
    , um trem chegou ocupando plataforma. Incremente 
    ```
    plataformas
    ```
     e avance 
    ```
    i
    ```
    . Atualize 
    ```
    max_plat
    ```
    .
    
4.  Se chegada 
    ```
    [i]
    ```
     > partida 
    ```
    [j]
    ```
    , um trem saiu. Decremente 
    ```
    plataformas
    ```
     e avance 
    ```
    j
    ```
    .
    
5.  O resultado será o 
    ```
    max_plat
    ```
    .
-   **Complexidade Esperada:** Tempo O(NlogN). Espaço O(1).
    
-   **Entrada:** 
    ```
    Chegadas = [900, 940, 950, 1100]
    ```
    , 
    ```
    Partidas = [910, 1200, 1120, 1130]
    ```
    
-   **Saída:** 
    ```
    3
    ```

### 17\. Máximo de Reuniões em Uma Sala (Maximum meetings in one room)

**Descrição:** Dados os horários de início e término de 
```
N
```
 reuniões, maximize o número de reuniões que podem ocorrer em uma única sala. **Conceito Chave:** Algoritmo Guloso ordenando pelo término. **Passo a Passo Sugerido:**

1.  Crie uma estrutura para guardar início, fim e id da reunião.
    
2.  **Ordene os objetos pelo horário de término** em ordem crescente. (Quem termina mais rápido libera a sala antes).
    
3.  Selecione a primeira reunião. Guarde o seu horário de término.
    
4.  Itere pelas próximas. Se o horário de início for maior (ou igual) ao término da reunião anterior selecionada, você pode alocá-la. Atualize o término rastreado.
-   **Complexidade Esperada:** Tempo O(NlogN).
    
-   **Entrada:** 
    ```
    Início = [1, 3, 0, 5, 8, 5]
    ```
    , 
    ```
    Fim = [2, 4, 6, 7, 9, 9]
    ```
    
-   **Saída:** 
    ```
    4
    ```

### 18\. Ordenação Específica de Maiúsculas/Minúsculas (Case-specific Sorting of Strings)

**Descrição:** Dada uma string com letras maiúsculas e minúsculas, ordene-a alfabeticamente, mas letras minúsculas só podem ocupar posições originais de minúsculas, e maiúsculas nas posições de maiúsculas. **Conceito Chave:** Separação de dados e fusão in-place. **Passo a Passo Sugerido:**

1.  Itere a string e armazene letras minúsculas em um array e maiúsculas em outro.
    
2.  Ordene ambos os arrays alfabeticamente.
    
3.  Use dois ponteiros para percorrer os arrays ordenados.
    
4.  Itere novamente a string original. Se a posição for uma letra minúscula, substitua pela próxima do array minúsculo ordenado. Faça o análogo para as maiúsculas.
-   **Complexidade Esperada:** Tempo O(NlogN).
    
-   **Entrada:** 
    ```
    "defRTSersUXI"
    ```
    
-   **Saída:** 
    ```
    "deeIRSfrsTUX"
    ```

### 19\. Ordenar por Frequência (Sort by Frequency)

**Descrição:** Ordene um array priorizando os elementos que mais se repetem. Em caso de empate de frequência, ordene pelo menor valor. **Conceito Chave:** Hashes com ordenação customizada. **Passo a Passo Sugerido:**

1.  Construa um HashMap contando a frequência de cada elemento.
    
2.  Crie uma função de ordenação customizada (Comparator).
    
3.  Se as frequências forem diferentes, ordene descrescentemente pela frequência.
    
4.  Se houver empate na frequência, ordene crescentemente pelo valor absoluto do número.
    
5.  Reconstrua o array final.
-   **Complexidade Esperada:** Tempo O(NlogN).
    
-   **Entrada:** 
    ```
    [2, 5, 2, 8, 5, 6, 8, 8]
    ```
    
-   **Saída:** 
    ```
    [8, 8, 8, 2, 2, 5, 5, 6]
    ```

### 20\. Mínimo de Operações para Elementos Distintos (Minimum Operations for Distinct)

**Descrição:** Qual a quantidade mínima de incrementos (+1 em um elemento) necessários para que todos os elementos do array se tornem únicos? **Conceito Chave:** Abordagem Gulosa (Greedy) empurrando o excesso. **Passo a Passo Sugerido:**

1.  Ordene o array em ordem crescente.
    
2.  Inicie 
    ```
    operacoes = 0
    ```
    . Itere a partir do índice 1.
    
3.  Se o número atual 
    ```
    A[i]
    ```
     for menor ou igual ao anterior 
    ```
    A[i-1]
    ```
    , temos uma colisão.
    
4.  O novo valor ideal para 
    ```
    A[i]
    ```
     é 
    ```
    A[i-1] + 1
    ```
    .
    
5.  Adicione 
    ```
    (novo_valor - A[i])
    ```
     às 
    ```
    operacoes
    ```
     e atualize 
    ```
    A[i]
    ```
     com o 
    ```
    novo_valor
    ```
    .
-   **Complexidade Esperada:** Tempo O(NlogN).
    
-   **Entrada:** 
    ```
    [3, 2, 1, 2, 1, 7]
    ```
    
-   **Saída:** 
    ```
    6
    ```
     (O array ficará 
    ```
    [1, 2, 3, 4, 5, 7]
    ```
    ).

### 21\. Máximo de Interseções de Linhas (Maximum intersections lines)

**Descrição:** Dadas duas retas paralelas contendo pontos de origem e destino, quantas linhas cruzam entre si? **Conceito Chave:** Redução para o problema de Contagem de Inversões. **Passo a Passo Sugerido:**

1.  Modele as ligações como pares 
    ```
    [superior, inferior]
    ```
    .
    
2.  Ordene a lista baseando-se estritamente na reta superior de forma crescente.
    
3.  Extraia apenas os números da reta inferior formando um novo array.
    
4.  A quantidade de cruzamentos geométricos é exatamente a Contagem de Inversões deste novo array. Aplique o algoritmo do Exercício 15.
-   **Complexidade Esperada:** Tempo O(NlogN).
    
-   **Entrada:** 
    ```
    Reta 1 = [1, 2, 3]
    ```
    , 
    ```
    Reta 2 = [3, 2, 1]
    ```
    
-   **Saída:** 
    ```
    3
    ```

### 22\. Máximo de Sobreposição de Intervalos (Maximum intervals overlapping)

**Descrição:** Semelhante ao problema das Plataformas, mas o objetivo é identificar o timestamp exato onde houve o maior acúmulo de eventos simultâneos. **Conceito Chave:** Sweep Line isolando timestamps. **Passo a Passo Sugerido:**

1.  Separe 
    ```
    Entradas
    ```
     e 
    ```
    Saídas
    ```
     e ordene ambos em ordem crescente.
    
2.  Use dois ponteiros para rastrear o tempo.
    
3.  Se ocorrer uma Entrada antes ou igual à Saída, incremente as sobreposições atuais.
    
4.  Ao atualizar o recorde máximo de sobreposições, salve imediatamente o timestamp dessa entrada na variável 
    ```
    tempo_pico
    ```
    .
    
5.  Se ocorrer uma Saída, decremente as sobreposições.
-   **Complexidade Esperada:** Tempo O(NlogN).
    
-   **Entrada:** 
    ```
    Entradas = [1, 2, 10, 5, 5]
    ```
    , 
    ```
    Saídas = [4, 5, 12, 9, 12]
    ```
    
-   **Saída:** O ponto temporal de valor 
    ```
    5
    ```
     hospedava 
    ```
    3
    ```
     eventos.

### 23\. Soma Mínima do Produto de Pares Consecutivos (Minimum Product sum of consecutive pairs)

**Descrição:** Permute os elementos de um array par agrupando-os de dois em dois, multiplicando-os e somando todos. Minimize essa soma final. **Conceito Chave:** Abordagem Min-Max de extremidades. **Passo a Passo Sugerido:**

1.  A matemática nos diz que, para minimizar produtos, devemos cruzar o maior número possível com o menor número possível.
    
2.  Ordene o array em ordem crescente.
    
3.  Coloque um ponteiro no começo (
    ```
    esq = 0
    ```
    ) e outro no fim (
    ```
    dir = tamanho - 1
    ```
    ).
    
4.  Multiplique 
    ```
    A[esq] * A[dir]
    ```
     e acumule na soma total.
    
5.  Avance 
    ```
    esq
    ```
     e recue 
    ```
    dir
    ```
     até o fim.
-   **Complexidade Esperada:** Tempo O(NlogN).
    
-   **Entrada:** 
    ```
    [1, 5, 3, 4]
    ```
    
-   **Saída:** 
    ```
    17
    ```
     (Após ordenar 
    ```
    [1,3,4,5]
    ```
    , cruza-se 1_5 e 3_4 = 5 + 12 = 17).

### 24\. Posição de um Elemento após Ordenação Estável (Position of an element after stable sort)

**Descrição:** Preveja o índice exato onde um elemento alvo (passado por índice) pararia se o array fosse ordenado utilizando ordenação estável. **Conceito Chave:** Predição por contagem linear. **Passo a Passo Sugerido:**

1.  Você não precisa usar Sort. Identifique o 
    ```
    alvo = A[indice_desejado]
    ```
    .
    
2.  Inicialize 
    ```
    nova_pos = 0
    ```
    .
    
3.  Varra o array contando os elementos estritamente menores que o 
    ```
    alvo
    ```
     (somando +1 à 
    ```
    nova_pos
    ```
    ).
    
4.  Para garantir a estabilidade, some +1 para elementos que são iguais ao 
    ```
    alvo
    ```
     mas cujos índices originais ocorrem antes do índice do alvo.
-   **Complexidade Esperada:** Tempo O(N). Espaço O(1).
    
-   **Entrada:** 
    ```
    array = [4, 3, 2, 4, 1]
    ```
    , alvo índice 
    ```
    3
    ```
     (O segundo "4")
    
-   **Saída:** 
    ```
    4
    ```

### 25\. Merge Sort para Lista Duplamente Encadeada (Merge Sort for Doubly Linked List)

**Descrição:** Implemente o Merge Sort focando na arquitetura de uma Lista Duplamente Encadeada (
```
next
```
 e 
```
prev
```
). **Conceito Chave:** Ponteiros Rápidos e Lentos em estruturas encadeadas. **Passo a Passo Sugerido:**

1.  Se a lista estiver vazia ou com um só elemento, retorne-a.
    
2.  Para achar o meio sem índices, use o método Tartaruga (pula 1) e Lebre (pula 2). Onde a tartaruga parar, ali é o meio.
    
3.  Quebre os links 
    ```
    next
    ```
     e 
    ```
    prev
    ```
     dividindo a lista em duas fisicamente.
    
4.  Chame o algoritmo recursivamente para ambas as metades.
    
5.  Realize o Merge convencional costurando os ponteiros de forma ordenada, garantindo a via de mão dupla 
    ```
    prev
    ```
    .
-   **Complexidade Esperada:** Tempo O(NlogN). Espaço extra O(1) (apenas ponteiros são rearranjados).
    
-   **Entrada:** 
    ```
    5 <-> 3 <-> 8 <-> 1
    ```
    
-   **Saída:** 
    ```
    1 <-> 3 <-> 5 <-> 8
    ```

### 26\. Ordenação Radix (Radix Sort)

**Descrição:** Algoritmo que quebra a barreira O(N log N) das comparações ao ordenar os números baseando-se estritamente em suas casas decimais (unidade, dezena, etc). **Conceito Chave:** Distribuição linear algorítmica não comparativa. **Passo a Passo Sugerido:**

1.  Encontre o maior valor absoluto do array para descobrir o número máximo de dígitos envolvidos.
    
2.  Inicie uma variável 
    ```
    exp = 1
    ```
     para extrair a casa das unidades.
    
3.  Enquanto 
    ```
    max_val / exp > 0
    ```
    , utilize uma rotina estável (como o Counting Sort) para agrupar e ordenar os números com base estritamente no dígito extraído: 
    ```
    (A[i] / exp) % 10
    ```
    .
    
4.  Multiplique o 
    ```
    exp
    ```
     por 10 para focar na próxima casa decimal, e repita.
-   **Complexidade Esperada:** Tempo O(D⋅(N+B)), onde D é o total de dígitos máximos e B a base decimal (10).
    
-   **Entrada:** 
    ```
    [170, 45, 75, 90, 802, 24, 2, 66]
    ```
    
-   **Saída:** 
    ```
    [2, 24, 45, 66, 75, 90, 170, 802]
    ```

### 27\. Segregar 0s e 1s em um Array (Segregate 0s and 1s in an array)

**Descrição:** Array lotado de zeros (0) e uns (1). Jogue todos os zeros para a esquerda e os uns para a direita numa única varredura. **Conceito Chave:** Dois ponteiros (Left & Right Pointers). **Passo a Passo Sugerido:**

1.  Inicialize ponteiros nas extremidades: 
    ```
    esq = 0
    ```
    , 
    ```
    dir = tamanho - 1
    ```
    .
    
2.  Enquanto 
    ```
    esq < dir
    ```
    :
    
      17.   Avance 
          ```
          esq
          ```
           enquanto encontrar 0.
          
      23.   Recue 
          ```
          dir
          ```
           enquanto encontrar 1.
          
      29.   Se eles pararem e não tiverem se cruzado, você encontrou um 1 na esquerda e um 0 na direita. Troque-os (swap) e continue.
-   **Complexidade Esperada:** Tempo O(N). Espaço O(1).
    
-   **Entrada:** 
    ```
    [0, 1, 0, 1, 1, 0]
    ```
    
-   **Saída:** 
    ```
    [0, 0, 0, 1, 1, 1]
    ```

### 28\. Ordenar Números Pares e Ímpares (Sort even and odd numbers)

**Descrição:** Ordene um array de modo que os números pares fiquem ordenados em ordem crescente, seguidos por todos os números ímpares, mas em ordem decrescente. **Conceito Chave:** Decomposição Binária e Múltiplos critério. **Passo a Passo Sugerido:**

1.  Crie duas listas. Use 
    ```
    numero % 2 == 0
    ```
     para colocar em Pares e o restante em Ímpares.
    
2.  Ordene a lista Par ascendentemente.
    
3.  Ordene a lista Ímpar descrescentemente.
    
4.  Concatene ambas repovoando o array pai.
-   **Complexidade Esperada:** Tempo O(NlogN) pelas ordenações isoladas.
    
-   **Entrada:** 
    ```
    [1, 2, 3, 5, 4, 7, 10]
    ```
    
-   **Saída:** 
    ```
    [2, 4, 10, 7, 5, 3, 1]
    ```

### 29\. Produto Mínimo de K Inteiros (Minimum product of k integers)

**Descrição:** Dado um array inteiramente positivo, calcule o menor produto combinando exatamente 
```
K
```
 elementos. **Conceito Chave:** Guloso combinatório positivo. **Passo a Passo Sugerido:**

1.  Ordene o array de forma crescente.
    
2.  Para que uma multiplicação de números positivos seja a menor possível, basta multiplicarmos os menores componentes disponíveis.
    
3.  Calcule o produto iterando nos 
    ```
    K
    ```
     primeiros elementos do array ordenado.
-   **Complexidade Esperada:** Tempo O(NlogN) (ordenar) ou O(NlogK) (usando Fila de Prioridade / Heap).
    
-   **Entrada:** 
    ```
    array = [11, 8, 5, 7, 5, 100]
    ```
    , 
    ```
    K = 3
    ```
    
-   **Saída:** 
    ```
    200
    ```
     (Multiplicação dos menores: 5 \* 5 \* 8)

### 30\. Permutação de Array com Soma de Pares ≥ K (Array Permutation with Pair Sums ≥ K)

**Descrição:** Tendo dois arrays de mesmo tamanho e um número 
```
K
```
, verifique se é possível rearranjá-los de modo que 
```
A[i] + B[i] >= K
```
 para todo índice. **Conceito Chave:** Emparelhamento Guloso Contrapeso. **Passo a Passo Sugerido:**

1.  A abordagem gulosa ideal para garantir a viabilidade das somas é tentar compensar os números menores com os maiores do outro conjunto.
    
2.  Ordene o array A em ordem crescente.
    
3.  Ordene o array B em ordem decrescente (ou leia de trás para frente).
    
4.  Verifique em uma única passagem: se 
    ```
    A[i] + B[i] < K
    ```
    , retorne 
    ```
    Falso
    ```
     sumariamente.
    
5.  Se passar limpo, retorne 
    ```
    Verdadeiro
    ```
    .
-   **Complexidade Esperada:** Tempo O(NlogN) por conta das ordenações.
    
-   **Entrada:** 
    ```
    A = [2, 1, 3]
    ```
    , 
    ```
    B = [7, 8, 9]
    ```
    , 
    ```
    K = 10
    ```
    
-   **Saída:** 
    ```
    Verdadeiro
    ```
     (Testando 1+9, 2+8, 3+7: todas dão exatamente 10).

</p>

</details>

<details>
  <summary>🔴 Nível 3 - Difícil</summary>

<p>

A fronteira final. Estes problemas exigem extrema clareza e uso profundo de Estruturas de Dados ou algoritmos não triviais, frequentemente com restrições rígidas de Espaço em RAM ($O(1)$).

### 31\. Mesclar Arrays Ordenados com Espaço Extra O(1) (Merge sorted arrays with O(1) extra space)

**Descrição:** Dados dois arrays distintos, mescle-os como se fossem um só, de modo que toda a sequência ordenada preencha o primeiro array inteiro e o excedente preencha o segundo. Restrição estrita: você não pode instanciar novos vetores, o Espaço Auxiliar deve ser obrigatoriamente O(1). **Conceito Chave:** Método de "Space Gap" inspirado na lógica do Shell Sort. **Passo a Passo Sugerido:**

1.  Trate os dois vetores como um fluxo contínuo abstrato de tamanho total 
    ```
    N + M
    ```
    .
    
2.  Calcule um salto ou espaçamento inicial usando a fórmula: 
    ```
    gap = ceil((N+M) / 2)
    ```
    .
    
3.  Compare elementos separados por essa distância de 
    ```
    gap
    ```
    . Se o valor da esquerda for maior que o da direita, aplique um Swap (troca).
    
4.  Você deverá realizar três formas de passagem lógica de ponteiros:
    
      21.   Ambos os ponteiros dentro do Array 1.
          
      23.   Um ponteiro no Array 1 e o outro caindo no Array 2 (esse é o passo crítico).
          
      25.   Ambos os ponteiros avaliando no Array 2.
    
5.  Após varrer a distância, reduza o gap pela metade 
    ```
    gap = ceil(gap / 2)
    ```
     e repita a varredura. Interrompa quando 
    ```
    gap == 0
    ```
    .
-   **Complexidade Esperada:** Tempo de O((n+m)log(n+m)). Espaço perfeito de O(1).
    
-   **Entrada:** 
    ```
    arr1 = [1, 3, 5, 7]
    ```
    , 
    ```
    arr2 = [0, 2, 6, 8, 9]
    ```
    
-   **Saída:** 
    ```
    arr1 = [0, 1, 2, 3]
    ```
    , 
    ```
    arr2 = [5, 6, 7, 8, 9]
    ```

### 32\. Contar Elementos Menores à Direita (Count smaller elements on Right side)

**Descrição:** Para cada elemento 
```
A[i]
```
, informe quantos elementos localizados à sua direita (
```
j > i
```
) são estritamente menores que ele (
```
A[j] < A[i]
```
). **Conceito Chave:** Árvore Indexada Binária (BIT / Fenwick Tree) ou varredura em Merge Sort modificado. **Passo a Passo Sugerido (Versão via Merge Sort):**

1.  A solução força bruta em O(N²) verificando todos falha em limites de tempo longos.
    
2.  Anexe cada valor do array a seu índice original formando um array de pares/tuplas.
    
3.  Execute o algoritmo recursivo de Merge Sort sobre esses pares, com o objetivo secundário de contar.
    
4.  Na fase final de Merge, unindo Metade Esquerda e Metade Direita, use a seguinte propriedade: sempre que o número avaliado na Metade Esquerda for estritamente **maior** que o da Metade Direita, todos os números que sobraram do lado direito até ali vão contar como "pulos" de valores menores à direita.
    
5.  Registre no índice do elemento associado quantas dessas transições acionaram o contador, somando ao total parcial dele.
-   **Complexidade Esperada:** Tempo O(NlogN). Espaço O(N) necessário para as tuplas de ponteiros auxiliares.
    
-   **Entrada:** 
    ```
    [12, 1, 2, 3, 0, 11, 4]
    ```
    
-   **Saída:** 
    ```
    [6, 1, 1, 1, 0, 1, 0]
    ```

### 33\. Menor Soma de Subconjunto Não Representável (Smallest Non-Representable Subset Sum)

**Descrição:** Encontre o menor inteiro positivo que NÃO pode ser representado como a soma de nenhum subconjunto formado pelos elementos numéricos fornecidos no array. **Conceito Chave:** Cobertura de Intervalo Contínuo e Acumulação Progressiva. **Passo a Passo Sugerido:**

1.  Ordene o array de entrada em ordem crescente para processar os limites de forma incremental.
    
2.  Inicie a variável referencial base: 
    ```
    resposta = 1
    ```
    . (Matematicamente testamos a partir de 1. O número não pode ser quebrado, devemos verificar se ele é gerável).
    
3.  Itere sobre os elementos do array ordenado 
    ```
    A[i]
    ```
    .
    
4.  Condição crucial: Se o elemento avaliado 
    ```
    A[i]
    ```
     for **maior** que a sua variável de teste 
    ```
    resposta
    ```
    , ocorre um vazio matemático insuperável. Você acabou de encontrar o "degrau fantasma" que quebra a sequência de possibilidade de combinações. O valor retido em 
    ```
    resposta
    ```
     é o limiar impossível e a solução.
    
5.  Caso o 
    ```
    A[i]
    ```
     seja menor ou igual, isso significa que todo o intervalo até 
    ```
    A[i] + resposta
    ```
     é perfeitamente "combinável". Incorpore o limite: 
    ```
    resposta += A[i]
    ```
    .
-   **Complexidade Esperada:** Tempo O(NlogN) restrito à ordenação da preparação. O cálculo ocorre rapidamente em O(N). Espaço O(1).
    
-   **Entrada:** 
    ```
    [1, 3, 6, 10, 11, 15]
    ```
    
-   **Saída:** 
    ```
    2
    ```
     (Pois 1 é representável, mas como o próximo elemento é 3, falta o número base para gerar o valor 2. Limite quebrado na primeira iteração.)

### 34\. Contar Subarrays com Mediana de Pelo Menos X (Count Subarrays with median at least X)

**Descrição:** A meta é varrer o array e calcular a quantidade de subarrays (segmentos contíguos) em que a mediana estatística daquele segmento seja no mínimo igual ou superior ao valor estipulado 
```
X
```
. **Conceito Chave:** Transformação Binarizada de Pesos + Contagem de Prefix Sum (Soma de Prefixos). **Passo a Passo Sugerido:**

1.  É inviável calcular a mediana localmente em subarrays de forma sequencial. Transforme a lógica: crie um array peso-espelho.
    
2.  Itere no original: se o valor for 
    ```
    >= X
    ```
    , coloque o peso 
    ```
    1
    ```
     na posição do array espelho. Se for 
    ```
    < X
    ```
    , atribua peso 
    ```
    17.1
    ```
    .
    
3.  A brilhante sacada estatística desta conversão é que qualquer subarray onde o somatório isolado das parcelas convertidas resultar em um valor 
    ```
    > 0
    ```
    , isso prova categoricamente que naquele escopo original existiam mais números altos do que baixos, consolidando uma Mediana que atenderá o requisito do valor 
    ```
    >= X
    ```
    .
    
4.  O problema agora vira a questão clássica: "Encontrar a quantidade de Subarrays com Soma Positiva".
    
5.  Aplique a técnica de Array de Soma de Prefixos (Prefix Sum) combinada com uso de uma Fenwick Tree (BIT) para registrar, em uma passagem linear rápida de O(log N), quantos prefixos passados no log da memória histórica tinham valores menores que o prefixo computado localmente na posição avaliada.
-   **Complexidade Esperada:** Tempo computacional excelente de O(NlogN). Espaço atrelado a arrays de pesos de O(N).
    
-   **Entrada:** 
    ```
    array = [2, 1, 4, 3]
    ```
    , alvo estatístico de 
    ```
    X = 3
    ```
    .
    
-   **Saída:** 
    ```
    4
    ```
     (Os blocos qualificados cujas medianas contidas dão 
    ```
    >= 3
    ```
     são: 
    ```
    [3]
    ```
    , 
    ```
    [4]
    ```
    , 
    ```
    [4,3]
    ```
     e o unificado inteiro 
    ```
    [1,4,3]
    ```
    ).

### 35\. Mesclar K Listas Encadeadas Ordenadas (Merge K sorted linked lists)

**Descrição:** Dado um array que abriga referências ou ponteiros diretos apontando para as cabeças de 
```
K
```
 Listas Encadeadas singulares - com a benesse de estarem individualmente ordenadas. A missão é tecê-las construindo e devolvendo apenas um ponteiro único mestre indicando a nascente principal de uma lista contínua gigante perfeitamente ordenada globalmente. **Conceito Chave:** Fusão de Múltiplas Entradas controlada por Fila de Prioridade (Min-Heap). **Passo a Passo Sugerido:**

1.  O grande vilão de performance em abordagens múltiplas convencionais é não priorizar o menor. Declare uma "Min-Heap" local e configure o nó de comparação para julgar o valor do conteúdo interno da Lista.
    
2.  Preencha a primeira rodada capturando exclusivamente a ponta (
    ```
    head
    ```
    ) de todas as 
    ```
    K
    ```
     listas encadeadas passadas em argumento, garantindo inserção ignorando cabeças vazias.
    
3.  Comece o loop mestre operando até a Heap secar inteiramente:
    
4.  Extraia o menor nó alojado na Min-Heap. Ele provou seu valor sendo o líder matemático entre as concorrentes da rodada.
    
5.  Acople o nó selecionado atrás da corrente resultante que está moldando na saída final gerada da estrutura.
    
6.  Avalie o nó recentemente sacado. Ele possuía um ponteiro seguindo com a corrente da onde veio (
    ```
    next != null
    ```
    )? Se sim, engate este irmão adjacente preenchendo o vazio na Heap imediatamente, garantindo reposição contínua sem que a Heap encha desnecessariamente de limites pesados em trânsito e rode fluida.
-   **Complexidade Esperada:** Tempo ágil mitigando explosões fatoriais alocando O(NlogK) no qual 
    ```
    N
    ```
     abrange a contagem sumária de todos os nós soltos presentes. Espaço retido de locação O(K) unicamente focado na largura operacional retida pela Min-Heap viva.
    
-   **Entrada:** 
    ```
    [1->4->5, 1->3->4, 2->6]
    ```
    
-   **Saída:** O bloco inteiro encadeado sem fragmentos soltos: 
    ```
    1->1->2->3->4->4->5->6
    ```
    .

### 36\. Trio com a Menor Diferença de Três Arrays (Smallest Difference Triplet from Three arrays)

**Descrição:** Extraia um esquadrão perfeito de três membros, com a lei inquebrável ditando que você deve recrutar estritamente exato um indivíduo isolado pertencente ao array A, um do B, e um do array C de forma a minimizar a matemática entre sua distância de tamanhos brutos (Valor Máximo daquele trio extraído perante o Valor Mínimo contido). A diferença computada deverá ser a mais estreita exequível possível de se travar. **Conceito Chave:** Pointers Tracking em Expansão Tridimensional. **Passo a Passo Sugerido:**

1.  Descarte busca caótica N³. Ordene preliminarmente os três vetores de entrada do menor para o maior crescimento orgânico de valor local.
    
2.  Invoque 3 ponteiros indicadores independentes partindo do zero em suas fileiras: 
    ```
    i
    ```
    , 
    ```
    j
    ```
     e 
    ```
    k
    ```
    .
    
3.  Processe um loop condicionador travado atuante apenas para fluir caso nem um dos líderes indicadores desabe ultrapassando as fronteiras de sua matriz.
    
4.  Identifique comparativamente os extremos alvos: qual recruta porta o posto do elemento _Máximo_, quem abriga o pilar de _Mínimo_ valor apontado e qual é a força liminar do valor mediador.
    
5.  Averigue e registre o delta matemático 
    ```
    (Máximo - Mínimo)
    ```
    . Confronte a variável e consolide sua retenção salvando sobrepondo a contagem caso a operação resulte em um desvio delta global ainda mais ajustado em espaço do limite guardado de sua diferença mínima histórica salva das passadas anteriores do loop.
    
6.  O segredo da operação: Empurrar membros com patentes grandes infla o buraco; avoque e obrigue marchar somente e solitário apenas o indicador representante dono da fôrma retentora do valor _Mínimo_ daquela trindade de base observada no passo a passo da vez (Incrementar apenas ponteiro de B caso dele adviesse o valor fraco avaliado, por exemplo). Trará oxigenação gerencial puxando e comprimindo o próximo gap e diferença dos soldados ao limite absoluto testável de fronteira para a próxima virada em análise.
-   **Complexidade Esperada:** O custo principal da execução é a tributação referencial preparatória do uso dos sortings limitando num satisfatório O(NlogN).
    
-   **Entrada:** 
    ```
    A=[5, 2, 8]
    ```
    , 
    ```
    B=[10, 7, 12]
    ```
     e array final 
    ```
    C=[9, 14, 6]
    ```
    .
    
-   **Saída:** O Trio referencial ótimo da extração sem falhas gera a resposta do bloco de repasse 
    ```
    [8, 7, 6]
    ```
     (pois ao testar suas combinações resultou no teto de barreira Mínima 8 de A em cota cruzada Mínima contra o valor de C equivalente a 6 gerando ínfima resposta testável 2 e não superável por qualquer grupo isolado diferente da matriz base).

### 37\. Ordenar N Números de 0 a N^2 - 1 em Tempo Linear (Sort n numbers from 0 to n^2 – 1 in linear time)

**Descrição:** É assegurado ao motor que todas as fatias de elementos preenchendo um determinado array numerado restrito de N itens obedecem à regra e limite de 
```
A[i] <= N^2 - 1
```
. Dado que esta regra isolada anômala é inviolável em matriz, demonstre e implante recurso exigindo resposta sem ultrapassar o uso restritivo base da barreira absoluta computacional purificada garantindo Tempo de Complexidade total estrito atestado da ordem O(N). **Conceito Chave:** Adaptação Radix Sort baseado na fórmula Numérica Liminar de Deslocamento de Base Matemática N (Base-N System). **Passo a Passo Sugerido:**

1.  Como qualquer número base sob crivo atende matematicamente a condição testável barreira 
    ```
    X < N^2
    ```
    , sabemos infalivelmente pela propriedade matricial fundamental contida do espectro que este respectivo valor assume fôrma integral caso fosse perfeitamente decomposto transmutado nas bases de raiz unicamente restrito em casas de 
    ```
    N
    ```
     base ao invés da humilde e famosa base limite humana 
    ```
    10
    ```
    , de forma limitrofe portando atrelada somente 2 casas / posições de Dígitos absolutas (Sendo A\*N referencial a Dezena matriz barreira base N e fator B representação em casa unitária purificada em base).
    
2.  Utilize o Counting Sort na armadura liminar do conceito Radix em precisas e imaculadas passadas estritamente de rodadas curtas alocadas de processamento em duas fases.
    
3.  Primeiro acionamento limitrofe (Focar Unidades): Reordene a matriz processando os alvos utilizando o filtro referencial avaliativo baseado em cálculo módulo base, cravado ao isolar limitrofe do membro unitário atestando estrito em limite da expressão matemática atrelada em fôrma: 
    ```
    (A[i] % N)
    ```
    .
    
4.  Dispare a Segunda Barreira e rodada matriz de ordem estável focada do sort limitante agora utilizando-se da fôrma de cota estrita gerencial focado pela matriz superior limite extrator repassado limitrofe no cálculo de divisibilidade de formula isolada: 
    ```
    (A[i] / N)
    ```
    . A ordem cairá perfeitamente estabilizada no assento.
-   **Complexidade Esperada:** Processamento purificado constante blindado em repasse liminar O(N) linear para ambas chamadas sequenciais isoladas da base, drenando tributo e repasse local fixo temporário estipulado alocado liminar RAM base auxiliar para contadores gerenciais barreira de pesos fixada matriz estipulada Cota O(N).
    
-   **Entrada:** Um N preenchido por tamanho de array n=5, gerando cota de muro limitador teto absoluto máximo na avaliação restritiva testável em base 24: 
    ```
    [12, 24, 0, 5, 23]
    ```
    .
    
-   **Saída:** Retorno e fôrma estrutural repassada limpa absoluta matriz: 
    ```
    [0, 5, 12, 23, 24]
    ```
    .

### 38\. Ordenar um Vetor 2D Diagonalmente (Sort a 2D vector diagonally)

**Descrição:** Modifique os limites abandonando vetores simples numéricos listados. Num universo matriz plano Grid 2D preenchida com valores desestruturados, você não alinhará nem as barreiras limites transversas de eixos em Linha e sequer em Colunas limitantes matriz absolutas, mas deverá repassar a lógica garantindo um reprocessamento purificado estrutural reordenando matriz iterativa interna diagonal descendente e limite crescente em alinhamento Norte/Oeste para vertentes base do precipício na forja limitrofe atestada inferior Sul/Leste do seu respectivo alinhamento. **Conceito Chave:** Decomposição Matricial Hash Mapeada em Coordenadas Projeção Diagonal (Matrix Projection Array Hash Mapping). **Passo a Passo Sugerido:**

1.  Todo e qualquer membro alojado estanque da matriz repassada e forja do Grid 2D da base habitante base do mesmo quadrante barreira de repouso em diagonal de Norte/Oeste ao limite cota de muro base inferior Leste emite fundamentalmente uma identidade irrefutável referencial base do resultado contíguo atestado forjado do índice restrito em cota limitrofe computada formula do vetor: 
    ```
    (Índice Linha - Índice Coluna)
    ```
     que exato equivale ao cálculo matemático mestre purificado da forja da variável: 
    ```
    i - j
    ```
    .
    
2.  Estabeleça sua arquitetura barreira de alocação forjada Hash Map atrelada em chaves que estocam Arrays Livres de Listagem iterativas do valor do conteúdo abrigado do elemento.
    
3.  Repasse em Loops sobrepostos em toda matriz: capture valor residente atual 
    ```
    matriz[i][j]
    ```
     inserindo na varredura respectiva atrelada sob base chave referenciada formula repassada 
    ```
    i - j
    ```
    .
    
4.  Uma vez que as rotinas foram drenadas para listas, dispare a reordenação iterativa array por array e ordene-os com regra rigorosa referenciada do Limiar DECRESCENTE atrelado (Do Valor Maior de cota na linha referencial rumo ao seu limite de Valor Inferior barreira na fila limite final). A estratégia decrescente facilita esvaziar do rabo para base sem precisar mexer matriz toda para o topo num estipulado referencial e limite O(1) de custo da lista atestada varrida batida do sistema usando e puxando função 
    ```
    pop
    ```
    .
    
5.  Percorra na matriz inicial novamente limpando e substituindo referencial os valores por atuar acionando pop() limite em cada chave testável limite diagonal.
-   **Complexidade Esperada:** Requesita base O(N \* M) do espaço RAM na formatação do Hash e repasse de estadias da barreira de forjada Array limitrofe, sendo que em tempo de CPU o repasse exige matriz barreira repousante em complexidade base matriz forjada de cota iterativa 
    ```
    O(N * M \log(K))
    ```
     de processamento puro iterativo sendo o limitante base matriz estipulado a variável teto atestada testável em 
    ```
    K
    ```
     alocada base barreira estanque máxima cravada ao cumprimento referencial total gerencial contido dentro de varredura diagonal da matriz teste exata batida da repassada da base do teto limite barreira do vetor limpo e forjado matriz de base array.
    
-   **Entrada:** Malha Base e Matriz Inicial fornecida liminar geradora testável limitante varrida: 
    ```
    [3, 3, 1, 1]
    ```
     
    ```
    [2, 2, 1, 2]
    ```
     
    ```
    [1, 1, 1, 2]
    ```
    
-   **Saída:** Cota Varredura e Ajuste Matriz Limite Alinhada em Diagonalização Orgânica Crescente: 
    ```
    [1, 1, 1, 1]
    ```
     
    ```
    [1, 2, 2, 2]
    ```
     
    ```
    [1, 2, 3, 3]
    ```

### 39\. Imprimir Níveis da Árvore Binária em Ordem Crescente (Print Binary Tree levels in sorted order)

**Descrição:** Percorra uma Árvore Binária capturando por blocos limitantes todos os nós que habitam a mesma altitude topológica ou andar do nível processado na árvore matriz forjada, exibindo como exigência estrita liminar o resgate iterativo de que cada grupo de filhos retornados atestando barreira de piso em questão deve ter cota referenciada rigorosa estrita e crescida ordenadamente em arrays separados sem limitação em complexidade limite repassada atestada limitrofe imposto por estruturação nativa matriz e deformidade limitante das posições originarias físicas irregulares dos ponteiros da matriz no sistema mestre. **Conceito Chave:** Travessia Nivelada com Ordenação Temporária de Camadas (Breadth-First Search com Arrays Auxiliares). **Passo a Passo Sugerido:**

1.  Implemente uma Busca em Largura (BFS - Breadth-First Search) no lugar da Busca em Profundidade DFS.
    
2.  Inicie a alocação matriz em memória instanciando e repassando na base atestada e matriz uma estrutura de 
    ```
    Fila/Queue
    ```
     e empurre a raiz da árvore liminar atestada dentro desta.
    
3.  Desencadeie o loop de travessia 
    ```
    while
    ```
    , atestando que operará somente sob estanque limite "Enquanto a Fila tiver passageiros e não reportar vazia".
    
4.  Determine uma variável referenciada que fixará o censo populacional do andar: capture base barreira estipulando matriz 
    ```
    tamanho_fila
    ```
    . Repasse e inicialize uma Lista auxiliar para absorver referencial.
    
5.  Engate iteração focada de loop rodando matriz com exatidão número estipulado atestada testável e idêntica de e base vezes iguais ao varrido limite do valor extraído anterior matriz 
    ```
    tamanho_fila
    ```
    : Extraia liminar repassando elemento limite da frente atestado matriz forjada referencial limitante barreira, pegue conteúdo e insira no array limitante referencial testável base atestado temporário matriz barreira forjada base. Teste filhos (esquerda, logo apoia direita atestada base barreira), e se presentes os direcione repassando no limite base do enfileiramento matriz.
    
6.  Apos finalização atestada deste micro-ciclo, submeta a matriz lista repassada preenchida pelo referencial andar a ordenamento atestado limite referencial crescente. Salve a emissão atestada no Output Final e inicie com o andar abaixo base liminar do limite repouso atestada e rodada limite base de iteração de repasse forjada.
-   **Complexidade Esperada:** Espaço limitante do limiar matriz cota RAM testável absorverá estanque O(N) exigindo uso focado na manutenção barreira temporária da 
    ```
    Fila
    ```
     para alocação testável atestada gerencial limitante. Tempo computacional repousará na cadência matriz base da avaliação dos loops internos atestada limitrofe varredura barreira consumindo liminar de custo forjado referencial repassado em alocação teste atestada testável de absorção total e restritivo limite estipulado O(NlogM) no teto matriz varredura na barreira atestada de resposta base, onde M descreve em limite repassada de base atestada no censo a largura estrita atestada populacional absoluta máxima atestada na força liminar de concentração nós que povoam e preenchem matriz testável e limitante concentrada atestada em único andar nível limite testável máximo limite repouso atestado.
    
-   **Entrada:** Escopo Raiz Forjada Inicial Array Referencial de Mapeamento:
    
    ```
         7    
       /   \  
      6     5 
     / \   / \
    4   3 2   1
      
    
    ```
    
-   **Saída:** Relatório Formatado Varredura Testável Ordenada Matriz Estrutural Resultante e Atestada Mapeamento Final: Nível 0: 
    ```
    [7]
    ```
     Nível 1: 
    ```
    [5, 6]
    ```
     Nível 2: 
    ```
    [1, 2, 3, 4]
    ```
     (Independentemente da alocação de pais na hierarquia ou posição na esquerda e direita da árvore da matriz de forja, a saída resultará ordenada matriz barreira na emissão por limite referencial e valor absoluto liminar no repasse da testagem do output).

</p>

</details>
