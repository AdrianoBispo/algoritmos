# Lista de Exercícios

Este documento contém uma lista progressiva e detalhada de problemas focada na técnica de **Dois Ponteiros (Two Pointers)**.

O objetivo deste material é desenvolver a sua lógica de programação. Compreenda o passo a passo algorítmico e as implicações de cada decisão antes de ir para o código. Você pode resolver esses problemas utilizando a linguagem de sua preferência (C, C++, Java, Python, Javascript, Go, etc.).

<details>
  <summary>Nível: Fácil (Easy Problems)</summary>

<p>


### 1\. [Remover Ocorrências](https://www.geeksforgeeks.org/dsa/remove-element/ "null")

**Descrição:** Dado um array e um valor específico (alvo), remova todas as ocorrências desse valor _in-place_ (modificando o próprio array na memória original) e retorne o novo tamanho válido do array. Não é permitido alocar um novo array. **Por que usar dois ponteiros?** Um loop simples tentaria deletar o elemento e arrastar todos os outros para a esquerda (muito custoso, O(N2)). Com dois ponteiros, fazemos isso em uma única passada. **Passo a passo lógico:**

1.  Inicialize um ponteiro 
    ```
    escritor
    ```
     no índice 0. Ele indicará onde o próximo elemento válido deve ser salvo.
    
2.  Utilize um ponteiro 
    ```
    leitor
    ```
     para iterar linearmente por todos os elementos do array (do índice 0 ao 
    ```
    N-1
    ```
    ).
    
3.  Se o elemento no ponteiro 
    ```
    leitor
    ```
     for **diferente** do valor alvo, ele é um valor válido. Copie este elemento para a posição atual do ponteiro 
    ```
    escritor
    ```
    .
    
4.  Incremente o ponteiro 
    ```
    escritor
    ```
    . Se for igual ao alvo, apenas ignore e avance o 
    ```
    leitor
    ```
    .
    
5.  Ao final, o valor numérico do 
    ```
    escritor
    ```
     representará o novo tamanho lógico do array. **Complexidade:** Tempo O(N) | Espaço O(1). **Exemplos:**
-   **Input Padrão:** 
    ```
    array = [3, 2, 2, 3]
    ```
    , 
    ```
    alvo = 3
    ```
    
-   **Output Padrão:** 
    ```
    novo_tamanho = 2
    ```
     (O array físico será 
    ```
    [2, 2, _, _]
    ```
    )
    
-   **Edge Case (Todos iguais ao alvo):** 
    ```
    array = [4, 4, 4]
    ```
    , 
    ```
    alvo = 4
    ```
     → 
    ```
    novo_tamanho = 0
    ```
    .

### 2\. [Mover Zeros para o Final](https://www.geeksforgeeks.org/dsa/move-zeroes-end-array/ "null")

**Descrição:** Mova todos os zeros de um array para o final da estrutura, garantindo estritamente que a ordem relativa dos elementos não nulos seja mantida. **Passo a passo lógico:**

1.  Inicialize um ponteiro 
    ```
    posicao_nao_zero
    ```
     em 0. Este ponteiro demarca o limite dos elementos válidos (não-zeros).
    
2.  Use um ponteiro 
    ```
    atual
    ```
     para percorrer o array do início ao fim.
    
3.  Sempre que o elemento apontado por 
    ```
    atual
    ```
     for **diferente de zero**, realize uma troca (swap) entre 
    ```
    array[atual]
    ```
     e 
    ```
    array[posicao_nao_zero]
    ```
    .
    
4.  Após a troca, incremente o ponteiro 
    ```
    posicao_nao_zero
    ```
     em 1.
    
5.  Se 
    ```
    atual
    ```
     apontar para zero, apenas avance-o. Os zeros naturalmente empurrados para trás. **Complexidade:** Tempo O(N) | Espaço O(1). **Exemplos:**
-   **Input Padrão:** 
    ```
    array = [0, 1, 0, 3, 12]
    ```
    
-   **Output Padrão:** 
    ```
    [1, 3, 12, 0, 0]
    ```
    
-   **Edge Case (Sem zeros):** 
    ```
    array = [1, 2, 3]
    ```
     → 
    ```
    [1, 2, 3]
    ```
     (faz swaps de um elemento com ele mesmo, operação segura).

### 3\. [Elementos Únicos em Array Ordenado](https://www.geeksforgeeks.org/dsa/remove-duplicates-sorted-array/ "null")

**Descrição:** Dado um array previamente ordenado, remova os elementos duplicados _in-place_ para que cada elemento apareça estritamente uma única vez e retorne o novo tamanho. **Por que a ordenação importa?** Como o array está ordenado, elementos duplicados estarão sempre adjacentes (lado a lado), permitindo a detecção imediata. **Passo a passo lógico:**

1.  Validação de segurança: Se o tamanho do array for 0 ou 1, retorne o próprio tamanho (não há o que duplicar).
    
2.  Inicialize um ponteiro 
    ```
    unico
    ```
     no índice 0. Ele guarda o último elemento único confirmado.
    
3.  Use um ponteiro 
    ```
    explorador
    ```
     iniciando do índice 1 até o final.
    
4.  Se 
    ```
    array[explorador] != array[unico]
    ```
    , encontramos um número novo! Incremente o 
    ```
    unico
    ```
     em 1 e, em seguida, sobrescreva 
    ```
    array[unico]
    ```
     com 
    ```
    array[explorador]
    ```
    .
    
5.  Retorne 
    ```
    unico + 1
    ```
     (pois o índice é zero-based, o tamanho é o índice + 1). **Complexidade:** Tempo O(N) | Espaço O(1). **Exemplos:**
-   **Input:** 
    ```
    array = [1, 1, 2, 2, 3]
    ```
    
-   **Output:** 
    ```
    novo_tamanho = 3
    ```
     (Array lógico final: 
    ```
    [1, 2, 3, _, _]
    ```
    )

### 4\. [Inverter String Preservando a Posição dos Espaços](https://www.geeksforgeeks.org/dsa/reverse-string-preserving-space-positions/ "null")

**Descrição:** Inverta os caracteres alfanuméricos de uma string, mas bloqueie os espaços em branco em suas posições indexadas originais. **Passo a passo lógico:**

1.  Converta a string em um array de caracteres (caso a linguagem exija, já que strings em Java/Python são imutáveis).
    
2.  Inicialize dois ponteiros opostos: 
    ```
    inicio = 0
    ```
     e 
    ```
    fim = tamanho_da_string - 1
    ```
    .
    
3.  Crie um loop que continue enquanto 
    ```
    inicio < fim
    ```
    :
    
      19.   Se o 
          ```
          array[inicio]
          ```
           for um espaço (' '), ele deve ficar onde está. Apenas faça 
          ```
          inicio++
          ```
          .
          
      29.   Se o 
          ```
          array[fim]
          ```
           for um espaço (' '), ele também deve ser ignorado. Faça 
          ```
          fim--
          ```
          .
          
      39.   Se **ambos** não forem espaços, aplique a inversão: troque (swap) 
          ```
          array[inicio]
          ```
           por 
          ```
          array[fim]
          ```
          . Após a troca, mova ambos simultaneamente: 
          ```
          inicio++
          ```
           e 
          ```
          fim--
          ```
          . **Complexidade:** Tempo O(N) | Espaço O(N) para o array de caracteres. **Exemplos:**
-   **Input:** 
    ```
    "abc de"
    ```
    
-   **Output:** 
    ```
    "edc ba"
    ```
    
-   **Edge Case (Múltiplos espaços):** 
    ```
    "a b c"
    ```
     → 
    ```
    "c b a"
    ```

### 5\. [Ordenar um Array de 0s, 1s e 2s](https://www.geeksforgeeks.org/dsa/sort-an-array-of-0s-1s-and-2s/ "null")

**Descrição:** Ordene um array contendo estritamente os inteiros 0, 1 e 2, fazendo isso em uma única iteração sem usar funções de ordenação. **Contexto:** Este é o famoso problema da "Bandeira Nacional Holandesa" (Dutch National Flag) criado por Edsger Dijkstra. **Passo a passo lógico (Três Ponteiros):**

1.  Defina três marcadores: 
    ```
    baixo = 0
    ```
     (limite dos 0s), 
    ```
    medio = 0
    ```
     (o iterador atual), e 
    ```
    alto = n - 1
    ```
     (limite dos 2s).
    
2.  O loop roda enquanto 
    ```
    medio <= alto
    ```
     (quando eles se cruzam, tudo está ordenado).
    
      21.   **Caso 0 (
          ```
          array[medio] == 0
          ```
          ):** O zero pertence ao início. Troque 
          ```
          array[medio]
          ```
           com 
          ```
          array[baixo]
          ```
          . Como ambos agora estão em posições corretas, incremente 
          ```
          baixo++
          ```
           e 
          ```
          medio++
          ```
          .
          
      43.   **Caso 1 (
          ```
          array[medio] == 1
          ```
          ):** O um já está no meio, onde pertence. Apenas avance o iterador 
          ```
          medio++
          ```
          .
          
      53.   **Caso 2 (
          ```
          array[medio] == 2
          ```
          ):** O dois pertence ao final. Troque 
          ```
          array[medio]
          ```
           com 
          ```
          array[alto]
          ```
          . Decremente 
          ```
          alto--
          ```
          . **Importante:** Não incremente o 
          ```
          medio
          ```
           aqui, pois o número que veio do final precisa ser avaliado na próxima iteração! **Complexidade:** Tempo O(N) | Espaço O(1). **Exemplo:**
-   **Input:** 
    ```
    array = [2, 0, 2, 1, 1, 0]
    ```
    
-   **Output:** 
    ```
    [0, 0, 1, 1, 2, 2]
    ```

### 6\. [Soma de Dois (Two Sum)](https://www.geeksforgeeks.org/dsa/check-if-pair-with-given-sum-exists-in-array/ "null")

**Descrição:** Verifique se existe um par de elementos distintos em um array cuja soma seja exatamente igual a um valor alvo 
```
X
```
. **Estratégia:** Se o array não for ordenado, ordene-o primeiro. A magia dos dois ponteiros opostos brilha em arrays ordenados. **Passo a passo lógico:**

1.  Após garantir que o array está ordenado, posicione 
    ```
    esq = 0
    ```
     e 
    ```
    dir = n - 1
    ```
    .
    
2.  Em um loop 
    ```
    while (esq < dir)
    ```
    , calcule a soma provisória: 
    ```
    soma = array[esq] + array[dir]
    ```
    .
    
3.  Verifique a condição matemática:
    
      23.   Se 
          ```
          soma == X
          ```
          , bingo! Retorne Verdadeiro (ou os índices/valores).
          
      29.   Se 
          ```
          soma < X
          ```
          , precisamos de um valor total maior. A única forma de aumentar a soma em um array ordenado é avançar o ponteiro menor para a direita: 
          ```
          esq++
          ```
          .
          
      39.   Se 
          ```
          soma > X
          ```
          , precisamos diminuir o valor total. Retraia o ponteiro maior para a esquerda: 
          ```
          dir--
          ```
          .
    
4.  Se o loop terminar e os ponteiros se cruzarem sem encontrar a soma, retorne Falso. **Complexidade:** Tempo O(NlogN) para ordenar + O(N) para a busca = O(NlogN) total. Espaço O(1). **Exemplo:**
-   **Input:** 
    ```
    array = [1, 2, 4, 5, 7, 11]
    ```
    , 
    ```
    X = 9
    ```
    
-   **Output:** 
    ```
    Verdadeiro
    ```
     (pois 2 + 7 = 9)

### 7\. [Soma de Par em Array Ordenado e Rotacionado](https://www.geeksforgeeks.org/dsa/given-a-sorted-and-rotated-array-find-if-there-is-a-pair-with-a-given-sum/ "null")

**Descrição:** Encontre se existe um par com uma soma específica em um array que foi ordenado de forma ascendente e, em seguida, rotacionado em um pivô desconhecido (ex: 
```
[11, 15, 6, 8, 9, 10]
```
). **Passo a passo lógico:**

1.  O primeiro desafio é encontrar o ponto de quebra (pivô), ou seja, o índice 
    ```
    i
    ```
     onde 
    ```
    array[i] > array[i+1]
    ```
    . Isso marca onde os maiores elementos terminam e os menores começam.
    
2.  Defina 
    ```
    esq
    ```
     como o índice do menor elemento (
    ```
    pivô + 1
    ```
    ) e 
    ```
    dir
    ```
     como o índice do maior elemento (
    ```
    pivô
    ```
    ).
    
3.  Calcule a 
    ```
    soma = array[esq] + array[dir]
    ```
    .
    
4.  Use aritmética modular para simular o comportamento circular do array:
    
      37.   Se 
          ```
          soma == alvo
          ```
          , retorne Verdadeiro.
          
      43.   Se 
          ```
          soma < alvo
          ```
          , precisamos aumentar. Avance o ponteiro esquerdo circularmente: 
          ```
          esq = (esq + 1) % n
          ```
          . (Ex: se ele estava no último índice, ele volta pro índice 0).
          
      53.   Se 
          ```
          soma > alvo
          ```
          , precisamos diminuir. Recue o direito circularmente: 
          ```
          dir = (dir - 1 + n) % n
          ```
          .
    
5.  Continue até que a busca cubra todos os elementos, limitando os passos ao tamanho do array 
    ```
    n
    ```
    . **Complexidade:** Tempo O(N) para achar o pivô e iterar. Espaço O(1). **Exemplo:**
-   **Input:** 
    ```
    array = [11, 15, 26, 38, 9, 10]
    ```
    , 
    ```
    alvo = 35
    ```
    
-   **Output:** 
    ```
    Verdadeiro
    ```
     (26 + 9 = 35)

### 8\. [Soma de Par Mais Próxima](https://www.geeksforgeeks.org/dsa/2-sum-pair-sum-closest-to-target/ "null")

**Descrição:** Encontre o par de elementos em um array ordenado cuja soma absoluta seja a mais próxima possível de um valor alvo 
```
X
```
. **Passo a passo lógico:**

1.  Inicialize 
    ```
    esq = 0
    ```
     e 
    ```
    dir = n - 1
    ```
    .
    
2.  Crie variáveis rastreadoras: 
    ```
    menor_diferenca = infinito
    ```
    , e 
    ```
    melhor_esq
    ```
    , 
    ```
    melhor_dir
    ```
     para armazenar os valores finais.
    
3.  Calcule a soma atual: 
    ```
    soma_atual = array[esq] + array[dir]
    ```
    .
    
4.  Calcule a diferença absoluta da soma atual para o alvo: 
    ```
    diff = valor_absoluto(X - soma_atual)
    ```
    .
    
5.  Se 
    ```
    diff < menor_diferenca
    ```
    , atualize a 
    ```
    menor_diferenca
    ```
     e salve os elementos atuais.
    
6.  Direcione os ponteiros:
    
      49.   Se 
          ```
          soma_atual < X
          ```
          , incremente 
          ```
          esq
          ```
           (tenta aproximar subindo a soma).
          
      59.   Se 
          ```
          soma_atual > X
          ```
          , decremente 
          ```
          dir
          ```
           (tenta aproximar descendo a soma).
          
      69.   Se 
          ```
          soma_atual == X
          ```
          , você achou a diferença 0, pode parar imediatamente. **Complexidade:** Tempo O(N) | Espaço O(1). **Exemplo:**
-   **Input:** 
    ```
    array = [10, 22, 28, 29, 30, 40]
    ```
    , 
    ```
    X = 54
    ```
    
-   **Output:** 
    ```
    [22, 30]
    ```
     (Soma = 52, Diferença = 2. A opção
    
    10,40
    
    dá 50, com diferença 4).

### 9\. [Par Mais Próximo de Dois Arrays Ordenados](https://www.geeksforgeeks.org/dsa/given-two-sorted-arrays-number-x-find-pair-whose-sum-closest-x/ "null")

**Descrição:** Variação do problema anterior. Dados dois arrays ordenados distintos e um número 
```
X
```
, encontre um elemento do array 1 e outro do array 2 cuja soma seja a mais próxima de 
```
X
```
. **Passo a passo lógico:**

1.  Como temos arrays diferentes, usaremos ponteiros opostos, mas iniciando em arrays distintos. Inicialize 
    ```
    p1 = 0
    ```
     (menor valor possível no array 1) e 
    ```
    p2 = m - 1
    ```
     (maior valor possível no array 2).
    
2.  Avalie a soma 
    ```
    soma = array1[p1] + array2[p2]
    ```
    .
    
3.  Verifique a diferença absoluta com 
    ```
    X
    ```
     
    ```
    |X - soma|
    ```
     e atualize sua variável de rastreamento de menor diferença se necessário.
    
4.  Lógica de movimento:
    
      29.   Se a soma for menor que 
          ```
          X
          ```
          , precisamos de um valor maior. Como 
          ```
          p2
          ```
           já está na metade dos "grandes" do array 2, nossa única opção é tentar um valor maior no array 1: incremente 
          ```
          p1++
          ```
          .
          
      43.   Se a soma for maior que 
          ```
          X
          ```
          , precisamos de um menor. Decremente 
          ```
          p2--
          ```
          . **Complexidade:** Tempo O(N+M) onde N e M são os tamanhos dos arrays | Espaço O(1). **Exemplo:**
-   **Input:** 
    ```
    arr1 = [1, 4, 5, 7]
    ```
    , 
    ```
    arr2 = [10, 20, 30, 40]
    ```
    , 
    ```
    X = 32
    ```
    
-   **Output:** 
    ```
    [1, 30]
    ```
     (Soma = 31, dif = 1).

### 10\. [Menor Subarray Maior que a Soma](https://www.geeksforgeeks.org/dsa/minimum-length-subarray-sum-greater-given-value/ "null")

**Descrição:** Encontre o comprimento do menor subarray contíguo (elementos vizinhos ininterruptos) cuja soma acumulada seja estritamente maior que um valor dado. **Estratégia (Janela Deslizante / Sliding Window):** Este é o caso de uso clássico onde os dois ponteiros formam uma janela que estica e encolhe. **Passo a passo lógico:**

1.  Inicialize dois ponteiros no início: 
    ```
    inicio = 0
    ```
    , 
    ```
    fim = 0
    ```
    . Crie 
    ```
    soma_atual = 0
    ```
     e 
    ```
    tamanho_minimo = infinito
    ```
    .
    
2.  Fase de Expansão: Enquanto 
    ```
    fim < n
    ```
    , vá adicionando 
    ```
    array[fim]
    ```
     à 
    ```
    soma_atual
    ```
     e incremente 
    ```
    fim++
    ```
    .
    
3.  Fase de Contração: Sempre que 
    ```
    soma_atual > valor_dado
    ```
    , entramos em um loop secundário interno 
    ```
    while
    ```
    :
    
      47.   Comparamos o tamanho da janela atual 
          ```
          (fim - inicio)
          ```
           com o 
          ```
          tamanho_minimo
          ```
           salvo e atualizamos se for menor.
          
      57.   Agora, tentamos ser otimistas e ver se podemos encolher a janela _ainda mais_ e continuar batendo o alvo. Subtraia 
          ```
          array[inicio]
          ```
           da 
          ```
          soma_atual
          ```
           e faça 
          ```
          inicio++
          ```
          .
    
4.  Repita a expansão e contração até o 
    ```
    fim
    ```
     percorrer todo o array. **Complexidade:** Tempo O(N) (cada elemento é visitado no máximo duas vezes) | Espaço O(1). **Exemplo:**
-   **Input:** 
    ```
    array = [1, 4, 45, 6, 0, 19]
    ```
    , 
    ```
    alvo = 51
    ```
    
-   **Output:** 
    ```
    3
    ```
     (O subarray 
    ```
    [4, 45, 6]
    ```
     soma 55. Apesar de tamanho 4 também ser válido, 3 é o mínimo).

### 11\. [Pares Dominantes](https://www.geeksforgeeks.org/dsa/find-the-number-of-dominant-pairs/ "null")

**Descrição:** Dado um array de tamanho par 
```
n
```
, encontre o número de pares 
```
(i, j)
```
 onde 
```
0 <= i < n/2
```
 (primeira metade), 
```
n/2 <= j < n
```
 (segunda metade), e cumpra a condição 
```
array[i] >= 5 * array[j]
```
. **Passo a passo lógico:**

1.  A chave aqui é tratar o array como duas metades independentes. Separe a primeira metade e a segunda metade e ordene-as individualmente (por exemplo, ambas em ordem decrescente).
    
2.  Por que ordenar? Se sabemos que 
    ```
    array[i]
    ```
     satisfaz a condição para um certo 
    ```
    array[j]
    ```
    , e a segunda metade está ordenada de forma decrescente, ele **obrigatoriamente** satisfará para todos os elementos menores após 
    ```
    j
    ```
    .
    
3.  Coloque um ponteiro 
    ```
    i = 0
    ```
     e 
    ```
    j = n/2
    ```
    .
    
4.  Avalie: Se 
    ```
    array[i] >= 5 * array[j]
    ```
    :
    
      33.   Como a metade 2 é decrescente, qualquer elemento após 
          ```
          j
          ```
           será ainda menor. Então, o elemento 
          ```
          i
          ```
           forma pares válidos com todo o resto da segunda metade!
          
      43.   Adicione 
          ```
          (n - j)
          ```
           ao seu contador total.
          
      49.   Como extraímos o máximo de 
          ```
          i
          ```
          , avance 
          ```
          i++
          ```
           para o próximo número da primeira metade.
    
5.  Se não cumprir a condição, precisamos de um 
    ```
    array[j]
    ```
     menor para satisfazer a equação, então avance 
    ```
    j++
    ```
    . **Complexidade:** Tempo O(NlogN) para a ordenação preliminar | Espaço O(1) ou dependente do algoritmo de sort. **Exemplo:**
-   **Input:** 
    ```
    array = [10, 8, 2, 1, 1, 2]
    ```
    
-   **Output:** 
    ```
    2
    ```
     (Pares válidos ocorrem entre as metades ordenadas. 10 domina 1 e 10 domina 2).

### 12\. [Palíndromo de Frase](https://www.geeksforgeeks.org/dsa/sentence-palindrome-palindrome-removing-spaces-dots-etc/ "null")

**Descrição:** Verifique se uma frase completa é um palíndromo (lê-se igual de trás para frente), ignorando estritamente todos os espaços, pontuações e neutralizando diferenças entre letras maiúsculas e minúsculas. **Passo a passo lógico:**

1.  Posicione ponteiros nas extremidades: 
    ```
    inicio = 0
    ```
     e 
    ```
    fim = tamanho_string - 1
    ```
    .
    
2.  Em um loop enquanto 
    ```
    inicio < fim
    ```
    :
    
      17.   **Bypass da esquerda:** Use um loop 
          ```
          while
          ```
           interno para avançar 
          ```
          inicio++
          ```
           se o caractere atual **não for** uma letra ou número (use funções da linguagem como 
          ```
          isalnum()
          ```
           ou verifique valores da tabela ASCII).
          
      31.   **Bypass da direita:** Use outro loop 
          ```
          while
          ```
           interno para retroceder 
          ```
          fim--
          ```
           se não for alfanumérico.
          
      41.   Importante: garanta que nestes sub-loops internos o 
          ```
          inicio
          ```
           nunca ultrapasse o 
          ```
          fim
          ```
          .
          
      51.   **Comparação:** Com os ponteiros limpos, converta ambos os caracteres para minúsculo. Se 
          ```
          char_inicio != char_fim
          ```
          , pare e retorne Falso.
          
      57.   Se forem iguais, continue avaliando: 
          ```
          inicio++
          ```
           e 
          ```
          fim--
          ```
          .
    
3.  Se os ponteiros se encontrarem, todas as comparações passaram: retorne Verdadeiro. **Complexidade:** Tempo O(N) | Espaço O(1). **Exemplo:**
-   **Input:** 
    ```
    "A man, a plan, a canal: Panama"
    ```
    
-   **Output:** 
    ```
    Verdadeiro
    ```
     (Avalia apenas 
    ```
    amanaplanacanalpanama
    ```
    ).

### 13\. [Intersecção de Arrays com Elementos Distintos](https://www.geeksforgeeks.org/dsa/intersection-of-two-arrays-with-distinct-elements/ "null")

**Descrição:** Dados dois arrays que garantidamente contêm apenas elementos distintos internamente, retorne um novo array ordenado contendo os elementos (intersecção) presentes em ambos. **Passo a passo lógico:**

1.  Como a técnica exige ordem para ser linear, ordene ambos os arrays se já não vierem ordenados.
    
2.  Inicialize 
    ```
    p1 = 0
    ```
     (marcando o array 1) e 
    ```
    p2 = 0
    ```
     (marcando o array 2). Crie uma lista/array de resultado.
    
3.  Enquanto 
    ```
    p1 < tamanho1
    ```
     e 
    ```
    p2 < tamanho2
    ```
    :
    
      23.   Faça a comparação base: 
          ```
          valor1 = arr1[p1]
          ```
           e 
          ```
          valor2 = arr2[p2]
          ```
          .
          
      33.   Se 
          ```
          valor1 == valor2
          ```
          : Achamos uma intersecção! Adicione à resposta. Como ambos os arrays são estritamente distintos, avance ambos simultaneamente (
          ```
          p1++
          ```
          , 
          ```
          p2++
          ```
          ).
          
      47.   Se 
          ```
          valor1 < valor2
          ```
          : Como os arrays crescem para a direita, o 
          ```
          valor1
          ```
           atual ficou "para trás" e nunca encontrará um par igual à frente no arr2. Avance 
          ```
          p1++
          ```
           para tentar encontrar um número maior.
          
      61.   Se 
          ```
          valor1 > valor2
          ```
          : Pela mesma lógica, avance 
          ```
          p2++
          ```
          . **Complexidade:** Tempo O(NlogN+MlogM) devido à ordenação, após isso a busca é linear O(N+M) | Espaço O(min(N,M)) para a resposta. **Exemplo:**
-   **Input:** 
    ```
    arr1 = [7, 1, 5, 2, 3, 6]
    ```
    , 
    ```
    arr2 = [3, 8, 6, 20, 7]
    ```
    
-   **Output:** 
    ```
    [3, 6, 7]
    ```
     (Após ordenação: arr1=
    
    1,2,3,5,6,7
    
    , arr2=
    
    3,6,7,8,20
    
    )

</p>

</details>

<details>
  <summary>Nível: Médio (Medium Problems)</summary>

<p>


### 14\. [Contar Pares com Diferença Absoluta Igual a k](https://www.geeksforgeeks.org/dsa/count-pairs-difference-equal-k/ "null")

**Descrição:** Determine matematicamente o número total de pares 
```
(i, j)
```
 em um array cuja diferença absoluta 
```
|array[j] - array[i]|
```
 seja estritamente igual a um valor alvo 
```
k
```
. **Passo a passo lógico:**

1.  Primeiro passo crucial: **Ordene o array**. Diferente da soma, a diferença requer controle direcional preciso.
    
2.  Posicione ambos os ponteiros no início do array, mas desfasados: 
    ```
    i = 0
    ```
     e 
    ```
    j = 1
    ```
    . Eles se moverão na mesma direção.
    
3.  Em um loop 
    ```
    while (i < n e j < n)
    ```
    :
    
      19.   **Validação de distanciamento:** Se 
          ```
          i == j
          ```
           em algum momento (por exemplo, após incrementar 
          ```
          i
          ```
          ), force 
          ```
          j++
          ```
           para garantir que estamos comparando elementos diferentes.
          
      33.   Calcule 
          ```
          diff = array[j] - array[i]
          ```
          .
          
      39.   Se 
          ```
          diff == k
          ```
          : Encontramos um par! Incremente o contador. Em seguida, avance 
          ```
          j++
          ```
          . (Nota: se houver elementos repetidos, uma lógica extra de contagem de repetições seria necessária, avalie o escopo do desafio).
          
      49.   Se 
          ```
          diff < k
          ```
          : A diferença está muito pequena. Para aumentá-la, precisamos aumentar o 
          ```
          array[j]
          ```
          , logo avance 
          ```
          j++
          ```
          .
          
      63.   Se 
          ```
          diff > k
          ```
          : A diferença estourou o limite. Para reduzi-la, precisamos aumentar o valor que subtraímos (
          ```
          array[i]
          ```
          ), logo avance 
          ```
          i++
          ```
          . **Complexidade:** Tempo O(NlogN) | Espaço O(1). **Exemplo:**
-   **Input:** 
    ```
    array = [1, 5, 3, 4, 2]
    ```
    , 
    ```
    k = 3
    ```
    
-   **Output:** 
    ```
    2
    ```
     (Pares possíveis no array ordenado 
    ```
    [1, 2, 3, 4, 5]
    ```
     são 
    ```
    [1, 4]
    ```
     e 
    ```
    [2, 5]
    ```
    ).

### 15\. [Soma de Trio no Array](https://www.geeksforgeeks.org/dsa/find-a-triplet-that-sum-to-a-given-value/ "null")

**Descrição:** Identifique se há a existência de exatamente três elementos (um trio) em um array cuja soma totalize um valor alvo 
```
X
```
. **Por que este problema é genial?** Ele ensina a quebrar um problema 3D em um problema 2D. Ao "congelar" um elemento, o problema se reduz ao clássico "Two Sum". **Passo a passo lógico:**

1.  Ordene o array em ordem crescente.
    
2.  Use um laço de repetição 
    ```
    for
    ```
     externo iterando um índice 
    ```
    i
    ```
     de 
    ```
    0
    ```
     até 
    ```
    n - 3
    ```
    . Este laço fixa a primeira peça do nosso trio, que chamaremos de "âncora".
    
3.  Dentro do laço, os ponteiros restantes entram em ação: defina 
    ```
    esq = i + 1
    ```
     (imediatamente após a âncora) e 
    ```
    dir = n - 1
    ```
     (no final).
    
4.  Aplique a mesma lógica do Two Sum para o subarray remanescente:
    
      33.   Calcule 
          ```
          soma_atual = array[i] + array[esq] + array[dir]
          ```
          .
          
      39.   Se 
          ```
          soma_atual == X
          ```
          : Retorne Verdadeiro imediatamente.
          
      45.   Se 
          ```
          soma_atual < X
          ```
          : Incremente 
          ```
          esq++
          ```
          .
          
      55.   Se 
          ```
          soma_atual > X
          ```
          : Decremente 
          ```
          dir--
          ```
          . **Complexidade:** Tempo O(N2) (um loop fixo multiplicando um loop dos ponteiros internos) | Espaço O(1). **Exemplo:**
-   **Input:** 
    ```
    array = [1, 4, 45, 6, 10, 8]
    ```
    , 
    ```
    X = 22
    ```
    
-   **Output:** 
    ```
    Verdadeiro
    ```
     (Trio: 4 + 10 + 8)

### 16\. [Soma de Dois Igual ao Terceiro](https://www.geeksforgeeks.org/dsa/find-triplet-sum-two-equals-third-element/ "null")

**Descrição:** Variação do Triplet Sum. Descubra se, dentro do array, existem dois elementos cuja soma é cirurgicamente igual a um terceiro elemento presente no mesmo array. **Passo a passo lógico:**

1.  A base é a mesma do problema 15: **Ordene o array**.
    
2.  A sacada aqui é inverter a perspectiva: como a soma de dois números em um array positivo sempre será maior que as partes, o número "Alvo" deve ser sempre um dos maiores números do array.
    
3.  Itere de **trás para frente** com um loop 
    ```
    for
    ```
    , onde a âncora 
    ```
    i
    ```
     começa em 
    ```
    n - 1
    ```
     até 
    ```
    2
    ```
    . Este 
    ```
    array[i]
    ```
     será o nosso "Alvo da vez".
    
4.  Defina os dois ponteiros limitados pelos números anteriores ao alvo: 
    ```
    esq = 0
    ```
     (o menor de todos) e 
    ```
    dir = i - 1
    ```
     (o maior logo antes do alvo).
    
5.  Com a fórmula mágica 
    ```
    array[esq] + array[dir] == array[i]
    ```
    :
    
      43.   Se forem iguais, achou o trio (retorne Verdadeiro).
          
      45.   Se a soma for menor que a âncora, precisamos elevar a soma: 
          ```
          esq++
          ```
          .
          
      51.   Se for maior, temos muito peso: 
          ```
          dir--
          ```
          . **Complexidade:** Tempo O(N2) | Espaço O(1). **Exemplo:**
-   **Input:** 
    ```
    array = [5, 32, 1, 7, 10, 50, 19, 21, 2]
    ```
    
-   **Output:** 
    ```
    Verdadeiro
    ```
     (Após ordenar: 
    ```
    1, 2, 5, 7...
    ```
     A soma de 2 + 5 = 7 é perfeitamente validada).

### 17\. [K-ésimo Elemento de Dois Arrays](https://www.geeksforgeeks.org/problems/k-th-element-of-two-sorted-array1317/1 "null")

**Descrição:** Imagine juntar dois arrays distintos previamente ordenados, formando um grandioso array ordenado. Retorne qual seria o número que ocuparia exatamente a 
```
k-ésima
```
 posição, mas sem alocar memória criando este terceiro array! **Passo a passo lógico:**

1.  A configuração requer leitura em duas pistas simultâneas: 
    ```
    p1 = 0
    ```
     (início do array 1) e 
    ```
    p2 = 0
    ```
     (início do array 2).
    
2.  Crie uma variável 
    ```
    contador = 0
    ```
     para rastrear sua posição virtual no "novo array invisível".
    
3.  Crie um loop 
    ```
    while (p1 < tamanho1 e p2 < tamanho2)
    ```
    :
    
      23.   Avalie o menor valor disponível: 
          ```
          se arr1[p1] < arr2[p2]
          ```
          .
          
      29.   Identificado o menor valor, registre-o em uma variável temporária 
          ```
          atual
          ```
          , incremente o contador 
          ```
          c++
          ```
           e avance o ponteiro do vencedor (neste exemplo, 
          ```
          p1++
          ```
          ).
          
      43.   Caso o 
          ```
          arr2[p2]
          ```
           fosse menor ou igual, faria o mesmo com o 
          ```
          p2
          ```
          .
          
      53.   **Checagem Imediata:** Verifique se o 
          ```
          contador == k
          ```
          . Se sim, a resposta é o valor 
          ```
          atual
          ```
          . Interrompa o programa.
    
4.  **Tratamento de Exaustão:** E se um array for muito menor que o outro e seus elementos acabarem? Se o loop principal terminar e 
    ```
    contador < k
    ```
    , você fará loops adicionais exclusivos para esvaziar 
    ```
    p1
    ```
     ou 
    ```
    p2
    ```
     até bater 
    ```
    k
    ```
    . **Complexidade:** Tempo O(K) na abordagem de ponteiros lineares (uma otimização avançada com Busca Binária poderia fazer isso em O(log(min(N,M))), mas desfoca do estudo de Two Pointers) | Espaço O(1). **Exemplo:**
-   **Input:** 
    ```
    arr1 = [2, 3, 6, 7, 9]
    ```
    , 
    ```
    arr2 = [1, 4, 8, 10]
    ```
    , 
    ```
    k = 5
    ```
    
-   **Output:** 
    ```
    6
    ```
     (Evolução virtual: 1 → 2 → 3 → 4 → 6).

### 18\. [União de 2 Arrays Ordenados com Duplicatas](https://www.geeksforgeeks.org/problems/union-of-two-sorted-arrays-1587115621/1 "null")

**Descrição:** Calcule matematicamente a união formal de dois arrays ordenados (que podem conter elementos repetidos). A regra de união matemática determina que os elementos da resposta devem ser distintos e estar ordenados. **Passo a passo lógico:**

1.  Coloque os ponteiros de largada: 
    ```
    i = 0
    ```
     e 
    ```
    j = 0
    ```
    . Aloque uma estrutura de lista dinâmica para acumular o resultado.
    
2.  Inicie o loop de travessia concorrente 
    ```
    while(i < n && j < m)
    ```
    :
    
      17.   **Bypass de Duplicidade Interna:** Se 
          ```
          arr1[i]
          ```
           for igual ao elemento anterior 
          ```
          arr1[i-1]
          ```
          , ele é uma repetição e você deve pular executando 
          ```
          i++
          ```
           e um 
          ```
          continue
          ```
          . Faça exatamente a mesma checagem de bypass para o 
          ```
          arr2[j]
          ```
          .
          
      39.   Comparação Inter-Arrays:
          
              41.   Se 
                  ```
                  arr1[i] < arr2[j]
                  ```
                  : O elemento do arr1 é o menor global disponível. Adicione-o na resposta e mova 
                  ```
                  i++
                  ```
                  .
                  
              51.   Se 
                  ```
                  arr2[j] < arr1[i]
                  ```
                  : O elemento do arr2 venceu. Adicione à resposta e mova 
                  ```
                  j++
                  ```
                  .
                  
              61.   Se houver **empate de valores** (
                  ```
                  arr1[i] == arr2[j]
                  ```
                  ): Ambos detêm o mesmo número. Adicione-o à resposta apenas uma vez, mas avance **ambos** os ponteiros simultaneamente (
                  ```
                  i++
                  ```
                   e 
                  ```
                  j++
                  ```
                  ), garantindo que não contaremos dobrado.
    
3.  **Rescaldo Final:** Como no problema anterior, um array pode acabar antes do outro. Crie loops 
    ```
    while
    ```
     separados no final para despejar os elementos remanescentes de 
    ```
    arr1
    ```
     (ou 
    ```
    arr2
    ```
    ), aplicando rigidamente a regra do "Bypass de Duplicidade Interna" antes de inserir. **Complexidade:** Tempo O(N+M) | Espaço O(N+M) para a lista final de retorno. **Exemplo:**
-   **Input:** 
    ```
    arr1 = [1, 2, 2, 2, 3]
    ```
    , 
    ```
    arr2 = [2, 3, 4, 5]
    ```
    
-   **Output:** 
    ```
    [1, 2, 3, 4, 5]
    ```

### 19\. [Subarrays com Máximo no Intervalo](https://www.geeksforgeeks.org/dsa/number-subarrays-maximum-value-given-range/ "null")

**Descrição:** Fornecido um array puro, determine o número total de subarrays contíguos concebíveis onde o maior valor numérico dentro desse subarray caia estritamente no intervalo fechado 
```
[L, R]
```
. **Por que Dois Ponteiros?** A contagem dinâmica de subarrays consecutivos se traduz visualmente como uma janela elástica que se expande por valores válidos. **Passo a passo lógico (Abordagem por Diferença Matemática):**

1.  O raciocínio direto é complexo de rastrear. O raciocínio brilhante usa a propriedade de conjuntos: 
    ```
    (Subarrays cujo Max <= R)
    ```
     5. 
    ```
    (Subarrays cujo Max < L)
    ```
    . A interseção matemática resultará na resposta cravada para a faixa pretendida!
    
2.  Crie uma função auxiliar 
    ```
    contaSubarraysValidos(array, Limite_K)
    ```
    :
    
      17.   Inicialize a contagem global: 
          ```
          total = 0
          ```
          .
          
      23.   Inicialize a janela acumulativa: 
          ```
          janela = 0
          ```
          .
          
      29.   Percorra o array elemento a elemento:
          
              31.   Se o elemento atual 
                  ```
                  array[i] <= Limite_K
                  ```
                  , este elemento não viola a regra. Ele expande a janela de possibilidades em 1: 
                  ```
                  janela++
                  ```
                  . Ao crescer a janela, todos os novos subarrays contíguos terminados neste elemento são válidos. Logo, fazemos a soma matemática 
                  ```
                  total = total + janela
                  ```
                  .
                  
              45.   Se o elemento causar uma ruptura na regra (
                  ```
                  array[i] > Limite_K
                  ```
                  ), a contiguidade lógica morre e o limite estoura. A punição? A janela zera imediatamente: 
                  ```
                  janela = 0
                  ```
                  .
    
3.  Na função principal, execute a matemática de diferença: 
    ```
    retorne contaSubarraysValidos(arr, R) - contaSubarraysValidos(arr, L - 1)
    ```
    . **Complexidade:** Tempo O(N) (duas travessias completas) | Espaço O(1). **Exemplo:**
-   **Input:** 
    ```
    array = [2, 0, 11, 3, 0]
    ```
    , 
    ```
    L = 1
    ```
    , 
    ```
    R = 10
    ```
    
-   **Output:** 
    ```
    4
    ```
     (Subarrays extraídos e analisados individualmente:
    
    2
    
    ,
    
    2,0
    
    ,
    
    3
    
    ,
    
    3,0
    
    . O número 11 explode qualquer janela em que toque).

### 20\. [Maior Substring com K Caracteres Únicos](https://www.geeksforgeeks.org/dsa/find-the-longest-substring-with-k-unique-characters-in-a-given-string/ "null")

**Descrição:** Identifique numericamente o tamanho da maior cadeia de caracteres consecutiva (substring) que mantenha a propriedade estrita de abrigar _exatamente_ 
```
K
```
 caracteres totalmente distintos em sua composição. **Passo a passo lógico (Janela Deslizante Expansiva/Contrativa):**

1.  Inicialize seus delimitadores espaciais: 
    ```
    esq = 0
    ```
     e 
    ```
    dir = 0
    ```
    . Crie uma variável global 
    ```
    maior_tamanho = -1
    ```
     (caso não seja possível formar o padrão) e uma tabela hash (Map ou Dicionário) para registrar a 
    ```
    [letra -> frequência de ocorrências]
    ```
    .
    
2.  O loop mestre avança o pioneiro 
    ```
    dir
    ```
     a cada ciclo:
    
      25.   Coloque a letra que 
          ```
          dir
          ```
           apontou no Dicionário. Se já existir, aumente a frequência em 1. Se for inédita, inicie a frequência em 1.
    
3.  Se o número total de chaves do dicionário (tipos de caracteres distintos) estiver menor que 
    ```
    K
    ```
    , a janela ainda está subdesenvolvida. Continue avançando 
    ```
    dir
    ```
    .
    
4.  Se o número de chaves for cirurgicamente **igual** a 
    ```
    K
    ```
    : É uma janela válida! Calcule a largura 
    ```
    (dir - esq + 1)
    ```
     e compare salvando se for maior que 
    ```
    maior_tamanho
    ```
    .
    
5.  Se o número total de chaves superar e for **maior** que 
    ```
    K
    ```
    : A janela explodiu. É o momento de purgar elementos a partir do fundo 
    ```
    esq
    ```
    .
    
      65.   Encolha a janela diminuindo a frequência do caractere que 
          ```
          esq
          ```
           aponta do Dicionário.
          
      71.   **Crucial:** Se a frequência de um caractere atingir zero após a subtração, ele foi exterminado da janela. A chave correspondente no mapa deve ser fisicamente apagada.
          
      73.   Após a redução, avance 
          ```
          esq++
          ```
          . Repita isso enquanto 
          ```
          tamanho do mapa > K
          ```
          . **Complexidade:** Tempo O(N) | Espaço O(K) para armazenar no máximo K+1 caracteres no mapa da janela. **Exemplo:**
-   **Input:** 
    ```
    string = "aabbcc"
    ```
    , 
    ```
    k = 2
    ```
    
-   **Output:** 
    ```
    4
    ```
     (As janelas vencedoras absolutas, com tamanho 4, são "aabb" ou "bbcc").

### 21\. [Remover e Inverter](https://www.geeksforgeeks.org/dsa/remove-repeating-chars-and-reverse-string-until-no-repetitions/ "null")

**Descrição:** Fornecida uma string, as regras determinam um ciclo punitivo onde: toda vez que você localiza a primeira letra repetida da frase partindo da sua atual direção de leitura, ela deve ser apagada da string e a frase inteira deve ser mecanicamente "revertida". O ciclo brutal acaba quando só restam caracteres distintos. **A Visão de Ouro:** Não Inverta Strings. Repito, _não inverta strings fisicamente_. Simula-se uma inversão apenas mudando a leitura para trás e para frente. Se você criar strings ao contrário a cada exclusão, causará tempo O(N2) por alocação na memória. **Passo a passo lógico (Simulação por Direção):**

1.  Crie uma matriz/dicionário rastreando a frequência global e real de todos os caracteres disponíveis desde o tempo zero.
    
2.  Defina os baluartes 
    ```
    esq = 0
    ```
     (na esquerda) e 
    ```
    dir = tamanho - 1
    ```
     (na direita). Crie uma booleana de estado de fluxo direcional: 
    ```
    sentido_normal = Verdadeiro
    ```
    .
    
3.  Abra um loop dinâmico enquanto 
    ```
    esq <= dir
    ```
    :
    
      23.   **Fase Esquerda (Se 
          ```
          sentido_normal
          ```
           for Verdadeiro):**
          
              29.   Analise a letra cravada em 
                  ```
                  esq
                  ```
                  .
                  
              35.   Tem frequência > 1 na contagem global? Sim! O gatilho disparou. Subtraia 1 da frequência, reescreva na posição original um marcador de aniquilação como 
                  ```
                  '#'
                  ```
                   (ou um vazio da sua linguagem). A penalidade foi aplicada: comute o estado com 
                  ```
                  sentido_normal = Falso
                  ```
                   e aplique 
                  ```
                  dir--
                  ```
                  .
                  
              49.   É letra única (frequência 1)? Não é o alvo. Avance pacientemente: 
                  ```
                  esq++
                  ```
                  .
          
      55.   **Fase Direita (Se 
          ```
          sentido_normal
          ```
           for Falso):**
          
              61.   O leitor agora é o 
                  ```
                  dir
                  ```
                  . Analise a letra.
                  
              67.   Frequência > 1? Gatilho! Apaga, marca com 
                  ```
                  '#'
                  ```
                  , pune a string revertendo de novo 
                  ```
                  sentido_normal = Verdadeiro
                  ```
                   e ande com o iterador reverso: 
                  ```
                  esq++
                  ```
                  .
                  
              81.   Letra única? Apenas ande em ré ignorando o ruído: 
                  ```
                  dir--
                  ```
                  .
    
4.  Geração do Retorno: Percorra a matriz final do início ao fim filtrando todas as marcas 
    ```
    '#'
    ```
    . Por fim, se e _somente se_ o status final for 
    ```
    sentido_normal == Falso
    ```
    , lance um reverso físico simples de O(N) antes de retornar. **Complexidade:** Tempo O(N) | Espaço O(N) para reconstrução da string. **Exemplo:**
-   **Input:** 
    ```
    "abab"
    ```
    
-   **Output:** 
    ```
    "ba"
    ```

### 22\. [O Problema da Celebridade](https://www.geeksforgeeks.org/dsa/the-celebrity-problem/ "null")

**Descrição:** Você está no controle de uma festa de socialites. O título nobre de "Celebridade" se enquadra em critérios cruéis e exatos: A celebridade não sabe do nome de um único participante (não conhece ninguém), enquanto paradoxalmente todos e cada um dos participantes conhece e reverencia a Celebridade. Você tem um detector matricial booleano através da função 
```
conhece(A, B)
```
 para testes. Prove a existência e encontre este indivíduo (ou relate 
```
-1
```
 se ele não for achado). **Por que Dois Ponteiros e não Teoria de Grafos Pesados?** Se visualizarmos isso como uma linha reta, a eliminação sucessiva dos fracos fará o monarca verdadeiro sobrar em tempo puramente linear. **Passo a passo lógico:**

1.  Aponte e crie uma arena imaginária delimitando dois candidatos opositores: 
    ```
    A = 0
    ```
     (início) e 
    ```
    B = n - 1
    ```
     (fim).
    
2.  O loop da morte se instaura: 
    ```
    enquanto A < B
    ```
    :
    
      17.   Chame o detector: 
          ```
          conhece(A, B)
          ```
          .
          
      23.   Se der Verdadeiro: Isso prova conclusivamente que o indivíduo "A" conhece o indivíduo "B". A regra quebra: a celebridade é burra em networking e não pode conhecer o B. O candidato "A" é varrido da festa. Aumente seu iterador substituindo o participante no ringue 
          ```
          A++
          ```
          .
          
      29.   Se der Falso: Isso prova que "A" esnoba sumariamente "B", ou seja, "B" falhou o teste rigoroso da fama, pois uma celebridade é onipresente na mente dos outros. Remova "B" da festa retraindo o limite 
          ```
          B--
          ```
          .
    
3.  Ao término desse balé destrutivo e lógico, restarão iguais a mesma pessoa 
    ```
    A == B
    ```
    . A pessoa "A" se provou resiliente e detém agora o título de _"Potencial Monarca da Celeb"_.
    
4.  **Fase de Verificação (Indispensável):** Isso era sobre probabilidades eliminatórias. Agora você deve testar "A" num loop 
    ```
    for
    ```
     isolado com todos. Para cada convidado 
    ```
    i
    ```
     de zero a n: se 
    ```
    A
    ```
     conhecer o indivíduo 
    ```
    i
    ```
    , ou o indivíduo 
    ```
    i
    ```
     61.*não** conhecer a pessoa 
    ```
    A
    ```
    , o título vira poeira (retorne 
    ```
    67.1
    ```
    ). Se a checagem com todos der certo, 
    ```
    A
    ```
     é coroada. **Complexidade:** Tempo O(N) | Espaço O(1). **Exemplo:**
-   **Input:** Uma matriz matricial 
    ```
    M[convidados]
    ```
     
    ```
    [[0, 1, 0],
    ```
     <- Convidado 0: só reverencia o 1. 
    ```
     [0, 0, 0],
    ```
     <- Convidado 1: zero interações! 
    ```
     [0, 1, 0]]
    ```
     <- Convidado 2: reverencia o 1.
    
-   **Output:** A Celebridade da festa é, indiscutivelmente, a Pessoa 1.

</p>

</details>

<details>
  <summary>Nível: Difícil (Hard Problems)</summary>

<p>


### 23\. [Problema de Retenção de Água da Chuva](https://www.geeksforgeeks.org/dsa/trapping-rain-water/ "null")

**Descrição:** É entregue uma matriz unidimensional não negativa detalhando e contornando a elevação altimétrica de bloquetes de terra enfileirados onde a largura fixa global de cada tijolo vale 
```
1
```
 unidade. Após uma precipitação gigantesca, estabeleça com rigor quantitativo e matemático quantas piscinas geométricas (unidades cúbicas de água limpa) serão confinadas sobre essas vales de terra no mundo 2D. **O Conceito (O que segura a água?):** Para qualquer pilar de terra na posição 
```
i
```
, a quantidade de litros d'água capaz de estagnar sobre sua crista provém estritamente de uma matemática natural e de limites opressores da física do cenário. Ela é determinada pelo 
```
Mínimo de Altura
```
 entre o pináculo geográfico absoluto à sua extrema Esquerda e o pináculo geográfico à sua extrema Direita, deduzida de sua respectiva base (altura nativa). Água = 
```
min(maximo_esq, maximo_dir) - altura_local
```
. A dificuldade brutal aqui é compilar as estáticas "Picos Extremos" dos limites sem torrar memória auxiliar (O(N) com Arrays Auxiliares). **Passo a passo lógico (Abordagem Genial** O(1) **de Espaço):**

1.  Delimitação geográfica das frentes: 
    ```
    esq = 0
    ```
     (Ponta Oceânica Ocidental) e 
    ```
    dir = tamanho - 1
    ```
     (Ponta Oceânica Oriental).
    
2.  Sensores altimétricos máximos zerados: 
    ```
    pico_max_esq = 0
    ```
     e 
    ```
    pico_max_dir = 0
    ```
    . Variável mestre 
    ```
    agua_armazenada = 0
    ```
    .
    
3.  Loop contínuo: 
    ```
    enquanto esq <= dir
    ```
    :
    
      31.   **Fase Operacional 1: Decisão da Parede Mestra Limitadora.** Analise friamente as elevações baseadas nos iteradores puros (as "paredes" atuais das frentes extremas): Se 
          ```
          terreno[esq] <= terreno[dir]
          ```
          . A ponta do flanco da Direita formou um muro titânico, maior do que a parede que ampara e bloqueia do lado Esquerdo. Qualquer volume de água injetado do lado da parede menor da Esquerda será fisicamente contido ali de modo inabalável pela colossal montanha da Direita. O obstáculo limitante não é o bloco 
          ```
          dir
          ```
          , logo podemos nos isolar completamente no trato de computação sobre a célula do bloco atual do index 
          ```
          esq
          ```
           da esquerda.
          
              45.   Caso 
                  ```
                  terreno[esq]
                  ```
                   supere brutalmente a marca histórica de barreira ocidental (
                  ```
                  terreno[esq] >= pico_max_esq
                  ```
                  ), isso não afunda e não retém água. É o pináculo. Apenas atualize altimetria: 
                  ```
                  pico_max_esq = terreno[esq]
                  ```
                  .
                  
              59.   Em contrapartida, se formos varridos por uma cota menor (estivermos em um vale), acumule na conta real o lucro fluído pela subtração da métrica do teto: 
                  ```
                  agua_armazenada += pico_max_esq - terreno[esq]
                  ```
                  .
                  
              65.   Ande topograficamente: 
                  ```
                  esq++
                  ```
                  .
          
      71.   **Fase Operacional 2 (Simétrica Oposta):** Se for a ponta Esquerda a grande muralha (
          ```
          terreno[esq] > terreno[dir]
          ```
          ), o bloqueio se inverte. Focamos inescrupulosamente na parede inferior (Direita).
          
              77.   Bateu a cota do paredão geográfico recordista asiático? Ajuste altimetria: 
                  ```
                  pico_max_dir = terreno[dir]
                  ```
                  .
                  
              83.   Ou é ladeira de vale que detém massa pluvial de poça na parede Leste? Inunde computando matematicamente o saldo do teto subtraído do chão nativo: 
                  ```
                  agua_armazenada += pico_max_dir - terreno[dir]
                  ```
                  .
                  
              89.   Avance: 
                  ```
                  dir--
                  ```
                  . **Complexidade:** Tempo O(N) (Uma cruzada cirúrgica das bordas pro centro, elemento por elemento). | Espaço O(1) (Nada de Arrays para mapear prefixos). **Exemplo:**
-   **Input:** 
    ```
    array = [0, 1, 0, 2, 1, 0, 1, 3, 2, 1, 2, 1]
    ```
    
-   **Output:** 
    ```
    6
    ```
     (Unidades mapeadas entre os paredões geológicos formados aos picos 1, 2 e o divisor absoluto central em valor de pico que era 3).

### 24\. [Soma de Quatro - Verificar Quádruplo](https://www.geeksforgeeks.org/dsa/find-four-numbers-with-sum-equal-to-given-sum/ "null")

**Descrição:** E scale as engrenagens a quatro marchas lógicas na arquitetura matemática do clássico 'Two Sum'. Fornecida uma listagem generalista, ratifique em formato booleano verdadeiro ou falso se incrustados na matriz, existem misteriosamente 4 números paralelos desconexos os quais perante adição simples gerem um peso predefinido como objetivo e Alvo 
```
X
```
. **O Conceito:** Onde falhamos em loops quádruplos de O(N4) inaceitáveis nas esferas computacionais, reduzimos brilhantemente para cravados O(N3) enrijecendo estrategicamente "ancoragens em bloco". Você trava duas pedras e os exploradores Two Pointers realizam a caça flexível nas outras pontas. **Passo a passo lógico:**

1.  Ordem imperativa do Caos: **Ordene** o array ascendentemente e rigorosamente. Sem esta fundação não aplicam-se movimentos dedutíveis Two Pointers em janelas fechadas.
    
2.  Trave a âncora primordial, com o clássico loop superior do 
    ```
    i
    ```
    . Vá de 
    ```
    0
    ```
     a meramente 
    ```
    n-4
    ```
     (reservar respiros limítrofes para preencher o resto do bonde de 4 e evitar 
    ```
    IndexOutOfBouds
    ```
    ).
    
3.  Aninhe a segunda âncora fixa. Desencadeie um novo laço de iteração dependente com escopo engajado na variável iterativa 
    ```
    j
    ```
    , atrelando o gatilho a principiar de 
    ```
    i + 1
    ```
     até as franjas operacionais de final limiar 
    ```
    n-3
    ```
    .
    
4.  Os iteradores de varredura ativa de Busca em Escala Two Pointers foram forjados no espaço restante dos blocos da máquina: Defina estático 
    ```
    esq = j + 1
    ```
     e 
    ```
    dir = n - 1
    ```
     na fronteira limite máxima disponível para varredura vetorial do grid numérico de procura.
    
5.  Invoque o laço de confronto binário do "Dois Ponteiros":
    
      47.   Equacione em registro global 
          ```
          Soma = array[i] + array[j] + array[esq] + array[dir]
          ```
          .
          
      53.   Balanceamentos Otimizados do Peso e Medida:
          
              55.   Alvo neutralizado por perfeição matemática (
                  ```
                  Soma == alvo
                  ```
                  )? Finalize o processo operacional emitindo Fiel Verdadeiro como sinalização final e encerre as chamadas computacionais pendentes.
                  
              61.   Alvo com desbalanceamento para menor peso de medida global (
                  ```
                  Soma < alvo
                  ```
                  )? Fazer contrapeso na balança: incremente de peso inferior pro centro: 
                  ```
                  esq++
                  ```
                  .
                  
              71.   Alvo estourando teto por obesidade excessiva de balança (
                  ```
                  Soma > alvo
                  ```
                  )? Cortar de peso magro pra esquerda recuando peso pesado do final de fita limiar: recue 
                  ```
                  dir--
                  ```
                  . **Complexidade:** Tempo O(N3) (dois loops for em cima e uma varredura paralela por baixo unindo os pontos cruzados) | Espaço logístico de processamento O(1) caso o sort inicial seja desconsiderado (ou equivalente à lógica sort usada). **Exemplo:**
-   **Input:** 
    ```
    array = [10, 2, 3, 4, 5, 9, 7, 8]
    ```
    , 
    ```
    alvo = 23
    ```
    
-   **Output:** 
    ```
    Verdadeiro
    ```
     (Os quádruplos formadores do eixo mestre provados por soma analógica seriam exemplificativamente listados em formadores paralelos limpos como:
    
    3,5,7,8
    
    , cuja soma totaliza dezenas lógicas corretas 23).

### 25\. [Soma de Quatro – Todos os Quádruplos Distintos com Soma Dada](https://www.geeksforgeeks.org/dsa/find-four-elements-that-sum-to-a-given-value-set-2/ "null")

**Descrição:** O ápice da provação acadêmica arquitetada. Semelhante simetricamente no aspecto central primário com o exercício número 24 contido na página anterior da lição algorítmica. No entanto, o paradigma operacional evolui exponencialmente num grau severo e sem tréguas: neste teste estrito de ferro, o programador desenvolvedor deve arquitetar a listagem irrestrita provendo aos testadores o print **completo** de conjuntos válidos. O pesadelo da memória e lógica é implementado pelo impeditivo mestre da regra real deste desafio: **Todos os quádruplos de respostas de somatórias e elementos interrelacionais devem ser escrupulosamente ímpares em identidade grupal e originais por definição matemática**. Cópias fantasmas formadas pela permutação e cruzamento de indexação gerando agrupamento clonado em repetições exatas (Exemplo: entregar 
```
[[-2,-1,1,2]
```
 e subitamente lançar nas costas do testador outra resma 
```
[-2,-1,1,2]
```
) resultará num estrondoso "Falha Total" no sistema automatizado validador, e em falência de banco de dados computacional caso levado pra vida profissional da engenharia de código com dados descontrolados de loops de redundância infinita em escopos globais numéricos absurdos. **Passo a passo lógico:**

1.  A matriz precisa de ordenação (
    ```
    Sort()
    ```
    ) como a fundação irremovível desta arquitetura mestre base dos Two Pointers dimensionais múltiplos de N e vetores de listas mutáveis pra armazenar seu log.
    
2.  Aplique a moldura simétrica em cascata aninhada de loop duplo 
    ```
    i
    ```
     e com loop interno encadeado secundário engrenado no 
    ```
    j
    ```
     como já solidificado no estudo de verificação primária simplista.
    
3.  **Ponto Crítico do Engenheiro (Os Saltos de Bloqueios Anti-Clones Matemáticos):** Para extirpar de vez e podar qualquer desabrochar logístico de clonagem indesejável de blocos iterados de respostas vetoriais de agrupamento de matrizes de resposta, adicione travas sistêmicas purgadas em saltos e _skips_ nas malhas estruturais da progressão direcional e rotativa de cada único e maldito iterador da equação, barrando passagens de loopings que usem a base em clones identificados (usar instrução mestre limpa e direta: 
    ```
    continue
    ```
     nas linhas processadoras se a linguagem atuar desta base limiar imperativa comum).
    
      23.   **Bloqueio Âncora I:** No topo master inicial do loop regente atrelado na âncora master suprema operada por 
          ```
          i
          ```
          , a trava dispara brutal se o índex não estiver no zero-based ground limit e provar clones colados por proximidade: se logicamente o 
          ```
          array[i] == array[i-1]
          ```
          , ative ignição 
          ```
          continue
          ```
          .
          
      37.   **Bloqueio Âncora J:** Na submalha rotatória gerida pela âncora co-master travada provida de base no iterador referenciado por local na malha atrelado por escopo variável em engrenagem secundária no identificador chamado de 
          ```
          j
          ```
          , ative a mesma proteção matemática primária de skip block: se 
          ```
          j > i + 1
          ```
           (para garantir que ele saia do ground zero local fixado após ancoragem base dele) e simultaneamente 
          ```
          array[j] == array[j-1]
          ```
          , defina o laço a pular operando o break-skip na volta chamando impiedoso a quebra parcial de bypass com 
          ```
          continue
          ```
          .
          
      55.   **Rescaldo Operacional de Bloqueio nos Exploradores Moveis:** Encontrada com precisão log-matemática a soma abençoada estrita provada para cravar com sinal igual ao 
          ```
          X
          ```
           (
          ```
          Alvo Mestre Global
          ```
          ), grave solenemente as 4 frentes (
          ```
          i
          ```
          , 
          ```
          j
          ```
          , 
          ```
          esq
          ```
          , 
          ```
          dir
          ```
          ) na estrutura limpa do repositório matriz matriz. Agora libere pra avanço padrão normal proximo ciclo incrementando e reduzindo os rastreadores moveis 
          ```
          esq++
          ```
           e 
          ```
          dir--
          ```
          . **Agora a terceira barreira anti-clonagem paralela final das esferas moveis do motor em tempo linear deve agir impiedosa purificando a continuidade do espaço vetorial no motor móvel e evitando inserção redundante do array de matriz**: lance minúsculos 
          ```
          while
          ```
           paralelos bloqueantes em tempo de execução subitânea checando lixo clonado: 
          ```
          enquanto(esq < dir e array[esq] == array[esq-1]) ative pulo cego forçado do pino de alça com esq++;
          ```
           e faça com clareza idêntica da operação espelhada e travada o mesmo check invertido em linha limpa final 
          ```
          enquanto(esq < dir e array[dir] == array[dir+1]) dispare um pulo seco com bloqueio descendo dir--;
          ```
          . **Complexidade:** Tempo puramente O(N3) (A filtragem por bypass skips reduz tempo operacional real mas estatisticamente mantém o Worst-Case global inalterado para 3 eixos paralelos em limite quadrático de processamento pesado da linha) | Espaço extra logado em uso de sistema para resposta estritamente variável entre cravados O(1) de base limpa temporária e limiar estrito O(N3) de Worst-Case caótico pra armazenamento exato local matriz resposta única e absoluta na saída computacional do software. **Exemplo:**
-   **Input:** 
    ```
    array = [1, 0, -1, 0, -2, 2]
    ```
    , 
    ```
    alvo = 0
    ```
    
-   **Output Resposta Sem Clones Sujos:** 
    ```
    [[-2, -1, 1, 2], [-2, 0, 0, 2], [-1, 0, 0, 1]]
    ```
     (Qualquer outra combinação seria apenas números com arranjo interno diferente resultando do cruzamento de cópias descartadas do numero zero nas casas de índices nativos separados 1 e 3 da input line base vetorial orginal nativa).

### Conclusão e Dicas Finais

A técnica de Dois Ponteiros é uma das ferramentas mais belas, poderosas e elegantes da lógica de programação. Quando você olha para um problema que parece exigir O(N2) (loops iterando sobre si mesmos para comparar pares), pergunte a si mesmo:

1.  **Eu posso ordenar este array?** (O sort custa O(NlogN), o que frequentemente compensa e muito em comparação a O(N2)).
    
2.  **Eu tenho acesso a ponteiros direcionalmente opostos ou em paralelo no mesmo sentido direcional de corrida algorítmica linear de passo a passo para espremer o resultado no meio (Two Sum) ou filtrar como funil pro final cravado num só pass-through limpo purificatório (Remove Duplicates)?**
    
3.  **Estou sendo requisitado para inspecionar um escopo limiar global que deve se expandir contínuo sem saltos para atender limites restritos contendo soma, máximos e alvos e esvaziando excessos?** (Pense com força em Janelas Deslizantes - Sliding Window).

Pratique a listagem massiva até as mãos codificadoras mecanizarem instintivamente a reação limpa das sub-regras e limites. Ao terminar a lista em linguagem natural pura pseudocodificada do português nativo de aprendizado limpo de base engenhada pra programador, escreva em código C ou base estrita Java sem métodos de ajuda do compilador/engine. Boa sorte, forte abstração cerebral pra ti e ótima rotina dura nos teus futuros estudos!

</p>

</details>
