
# Lista de Exercícios - Algoritmos de Busca

Este documento fortalece a lógica de programação através da resolução de problemas clássicos e avançados de algoritmos de busca. Os exercícios estão divididos por nível de dificuldade e cobrem os principais padrões algorítmicos exigidos em entrevistas técnicas e competições de programação.

Para cada problema, você encontrará: descrição, entrada (Input) e saída (Output) esperadas, um roteiro lógico agnóstico a linguagens de programação (C, C++, Java, Python, TypeScript, Go, etc.), complexidades de tempo e espaço (Big-O), casos extremos (Edge Cases) e uma Dica de Ouro para identificar o padrão.

<details>
    <summary>🟢 Nível 1 - Fácil</summary>

Problemas de nível fácil exigem domínio de estruturas de repetição, lógica condicional básica e introdução a ponteiros e matemática simples aplicada a arrays. O objetivo é otimizar soluções de Força Bruta O(N²) para O(N) ou O(logN).

### 1. Missing Number

**Descrição:** Dado um array contendo N-1 números distintos no intervalo de 1 a N, encontre o número que está faltando.

**Input:** Um array de inteiros e o valor N. (Ex: `arr = [1, 2, 4, 6, 3, 7, 8], N = 8`)

**Output:** O número inteiro ausente. (Ex: `5`)

**Passo a Passo:**
1. Calcule a soma esperada usando a fórmula: `Soma = N * (N + 1) / 2`
2. Percorra o array fornecido e calcule a soma de todos os elementos presentes.
3. Subtraia a soma real da soma teórica. O resultado é o número faltando.

**Complexidade:** Tempo O(N) | Espaço O(1)

**Casos Extremos:** Array onde o número faltando é o primeiro (1) ou o último (N). Arrays vazios se N=1.

**Dica de Ouro:** Em linguagens estritamente tipadas, a soma `N*(N+1)` pode causar Integer Overflow. Uma alternativa é usar a operação lógica XOR (`^`).

### 2. Second Largest

**Descrição:** Encontre o segundo maior elemento distinto em um array não ordenado.

**Input:** Um array de inteiros. (Ex: `arr = [12, 35, 1, 10, 34, 1]`)

**Output:** O valor do segundo maior elemento, ou `-1` se não houver. (Ex: `34`)

**Passo a Passo:**
1. Inicialize `maior` e `segundo_maior` com o menor valor possível.
2. Percorra o array elemento por elemento em uma única passagem.
3. Se o elemento atual for maior que `maior`, atualize `segundo_maior` para o valor antigo de `maior` e depois atualize `maior`.
4. Se o elemento for menor que `maior` mas maior que `segundo_maior`, atualize apenas `segundo_maior`.

**Complexidade:** Tempo O(N) | Espaço O(1)

**Casos Extremos:** Array com elementos idênticos (deve retornar `-1`). Array com menos de dois elementos.

**Dica de Ouro:** Evite ordenar o array (O(NlogN)). Uma única travessia (O(N)) demonstra melhor domínio da manipulação de estados.

### 3. Common in Three Sorted Arrays

**Descrição:** Dados três arrays já ordenados, encontre os elementos comuns a todos os três simultaneamente.

**Input:** Três arrays de inteiros ordenados. (Ex: `A = [1, 5, 10], B = [3, 4, 5, 10], C = [5, 10, 20]`)

**Output:** Um array com os elementos comuns. (Ex: `[5, 10]`)

**Passo a Passo:**
1. Utilize três ponteiros (índices independentes), um para cada array, todos iniciando na posição 0.
2. Use um laço enquanto nenhum ponteiro ultrapassar o limite do seu respectivo array.
3. Se os três elementos apontados forem iguais, adicione ao resultado e avance os três ponteiros.
4. Se não forem iguais, identifique qual é o menor e avance apenas esse ponteiro.

**Complexidade:** Tempo O(N₁+N₂+N₃) | Espaço O(1) (ignorando o espaço da resposta)

**Casos Extremos:** Arrays de tamanhos drasticamente diferentes. Repetição consecutiva do elemento comum (evitar duplicatas).

**Dica de Ouro:** Este é um excelente exemplo do padrão "Multiple Pointers". Aproveitar a ordenação prévia evita um problema O(N³).

### 4. Transition Point in Binary Array

**Descrição:** Dado um array binário ordenado (0s seguidos por 1s), encontre o índice onde ocorre a primeira transição de 0 para 1.

**Input:** Um array binário ordenado. (Ex: `arr = [0, 0, 0, 1, 1]`)

**Output:** O índice do primeiro 1, ou `-1` se não houver. (Ex: `3`)

**Passo a Passo:**
1. Aplique Busca Binária. Defina `inicio = 0` e `fim = tamanho - 1`.
2. Encontre o índice do `meio`.
3. Se `arr[meio] == 0`, a transição está na metade direita: `inicio = meio + 1`.
4. Se `arr[meio] == 1`, verifique se é o primeiro: `meio == 0` ou `arr[meio-1] == 0`. Se sim, retorne `meio`. Senão: `fim = meio - 1`.

**Complexidade:** Tempo O(logN) | Espaço O(1)

**Casos Extremos:** Array contendo apenas zeros ou apenas uns.

**Dica de Ouro:** Busca Binária não serve apenas para encontrar valores exatos, mas também "limites" ou "padrões", como transições.

### 5. Floor in Sorted Array

**Descrição:** Dado um array ordenado e um valor alvo X, encontre o "piso" (floor) de X: o maior elemento no array menor ou igual a X.

**Input:** Um array ordenado e um inteiro X. (Ex: `arr = [1, 2, 8, 10, 11, 12, 19], X = 5`)

**Output:** O índice do piso de X, ou `-1` se não existir. (Ex: `1` correspondente ao valor `2`)

**Passo a Passo:**
1. Utilize Busca Binária. Mantenha uma variável auxiliar `resultado = -1`.
2. Calcule o `meio`. Se `arr[meio] == X`, retorne `meio`.
3. Se `arr[meio] < X`, este é um candidato válido: salve `resultado = meio` e busque à direita: `inicio = meio + 1`.
4. Se `arr[meio] > X`, ignore a metade direita: `fim = meio - 1`.

**Complexidade:** Tempo O(logN) | Espaço O(1)

**Casos Extremos:** X menor que todos os elementos. X maior que o último elemento.

**Dica de Ouro:** A variável `resultado` atua como memória de "melhor aproximação". Variantes de Busca Binária continuam refinando mesmo após encontrar correspondências.

### 6. Pair with Difference

**Descrição:** Dado um array e um valor alvo N, descubra se existe algum par de elementos cuja diferença absoluta seja exatamente igual a N.

**Input:** Um array e um inteiro N. (Ex: `arr = [5, 20, 3, 2, 5, 80], N = 78`)

**Output:** Um valor booleano (True ou False). (Ex: `True` para o par [2, 80])

**Passo a Passo:**
1. Ordene o array em ordem crescente.
2. Utilize dois ponteiros: `i = 0` (ponteiro lento) e `j = 1` (ponteiro rápido).
3. Calcule `diff = arr[j] - arr[i]`.
4. Se `diff == N` e `i != j`, retorne `True`.
5. Se `diff < N`, avance `j++` para aumentar a diferença.
6. Se `diff > N`, avance `i++` para diminuir a diferença.

**Complexidade:** Tempo O(NlogN) | Espaço O(1) ou O(N) dependendo do algoritmo de ordenação

**Casos Extremos:** N = 0 (busca por números duplicados). Arrays muito curtos ou com números negativos.

**Dica de Ouro:** Alternativamente, use uma Tabela Hash (HashSet). Para cada número `num`, verifique se `num - N` ou `num + N` existe no conjunto. Complexidade O(N).

### 7. Square Root

**Descrição:** Dado um número inteiro X, retorne a raiz quadrada inteira de X. Se não for um quadrado perfeito, retorne apenas a parte inteira (piso).

**Input:** Um número inteiro X. (Ex: `X = 11`)

**Output:** A parte inteira da raiz quadrada. (Ex: `3`, pois 3²=9 e 4²=16)

**Passo a Passo:**
1. Trate casos base: se X é 0 ou 1, retorne X.
2. Configure Busca Binária com `inicio = 1` e `fim = X / 2` (para X>1, a raiz nunca ultrapassa sua metade).
3. Calcule `meio`. Se `meio * meio == X`, retorne `meio`.
4. Se `meio * meio < X`, guarde `resultado = meio` e busque à direita: `inicio = meio + 1`.
5. Se `meio * meio > X`, busque à esquerda: `fim = meio - 1`.

**Complexidade:** Tempo O(logX) | Espaço O(1)

**Casos Extremos:** Números absurdamente grandes podem causar Integer Overflow.

**Dica de Ouro:** Em vez de `meio * meio > X`, use `meio > X / meio` para evitar overflow.

### 8. Rotation Count

**Descrição:** Um array inicialmente ordenado em ordem crescente foi "rotacionado" um número desconhecido de vezes. Encontre quantas rotações sofreu. A quantidade equivale ao índice do menor elemento.

**Input:** Um array rotacionado. (Ex: `arr = [15, 18, 2, 3, 6, 12]`)

**Output:** Um inteiro representando a quantidade de rotações. (Ex: `2` referente ao índice do valor `2`)

**Passo a Passo:**
1. Use Busca Binária com `inicio = 0` e `fim = tamanho - 1`.
2. Se `arr[inicio] <= arr[fim]`, o array não sofreu rotação real: retorne `inicio` (0).
3. Calcule `meio`. Se o elemento é menor que ambos os vizinhos, é a anomalia (menor). Retorne `meio`.
4. Se a porção `[inicio...meio]` está ordenada, o mínimo está em `[meio+1...fim]`: `inicio = meio + 1`.
5. Senão, o mínimo está em `[inicio...meio]`: `fim = meio - 1`.

**Complexidade:** Tempo O(logN) | Espaço O(1)

**Casos Extremos:** Array com 1 ou 2 elementos. Arrays rotacionados perfeitamente.

**Dica de Ouro:** A "quebra de monotonicidade" é chave. Uma das duas metades sempre está linearmente ordenada.

### 9. Matrix Sorted Search

**Descrição:** Você recebe uma matriz onde todas as linhas e colunas estão ordenadas. Busque pelo alvo X de maneira otimizada.

**Input:** Uma matriz M×N e um número alvo X. (Ex: `mat = [[10, 20, 30], [15, 25, 35], [27, 29, 37]], X = 29`)

**Output:** True/False ou as coordenadas (linha, coluna). (Ex: `True` ou `[2, 1]`)

**Passo a Passo:**
1. Comece no canto superior direito: `i = 0, j = n - 1`.
2. Compare o valor atual com X.
3. Se forem iguais, encontrou.
4. Se X é menor que o elemento atual, X não está embaixo desta coluna: `j--`.
5. Se X é maior, X não está à esquerda desta linha: `i++`.
6. Repita até encontrar ou sair dos limites.

**Complexidade:** Tempo O(M+N) | Espaço O(1)

**Casos Extremos:** Matriz nula. X drasticamente menor ou maior que os extremos.

**Dica de Ouro:** Começar do canto superior direito transforma o grid em um comportamento similar a uma Árvore de Busca Binária.

### 10. Bitonic Peak Search

**Descrição:** Identifique o pico máximo em um array "bitônico" que sobe estritamente até um ponto e depois desce estritamente.

**Input:** Um array bitônico. (Ex: `arr = [1, 3, 50, 10, 9, 7, 6]`)

**Output:** O maior número (pico). (Ex: `50`)

**Passo a Passo:**
1. Use Busca Binária com `inicio = 0` e `fim = tamanho - 1`.
2. Encontre `meio`. Se é maior que ambos os vizinhos, é o pico.
3. Se `arr[meio] < arr[meio + 1]`, ainda está subindo: `inicio = meio + 1`.
4. Se `arr[meio] < arr[meio - 1]`, já passou do pico: `fim = meio - 1`.

**Complexidade:** Tempo O(logN) | Espaço O(1)

**Casos Extremos:** Pico nas extremidades. Necessário cuidado com limites de índices.

**Dica de Ouro:** A variação pontual entre elementos adjacentes é suficiente para mapear o comportamento da curva.

</details>

<details>
    <summary>🟠 Nível 2 - Médio</summary>

Problemas médios combinam técnicas e aumentam a complexidade. Abordagens ingênuas resultam em erro "Time Limit Exceeded" (TLE).

### 1. Search in Rotated Sorted Array

**Descrição:** Busque um elemento X em um array originalmente ordenado mas que sofreu rotação. Complexidade estritamente logarítmica.

**Input:** Array rotacionado e valor alvo X. (Ex: `arr = [5, 6, 7, 8, 9, 10, 1, 2, 3], X = 3`)

**Output:** O índice real do elemento, ou `-1` se ausente. (Ex: `8`)

**Passo a Passo:**
1. Configure a Busca Binária clássica.
2. Ao calcular `meio`, descubra onde está a "porção ordenada".
3. Se a metade esquerda está ordenada (`arr[inicio] <= arr[meio]`), verifique se X reside nesse intervalo (`arr[inicio] <= X < arr[meio]`). Se sim, busque à esquerda. Senão, à direita.
4. Se falhar, a metade direita está obrigatoriamente ordenada. Repita o raciocínio.

**Complexidade:** Tempo O(logN) | Espaço O(1)

**Casos Extremos:** Valores duplicados (ex: `[1, 0, 1, 1, 1]`) tornam o algoritmo linear no pior caso.

**Dica de Ouro:** Encontre o "refúgio da ordem" e pergunte se o alvo se enquadra nessa janela.

### 2. Majority Element

**Descrição:** Detecte o elemento majoritário que aparece estritamente mais de ⌊N/2⌋ vezes.

**Input:** Um array preenchido de tamanho N. (Ex: `arr = [3, 1, 3, 3, 2]`)

**Output:** O número majoritário. (Ex: `3`)

**Passo a Passo:**
1. Implemente o Algoritmo de Votação de Boyer-Moore (O(1) espaço).
2. Assuma o primeiro elemento como `candidato` com `contador = 1`.
3. Percorra do segundo elemento em diante. Se encontrar `candidato`, incremente `contador`. Se encontrar diferente, decremente.
4. Se `contador` chegar a zero, o novo elemento assume a candidatura.
5. Ao final, o `candidato` sobrevivente é a melhor chance. Verifique em uma segunda passagem que aparece mais de N/2 vezes.

**Complexidade:** Tempo O(N) | Espaço O(1)

**Casos Extremos:** Array sem elemento com maioria absoluta.

**Dica de Ouro:** Diferentes destroem uns aos outros. Como o majoritário tem >50%, invariavelmente "vence".

### 3. K'th Smallest/Largest in Unsorted Array

**Descrição:** Isole o K-ésimo menor (ou maior) elemento em um array não ordenado.

**Input:** Um array bruto e seletor K. (Ex: `arr = [7, 10, 4, 3, 20, 15], K = 3`)

**Output:** O número na posição correta. (Ex: `7`)

**Passo a Passo:**
1. Use o Algoritmo Quickselect baseado na estrutura do QuickSort.
2. Selecione um "pivô" arbitrariamente (geralmente o último elemento).
3. Particione: reorganize para que elementos menores fiquem à esquerda e maiores à direita.
4. Compare a posição do pivô com K-1. Se igual, encontrou. Se maior, busque à esquerda. Senão, à direita.

**Complexidade:** Tempo O(N) em média (O(N²) pior caso) | Espaço O(1) iterativo

**Casos Extremos:** K fora dos limites. Array já ordenado inversamente.

**Dica de Ouro:** Heap (Min-Heap/Max-Heap) oferece alternativa robust O(NlogK) em dados fluxo.

### 4. Count Frequency in Sorted Array

**Descrição:** Calcule quantas vezes o valor alvo X aparece em um array pré-ordenado.

**Input:** Um array linearmente organizado e chave X. (Ex: `arr = [1, 1, 2, 2, 2, 2, 3], X = 2`)

**Output:** A frequência de X. (Ex: `4`)

**Passo a Passo:**
1. Evite varredura linear O(N). Use Busca Binária.
2. Crie uma busca modificada para encontrar a **primeira ocorrência**. Continue mesmo após encontrar, deslocando limites à esquerda.
3. Crie outra busca modificada para encontrar a **última ocorrência**, deslocando à direita.
4. Calcule: `(last_occurrence - first_occurrence) + 1`. Se não encontrado, retorne `0`.

**Complexidade:** Tempo O(logN) | Espaço O(1)

**Casos Extremos:** Array composto integralmente por X. X inexistente.

**Dica de Ouro:** Compreender deslocamentos de limites separa profissionais sêniors de juniores.

### 5. Peak Element

**Descrição:** Identifique um elemento topológico tal que é expressivamente maior ou igual aos vizinhos imediatos.

**Input:** Array terreno misto. (Ex: `arr = [10, 20, 15, 2, 23, 90, 67]`)

**Output:** O índice do pico. (Ex: `1` [valor `20`] ou `5` [valor `90`])

**Passo a Passo:**
1. Use Busca Binária com `inicio = 0, fim = N - 1`.
2. Examine `meio`. Se é maior que vizinhos, é pico.
3. Se `arr[meio] < arr[meio + 1]`, progride para direita: `inicio = meio + 1`.
4. Se `arr[meio] < arr[meio - 1]`, recua para esquerda: `fim = meio - 1`.

**Complexidade:** Tempo O(logN) | Espaço O(1)

**Casos Extremos:** Sequências monótonas longas. Crateras centrais.

**Dica de Ouro:** Seguir a encosta que sobe garante encontrar um pico.

### 6. Smallest Missing Positive

**Descrição:** Encontre o inteiro positivo mais prematuro evadido em um array caótico não ordenado. Restrições: O(N) tempo, O(1) espaço.

**Input:** Caldeirão caótico. (Ex: `arr = [3, 4, -1, 1]`)

**Output:** A vacância. (Ex: `2`)

**Passo a Passo:**
1. Use Cyclic Sort. O vetor atua como tabela hash. Forçar número X na coordenada X-1.
2. Percorra. Se número X pertence a [1...N], verifique se está no lugar correto (índice X-1). Se não, troque com occupante incorreto repetidamente até estabilizar ou encontrar lixo.
3. Segunda varredura linear: encontre primeiro índice onde `arr[i] != i + 1`. Resposta é `i + 1`.
4. Se todos batem, resposta é `N + 1`.

**Complexidade:** Tempo O(N) | Espaço O(1)

**Casos Extremos:** Array só de negativos. Clones numéricos (evitar loops infinitos verificando equivalência antes de swap).

**Dica de Ouro:** Cyclic Sort economiza memória extra mapeando indices naturais.

### 7. All Triplets with Zero Sum

**Descrição:** Desmascare a existência de três constituintes cuja soma é zero.

**Input:** Um arranjo. (Ex: `arr = [0, -1, 2, -3, 1]`)

**Output:** Valor booleano ou triplas. (Ex: `True` para `[-1, 0, 1]`)

**Passo a Passo:**
1. Ordene o array.
2. Fixe o primeiro número num loop (índice `i`).
3. Use Two Pointers no restante: `inicio = i + 1`, `fim = tamanho - 1`.
4. Se soma for zero, adicione ao resultado e avance ponteiros.
5. Se soma negativa, avance `inicio++`. Se positiva, recue `fim--`.
6. Para evitar duplicatas, salte valores repetidos.

**Complexidade:** Tempo O(N²) | Espaço O(1) ou dependente da ordenação

**Casos Extremos:** Todos positivos (nenhuma soma zero). Arrays repletos de zeros.

**Dica de Ouro:** Blocos `if` avançando sobre duplicatas evitam triplas repetidas.

### 8. First and Last Positions in Sorted Array

**Descrição:** Delimite as guaritas fronteiriças de ingresso e terminação da aparição de um elemento.

**Input:** Array ordenado e valor X. 

**Output:** Posições reais [first, last]. Se ausente, `[-1, -1]`.

**Passo a Passo:**
1. Programe duas sub-rotinas separadas para Busca Binária.
2. Na função "primeira ocorrência": ao encontrar X, salve e continue à esquerda (`fim = meio - 1`).
3. Na função "última ocorrência": ao encontrar X, salve e continue à direita (`inicio = meio + 1`).
4. Retorne ambos índices.

**Complexidade:** Tempo O(logN) | Espaço O(1)

**Casos Extremos:** X não existe.

**Dica de Ouro:** Separação conceitual em duas funções torna código robusto e legível (Clean Code).

### 9. Two Repeating Elements

**Descrição:** Extraia a identidade dos dois clones numéricos em um array onde números variam de 1 a N e há N+2 espaços (força exatamente 2 repetições).

**Input:** População aglomerada. (Ex: `arr = [4, 2, 4, 5, 2, 3, 1], N = 5`)

**Output:** Os dois falsários. (Ex: `4` e `2`)

**Passo a Passo:**
1. Garanta O(N) tempo e O(1) espaço corrompendo intencionalmente o array.
2. Percorra sequencialmente. Para cada número `num`, transforme `abs(num)` em índice.
3. Visite a casa correspondente `arr[abs(num) - 1]` e negativize seu valor como "marcação".
4. Se encontrar valor já negativizado em futura iteração, aquele `abs(num)` é um dos repetidos.

**Complexidade:** Tempo O(N) | Espaço O(1)

**Casos Extremos:** Preservar dados originais após execução (aplicar `abs()` novamente no final).

**Dica de Ouro:** Negativar como flag booleano dentro do próprio vetor é um dos truques O(1) mais formidáveis.

### 10. Single in Sorted Array

**Descrição:** Em um cenário onde todo elemento caminha em pares idênticos, extraia a anomalia solitária em logarítmico.

**Input:** Soldados gêmeos e um desertor. (Ex: `arr = [1, 1, 2, 2, 3, 4, 4, 5, 5]`)

**Output:** O solitário. (Ex: `3`)

**Passo a Passo:**
1. Configure Busca Binária: `inicio = 0, fim = N - 1`.
2. Em pista ininterrupta, gêmeos ocupam índices pares (0,2,4) e seus clones os ímpares (1,3,5).
3. Se `meio % 2 == 0`, verifique se `arr[meio] == arr[meio+1]`. Se sim, pista limpa à direita: `inicio = meio + 2`.
4. Se verificação falha, o solitário está à esquerda: `fim = meio` ou `fim = meio - 1`.

**Complexidade:** Tempo O(logN) | Espaço O(1)

**Casos Extremos:** Solitário na borda. Cuidado com Array Index Out of Bounds.

**Dica de Ouro:** Paridade de índice é genialidade pura para buscas estruturais.

### 11. Two Elements with Sum Closest to Zero

**Descrição:** Encontre dois elementos cuja soma se aproxime máximo do zero.

**Input:** Array de positivos e negativos. (Ex: `arr = [1, 60, -10, 70, -80, 85]`)

**Output:** Os dois elementos. (Ex: `-80` e `85`, soma = `5`)

**Passo a Passo:**
1. Ordene crescentemente.
2. Two Pointers: `esq = 0`, `dir = N - 1`.
3. Arquive a menor soma absoluta em `menor_soma_absoluta`.
4. Calcule `soma = arr[esq] + arr[dir]`. Se `abs(soma) < abs(menor_soma_absoluta)`, atualize.
5. Se `soma < 0`, avance esquerda (`esq++`). Se `soma > 0`, recue direita (`dir--`).

**Complexidade:** Tempo O(NlogN) | Espaço O(1)

**Casos Extremos:** Array com apenas dois elementos. Todos da mesma polaridade.

**Dica de Ouro:** Use `abs()` ao guardar melhor soma, mas nunca ao decidir mover ponteiros.

### 12. Count ≤ Elements from 2nd Array

**Descrição:** Para cada elemento de A, conte quantos elementos em B são menores ou iguais.

**Input:** Dois arrays A e B. (Ex: `A = [1, 2, 3, 4, 7, 9], B = [0, 1, 2, 1, 1, 4]`)

**Output:** Array de contagens pareadas. (Ex: `[4, 5, 5, 6, 6, 6]`)

**Passo a Passo:**
1. Ordene B.
2. Para cada elemento em A, use Busca Binária (upper_bound) em B.
3. A posição retornada é exatamente a contagem de elementos ≤ ao elemento de A.

**Complexidade:** Tempo O(MlogM + NlogM) | Espaço O(1) ou O(resultado)

**Casos Extremos:** B vazio. Todos elementos maiores/menores.

**Dica de Ouro:** C++ oferece `upper_bound()`. Python oferece `bisect.bisect_right()`.

### 13. Smallest Number with n Factorial Zeros

**Descrição:** Ache o menor M tal que M! tenha no mínimo N zeros finais.

**Input:** Valor alvo N.

**Output:** O número gerador M.

**Passo a Passo:**
1. Zeros finais vêm de fatores 10 (2×5). Em fatoriais, "5" é o gargalo.
2. Crie função O(logX): `contaFatores5(X) = (X/5) + (X/25) + (X/125)...`
3. Busca Binária na resposta: `inicio = 0, fim = 5*N`.
4. Se `contaFatores5(meio) >= N`, guarde e busque menores (`fim = meio - 1`). Senão, busque maiores.

**Complexidade:** Tempo O(log²(5N)) | Espaço O(1)

**Casos Extremos:** N=0.

**Dica de Ouro:** Quantidade de fator primo P em X! = sum(⌊X/P^k⌋).

### 14. K'th Smallest in Given N Ranges

**Descrição:** Combine intervalos mesclando sobreposições e encontre o K-ésimo valor.

**Input:** Array de intervalos `[[1, 4], [6, 8]]`, K=6.

**Output:** `7`.

**Passo a Passo:**
1. Merge Intervals: ordene, depois mescle quando `inicio_atual <= fim_anterior`.
2. Para query K, viaje pelos intervalos mesclados.
3. Calcule tamanho: `fim - inicio + 1`.
4. Se K ≤ tamanho, resposta é `inicio + K - 1`. Senão, `K -= tamanho`, próximo intervalo.

**Complexidade:** Tempo O(NlogN + Q×N) | Espaço O(N)

**Dica de Ouro:** Com Q massivo, prefira Prefix Sum + Busca Binária: O(QlogN).

### 15. Minimum Repeats for Substring

**Descrição:** Mínimo de concatenações de A para absorver B como substring.

**Input:** `A = "abcd"`, `B = "cdabcdab"`.

**Output:** `3`.

**Passo a Passo:**
1. Enquanto `len(A_clonada) < len(B)`, concatene A e incremente contador.
2. Verifique se B está em A_clonada.
3. Se não, adicione A uma vez mais e verifique novamente.

**Complexidade:** Tempo O(N×M) sem otimizações.

**Dica de Ouro:** KMP reduz para O(N+M).

### 16. Remove Coins for ≤ K Difference

**Descrição:** Mínimo de moedas a sacar até a variação entre torres ≤ K.

**Input:** Torres `[1, 5, 1, 2, 5, 1]`, K=3.

**Output:** `2`.

**Passo a Passo:**
1. Ordene: `[1, 1, 1, 2, 5, 5]`.
2. Para cada elemento i como piso, teto é `arr[i] + K`.
3. Remova tudo acima do teto. Totalize remoções.
4. Retenha mínimo.

**Complexidade:** Tempo O(NlogN) | Espaço O(N)

**Dica de Ouro:** Simular num array ordenado simplifica cálculos.

</details>

<details>
    <summary>🔴 Nível 3 - Difícil</summary>

Problemas difíceis utilizam "Binary Search on Answer" e otimizações avançadas.

### 1. Median of Two Sorted Arrays

**Descrição:** Extraia a mediana fundida de dois arrays sem usar memória extra. Complexidade obrigatória: O(log(min(N,M))).

**Input:** Dois arrays A e B.

**Output:** A mediana.

**Passo a Passo:**
1. Aplique Busca Binária exclusivamente no array menor A.
2. Particione ambos em duas metades balanceadas.
3. Garanta para cada partição: `esquerda_A <= direita_B` E `esquerda_B <= direita_A`.
4. Se violado, desloque o corte em A. Caso contrário, calcule a mediana.

**Complexidade:** Tempo O(log(min(N,M))) | Espaço O(1)

**Dica de Ouro:** Particione, não busque. O segredo é dividir em duas metades perfeitamente balanceadas.

### 2. Book Allocation Problem

**Descrição:** Particione livros entre estudantes garantindo contiguidade. Minimize o máximo de páginas alocadas.

**Input:** Array de páginas dos livros, número de estudantes.

**Output:** Mínimo do máximo.

**Passo a Passo:**
1. Busca Binária no espaço de resposta: de `max(arr)` a `sum(arr)`.
2. Para cada "chute" (teste), valide se é possível distribuir livros.
3. Crie função `isPossible(maxPages, students)`: simule contígua e conte quantos estudantes precisam.
4. Se possível com limite testado, busque menores. Senão, busque maiores.

**Complexidade:** Tempo O(Nlog(Soma))

**Dica de Ouro:** A filosofia: teste um "chute", veja se distribui, refine.

### 3. Painter's Partition

**Descrição:** Clone isomórfico de Book Allocation. Pinte quadros adjacentes com limite de tinta.

**Complexidade:** Tempo O(Nlog(Soma dos Quadros))

**Dica de Ouro:** Mesma estrutura. Simule "rolo de pintura" até esgotar a tinta fixa testada.

### 4. Aggressive Cows

**Descrição:** Afaste vaquinhas minimizando aglomeração. Maximize a distância mínima entre duas.

**Input:** Posições de baias, número de vaquinhas.

**Output:** Máxima distância mínima.

**Passo a Passo:**
1. Ordene posições de baias.
2. Busca Binária no espaço de resposta: de `0` a `max - min`.
3. Para cada "chute" de distância, valide quantas vaquinhas cabem mantendo essa distância.

**Complexidade:** Tempo O(NlogN + Nlog(MaxDist))

**Dica de Ouro:** Mesma estratégia: teste, valide, refine.

### 5. Split Array to Minimize Max Sum

**Descrição:** Divida array em K sub-arrays minimizando o máximo da soma agregada.

**Complexidade:** Tempo O(NlogS)

**Dica de Ouro:** Todos estes problemas ("Binary Search on Answer") usam a mesma armação.

### 6. Maximize Min Flower Height

**Descrição:** Regue flores com aspersor de raio W usando ações limitadas. Maximize a altura mínima final.

**Passo a Passo:**
1. Busca Binária: de altura `0` a altura `max`.
2. Para cada altura alvo, verifique se é alcançável.
3. Use Sliding Window / Difference Array para simular rega em O(N).
4. Maneje potencial overflow rastreando água acumulada.

**Complexidade:** Tempo O(NlogH)

**Dica de Ouro:** Avoid O(N×W) loops. Use Window Slide.

</details>

