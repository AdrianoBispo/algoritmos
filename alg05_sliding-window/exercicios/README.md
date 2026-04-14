# Lista de Exercícios

Esta lista de exercícios e guia de estudos foi criada para fortalecer a lógica de programação utilizando a técnica de **Janela Flutuante (Sliding Window)**. O foco aqui não é a sintaxe específica de uma linguagem, mas sim o raciocínio algorítmico estruturado. Você pode resolver esses problemas utilizando qualquer linguagem de programação moderna (C, C++, Java, Python, JavaScript/TypeScript, Go, Rust, etc.).

## 🟢 Nível: Fácil

Neste nível, os problemas focam na mecânica básica de criar uma janela, expandi-la e deslizá-la sem lógicas de condição muito complexas.

### 1\. Soma máxima de uma subarray de tamanho k

**Descrição:** Dado um array de inteiros (podendo conter valores positivos e negativos) e um número inteiro 
```
k
```
, sua tarefa é encontrar a soma máxima resultante de qualquer subarray contíguo de tamanho exato 
```
k
```
. **Input / Output Exemplo:**

-   **Input:** 
    ```
    arr = [2, 1, 5, 1, 3, 2]
    ```
    , 
    ```
    k = 3
    ```
    
-   **Output:** 
    ```
    9
    ```
     (Subarray 
    ```
    [5, 1, 3]
    ```
    )

**Passo a passo lógico detalhado:**

1.  **Inicialização:** Verifique se o tamanho do array é menor que 
    ```
    k
    ```
    . Se for, o problema é inválido (retorne um erro ou valor nulo dependendo da linguagem).
    
2.  **Primeira Janela:** Calcule a soma dos primeiros 
    ```
    k
    ```
     elementos. Esta é a sua base. Salve essa soma em duas variáveis: 
    ```
    soma_atual
    ```
     e 
    ```
    soma_maxima
    ```
    .
    
3.  **Deslizamento:** Inicie um loop a partir do índice 
    ```
    k
    ```
     até o final do array.
    
4.  **Atualização em O(1):** Para "deslizar" a janela, pegue a 
    ```
    soma_atual
    ```
    , adicione o elemento que está entrando na janela (índice atual) e subtraia o elemento que ficou para trás (índice atual - 
    ```
    k
    ```
    ).
    
5.  **Checagem:** Compare a 
    ```
    soma_atual
    ```
     com a 
    ```
    soma_maxima
    ```
     e atualize a máxima se necessário.
-   **Complexidade:** Tempo O(N) porque passamos pelo array apenas uma vez. Espaço O(1) pois usamos apenas variáveis auxiliares simples.

### 2\. Menor janela contendo 0, 1 e 2

**Descrição:** Dada uma string composta exclusivamente pelos caracteres '0', '1' e '2', encontre o tamanho da menor substring contígua que contenha pelo menos uma ocorrência de cada um dos três dígitos. **Input / Output Exemplo:**

-   **Input:** 
    ```
    S = "01212"
    ```
    
-   **Output:** 
    ```
    3
    ```
     (A substring "012")

**Passo a passo lógico detalhado:**

1.  **Rastreamento:** Crie variáveis ou um array de tamanho 3 para armazenar o _último índice visto_ para cada caractere ('0', '1', '2'). Inicialize todas com 
    ```
    3.1
    ```
    .
    
2.  **Iteração:** Percorra a string com um único ponteiro (representando o fim da janela) da esquerda para a direita.
    
3.  **Atualização de Estado:** A cada passo, atualize o índice do caractere atual.
    
4.  **Condição de Validação:** A janela só é válida se todos os três índices forem diferentes de 
    ```
    13.1
    ```
     (ou seja, você já viu todos pelo menos uma vez).
    
5.  **Cálculo de Tamanho:** Se a janela for válida, o tamanho atual dela será a diferença entre o índice atual e o _menor_ índice entre os três armazenados, somando 1.
    
6.  **Otimização:** Mantenha o registro do menor tamanho encontrado. Retorne 0 ou -1 se o loop terminar e não encontrar a janela.
-   **Complexidade:** Tempo O(N), Espaço O(1).

### 3\. Verificar se uma permutação do padrão é substring

**Descrição:** Dadas duas strings, um 
```
texto
```
 e um 
```
padrão
```
, verifique se alguma permutação exata do 
```
padrão
```
 existe como substring contígua dentro do 
```
texto
```
. Um anagrama é considerado uma permutação. **Input / Output Exemplo:**

-   **Input:** 
    ```
    texto = "BACDGABCDA"
    ```
    , 
    ```
    padrao = "ABCD"
    ```
    
-   **Output:** 
    ```
    Verdadeiro
    ```
     (A substring "BACD" é uma permutação válida)

**Passo a passo lógico detalhado:**

1.  **Casos Base:** Se o 
    ```
    padrão
    ```
     for maior que o 
    ```
    texto
    ```
    , retorne falso imediatamente.
    
2.  **Mapa de Frequência:** Crie um array de frequência de tamanho 26 (assumindo apenas letras minúsculas ou maiúsculas) para contar os caracteres do 
    ```
    padrão
    ```
    . Faça o mesmo para a primeira janela do 
    ```
    texto
    ```
     (de tamanho igual ao do 
    ```
    padrão
    ```
    ).
    
3.  **Comparação de Mapas:** Se os dois arrays de frequência forem exatamente iguais, retorne verdadeiro. Comparar arrays de tamanho fixo 26 é uma operação O(1).
    
4.  **Deslizamento:** Mova a janela um caractere para a direita: adicione a frequência do novo caractere que entra na janela e decremente a frequência do caractere que sai da extremidade esquerda.
    
5.  **Verificação Contínua:** Continue comparando os mapas a cada passo.
-   **Complexidade:** Tempo O(N), Espaço O(1) (o tamanho do alfabeto é constante).

### 4\. Contar subarrays estritamente crescentes

**Descrição:** Dado um array numérico, conte o número total de subarrays contíguos onde os elementos estão organizados em ordem estritamente crescente (ex: a<b<c). **Input / Output Exemplo:**

-   **Input:** 
    ```
    arr = [1, 2, 2, 4]
    ```
    
-   **Output:** 
    ```
    4
    ```
     (Subarrays: 
    ```
    [1]
    ```
    , 
    ```
    [2]
    ```
    , 
    ```
    [2]
    ```
    , 
    ```
    [4]
    ```
    , 
    ```
    [1, 2]
    ```
    , 
    ```
    [2, 4]
    ```
    )

**Passo a passo lógico detalhado:**

1.  **Entendendo a Matemática:** Se você tem uma sequência crescente de tamanho 
    ```
    L
    ```
    , ela contribui com 
    ```
    L
    ```
     novos subarrays válidos ao resultado total.
    
2.  **Estado Inicial:** Inicialize um contador 
    ```
    tamanho_janela = 1
    ```
     (todo elemento único é crescente por si só) e 
    ```
    total = 1
    ```
     (contabilizando o primeiro elemento).
    
3.  **Travessia:** Percorra o array a partir do segundo elemento (índice 1).
    
4.  **Expansão da Janela:** Se o elemento atual for estritamente maior que o anterior (
    ```
    arr[i] > arr[i-1]
    ```
    ), incremente o 
    ```
    tamanho_janela
    ```
    . Adicione o valor de 
    ```
    tamanho_janela
    ```
     à variável 
    ```
    total
    ```
    .
    
5.  **Quebra de Janela:** Se a sequência for quebrada (o atual não for maior que o anterior), resete o 
    ```
    tamanho_janela
    ```
     para 1 e adicione 1 ao 
    ```
    total
    ```
    .
-   **Complexidade:** Tempo O(N), Espaço O(1).

### 5\. Remover caracteres consecutivos

**Descrição:** Dada uma string, processe-a da esquerda para a direita removendo todos os caracteres que são repetições consecutivas do caractere anterior, deixando apenas uma única ocorrência de cada "bloco" de caracteres. **Input / Output Exemplo:**

-   **Input:** 
    ```
    S = "aabbccba"
    ```
    
-   **Output:** 
    ```
    "abcba"
    ```

**Passo a passo lógico detalhado:**

1.  **Inicialização:** Crie uma estrutura para construir a resposta (como um StringBuilder em Java, ou array em JS/Python para evitar concatenações custosas de strings imutáveis).
    
2.  **Primeiro Elemento:** Adicione o primeiro caractere da string original à sua estrutura de resultado.
    
3.  **Avaliação Relativa:** Inicie um loop do segundo caractere em diante. A "janela" aqui analisa apenas dois elementos adjacentes: o caractere atual e o último caractere que foi inserido no resultado.
    
4.  **Decisão:** Se o caractere atual for diferente do último caractere processado, anexe-o ao resultado. Caso contrário, ignore-o e continue o loop.
-   **Complexidade:** Tempo O(N) para varrer a string, Espaço O(N) no pior caso para armazenar a string resultante.

### 6\. Soma máxima de subarray <= x

**Descrição:** Encontre a soma máxima de um subarray contíguo cuja soma não exceda (seja menor ou igual a) um valor 
```
x
```
 especificado. Assuma que o array contém números inteiros não negativos. **Input / Output Exemplo:**

-   **Input:** 
    ```
    arr = [1, 2, 3, 4, 5]
    ```
    , 
    ```
    x = 11
    ```
    
-   **Output:** 
    ```
    10
    ```
     (Subarray 
    ```
    [1, 2, 3, 4]
    ```
    )

**Passo a passo lógico detalhado:**

1.  **Janela Dinâmica:** Aqui o tamanho da janela não é fixo. Use dois ponteiros (
    ```
    inicio
    ```
     e 
    ```
    fim
    ```
    ), ambos começando no índice 0. Inicialize a 
    ```
    soma_atual = 0
    ```
     e 
    ```
    soma_maxima = 0
    ```
    .
    
2.  **Expansão:** Inicie um loop com o ponteiro 
    ```
    fim
    ```
    . Adicione o valor de 
    ```
    arr[fim]
    ```
     à 
    ```
    soma_atual
    ```
    .
    
3.  **Validação e Encolhimento:** Use um loop 
    ```
    while
    ```
     interno. Enquanto a 
    ```
    soma_atual
    ```
     for maior que 
    ```
    x
    ```
    , significa que a janela violou a regra. Subtraia o valor apontado por 
    ```
    arr[inicio]
    ```
     da 
    ```
    soma_atual
    ```
     e incremente o ponteiro 
    ```
    inicio
    ```
     em 1.
    
4.  **Registro de Sucesso:** Assim que o loop 
    ```
    while
    ```
     interno terminar, a janela será válida novamente (soma <= x). Atualize a 
    ```
    soma_maxima
    ```
     comparando-a com a 
    ```
    soma_atual
    ```
    .
    
5.  **Retorno:** Retorne a 
    ```
    soma_maxima
    ```
     ao final.
-   **Complexidade:** Tempo O(N). Mesmo havendo um loop aninhado, cada ponteiro (
    ```
    inicio
    ```
     e 
    ```
    fim
    ```
    ) percorre o array no máximo uma vez. Espaço O(1).

## 🟡 Nível: Médio

Problemas de nível médio frequentemente requerem o uso de estruturas de dados auxiliares (como Mapas de Hash ou Sets) para gerenciar o estado dos elementos que estão _dentro_ da janela dinâmica.

### 7\. Maior substring com caracteres distintos

**Descrição:** Dado um string, encontre o comprimento da maior substring contígua que não contém nenhum caractere repetido. Este é um dos problemas clássicos mais famosos de entrevistas. **Input / Output Exemplo:**

-   **Input:** 
    ```
    S = "abcabcbb"
    ```
    
-   **Output:** 
    ```
    3
    ```
     (A substring "abc" ou "bca" ou "cab")

**Passo a passo lógico detalhado:**

1.  **Estrutura de Rastreamento:** Use um HashSet ou um HashMap (para guardar os índices dos caracteres) para gerenciar os caracteres presentes na janela atual.
    
2.  **Dois Ponteiros:** 
    ```
    inicio
    ```
     = 0 e 
    ```
    fim
    ```
     = 0. Variável 
    ```
    tamanho_maximo
    ```
     = 0.
    
3.  **Avanço:** Expanda a janela iterando com o ponteiro 
    ```
    fim
    ```
    .
    
4.  **Resolução de Conflitos:** Se o caractere apontado por 
    ```
    fim
    ```
     já existir no conjunto, sua janela está inválida. Você deve usar um loop 
    ```
    while
    ```
     para remover do conjunto o caractere apontado pelo ponteiro 
    ```
    inicio
    ```
    , incrementando o 
    ```
    inicio
    ```
    , até que o caractere duplicado não esteja mais no conjunto. _(Otimização: Se usar um HashMap com índices, pode pular o ponteiro 
    ```
    inicio
    ```
     diretamente para 
    ```
    indice_repetido + 1
    ```
    )._
    
5.  **Adição e Atualização:** Adicione o novo caractere ao conjunto. Calcule o tamanho da janela atual (
    ```
    fim - inicio + 1
    ```
    ) e atualize o 
    ```
    tamanho_maximo
    ```
    .
-   **Complexidade:** Tempo O(N), Espaço O(min(N,M)) onde M é o tamanho do alfabeto, pois o conjunto guarda caracteres únicos.

### 8\. Substrings com K distintos

**Descrição:** Dada uma string e um inteiro 
```
k
```
, conte o número exato de substrings contíguas que contêm exatamente 
```
k
```
 caracteres distintos. **Input / Output Exemplo:**

-   **Input:** 
    ```
    S = "aba"
    ```
    , 
    ```
    k = 2
    ```
    
-   **Output:** 
    ```
    3
    ```
     ("ab", "ba", "aba")

**Passo a passo lógico detalhado:** _Dica de Ouro Algorítmica: O conceito de "contar EXATAMENTE K" é difícil com janela flutuante direta, porque a janela pode continuar válida ao se expandir. O truque matemático é calcular:_ 
```
Exatamente(K) = No_Maximo(K) - No_Maximo(K-1)
```
.

1.  **Função Auxiliar:** Crie uma função chamada 
    ```
    subStringsComNoMaximo(string, k)
    ```
     que retorna um inteiro.
    
2.  **Lógica do No Máximo K:** Dentro da função, use dois ponteiros e um Mapa de Hash para rastrear a frequência dos caracteres.
    
3.  **Expansão e Ajuste:** Expanda a direita. Se o tamanho do Mapa (número de chaves) exceder 
    ```
    K
    ```
    , encolha da esquerda removendo as contagens até que o tamanho do mapa volte a ser 
    ```
    <= K
    ```
    .
    
4.  **Cálculo de Combinações:** Quando a janela é válida, o número de substrings válidas _que terminam no índice direito atual_ é exatamente 
    ```
    (direita - esquerda + 1)
    ```
    . Adicione isso ao total.
    
5.  **Conclusão:** Chame a função duas vezes no código principal e retorne a subtração mencionada na dica.
-   **Complexidade:** Tempo O(N) para cada chamada da função. Espaço O(K) para armazenar o mapa de frequências.

### 9\. Máximo de 1s consecutivos com K flips

**Descrição:** Dado um array binário (apenas 0s e 1s), você tem permissão para virar (flip) no máximo 
```
k
```
 zeros para o valor um. Encontre o comprimento máximo de uma subarray contendo apenas números 1 após as viradas. **Input / Output Exemplo:**

-   **Input:** 
    ```
    arr = [1,1,1,0,0,0,1,1,1,1,0]
    ```
    , 
    ```
    k = 2
    ```
    
-   **Output:** 
    ```
    6
    ```
     (Ao virar os dois últimos zeros da primeira sequência ou os dois primeiros da segunda)

**Passo a passo lógico detalhado:**

1.  **Mudança de Perspectiva:** Em vez de pensar em "virar" os números, reformule o problema: "Encontre a maior subarray que contenha _no máximo_ 
    ```
    k
    ```
     números 
    ```
    0
    ```
    ".
    
2.  **Janela Dinâmica:** Use os ponteiros 
    ```
    esquerda
    ```
     e 
    ```
    direita
    ```
     começando em 0. Mantenha um 
    ```
    contador_zeros = 0
    ```
    .
    
3.  **Deslizamento:** Avance o ponteiro da 
    ```
    direita
    ```
    . Se o elemento encontrado for 
    ```
    0
    ```
    , incremente o 
    ```
    contador_zeros
    ```
    .
    
4.  **Ajuste de Custo:** Enquanto o 
    ```
    contador_zeros
    ```
     for estritamente maior que 
    ```
    k
    ```
    , a janela excedeu seu "orçamento" de flips. Verifique o elemento no ponteiro da 
    ```
    esquerda
    ```
    : se for 
    ```
    0
    ```
    , decremente o 
    ```
    contador_zeros
    ```
    . Avance a 
    ```
    esquerda
    ```
     em 1.
    
5.  **Maximização:** O tamanho da sequência contínua a cada iteração válida será 
    ```
    (direita - esquerda + 1)
    ```
    . Mantenha o valor máximo.
-   **Complexidade:** Tempo O(N), Espaço O(1).

### 10\. Máximo de frutas em duas cestas

**Descrição:** Você está visitando uma fazenda com uma única fileira de árvores frutíferas da esquerda para a direita. As árvores são representadas por um array de inteiros, onde cada número representa um "tipo" de fruta. Você tem exatamente duas cestas. Cada cesta só pode conter um único tipo de fruta, mas a quantidade é ilimitada. Você deve começar de alguma árvore e colher consecutivamente. Qual é a maior quantidade de árvores (frutas) que você consegue colher? **Input / Output Exemplo:**

-   **Input:** 
    ```
    arr = [1, 2, 1, 2, 3]
    ```
    
-   **Output:** 
    ```
    4
    ```
     (Colhendo das árvores 0 a 3, subarray 
    ```
    [1, 2, 1, 2]
    ```
    )

**Passo a passo lógico detalhado:**

1.  **Tradução Algorítmica:** Este problema pitoresco é uma metáfora exata para: "Encontre a maior subarray com no máximo 2 elementos distintos". (Idêntico ao exercício 8 com 
    ```
    k=2
    ```
    ).
    
2.  **Estado:** Use um Mapa de Hash para rastrear o 
    ```
    tipo_da_fruta
    ```
     (chave) e a 
    ```
    quantidade_colhida
    ```
     (valor).
    
3.  **Avanço:** Expanda a direita, inserindo as frutas no mapa.
    
4.  **Excesso de Cestas:** Se houver mais de 2 chaves no mapa, você pegou um terceiro tipo de fruta. Encolha a janela pela esquerda: decremente a contagem da fruta no índice 
    ```
    esquerda
    ```
    . Se a contagem chegar a 0, remova a chave do mapa. Incremente a 
    ```
    esquerda
    ```
     até o mapa ter apenas 2 chaves novamente.
    
5.  **Atualização:** Mantenha o tamanho máximo da janela a cada passo.
-   **Complexidade:** Tempo O(N), Espaço O(1) (o mapa nunca terá mais de 3 elementos ao mesmo tempo).

### 11\. Substrings de comprimento k com k-1 elementos distintos

**Descrição:** Dada uma string e um tamanho de janela fixo 
```
k
```
, conte o número de substrings contíguas que possuem tamanho exato 
```
k
```
 e contêm exatamente 
```
k-1
```
 caracteres distintos (isso significa que na janela inteira, apenas um único caractere está duplicado uma vez, e os demais são únicos). **Input / Output Exemplo:**

-   **Input:** 
    ```
    S = "abcc"
    ```
    , 
    ```
    k = 2
    ```
    
-   **Output:** 
    ```
    1
    ```
     (Substring "cc" tem 2 caracteres de comprimento, e apenas 1 distinto, que é 2-1).

**Passo a passo lógico detalhado:**

1.  **Setup Inicial:** Como o tamanho é conhecido (
    ```
    k
    ```
    ), estamos lidando com uma _Janela Fixa_. Inicialize um mapa de frequências.
    
2.  **Construção da Primeira Janela:** Preencha o mapa com os primeiros 
    ```
    k
    ```
     caracteres da string.
    
3.  **Condição de Contagem:** Verifique o número de chaves do mapa. Se for exatamente igual a 
    ```
    k-1
    ```
    , incremente seu 
    ```
    contador_de_resultados
    ```
    .
    
4.  **Ciclo de Deslizamento:** Deslize a janela a partir do índice 
    ```
    k
    ```
     até o fim:
    
      29.   Remova/decremente o caractere que sai (índice 
          ```
          i - k
          ```
          ). Se a contagem chegar a zero, delete a chave.
          
      35.   Adicione/incremente o novo caractere que entra (índice 
          ```
          i
          ```
          ).
          
      41.   Verifique a condição (
          ```
          chaves == k-1
          ```
          ) e atualize o contador.
-   **Complexidade:** Tempo O(N), Espaço O(K).

### 12\. Remoções mínimas para soma-alvo

**Descrição:** Dado um array de inteiros e um valor 
```
alvo
```
, você pode realizar operações removendo elementos das extremidades (ou da esquerda, ou da direita). Encontre o número mínimo de elementos que precisam ser removidos para que a soma exata dos elementos removidos seja igual ao 
```
alvo
```
. **Input / Output Exemplo:**

-   **Input:** 
    ```
    arr = [1,1,4,2,3]
    ```
    , 
    ```
    alvo = 5
    ```
    
-   **Output:** 
    ```
    2
    ```
     (Remover os elementos 2 e 3 da extremidade direita)

**Passo a passo lógico detalhado:**

1.  **O Truque do Inverso:** Remover elementos das pontas deixa um subarray contínuo no meio. Se você quer que a soma das pontas seja 
    ```
    alvo
    ```
    , significa que você quer encontrar a _maior_ subarray contínua no meio cuja soma seja 
    ```
    Soma_Total - Alvo
    ```
    .
    
2.  **Matemática Inicial:** Calcule a 
    ```
    soma_total
    ```
     de todo o array. Defina 
    ```
    alvo_meio = soma_total - alvo
    ```
    .
    
3.  **Validação:** Se 
    ```
    alvo_meio < 0
    ```
    , é impossível. Retorne -1. Se for 0, retorne o tamanho do array inteiro.
    
4.  **Buscando a Maior Janela:** Aplique a janela deslizante dinâmica clássica para encontrar o comprimento da maior subarray cuja soma seja _exatamente_ 
    ```
    alvo_meio
    ```
    .
    
5.  **Resultado Final:** A resposta será 
    ```
    Tamanho_Total_do_Array - Tamanho_da_Maior_Subarray_Encontrada
    ```
    . Se nenhuma subarray exata for encontrada, retorne -1.
-   **Complexidade:** Tempo O(N), Espaço O(1).

### 13\. Substituição da maior sequência repetida de caracteres

**Descrição:** Dada uma string em letras maiúsculas, você tem a permissão de substituir no máximo 
```
k
```
 caracteres para qualquer outro caractere maiúsculo. O objetivo é encontrar o comprimento da maior substring resultante que contenha o mesmo caractere repetido repetidas vezes. **Input / Output Exemplo:**

-   **Input:** 
    ```
    S = "AABABBA"
    ```
    , 
    ```
    k = 1
    ```
    
-   **Output:** 
    ```
    4
    ```
     (Substitua o primeiro 'B' para ter "AAAA", ou o último 'A' para ter "BBBB")

**Passo a passo lógico detalhado:**

1.  **Lógica de Desperdício:** Em qualquer janela que você considere, o cenário ideal é manter o caractere mais frequente e substituir os "outros".
    
2.  **Mapa de Frequência Dinâmico:** Use um array de tamanho 26 para rastrear a frequência dos caracteres na janela atual.
    
3.  **Ponteiros e Rastreador Max:** Use ponteiros 
    ```
    esquerda
    ```
     e 
    ```
    direita
    ```
    . Mantenha uma variável 
    ```
    max_freq
    ```
     que guarda a contagem do caractere mais frequente na janela atual.
    
4.  **Deslizamento:** Avance 
    ```
    direita
    ```
    , atualize a contagem e atualize 
    ```
    max_freq
    ```
     (
    ```
    max_freq = max(max_freq, contagem_atual)
    ```
    ).
    
5.  **Fórmula de Avaliação:** A quantidade de letras que precisam ser alteradas na janela é 
    ```
    (Tamanho_da_Janela - max_freq)
    ```
    .
    
6.  **Encolhimento:** Se 
    ```
    (direita - esquerda + 1) - max_freq > k
    ```
    , sua janela é inválida. Diminua a contagem do caractere em 
    ```
    esquerda
    ```
     e incremente 
    ```
    esquerda
    ```
    . _(Nota: 
    ```
    max_freq
    ```
     não precisa ser rebaixado estritamente para manter a corretude da janela máxima, pois só nos importamos quando a janela puder crescer ainda mais)._
-   **Complexidade:** Tempo O(N), Espaço O(1).

### 14\. Subarray binária com soma

**Descrição:** Dado um array composto apenas por zeros e uns, e um número inteiro 
```
S
```
, conte quantos subarrays _contíguos_ têm a soma exata igual a 
```
S
```
. **Input / Output Exemplo:**

-   **Input:** 
    ```
    arr = [1,0,1,0,1]
    ```
    , 
    ```
    S = 2
    ```
    
-   **Output:** 
    ```
    4
    ```

**Passo a passo lógico detalhado:** _Dica de Arquitetura: Janela flutuante clássica falha aqui se houver elementos que somam zero (como valores negativos ou o próprio zero contínuo), porque expandir não necessariamente aumenta a soma. Usaremos a técnica de Somas de Prefixo (Prefix Sums) com HashMap._

1.  **Mapa de Prefixos:** Crie um mapa para armazenar 
    ```
    (soma_acumulada -> frequencia_dessa_soma)
    ```
    . Inicialize o mapa com 
    ```
    (0 -> 1)
    ```
     para cobrir o caso em que a própria soma a partir do índice 0 já bate com o alvo.
    
2.  **Iteração e Soma:** Percorra o array mantendo uma variável 
    ```
    soma_atual
    ```
    . Adicione o elemento atual a ela.
    
3.  **Checagem de Complemento:** O que estamos buscando no passado é um prefixo cuja soma seja 
    ```
    soma_atual - S
    ```
    . Verifique se essa diferença existe no mapa. Se existir, some a frequência dela ao seu contador total.
    
4.  **Registro:** Atualize o mapa incrementando a frequência da 
    ```
    soma_atual
    ```
     atual no mapa.
-   **Complexidade:** Tempo O(N) em média, Espaço O(N) para armazenar o mapa.

### 15\. Produto da subarray menor que K

**Descrição:** Dado um array de inteiros estritamente positivos, retorne o número de subarrays contíguos onde o produto de todos os seus elementos seja estritamente menor que 
```
k
```
. **Input / Output Exemplo:**

-   **Input:** 
    ```
    arr = [10, 5, 2, 6]
    ```
    , 
    ```
    k = 100
    ```
    
-   **Output:** 
    ```
    8
    ```

**Passo a passo lógico detalhado:**

1.  **Caso Extremo:** Como os números são positivos, se 
    ```
    k <= 1
    ```
    , não existe produto válido (visto que o menor elemento positivo é 1). Retorne 0 imediatamente.
    
2.  **Configuração da Janela:** Inicialize 
    ```
    produto = 1
    ```
    , 
    ```
    esquerda = 0
    ```
    , 
    ```
    total = 0
    ```
    .
    
3.  **Avanço (Multiplicação):** Faça um loop com 
    ```
    direita
    ```
    . Multiplique 
    ```
    produto
    ```
     por 
    ```
    arr[direita]
    ```
    .
    
4.  **Ajuste (Divisão):** Use um 
    ```
    while (produto >= k)
    ```
    . Dentro dele, divida o 
    ```
    produto
    ```
     por 
    ```
    arr[esquerda]
    ```
     e avance 
    ```
    esquerda
    ```
    . Isso encolhe a janela até que o produto fique estritamente menor que 
    ```
    k
    ```
    .
    
5.  **A Matemática das Subarrays:** A cada passo que a janela é válida, toda subarray que _termina_ no índice 
    ```
    direita
    ```
     é válida. O número dessas subarrays é exatamente 
    ```
    (direita - esquerda + 1)
    ```
    . Adicione isso ao 
    ```
    total
    ```
    .
-   **Complexidade:** Tempo O(N), Espaço O(1).

### 16\. Contar ocorrências de anagramas

**Descrição:** Dadas uma string longa (
```
txt
```
) e uma string padrão menor (
```
pat
```
), encontre as posições iniciais (índices 0-based) de todos os anagramas da palavra padrão presentes dentro do texto. **Input / Output Exemplo:**

-   **Input:** 
    ```
    txt = "cbaebabacd"
    ```
    , 
    ```
    pat = "abc"
    ```
    
-   **Output:** 
    ```
    [0, 6]
    ```
     (Os anagramas são "cba" no índice 0 e "bac" no índice 6)

**Passo a passo lógico detalhado:**

1.  **Janela Fixa:** O tamanho da janela é exatamente o tamanho do padrão 
    ```
    pat
    ```
    .
    
2.  **Mapas de Frequência:** Construa um mapa (ou array de 26 posições) para o padrão. Construa outro mapa para a primeira janela no 
    ```
    txt
    ```
    .
    
3.  **Processamento Uniforme:** A cada posição da janela, compare se os dois mapas são iguais. Se forem, insira o ponteiro da esquerda (início da janela) no array de resultados.
    
4.  **Manutenção Contínua:** Ao deslizar a janela para a direita, decremente a frequência do caractere no índice 
    ```
    esquerda
    ```
    , e incremente a do novo caractere no índice 
    ```
    direita
    ```
    .
-   **Complexidade:** Tempo O(N) (comparação de arrays de tamanho fixo 26 é O(1)), Espaço O(1).

### 17\. Maior soma de subarray com tamanho de pelo menos k

**Descrição:** Dado um array de inteiros (que pode incluir números negativos) e um número inteiro 
```
k
```
, encontre a maior soma de um subarray contíguo que tenha _pelo menos_ 
```
k
```
 elementos em seu comprimento. **Input / Output Exemplo:**

-   **Input:** 
    ```
    arr = [1, -2, 2, -3], k = 2
    ```
    
-   **Output:** 
    ```
    1
    ```
     (A subarray 
    ```
    [1, -2, 2]
    ```
     tem tamanho 3, soma = 1. A janela de tamanho 2 
    ```
    [1, -2]
    ```
     tem soma -1)

**Passo a passo lógico detalhado:** _Dica: Uma abordagem direta de janela flutuante não funciona perfeitamente por causa dos números negativos. Vamos combinar a soma de prefixos máxima com a janela deslizante._

1.  **Cálculo da Soma Máxima (Kadane Modificado):** Crie um array auxiliar 
    ```
    max_soma
    ```
     do mesmo tamanho do array original. Preencha-o guardando a soma máxima de qualquer subarray que termine no índice 
    ```
    i
    ```
    .
    
2.  **Janela Base:** Calcule a soma da primeira janela de tamanho exato 
    ```
    k
    ```
    . Inicialize a 
    ```
    resposta
    ```
     com esse valor.
    
3.  **Deslizamento Estratégico:** A partir de 
    ```
    i = k
    ```
     até o final do array:
    
      27.   Atualize a soma da janela atual de tamanho 
          ```
          k
          ```
           (adiciona 
          ```
          arr[i]
          ```
          , remove 
          ```
          arr[i-k]
          ```
          ).
          
      41.   A possível maior soma terminando em 
          ```
          i
          ```
           com _pelo menos_ 
          ```
          k
          ```
           elementos é a "soma da janela atual de tamanho K" MAIS a "maior soma do prefixo que terminou imediatamente antes dessa janela", SE essa soma de prefixo for positiva.
          
      51.   Portanto: 
          ```
          candidato = soma_janela_K + max(0, max_soma[i-k])
          ```
          .
          
      57.   Atualize a 
          ```
          resposta
          ```
           se o 
          ```
          candidato
          ```
           for maior.
-   **Complexidade:** Tempo O(N) (duas passadas independentes), Espaço O(N) para armazenar o array do Kadane.

### 18\. Contar elementos distintos em cada janela de tamanho K

**Descrição:** Dado um array de inteiros e um valor de janela fixo 
```
k
```
, imprima em um array ou lista o número de elementos únicos (distintos) presentes em cada janela de tamanho 
```
k
```
. **Input / Output Exemplo:**

-   **Input:** 
    ```
    arr = [1, 2, 1, 3, 4, 2, 3]
    ```
    , 
    ```
    k = 4
    ```
    
-   **Output:** 
    ```
    [3, 4, 4, 3]
    ```
     (Na primeira janela \[1,2,1,3\], temos os únicos 1, 2, 3 = total 3).

**Passo a passo lógico detalhado:**

1.  **Setup Inicial:** Use um HashMap para contar as frequências. Adicione os primeiros 
    ```
    k
    ```
     elementos no mapa.
    
2.  **Primeiro Registro:** A quantidade de elementos distintos na primeira janela é simplesmente o número de chaves no mapa (ou tamanho do mapa). Guarde isso no resultado.
    
3.  **Deslizamento e Gestão:** Ao mover a janela um passo:
    
      11.   Diminua a frequência do elemento que "saiu" (índice 
          ```
          i-k
          ```
          ). Se a frequência cair para 0, **remova** a chave do mapa.
          
      17.   Adicione/incremente o elemento que "entrou" (índice 
          ```
          i
          ```
          ).
          
      23.   O número de distintos na nova janela é novamente o tamanho do mapa.
-   **Complexidade:** Tempo O(N), Espaço O(K).

### 19\. Subarray com soma dada

**Descrição:** Encontre os índices inicial e final (inclusive) de uma subarray contínua que tenha a soma exata igual a um valor fornecido. Para facilitar, neste cenário considere que o array contém apenas números **inteiros não-negativos**. Se houver múltiplas respostas, retorne a primeira encontrada. **Input / Output Exemplo:**

-   **Input:** 
    ```
    arr = [1, 4, 20, 3, 10, 5]
    ```
    , 
    ```
    soma = 33
    ```
    
-   **Output:** 
    ```
    Índices 2 a 4
    ```
     (Referente a 
    ```
    [20, 3, 10]
    ```
    )

**Passo a passo lógico detalhado:**

1.  **Dois Ponteiros Dinâmicos:** 
    ```
    inicio = 0
    ```
    , 
    ```
    fim = 0
    ```
    , 
    ```
    soma_atual = arr[0]
    ```
    .
    
2.  **Avanço Cauteloso:** Use um loop onde o 
    ```
    fim
    ```
     vai até o tamanho final do array.
    
3.  **Encolhimento:** _Antes_ de testar a igualdade e expandir, use um loop 
    ```
    while
    ```
    : se a 
    ```
    soma_atual > soma_desejada
    ```
     e 
    ```
    inicio < fim
    ```
    , subtraia 
    ```
    arr[inicio]
    ```
     da 
    ```
    soma_atual
    ```
     e incremente 
    ```
    inicio
    ```
    .
    
4.  **Acerto Exato:** Se a 
    ```
    soma_atual == soma_desejada
    ```
    , retorne o par 
    ```
    [inicio, fim]
    ```
    .
    
5.  **Expansão:** Se ainda for menor, incremente 
    ```
    fim
    ```
     (não passe dos limites) e adicione o novo 
    ```
    arr[fim]
    ```
     à 
    ```
    soma_atual
    ```
    .
-   **Complexidade:** Tempo O(N), Espaço O(1). _(Nota: Se existissem números negativos, essa lógica falharia e você precisaria da técnica do exercício 14)._

### 20\. Primeiro inteiro negativo em cada janela de tamanho k

**Descrição:** Dado um array e um inteiro de tamanho de janela 
```
k
```
, encontre o primeiro elemento que seja um número negativo para cada uma das janelas. Se uma janela não tiver nenhum número negativo, registre 
```
0
```
. **Input / Output Exemplo:**

-   **Input:** 
    ```
    arr = [-8, 2, 3, -6, 10]
    ```
    , 
    ```
    k = 2
    ```
    
-   **Output:** 
    ```
    [-8, 0, -6, -6]
    ```

**Passo a passo lógico detalhado:**

1.  **Estrutura de Fila (Queue / Deque):** Use uma fila dupla ou simples para armazenar os _índices_ dos elementos negativos (nunca os valores diretamente, para saber quando eles expiram da janela).
    
2.  **Preenchimento Inicial:** Varra os primeiros 
    ```
    k
    ```
     elementos. Se 
    ```
    arr[i] < 0
    ```
    , coloque 
    ```
    i
    ```
     no fim da fila.
    
3.  **Primeira Resposta:** A resposta para a primeira janela será o valor apontado pelo índice no topo (início) da fila. Se a fila estiver vazia, a resposta é 0.
    
4.  **Deslizamento:** Para o restante do array:
    
      21.   Verifique se o índice no início da fila é menor ou igual a 
          ```
          i - k
          ```
           (ou seja, ele ficou para trás e não pertence mais à janela atual). Se sim, remova-o do início.
          
      27.   Se o novo elemento (
          ```
          arr[i]
          ```
          ) for negativo, coloque seu índice no fim da fila.
          
      33.   Colete a resposta para a janela atual olhando o início da fila.
-   **Complexidade:** Tempo O(N), Espaço O(K) no pior caso.

### 21\. Menor janela que contém todos os caracteres da própria string

**Descrição:** Dada uma string complexa, extraia a menor substring contígua que consiga abranger todos os caracteres únicos que existem espalhados por toda a string. **Input / Output Exemplo:**

-   **Input:** 
    ```
    S = "aabcbcdbca"
    ```
    
-   **Output:** 
    ```
    "dbca"
    ```
     (Tamanho 4, contém a, b, c, d)

**Passo a passo lógico detalhado:**

1.  **Identificando o Objetivo:** Primeiro, crie um Set com todos os caracteres da string original para descobrir quantos caracteres únicos totais existem. Deixe este valor em 
    ```
    num_unicos_total
    ```
    .
    
2.  **Controle Dinâmico:** Use ponteiros 
    ```
    esq
    ```
     e 
    ```
    dir
    ```
     iniciando em 0, e um mapa 
    ```
    freq_janela
    ```
     para contar o que está na janela.
    
3.  **Expansão:** Avance 
    ```
    dir
    ```
    , adicionando letras ao 
    ```
    freq_janela
    ```
    .
    
4.  **Validação e Encolhimento:** Quando o tamanho de 
    ```
    freq_janela
    ```
     (número de chaves) atingir 
    ```
    num_unicos_total
    ```
    , significa que você tem todos eles. Agora, tente otimizar: em um loop 
    ```
    while
    ```
    , atualize sua 
    ```
    menor_janela_vista
    ```
    . Então, decremente a frequência de 
    ```
    S[esq]
    ```
    . Se cair para 0, remova do mapa. Incremente 
    ```
    esq
    ```
    . O loop termina porque a chave sumiu e a janela voltou a ser inválida.
    
5.  **Continuar:** Expanda 
    ```
    dir
    ```
     novamente até achar outra janela válida.
-   **Complexidade:** Tempo O(N), Espaço O(min(N,M)).

### 22\. Menor janela em uma string contendo todos os caracteres de outra string

**Descrição:** Dadas duas strings, um Texto 
```
S
```
 e um Padrão 
```
P
```
, encontre a menor janela/substring no texto 
```
S
```
 que possua _todos_ os caracteres de 
```
P
```
, incluindo a quantidade apropriada de repetições. **Input / Output Exemplo:**

-   **Input:** 
    ```
    S = "timetopractice"
    ```
    , 
    ```
    P = "toc"
    ```
    
-   **Output:** 
    ```
    "toprac"
    ```
     (Tamanho 6)

**Passo a passo lógico detalhado:**

1.  **Frequência do Padrão:** Crie um mapa de frequência 
    ```
    mapa_p
    ```
     contendo quantos caracteres cada letra tem no padrão 
    ```
    P
    ```
    .
    
2.  **Controles:** Variável 
    ```
    matches = 0
    ```
     (quantos caracteres da janela já satisfazem a demanda de 
    ```
    mapa_p
    ```
    ).
    
3.  **Navegação (Expansão):** Varra 
    ```
    S
    ```
     com o ponteiro 
    ```
    direita
    ```
    . Para a letra atual 
    ```
    char_dir
    ```
    , diminua a contagem dela no 
    ```
    mapa_p
    ```
    . Se a contagem (após a redução) ainda for 
    ```
    >= 0
    ```
    , significa que era uma letra útil. Incremente 
    ```
    matches
    ```
    .
    
4.  **Atingiu a Condição:** Se 
    ```
    matches == tamanho_de_P
    ```
    , você encontrou uma janela válida.
    
5.  **Otimização (Encolhimento):** Tente encolher da 
    ```
    esquerda
    ```
     enquanto 
    ```
    matches == tamanho_de_P
    ```
    . Salve o tamanho mínimo. Restaure a letra que está saindo (
    ```
    S[esq]
    ```
    ): incremente sua contagem no 
    ```
    mapa_p
    ```
    . Se a contagem subir para 
    ```
    > 0
    ```
    , você perdeu uma letra crítica, então 
    ```
    matches--
    ```
    . Avance 
    ```
    esquerda
    ```
    .
-   **Complexidade:** Tempo O(N), Espaço O(1) (tamanho do alfabeto).

### 23\. Subarrays equivalentes

**Descrição:** Em um array de inteiros, um "subarray equivalente" é definido como um subarray que possui exatamente a mesma quantidade de elementos distintos únicos que o array original completo. Encontre o número total de subarrays que satisfazem essa condição. **Input / Output Exemplo:**

-   **Input:** 
    ```
    arr = [2, 1, 3, 2, 3]
    ```
    
-   **Output:** 
    ```
    5
    ```
     (Subarrays: 
    ```
    [2,1,3]
    ```
    , 
    ```
    [1,3,2]
    ```
    , 
    ```
    [3,2,3]
    ```
    , 
    ```
    [2,1,3,2]
    ```
    , 
    ```
    [1,3,2,3]
    ```
    , o array todo 
    ```
    [2,1,3,2,3]
    ```
    )

**Passo a passo lógico detalhado:**

1.  **Definindo o Alvo:** Crie um HashSet do array completo. O 
    ```
    alvo_distintos
    ```
     é o tamanho deste HashSet.
    
2.  **Janela e Mapa:** Inicie ponteiros 
    ```
    esq
    ```
     e 
    ```
    dir
    ```
    , e um mapa de frequência para a janela.
    
3.  **Expansão e Aritmética Mágica:** Expanda da 
    ```
    direita
    ```
    . Quando o mapa tiver exatamente 
    ```
    alvo_distintos
    ```
     chaves, isso significa que a janela 
    ```
    arr[esq...dir]
    ```
     é válida.
    
4.  **O Grande Pulo:** Se a janela 
    ```
    [esq...dir]
    ```
     é válida, adivinhe o que mais é válido? Adicionar qualquer elemento à direita dela mantém todos os originais! Ou seja, as subarrays 
    ```
    [esq...dir+1]
    ```
    , 
    ```
    [esq...dir+2]
    ```
     até o final do array também são válidas. Portanto, adicione à resposta final a quantidade de elementos restantes: 
    ```
    (Tamanho_do_Array - dir)
    ```
    .
    
5.  **Encolhimento:** Agora, encolha da 
    ```
    esquerda
    ```
     (removendo a frequência e possivelmente a chave do mapa) e veja se a janela ainda tem 
    ```
    alvo_distintos
    ```
    . Se tiver, some o restante novamente. Repita até a janela quebrar, então volte a expandir a 
    ```
    direita
    ```
    .
-   **Complexidade:** Tempo O(N), Espaço O(N).

## 🔴 Nível: Difícil

Os problemas difíceis de Janela Flutuante frequentemente exigem a mistura de múltiplas técnicas (como pilhas monotônicas, mapas sofisticados, ou janelas duplas atípicas). A compreensão cristalina dos níveis anteriores é imperativa aqui.

### 24\. Máximo dos mínimos para cada tamanho de janela

**Descrição:** Dado um array numérico, para cada tamanho de janela possível (de K\=1 até K\=N), primeiro determine qual é o elemento mínimo dentro de cada janela desse tamanho. Após isso, selecione o valor máximo entre todos esses mínimos encontrados. Retorne uma lista de tamanho N com esses valores máximos em ordem de tamanho de janela. **Input / Output Exemplo:**

-   **Input:** 
    ```
    arr = [10, 20, 30, 50, 10, 70, 30]
    ```
    
-   **Output:** 
    ```
    [70, 30, 20, 10, 10, 10, 10]
    ```

**Passo a passo lógico detalhado:** _(Nota: Embora este problema aborde "janelas", a solução linear ideal usa Pilhas Monotônicas para calcular a contribuição de cada elemento, não deslizamento tradicional)._

1.  **Determinação de Domínio:** Para cada elemento 
    ```
    arr[i]
    ```
    , precisamos saber até onde ele se estende como o "menor valor absoluto" de um intervalo.
    
2.  **Limites (Next e Previous Smaller):** Use uma Pilha Monotônica para encontrar o índice do _Próximo Menor_ e _Anterior Menor_ para cada índice 
    ```
    i
    ```
    .
    
3.  **Tamanho do Domínio:** O elemento 
    ```
    arr[i]
    ```
     será o mínimo garantido para qualquer janela cujo tamanho seja até 
    ```
    Comprimento = (ProximoMenor[i] - AnteriorMenor[i] - 1)
    ```
    .
    
4.  **Preenchimento Inicial:** Crie um array de resultados 
    ```
    ans
    ```
    . Atualize o valor: 
    ```
    ans[Comprimento] = max(ans[Comprimento], arr[i])
    ```
    .
    
5.  **Propagação Inversa:** Pode haver buracos no array 
    ```
    ans
    ```
    . Faça um loop reverso do tamanho máximo até 1. Se 
    ```
    arr[i]
    ```
     foi o máximo dos mínimos em uma janela de tamanho 5, ele fatalmente será um forte candidato para uma janela de tamanho 4. A lógica dita: 
    ```
    ans[i] = max(ans[i], ans[i+1])
    ```
    .
-   **Complexidade:** Tempo O(N) usando pilhas e propagação linear, Espaço O(N).

### 25\. Maior substring com K elementos únicos

**Descrição:** Este problema é uma variação restrita e invertida do Nível Médio. Encontre a maior substring contígua de uma string desde que essa substring não exceda o limite de 
```
k
```
 caracteres distintos em sua composição. **Input / Output Exemplo:**

-   **Input:** 
    ```
    S = "aabacbebebe"
    ```
    , 
    ```
    k = 3
    ```
    
-   **Output:** 
    ```
    7
    ```
     (A substring "cbebebe" tem tamanho 7 e apenas 3 caracteres distintos: c, b, e)

**Passo a passo lógico detalhado:**

1.  **Dinâmica Clássica Expand-Shrink:** Configure um HashMap e dois ponteiros.
    
2.  **Processamento:** Avance o ponteiro da 
    ```
    direita
    ```
    , adicionando caracteres ao mapa.
    
3.  **Verificação Limite:** A restrição é 
    ```
    tamanho_mapa <= k
    ```
    . Se o tamanho do mapa atingir 
    ```
    k + 1
    ```
    , a janela ficou ilegal.
    
4.  **Correção pela Esquerda:** Inicie o loop 
    ```
    while
    ```
    . Decremente a frequência de 
    ```
    S[esquerda]
    ```
    . Se a frequência atingir zero, a chave é deletada do mapa, trazendo o tamanho do mapa de volta para 
    ```
    k
    ```
     (janela legalizada novamente). Incremente 
    ```
    esquerda
    ```
    .
    
5.  **Registro Constante:** Sempre que a janela for legal (tamanho do mapa ≤ k), compare e salve 
    ```
    tamanho_maximo = max(tamanho_maximo, direita - esquerda + 1)
    ```
    .
-   **Complexidade:** Tempo O(N), Espaço O(K).

### 26\. Menor substring em janela (Hardcore Matching)

**Descrição:** Semelhante ao exercício 22, mas estruturado com casos de teste maciços e caracteres variados (maiúsculas, minúsculas, símbolos). Exige a identificação da menor string em 
```
S
```
 que faça "match" exato (incluindo volume de letras) do padrão 
```
P
```
. **Input / Output Exemplo:**

-   **Input:** 
    ```
    S = "zoomlazapzo"
    ```
    , 
    ```
    P = "oza"
    ```
    
-   **Output:** 
    ```
    "apzo"
    ```

**Passo a passo lógico detalhado:** _Dica: Fazer cópias de mapas dentro de loops em problemas Hard causa Time Limit Exceeded (TLE). A eficiência máxima é requerida._

1.  **Mapeamento de Requisitos:** Preencha um array inteiro de tamanho 256 (tabela ASCII completa) para atuar como 
    ```
    hash_pat
    ```
    . Guarde também quantos caracteres únicos tem o padrão em 
    ```
    count_necessario
    ```
    .
    
2.  **Mapeamento da Janela:** Use um 
    ```
    hash_str
    ```
     paralelo para ir registrando as letras de 
    ```
    S
    ```
     à medida que a janela avança.
    
3.  **Variável de Controle O(1):** Mantenha um contador 
    ```
    letras_encontradas
    ```
    . Quando você encontrar em 
    ```
    S
    ```
     uma letra que existe em 
    ```
    P
    ```
    , incremente em 
    ```
    hash_str
    ```
    . **SE**, após incrementar, 
    ```
    hash_str[char] <= hash_pat[char]
    ```
    , significa que essa letra foi útil. Incremente 
    ```
    letras_encontradas
    ```
    .
    
4.  **Minimização Agressiva:** Se 
    ```
    letras_encontradas == tamanho(P)
    ```
    , inicie o encolhimento. Verifique o elemento na extremidade esquerda. Se ele for "inútil" (não pertence a P) OU se temos sobras dele na janela atual (
    ```
    hash_str[char] > hash_pat[char]
    ```
    ), nós o descartamos decrementando a contagem e subindo a 
    ```
    esquerda
    ```
    .
    
5.  **Captura Fina:** A cada vez que não der mais para encolher, cheque o tamanho atual. Se for o menor visto, guarde o ponteiro 
    ```
    inicio_absoluto
    ```
     e o 
    ```
    tamanho_minimo
    ```
    . Ao final do algoritmo principal, use 
    ```
    substring(inicio_absoluto, tamanho_minimo)
    ```
    .
-   **Complexidade:** Tempo O(N), Espaço O(1) (Array estático 256).

### 27\. Maior subarray com soma e pelo menos k números

**Descrição:** Uma extensão diabólica do problema clássico de subarrays limitadas. Você deve encontrar uma subarray contígua com **pelo menos** 
```
K
```
 números de comprimento e que gere a **soma aritmética máxima** possível. **Input / Output Exemplo:**

-   **Input:** 
    ```
    arr = [2, 3, 1, -7, 6, -5, -4, 4, 3, 3, 2, -9, -5, 6, 1, 2, 1, 1], k = 4
    ```
    
-   **Output:** 
    ```
    15
    ```

**Passo a passo lógico detalhado:**

1.  **O Desafio dos Negativos:** Como não há garantia de positividade, uma janela não cresce monotonamente. A sacada é uma variante de "Janela Deslizante Retardada" baseada na soma de prefixos.
    
2.  **Criação do Prefixo:** Calcule um array de prefixos simples onde 
    ```
    prefix[i]
    ```
     soma de 0 até 
    ```
    i
    ```
    .
    
3.  **Base do Algoritmo:** Para qualquer índice 
    ```
    i
    ```
    , a soma da subarray entre o índice 
    ```
    j
    ```
     (onde j≤i−k) e 
    ```
    i
    ```
     é 
    ```
    prefix[i] - prefix[j]
    ```
    .
    
4.  **Maximização:** Para maximizar 
    ```
    prefix[i] - prefix[j]
    ```
    , você precisa do **menor** 
    ```
    prefix[j]
    ```
     possível.
    
5.  **A Janela Fantasma:** Mantenha uma variável 
    ```
    menor_prefix_distante
    ```
    . Conforme seu loop avança de 
    ```
    i = k
    ```
     até o final do array, seu ponteiro atrasado "j" é igual a 
    ```
    i - k
    ```
    .
    
6.  **Atualização Dinâmica:** A cada passo, atualize 
    ```
    menor_prefix_distante = min(menor_prefix_distante, prefix[i - k])
    ```
    . Então, a melhor soma possível terminando exatamente no índice 
    ```
    i
    ```
     e com tamanho ≥ 
    ```
    k
    ```
     é o 
    ```
    prefix[i] - menor_prefix_distante
    ```
    . Guarde o valor máximo visto.
-   **Complexidade:** Tempo O(N) varredura simples, Espaço O(N) (que pode ser otimizado para O(1) se a soma for controlada sem array paralelo completo).

## Dicas Finais para Implementação e Estudos

Para transcrever a lógica do padrão **Janela Flutuante (Sliding Window)** para código de forma eficaz, observe o esqueleto abaixo que responde a mais de 80% dos problemas dinâmicos:

```
// Esqueleto Lógico Pseudo-Código

inicializar_esquerda = 0
inicializar_direita = 0
estrutura_de_controle = Novo Mapa() / Variáveis
melhor_resultado = infinito (ou 0)

enquanto direita < tamanho_do_array:
    // 1. Inserir o elemento da "direita" na estrutura da janela
    adicionar_elemento(estrutura_de_controle, array[direita])
    
    // 2. Verificar se a janela violou as regras
    enquanto a janela é INVÁLIDA (ex: soma estourou limite):
        // a. Remover o elemento da "esquerda" da estrutura
        remover_elemento(estrutura_de_controle, array[esquerda])
        // b. Encolher a janela
        esquerda++
    
    // 3. Atualizar a resposta, porque a janela agora está limpa e válida
    melhor_resultado = calcular_melhor(melhor_resultado, tamanho/valor da janela)
    
    // 4. Expandir para o próximo ciclo
    direita++

retornar melhor_resultado
  

```

Siga praticando primeiramente entendendo a parte matemática de como a janela desliza, evitando pular diretamente para a escrita do código. Bons estudos e excelente evolução algorítmica!