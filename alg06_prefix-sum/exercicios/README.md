# Lista de Exercícios - Algoritmos de Soma de Prefixo (Prefix Sum)

Esta lista de exercícios tem como objetivo fortalecer e expandir sua lógica de programação em torno de uma das técnicas mais elegantes e fundamentais da ciência da computação: a **Soma de Prefixo** (Prefix Sum). Os problemas abaixo estão organizados por ordem crescente de dificuldade e foram elaborados de forma agnóstica de linguagem. Sinta-se livre para resolvê-los em C, C++, C#, Java, Kotlin, Javascript/Typescript, Python, PHP, Go, Ruby ou qualquer outra linguagem de sua preferência.

<details>
    <summary>🟢 Nível 1 - Fácil</summary>

Nesta seção, o foco é entender a mecânica básica de acumulação de valores e como reverter esse processo ou utilizá-lo para consultas rápidas.

#### 1. Array original a partir de prefix sums

**Descrição do Problema:** Dado um array que representa a soma de prefixos de um array original oculto, sua tarefa é reconstruir e retornar o array original.

**Aplicações Práticas:** Muito comum na área de dados. Imagine que você tem um relatório de "vendas totais acumuladas do mês" até cada dia, e seu chefe pede para você descobrir quanto foi vendido _exatamente_ em cada dia individual.

**Passo a Passo Sugerido:**

1. Crie um array `resultado` do mesmo tamanho que o array de entrada para evitar a mutação dos dados originais (boa prática).
2. O primeiro elemento do `resultado` é sempre igual ao primeiro elemento do array de prefixos, pois não há elementos anteriores para acumular.
3. Para os próximos elementos (a partir do índice 1), o valor original do dia em questão é simplesmente a diferença entre o valor do prefixo atual (acumulado até hoje) e o valor do prefixo imediatamente anterior (acumulado até ontem).

**Complexidade Esperada:** Tempo O(N), Espaço O(N).

**Exemplo:**
- **Input:** `prefix = [5, 7, 10, 16]`
- **Processamento:** `[5, (7-5), (10-7), (16-10)]`
- **Output:** `original = [5, 2, 3, 6]`

#### 2. Média de um intervalo no array

**Descrição do Problema:** Dado um array de números e múltiplas consultas de intervalos `[L, R]` (onde L é o índice inicial e R o final), calcule a média matemática dos elementos dentro desse intervalo de forma eficiente.

**Aplicações Práticas:** Analisar a média de temperatura de uma semana específica dentro de um registro de anos, ou a média de preço de uma ação na bolsa durante um período específico.

**Passo a Passo Sugerido:**

1. Pré-processe o array construindo um novo array de `prefix_sum`, onde cada posição `i` guarda a soma de todos os elementos do índice `0` até `i`. Este passo leva O(N).
2. Para cada consulta `[L, R]`, em vez de iterar de L até R, a soma do intervalo é rapidamente calculada pela fórmula: `prefix_sum[R] - prefix_sum[L-1]`.
3. **Atenção:** Trate cuidadosamente o caso onde `L=0` (pois `L-1` resultaria em índice -1, causando erro em muitas linguagens). Se `L=0`, a soma é apenas `prefix_sum[R]`.
4. Divida a soma obtida pela quantidade de elementos no intervalo. A fórmula matemática para a quantidade de elementos é `(R - L + 1)`. O resultado será a média.

**Complexidade Esperada:** O(N) para pré-processamento, O(1) por consulta.

**Exemplo:**
- **Input:** `arr = [1, 2, 3, 4, 5]`, Consultas: `[0, 2]`, `[1, 4]`
- **Output:** `[2, 3.5]` (Médias de `[1,2,3] = 6/3 = 2` e `[2,3,4,5] = 14/4 = 3.5`)

#### 3. Índice de equilíbrio

**Descrição do Problema:** Encontre um "índice de equilíbrio" em um array. Um índice de equilíbrio atua como um pivô de gangorra: é a posição onde a soma de todos os elementos à sua esquerda é estritamente igual à soma de todos os elementos à sua direita.

**Passo a Passo Sugerido e Lógica:**

1. Uma abordagem inocente seria recalcular as somas esquerda e direita para cada índice (O(N²)). Para otimizar, primeiro calcule a `soma_total` de todos os elementos do array em uma única passagem.
2. Crie uma variável `soma_esquerda` inicializada em 0.
3. Itere pelo array. Em cada passo, você não precisa calcular a direita do zero. A `soma_direita` será sempre `soma_total - soma_esquerda - elemento_atual`.
4. Se `soma_esquerda` for exatamente igual a `soma_direita`, você encontrou o ponto de equilíbrio! Retorne o índice atual.
5. Caso não seja igual, antes de ir para o próximo índice, adicione o `elemento_atual` à `soma_esquerda`.

**Complexidade Esperada:** Tempo O(N), Espaço O(1).

**Exemplo:**
- **Input:** `arr = [-7, 1, 5, 2, -4, 3, 0]`
- **Output:** `3` (No índice 3, o valor é 2. A soma à esquerda `[-7, 1, 5]` é -1, e à direita `[-4, 3, 0]` é -1)

#### 4. Dividir um array em dois subarrays com soma igual

**Descrição do Problema:** Verifique se é possível "cortar" o array em duas metades (não necessariamente do mesmo tamanho, mas contíguas) de forma que a soma da primeira metade seja idêntica à da segunda.

**Aplicações Práticas:** Muito usado em lógica de divisão justa de recursos, como balanceamento de carga entre dois servidores que processam tarefas sequenciais.

**Passo a Passo Sugerido:**

1. Calcule a soma total de todo o array.
2. Observe a matemática: se a soma total for um número ímpar (e estivermos lidando apenas com inteiros), é matematicamente impossível dividi-lo em duas metades iguais. Você pode retornar `False` imediatamente.
3. Se for par, o objetivo é encontrar um prefixo que some exatamente `soma_total / 2`.
4. Itere pelo array somando os elementos sequencialmente em uma variável `soma_atual`.
5. Se em algum momento a `soma_atual` for igual à metade da soma total, significa que o resto do array consequentemente também somará a outra metade.

**Exemplo:**
- **Input:** `arr = [1, 2, 3, 4, 5, 5]`
- **Output:** `True` (O array corta após o número 4. A primeira parte `[1, 2, 3, 4]` soma 10, e a segunda `[5, 5]` também soma 10)

#### 5. Produto do array exceto ele mesmo

**Descrição do Problema:** Dado um array numérico, retorne um novo array onde cada posição `i` contenha o produto de todos os números do array original, _exceto_ o número no próprio índice `i`. 

**Restrição crucial:** Você não pode simplesmente multiplicar tudo e depois dividir pelo elemento atual, pois operadores de divisão são proibidos (e falhariam se houvesse zeros no array).

**Passo a Passo Sugerido:**

1. A solução é usar a técnica de prefixo em duas direções. Crie um array de `prefixos` onde a posição `i` contém o produto de todos os números estritamente à esquerda de `i`.
2. Crie um array de `sufixos` (prefixo invertido) onde a posição `i` contém o produto de todos os números estritamente à direita de `i`.
3. O resultado para qualquer índice `i` é simplesmente `prefixos[i] * sufixos[i]`.
4. **Desafio Extra:** Tente fazer isso com complexidade de espaço O(1) (ignorando o array de resposta). Você pode calcular o prefixo diretamente no array de saída, e depois usar uma variável para acumular o sufixo de trás para frente, multiplicando no próprio array.

**Exemplo:**
- **Input:** `arr = [1, 2, 3, 4]`
- **Output:** `[24, 12, 8, 6]` (No índice 0, fazemos 2 × 3 × 4. No índice 1, fazemos 1 × 3 × 4, etc.)

</details>

<details>
    <summary>🟠 Nível 2 - Médio</summary>

Neste nível, a técnica de Prefix Sum é combinada com Dicionários/Hash Maps e algoritmos de Janela Deslizante (Sliding Window) para alcançar complexidades O(N) em problemas complexos.

#### 6. Menor subarray contíguo com soma mínima

**Descrição do Problema:** Encontre o subarray contíguo (com pelo menos 1 elemento) que resulte na menor soma algébrica possível, permitindo números negativos.

**Aplicações Práticas:** Em finanças, isso ajuda a identificar o período contínuo de maior prejuízo em uma série histórica de fluxo de caixa.

**Passo a Passo Sugerido:**

1. Utilize uma inversão lógica do famoso Algoritmo de Kadane.
2. Mantenha controle de duas variáveis: `soma_minima_global` (iniciada com infinito positivo ou o primeiro elemento) e `soma_atual` (iniciada em 0).
3. Itere pelo array: adicione o elemento na `soma_atual`. A decisão crucial é: a `soma_atual` acumulada com o elemento novo é menor que o próprio elemento sozinho? Se o elemento sozinho for ainda menor, "zere" o passado e comece um novo subarray a partir desse elemento (`soma_atual = min(elemento, soma_atual + elemento)`).
4. Atualize a `soma_minima_global` sempre que a `soma_atual` atingir um novo fundo.

**Exemplo:**
- **Input:** `arr = [3, -4, 2, -3, -1, 7, -5]`
- **Output:** `-6` (O subarray `[-4, 2, -3, -1]` atinge o menor valor de vale possível)

#### 7. Subarray com soma 0

**Descrição do Problema:** Determine se existe pelo menos um subarray contíguo dentro do array onde a soma exata de todos os seus elementos resulte em zero.

**Por que funciona matematicamente?** Se durante a contagem de prefixo a `soma_acumulada` atingir o valor "X" no índice `i`, e posteriormente atingir novamente o valor "X" no índice `j`, a única explicação matemática para o valor não ter mudado é que a soma de todos os elementos entre os índices `i+1` e `j` é exatamente zero.

**Passo a Passo Sugerido:**

1. Use uma estrutura de dados de busca rápida, como um Conjunto (Set) ou Hash Map, para memorizar os prefixos que já vimos.
2. Mantenha uma variável de `soma_acumulada`. Adicione o valor `0` ao Set logo no início para tratar casos em que o prefixo inteiro desde o começo já zera sozinho.
3. Itere adicionando valores à `soma_acumulada`.
4. Se essa nova `soma_acumulada` já estiver no Set, bingo! Temos um subarray nulo.
5. Caso contrário, adicione o prefixo atual ao Set e siga em frente.

**Exemplo:**
- **Input:** `arr = [4, 2, -3, 1, 6]`
- **Output:** `True` (O subarray central `[2, -3, 1]` soma zero)

#### 8. Contar subarrays com soma K

**Descrição do Problema:** Expansão do problema anterior. Em vez de procurar soma 0, procure uma soma específica `K`, e conte exatamente quantos subarrays cumprem essa condição.

**Passo a Passo Sugerido:**

1. Desta vez um simples Set não basta, precisamos de um Dicionário/Hash Map para armazenar as **frequências** das somas de prefixo (quantas vezes vimos aquela mesma soma).
2. Inicialize o mapa com o par `{0: 1}`. Isso prevê o caso em que um elemento ou soma direta já é igual a `K`.
3. Mantenha uma `soma_acumulada` e um `contador_total`.
4. Em cada passo, verifique a mágica do algoritmo: se `(soma_acumulada - K)` existe no Dicionário. Por que? Porque se nossa soma atual é 15 e procuramos K=5, estamos perguntando ao mapa: "Você já viu alguma soma de valor 10 no passado?". Se sim, a diferença entre aquele ponto 10 e este ponto 15 é exatamente o 5 que queremos.
5. Adicione a frequência dessa diferença ao seu `contador_total`.
6. Incremente a contagem da `soma_acumulada` atual no mapa.

**Exemplo:**
- **Input:** `arr = [1, 1, 1]`, `K = 2`
- **Output:** `2` (Os dois subarrays válidos são os primeiros dois uns `[1, 1]` e os dois últimos uns `[1, 1]`)

#### 9. Maior subarray com soma K

**Descrição do Problema:** Semelhante ao problema 8, mas não queremos contar a quantidade. Queremos descobrir o **comprimento máximo** (o maior número de elementos possíveis) de um subarray que some exatamente `K`.

**Passo a Passo Sugerido:**

1. A mudança chave no Hash Map aqui é: em vez de guardar frequências, vamos guardar o **índice** onde cada `soma_acumulada` foi observada pela **primeira vez**.
2. Rastreie a variável `tamanho_maximo` (inicializada em 0).
3. Ao calcular a `soma_acumulada`, se `(soma_acumulada - K)` estiver no Hash Map, pegue o índice salvo e subtraia do índice atual para obter o comprimento desse subarray. Atualize `tamanho_maximo` se necessário.
4. **Regra de Ouro:** Só adicione a `soma_acumulada` ao mapa se ela **ainda não existir**. Como queremos o maior subarray possível, precisamos preservar o índice mais antigo (mais distante) onde aquela soma apareceu.

**Exemplo:**
- **Input:** `arr = [10, 5, 2, 7, 1, 9]`, `K = 15`
- **Output:** `4` (O maior subarray válido é `[5, 2, 7, 1]`, contendo 4 elementos)

#### 10. Remoções mínimas para soma-alvo

**Descrição do Problema:** Você recebe um array e um valor alvo `X`. Você só pode remover itens das extremidades (esquerda ou direita) do array. Qual o número mínimo de remoções para que os elementos restantes no array somem `X`?

**Aplicações Práticas:** Este problema costuma aparecer em otimização de buffers de stream ou restrições de cortes de matérias-primas.

**Passo a Passo Sugerido:**

1. Este problema testa sua capacidade de "pensar ao contrário". Remover elementos das pontas para sobrar uma soma `X` no meio é rigorosamente igual a encontrar o **maior subarray contíguo no centro** cuja soma seja exatamente `Soma_Total_Original - X`.
2. Calcule o novo alvo para o subarray central: `Alvo = Soma_Total - X`. Se for negativo, retorne impossível.
3. Use a técnica de Prefix Sum com Hash Map (exatamente como no Exercício 9) para encontrar o tamanho do maior subarray com esse `Alvo`.
4. O seu resultado de remoções mínimas será `Tamanho_Total_do_Array - Tamanho_do_Maior_Subarray_Encontrado`.

**Exemplo:**
- **Input:** `arr = [1, 1, 4, 2, 3]`, `X = 5`
- **Output:** `2` (Remova o 1 da esquerda e o 3 da direita, sobrando `[1, 4]` que somam 5. Foram feitas 2 remoções)

#### 11. Soma de subarray divisível por K

**Descrição do Problema:** Conte quantos subarrays contíguos possuem uma soma total que seja múltipla perfeita de `K` (resto da divisão por `K` é 0).

**A Matemática (Aritmética Modular):** A lógica aqui diz que se você tem dois prefixos, A e B, e o resto da divisão de ambos por `K` for o mesmo (`A % K == B % K`), então a diferença entre eles `(A - B)` é garantidamente divisível por `K`.

**Passo a Passo Sugerido:**

1. Use um Hash Map para armazenar a frequência dos restos de divisão vistos, iniciando com `{0: 1}` (pois se o resto for 0 logo de cara, é um subarray válido).
2. Para cada elemento, acumule na variável de soma e calcule o resto: `resto = soma_acumulada % K`.
3. **Tratamento de Exceção:** Em linguagens como C++, Java e JS, o operador `%` com números negativos gera restos negativos. Para converter para um resto positivo matematicamente correto, faça `resto = (resto + K) % K`.
4. Se o resto já existir no mapa, adicione a frequência desse resto ao seu total de subarrays.
5. Incremente a aparição do resto no mapa.

**Exemplo:**
- **Input:** `arr = [4, 5, 0, -2, -3, 1]`, `K = 5`
- **Output:** `7` (Subarrays: `[5]`, `[5, 0]`, `[0]`, `[-2, -3]`, `[0, -2, -3]`, `[5, 0, -2, -3]`, `[4, 5, 0, -2, -3, 1]`)

#### 12. Maior faixa em dois arrays binários

**Descrição do Problema:** Você recebe dois arrays contendo apenas 0s e 1s, ambos do mesmo tamanho. Encontre o comprimento do maior intervalo idêntico `[i, j]` em ambos os arrays onde a quantidade (soma) de itens dentro do intervalo seja exatamente igual em ambos.

**Passo a Passo Sugerido:**

1. O truque para não iterar infinitamente é reduzir dois arrays em um só usando o padrão de "Array de Diferenças".
2. Crie um array auxiliar onde `aux[i] = arr1[i] - arr2[i]`.
3. Por que isso funciona? Se no intervalo `[i, j]` a soma de `arr1` for igual à soma de `arr2`, a soma de `arr1 - arr2` nesse mesmo intervalo será obrigatoriamente zero.
4. O problema agora se tornou idêntico ao "Encontrar o maior subarray com soma 0", que você já resolveu usando Prefix Sum e Hash Map.

**Exemplo:**
- **Input:** `arr1 = [0, 1, 0, 1, 1, 1, 1]`, `arr2 = [1, 1, 1, 1, 1, 0, 1]`
- **Array Auxiliar:** `[-1, 0, -1, 0, 0, 1, 0]`
- **Output:** `6` (Do índice 1 ao 6, a soma original de ambos é 5. A soma no auxiliar é 0)

#### 13. Maior faixa com a mesma soma (Lógica Avançada Independente)

**Descrição do Problema:** Este exercício reforça o problema 12, mas exige que você otimize a memória. Escreva a mesma lógica **sem** criar o terceiro array `aux`. O espaço de complexidade deve ser rigidamente O(1) de alocação de array novo (usando apenas o mapa).

**Passo a Passo Sugerido:**

1. Em vez de iterar sobre um array auxiliar pré-calculado, você manterá variáveis de prefixo correntes `pref1` e `pref2`.
2. A cada iteração sobre os originais, faça `pref1 += arr1[i]` e `pref2 += arr2[i]`.
3. Calcule imediatamente a diferença `diff = pref1 - pref2`.
4. Procure essa `diff` no seu Hash Map de diferenças passadas. Se ela já ocorreu no índice mais antigo `j`, o comprimento será `i - j`.

**Exemplo:**
- **Input:** `arr1 = [0, 0, 0]`, `arr2 = [1, 1, 1]`
- **Output:** `0` (As diferenças só divergem, nunca se repetem, então não há repetição de soma)

#### 14. Inteiro que mais ocorre em intervalos dados

**Descrição do Problema:** Dada uma vasta lista de intervalos `[L, R]`, descubra qual número inteiro foi coberto pelo maior número de intervalos.

**Aplicações Práticas:** Análise de horários de pico. Se você tem os horários de entrada e saída de vários usuários em um sistema, qual o minuto do dia que teve o maior número de pessoas logadas ao mesmo tempo?

**Passo a Passo Sugerido (Algoritmo de Line Sweep):**

1. Iterar em cada número entre todos os L e R causaria limite de tempo excedido (TLE). Use o padrão "Prefix Sum offline".
2. Crie um grande array de tamanho que comporte o maior número possível no domínio de dados (iniciado com zeros).
3. Para cada intervalo `[L, R]`, marque a entrada somando 1 na posição L (`arr[L] += 1`). E a saída subtraindo 1 logo _após_ o fim do intervalo (`arr[R+1] -= 1`).
4. Ao final, passe o array fazendo uma Prefix Sum sequencial. Magicamente, o valor no índice `i` vai representar o número exato de intervalos sobrepondo aquele número.
5. Retorne o índice que possui o valor máximo de prefixo.

**Exemplo:**
- **Input:** `L = [1, 4, 3, 1]`, `R = [15, 8, 5, 4]` (Isso significa intervalos [1,15], [4,8]...)
- **Output:** `4` (No índice 4, após o Prefix Sum, a soma acumulada atinge o pico)

#### 15. Inteiro que mais ocorre (Otimização Espacial)

**Descrição do Problema:** A mesma premissa do problema 14, mas refinando ainda mais a solução se o intervalo de R for gigantesco ou se quisermos encontrar rapidamente os empates.

**Passo a Passo Sugerido:**

1. Analise o valor máximo existente no array `R` em uma passagem rápida O(N).
2. Aloque seu array de suporte estritamente com tamanho `Max(R) + 2`. Isso economiza alocação excessiva de memória em comparação a um tamanho fixo gigante estático.
3. Ao calcular a Soma de Prefixo no passo final, não gere um array novo. Use uma variável `acumulador_atual` iterando pela matriz e armazene a resposta numa variável separada para evitar o custo de espaço do array pós-processado.

**Exemplo:**
- **Input:** `L=[2, 1, 3]`, `R=[5, 3, 9]`
- **Output:** `3` (O número 3 ocorre dentro de todos os 3 limites)

</details>

<details>
    <summary>🔴 Nível 3 - Difícil</summary>

Onde a matemática plana entra em cena. Lidar com grades bidimensionais exige cuidado absoluto com os índices, normalmente aplicando o **Princípio da Inclusão-Exclusão** da teoria dos conjuntos, mapeado para programação geométrica.

#### 16. Computar matriz anterior

**Descrição do Problema:** Você recebe uma Matriz de Prefixos 2D. Esta matriz foi gerada de forma que cada célula `(i, j)` seja a soma de todos os valores originais formando um retângulo desde a origem superior esquerda `(0,0)` até o ponto inferior direito `(i,j)`. Sua tarefa é restaurar a matriz original que gerou esses prefixos.

**O Princípio da Inclusão-Exclusão:** Se você tem a área total `(i, j)` e quer saber só o valor pontual daquela célula, precisa pegar a área total, retirar a área que estava acima e a área que estava à esquerda. Mas ao retirar ambas, você acabou retirando a área da diagonal superior esquerda DUAS vezes, então você precisa somá-la novamente para compensar.

**Passo a Passo Sugerido:**

1. Percorra a matriz de prefixos, preferencialmente de trás para frente ou salvando em uma nova matriz para não sobrescrever dados necessários.
2. O valor original na posição `(i, j)` será calculado como: `M[i][j] - M[i-1][j] - M[i][j-1] + M[i-1][j-1]`.
3. Cuide das bordas com muito cuidado. Na linha zero ou coluna zero, os valores de "cima" ou "esquerda" serão considerados 0.

**Exemplo:**
- **Input - Matriz de Prefixos:** `[[2, 5], [7, 14]]`
- **Output - Matriz Original:** `[[2, 3], [5, 4]]` (Para a célula (1,1) onde tínhamos 14, fizemos: 14 - 7 - 5 + 2 = 4)

#### 17. Maior submatriz com soma 0

**Descrição do Problema:** Dada uma matriz contendo valores positivos e negativos, você precisa encontrar um "retângulo" dentro da matriz (submatriz) cujos elementos somem exatamente zero, e este retângulo precisa ter a maior área (maior número de células) de todas as opções de soma 0.

**Passo a Passo Sugerido:**

1. A abordagem por força bruta em matrizes para todas as submatrizes é O(N^6) ou O(N^4), o que é terrível. Para otimizar, faremos a técnica de Compressão 1D.
2. Crie dois loops aninhados que ancoram a "Coluna Esquerda (L)" e a "Coluna Direita (R)" da matriz. O que estamos fazendo é definir uma "largura de parede" e varrer da esquerda para a direita.
3. Crie um array temporário de tamanho igual ao número de linhas. Quando a coluna R avançar, adicione o valor de cada célula à sua respectiva linha nesse array temporário.
4. Agora vem a genialidade: o array temporário de 1 dimensão representa as linhas "esmagadas" desse retângulo. Tudo que você tem que fazer agora é passar esse array de 1 dimensão pelo algoritmo que você construiu lá no **Exercício 7 e 9** (Maior subarray contíguo 1D com soma 0).
5. A área máxima será o tamanho máximo encontrado na função 1D multiplicado pela largura das colunas analisadas `(R - L + 1)`. Mantenha a maior global.

**Exemplo:**
- **Input - Matriz:**
    ```
    [[ 9,  7, 16,  5],
     [ 1, -6, -7,  3],
     [ 1,  8,  7,  9],
     [ 7, -2,  0, 10]]
    ```
- **Output:** `6` (Isso forma um retângulo 2x3 ou 3x2 dentro da matriz cuja soma zera)

#### 18. Retângulo de soma máxima

**Descrição do Problema:** Dada uma matriz com números aleatórios, ache a submatriz cuja soma de seus componentes crie o maior valor absoluto positivo possível.

**Aplicações Práticas:** Conhecido popularmente no meio científico como Algoritmo de Kadane 2D, é crucial em computação gráfica para encontrar a região mais brilhante em uma imagem.

**Passo a Passo Sugerido:**

1. Assim como no exercício anterior, use os "ponteiros fixadores" L e R nas colunas. Isso fixará a dimensão horizontal.
2. "Esmague" horizontalmente os elementos dentro dessas colunas usando uma Prefix Sum temporária. Isso vai compactar a matriz 2D para um array temporal 1D a cada iteração de R.
3. Submeta este array 1D ao clássico Algoritmo de Kadane de soma máxima (visto superficialmente no Exercício 6 de soma mínima).
4. Essa combinação de 2 loops fixadores (O(Colunas²)) com 1 loop de Kadane (O(Linhas)) resulta em uma complexidade O(C² × L), extremamente mais eficiente que a versão ingênua O(N⁴).

**Exemplo:**
- **Input - Matriz:**
    ```
    [[ 1,  2, -1, -4, -20],
     [-8, -3,  4,  2,   1],
     [ 3,  8, 10,  1,   3],
     [-4, -1,  1,  7,  -6]]
    ```
- **Output:** `29` (Formada pela submatriz de pico `[[4, 2], [10, 1], [1, 7]]`)

#### Dicas Finais para seus Estudos

Ao codificar esses exercícios, você provavelmente se deparará com falhas no compilador devido a índices errados ("Out of Bounds") ou respostas erradas porque a soma deixou um elemento de fora. Isso é chamado de **Off-By-One Error** e é o maior inimigo de quem aprende Prefix Sum.

**Três regras de ouro para não errar:**

1. Sempre desenhe o array num pedaço de papel antes de digitar, apontando para os índices com canetas de cores diferentes.
2. Em consultas do tipo `[L, R]`, lembre-se que se a fórmula for `Prefixo[R] - Prefixo[L-1]`, o índice L pode ser 0, forçando um acesso a índice -1. Escreva um bloco `if (L == 0)` explícito ou utilize **arrays 1-based** (arrays onde você insere um `0` inofensivo na primeira posição do prefixo para que todos os índices desloquem +1 e L nunca cause overflow negativo).
3. Nunca modifique o array original (a menos que a restrição espacial seja O(1) extremo). Aloque sempre um novo array para a Prefix Sum e salve dores de cabeça com rastreio de memória corrompida.

**Bons estudos e ótimo código!**

</details>
