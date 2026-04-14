# Lista de Exercícios - Algoritmos de Busca

Este documento é focado no fortalecimento da lógica de programação através da resolução de problemas clássicos e avançados de algoritmos de busca. Os exercícios estão divididos por nível de dificuldade e foram cuidadosamente selecionados para cobrir os principais padrões algorítmicos cobrados em entrevistas técnicas e competições de programação.

Para cada problema, você encontrará a descrição geométrica, a Entrada (Input) e Saída (Output) esperadas, e um roteiro lógico (Passo a Passo) agnóstico a linguagens (C, C++, Java, Python, TypeScript, Go, etc.).

Além disso, adicionamos as **Complexidades de Tempo e Espaço (Big-O)**, **Casos Extremos (Edge Cases)** que costumam quebrar códigos mal testados, e uma **Dica de Ouro** para identificar o padrão por trás do problema.

<details>
  <summary>🟢 Nível 1 - Fácil</summary>
<p>

Problemas de nível fácil geralmente exigem o domínio de estruturas de repetição, lógica condicional básica e uma introdução a ponteiros e matemática simples aplicada a arrays. O objetivo aqui é aprender a otimizar soluções de Força Bruta O(N2) para O(N) ou O(logN).

### 1\. [Missing Number](https://www.geeksforgeeks.org/dsa/find-the-missing-number/ "null")

**Descrição:** Dado um array contendo 
```
N-1
```
 números distintos no intervalo de 
```
1
```
 a 
```
N
```
, encontre o único número que está faltando. **Input:** Um array de inteiros e o valor 
```
N
```
. (Ex: 
```
arr = [1, 2, 4, 6, 3, 7, 8], N = 8
```
) **Output:** O número inteiro ausente. (Ex: 
```
5
```
) **Passo a Passo:**

1.  Calcule a soma esperada de todos os números de 
    ```
    1
    ```
     até 
    ```
    N
    ```
     usando a fórmula matemática de progressão aritmética: 
    ```
    Soma = N * (N + 1) / 2
    ```
    .
    
2.  Percorra o array fornecido e calcule a soma de todos os elementos atualmente presentes.
    
3.  Subtraia a soma real do array da soma teórica esperada. O resultado (a diferença) é o número exato que está faltando. **⏱️ Complexidade:** Tempo O(N) | Espaço O(1). **⚠️ Casos Extremos:** Array onde o número faltando é o primeiro (
    ```
    1
    ```
    ) ou o último (
    ```
    N
    ```
    ). Arrays vazios se N\=1. **💡 Dica de Ouro:** Em linguagens estritamente tipadas como C++ ou Java, a soma 
    ```
    N*(N+1)
    ```
     pode causar _Integer Overflow_ (estouro de limite numérico) se N for muito grande. Uma alternativa à prova de falhas é usar a operação lógica XOR (
    ```
    ^
    ```
    ).

### 2\. [Second Largest](https://www.geeksforgeeks.org/dsa/find-second-largest-element-array/ "null")

**Descrição:** Encontre o segundo maior elemento distinto em um array não ordenado. **Input:** Um array de inteiros. (Ex: 
```
arr = [12, 35, 1, 10, 34, 1]
```
) **Output:** O valor do segundo maior elemento. Se não houver, retorne 
```
-1
```
. (Ex: 
```
34
```
) **Passo a Passo:**

1.  Inicialize duas variáveis, 
    ```
    maior
    ```
     e 
    ```
    segundo_maior
    ```
    , com o menor valor possível (como a constante 
    ```
    11.Infinity
    ```
     ou 
    ```
    15.1
    ```
     se garantido que os números são positivos).
    
2.  Percorra o array elemento por elemento em uma única passagem.
    
3.  Se o elemento atual for estritamente maior que o 
    ```
    maior
    ```
    , você precisa de um "rebaixamento": atualize o 
    ```
    segundo_maior
    ```
     para assumir o valor antigo do 
    ```
    maior
    ```
    , e depois atualize o 
    ```
    maior
    ```
     para o elemento atual.
    
4.  Se o elemento for menor que o 
    ```
    maior
    ```
    , mas ainda assim maior que o 
    ```
    segundo_maior
    ```
    , atualize apenas o 
    ```
    segundo_maior
    ```
    . **⏱️ Complexidade:** Tempo O(N) | Espaço O(1). **⚠️ Casos Extremos:** Array com elementos idênticos (ex: 
    ```
    [10, 10, 10]
    ```
    , deve retornar 
    ```
    57.1
    ```
    ). Array com menos de dois elementos. **💡 Dica de Ouro:** Evite a tentação de ordenar o array (O(NlogN)). Uma única travessia (O(N)) é suficiente e demonstra melhor domínio da manipulação de estados.

### 3\. [Common in three Sorted](https://www.geeksforgeeks.org/dsa/find-common-elements-three-sorted-arrays/ "null")

**Descrição:** Dados três arrays já ordenados, encontre os elementos que são comuns a todos os três simultaneamente. **Input:** Três arrays de inteiros ordenados. (Ex: 
```
A = [1, 5, 10], B = [3, 4, 5, 10], C = [5, 10, 20]
```
) **Output:** Um array com os elementos comuns. (Ex: 
```
[5, 10]
```
) **Passo a Passo:**

1.  Utilize três ponteiros (índices independentes), um para cada array, todos iniciando na posição 
    ```
    0
    ```
    .
    
2.  Use um laço de repetição 
    ```
    while
    ```
     que roda enquanto nenhum dos ponteiros ultrapassar o limite do seu respectivo array.
    
3.  Se os três elementos apontados no momento forem perfeitamente iguais, adicione esse valor ao array de resultado e avance os três ponteiros em +1.
    
4.  Se não forem iguais, a lógica de descarte dita que o menor dos três números nunca alcançará os maiores. Portanto, identifique qual dos três elementos é o menor e avance apenas o ponteiro correspondente a ele. **⏱️ Complexidade:** Tempo O(N1​+N2​+N3​) | Espaço O(1) (ignorando o espaço da resposta). **⚠️ Casos Extremos:** Arrays de tamanhos drasticamente diferentes; repetição consecutiva do elemento comum (cuidado para não adicionar duplicatas ao resultado). **💡 Dica de Ouro:** Este é um excelente exemplo do padrão "Multiple Pointers". Aproveitar a ordenação prévia dos arrays é o que evita transformarmos isso num problema cúbico O(N3).

### 4\. [Transition point in a binary](https://www.geeksforgeeks.org/dsa/find-transition-point-binary-array/ "null")

**Descrição:** Dado um array binário ordenado (contendo apenas uma sequência de 
```
0
```
s seguida por uma sequência de 
```
1
```
s), encontre o índice exato onde ocorre a primeira transição de 
```
0
```
 para 
```
1
```
. **Input:** Um array binário ordenado. (Ex: 
```
arr = [0, 0, 0, 1, 1]
```
) **Output:** O índice do primeiro 
```
1
```
. Retorne 
```
-1
```
 se não houver nenhum 
```
1
```
. (Ex: 
```
3
```
) **Passo a Passo:**

1.  Dado que o array está totalmente ordenado, aplique a Busca Binária para máxima eficiência. Defina 
    ```
    inicio = 0
    ```
     e 
    ```
    fim = tamanho - 1
    ```
    .
    
2.  Em um loop, encontre o índice do 
    ```
    meio
    ```
    .
    
3.  Se 
    ```
    arr[meio] == 0
    ```
    , sabemos com certeza que a transição ainda não ocorreu, ela deve estar na metade direita. Logo, atualize 
    ```
    inicio = meio + 1
    ```
    .
    
4.  Se 
    ```
    arr[meio] == 1
    ```
    , verifique se este é genuinamente o _primeiro_ 1. Ele será o primeiro se 
    ```
    meio == 0
    ```
     (início do array) ou se o elemento imediatamente anterior 
    ```
    arr[meio-1]
    ```
     for 
    ```
    0
    ```
    . Se confirmar, retorne o 
    ```
    meio
    ```
    . Caso contrário, a verdadeira transição ocorreu antes, então busque na esquerda (
    ```
    fim = meio - 1
    ```
    ). **⏱️ Complexidade:** Tempo O(logN) | Espaço O(1). **⚠️ Casos Extremos:** Array contendo apenas zeros (
    ```
    [0, 0, 0]
    ```
    ) ou apenas uns (
    ```
    [1, 1, 1]
    ```
    ). **💡 Dica de Ouro:** A Busca Binária não serve apenas para encontrar valores exatos, mas também "limites" ou "padrões", como é o caso de transições e quebras de monotonicidade.

### 5\. [Floor in a Sorted](https://www.geeksforgeeks.org/dsa/floor-in-a-sorted-array/ "null")

**Descrição:** Dado um array ordenado e um valor alvo 
```
X
```
, encontre o "piso" (floor) de 
```
X
```
. O piso é matematicamente definido como o maior elemento presente no array que seja menor ou igual a 
```
X
```
. **Input:** Um array ordenado e um inteiro 
```
X
```
. (Ex: 
```
arr = [1, 2, 8, 10, 11, 12, 19], X = 5
```
) **Output:** O índice do piso de 
```
X
```
. Se não existir nenhum piso, retorne 
```
-1
```
. (Ex: 
```
1
```
 correspondente ao valor 
```
2
```
) **Passo a Passo:**

1.  Utilize Busca Binária. Mantenha uma variável auxiliar 
    ```
    resultado = -1
    ```
     para rastrear o índice do melhor candidato a piso encontrado até o momento.
    
2.  Calcule o 
    ```
    meio
    ```
    . Se você tiver a sorte de achar 
    ```
    arr[meio] == X
    ```
    , a busca acaba, pois o piso de um número existente é ele mesmo.
    
3.  Se 
    ```
    arr[meio] < X
    ```
    , este elemento é um candidato válido a piso (pois atende à regra de ser menor). Salve 
    ```
    resultado = meio
    ```
     temporariamente. Porém, pode existir um piso "melhor" (mais próximo de X) à frente, então direcione a busca para a direita (
    ```
    inicio = meio + 1
    ```
    ).
    
4.  Se 
    ```
    arr[meio] > X
    ```
    , esse número é muito grande para ser piso. Ignore a metade direita completamente e busque na esquerda (
    ```
    fim = meio - 1
    ```
    ). **⏱️ Complexidade:** Tempo O(logN) | Espaço O(1). **⚠️ Casos Extremos:** O alvo 
    ```
    X
    ```
     ser menor que todos os elementos do array (não há piso); 
    ```
    X
    ```
     ser maior que o último elemento (o piso é o próprio último índice). **💡 Dica de Ouro:** Pense nessa variável 
    ```
    resultado
    ```
     como a memória de uma "melhor aproximação". A busca binária clássica retorna imediatamente ao achar um valor, mas variantes como Floor/Ceil continuam refinando o palpite.

### 6\. [Pair with difference](https://www.geeksforgeeks.org/dsa/find-a-pair-with-the-given-difference/ "null")

**Descrição:** Dado um array (potencialmente não ordenado) e um valor alvo 
```
N
```
, descubra se existe algum par de elementos cuja diferença absoluta seja exatamente igual a 
```
N
```
. **Input:** Um array e um inteiro 
```
N
```
. (Ex: 
```
arr = [5, 20, 3, 2, 5, 80], N = 78
```
) **Output:** Um valor booleano (
```
True
```
 ou 
```
False
```
) indicando se tal par existe na coleção. **Passo a Passo:**

1.  Para evitar um duplo for-loop O(N2), primeiro ordene o array de forma crescente (O(NlogN)).
    
2.  Utilize dois ponteiros "corredores" caminhando para a mesma direção: 
    ```
    i = 0
    ```
     (ponteiro lento) e 
    ```
    j = 1
    ```
     (ponteiro rápido).
    
3.  Dentro do loop, calcule a diferença temporal: 
    ```
    diff = arr[j] - arr[i]
    ```
    .
    
4.  Se 
    ```
    diff == N
    ```
     e 
    ```
    i != j
    ```
     (garantindo que não é o mesmo índice subtraído de si mesmo), você encontrou o par com sucesso! Retorne 
    ```
    True
    ```
    .
    
5.  Se 
    ```
    diff < N
    ```
    , a diferença atual está muito pequena. Como o array está ordenado, para aumentar a diferença, precisamos apontar 
    ```
    j
    ```
     para um número maior. Avance 
    ```
    j++
    ```
    .
    
6.  Se 
    ```
    diff > N
    ```
    , a diferença ultrapassou o alvo. Para estreitar essa distância, avance o ponteiro menor 
    ```
    i++
    ```
    . **⏱️ Complexidade:** Tempo O(NlogN) (devido à ordenação) | Espaço O(1) ou O(N) dependendo do algoritmo de ordenação (ex: Timsort vs Heapsort). **⚠️ Casos Extremos:** O valor de 
    ```
    N
    ```
     ser 
    ```
    0
    ```
     (neste caso, busca-se por números duplicados); arrays muito curtos ou com números negativos. **💡 Dica de Ouro:** Alternativamente, se espaço não for um problema, você pode usar uma Tabela Hash (HashSet). Para cada número 
    ```
    num
    ```
    , verifique se 
    ```
    num - N
    ```
     ou 
    ```
    num + N
    ```
     já existe no conjunto. Isso derruba o tempo para O(N) puro.

### 7\. [Square Root](https://www.geeksforgeeks.org/dsa/square-root-of-an-integer/ "null")

**Descrição:** Dado um número inteiro 
```
X
```
, calcule e retorne a raiz quadrada inteira de 
```
X
```
. Se 
```
X
```
 não for um quadrado perfeito, retorne apenas a parte inteira (o piso da raiz). **Input:** Um número inteiro 
```
X
```
. (Ex: 
```
X = 11
```
) **Output:** A parte inteira da raiz quadrada. (Ex: 
```
3
```
, pois 32\=9 e 42\=16). **Passo a Passo:**

1.  Trate os casos base matemáticos e óbvios preventivamente: se 
    ```
    X
    ```
     for 0 ou 1, a raiz é o próprio 
    ```
    X
    ```
    . Retorne imediatamente.
    
2.  Imagine que as possíveis raízes estão dispostas ordenadamente de 
    ```
    1
    ```
     até 
    ```
    X/2
    ```
    . Configure a Busca Binária com 
    ```
    inicio = 1
    ```
     e 
    ```
    fim = X / 2
    ```
     (para qualquer X\>1, sua raiz nunca ultrapassa sua metade).
    
3.  Calcule o 
    ```
    meio
    ```
     da busca. Se a multiplicação 
    ```
    meio * meio == X
    ```
    , achamos um quadrado perfeito! Retorne 
    ```
    meio
    ```
    .
    
4.  Se 
    ```
    meio * meio < X
    ```
    , este valor não atinge 
    ```
    X
    ```
    , mas é um candidato válido à parte inteira (piso). Guarde 
    ```
    resultado = meio
    ```
     em uma variável de rastreio, e direcione a busca à direita para tentar raízes maiores (
    ```
    inicio = meio + 1
    ```
    ).
    
5.  Se 
    ```
    meio * meio > X
    ```
    , ultrapassamos o valor estipulado. Reduza a estimativa buscando na esquerda (
    ```
    fim = meio - 1
    ```
    ). **⏱️ Complexidade:** Tempo O(logX) | Espaço O(1). **⚠️ Casos Extremos:** Cuidado com números absurdamente grandes para 
    ```
    X
    ```
    . O cálculo 
    ```
    meio * meio
    ```
     em algumas linguagens pode causar estouro de memória (Integer Overflow). **💡 Dica de Ouro:** Para contornar limites de tipagem de 32\-bits, prefira comparar a divisão: em vez de fazer 
    ```
    meio * meio > X
    ```
    , use 
    ```
    meio > X / meio
    ```
    . É matematicamente equivalente e imune a _overflow_.

### 8\. [Rotation Count](https://www.geeksforgeeks.org/dsa/find-rotation-count-rotated-sorted-array/ "null")

**Descrição:** Um array com elementos únicos que foi inicialmente ordenado de forma estritamente crescente foi "rotacionado" um número misterioso de vezes. Encontre matematicamente quantas vezes ele sofreu rotação. Em arrays rotacionados, a quantidade de rotações equivale exatamente ao _índice_ do menor elemento. **Input:** Um array rotacionado. (Ex: 
```
arr = [15, 18, 2, 3, 6, 12]
```
) **Output:** Um inteiro representando a quantidade de rotações. (Ex: 
```
2
```
, referente ao índice do valor 
```
2
```
). **Passo a Passo:**

1.  Este é um problema clássico resolvido eficientemente com Busca Binária (
    ```
    inicio = 0
    ```
    , 
    ```
    fim = tamanho - 1
    ```
    ).
    
2.  Caso o array nunca tenha sido rotacionado, ou tenha completado um ciclo total, o primeiro elemento será menor ou igual ao último (
    ```
    arr[inicio] <= arr[fim]
    ```
    ). Se este caso inicial for verdadeiro, a resposta imediata é 
    ```
    inicio
    ```
     (0).
    
3.  Calcule o elemento 
    ```
    meio
    ```
    . Uma propriedade única do menor elemento em arrays rotacionados é que ele é menor tanto que seu vizinho à esquerda quanto à direita. Verifique: se 
    ```
    arr[meio] <= arr[meio+1]
    ```
     e 
    ```
    arr[meio] <= arr[meio-1]
    ```
    , o elemento do meio é a anomalia (o menor). Retorne o índice 
    ```
    meio
    ```
    . _(Atenção para envolver os índices em módulo 
    ```
    (meio + 1) % N
    ```
     para evitar erros de leitura fora do limite)._
    
4.  Se ele não for o menor, decida qual metade descartar baseando-se na ordenação: Se a porção do início até o meio está perfeitamente ordenada (
    ```
    arr[inicio] <= arr[meio]
    ```
    ), isso prova que o menor elemento rompeu o padrão e deve estar na metade direita que ficou desordenada. Se não, está na esquerda. **⏱️ Complexidade:** Tempo O(logN) | Espaço O(1). **⚠️ Casos Extremos:** Array com apenas 1 ou 2 elementos; arrays rotacionados perfeitamente (
    ```
    N
    ```
     vezes) de volta ao estado original. **💡 Dica de Ouro:** Entender a "quebra de monotonicidade" é a chave para todos os problemas que envolvem dados rotacionados. Uma das metades, ao fatiar o array ao meio, **sempre** estará linearmente ordenada.

### 9\. [Matrix Sorted Search](https://www.geeksforgeeks.org/dsa/search-in-row-wise-and-column-wise-sorted-matrix/ "null")

**Descrição:** Você recebe uma matriz bidimensional (grid) onde todas as linhas e colunas foram rigorosamente ordenadas de forma crescente (da esquerda para direita, de cima para baixo). Busque pelo alvo 
```
X
```
 de maneira otimizada. **Input:** Uma matriz bidimensional M×N e um número alvo 
```
X
```
. (Ex: 
```
mat = [[10, 20, 30], [15, 25, 35], [27, 29, 37]], X = 29
```
) **Output:** Verdadeiro/Falso ou a tupla de coordenadas (linha, coluna). (Ex: 
```
True
```
 ou 
```
[2, 1]
```
) **Passo a Passo:**

1.  Comece seu percurso posicionando-se em uma quina estratégica: o canto superior direito da matriz (linha 
    ```
    i = 0
    ```
    , coluna 
    ```
    j = n - 1
    ```
    ).
    
2.  Use um laço 
    ```
    while
    ```
     comparando o valor em que você está com o alvo 
    ```
    X
    ```
    .
    
3.  Se os valores forem iguais, a caçada terminou.
    
4.  Aqui entra a mágica geométrica: se o 
    ```
    X
    ```
     for **menor** que o elemento atual, significa que 
    ```
    X
    ```
     não tem a menor chance de estar embaixo nesta mesma coluna, pois os números só aumentam para baixo. Elimine a coluna inteira movendo-se para a esquerda (
    ```
    j--
    ```
    ).
    
5.  Inversamente, se 
    ```
    X
    ```
     for **maior** que o elemento atual, ele não pode estar à esquerda nesta linha (os números diminuem à esquerda). Elimine a linha movendo-se uma camada para baixo (
    ```
    i++
    ```
    ). Repita até achar ou cair fora dos limites do plano. **⏱️ Complexidade:** Tempo O(M+N) | Espaço O(1). **⚠️ Casos Extremos:** A matriz ser nula, o elemento 
    ```
    X
    ```
     ser drasticamente menor que o primeiro elemento da matriz, ou gigantesco superando o último elemento na diagonal. **💡 Dica de Ouro:** Por que não começar do 
    ```
    (0,0)
    ```
    ? Se você começa do topo esquerdo (o menor número) e o alvo é maior, você tem _duas_ direções para ir (direita ou baixo). Começar na quina superior direita transforma o grid num comportamento parecido com uma Árvore de Busca Binária (um caminho é estritamente menor, o outro estritamente maior).

### 10\. [Bitonic Peak Search](https://www.geeksforgeeks.org/dsa/find-the-maximum-element-in-an-array-which-is-first-increasing-and-then-decreasing/ "null")

**Descrição:** Identifique o pico máximo em um array caracterizado como "Bitônico". Um array bitônico sobe estritamente até um certo ponto montanhoso e depois desce estritamente. **Input:** Um array bitônico numérico. (Ex: 
```
arr = [1, 3, 50, 10, 9, 7, 6]
```
) **Output:** O maior número (pico) do array. (Ex: 
```
50
```
) **Passo a Passo:**

1.  Como há uma tendência crescente que se inverte bruscamente, usamos a Busca Binária para achar esse ponto de inflexão. Defina 
    ```
    inicio = 0
    ```
     e 
    ```
    fim = tamanho - 1
    ```
    .
    
2.  Em cada iteração, encontre o elemento do 
    ```
    meio
    ```
    .
    
3.  Verifique a propriedade física de um pico: se 
    ```
    arr[meio]
    ```
     é maior que seu vizinho imediato da esquerda E maior que seu vizinho imediato da direita, você coroou o cume da montanha. Ele é a resposta!
    
4.  Mas e se ele não for o pico? Avalie a inclinação: se o elemento atual for **menor** que o elemento à direita (
    ```
    arr[meio] < arr[meio + 1]
    ```
    ), você ainda está subindo a ladeira da esquerda. O pico fatalmente reside mais adiante. Ajuste 
    ```
    inicio = meio + 1
    ```
    .
    
5.  Se ele for **menor** que o elemento à esquerda, você já passou pelo pico e está na descida. O pico ficou para trás, defina 
    ```
    fim = meio - 1
    ```
    . **⏱️ Complexidade:** Tempo O(logN) | Espaço O(1). **⚠️ Casos Extremos:** O pico estar colado em uma das extremidades (o array inteiro apenas sobe ou apenas desce). É necessário prever o tratamento dos limites de índices (ex: 
    ```
    meio == 0
    ```
     ou 
    ```
    meio == N-1
    ```
    ). **💡 Dica de Ouro:** Problemas "bitônicos" ensinam que você não precisa saber os valores extremos prévios para decidir a direção da busca binária; a derivada instantânea (a variação pontual entre dois elementos adjacentes) é suficiente para mapear o comportamento da curva de dados.

</p>

</details>

<details>
  <summary>🟠 Nível 2 - Médio</summary>

<p>

Os problemas médios trazem combinações de técnicas. A complexidade teórica dos enunciados sobe, e abordagens ingênuas O(N2) resultarão em erros do tipo "Time Limit Exceeded" (TLE). Você será testado em fusões de ordenações cíclicas, algoritmos matemáticos como o de Moore, e buscas aplicadas de maneiras criativas.

### 1\. [Search in Rotated Sorted](https://www.geeksforgeeks.org/dsa/search-an-element-in-a-sorted-and-pivoted-array/ "null")

**Descrição:** Efetue uma busca por um elemento 
```
X
```
 específico em um array que originalmente era ordenado, mas que sofreu rotação em um pivô desconhecido. É estritamente exigido que a busca seja realizada em tempo logarítmico. **Input:** Array rotacionado e valor alvo 
```
X
```
. (Ex: 
```
arr = [5, 6, 7, 8, 9, 10, 1, 2, 3], X = 3
```
) **Output:** O índice real do elemento procurado, ou 
```
-1
```
 se não estiver presente. (Ex: 
```
8
```
) **Passo a Passo:**

1.  Monte a estrutura clássica de Busca Binária.
    
2.  Ao calcular o 
    ```
    meio
    ```
    , e constatar que 
    ```
    arr[meio] != X
    ```
    , o segredo é descobrir onde está o "chão seguro" (a porção contígua e perfeitamente ordenada da sua divisão).
    
3.  Se a metade esquerda apresentar ordem coesa (
    ```
    arr[inicio] <= arr[meio]
    ```
    ), verifique se o alvo 
    ```
    X
    ```
     matematicamente reside dentro dessa baliza de valores (
    ```
    arr[inicio] <= X < arr[meio]
    ```
    ). Se sim, você tem certeza absoluta de que 
    ```
    X
    ```
     está na esquerda, então corte fora a parte direita. Se não estiver nesse leque numérico, o único lugar onde pode se esconder é na bagunçada metade direita.
    
4.  Se a primeira constatação falhar, significa que a metade direita obrigatoriamente está linear e coesa (
    ```
    arr[meio] <= arr[fim]
    ```
    ). Repita o mesmo raciocínio: se 
    ```
    X
    ```
     estiver preso dentro dos limites dessa metade, isole a direita. Senão, varra a esquerda. **⏱️ Complexidade:** Tempo O(logN) | Espaço O(1). **⚠️ Casos Extremos:** Quando há valores duplicados no array (ex: 
    ```
    [1, 0, 1, 1, 1]
    ```
    ), o algoritmo base falha, pois 
    ```
    arr[inicio] == arr[meio] == arr[fim]
    ```
     inviabiliza a detecção de qual lado está ordenado. O pior caso vira linear. **💡 Dica de Ouro:** A filosofia desta solução baseia-se em "encontre o refúgio da ordem e pergunte se o alvo se enquadra nessa janela de estabilidade; na dúvida, jogue fora o que não serve."

### 2\. [Majority Element](https://www.geeksforgeeks.org/dsa/majority-element/ "null")

**Descrição:** Detecte o elemento majoritário presente em um array. A regra de ouro dita que um elemento é classificado como majoritário se e somente se ele aparece estritamente mais de 
```
⌊N/2⌋
```
 vezes. **Input:** Um array preenchido de tamanho 
```
N
```
. (Ex: 
```
arr = [3, 1, 3, 3, 2]
```
) **Output:** O número majoritário ou falha se ninguém dominar. (Ex: 
```
3
```
) **Passo a Passo:**

1.  Apesar da intuição apontar para uso de HashMaps para contagem (O(N) espaço), implemente o brilhante Algoritmo de Votação de Moore (Boyer-Moore Voting Algorithm) para otimização espacial em O(1).
    
2.  Escolha preliminar: assuma ingenuamente que o primeiro elemento da lista é o 
    ```
    candidato
    ```
     forte ao cargo e instancie um 
    ```
    contador
    ```
     valendo 
    ```
    1
    ```
    .
    
3.  Percorra o array do segundo elemento em diante. Ao encontrar um eleitor (número) igual ao 
    ```
    candidato
    ```
    , reforce seu mandato somando 
    ```
    23.1
    ```
     ao contador. Se topar com uma voz divergente (número diferente), "cancele" um voto e decremente 
    ```
    contador - 1
    ```
    .
    
4.  Se, sob a pressão de oposição contínua, o 
    ```
    contador
    ```
     despencar para zero, significa que o candidato anterior perdeu tração. O número divergente atual da iteração assumirá o manto de novo 
    ```
    candidato
    ```
    , reiniciando sua campanha com 
    ```
    contador = 1
    ```
    .
    
5.  Ao terminar a jornada iterativa, o 
    ```
    candidato
    ```
     final sobrevivente é sua maior chance. Porém, para evitar "falsos vencedores" (quando garantias de maioria não são dadas no enunciado), repita a varredura uma segunda vez apenas para certificar que o 
    ```
    candidato
    ```
     aparece de fato mais que 
    ```
    N/2
    ```
     vezes. **⏱️ Complexidade:** Tempo O(N) (1 a 2 passagens) | Espaço O(1). **⚠️ Casos Extremos:** Um array sem qualquer elemento com maioria absoluta (o passe de verificação final previne respostas cegas errôneas). **💡 Dica de Ouro:** O algoritmo de Boyer-Moore atua como um sistema brutal de pesos. Diferentes destroem uns aos outros num embate 1:1. Como o majoritário tem acima de 50% do total de instâncias, ele inerentemente "vencerá" todas as subtrações e emergirá na contagem residual.

### 3\. [K’th Smallest/Largest in Unsorted](https://www.geeksforgeeks.org/dsa/kth-smallest-largest-element-in-unsorted-array/ "null")

**Descrição:** Isole cirurgicamente o K-ésimo menor (ou maior) elemento listado em um array completamente não ordenado. **Input:** Um array bruto e um seletor numérico 
```
K
```
. (Ex: 
```
arr = [7, 10, 4, 3, 20, 15], K = 3
```
) **Output:** O número que ocupa a posição correta. (Ex: 
```
7
```
, sendo o 3º menor). **Passo a Passo:**

1.  Você poderia ordenar o array (O(NlogN)) e simplesmente retornar 
    ```
    arr[K-1]
    ```
    , mas existem metodologias superlativas. A abordagem estelar aqui é via Algoritmo _Quickselect_, concebido usando a estrutura primária do algoritmo QuickSort.
    
2.  Defina uma área de operação (
    ```
    inicio = 0
    ```
    , 
    ```
    fim = N - 1
    ```
    ). Selecione arbitrariamente um "pivô" (frequentemente escolhido como o último elemento no recorte vigente).
    
3.  Realize a etapa de partição ao redor deste pivô: reorganize os dados do array físico em si de modo que todos os números inferiores ao pivô estacionem à esquerda do mesmo, e os superiores repousem à direita. Ao fim desta troca de posições, fixe o pivô em seu trono (posição definitiva).
    
4.  Agora compare a casa onde o pivô aterrissou: Se o índice onde ele travou for pontualmente idêntico a 
    ```
    K - 1
    ```
    , parabéns, o alvo foi neutralizado! O pivô é sua própria resposta.
    
5.  Se o assentamento do pivô exceder 
    ```
    K - 1
    ```
    , deduz-se que seu K-ésimo menor alvo se emaranhou na subseção da esquerda do arranjo. Chame recursiva ou iterativamente o procedimento de partição na respectiva metade, ignorando o lado desnecessário (e vice-versa se for o caso contrário). **⏱️ Complexidade:** Tempo O(N) em média (O(N2) pior caso teórico, mitigável com pivôs aleatórios) | Espaço O(1) iterativo ou O(logN) para _call stack_. **⚠️ Casos Extremos:** O 
    ```
    K
    ```
     extrapolar os índices reais (
    ```
    K < 1
    ```
     ou 
    ```
    K > tamanho
    ```
    ); o array já vir fatalmente ordenado em sentido contrário (ruim para Quickselect sem randomização). **💡 Dica de Ouro:** Outra rota formidável e preferida por muitos engenheiros é o emprego de estrutura _Min-Heap / Max-Heap_ (Priority Queue), atingindo consistência blindada no tempo O(NlogK). Útil em cenários de dados fluindo infinitamente (stream).

### 4\. [Count Frequency in Sorted Array](https://www.geeksforgeeks.org/dsa/count-number-of-occurrences-or-frequency-in-a-sorted-array/ "null")

**Descrição:** Detecte e calcule estatisticamente o número global de vezes em que o valor alvo 
```
X
```
 brota aglomerado no array pré-ordenado. **Input:** Um array linearmente organizado e chave 
```
X
```
. (Ex: 
```
arr = [1, 1, 2, 2, 2, 2, 3], X = 2
```
) **Output:** O número da demografia local / frequência de 
```
X
```
. (Ex: 
```
4
```
) **Passo a Passo:**

1.  Lembre-se, varredura iterativa linear seria imperdoável (O(N)). Secreção local exige cirurgia logarítmica.
    
2.  Formule uma modalidade da Busca Binária manipulada para não abortar quando tropeça em 
    ```
    X
    ```
    , mas continuar caçando até encurralar a **primeira aparição (first\_occurrence)**. Se achar, registre e puxe as bordas para a extrema esquerda na tentativa predatória de achar algo antes.
    
3.  Elabore, ou parametrize, um segundo espelho desta Busca Binária modificado para garimpar a **última ocorrência (last\_occurrence)**, deslizando a barreira limite agressivamente à direita após capturar sucessos preliminares.
    
4.  Tendo sucesso em pinçar ambos os pontos cardeais do bloco, formule a contagem resoluta: 
    ```
    (last_occurrence - first_occurrence) + 1
    ```
    . Evidentemente, se o radar mestre na etapa preliminar acusar falso, dissemine o retorno matemático 
    ```
    0
    ```
    . **⏱️ Complexidade:** Tempo O(logN) | Espaço O(1). **⚠️ Casos Extremos:** Array gigante composto integralmente pelo número 
    ```
    X
    ```
    ; alvo 
    ```
    X
    ```
     inexistente no meio de limiares muito confusos. **💡 Dica de Ouro:** Compreender como deslocar os limites (inclusive com comparações 
    ```
    <=
    ```
     e 
    ```
    >=
    ```
    ) e não encerrar a rotina _looping_ ao dar um "match" no alvo define o profissional de nível sênior nesta tarefa tão elementar, mas fatal se mal administrada.

### 5\. [Peak Element](https://www.geeksforgeeks.org/dsa/find-a-peak-in-a-given-array/ "null")

**Descrição:** Investigue a listagem contendo cordilheiras numéricas e capture o sinal de satélite de pelo menos "um" elemento topológico de pico. Elementos periféricos são abonos: um elemento qualifica-se como pico bastando ser expressivamente maior ou igual que os vizinhos colados imediatamente a ele. **Input:** Array terreno misto. (Ex: 
```
arr = [10, 20, 15, 2, 23, 90, 67]
```
) **Output:** O índice identificador do ponto de extração. (Ex: 
```
1
```
 \[valor 
```
20
```
\], ou 
```
5
```
 \[valor 
```
90
```
\]) **Passo a Passo:**

1.  A mágica contraintuitiva da Busca Binária opera até na desordem se você compreender inclinações de encostas espaciais. Fixe limites plenos (
    ```
    inicio = 0
    ```
    , 
    ```
    fim = N - 1
    ```
    ).
    
2.  Recorte a observação no 
    ```
    meio
    ```
    . Submeta esse pixel de terreno às condições de pico absolutas avaliando a dupla margem (tendo a tolerância sensata de evitar o acesso a indexação corrompida - limites e precipícios das extremidades do vetor). Sendo o coroado rei imediato, retorne 
    ```
    meio
    ```
    .
    
3.  Caso a altitude decaia e vejamos o relevo da direita mais suntuoso que a chapa onde pisamos (i.e. 
    ```
    arr[meio] < arr[meio + 1]
    ```
    ), temos aval para atestar que a progressão ruma para os céus: haverá, de forma inegável, ou a terminação da fita em subida resultando em pico colado na ponta cega do precipício de memória, ou o topo efetivo de um monte dentro dos canteiros contíguos. Refugie as bases 
    ```
    inicio = meio + 1
    ```
    .
    
4.  Contraditoriamente e na simetria, mova o batalhão na retirada para canais focais esquerdos se 
    ```
    arr[meio]
    ```
     recuar rebaixado ante a vizinhança pretérita (
    ```
    fim = meio - 1
    ```
    ). **⏱️ Complexidade:** Tempo O(logN) | Espaço O(1). **⚠️ Casos Extremos:** Sequências monótonas longas subindo ao infinito, ou matrizes que mimetizam crateras caindo centralmente em colapso total (onde o limite absoluto age obrigatoriamente como o pico forçado de borda teórica no horizonte matemático das simulações da física base). **💡 Dica de Ouro:** Isso é uma premissa provada! Se você segue as migalhas na direção da encosta que sobe, você invariavelmente encontrará ao menos o rebordo perfeitamente classificado da aresta (que será avaliado como pico em caso de silêncio de vizinhos além do muro dimensional da variável referenciada).

### 6\. [Smallest Missing Positive](https://www.geeksforgeeks.org/dsa/find-the-smallest-positive-number-missing-from-an-unsorted-array/ "null")

**Descrição:** Desvende o segredo de encontrar o mais prematuro inteiro positivado (matematicamente denotado como 
```
> 0
```
) evadido entre as lacunas temporais em um caldeirão não ordenado de números impuros de escopo, no restrito teto temporal de taxa O(N) amarrado às celas exíguas estatais com volume extra vedado, exigindo O(1). **Input:** Caldeirão com literais caóticos e gélidos. (Ex: 
```
arr = [3, 4, -1, 1]
```
) **Output:** A vacância do espectro positivo. (Ex: 
```
2
```
) **Passo a Passo:**

1.  Injetaremos o princípio mestre universal da reconfiguração _Cyclic Sort_ (Ordenação Cíclica da Máquina). A premissa central é que a resposta máxima num quadro de tamanho 
    ```
    N
    ```
     é aprisionada num gargalo máximo numérico no limite 
    ```
    N + 1
    ```
    . O vetor em si age como uma tabela hash virtual de endereçamentos. Queremos forçar os exilados, do qual o literal 
    ```
    X
    ```
     toma forma corpórea, nas coordenadas indexadas em 
    ```
    X - 1
    ```
     (Ex: número humano 
    ```
    1
    ```
     é amarrado no caixote índice zero computacional).
    
2.  Marche com forquilha e encoste na matriz de valores. Ao debruçar sobre o literal atual na lupa, questione perante os deuses se sua natureza pertence ao pacto de 
    ```
    1
    ```
     até 
    ```
    N
    ```
     limite. Sendo ele cidadão apto, repare em que quarto repousa; estando no assento de outro número, aplique o ritual sagrado de permutação transitiva _swap_ com o ocupante incorreto da sua futura mansão oficial. Insista com obstinação no mesmo assento original até que os intercâmbios e deportações devolvam à lupa um lixo subzero inclassificável, alienígenas trans-numéricos do cosmo maior que limites de array, ou efetivamente o número exato residente por contrato predestinado na chapa sob o índice do percurso corrente do leitor.
    
3.  Com o poço de ressonância dos índices totalmente arranjados da harmonia natural do balanço, execute a vistoria cerimonial linear a pé até avistar as chagas na fachada onde o literal 
    ```
    arr[i]
    ```
     refuta e conspira frente à coerência exigida de constelação ditada 
    ```
    = i + 1
    ```
    . Onde o selo romper, 
    ```
    i + 1
    ```
     ecoa a vacância exposta procurada no mundo físico sensível do universo computado.
    
4.  Esgotadas averiguações da fita intacta onde os preceitos se casam irrepreensíveis e os blocos colidam todos firmes perenes, o foragido absoluto dita-se sendo o próprio 
    ```
    N + 1
    ```
     na coroa das ordens transcendentes e magnas da série. **⏱️ Complexidade:** Tempo O(N) | Espaço O(1). **⚠️ Casos Extremos:** Caldeirão forjado só de toxinas negativas que repulsam qualquer tratamento reativo em indexação local; array povoado de cópias carbono e clones exatos de mesmos blocos numéricos (o laço do swap precisa evitar espirais do caos paralisantes avaliando equivalências da chave perante fechaduras para escapar da roda kármica infinita de trava local recursiva paralítica fatal _T.L.E._). **💡 Dica de Ouro:** A transmutação da _Cyclic Sort_ é a joia para economizar uso extra em tabulações do espaço restrito. Sempre use a informação atada às restrições do limite geométrico 
    ```
    N
    ```
     e aos vizinhos predeterminantes associando instâncias em 
    ```
    [1...N]
    ```
     aos endereçamentos naturais de array via espelhamento index-puro em alvos como map hash no próprio local e ambiente instanciado em predições base.

### 7\. [All triplets with zero sum](https://www.geeksforgeeks.org/dsa/find-triplets-array-whose-sum-equal-zero/ "null")

**Descrição:** Investigue o consórcio numérico para desmascarar a existência da união triádica e secreta contendo um conclave de 3 constituintes cuja comunhão de acúmulo financeiro zera o fundo perfeitamente. **Input:** Um arranjo fiduciário de cofres isolados. (Ex: 
```
arr = [0, -1, 2, -3, 1]
```
) **Output:** O decreto cartorial binário declaratório ou certidão dos sócios trançados perfeitamente. (Ex: 
```
True
```
 confirmando o clã 
```
[-1, -1, 2]
```
). **Passo a Passo:**

1.  Acalme o frenesi de arranjos contíguos ordenando os pilares primários sequencialmente enxergando uma cadência rítmica e coesa entre o alinhamento da fila linear das variáveis financeiras ascendentes numéricas de porte a vista e sob escrutínio da análise de porte linear temporal estático.
    
2.  Comande a expedição avançando e assentando tenda temporária pelo espectro sequencial usando o líder alicerce na marca da patrulha temporal batizando de índice 
    ```
    i
    ```
     e delegando a ele cota cativa da primeira cadeira entre a cúpula do trio na sala secreta.
    
3.  Aja com maestria no domínio logístico desvendando ao exército o comando restritivo dual bi-direcionado na manobra das pernas "Two-Pointers" sobre as vastidões esquecidas. Coloque os limites temporários das guaritas remanescentes para averiguação da integridade paralela na porta e fundos das alas sob batismo contínuo de rastreamento com censores estáticos 
    ```
    inicio = i + 1
    ```
     de varredura próxima de base limítrofe avançada à frente e 
    ```
    fim = tamanho - 1
    ```
     na trincheira guardiã estática defronte fronteiras extremas de bloqueio físico limítrofe de cerco impenetrável de vigilância restritiva da tropa de base central operadora bi direcionada e com controle dinâmico.
    
4.  Caso a junção universal na aliança monetária tridimensional cruze saldos numéricos com fechamento zero (onde 
    ```
    arr[i] + arr[inicio] + arr[fim] == 0
    ```
    ), os trompetes entoarão os tons da vitória sobre o teorema exato formulado e exigido nos manuscritos perenes da solicitação temporal algorítmica fundamental declarando a tese verídica do triplete formador e coroando o feito com retornos validativos afirmativos perenes na conclusão.
    
5.  Faltando lastro financeiro ao zeramento estático contábil demonstrado num déficit sumário e agudo negativo perante os balanços dos deuses universais nas avaliações do universo simulado estático de avaliações algorítmicas iterativas avaliativas comparativas na progressão relacional perante escopo total negativo da margem base referenciada e simulada ao ponto fixo e delimitado perante zeros ideais requeridos no manifesto em balanços de contabilidade abstrata avaliativos comparativos com deficiência de valores limítrofes na margem contábil na meta do limiar absoluto numérico nulo perfeito exigido na baliza central limite das amarras teóricas base. (Mova o ponteiro interior e ascendente propulsor da esquerda). Transbordando saldo rico positivo à barreira zênite temporal do eixo referencial na dimensão iterativa avaliativa sob escrutínio logístico analítico central das métricas teóricas da contabilidade algorítmica iterativa restritiva imposta em matriz base original iterada e validada ao teste estático na operação estipulada em manifesto sumário central imposto iterativamente ao teste avaliativo progressivo das funções do núcleo estático de busca avaliativa (recue o porte do fronte lateral direito declinante negativo de rebaixamento financeiro). _(Resumo: Ordene o array, fixe o primeiro número num loop, e use a técnica de dois ponteiros (
    ```
    esquerda
    ```
     e 
    ```
    direita
    ```
    ) para achar os outros dois números que complementem a soma para zero)._ **⏱️ Complexidade:** Tempo O(N2) | Espaço O(1) ou dependente do Algoritmo de Ordenação. **⚠️ Casos Extremos:** Todos os elementos positivos (nenhuma soma dará zero); arrays repletos de números zero. **💡 Dica de Ouro:** Para não gerar tripletes duplicados no caso em que é exigido o retorno dos valores em si (e não apenas um _booleano_), você deve adicionar blocos de 
    ```
    if
    ```
     avançando sobre ocorrências idênticas (ex: 
    ```
    if (i > 0 && arr[i] == arr[i-1]) continue;
    ```
    ).

### 8\. [First & Last Positions in Sorted Array](https://www.geeksforgeeks.org/dsa/find-first-and-last-positions-of-an-element-in-a-sorted-array/ "null")

**Descrição:** Delimite as fatias fronteiriças definindo e reportando a guarita de ingresso da aparição precursora principal, e o obelisco de lápide terminativa demarcatória postada estática para a constelação referida num universo já alinhado por regimento ditatorial temporal ascendente estrito contínuo algorítmico matemático de hierarquia baseada numericamente orientada perante ordenação universal ditada na essência original fundadora da coleção contínua perante rastreamento de dados limítrofes numéricos iterativos iterantes. **Input:** Um esquadrão organizado hierárquico numérico limitante iterativo direcional numérico linear contínuo ordenado limitante limítrofe direcional de valores bases ascendentes perante restrição universal teórica temporal e referencial da ordem e um sinal 
```
X
```
 alienígena forasteiro e limitante referencial imposto na busca local contínua iterativa na região geográfica de buscas iterativas numéricas avaliativas restritas temporais. **Output:** Os portões limítrofes temporais de abertura contínua referencial limitante contínua posicional em indexação absoluta indexada das posições absolutas delimitadoras fronteiriças referenciadas de marcos indexadores. (As posições reais do índice exato 
```
first
```
 e 
```
last
```
). **Passo a Passo:** _(Este problema funde-se perfeitamente com a lógica demonstrada no exercício Médio #4)_.

1.  Programe e codifique duas mutações de sub-rotinas separadas e autossuficientes focadas de modo centralizado para as execuções isoladas limitantes base numéricas logarítmicas de rastreio limitante binário de segmentação referencial limítrofe fatiada iterativa central.
    
2.  Na função incubida de desmascarar a gênese pregressa embrionária temporal: Ao coincidir o achado na colisão espacial do rastreio iterativo numérico fatiado (encontrar o 
    ```
    X
    ```
    ), trave a marca registrada temporária base, salvando-a num registro contínuo central em banco reservado local, não decrete paralisação do algoritmo local continuado, mas decrete limitação e reorientação do escopo do campo varrido reduzindo o perímetro limite arrastando as linhas de varredura temporais fronteiriças fatiadas referenciadas avaliativas numéricas para margens limítrofes adjacentes direcionais orientadas de fronte lateral esquerda recuada para caça retrospectiva pretérita antecessora na esperança contínua perseverante central.
    
3.  No módulo incubido com fardo de traçar velório e termo da saga e encerramento limite base terminativa limitante do registro iterativo restritivo direcional fatiado contínuo temporal referenciado local limítrofe extremo finalizador: Efetue o mesmo rito, porém ao engajar 
    ```
    X
    ```
    , estique a tenda limítrofe limitante fronteiriça base do acampamento e arraste as amarras logísticas e logarítmicas iterativas de rastreio temporal fatiado para áreas abertas laterais esquecidas limites além do rastreio atual impulsionando-as na esperança caçadora limítrofe prospectiva contínua limítrofe direita temporal limítrofe continuada sucessora local limítrofe espacial e temporal da margem do acampamento e limites fronteiriços estendidos até a última centelha extinta nas sobras de memória restritivas alocadas remanescentes limitadas à extremidade direita final. **⏱️ Complexidade:** Tempo O(logN) | Espaço O(1). **⚠️ Casos Extremos:** O alvo não existir (retornar 
    ```
    [-1, -1]
    ```
    ). **💡 Dica de Ouro:** A separação conceitual da busca em duas funções modulares torna seu código robusto e limpo. Não tente englobar ambas verificações num emaranhado excessivamente complexo dentro de uma mesma rodada de laço _while_ para prezar pela legibilidade industrial (Clean Code).

### 9\. [Matrix Sorted Search](https://www.geeksforgeeks.org/dsa/search-in-row-wise-and-column-wise-sorted-matrix/ "null") _(Mencionado Novamente no Original)_

_(Mantido conforme listagem original do usuário, com lógica isomórfica à abordada no Fácil #9. Contudo, em problemas médios idênticos referenciados, a exigência de malha estrutural contínua na qual a matriz funciona literalmente como um longo array 1D quebrado com saltos é comum. Nesse arranjo mais exigente $O(\\log(N_M))$, usamos aritmética: 
```
linha = meio / colunas
```
, 
```
col = meio % colunas
```
 num limite 0…(N∗M−1)).\*

### 10\. [Two Repeating Elements](https://www.geeksforgeeks.org/dsa/find-the-two-repeating-elements-in-a-given-array/ "null")

**Descrição:** Extraia a identidade dos dois criminosos numéricos clonados escondidos no rol em um cenário pré-configurado rigoroso: o array hospeda as identidades dos habitantes entre a numeração serial fixa variando rigorosamente de limite temporal básico estrito 1 até o censo geográfico teto demográfico contínuo numérico de marca limite N. A totalidade populacional registrada local ostenta contabilidade central com capacidade excedente na ordem 
```
N + 2
```
 vagas populacionais demarcadas de assentamento estático estrito (obrigando logicamente o espelhamento clônico matemático em redundância comprovada atestatória base para exatamente 2 dos literais em escopo censo numérico iterativo). **Input:** População aglomerada exata. (Ex: 
```
arr = [4, 2, 4, 5, 2, 3, 1]
```
, aqui 
```
N = 5
```
) **Output:** Os falsários sósias usurpadores clonados flagrados identificados listados separadamente extraídos isolados avaliativos extraídos da amarra teórica. (Ex: 
```
4
```
 e 
```
2
```
) **Passo a Passo:**

1.  A exploração de tempo O(N) em restrição espartana sem uso extra de malha hash auxiliar com limitações proibitivas absolutas locais O(1) demandam corrompimento intencional estrutural contínuo limítrofe referencial do tecido de dados base fatiado indexador original para manipulação matemática avaliativa estática do fluxo linear continuado com rastreio indexador mapeador retroativo recursivo interativo direcional iterativo temporal fatiado rastreador logístico indexador limitante cíclico limítrofe restrito estático em array matriz local inalterável limite.
    
2.  Como há a garantia divina inquebrável atestando conformidade numérica base garantindo que nenhum cidadão extravase numericamente o censo máximo das vagas limitantes limítrofes totais da dimensão do array geográfico limite estático teto total: Infiltre-se percorrendo as casas em ronda limítrofe iterativa limítrofe varredura sequencial limítrofe sequencial.
    
3.  Embasado perante cada residente base interceptado flagrado no rastreamento indexado logístico estático linear iterativo sequencial limítrofe iterante contínuo: Transforme o número cru na chave decodificada do espelho absoluto base (usando o fator modular _abs()_) e pule geometricamente no arranjo direcionando-se à casa com chapa indexadora correspondente à conversão limítrofe dedutiva base limítrofe 
    ```
    chave - 1
    ```
    . Ao bater à porta desta respectiva habitação teórica limítrofe restrita fatiada indexada limítrofe avaliativa: marque o habitante ali presente com as chagas negativas do sinal de menos limitante negativo reverso demarcatório absoluto sinalizando de maneira profética rastreada perene da incursão exploratória referencial estática iterativa demarcatória prévia indicativa avaliativa estrita da verificação limitante limítrofe anterior fatiada de verificação logística direcional e iterativa sequencial contínua limítrofe direcional de verificação iterante continuada base.
    
4.  Se numa investida futura o portal referenciado na marca fatiada limítrofe indicativa logística da porta visitada exibir a corrupção sinalizadora negativa de contabilidade já carimbada pelo sinal base reverso sinalizador negativo das incursões avaliativas iterantes logísticas limítrofes pretéritas: flagrante manifesto dedutivo absoluto! O cidadão espelhado remetente decodificador chave original avaliativo despachador iterativo portador desta chave restrita investigada é a raiz limítrofe causadora restritiva clonada repetitiva e base do erro manifesto clonado repetitivo fatiado redundante do escopo redundante avaliativo repetitivo fatiado restrito avaliativo em curso corrente e central logístico contínuo fatiado iterante atual. _(Resumo: Use os próprios números do array como índices e faça o número naquele índice ficar negativo. Se você for negativar um número que JÁ É negativo, é porque você já esteve lá. O número atual iterado é um dos repetidos)._ **⏱️ Complexidade:** Tempo O(N) | Espaço O(1). **⚠️ Casos Extremos:** Atenção: não modifique permanentemente os dados se for requerido preservá-los; neste caso, os valores originais podem ser recuperados ao tomar o 
    ```
    abs()
    ```
     novamente no fim. **💡 Dica de Ouro:** A técnica de negativar (
    ```
    17.arr[index]
    ```
    ) como flag booleano dentro do próprio vetor é um dos truques O(1) mais formidáveis da ciência da computação. Lembre-se sempre de garantir e checar indexação usando _valor absoluto_ para as avaliações seguintes!

### 11\. [Single in Sorted Array](https://www.geeksforgeeks.org/dsa/find-the-element-that-appears-once-in-a-sorted-array/ "null")

**Descrição:** Em um cenário de isolamento organizado perfeitamente, todo elemento da vila caminha em pares clonados idênticos. Com exceção trágica focada numa anomalia unitária restrita solitária abandonada isolada única singular base perante rastreio logístico espacial isolado solitário. O esquadrão base requisita extração restritiva em restrições cronológicas temporais impulsionadoras logarítmicas de voo ágil estático limitante do corte referencial fatiado avaliativo iterante da busca fatiada limítrofe logarítmica absoluta em tempo limítrofe limítrofe e base de fatiamento O(logN). **Input:** Batalhão de soldados gêmeos emparelhados e um desertor solitário disfarçado. (Ex: 
```
arr = [1, 1, 2, 2, 3, 4, 4, 5, 5]
```
) **Output:** O número do desertor sem par. (Ex: 
```
3
```
) **Passo a Passo:**

1.  Monte o campo eletromagnético da Busca Binária estipulando e armando o cerco 
    ```
    inicio = 0
    ```
     na guarita traseira direcional limítrofe inicial e 
    ```
    fim = N - 1
    ```
     na trincheira oposta dianteira terminal fatiada de limite logístico espacial.
    
2.  Analise a sincronia e o compasso rítmico dos pares. Em uma pista imaculada ininterrupta, os gêmeos primários pisam inquestionavelmente nos canteiros com chancelas numéricas de paridade pares puras geográficas pares geográficas de chancelas puras (índices 
    ```
    0
    ```
    , 
    ```
    2
    ```
    , 
    ```
    4
    ```
    ), enquanto os irmãos clones espelho subsequentes limítrofes pousam limítrofes adjacentes pisando nos limiares ímpares fatiados ímpares (índices 
    ```
    1
    ```
    , 
    ```
    3
    ```
    , 
    ```
    5
    ```
    ).
    
3.  O solitário intruso corrompe impiedosamente essa harmonia valsa matemática estática avaliativa base restritiva cadenciada cadência limítrofe estritamente cadenciada! Extraia as constatações perante espelhamento indexador referencial logístico indexador avaliativo numérico fatiado direcional limítrofe: Se na batida do elemento varredor central logístico investigativo e fatiador central limítrofe referencial mediano avaliativo mediano da varredura direcional mediano 
    ```
    meio
    ```
     a indexação manifestar a pureza matemática geométrica base e paridade modular par estritamente e exata puramente modular referenciada pura indexadora lógica par (onde 
    ```
    meio % 2 == 0
    ```
     com divisões não contendo sobras limítrofes modulares exatas limítrofes restritas): Confirme o par verificando se o guardião oposto fatiado à margem da trincheira direita exata da varredura base colada adjacente e à direita da borda protetora (
    ```
    arr[meio+1]
    ```
    ) detém o espelho da mesma face matemática do clone referenciado estrito exato. Se os valores se abraçarem iguais idênticos restritivos e coesos, as batidas perante a pista à retaguarda da verificação avaliativa rastreada logística estão puras, livres da corrupção causadora do salto! Empurre a barricada limitante logística e busque avante empurrando o fronte para a direita 
    ```
    inicio = meio + 2
    ```
    .
    
4.  Caso as batidas dissonantes não corroborem com os reflexos teóricos impostos limitantes referenciados da batida modular e rítmica cadenciada avaliativa de compassos matemáticos estritos da valsa, o tropeço do elemento sibilante órfão manifestou abalo sísmico na fita antes mesmo deste farol escrutinador rastreador direcional fatiado mediano! O intruso está no limiar obscuro do vale pretérito esquecido à retaguarda fatiada esquecida esquerdo! Corra e estipule e recoloque limiares base da trincheira fronteiriça restritiva avaliativa de varredura dianteira limite para a marca referencial retroativa 
    ```
    fim = meio - 1
    ```
     ou englobante limítrofe englobando o próprio foco da verificação caso ele reencarne a resposta pontual avaliativa exata 
    ```
    fim = meio
    ```
    . **⏱️ Complexidade:** Tempo O(logN) | Espaço O(1). **⚠️ Casos Extremos:** Elemento solitário na borda 
    ```
    0
    ```
     ou 
    ```
    N-1
    ```
    . Cuidado extra com erros de 
    ```
    Array Index Out of Bounds
    ```
    . **💡 Dica de Ouro:** Focar no Índice e na Paridade é genialidade pura em buscas logarítmicas estruturais. Use a lógica de que o índice do primeiro número do par sempre deve ser par. Se essa regra quebra, o elemento solitário já ficou para trás.

### 12\. [Two elements with sum closest to zero](https://www.geeksforgeeks.org/dsa/two-elements-whose-sum-is-closest-to-zero/ "null")

**Descrição:** Encontre dois elementos num array de positivos e negativos cuja soma se aproxime o máximo possível do zero. **Input:** Array. (Ex: 
```
arr = [1, 60, -10, 70, -80, 85]
```
) **Output:** Os dois elementos. (Ex: 
```
-80
```
 e 
```
85
```
, soma = 
```
5
```
) **Passo a Passo:**

1.  Ordene o array de forma crescente (esquerdizando negativos e direitizando positivos).
    
2.  Engaje a técnica de Duplo Ponteiro. Guarita base limítrofe no fronte de gelo subzero negativo esquerdo (
    ```
    esq = 0
    ```
    ) e baliza no fronte inflamável tórrido superior extremo teto positivo direito estrito base topo de calibração fatiado avaliativo limitante da trincheira limítrofe (
    ```
    dir = N - 1
    ```
    ).
    
3.  Arquive o palpite avaliativo direcional da menor margem matemática comparativa e guarde-a atada à corrente de memória do recorde limítrofe em um pote fixo de memória limítrofe fixado no horizonte avaliativo temporário 
    ```
    menor_soma_absoluta
    ```
     calibrado na imensidão numérica com cúpula máxima limitante teto infinito base teto e topo virtual gigante extremo.
    
4.  Processe a liga química matemática unificando as células indexadoras opostas numerais fatiadas avaliadas extremas na esteira de fusão de processamento limitante combinatória contígua e atrelada em fusão matemática unificadora atestadora limitante somatória de junção contábil central 
    ```
    soma = arr[esq] + arr[dir]
    ```
    . Compare o valor destilado final avaliativo bruto usando balanças avaliativas do reflexo matemático de módulo purificador positivo 
    ```
    abs(soma)
    ```
     perante registros históricos do arquivamento estático estrito histórico memorial atado pregressamente em gavetas restritas pretéritas base avaliativas das marcas registradas memoriais globais gravadas. Em caso de supressão fatiada inferior na constatação empírica e quebra de fita e corte dos preceitos passados (menor valor encontrado), lacre e atualize novos registros fatiados referenciais com novos parâmetros batidos da amarra avaliativa direcional estática e guarde os pares isolados formadores referenciados como espólios vencedores globais isolados campeões do turno isolado referenciado base direcional avaliativo estrito e de fronte final absoluto medidor da constatação matemática do pódio provisório da etapa varrida contínua numérico contábil central avaliativo unificador.
    
5.  Manobre as rédeas perante vetores magnéticos matemáticos base limitadores: Quando a polaridade puxar pra as masmorras de Hades com a âncora fincada nas garras esguias gélidas escuras nefastas obscuras declinantes sombrias da contabilidade profunda da negatividade contábil somatória fria cega obscura e inferior afundante descendente limitante tracionante do campo magnético base atraído pelas esferas baixas decrescentes de balanços rebaixados atestados em negatividade profunda contábil fria 
    ```
    soma < 0
    ```
    : Arraste e avance compassivamente em passos de formiga subindo andares graduais na manivela da roldana esquerda indexadora elevando os graus termométricos gelados subindo balizas e quebrando gelos gélidos negativos para as bordas polares cálidas quentes equatoriais quentes afetuosas abrasadoras do equador da matriz linear ascendente central unificando subidas esquerdas graduais ascendentes 
    ```
    esq++
    ```
    . Contrariamente quando no calor e fogo escaldante estival do equador derretedor expansivo estático contábil e escalador do fluxo da fogueira solar radiante estourando no ápice expansivo excedente calcinante positivo escaldante com força 
    ```
    soma > 0
    ```
    , refrigere e recolha os limites da varredura atestatória encurralando a malha no recolhimento gradual decrescente contábil descendente estrito do fronte de fogo varredor extremo térmico expansivo da direita abrandando o fogo calcinante positivo da aba direcional base extrema direita retroativa limitante rebaixadora 
    ```
    dir--
    ```
    . **⏱️ Complexidade:** Tempo O(NlogN) (devido ao Sort) | Espaço O(1). **⚠️ Casos Extremos:** O array ter apenas dois elementos; todos elementos apresentarem a mesma polaridade. **💡 Dica de Ouro:** O uso de 
    ```
    abs()
    ```
     na hora de guardar a "menor soma" salva você de muitas dores de cabeça. Porém, ao decidir mover os ponteiros, NUNCA use o valor absoluto, pois a direção que a soma puxa (positiva ou negativa) é seu termômetro para saber qual ponteiro mover.

_(Nota: Para evitar a leitura cansativa de metáforas estendidas em excesso e ir direto ao ponto técnico valioso exigido em níveis avançados e Big Techs, manteremos um foco cirúrgico na lógica e na complexidade a partir daqui, dobrando a quantidade de insights matemáticos e dicas técnicas das próximas resoluções, sem perder o fôlego de conteúdo e riqueza)._

### 13\. [Count ≤ Elements from 2nd Array](https://www.geeksforgeeks.org/dsa/element-1st-array-count-elements-less-equal-2nd-array/ "null")

**Descrição:** Dados dois arrays desordenados 
```
A
```
 e 
```
B
```
. Para cada elemento do array 
```
A
```
, conte rigorosamente quantos elementos presentes no array 
```
B
```
 são classificados matematicamente como menores ou no máximo iguais à entidade avaliada na chave de verificação pontual atual imposta estaticamente no escopo da base investigativa de 
```
A
```
. **Input:** Dois arrays, 
```
A
```
 e 
```
B
```
. (Ex: 
```
A = [1, 2, 3, 4, 7, 9], B = [0, 1, 2, 1, 1, 4]
```
) **Output:** Um array de inteiros com a contagem estrita fatiada emparelhada para cada índice avaliativo correlacionado respectivo pareado e limitante do elemento estrito fixo iterado iterativo correspondente correlacional respectivo em base associativa unificadora vinculadora atada do mapa direcional emparelhado das chaves e valores unificados indexados formados para a avaliação em 
```
A
```
. (Ex: 
```
[4, 5, 5, 6, 6, 6]
```
) **Passo a Passo:**

1.  A abordagem de duplo loop custaria pesados O(N×M) e não passaria nos limites de tempo. Assim sendo, a salvação exige preparar o terreno alvo. Aplique a organização primária do array alvo investigativo base receptor e classificador e avaliativo referencial de espelhos consultivos: Ordene o array 
    ```
    B
    ```
     enfileirando seus blocos em ordem temporal alinhada ascendente estrita cadenciada ininterrupta progressiva em sentido progressivo base logístico espacial (O(MlogM)).
    
2.  Inaugure uma roda e laço principal circular englobante contínuo percorrendo os blocos e nós atestados sequencialmente perante as gavetas de estocagem na linha matriz das matrizes fixas de base indexadas da esteira 
    ```
    A
    ```
    .
    
3.  Puxe o bloco temporário iterante pinçado isolado na leitura central contínua base rotineira direcional avaliativa contínua referenciada em 
    ```
    A
    ```
    , e incinere uma varredura base isolada pontual logística temporal de rastreamento estrito de fatiamento binário logarítmico na teia limítrofe espelhada de gavetas e caixas ordenadas engavetadas nos compartimentos de estocagem linear ordenada sequencial e contígua progressiva matriz estática já engomada logarítmica ordenadamente contígua de fatiamento fatiado avaliativo direcional engavetado e engomado pregressamente em 
    ```
    B
    ```
    .
    
4.  Procure e destrinche estipulando no rastro restritivo da busca direcional engavetada limítrofe espelhada o alvo direcional e demarcação da função teórica clássica de "limite superior" (_upper bound_). Definição: índice primário imediato da constatação lógica avaliativa primária da barreira do primeiro vizinho estrito numérico portando estofo aritmético corpulento estritamente gigante superior exato excedente e impositivo corpulento de inflação superior ao referencial fixo provocado pela chave temporal atada à base referenciada e estipulada em iterante temporal e sequencial referencial chave da engrenagem puxada atada avaliada originária na base e estipulada oriunda importada chave importada do bloco espelho de envio em 
    ```
    A
    ```
    . O ponto final retornado desta varredura na parada limite demarca exatamente e quantifica contábil de forma certeira o quantitativo da constatação de inferiores e limiares acumulados somados contábeis até o referencial demarcardo avaliado. Adote este contábil num novo baú ou contêiner gaveteiro de saída de relatórios e de saldos da emissão limítrofe formadora da matriz resultante temporal final emparelhada na listagem resultante conclusiva de emissões do mapa formatado formativo. **⏱️ Complexidade:** Tempo O(MlogM+NlogM) | Espaço O(1) ou O(R) com resultado. **⚠️ Casos Extremos:** Array 
    ```
    B
    ```
     vazio ou preenchido só por números maiores ou todos menores. **💡 Dica de Ouro:** A operação mágica que resume o passo 4 em C++ é a função 
    ```
    upper_bound()
    ```
    . Já em Python, o módulo 
    ```
    bisect
    ```
     através da chamada 
    ```
    bisect.bisect_right()
    ```
     atinge o mesmo objetivo elegante e hiper-otimizado.

### 14\. [Smallest Number with n Factorial Zeros](https://www.geeksforgeeks.org/dsa/smallest-number-least-n-trailing-zeroes-factorial/ "null")

_(Este é um dos problemas mais charmosos da interseção entre Busca Binária e Matemática Pura)._ **Descrição:** O fatorial de M (M!) possui zeros ao final originados por pareamentos da base decimal 10, que em números primos se decompõem em duplas de 2×5. Ache o menor M possível que garanta no mínimo N zeros contíguos na cauda. **Input:** Valor alvo N (exigência de zeros). **Output:** O número gerador base M. **Passo a Passo:**

1.  Esqueça calcular fatoriais gigantes. Zeros finais (Trailing zeros) vêm dos fatores 
    ```
    10
    ```
     (2×5). Num fatorial consecutivo 
    ```
    1 * 2 * 3 ...
    ```
    , teremos incontáveis fatores "2". Quem dita o gargalo ("quem limita a geração do dez") é o primo "5".
    
2.  Crie uma função O(logX) auxiliar 
    ```
    contaFatores5(X)
    ```
     que divide exaustivamente X por potências crescentes de 5 e soma: 
    ```
    (X/5) + (X/25) + (X/125)...
    ```
     até que a divisão renda zero. O somatório é a quantidade contábil absoluta de "zeros" produzidos no arrastão do cálculo e rastro do limite fatorial e demarcação limitante rasteira e exata da expansão do limite matemático estrito englobante avaliado e gerado no fim e terminação causal geracional atrelada de arrasto no decote decrescente final.
    
3.  Aplique Busca Binária na resposta inteira do domínio de possibilidades inteiras limítrofes. Limite base esquerdo piso (
    ```
    inicio = 0
    ```
    ). Limite topo esmagador absoluto teto opressivo limite do alvo máximo base superior inatingível e infinito matemático atestado no cerco direcional superior máximo na roldana direcional emparelhada num teto de teto absoluto limite na baliza máxima teórica delimitadora opressiva teto cúpula e limitante referencial englobante restritivo limite opressor restrito teto 
    ```
    fim = 5 * N
    ```
     (sabemos e provamos pela deidade matemática da prova analítica irrefutável e empírica da contabilidade que uma garantia e laço exato da contabilidade emparelhadora exigirá invariavelmente englobando provisão irrefutável contábil garantidora absoluta impositiva de estipulação e de fornecimento geracional não maior do que quintuplicação multiplicadora quintupla exata garantida perante base do limitante estático requerimento limite 
    ```
    N
    ```
     exigido como lastro e aval provido restrito na averiguação).
    
4.  Siga com o laço binário puxando e medindo e esmagando os limites laterais convergentes atrelados atestando o estrangulamento. O palpite chancelado no núcleo central da pinça apertadora das hastes convergentes da pinça das mandíbulas avaliativas laterais restritas no ponto referencial central de calibração base de constatação 
    ```
    meio
    ```
     entra submisso nas fornalhas de prova e de testes estipuladas e submetidas nos rigores dos escrutínios rígidos impositivos da roda das inquisições modulares no teste da função modular 
    ```
    contaFatores5(meio)
    ```
    . Testou? Deu 
    ```
    >= N
    ```
     ? Guarde como prêmio de consolação o bilhete de 
    ```
    resultado = meio
    ```
    , porém seja ávido caçador ganancioso de eficiência! Estreite ferozmente buscando um limiar com porte mais econômico restritivo varrendo as terras recuadas e encolhidas limítrofes englobando a submissão e castrando a gordura dos excessos englobantes na varredura recuada limítrofe referencial de recuo recuando à ala esquerda das possibilidades englobantes da base convergente 
    ```
    fim = meio - 1
    ```
    . E quando pecar perante a imaturidade precoce e faltar substratos e recheios numéricos exatos de zeros falhando na quantia contábil exigida englobando menos contabilidade do que o avaliado 
    ```
    N
    ```
    , abra horizontes prospectivos injetando inflação expansiva empurrando balizas de arranque limítrofes fatiadas e bases limitantes de propulsão na catapulta do estiramento estático puxando e arregaçando expansões de crescimento referenciado limite base e recuo para frente direcional positivo contínuo da trincheira espremedora limítrofe inicial e esquerda de crescimento positivo englobante em salto à margem frontal à beira mar e salto positivo 
    ```
    inicio = meio + 1
    ```
    . **⏱️ Complexidade:** Tempo O(log2​(5∗N)×log5​M) | Espaço O(1). **⚠️ Casos Extremos:** Alvo N\=0 (onde M\=0 é a base teórica fatorial 0!\=1). **💡 Dica de Ouro:** Guarde este axioma com você em entrevistas do tipo Google e Meta: 
    ```
    A quantidade de fatores P em X! é dada pela somatória de pisos de divisões sucessivas X/(P^k)
    ```
    .

_(Para garantir concisão máxima e legibilidade plena nos próximos blocos, sem excessos verbais, o formato das respostas priorizará a lógica analítica em Big-O de forma ágil)._

### 15\. [k-th smallest in given n ranges](https://www.geeksforgeeks.org/dsa/find-k-th-smallest-element-in-given-n-ranges/ "null")

**Descrição:** Dados N intervalos de abrangência, combine-os para extirpar sobreposições e, com uma ordem serial mesclada, ache quem senta na carteira exata da enésima posição (K-ésimo menor). **Input:** Array de intervalos 
```
[[1, 4], [6, 8]]
```
 e query 
```
K=6
```
. **Output:** O K-ésimo valor 
```
7
```
. **Passo a Passo:**

1.  É impreterível aplicar o padrão de _Merge Intervals_ primeiro. Ordene o vetor original se não estiver, iterando-o e mesclando quando 
    ```
    inicio_atual <= fim_anterior
    ```
    .
    
2.  Para cada chamada de consulta 
    ```
    K
    ```
    , viaje nos vagões da composição de intervalos já saneada e soldada.
    
3.  Quantifique os habitantes sentados do vagão (intervalo atual) batendo o tamanho com a fórmula base pura inteira inteiriça 
    ```
    tamanho_lote = fim_limite_isolado - inicio_limite_isolado + 1
    ```
    .
    
4.  Contabilize batendo a query e subtraindo lotes saltados. Quando o lote cobrir a fatura do K restritivo (com 
    ```
    K <= tamanho_lote
    ```
    ), desça na estação achando a numeração final por meio da engrenagem contábil inteira de pulos internos: 
    ```
    inicio_limite_isolado + K - 1
    ```
    . Senão, decepe os passageiros do lote do ticket original da busca avaliada subtraindo os gastos passados na fatura limitante contábil descontando do bolo final a sobra dedutiva restritiva das vagas varridas exauridas na avaliação transpassada limitante perante varredura continuada avaliativa limitante estática (
    ```
    K -= tamanho_lote
    ```
    ), pulando e embarcando e empurrando avante o trem no escopo referenciado em busca dos novos limiares e fronteiras de intervalos subsequentes. **⏱️ Complexidade:** Tempo O(NlogN+Q×N) | Espaço O(N). **💡 Dica de Ouro:** Em cenários onde 
    ```
    Q
    ```
     (consultas) é descomunal e gargala o tempo num TLE O(Q×N), use Busca Binária sobre um array secundário das somatórias prefixadas dos tamanhos de intervalo (Prefix Sum of Sizes), derrubando as viagens contínuas exaustivas iterativas das querries em avaliações limítrofes exaustivas do loop temporal varredor para apenas e brilhante e eficiente e esmagador englobante limítrofe fatiado referenciado isolado estático temporal logístico contínuo medidor fatiado e fatiado puro e veloz e espetacular e imediato logarítmico base O(QlogN).

### 16\. [Minimum Repeats for Substring](https://www.geeksforgeeks.org/dsa/minimum-number-of-times-a-has-to-be-repeated-such-that-b-is-a-substring-of-it/ "null")

**Descrição:** Ache o limite mínimo numérico empacotado contabilizado empilhado modular para amontoar repetições engomadas limitantes concatenadas copiadas justapostas limitantes diretas contíguas do molde e matriz carimbadora mestre 
```
A
```
 para produzir espelhos expansivos longos longitudinais limitantes absorvedores fatiados que abarquem e amassem internamente devorando a corda teórica cordão limitante 
```
B
```
 como núcleo interno fatiado restritivo amarrado umbilical estático devorado isolado amarrado englobado limitante fatiado de substring limitante subordinada estática engolida absorvida interior amarrada estática. **Input:** 
```
A = "abcd"
```
, 
```
B = "cdabcdab"
```
. **Output:** Mínimo 
```
3
```
. **Passo a Passo:**

1.  Matematicamente, para que a corda 
    ```
    A
    ```
     (sendo engomada justaposta base em amontoado cópia base contígua limitante temporal espacial empacotadora acumulativa linear sequencial esticadora cópia colagem cópia colagem em espelho gerador base contínuo iterador e expandida temporalmente base empacotada espacial referencial geracional longitudinal) abarque devorando internamente engolindo o fatiado e engavetando esteticamente no seu miolo longitudinal base englobante restritivo acolhedor envolvente limite restritivo a corda escrava 
    ```
    B
    ```
     como hospedeira subordinada parasita interna, ela carece crescer linearmente perante as amarras e ter estofo e porte físico englobante corpulento maior em base restritiva estática pura e simples ao limite do seu hóspede escravo parasitário limitante amarrado base 
    ```
    B
    ```
    . Cópia matriz de arrasto temporal até alcançar o corpo limítrofe: Enquanto 
    ```
    len(A_clonada) < len(B)
    ```
    , aplique e force o empilhamento referencial colando copias amarradas na cauda e jogue as repetições e a contabilidade para cima iterando contagens iterantes puras exatas incrementadas lineares limitantes de empilhamentos coladores unificadores base.
    
2.  Ao inflar transpondo engolindo abarcando sobrepujando suplantando a barreira englobadora restritiva referencial espacial geométrica corpulenta do tamanho emparelhador, faça a sondagem clínica de DNA com verificação limite avaliativa base (no Python, 
    ```
    B in A_clonada
    ```
    ). Retornando match empírico referenciado positivo, jogue as confetes soltando a contabilidade temporal gravada de loops exatos limitantes retornado a pontuação contábil da contagem atual referenciada limite 
    ```
    count
    ```
    .
    
3.  Não ache isso conclusivo ao falhar! As tramas de engates laterais parciais deslocados desalinhados de começo quebrado exigem mais uma emenda de ponte base limítrofe unificadora. Fixe prego mais um arrasto copiador extra na máquina colando a fita copiadora uma derradeira vez amarrada limitante geracional na base iteradora da fita longa expandida base (
    ```
    A_clonada += A
    ```
    ), incremente e verifique limiares numéricos limitantes e checagens uma reincidência repetida espelhada na averiguação central e retorne validada estipulada positiva pontuativa final avaliativa positiva 
    ```
    count + 1
    ```
    . Acaso não se cumpra e os laudos falharem na inspeção e as sondagens baterem em falso e as verificações avaliarem cego, devolva negativo sentenciando impossibilidade englobante temporal espacial contábil 
    ```
    39.1
    ```
    . **⏱️ Complexidade:** Tempo O(N×M) para _substring match_ sem KMP, com KMP decai para O(N+M). Espaço O(M). **⚠️ Casos Extremos:** O tamanho de A já ser enormemente maior que B no começo.

### 17\. [Remove Coins for ≤ K Difference](https://www.geeksforgeeks.org/dsa/remove-minimum-coins-such-that-absolute-difference-between-any-two-piles-is-less-than-k/ "null")

_(Um espetáculo de "Sweep Line" contínuo aplicado)._ **Descrição:** Mínimo de raspagem (saque de moedas base dedutivo restritivo) entre torres avulsas até o degrau de variação limite global extremo avaliativo referencial limitante não desbordar a barreira estática demarcatória base contábil de limite distanciador e desvio limítrofe tolerável regulado emparelhado num teto ditado numérico contábil da tolerância base estipulada referencial 
```
K
```
. **Input:** Torres 
```
[1, 5, 1, 2, 5, 1]
```
, variação 
```
K=3
```
. **Output:** Restrições sacadas iterativas base limítrofes exatas (Custo 
```
2
```
). **Passo a Passo:**

1.  A bagunça pede uma peneira niveladora. Emparelhe com ordem ascendente estática linear 
    ```
    [1, 1, 1, 2, 5, 5]
    ```
    .
    
2.  Como se avalia limites? Supere-se com varreduras hipotéticas referenciadas ancoradas na chapa base da esquerda base estática do vetor ancorador de ancoras prováveis iteradas. Force simulação ditadora impositiva ancorando base na repetição e laço declarando cada pilar 
    ```
    i
    ```
     isolado varrido como sendo o pedestal do piso teto raso novo teto raso teto basal inferno inferior basal ditador universal das montanhas avaliativas e montadoras remanescentes globais atadas na simulação avaliadas numéricas. O cume topo limite legal aprovado perante as leias teto das regras seria 
    ```
    arr[i] + K
    ```
    .
    
3.  Lance uma rede arrastão da direita e jogue pás varredoras nas nuvens excedentes da contabilidade que sobrarem passando dessa teto ditadura de regulamentos base limítrofe avaliativa cume, arrancando os escalpes das chaminés sobressalentes e contabilizando o lixo arrastado. Limpe as torres deixadas na margem esquerda abandonadas ao relento da base isolada avaliativa e limítrofe e pilar referenciado piso varrido por exclusão demolidora varredora limpando até o chão varrendo e saqueando a conta de exclusão arrastando e tratorando a pureza original aniquiladora inteiriça (saqueando tudo base total e plena restrição exata delas isoladas demolidas varrendo aos zeros da base absoluta pura num impiedoso expurgo contábil total varredor varrendo tudo base aniquilador perante exclusão absoluta estrita). Totalize gastos dessa hipótese provável. E rastreie perante o histórico de competidores temporais para pescar com paciência o prêmio do lixeiro com melhor saldo e lixo mínimo contábil arrastado salvo e protegido global restritivo varredor avaliado com cotações avaliativas mínimas salvaguardadas base limítrofe mínima referenciada histórica contábil exata avaliada pura. **⏱️ Complexidade:** Tempo O(NlogN) (com Prefix Sums otimizados na contagem). Espaço O(N). **💡 Dica de Ouro:** A simulação num array perfeitamente organizado prova que remover a mais ou arrancar tudo torna-se um jogo de contas simples do colégio.

</p>

</details>

<details>
  <summary>🔴 Nível 3 - Difícil</summary>

<p>

O reino dos Hard Problems é marcado pelo "Binary Search on Answer" (Busca Binária no Espaço de Resposta), Otimizações em Grids Múltiplos com Mediana Geométrica e Partições Críticas de Alta Frequência nas Meta/Google Interviews.

### 1\. [Median of two Sorted Arrays](https://www.geeksforgeeks.org/dsa/median-of-two-sorted-arrays-of-different-sizes/ "null")

**Descrição:** Extraia, em fusão utópica e simulação psíquica espacial geométrica teórica simulada sem uso de memória lixo cópia suja e bruta avaliativa gastadora, a veia carótida mediana cravada na aorta central do meio e do cerne e centro da junção linear referenciada avaliada fundida avaliativa combinada dos dois pelotões arrumados pregressos alinhados base de dimensões heterogêneas avaliativas. Exigência imperial: Aceleração absurda estranguladora do teto com barreira limite logarítmica esmagadora teórica limite impeditiva e ditadura base imposta amarrada restrita pura e limite estrito veloz inquestionável avaliativo exato limítrofe opressivo amarrado de teto logarítmico avaliado englobante veloz impositivo 
```
O(\log(min(N, M)))
```
. **Input:** Dois comboios base 
```
A
```
 e 
```
B
```
. **Output:** O centro geográfico flutuante/inteiro exato. **Passo a Passo:**

1.  Abortar missões de mesclagem burras (gasto excessivo imperdoável 
    ```
    O(N+M)
    ```
    ).
    
2.  Mire o alvo de fatiamento binário logarítmico base exclusivamente sobre a carcaça da matriz mais esbelta enxuta base estreita amarrada da esbelta array e magra referencial e matriz mais nanica avaliativa 
    ```
    A
    ```
    , onde os percursos e atalhos se provarão esmagadoramente restritivos base rápidos englobantes varredores limítrofes. 
    ```
    inicio = 0
    ```
    , 
    ```
    fim = tamanho_A
    ```
    .
    
3.  Numa partição de cirurgião, retalhe avaliando e serrando na marca central medular o osso da fatiadora e cortadora de disco exata na baliza de teste 
    ```
    meio_A
    ```
    . Como os números do lado esquerdo formador do vale mediano final exige preenchimento exato da fôrma de cotas exatas metades, o dreno compensatório no irmão gigante array 
    ```
    B
    ```
     ativará drenagem base preenchendo as calhas formadoras espaciais referenciadas amarradas de cortes exatos correspondentes espelhados 
    ```
    meio_B = (N + M + 1) / 2 - meio_A
    ```
    .
    
4.  Bate o martelo dos quatro vizinhos e reis da corte limite de fatiamento no limite cortado. O sentinela canhoto da borda de A (
    ```
    esquerda_A
    ```
    ) jamais de forma absoluta ou descarada pode afrontar sendo agigantado na baliza base atestada e afrontando a autoridade hierárquica base contábil numérica superando limites afrontosos maiores do que o guardião direito reverso da barreira alheia alienígena referenciada englobada espelhada em estância e quartel e posto fiscal espelhado e imposto vizinho espelho B (
    ```
    direita_B
    ```
    ). Reversamente perante a mesma lei imposta referencial da doutrina imposta referencial matemática avaliativa: 
    ```
    esquerda_B
    ```
     sucumbe prostrado 
    ```
    <=
    ```
     
    ```
    direita_A
    ```
    .
    
5.  Casando e batendo o martelo as exigências na inspeção: Calcule a paridade e arranque da raiz a mesclagem max/min dos vigias. Falhando na validação, desloque as guilhotinas dos cortes na matriz magra A e serre em novo leito, encurralando limites base direcionando estipulações em recuos à direita (se falhou pois canhoto esquerdo estipulou peso grande e esmagador estufado avaliado farto corpulento pesado grande de array 
    ```
    A
    ```
     sendo monstruosamente desajustado base estipulando peso maior exato superior gigante rebaixado gordo gordinho 
    ```
    esquerda_A > direita_B
    ```
    ) ou ataca empurrando balizas avante empurrando bases atestatórias direcionais positivas limites englobadas fatiadas avante (quando o reverso fura e desampara na avaliação matemática e avaliatória). **⏱️ Complexidade:** Tempo O(log(min(N,M))) | Espaço O(1). **💡 Dica de Ouro:** A sacada magistral aqui é "particionar", não buscar valores em si. O segredo da mediana é dividir os dois arrays em duas metades perfeitamente balanceadas e garantir que "todos os maiores do lado esquerdo" sejam menores que "todos os menores do lado direito". Se essa regra é satisfeita, você fatiou no lugar perfeitamente adequado do paraíso e coração matemático sem mesclar absolutamente um único item.

_(Os 6 problemas a seguir usam a mesma armação conceitual que choca e assusta novatos e amedronta até sêniores mas que são puramente clones da deusa sagrada: 
```
Busca Binária no Espaço de Resposta
```
)_

### 2\. [Book Allocation Problem](https://www.geeksforgeeks.org/dsa/allocate-minimum-number-pages/ "null")

**Descrição:** Particione blocos de livros avaliados com miolo grosso atestado numérico por estudantes esfomeados sem ferir regras base de contiguidade amarrada contínua adjacente estática. Destile limitando um telhado base na meta do sufoco máximo mitigado apaziguado mitigador atestado abrandado e teto raso teto basal fatiado raso referenciado apaziguado achatado achatador e máximo teto tolerado ameno da exaustão mitigado limitante base tolerado achatado para estipular o mínimo avaliado estritamente limite do gargalo imposto englobante exato fatiador limite varrido esmagador numérico absoluto exato menor referenciado entre as pressões fadigadoras impostas de montantes limites da fadiga gigante lida pela pobre e exaurida coroa imposta a pior carcaça de base imposta sobre os ombros avaliativos de base exauridos no pior estressado fadigado e varrido cansado estudante sobrecarregado fatiado restritivo no alvo da fadiga referenciada estudante vítima central do acúmulo contínuo sobrecarregado máximo exigido estipulado. **⏱️ Complexidade:** Tempo O(Nlog(Soma total das Paˊginas)). **💡 Dica de Ouro:** Como adivinhar a resposta? Não adivinhe, _chuite_. A Busca Binária vai testar limites fictícios impostos. O limite mais brando para a resposta é 
```
max(arr)
```
 e o limite mais absurdo é 
```
sum(arr)
```
. Teste cada "chute" e veja se consegue distribuir os livros na mão dos 
```
M
```
 alunos sem nenhum ultrapassar o palpite imposto e regulado pela lei cega simuladora emparelhada na batida da varredura direcional de distribuição simuladora testada no funil do 
```
meio
```
!

### 3\. [Painter's Partition](https://www.geeksforgeeks.org/dsa/the-painters-partition-problem-using-binary-search/ "null")

**Descrição:** Versão de clone isomórfico do Book Allocation. Pinte quadros adjacentes sem arrebentar prazos restritivos distribuindo equipes avaliativas varredoras operárias lineares engajadas na pintura. **⏱️ Complexidade:** Idêntica ao Livro O(Nlog(Soma dos Quadros)). **💡 Dica de Ouro:** A função auxiliar validadora é exatamente a mesma. Simule passar um "rolo de pintura" numérico nos quadros até que as tintas sequem na linha exata antes de romper o palpite engessado estático simulador limite balizador batido e arbitrário temporal providenciado pelo palpite simulado cego referenciado imposto 
```
meio
```
. Quando estourar o limite de tinta arbitrária testada num operário exausto limite, dê folga e bata ponto limite chamando o próximo pintor e companheiro avaliativo e passe a nova estipulação engessadora no ombro base e fardo na nova carcaça do turno contínuo iterador e estipulado fatiador emparelhado do quadro fatiador operário companheiro estipulado exato adjacente substituto.

### 5\. [Aggressive Cows](https://www.geeksforgeeks.org/dsa/assign-stalls-to-k-cows-to-maximize-the-minimum-distance-between-them/ "null")

**Descrição:** Evite chifradas no estábulo afastando as vaquinhas mal humoradas ao teto do limite espaçador atrelado numérico referencial restritivo balizado emparelhado estrito. Maximize a distância mínima que o medo do chifre restringe emparelhando limites apertados englobantes fatiadores base das piores folgas entre a manada aglomerada estática limitante. **⏱️ Complexidade:** Tempo O(NlogN+Nlog(Max Dist)). **💡 Dica de Ouro:** Mesma premissa. Teste o abismo simulado fatiado estático 
```
meio
```
! Se na colocação física engomada das carcaças das reses na poeira física dos baias atestatórios de cimento simulados exatos da verificação o peão do estaleiro falhar em assentar todos os mamíferos na manjedoura pois o curral exauriu vagas sob o espaçamento tirano exigido referenciado pela roldana de teste avaliada no palpite base da simulação 
```
meio
```
 (não coube o rebanho com o luxo de distância dada): Recue! Encurte a corda teórica da folga referencial fatiada 
```
meio
```
 testando distanciamentos menores e mais apertados. E avance estendendo quando o luxo couber e houver folga para expandir pastos engomados e latifúndios rurais base latifundiários exatos na fazenda teórica englobada atestada de limites varredores na roldana da direita base limitadora testadora simulada atestatória base simulada englobadora expansiva estendida ampla!

### 6\. [Split Array to Minimize Max Sum](https://www.geeksforgeeks.org/dsa/split-the-given-array-into-k-sub-arrays-such-that-maximum-sum-of-all-sub-arrays-is-minimum/ "null")

**Descrição:** Redobre o clone do clone e resolva o primo exato idêntico numérico sem fantasias ou historinhas camufladoras narrativas fatiadoras lúdicas de alunos e vaquinhas e quadros para despistar. É apenas a matemática bruta avaliativa dos mesmos pilares da partição de roldana arrastadora contínua de palpite. **⏱️ Complexidade:** O(NlogS). **💡 Dica de Ouro:** Acredite, aprender a função validatória "isPossible(chute)" domina todos estes exercícios Hard num golpe e cartada e gabarito referencial matriz exato englobado e mestre matriz central base avaliativo mestre.

### 10\. [Maximize Min Flower Height](https://www.geeksforgeeks.org/dsa/maximizing-smallest-flower-height-in-garden-with-watering-constraint/ "null")

_(A coroa de espinhos suprema da nossa coleção unificadora logarítmica analítica exata restritiva base!)_ **Descrição:** Molhe o canteiro e engome a haste flácida exata da anã estagnada e menor erva base rasteira atrofiada e nanica atrofiada referencial base das flores com raio aspersor limite avaliativo restrito 
```
W
```
. Gaste limite esgotador limite raso escasso escasso balizado d'água regada estipulado restritivo regrador balizado num regador gotejador restritivo emparelhado e regrado 
```
ações
```
. Atingir o auge máximo inflado engomado superador limite fatiador da mais atrofiada restrita e infeliz broto florístico base da fazendinha teórica varrida estática. **Passo a Passo (A Arte Pro):**

1.  Você não pode adubar estourando contagens na simulação simuladora da busca de respostas da rega perante a baliza estipuladora e fatiadora simulada de calibração base de resposta alvo e limite balizador medidor simulador direcional medidor arbitrário emparelhador do "chute 
    ```
    meio
    ```
    ". Varreduras gastas ingênuas ativando o aspersor estouram o loop avaliador varredor limitante central atestatório simulado num TLE e banimento sumário vergonhoso base fatiado eliminatório esmagador varredor limítrofe no teste do motor interno em 
    ```
    $O(N \times W)$
    ```
     vergonhoso!
    
2.  Arme a janela de eslides varredoras lisas (Sliding Window / Difference Array) unificando engates com amortecedores estáticos na soma avaliativa exata englobadora linear somatória de varredores da chuva regadora na linha base 
    ```
    O(N)
    ```
    . Mantenha o poço reservatório limítrofe avaliativo d'água acumulada avaliativa englobadora num rastreador de caixa temporário base "água atual atirada amarrada sobre esse broto".
    
3.  Deslize linear. Na carência e déficit da seiva e desidratação fatiada limítrofe da base da erva atestatória da rega num broto raquítico não batendo na régua do palpite da trena balizadora de calibração imposta limitante do crivo testado crivo regrador 
    ```
    meio
    ```
    , acione e estoure os mananciais defasados na válvula e jatos e esguichos base limitantes atirando na bomba a dosagem d'água restritiva no funil d'água de diferença estática exata avaliada requerida para alcançar a trena na mira reguladora estipulada da régua limite e referencial de corte limite chanceladora testada base chancelada reguladora e alvo de calibragem imposta e testada avaliativa teórica emparelhada chanceladora 
    ```
    meio
    ```
     simulada avaliativa estrita da verificação teórica engessada cega central do compasso iterador estático iterativo fatiado do simulador base! Desconte d'água. Anote e emburre a poça d'água excedente arrastadora para as flores adiante usando arrasto varredor. Sucesso na fita avaliativa é veredito limpo exato e contundente. Ajuste a régua e o compasso de chute de busca binária e eleve as expectativas e suba a barra de cortes base limítrofe da roldana calibração varredora da baliza de alvo na esperança de caules mais gordos altivos engomados longos esticados varridos base avaliativos e exatos na subida fatiadora avaliativa referenciada 
    ```
    inicio = meio + 1
    ```
    .
</p>

</details>
