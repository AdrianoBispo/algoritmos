# Lista de Exercícios - Algoritmo de Backtracking

Bem-vindo(a) à sua jornada de domínio em Algoritmos de Backtracking! Esta lista foi elaborada para focar no fortalecimento da sua lógica de programação e na sua capacidade de resolver problemas complexos de otimização e busca.

Você pode implementar as soluções na linguagem de programação de sua preferência (C, C++, C#, Java, Kotlin, Javascript/Typescript, Python, PHP, Go, Ruby, etc.). Concentre-se em entender a **transição de estado**, como os dados são modificados na ida da recursão e como devem ser restaurados no retorno.

### Dicas Gerais de Debugging em Backtracking

Entender a lógica de ida e volta (backtracking) é como aprender a andar de bicicleta: depois que o conceito "clica", problemas que pareciam impossíveis viram combinações de decisões e validações.

**Seu código falhou ou entrou em Loop? Pergunte-se:**

1. **Minha base case (condição de parada) está correta?**
    Se ela estiver errada (ou ausente), o algoritmo pode entrar em loop, causar estouro de pilha (Stack Overflow) ou estourar limite de tempo.

2. **Estou desfazendo o estado corretamente no retorno?**
    Toda escolha feita na ida deve ser desfeita na volta. Exemplos: remover item da lista, desmarcar `visited`, restaurar célula na matriz.

3. **Estou salvando cópia ou referência?**
    Em Python e Java, listas e arrays são estruturas por referência. Ao salvar uma solução parcial, grave uma cópia (por exemplo, `minha_lista.copy()`), não a referência original.

4. **Estou podando galhos inviáveis cedo?**
    A árvore de busca cresce de forma exponencial. Sem poda (checagens antecipadas), o código tende a ficar lento e pode gerar TLE (Time Limit Exceeded).

Treine com frequência, desenhe a árvore de estados no papel antes de codar e valide casos simples manualmente. Em backtracking, raciocínio vem antes de implementação.

<details>
  <summary>🟢 Nível 1 - Fácil</summary>

Nesta seção, o foco está em entender a mecânica básica de inclusão/exclusão e a navegação simples em árvores de decisão.

### 1. Encontrar todos os subconjuntos

**Descrição:** Dado um conjunto de números inteiros, gere todos os subconjuntos possíveis (também conhecido como conjunto das partes ou _Power Set_).

**Intuição:** Este é o padrão clássico de "Pegar ou Não Pegar". Para cada elemento, a árvore de decisão se bifurca.

**Passo a Passo:**

1. Crie uma função recursiva que receba o índice atual do array original e o subconjunto temporário construído até o momento.
2. No estado atual, você tem duas bifurcações: incluir o elemento atual no subconjunto temporário ou seguir sem ele.
3. Chame a recursão para o próximo índice (avançando na árvore).
4. Quando o índice for igual ao tamanho do array de entrada (condição de parada), adicione uma _cópia_ do subconjunto temporário à lista de respostas.

**Dica de Implementação:** Sempre adicione uma cópia (ou clone) da lista temporária ao resultado final. Se você passar a referência original, ela será modificada nos próximos passos e todas as suas respostas ficarão vazias.

**Complexidade:** Tempo O(2^N) e Espaço O(N) (devido à pilha de recursão), onde N é o número de elementos.

- **Input:** `[1, 2]`
- **Output:** `[], [1], [2], [1, 2]`

### 2. Verificar string soma

**Descrição:** Verifique se uma string de dígitos numéricos pode ser dividida de forma que o terceiro número subsequente seja sempre a soma dos dois números imediatamente anteriores.

**Intuição:** Como não sabemos o tamanho de cada número na string, precisamos testar dinamicamente comprimentos diferentes para os dois primeiros blocos numéricos.

**Passo a Passo:**

1. Itere com dois loops iniciais para escolher os comprimentos dos dois primeiros números da string (prefixos).
2. Com os dois primeiros números definidos (por exemplo, "12" e "24"), calcule a soma ("36") e verifique se esse exato resultado aparece imediatamente após eles na string original.
3. Use recursão para verificar o restante da string usando o segundo número como novo "primeiro" e a soma atual como "segundo".
4. Se chegar ao final da string de forma exata, retorne verdadeiro. Se o número não bater, faça o backtrack e tente outros comprimentos no loop inicial.

**Dica de Implementação:** Cuidado com strings grandes que podem ultrapassar o limite de inteiros de 32 ou 64 bits da sua linguagem. Em Python isso é gerenciado automaticamente, mas em Java ou C++, pode ser necessário usar bibliotecas numéricas como `BigInteger` ou fazer a soma caractere por caractere.

- **Input:** `"122436"`
- **Output:** `True` _(Pois 12 + 24 = 36 e consome a string perfeitamente)_

### 3. Todos os caminhos entre dois vértices

**Descrição:** Em um grafo direcionado, conte o número total de caminhos válidos e únicos de um vértice de origem até um vértice de destino.

**Intuição:** Uma simples busca em profundidade (DFS) que, ao invés de parar quando acha o destino, registra um sucesso e continua buscando outras rotas, voltando atrás nos nós visitados.

**Passo a Passo:**

1. Receba o nó atual e marque-o como `visitado` em um array ou HashSet booleano para evitar loops infinitos.
2. Se o vértice atual for exatamente o destino desejado, incremente sua variável global ou contador de caminhos.
3. Para cada vértice adjacente (vizinho) que ainda _não_ foi visitado, chame a recursão passando esse vizinho como o novo vértice atual.
4. **Backtrack:** Ao retornar da recursão, desmarque o vértice atual do conjunto de visitados. Isso é crucial para que este nó possa ser visitado novamente a partir de um caminho inicial diferente.

**Complexidade:** O pior caso em grafos densos pode chegar a O(V!) caminhos, onde V é o número de vértices.

- **Input:** `Grafo: 0→1, 0→2, 1→2, 2→3`, `Origem: 0`, `Destino: 3`
- **Output:** `2` _(Os caminhos possíveis são: 0→1→2→3 e 0→2→3)_

### 4. Todos os subconjuntos distintos

**Descrição:** Dado um conjunto de números que pode conter elementos duplicados, retorne todos os subconjuntos distintos possíveis (sem repetições lógicas).

**Intuição:** Derivado do problema 1, mas precisamos de uma lógica para podar galhos da árvore que gerariam conjuntos idênticos.

**Passo a Passo:**

1. **Passo Fundamental:** Ordene o array de entrada primeiro. Isso garante que elementos duplicados fiquem estritamente adjacentes (ex: `[2, 1, 2]` vira `[1, 2, 2]`).
2. Inicie a recursão passando o índice atual.
3. Ao iterar pelas opções num laço `for`, pule a chamada recursiva (faça um `continue`) se o elemento atual for igual ao anterior (`arr[i] == arr[i-1]`) e o anterior não for o próprio índice inicial daquela profundidade recursiva.
4. Armazene o valor na lista temporária, chame a recursão para `i + 1`, e faça o backtrack removendo o último elemento adicionado.

- **Input:** `[1, 2, 2]`
- **Output:** `[], [1], [2], [1, 2], [2, 2], [1, 2, 2]` _(Note que [2] aparece apenas uma vez)_

### 5. Caminho de comprimento maior que k a partir de uma origem

**Descrição:** Em um grafo ponderado (com pesos nas arestas), verifique se existe _algum_ caminho a partir de um vértice de origem cujo peso total percorrido seja estritamente maior que um valor `k`.

**Intuição:** Uma DFS focada em acumular o peso. A poda ocorre automaticamente assim que a condição é satisfeita, encerrando o algoritmo precocemente.

**Passo a Passo:**

1. Mantenha um vetor ou mapa booleano para registrar os nós visitados na ramificação atual da rota.
2. Na função recursiva, receba o nó atual e o valor `k` restante. Se `k` for menor ou igual a 0, você já ultrapassou o objetivo; retorne `True` imediatamente.
3. Para cada vizinho não visitado, subtraia o peso da aresta entre eles do valor `k` e chame a recursão.
4. **Backtrack:** Se a chamada recursiva retornar `False` (não conseguiu passar de `k` por aquele caminho), desmarque o vizinho e tente explorar as outras arestas adjacentes.

- **Input:** `Grafo ponderado`, `Origem: 0`, `k: 50`
- **Output:** `True` ou `False`

### 6. Todos os caminhos de uma origem para um destino

**Descrição:** Variação do Problema 3. Em vez de apenas contar, você deve salvar e imprimir as listas exatas contendo a sequência de nós percorrida.

**Intuição:** Ao invés de um inteiro contador, você carregará uma estrutura de dados de estado (lista) durante a DFS.

**Passo a Passo:**

1. Mantenha uma lista/array que atue como a trilha de migalhas de pão do seu caminho atual.
2. Ao entrar no nó, adicione-o ao final da lista e marque-o como visitado.
3. Se atingir o destino, crie uma cópia profunda (deep copy) da lista atual e adicione-a à resposta final.
4. Caso contrário, para cada vizinho não visitado, faça a chamada recursiva.
5. **Backtrack:** Na saída da função recursiva, dê um `pop()` (remova) no último nó da lista e desmarque-o como visitado, restaurando o estado para a função chamadora.

- **Input:** `Grafo: 0→1, 0→2, 1→3, 2→3`, `Origem: 0`, `Destino: 3`
- **Output:** `[[0, 1, 3], [0, 2, 3]]`

</details>

<details>
  <summary>🟠 Nível 2 - Médio</summary>

Aqui, o estado armazenado fica mais complexo e as condições de poda tornam-se essenciais para a performance do algoritmo.

### 7. Tug of War (Guerra dos Sexos)

**Descrição:** Dado um conjunto de N pessoas com diferentes pesos, divida-os em duas equipes (subconjuntos) de forma que a diferença total de peso entre as duas equipes seja a mínima possível. As equipes devem ter o mesmo número de pessoas (ou diferir por 1 se N for ímpar).

**Intuição:** Precisamos testar permutações e combinações dividindo em dois grupos simulados. A profundidade da recursão é N (cada elemento deve ir para o Grupo 1 ou Grupo 2).

**Passo a Passo:**

1. Crie variáveis para rastrear o elemento atual (`index`), os itens do Grupo 1, itens do Grupo 2 e a soma corrente de cada grupo.
2. Para o elemento atual, tente adicioná-lo ao Grupo 1. Antes de adicionar, verifique se o tamanho do Grupo 1 não excede `⌈N/2⌉`. Se for válido, adicione-o e avance recursivamente.
3. Ao retornar da chamada (Backtrack), remova-o do Grupo 1.
4. Faça a mesma tentativa adicionando o elemento ao Grupo 2, e chame a recursão. Remova-o no backtrack.
5. Quando atingir o final do array, calcule a diferença absoluta de pesos. Se for menor que a melhor diferença global já vista, atualize sua configuração final.

**Complexidade:** Sem otimizações de Programação Dinâmica, a força bruta em backtracking leva O(2^N).

- **Input:** `[3, 4, 5, -3, 100, 1, 89, 54, 23, 20]`
- **Output:** `Equipe 1: [4, 100, 1, 23, 20] (Soma: 148), Equipe 2: [3, 5, -3, 89, 54] (Soma: 148)`

### 8. Problema das 8 Rainhas

**Descrição:** Posicione 8 rainhas em um tabuleiro de xadrez 8×8 tradicional de modo que nenhuma delas consiga se atacar. Rainhas movem-se na horizontal, vertical e diagonais infinitamente.

**Intuição:** Preencher a matriz de forma ingênua seria gerar 64!/(8!·56!) combinações. Usando a lógica de que cada rainha deve estar obrigatoriamente em uma coluna diferente, reduzimos para testar linha por linha em cada coluna.

**Passo a Passo:**

1. A função recursiva processará o tabuleiro coluna por coluna (índice da coluna).
2. Na coluna atual, itere sobre as 8 linhas. Para cada célula (linha, coluna), use uma função auxiliar `is_safe()` para verificar se há alguma rainha à esquerda na mesma linha, ou nas diagonais superiores e inferiores à esquerda.
3. Se a casa for segura, coloque `1` ou 'Q' na matriz e avance recursivamente chamando `resolve_rainhas(coluna + 1)`.
4. **Backtrack:** Se posicionar a rainha ali retornar `False` lá na frente, retorne o valor da célula para `0` e tente a linha de baixo.

**Complexidade:** Otimizado, testa no máximo 8^8 estados, parando muito antes via poda de diagonais.

- **Input:** (Nenhum)
- **Output:** Matriz gráfica onde 'Q' são as posições válidas e '.' são vazias.

### 9. Soma Combinacional

**Descrição:** Encontre todas as combinações únicas de números em um array de candidatos que somem exatamente a um valor `target`. O mesmo número pode ser utilizado repetidas vezes.

**Intuição:** Diferente da construção de subconjuntos onde andamos sempre para frente, aqui podemos escolher ficar no mesmo índice numérico e extraí-lo várias vezes até estourar o limite.

**Passo a Passo:**

1. O primeiro passo crucial é remover duplicatas e ordenar o array de candidatos para evitar gerar respostas espelhadas/redundantes.
2. Na recursão, passe o array, o `target` atualizado, o índice atual e a lista temporária.
3. Se o `target` for exatamente 0, copie a lista para os resultados. Se for menor que 0, apenas dê `return` para acionar a poda/backtrack.
4. Para o passo indutivo, você tem duas escolhas exclusivas:
    - Adicionar o candidato atual na lista, subtrair seu valor do target, e chamar a recursão _sem alterar o índice_ (permitindo usá-lo de novo).
    - Não adicionar o candidato e chamar a recursão incrementando o índice para `i + 1`.

- **Input:** `Array: [2, 3, 6, 7]`, `Target: 7`
- **Output:** `[[2, 2, 3], [7]]`

### 10. Algoritmo de Warnsdorff para o Passeio do Cavalo

**Descrição:** O "Knight's Tour" exige que o cavalo do xadrez visite todas as 64 casas sem repetir nenhuma. O Backtracking puro demora muito tempo para tabuleiros grandes. A Heurística de Warnsdorff resolve isso guiando as decisões inteligentemente.

**Intuição:** Sempre mova o cavalo para a casa adjacente que tiver o _menor número de movimentos válidos futuros_. É uma estratégia gulosa acoplada ao backtracking.

**Passo a Passo:**

1. A partir de uma célula, em vez de tentar qualquer um dos 8 movimentos em ordem fixa, calcule o "grau" de cada destino válido (quantos saltos válidos aquela casa possui).
2. Ordene as escolhas de destino com base nesse grau (do menor para o maior).
3. Mova para a casa com menor grau. Isso força o cavalo a visitar bordas e cantos do tabuleiro primeiro, evitando ficar preso no centro.
4. Faça o backtrack tradicional caso se encontre num beco sem saída (grau 0) antes do salto 64.

- **Input:** `Posição inicial: (2, 2)`
- **Output:** Matriz 8×8 contendo a sequência de números de 1 a 64 mapeando o caminho completo.

### 11. Caminhos da Célula do Canto até a Célula do Meio em um Labirinto

**Descrição:** Imagine uma matriz quadrada de tamanho ímpar (ex: 9×9). Cada célula contém um número indicando a _distância exata_ que você deve saltar a partir dela em linha reta. Começando nos cantos, você deve chegar ao exato meio da matriz.

**Intuição:** Diferente de grafos adjacentes onde se avança de 1 em 1 bloco, o cálculo de coordenadas é elástico (ex: salto `linha + valor_celula`).

**Passo a Passo:**

1. Crie uma matriz booleana de `visitados`.
2. O passo recursivo começa lendo o valor `n = matriz[linha][coluna]`.
3. Se a célula for a central (coordenadas `N/2, N/2`), armazene e imprima o caminho percorrido.
4. Calcule as quatro novas posições saltando exatamente `n` casas para Norte (`linha - n`), Sul (`linha + n`), Leste (`coluna + n`) e Oeste (`coluna - n`).
5. Se uma nova posição estiver dentro dos limites do grid e não foi visitada, adicione à lista, marque e faça a recursão.
6. **Backtrack:** Desfaça a visita e remova o elemento da trilha no final.

- **Input:** Matriz quadrada N×N de inteiros
- **Output:** A sequência de coordenadas saltadas.

### 12. Maior Número Possível com no Máximo K Trocas

**Descrição:** Dado um número enorme armazenado em formato de string, e um inteiro `K`, encontre o maior número possível realizando no máximo `K` trocas (swaps) de posições de qualquer par de dígitos.

**Intuição:** Tratar dígitos como caracteres. O backtracking testará trocar um número pequeno inicial por um número grande localizado mais ao fim da string.

**Passo a Passo:**

1. Inicie salvando a string de entrada original em uma variável global `valor_maximo`.
2. A recursão recebe a string atual e a quantidade restante de trocas `K`. Se `K == 0`, apenas retorne.
3. Crie um loop aninhado iterando comparando o caractere no índice `i` com o de índice `j` (`j > i`).
4. Se o dígito em `j` for maior que o dígito em `i`, faça o _swap_ entre eles na string.
5. Verifique se a string gerada é numericamente maior que `valor_maximo` e atualize-o se sim.
6. Chame a recursão decrementando `K` em 1.
7. **Backtrack:** Desfaça o _swap_ para que o loop teste trocar `i` com o próximo valor de `j`.

**Dica de Implementação:** Use funções de comparação de strings padrão (`compareTo` ou operadores `>`), pois garantem a comparação lexicográfica correta para strings do mesmo tamanho.

- **Input:** `String: "129814999", K: 4`
- **Output:** `"999984211"`

### 13. Rato em um Labirinto com Múltiplos Saltos Permitidos

**Descrição:** O labirinto não contém 1s e 0s, mas números positivos. Um número `X` numa casa significa que o rato pode escolher saltar 1, 2, ..., ou até `X` espaços para a direita ou para baixo. O alvo é o canto inferior direito.

**Intuição:** A ramificação não é apenas direcional, mas também envolve _força_ do pulo.

**Passo a Passo:**

1. A função parte de `(0, 0)`. Verifique a condição de vitória: linha e coluna estarem na última posição.
2. Leia o valor da célula: `saltos_max = labirinto[l][c]`. Se for 0, é um beco sem saída.
3. Crie um loop de `i = 1` até `saltos_max`.
4. Primeiro, tente pular `i` posições para a direita chamando a recursão para `(l, c + i)`. Se retornar verdadeiro, repasse a vitória.
5. Se falhar, faça o backtrack (o código continuará no loop) e tente pular `i` casas para baixo `(l + i, c)`.
6. Se todos os saltos possíveis falharem, retorne `Falso`.

- **Input:** `[[2, 1, 0, 0], [3, 0, 0, 1], [0, 1, 0, 1], [0, 0, 0, 1]]`
- **Output:** Matriz visual indicando as pegadas do caminho que obteve sucesso.

### 14. N Rainhas em Espaço O(n)

**Descrição:** Otimização arquitetural do problema 8. Resolva N Rainhas sem alocar matrizes 2D para o tabuleiro, economizando drasticamente alocação de memória usando apenas um array unidimensional de tamanho `N`.

**Intuição:** Sabemos que cada linha só comporta 1 rainha. Então um array `tab[4] = [1, 3, 0, 2]` significa que na linha 0 a rainha está na coluna 1; na linha 1, coluna 3, etc.

**Passo a Passo:**

1. Crie um array de tamanho `N`. Inicie o backtracking recebendo o índice da linha atual.
2. A verificação de segurança `is_safe()` itera sobre as linhas já preenchidas antes da atual (até `linha - 1`).
3. Uma posição `(linha_atual, col_tentativa)` é atacada se a coluna bater: `tab[linha_anterior] == col_tentativa`.
4. É atacada na diagonal se a diferença de X for igual a diferença de Y: `abs(tab[linha_anterior] - col_tentativa) == abs(linha_anterior - linha_atual)`.
5. Com a verificação rápida, avance o backtracking registrando o valor da coluna no array.

**Complexidade:** Espaço cai de O(N²) para O(N) real.

- **Input:** `N = 4`
- **Output:** `[1, 3, 0, 2]`

</details>

<details>
  <summary>🔵 Problemas Padrão (Clássicos)</summary>

Estes são os "Hello World" avançados do Backtracking. São amplamente cobrados em exames de seleção corporativos.

### 15. Permutações de uma String

**Descrição:** Dada uma string (ou um array de caracteres), produza todas as reordenações possíveis (permutações) desses caracteres de forma única.

**Intuição:** Fixamos um caractere na primeira posição e permutamos o resto; depois fixamos o segundo caractere, etc. Fazemos isso trocando referências in-place.

**Passo a Passo:**

1. A função base recebe a string convertida para Array, um ponteiro esquerdo `L` (inicial 0) e o ponteiro direito `R` (último índice).
2. Se `L == R`, imprima o array atual, pois a permutação chegou no fim.
3. Se não, inicie um loop `i` indo de `L` até `R`.
4. Faça o _Swap_ (troca) entre o caractere no índice `L` e no índice `i`. Isso equivale a colocar `i` na frente.
5. Chame recursivamente avançando: `permutar(arr, L + 1, R)`.
6. **Backtrack:** Desfaça o _Swap_ entre `L` e `i` para retornar a string ao estado original antes do laço avançar para o próximo caractere.

**Complexidade:** Tempo O(N·N!).

- **Input:** `"ABC"`
- **Output:** `"ABC", "ACB", "BAC", "BCA", "CAB", "CBA"`

### 16. Problema do Passeio do Cavalo Clássico

**Descrição:** Determinar a ordem exata para um cavalo saltar e cobrir todo um tabuleiro N×N sem repetições. Aqui você programará a base bruta do backtracking sem heurísticas de otimização.

**Intuição:** Uma DFS exaustiva tentando todas as 8 direções até preencher as 64 casas.

**Passo a Passo:**

1. Inicialize uma matriz N×N com -1 representando casas não visitadas. Registre a origem com 0 (movimento zero).
2. Declare dois arrays para as coordenadas dos saltos em L (X: `[2, 1, -1, -2, -2, -1, 1, 2]`, Y: `[1, 2, 2, 1, -1, -2, -2, -1]`).
3. Para cada passo da recursão, tente os 8 movimentos fazendo um `for`.
4. Valide o próximo salto: deve estar dentro de 0 e N-1 e a célula de destino deve ser -1.
5. Se válido, insira o número do salto atual na matriz e chame recursão.
6. **Backtrack:** Se falhar, volte a célula para -1.

- **Input:** Origem em (0, 0)
- **Output:** Matriz resolvida com os pulos sequenciais.

### 17. Rato em um Labirinto

**Descrição:** Um rato quer fugir de um labirinto. A matriz é feita de `1` (caminho livre) e `0` (parede de bloqueio). Ele pode se mover D (baixo), L (esquerda), R (direita) e U (cima). Imprima todos os caminhos até o canto inferior direito.

**Intuição:** Devemos tentar as direções na ordem Lexicográfica para que a resposta seja impressa em ordem alfabética (D → L → R → U).

**Passo a Passo:**

1. Verificação básica: se a origem `(0, 0)` ou destino for parede (`0`), aborte imediatamente.
2. Inicie a DFS acumulando uma string de caminho (ex: `"DDR"`).
3. Na posição atual, se chegou no destino, guarde o caminho na lista de retornos.
4. Para mover, altere o valor da célula atual temporariamente para `0` (ou marque em uma matriz de visitados paralela) para impedir ciclos.
5. Tente mover para Baixo, Esquerda, Direita e Cima. Anexe a respectiva letra na chamada recursiva.
6. **Backtrack:** Restaure a célula atual para `1` (ou desmarque de visitado) e retorne.

- **Input:** `[[1,0,0,0], [1,1,0,1], [1,1,0,0], [0,1,1,1]]`
- **Output:** `["DDRDRR", "DRDDRR"]`

### 18. Problema das N Rainhas (Busca Exaustiva)

**Descrição:** Versão generalizada para descobrir uma única configuração segura de `N` rainhas nnum tabuleiro `N × N`.

**Intuição:** Diferente da versão otimizada com array 1D, esta abordagem trabalha diretamente na matriz bidimensional para fins didáticos.

**Passo a Passo:**

1. Passe o índice da coluna por parâmetro.
2. Para achar onde depositar na coluna `C`, itere por todas as linhas `L = 0` até `N-1`.
3. Verifique usando loops a linha para trás e ambas diagonais para a esquerda.
4. Assinale `matriz[L][C] = 1` e chame recursivamente `resolver(C + 1)`.
5. Apague a célula (`= 0`) no backtrack.

**Dica de Implementação:** A verificação se a rainha é atacada pode usar arrays de hash ou bitmask para consultas em O(1).

- **Input:** `N = 4`
- **Output:** `[[0, 1, 0, 0], [0, 0, 0, 1], [1, 0, 0, 0], [0, 0, 1, 0]]`

### 19. Quebra-cabeça Criptográfico de Soma de Palavras

**Descrição:** Resolva o famoso puzzle "SEND + MORE = MONEY". Cada letra do alfabeto representa um algarismo distinto de 0 a 9. Letras iguais são algarismos iguais. Não há zeros à esquerda.

**Intuição:** Precisamos encontrar o mapeamento perfeito (Permutação) combinando caracteres únicos aos dígitos validando contra uma equação matemática.

**Passo a Passo:**

1. Faça a extração das letras únicas de todas as palavras envolvidas e coloque num array (no máximo 10).
2. Crie um array booleano de 0 a 9 marcando quais números já foram usados, e um mapa `letra → valor`.
3. Na recursão, avance pelas letras únicas. Para a letra no índice atual, teste atribuir os números de 0 a 9 que não estiverem em uso.
4. Preencha o mapa, marque o dígito como usado e recursione.
5. Quando todas as letras tiverem um valor, monte os números inteiros correspondentes. Se A + B == C, você achou a solução. Imprima e finalize.
6. **Backtrack:** Desvincule o dígito da letra e desmarque do array numérico antes da próxima iteração.

- **Input:** `"SEND", "MORE", "MONEY"`
- **Output:** `S:9, E:5, N:6, D:7, M:1, O:0, R:8, Y:2`

### 20. Problema da Soma de Subconjunto (Subset Sum)

**Descrição:** Indicar se dentro de um array numérico é possível selecionar um grupo de itens cuja soma exata alcance um valor alvo (`target`).

**Intuição:** Em essência, é um problema que tem raízes em Programação Dinâmica (Knapsack 0/1), mas o algoritmo por backtracking puro é a fundação para entendê-lo.

**Passo a Passo:**

1. A cada nó da árvore de recursão, observe o elemento sob o índice atual.
2. Você pode subtrair o valor dele do alvo global `target` (ação de incluí-lo) e avançar, ou pode deixá-lo ignorado e apenas avançar o índice mantendo o alvo intocado.
3. Se o alvo passar a ser exatamente 0, retorne verdadeiro em cadeia.
4. Se o limite de itens do array acabar, ou se o alvo se tornar estritamente negativo, retorne falso, acionando o backtrack.

**Complexidade:** O(2^N). Em grandes arrays, isso exige Programação Dinâmica para otimização.

- **Input:** `Array: [3, 34, 4, 12, 5, 2], Target: 9`
- **Output:** `True` _(Atingido combinando 4 e 5)_

### 21. Problema de Coloração M de Grafos

**Descrição:** Determinar se um grafo pode ser inteiramente colorido distribuindo no máximo `m` cores entre seus vértices, com a lei de que nenhum vértice vizinho (adjacente) tenha a mesma cor.

**Intuição:** Semelhante ao Sudoku, testamos valores possíveis (cores) em células vazias (nós do grafo) garantindo restrições laterais de forma incremental.

**Passo a Passo:**

1. Inicie um array unidimensional de "cor" inicializado com 0.
2. Processaremos vértice a vértice recursivamente, controlando por um parâmetro `u`.
3. Para o vértice atual `u`, teste cores de 1 até `m`.
4. Uma cor é segura se, olhando na matriz/lista de adjacência, não há aresta de `u` para `v` em que `cor[v]` já seja igual à cor testada.
5. Em cenário seguro, atribua `cor[u] = c` e acione a recursão para `u + 1`.
6. **Backtrack:** Apague a cor: `cor[u] = 0`.

- **Input:** Matriz de Adjacência do Grafo V=4, m = 3
- **Output:** `True` (As cores válidas aplicadas por nó, ex: [1, 2, 3, 2])

### 22. Ciclo Hamiltoniano

**Descrição:** Descubra se existe em um grafo um ciclo que visite rigidamente todos os vértices exatamente uma vez, retornando ao nó de início.

**Intuição:** Uma DFS rigorosa onde o caminho acumulado não apenas precisa atingir o tamanho V, mas o nó final tem que possuir uma via que o religue com a origem.

**Passo a Passo:**

1. Fixe o nó inicial (ex: vértice 0) no array temporário do seu percurso.
2. Busque recursivamente qual o próximo candidato na vizinhança que ainda não conste no array histórico.
3. Se o candidato passar no teste de pureza (inédito na viagem atual), anexe e desça uma camada na árvore de decisões.
4. Quando o número de itens na lista alcançar o total de vértices globais, faça uma varredura final verificando se há uma aresta ligando o último integrante da lista até o elemento da cabeça da lista.
5. **Backtrack:** Descarte o vértice das anotações se os retornos abaixo disserem que se chegou num precipício e suba de volta.

- **Input:** Matriz de Adjacência Booleana/Binária
- **Output:** Caminho circular, por exemplo: [0, 1, 2, 4, 3, 0]

### 23. Sudoku Solver Exaustivo

**Descrição:** Projetar o algoritmo clássico para resolver Sudokus automaticamente. Preencha uma matriz 9×9 com lacunas parcialmente abastecidas, obedecendo às leis: cada linha, coluna e os 9 mini-quadrados internos (3×3) devem exibir algarismos únicos entre 1 e 9.

**Intuição:** Buscar a primeira lacuna vazia, tentar um número. Se não violar a matriz, injete. Se quebrar na frente, apague e tente o próximo algarismo.

**Passo a Passo:**

1. Tenha uma função primária que detecte vazios. Se rodar na matriz iterativamente e não topar com nenhum `0`, vitória declarada.
2. Na célula vazia flagrada, submeta os números possíveis (1 a 9) num laço.
3. Regra de checagem tripla: varrer a linha corrente, a coluna, e calcular a coordenada raiz local do sub-grid 3×3 vasculhando as 9 células dali.
4. Aprovado nos testes? Grave o valor, efetue chamada recursiva e aguarde o booleano de resposta.
5. **Backtrack:** Chumbou? Faça `grade[row][col] = 0` para despovoar.

- **Input:** Matriz 9×9 com valores parciais e marcadores 0 ou -1.
- **Output:** A grade matematicamente resolvida.

### 24. Quebra-cabeça Magnético

**Descrição:** Simule física magnética simples. Você dispõe de blocos retangulares de dominó emparelhados sobre uma tábua. Preencha-os com polos positivos `+` e negativos `-`, observando limitações de volume margenais: polos idênticos nunca deverão partilhar contato horizontal e vertical em lajotas separadas.

**Intuição:** Uma fusão mental do sistema Sudoku e restrições de Coloração.

**Passo a Passo:**

1. As iterações do avanço de Backtracking esquadrinham casa por casa dentro das limitações matriciais.
2. Identifique o formato de bloco da casa lida. Quando topar com espaço virgem, experimente posicionar padrões polarizados binários como `[+, -]` ou `[-, +]`.
3. Dispare averiguação perimetral adjacente de checagem. Dois elementos positivos encostados causam curto circuito lógico.
4. Alcançando o destino das coordenadas, faça balanço contábil sumariando cargas horizontais e longitudinais de preenchimento comparando contagens limites.
5. **Backtrack:** Limpe os polos colocados se ocorrer um conflito de regras ou falha de contagem nas margens.

- **Input:** Matriz esqueleto representativa de blocos, Arrays de restrições das fileiras.
- **Output:** Placa visual preenchida com padrões + -.

### 25. Remover Parênteses Inválidos para Máxima String Válida

**Descrição:** Dada uma string com parênteses desbalanceados, elimine o quantitativo mínimo necessário de falhas, mas faça em _múltiplas variações de combinações perfeitas diferentes_.

**Intuição:** Calcule na largada exatos números brutos do que sobra. Backtracking então funciona apagando a string na quantidade pré estipulada, gerando galhos de variantes filtradas.

**Passo a Passo:**

1. A priori, submeta a palavra bruta a um cálculo com Stack para flagrar o número integral mínimo de erros.
2. Na função autônoma, use um laço For interativo de remoções fatiando a string atual e tirando cirurgicamente parênteses. Cada remoção re-chama uma ramificação deduzindo contagem permitida e avançando checagens balanceadoras.
3. Ao findar cortes, rode balanceamento nativo simples. Adicione resgates limpos finalísticos ao Hashset local a fim de repelir repetições.

- **Input:** `"()())()"`
- **Output:** Coleção Arrays: `["()()()", "(())()"]`

</details>

