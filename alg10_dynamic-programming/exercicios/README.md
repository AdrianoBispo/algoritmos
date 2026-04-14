# Lista de Exercícios - Programação Dinâmica

Esta lista foi elaborada para fortalecer a sua lógica de programação através da técnica de **Programação Dinâmica (DP - Dynamic Programming)**. O objetivo deste documento não é fornecer código pronto para copiar e colar, mas sim o raciocínio analítico necessário para modelar o **estado** e a **transição** de cada problema. Isso permitirá que você resolva os desafios na linguagem de programação de sua preferência (C, Python, Java, Go, Typescript, etc.).

---

<details>
<summary>🟢 Nível 1 - Fácil</summary>

Estes problemas são focados em reconhecimento de padrões simples (sequências matemáticas) e modelagem de estado unidimensional.

### 1. Números de Fibonacci

- **Descrição:** Calcule o enésimo termo da sequência de Fibonacci. A sequência começa com 0 e 1, e cada número subsequente é a soma dos dois anteriores.
- **Passo a passo:** 1. Defina o estado `dp[i]` como o i-ésimo número de Fibonacci. 2. Inicialize os casos base: `dp[0] = 0` e `dp[1] = 1`. 3. Para `i` de 2 até `n`, calcule: `dp[i] = dp[i-1] + dp[i-2]`.
- **Complexidade:** Tempo: `O(n)`. Espaço: `O(n)` com array, otimizável para `O(1)`.
- **Input:** Um número inteiro `n` (ex: `5`).
- **Output:** O valor correspondente na sequência (ex: `5`).

### 2. Números Tribonacci

- **Descrição:** Variação do Fibonacci onde cada termo é a soma dos **três** anteriores.
- **Passo a passo:** 1. Estado: `dp[i]` é o i-ésimo termo. 2. Casos base: `dp[0] = 0`, `dp[1] = 1`, `dp[2] = 1`. 3. Transição: `dp[i] = dp[i-1] + dp[i-2] + dp[i-3]`.
- **Complexidade:** Tempo: `O(n)`. Espaço: `O(n)`, otimizável para `O(1)`.
- **Input:** Um número inteiro `n` (ex: `4`).
- **Output:** O enésimo número Tribonacci (ex: `2`).

### 3. Números de Lucas

- **Descrição:** Sequência com lógica similar a Fibonacci, mas com valores sementes diferentes (2 e 1).
- **Passo a passo:** 1. Estado: `dp[i]` é o i-ésimo termo de Lucas. 2. Casos base: `dp[0] = 2`, `dp[1] = 1`. 3. Transição: `dp[i] = dp[i-1] + dp[i-2]`.
- **Complexidade:** Tempo: `O(n)`. Espaço: `O(1)`.
- **Input:** Um número inteiro `n` (ex: `3`).
- **Output:** O enésimo número de Lucas (ex: `4`).

### 4. Subir Escadas

- **Descrição:** Você sobe uma escada com `n` degraus, podendo subir 1 ou 2 degraus por vez. Quantas maneiras distintas existem para chegar ao topo?
- **Passo a passo:** 1. Estado: `dp[i]` é o número total de formas para alcançar o degrau `i`. 2. Casos base: `dp[0] = 1`, `dp[1] = 1`. 3. Transição: `dp[i] = dp[i-1] + dp[i-2]`.
- **Complexidade:** Tempo: `O(n)`. Espaço: `O(n)` ou `O(1)`.
- **Input:** Um número inteiro `n` (ex: `3`).
- **Output:** Número de formas distintas (ex: `3` -> [1,1,1], [1,2], [2,1]).

### 5. Subir Escadas com 3 Movimentos

- **Descrição:** Expansão onde você pode pular 1, 2 ou até 3 degraus de uma só vez.
- **Passo a passo:** 1. Estado: `dp[i]` é o número de formas para alcançar o degrau `i`. 2. Casos base: `dp[0]=1`, `dp[1]=1`, `dp[2]=2`. 3. Transição: `dp[i] = dp[i-1] + dp[i-2] + dp[i-3]`.
- **Complexidade:** Tempo: `O(n)`. Espaço: `O(1)`.
- **Input:** Um número inteiro `n` (ex: `4`).
- **Output:** Número total de formas (ex: `7`).

### 6. Subir Escadas Ponderado

- **Descrição:** Cada degrau tem um custo associado. Calcule o custo mínimo para chegar ao topo podendo subir 1 ou 2 degraus.
- **Passo a passo:** 1. Estado: `dp[i]` é o menor custo para alcançar o degrau `i`. 2. Base: `dp[0] = custo[0]`, `dp[1] = custo[1]`. 3. Transição: `dp[i] = custo[i] + min(dp[i-1], dp[i-2])`.
- **Complexidade:** Tempo: `O(n)`. Espaço: `O(1)`.
- **Input:** Array de inteiros (ex: `[10, 15, 20]`).
- **Output:** Custo mínimo (ex: `15`).

### 7. Máximo de Segmentos

- **Descrição:** Corte um segmento de tamanho `N` em peças de tamanhos específicos `p`, `q` ou `r`. Maximize o número de segmentos resultantes.
- **Passo a passo:** 1. Estado: `dp[i]` é o número máximo de cortes para tamanho `i`. 2. Base: `dp[0] = 0`. 3. Transição: Para cada tamanho `i`, atualize `dp[i+p]`, `dp[i+q]`, `dp[i+r]` com `max(dp[atual], dp[anterior] + 1)`.
- **Complexidade:** Tempo: `O(N)`. Espaço: `O(N)`.
- **Input:** Tamanho `N` e cortes `p`, `q`, `r` (ex: `N=4, p=2, q=1, r=1`).
- **Output:** Número máximo de cortes (ex: `4`).

### 8. Enésimo Número de Catalan

- **Descrição:** Encontre o enésimo número da sequência de Catalan, construído pela soma dos produtos de pares de números anteriores.
- **Passo a passo:** 1. Estado: `dp[i]` armazena o i-ésimo número de Catalan. 2. Base: `dp[0] = 1`, `dp[1] = 1`. 3. Transição: `dp[i] = Σ(dp[j] * dp[i-j-1])` para `j` de 0 até `i-1`.
- **Complexidade:** Tempo: `O(n²)`. Espaço: `O(n)`.
- **Input:** Um inteiro `n` (ex: `3`).
- **Output:** O número de Catalan (ex: `5`).

### 9. Contar BSTs Únicos

- **Descrição:** Dado `N` chaves distintas, encontre o número de Árvores Binárias de Busca estruturalmente únicas.
- **Passo a passo:** 1. Modele onde `dp[i]` é o número de árvores com `i` chaves. 2. Para cada possível raiz `j`, multiplique as formas de organizar lado esquerdo `(j-1)` pelo lado direito `(i-j)`.
- **Complexidade:** Tempo: `O(N²)`. Espaço: `O(N)`.
- **Input:** Inteiro `N` chaves (ex: `3`).
- **Output:** Quantidade de BSTs únicas (ex: `5`).

### 10. Contar Parênteses Válidos

- **Descrição:** Encontre o número de expressões de parênteses bem formadas para `N` pares.
- **Passo a passo:** 1. Aplicação dos Números de Catalan. 2. Estado e transição seguem a mesma implementação do item 8.
- **Complexidade:** Tempo: `O(N²)`. Espaço: `O(N)`.
- **Input:** Inteiro `N` representando os pares (ex: `3`).
- **Output:** Número de expressões válidas (ex: `5` -> `()()()`, `(())()`, `()(())`, `(()())`, `((()))`).

### 11. Formas de Triangulação de um Polígono

- **Descrição:** Encontre o número de maneiras de dividir um polígono convexo de `N+2` lados em triângulos.
- **Passo a passo:** 1. Outra aplicação dos Números de Catalan. 2. Escolher um lado base e formar triângulo divide o polígono em dois menores.
- **Complexidade:** Tempo: `O(N²)`. Espaço: `O(N)`.
- **Input:** Número de lados `N` (ex: `4`).
- **Output:** Formas de triangulação (ex: `2`).

### 12. Soma Mínima em um Triângulo

- **Descrição:** Encontre o caminho do topo à base com menor soma, movendo-se para vizinhos adjacentes abaixo.
- **Passo a passo:** 1. Resolva de baixo para cima (**bottom-up**). 2. Estado: `dp[i][j]` é a soma mínima partindo daquela posição. 3. Base: Última linha = última linha do triângulo. 4. Transição: `dp[i][j] = triangulo[i][j] + min(dp[i+1][j], dp[i+1][j+1])`.
- **Complexidade:** Tempo: `O(L²)`. Espaço: `O(L)`.
- **Input:** Matriz triangular (ex: `[[2], [3,4], [6,5,7]]`).
- **Output:** Soma mínima (ex: `10` -> 2 -> 3 -> 5).

### 13. Quadrados Perfeitos Mínimos

- **Descrição:** Encontre o menor número de quadrados perfeitos cuja soma total seja `N`.
- **Passo a passo:** 1. Pense como um problema de "troco" com quadrados como "moedas". 2. Estado: `dp[i]` é a quantidade mínima de peças para somar `i`. 3. Base: `dp[0] = 0`. 4. Transição: `dp[i] = min(dp[i], 1 + dp[i - j*j])` para `j*j <= i`.
- **Complexidade:** Tempo: `O(N * √N)`. Espaço: `O(N)`.
- **Input:** Inteiro `N` (ex: `12`).
- **Output:** Mínimo de quadrados (ex: `3` -> 4+4+4).

### 14. Formas de Particionar um Conjunto

- **Descrição:** Encontre o número de partições possíveis de um conjunto com `N` elementos (Números de Bell).
- **Passo a passo:** 1. Construa o "Triângulo de Bell" usando DP bidimensional. 2. Estado: `dp[i][j]` é o j-ésimo valor na i-ésima linha. 3. Base: `dp[0][0] = 1`. 4. Transição: `dp[i][0] = dp[i-1][i-1]`. Para o restante: `dp[i][j] = dp[i-1][j-1] + dp[i][j-1]`.
- **Complexidade:** Tempo: `O(N²)`. Espaço: `O(N²)`, reduzível para `O(N)`.
- **Input:** Inteiro `N` (ex: `3`).
- **Output:** Número de partições (ex: `5`).

### 15. Coeficiente Binomial

- **Descrição:** Calcule C(n, k) — maneiras de escolher `k` itens de `n` disponíveis.
- **Passo a passo:** 1. Estado: `dp[i][j]` = C(i, j). 2. Base: `dp[i][0] = 1` e `dp[i][i] = 1`. 3. Transição (Pascal): `dp[i][j] = dp[i-1][j-1] + dp[i-1][j]`.
- **Complexidade:** Tempo: `O(N * K)`. Espaço: `O(N * K)` ou `O(K)`.
- **Input:** Dois inteiros `n` e `k` (ex: `5, 2`).
- **Output:** O coeficiente (ex: `10`).

### 16. Triângulo de Pascal

- **Descrição:** Gere as primeiras `N` linhas do triângulo de Pascal.
- **Passo a passo:** 1. Estado: `dp[i][j]` armazena o valor na linha `i`, coluna `j`. 2. Cada linha começa e termina com 1. 3. Valores internos: `dp[i][j] = dp[i-1][j-1] + dp[i-1][j]`.
- **Complexidade:** Tempo: `O(N²)`. Espaço: `O(N²)`.
- **Input:** Inteiro `N` (ex: `5`).
- **Output:** Uma matriz dentada representando o triângulo.

### 17. Enésima Linha do Triângulo de Pascal

- **Descrição:** Compute apenas a N-ésima linha do triângulo usando otimização de espaço (array 1D).
- **Passo a passo:** 1. Crie um array 1D de tamanho N. Base: `dp[0] = 1`. 2. Itere pelas colunas **de trás para frente** para evitar sobrescrever dados necessários. 3. Transição: `dp[j] = dp[j] + dp[j-1]`.
- **Complexidade:** Tempo: `O(N²)`. Espaço: `O(N)`.
- **Input:** Inteiro índice `N` (ex: `3`).
- **Output:** Array 1D (ex: `[1, 3, 3, 1]`).

### 18. Ladrão da Casa (House Robber)

- **Descrição:** Dado um array de valores em casas, maximize quanto você rouba sem assaltar casas adjacentes.
- **Passo a passo:** 1. Estado: `dp[i]` indica o lucro máximo até a casa `i`. 2. Base: `dp[0] = arr[0]`, `dp[1] = max(arr[0], arr[1])`. 3. Transição: `dp[i] = max(arr[i] + dp[i-2], dp[i-1])`.
- **Complexidade:** Tempo: `O(N)`. Espaço: `O(N)`, otimizável para `O(1)`.
- **Input:** Array de inteiros não negativos (ex: `[6, 7, 1, 3, 8, 2, 4]`).
- **Output:** Valor máximo (ex: `19` -> 6, 1, 8, 4).

### 19. Caminho de Custo Mínimo

- **Descrição:** Dada uma matriz com custos nas células, encontre a rota mais barata de (0,0) até o canto inferior direito. Movimentos: direita, baixo ou diagonal.
- **Passo a passo:** 1. Estado: `dp[i][j]` guarda o custo mínimo para alcançar (i, j). 2. Base: `dp[0][0] = custo[0][0]`. Primeira linha e coluna: soma acumulada. 3. Transição: `dp[i][j] = custo[i][j] + min(dp[i-1][j-1], dp[i-1][j], dp[i][j-1])`.
- **Complexidade:** Tempo: `O(M * N)`. Espaço: `O(M * N)`.
- **Input:** Matriz de inteiros.
- **Output:** Valor do custo mínimo.

### 20. Formas de Decodificar

- **Descrição:** Uma mensagem numérica (A=1...Z=26) é dada. Quantas interpretações válidas existem? (Ex: "12" -> "AB" ou "L")
- **Passo a passo:** 1. Estado: `dp[i]` registra decodificações válidas até o índice `i`. 2. Base: Valida dependendo se for diferente de '0'. 3. Transição: Se caractere atual ≠ '0': `dp[i] += dp[i-1]`. Se dois caracteres formam "10"-"26": `dp[i] += dp[i-2]`.
- **Complexidade:** Tempo: `O(N)`. Espaço: `O(N)`, otimizável para `O(1)`.
- **Input:** String de dígitos (ex: `"226"`).
- **Output:** Número de interpretações (ex: `3`).

### 21. Problema da Soma de Subconjunto (Subset Sum)

- **Descrição:** Verifique se existe subconjunto cuja soma seja um alvo `S`.
- **Passo a passo:** 1. Estado: `dp[i][j]` é booleano, verdadeiro se soma `j` é atingível com primeiros `i` elementos. 2. Base: A soma 0 sempre é atingível. 3. Transição: Se elemento cabe: `dp[i][j] = dp[i-1][j] || dp[i-1][j - array[i-1]]`.
- **Complexidade:** Tempo: `O(N * S)` (pseudo-polinomial). Espaço: `O(N * S)`.
- **Input:** Array e soma alvo (ex: `[3, 34, 4, 12, 5, 2]`, S = 9).
- **Output:** Booleano (ex: `Verdadeiro`).

### 22. Problema da Troca de Moedas - Contar Formas (Coin Change)

- **Descrição:** Quantas combinações distintas de moedas somam o valor `V`? (ordem não importa)
- **Passo a passo:** 1. Estado: `dp[j]` = número de composições para valor `j`. 2. Base: `dp[0] = 1`. 3. Transição: Para cada moeda, da sua denominação até `V`: `dp[j] += dp[j - moeda]`.
- **Complexidade:** Tempo: `O(M * V)`. Espaço: `O(V)`.
- **Input:** Array de moedas e valor (ex: `[1, 2, 3]`, V = 4).
- **Output:** Número de arranjos (ex: `4` -> {1,1,1,1}, {1,1,2}, {2,2}, {1,3}).

### 23. Troca de Moedas – Número Mínimo

- **Descrição:** Qual a quantidade **mínima** de moedas para formar valor `V`?
- **Passo a passo:** 1. Estado: `dp[j]` = quantidade mínima para valor `j`. Inicialize com infinito. 2. Base: `dp[0] = 0`. 3. Transição: `dp[j] = min(dp[j], 1 + dp[j - moeda])`.
- **Complexidade:** Tempo: `O(M * V)`. Espaço: `O(V)`.
- **Input:** Moedas e soma (ex: `[9, 6, 5, 1]`, V = 11).
- **Output:** Quantidade mínima (ex: `2` -> 5 + 6).

### 24. Algoritmo de Pintura da Cerca

- **Descrição:** Pinte `n` postes com `k` cores, proibindo 3 postes adjacentes com mesma cor. Quantas decorações?
- **Passo a passo:** 1. Estado: `same` = últimos 2 postes mesma cor, `diff` = cores diferentes. 2. Base: 1 poste: `same=0`, `diff=k`. 3. Transição: `same = diff_anterior`, `diff = (same_anterior + diff_anterior) * (k-1)`.
- **Complexidade:** Tempo: `O(n)`. Espaço: `O(1)`.
- **Input:** `n` postes e `k` cores (ex: `n=3, k=2`).
- **Output:** Quantidade de modos (ex: `6`).

### 25. Cortar uma Haste (Rod Cutting)

- **Descrição:** Corte haste de comprimento `N` para maximizar receita usando tabela de preços.
- **Passo a passo:** 1. Estado: `dp[i]` = receita máxima para haste tamanho `i`. 2. Base: `dp[0] = 0`. 3. Transição: `dp[i] = max(dp[i], preco[j] + dp[i-j-1])` testando todos cortes possíveis.
- **Complexidade:** Tempo: `O(N²)`. Espaço: `O(N)`.
- **Input:** Array de preços (ex: `[1, 5, 8, 9]`).
- **Output:** Lucro máximo (ex: `10`).

### 26. Jump Game (Salto Mínimo)

- **Descrição:** Atinja o final com o **menor número de saltos**. Elemento dita alcance máximo.
- **Passo a passo:** 1. Estado: `dp[i]` = menor número de pulos para alcançar índice `i`. 2. Base: `dp[0] = 0`, demais = infinito. 3. Transição: De cada `i`, atualizar `dp[j] = min(dp[j], dp[i] + 1)` para `j` dentro do alcance.
- **Complexidade:** Tempo: `O(N²)`. Espaço: `O(N)`.
- **Input:** Array (ex: `[1, 3, 5, 8, 9, 2, 6]`).
- **Output:** Número de saltos (ex: `3`).

### 27. Maior Substring Comum (LCS - Longest Common Substring)

- **Descrição:** Extraia o tamanho da maior cadeia **contígua** compartilhada identicamente.
- **Passo a passo:** 1. Estado: `dp[i][j]` = comprimento do match terminando em S1[i-1] e S2[j-1]. 2. Base: zeros. 3. Transição: Se S1[i-1] == S2[j-1]: `dp[i][j] = dp[i-1][j-1] + 1`. Senão: `dp[i][j] = 0`. Monitore máximo.
- **Complexidade:** Tempo: `O(N * M)`. Espaço: `O(N * M)`.
- **Input:** Dois textos (ex: "abcdxyz" e "xyzabcd").
- **Output:** Tamanho (ex: `4`).

### 28. Contar Todos os Caminhos em uma Grade

- **Descrição:** De (0,0) até canto inferior direito, contando apenas movimentos direita/baixo.
- **Passo a passo:** 1. Estado: `dp[i][j]` = número de vias para alcançar (i,j). 2. Base: `dp[0][..] = 1` e `dp[..][0] = 1`. 3. Transição: `dp[i][j] = dp[i-1][j] + dp[i][j-1]`.
- **Complexidade:** Tempo: `O(m * n)`. Espaço: `O(m * n)` ou `O(n)`.
- **Input:** Dimensões `m, n` (ex: `3, 3`).
- **Output:** Total de caminhos (ex: `6`).

### 29. Caminhos em uma Grade com Obstáculos

- **Descrição:** Extensão anterior onde valor 1 = obstáculo. Conte caminhos evitando-os.
- **Passo a passo:** 1. Se `grid[i][j] == 1`: `dp[i][j] = 0`. Senão, processe normalmente. 2. Obstáculo em linha reta bloqueia tudo depois dele.
- **Complexidade:** Tempo: `O(M * N)`. Espaço: `O(M * N)`.
- **Input:** Mapa 2D (ex: `[[0,0,0], [0,1,0], [0,0,0]]`).
- **Output:** Total de caminhos (ex: `2`).

### 30. Máximo de A usando Teclado Especial

- **Descrição:** Teclado com 4 comandos: digitar A, Ctrl-A, Ctrl-C, Ctrl-V. Com `N` ações, maximize A's na tela.
- **Passo a passo:** 1. Estado: `dp[i]` = máximo de A's com `i` cliques. 2. Base: Para `i <= 6`, `dp[i] = i`. 3. Transição: Para `i > 6`, teste selecionar+copiar+colar: `dp[i] = max(dp[j-2] * (i-j+1))` iterando `j`.
- **Complexidade:** Tempo: `O(N²)`. Espaço: `O(N)`.
- **Input:** Contador `N` (ex: `7`).
- **Output:** Máximo de A's (ex: `9`).

</details>

<details>
<summary>🟠 Nível 2 - Médio</summary>

Os exercícios aqui combinam dois parâmetros no estado (matrizes DP bidimensionais) e requerem um processo transicional bem fundamentado. Problemas de Subsequência são reis nesta etapa.

### 31. Transbordamento de Água

- **Descrição:** Copos em cascata triangular. Derrame `X` litros no topo. Qual volume fica em dado copo?
- **Passo a passo:** 1. Estado: `dp[r][c]` = quantidade de líquido no copo (r, c). 2. Base: `dp[0][0] = X`. 3. Transição: Se `dp[r][c] > 1`, transborda: despeja `(dp[r][c] - 1) / 2` para `dp[r+1][c]` e `dp[r+1][c+1]`. Capa em 1.
- **Complexidade:** Tempo: `O(K²)`. Espaço: `O(K²)`.
- **Input:** Quantidade `X` e coordenadas (r, c).
- **Output:** Volume final (ex: `0.5`).

### 32. Maior Subsequência Comum (LCS - Longest Common Subsequence)

- **Descrição:** Encontre a maior subsequência (não necessariamente contígua) compartilhada.
- **Passo a passo:** 1. Estado: `dp[i][j]` = LCS de S1[0..i-1] e S2[0..j-1]. 2. Se S1[i-1] == S2[j-1]: `dp[i][j] = dp[i-1][j-1] + 1`. Senão: `dp[i][j] = max(dp[i-1][j], dp[i][j-1])`.
- **Complexidade:** Tempo: `O(N * M)`. Espaço: `O(N * M)` ou `O(N)`.
- **Input:** Duas strings (ex: `"AGGTAB"` e `"GXTXAYB"`).
- **Output:** Tamanho da LCS (ex: `4` -> "GTAB).

### 33. Maior Subsequência Crescente (LIS - Longest Increasing Subsequence)

- **Descrição:** Encontre o comprimento da maior subsequência em ordem crescente.
- **Passo a passo:** 1. Estado: `dp[i]` = comprimento máximo terminando em `i`. 2. Base: `dp[i] = 1`. 3. Transição: Para cada j < i, se `arr[i] > arr[j]`: `dp[i] = max(dp[i], dp[j] + 1)`.
- **Complexidade:** Tempo: `O(N²)`. Espaço: `O(N)`. (Otimizável para `O(N log N)` com busca binária)
- **Input:** Array (ex: `[10, 22, 9, 33, 21, 50]`).
- **Output:** Comprimento (ex: `4`).

### 34. Distância de Edição (Edit Distance / Levenshtein)

- **Descrição:** Número mínimo de operações (inserir, remover, substituir) para transformar S1 em S2.
- **Passo a passo:** 1. Estado: `dp[i][j]` = custo para S1[0..i] tornar-se S2[0..j]. 2. Base: Transformar de/para vazio custa inserções/remoções. 3. Transição: Se caracteres iguais: `dp[i][j] = dp[i-1][j-1]`. Senão: `dp[i][j] = 1 + min(dp[i-1][j], dp[i][j-1], dp[i-1][j-1])`.
- **Complexidade:** Tempo: `O(N * M)`. Espaço: `O(N * M)` ou `O(min(N,M))`.
- **Input:** Strings (ex: `"kitten"` e `"sitting"`).
- **Output:** Número de operações (ex: `3`).

### 35. Maior Subconjunto Divisível

- **Descrição:** Encontre o maior subconjunto onde cada par funciona (um divide o outro). Dica: ordene!
- **Complexidade:** Tempo: `O(N²)`. Espaço: `O(N)`.

### 36. Agendamento de Trabalhos Ponderado

- **Descrição:** `N` trabalhos com horário e pagamento. Maximize renda sem conflitos.
- **Complexidade:** Tempo: `O(N log N)`. Espaço: `O(N)`.

### 37. Problema da Mochila 0-1 (Knapsack Clássica)

- **Descrição:** Preencha bolsa com capacidade `W` usando itens com peso/valor. Maximize valor total.
- **Passo a passo:** 1. Estado: `dp[i][w]` = máximo valor com primeiros `i` itens e capacidade `w`. 2. Base: `dp[0][..] = 0`. 3. Transição: Se peso couber: `dp[i][w] = max(dp[i-1][w], valor[i] + dp[i-1][w-peso[i]])`.
- **Complexidade:** Tempo: `O(N * W)`. Espaço: `O(N * W)`.

### 38. Impressão de Itens na Mochila 0/1

- **Descrição:** Além do lucro máximo, quais itens foram selecionados?
- **Passo a passo:** Após DP, faça backtracking da tabela.
- **Complexidade:** Tempo = Mochila 0/1 + `O(N)`.

### 39. Mochila Ilimitada

- **Descrição:** Itens podem ser repetidos infinitas vezes.
- **Passo a passo:** 1. Base: `dp[w] = 0`. 2. Transição: Itere peso crescente: `dp[w] = max(dp[w], valor[i] + dp[w-peso[i]])`.
- **Complexidade:** Tempo: `O(N * W)`. Espaço: `O(W)`.

### 40. Problema de Quebra de Palavras (Word Break)

- **Descrição:** Particione string usando dicionário. Valide se particionamento é possível.
- **Passo a passo:** 1. Estado: `dp[i]` = verdadeiro se prefixo até `i` é válido. 2. Base: `dp[0] = true`. 3. Transição: Para cada `j < i`, se `dp[j]` e substring de `j` até `i` está no dicionário: `dp[i] = true`.
- **Complexidade:** Tempo: `O(N³)` ou `O(N²)` com Trie. Espaço: `O(N)`.

### 41. Maior Quadrado com Borda X

- **Dica:** Use tabelas separadas para horizontal/vertical. Custa `O(N³)` com pré-processamento DP.

### 42. Problema do Egg Dropping

- **Descrição:** Com `k` ovos, minimize tentativas no pior caso para encontrar andar crítico.
- **Complexidade:** DP Clássica: `O(K * N²)`. Otimizado com busca binária: `O(K * N log N)`.

### 43 e 44. Particionamento e Contagem de Palíndromos

- **Descrição:** Trabalhar com palíndromos envolve matriz booleana prévia: `is_palindrome[i][j]`.
- **Complexidade:** Tempo: `O(N²)`. Espaço: `O(N²)`.

### 45. Palíndromo via Expansão pelo Centro

- **Descrição:** Expanda a partir de cada centro (não precisa matriz 2D).
- **Complexidade:** Tempo: `O(N²)`. Espaço: `O(1)`.

### 46 a 58. Teoria de Jogos e DP em Grafos

- **Estratégia de Jogo:** Você maximiza enquanto adversário minimiza.
- **Bellman-Ford:** Caminhos mínimos com arestas negativas. `O(V * E)`.
- **Floyd-Warshall:** Todos os pares. `O(V³)` tempo, `O(V²)` espaço.

</details>

<details>
<summary>🔴 Nível 3 - Difícil</summary>

Estes combinam DP com teorias avançadas, otimizações matemáticas e estruturas complexas.

### 59. Maior Quadrado com Borda X (Versão Otimizada)

- **Complexidade Final:** `O(N³)` com pré-processamento.

### 60. Problema do Egg Dropping (Versão Otimizada)

- **Complexidade Final:** `O(K * N log N)` com busca binária.

### 61 e 62. Particionamento Palíndromico

- **Descrição:** Particione string em palíndromos. Use matriz `is_palindrome` pré-computada.
- **Complexidade:** Tempo: `O(N²)`. Espaço: `O(N²)`.

### 63 a 73. Teoria de Jogos

- **Game Theory:** Alternância de turno onde você maximiza e adversário minimiza.
- **Aplicações:** Estratégias ótimas em jogos com matrizes e arrays.

### 74. DP em Árvores (Tree DP)

- **Descrição:** Use DFS recursiva com retorno de tuplas em vez de matrizes bidimensionais.
- **Típico:** `dfs(nó) -> [sim_pego_nó, nao_pego_nó]`.
- **Complexidade:** Tempo: `O(V)`. Espaço: `O(altura)`.

### 75 a 77. Otimizações Avançadas

- **Expansão pelo Centro:** Para palíndromos, evita matriz 2D. `O(N²)` com `O(1)` espaço.
- **Convex Hull Trick:** Para otimizar DP linear para `O(N log N)`.
- **Outro Tópico Avançado:** Limites superiores inferiores com estruturas sofisticadas.

</details>
