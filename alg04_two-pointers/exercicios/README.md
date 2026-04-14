# Lista de Exercícios - Técnica dos Dois Ponteiros

Este documento contém uma lista progressiva e detalhada de problemas focada na técnica de **Dois Ponteiros (Two Pointers)**. O objetivo deste material é desenvolver a sua lógica de programação. Você pode resolver esses problemas utilizando a linguagem de sua preferência (C, C++, Java, Python, Javascript, Go, etc.).

<details>
    <summary>🟢 Nível 1 - Fácil</summary>

<p>

### 1. Remover Ocorrências

**Descrição:** Dado um array e um valor específico (alvo), remova todas as ocorrências desse valor _in-place_ e retorne o novo tamanho válido do array. Não é permitido alocar um novo array.

**Por que usar dois ponteiros?** Um loop simples tentaria deletar o elemento e arrastar todos os outros para a esquerda (muito custoso, O(N²)). Com dois ponteiros, fazemos isso em uma única passada.

**Passo a passo lógico:**

1. Inicialize um ponteiro `escritor` no índice 0. Ele indicará onde o próximo elemento válido deve ser salvo.
2. Utilize um ponteiro `leitor` para iterar linearmente por todos os elementos do array (do índice 0 ao `N-1`).
3. Se o elemento no ponteiro `leitor` for **diferente** do valor alvo, ele é um valor válido. Copie este elemento para a posição atual do ponteiro `escritor`.
4. Incremente o ponteiro `escritor`. Se for igual ao alvo, apenas ignore e avance o `leitor`.
5. Ao final, o valor numérico do `escritor` representará o novo tamanho lógico do array.

**Complexidade:** Tempo O(N) | Espaço O(1).

**Exemplos:**
- **Input Padrão:** `array = [3, 2, 2, 3]`, `alvo = 3`
- **Output Padrão:** `novo_tamanho = 2` (O array físico será `[2, 2, _, _]`)
- **Edge Case (Todos iguais ao alvo):** `array = [4, 4, 4]`, `alvo = 4` → `novo_tamanho = 0`

### 2. Mover Zeros para o Final

**Descrição:** Mova todos os zeros de um array para o final da estrutura, garantindo que a ordem relativa dos elementos não nulos seja mantida.

**Passo a passo lógico:**

1. Inicialize um ponteiro `posicao_nao_zero` em 0. Este ponteiro demarca o limite dos elementos válidos (não-zeros).
2. Use um ponteiro `atual` para percorrer o array do início ao fim.
3. Sempre que o elemento apontado por `atual` for **diferente de zero**, realize uma troca (swap) entre `array[atual]` e `array[posicao_nao_zero]`.
4. Após a troca, incremente o ponteiro `posicao_nao_zero` em 1.
5. Se `atual` apontar para zero, apenas avance-o. Os zeros naturalmente são empurrados para trás.

**Complexidade:** Tempo O(N) | Espaço O(1).

**Exemplos:**
- **Input Padrão:** `array = [0, 1, 0, 3, 12]`
- **Output Padrão:** `[1, 3, 12, 0, 0]`
- **Edge Case (Sem zeros):** `array = [1, 2, 3]` → `[1, 2, 3]` (faz swaps de um elemento com ele mesmo, operação segura)

### 3. Elementos Únicos em Array Ordenado

**Descrição:** Dado um array previamente ordenado, remova os elementos duplicados _in-place_ para que cada elemento apareça estritamente uma única vez e retorne o novo tamanho.

**Por que a ordenação importa?** Como o array está ordenado, elementos duplicados estarão sempre adjacentes, permitindo a detecção imediata.

**Passo a passo lógico:**

1. **Validação de segurança:** Se o tamanho do array for 0 ou 1, retorne o próprio tamanho (não há o que duplicar).
2. Inicialize um ponteiro `unico` no índice 0. Ele guarda o último elemento único confirmado.
3. Use um ponteiro `explorador` iniciando do índice 1 até o final.
4. Se `array[explorador] != array[unico]`, encontramos um número novo! Incremente o `unico` em 1 e, em seguida, sobrescreva `array[unico]` com `array[explorador]`.
5. Retorne `unico + 1` (pois o índice é zero-based, o tamanho é o índice + 1).

**Complexidade:** Tempo O(N) | Espaço O(1).

**Exemplos:**
- **Input:** `array = [1, 1, 2, 2, 3]`
- **Output:** `novo_tamanho = 3` (Array lógico final: `[1, 2, 3, _, _]`)

### 4. Inverter String Preservando a Posição dos Espaços

**Descrição:** Inverta os caracteres alfanuméricos de uma string, mas bloqueie os espaços em branco em suas posições indexadas originais.

**Passo a passo lógico:**

1. Converta a string em um array de caracteres (caso a linguagem exija, já que strings em Java/Python são imutáveis).
2. Inicialize dois ponteiros opostos: `inicio = 0` e `fim = tamanho_da_string - 1`.
3. Crie um loop que continue enquanto `inicio < fim`:
     - Se `array[inicio]` for um espaço (' '), ele deve ficar onde está. Apenas faça `inicio++`.
     - Se `array[fim]` for um espaço (' '), ele também deve ser ignorado. Faça `fim--`.
     - Se **ambos** não forem espaços, aplique a inversão: troque `array[inicio]` por `array[fim]`. Após a troca, mova ambos simultaneamente: `inicio++` e `fim--`.

**Complexidade:** Tempo O(N) | Espaço O(N) para o array de caracteres.

**Exemplos:**
- **Input:** `"abc de"`
- **Output:** `"edc ba"`
- **Edge Case (Múltiplos espaços):** `"a b c"` → `"c b a"`

### 5. Ordenar um Array de 0s, 1s e 2s

**Descrição:** Ordene um array contendo estritamente os inteiros 0, 1 e 2, fazendo isso em uma única iteração sem usar funções de ordenação.

**Contexto:** Este é o famoso problema da "Bandeira Nacional Holandesa" (Dutch National Flag) criado por Edsger Dijkstra.

**Passo a passo lógico (Três Ponteiros):**

1. Defina três marcadores: `baixo = 0` (limite dos 0s), `medio = 0` (o iterador atual), e `alto = n - 1` (limite dos 2s).
2. O loop roda enquanto `medio <= alto` (quando eles se cruzam, tudo está ordenado).
     - **Caso 0** (`array[medio] == 0`): O zero pertence ao início. Troque `array[medio]` com `array[baixo]`. Como ambos agora estão em posições corretas, incremente `baixo++` e `medio++`.
     - **Caso 1** (`array[medio] == 1`): O um já está no meio, onde pertence. Apenas avance o iterador `medio++`.
     - **Caso 2** (`array[medio] == 2`): O dois pertence ao final. Troque `array[medio]` com `array[alto]`. Decremente `alto--`. **Importante:** Não incremente o `medio` aqui, pois o número que veio do final precisa ser avaliado na próxima iteração!

**Complexidade:** Tempo O(N) | Espaço O(1).

**Exemplo:**
- **Input:** `array = [2, 0, 2, 1, 1, 0]`
- **Output:** `[0, 0, 1, 1, 2, 2]`

### 6. Soma de Dois (Two Sum)

**Descrição:** Verifique se existe um par de elementos distintos em um array cuja soma seja exatamente igual a um valor alvo `X`.

**Estratégia:** Se o array não for ordenado, ordene-o primeiro. A magia dos dois ponteiros opostos brilha em arrays ordenados.

**Passo a passo lógico:**

1. Após garantir que o array está ordenado, posicione `esq = 0` e `dir = n - 1`.
2. Em um loop `while (esq < dir)`, calcule a soma provisória: `soma = array[esq] + array[dir]`.
3. Verifique a condição matemática:
     - Se `soma == X`, bingo! Retorne Verdadeiro (ou os índices/valores).
     - Se `soma < X`, precisamos de um valor total maior. A única forma de aumentar a soma em um array ordenado é avançar o ponteiro menor para a direita: `esq++`.
     - Se `soma > X`, precisamos diminuir o valor total. Retraia o ponteiro maior para a esquerda: `dir--`.
4. Se o loop terminar e os ponteiros se cruzarem sem encontrar a soma, retorne Falso.

**Complexidade:** Tempo O(NlogN) para ordenar + O(N) para a busca = O(NlogN) total. Espaço O(1).

**Exemplo:**
- **Input:** `array = [1, 2, 4, 5, 7, 11]`, `X = 9`
- **Output:** `Verdadeiro` (pois 2 + 7 = 9)

### 7. Soma de Par em Array Ordenado e Rotacionado

**Descrição:** Encontre se existe um par com uma soma específica em um array que foi ordenado de forma ascendente e, em seguida, rotacionado em um pivô desconhecido (ex: `[11, 15, 6, 8, 9, 10]`).

**Passo a passo lógico:**

1. O primeiro desafio é encontrar o ponto de quebra (pivô), ou seja, o índice `i` onde `array[i] > array[i+1]`. Isso marca onde os maiores elementos terminam e os menores começam.
2. Defina `esq` como o índice do menor elemento (`pivô + 1`) e `dir` como o índice do maior elemento (`pivô`).
3. Calcule a `soma = array[esq] + array[dir]`.
4. Use aritmética modular para simular o comportamento circular do array:
     - Se `soma == alvo`, retorne Verdadeiro.
     - Se `soma < alvo`, precisamos aumentar. Avance o ponteiro esquerdo circularmente: `esq = (esq + 1) % n`.
     - Se `soma > alvo`, precisamos diminuir. Recue o direito circularmente: `dir = (dir - 1 + n) % n`.
5. Continue até que a busca cubra todos os elementos, limitando os passos ao tamanho do array `n`.

**Complexidade:** Tempo O(N) | Espaço O(1).

**Exemplo:**
- **Input:** `array = [11, 15, 26, 38, 9, 10]`, `alvo = 35`
- **Output:** `Verdadeiro` (26 + 9 = 35)

### 8. Soma de Par Mais Próxima

**Descrição:** Encontre o par de elementos em um array ordenado cuja soma absoluta seja a mais próxima possível de um valor alvo `X`.

**Passo a passo lógico:**

1. Inicialize `esq = 0` e `dir = n - 1`.
2. Crie variáveis rastreadoras: `menor_diferenca = infinito`, e `melhor_esq`, `melhor_dir` para armazenar os valores finais.
3. Calcule a soma atual: `soma_atual = array[esq] + array[dir]`.
4. Calcule a diferença absoluta: `diff = |X - soma_atual|`.
5. Se `diff < menor_diferenca`, atualize a `menor_diferenca` e salve os elementos atuais.
6. Direcione os ponteiros:
     - Se `soma_atual < X`, incremente `esq` (tenta aproximar subindo a soma).
     - Se `soma_atual > X`, decremente `dir` (tenta aproximar descendo a soma).
     - Se `soma_atual == X`, você achou a diferença 0, pode parar imediatamente.

**Complexidade:** Tempo O(N) | Espaço O(1).

**Exemplo:**
- **Input:** `array = [10, 22, 28, 29, 30, 40]`, `X = 54`
- **Output:** `[22, 30]` (Soma = 52, Diferença = 2. A opção `[10, 40]` dá 50, com diferença 4)

### 9. Par Mais Próximo de Dois Arrays Ordenados

**Descrição:** Dados dois arrays ordenados distintos e um número `X`, encontre um elemento do array 1 e outro do array 2 cuja soma seja a mais próxima de `X`.

**Passo a passo lógico:**

1. Como temos arrays diferentes, usaremos ponteiros opostos, mas iniciando em arrays distintos. Inicialize `p1 = 0` (menor valor possível no array 1) e `p2 = m - 1` (maior valor possível no array 2).
2. Avalie a soma `soma = array1[p1] + array2[p2]`.
3. Verifique a diferença absoluta com `X`: `|X - soma|` e atualize sua variável de rastreamento de menor diferença se necessário.
4. Lógica de movimento:
     - Se a soma for menor que `X`, precisamos de um valor maior. Como `p2` já está na metade dos "grandes" do array 2, nossa única opção é tentar um valor maior no array 1: incremente `p1++`.
     - Se a soma for maior que `X`, precisamos de um menor. Decremente `p2--`.

**Complexidade:** Tempo O(N+M) | Espaço O(1).

**Exemplo:**
- **Input:** `arr1 = [1, 4, 5, 7]`, `arr2 = [10, 20, 30, 40]`, `X = 32`
- **Output:** `[1, 30]` (Soma = 31, dif = 1)

### 10. Menor Subarray Maior que a Soma

**Descrição:** Encontre o comprimento do menor subarray contíguo cuja soma acumulada seja estritamente maior que um valor dado.

**Estratégia (Janela Deslizante):** Este é o caso de uso clássico onde os dois ponteiros formam uma janela que estica e encolhe.

**Passo a passo lógico:**

1. Inicialize dois ponteiros no início: `inicio = 0`, `fim = 0`. Crie `soma_atual = 0` e `tamanho_minimo = infinito`.
2. **Fase de Expansão:** Enquanto `fim < n`, vá adicionando `array[fim]` à `soma_atual` e incremente `fim++`.
3. **Fase de Contração:** Sempre que `soma_atual > valor_dado`, entramos em um loop secundário interno:
     - Comparamos o tamanho da janela atual `(fim - inicio)` com o `tamanho_minimo` salvo e atualizamos se for menor.
     - Subtraia `array[inicio]` da `soma_atual` e faça `inicio++`.
4. Repita a expansão e contração até o `fim` percorrer todo o array.

**Complexidade:** Tempo O(N) (cada elemento é visitado no máximo duas vezes) | Espaço O(1).

**Exemplo:**
- **Input:** `array = [1, 4, 45, 6, 0, 19]`, `alvo = 51`
- **Output:** `3` (O subarray `[4, 45, 6]` soma 55. Apesar de tamanho 4 também ser válido, 3 é o mínimo)

### 11. Pares Dominantes

**Descrição:** Dado um array de tamanho par `n`, encontre o número de pares `(i, j)` onde `0 <= i < n/2` (primeira metade), `n/2 <= j < n` (segunda metade), e cumpra a condição `array[i] >= 5 * array[j]`.

**Passo a passo lógico:**

1. A chave aqui é tratar o array como duas metades independentes. Separe a primeira metade e a segunda metade e ordene-as individualmente (por exemplo, ambas em ordem decrescente).
2. **Por que ordenar?** Se sabemos que `array[i]` satisfaz a condição para um certo `array[j]`, e a segunda metade está ordenada de forma decrescente, ele **obrigatoriamente** satisfará para todos os elementos menores após `j`.
3. Coloque um ponteiro `i = 0` e `j = n/2`.
4. Avalie: Se `array[i] >= 5 * array[j]`:
     - Como a metade 2 é decrescente, qualquer elemento após `j` será ainda menor. Então, o elemento `i` forma pares válidos com todo o resto da segunda metade!
     - Adicione `(n - j)` ao seu contador total.
     - Como extraímos o máximo de `i`, avance `i++` para o próximo número da primeira metade.
5. Se não cumprir a condição, precisamos de um `array[j]` menor para satisfazer a equação, então avance `j++`.

**Complexidade:** Tempo O(NlogN) | Espaço O(1) ou dependente do algoritmo de sort.

**Exemplo:**
- **Input:** `array = [10, 8, 2, 1, 1, 2]`
- **Output:** `2` (Pares válidos ocorrem entre as metades ordenadas. 10 domina 1 e 10 domina 2)

### 12. Palíndromo de Frase

**Descrição:** Verifique se uma frase completa é um palíndromo, ignorando estritamente todos os espaços, pontuações e neutralizando diferenças entre letras maiúsculas e minúsculas.

**Passo a passo lógico:**

1. Posicione ponteiros nas extremidades: `inicio = 0` e `fim = tamanho_string - 1`.
2. Em um loop enquanto `inicio < fim`:
     - **Bypass da esquerda:** Use um loop interno para avançar `inicio++` se o caractere atual **não for** uma letra ou número.
     - **Bypass da direita:** Use outro loop interno para retroceder `fim--` se não for alfanumérico.
     - **Importante:** Garanta que nestes sub-loops internos o `inicio` nunca ultrapasse o `fim`.
     - **Comparação:** Com os ponteiros limpos, converta ambos os caracteres para minúsculo. Se `char_inicio != char_fim`, pare e retorne Falso.
     - Se forem iguais, continue: `inicio++` e `fim--`.
3. Se os ponteiros se encontrarem, todas as comparações passaram: retorne Verdadeiro.

**Complexidade:** Tempo O(N) | Espaço O(1).

**Exemplo:**
- **Input:** `"A man, a plan, a canal: Panama"`
- **Output:** `Verdadeiro` (Avalia apenas `amanaplanacanalpanama`)

### 13. Intersecção de Arrays com Elementos Distintos

**Descrição:** Dados dois arrays que garantidamente contêm apenas elementos distintos internamente, retorne um novo array ordenado contendo os elementos (intersecção) presentes em ambos.

**Passo a passo lógico:**

1. Como a técnica exige ordem para ser linear, ordene ambos os arrays se já não vierem ordenados.
2. Inicialize `p1 = 0` (marcando o array 1) e `p2 = 0` (marcando o array 2). Crie uma lista/array de resultado.
3. Enquanto `p1 < tamanho1` e `p2 < tamanho2`:
     - Faça a comparação base: `valor1 = arr1[p1]` e `valor2 = arr2[p2]`.
     - Se `valor1 == valor2`: Achamos uma intersecção! Adicione à resposta. Como ambos os arrays são estritamente distintos, avance ambos simultaneamente (`p1++`, `p2++`).
     - Se `valor1 < valor2`: O `valor1` atual ficou "para trás" e nunca encontrará um par igual à frente no arr2. Avance `p1++` para tentar encontrar um número maior.
     - Se `valor1 > valor2`: Pela mesma lógica, avance `p2++`.

**Complexidade:** Tempo O(NlogN+MlogM) | Espaço O(min(N,M)) para a resposta.

**Exemplo:**
- **Input:** `arr1 = [7, 1, 5, 2, 3, 6]`, `arr2 = [3, 8, 6, 20, 7]`
- **Output:** `[3, 6, 7]` (Após ordenação: arr1 = `[1, 2, 3, 5, 6, 7]`, arr2 = `[3, 6, 7, 8, 20]`)

</p>

</details>

<details>
    <summary>🟠 Nível 2 - Médio</summary>

<p>

### 14. Contar Pares com Diferença Absoluta Igual a k

**Descrição:** Determine o número total de pares `(i, j)` em um array cuja diferença absoluta `|array[j] - array[i]|` seja estritamente igual a um valor alvo `k`.

**Passo a passo lógico:**

1. **Primeiro passo crucial:** Ordene o array. Diferente da soma, a diferença requer controle direcional preciso.
2. Posicione ambos os ponteiros no início do array, mas desfasados: `i = 0` e `j = 1`. Eles se moverão na mesma direção.
3. Em um loop `while (i < n e j < n)`:
     - **Validação de distanciamento:** Se `i == j` em algum momento, force `j++` para garantir que estamos comparando elementos diferentes.
     - Calcule `diff = array[j] - array[i]`.
     - Se `diff == k`: Encontramos um par! Incremente o contador e avance `j++`.
     - Se `diff < k`: A diferença está muito pequena. Para aumentá-la, avance `j++`.
     - Se `diff > k`: A diferença estourou o limite. Para reduzi-la, avance `i++`.

**Complexidade:** Tempo O(NlogN) | Espaço O(1).

**Exemplo:**
- **Input:** `array = [1, 5, 3, 4, 2]`, `k = 3`
- **Output:** `2` (Pares no array ordenado `[1, 2, 3, 4, 5]` são `[1, 4]` e `[2, 5]`)

### 15. Soma de Trio no Array

**Descrição:** Identifique se há existência de exatamente três elementos (um trio) em um array cuja soma totalize um valor alvo `X`.

**Por que este problema é genial?** Ele ensina a quebrar um problema 3D em um problema 2D. Ao congelar um elemento, o problema se reduz ao clássico "Two Sum".

**Passo a passo lógico:**

1. Ordene o array em ordem crescente.
2. Use um laço `for` externo iterando um índice `i` de `0` até `n - 3`. Este laço fixa a primeira peça do nosso trio.
3. Dentro do laço, os ponteiros restantes entram em ação: defina `esq = i + 1` e `dir = n - 1`.
4. Aplique a lógica do Two Sum para o restante:
     - Calcule `soma_atual = array[i] + array[esq] + array[dir]`.
     - Se `soma_atual == X`: Retorne Verdadeiro.
     - Se `soma_atual < X`: Incremente `esq++`.
     - Se `soma_atual > X`: Decremente `dir--`.

**Complexidade:** Tempo O(N²) | Espaço O(1).

**Exemplo:**
- **Input:** `array = [1, 4, 45, 6, 10, 8]`, `X = 22`
- **Output:** `Verdadeiro` (Trio: 4 + 10 + 8)

### 16. Soma de Dois Igual ao Terceiro

**Descrição:** Descubra se, dentro do array, existem dois elementos cuja soma é cirurgicamente igual a um terceiro elemento presente no mesmo array.

**Passo a passo lógico:**

1. **Ordene o array**.
2. **A sacada:** Como a soma de dois números em um array positivo sempre será maior que as partes, o número "Alvo" deve ser sempre um dos maiores números do array.
3. Itere de **trás para frente** com um loop `for`, onde a âncora `i` começa em `n - 1` até `2`. Este `array[i]` será o "Alvo da vez".
4. Defina os dois ponteiros: `esq = 0` (o menor de todos) e `dir = i - 1` (o maior logo antes do alvo).
5. Com a fórmula `array[esq] + array[dir] == array[i]`:
     - Se forem iguais, retorne Verdadeiro.
     - Se a soma for menor que a âncora, incremente `esq++`.
     - Se a soma for maior, decremente `dir--`.

**Complexidade:** Tempo O(N²) | Espaço O(1).

**Exemplo:**
- **Input:** `array = [5, 32, 1, 7, 10, 50, 19, 21, 2]`
- **Output:** `Verdadeiro` (Após ordenar: `1, 2, 5, 7...` A soma de 2 + 5 = 7 é validada)

### 17. K-ésimo Elemento de Dois Arrays

**Descrição:** Juntar virtualmente dois arrays ordenados e retornar o elemento que ocuparia exatamente a k-ésima posição, sem alocar um terceiro array.

**Passo a passo lógico:**

1. A configuração requer leitura em duas pistas simultâneas: `p1 = 0` (início do array 1) e `p2 = 0` (início do array 2).
2. Crie uma variável `contador = 0` para rastrear sua posição virtual no "novo array invisível".
3. Crie um loop `while (p1 < tamanho1 e p2 < tamanho2)`:
     - Avalie o menor valor disponível: se `arr1[p1] < arr2[p2]`.
     - Identificado o menor valor, registre-o em uma variável `atual`, incremente `contador++` e avance o ponteiro do vencedor (`p1++`).
     - Caso o `arr2[p2]` fosse menor ou igual, faria o mesmo com o `p2`.
     - **Checagem Imediata:** Se `contador == k`, a resposta é `atual`. Interrompa.
4. **Tratamento de Exaustão:** Se o loop principal terminar e `contador < k`, faça loops adicionais exclusivos para esvaziar `p1` ou `p2` até bater `k`.

**Complexidade:** Tempo O(K) | Espaço O(1).

**Exemplo:**
- **Input:** `arr1 = [2, 3, 6, 7, 9]`, `arr2 = [1, 4, 8, 10]`, `k = 5`
- **Output:** `6` (Evolução virtual: 1 → 2 → 3 → 4 → 6)

### 18. União de 2 Arrays Ordenados com Duplicatas

**Descrição:** Calcule a união formal de dois arrays ordenados. Os elementos da resposta devem ser distintos e estar ordenados.

**Passo a passo lógico:**

1. Coloque os ponteiros de largada: `i = 0` e `j = 0`. Aloque uma estrutura de lista dinâmica para acumular o resultado.
2. Inicie o loop `while(i < n && j < m)`:
     - **Bypass de Duplicidade Interna:** Se `arr1[i]` for igual ao elemento anterior, pule com `i++`. Faça o mesmo para `arr2[j]`.
     - **Comparação Inter-Arrays:**
         - Se `arr1[i] < arr2[j]`: Adicione `arr1[i]` à resposta e mova `i++`.
         - Se `arr2[j] < arr1[i]`: Adicione `arr2[j]` à resposta e mova `j++`.
         - Se `arr1[i] == arr2[j]`: Adicione-o uma única vez e avance ambos (`i++` e `j++`).
3. **Rescaldo Final:** Crie loops `while` separados para despejar os elementos remanescentes de `arr1` ou `arr2`, aplicando a regra do "Bypass de Duplicidade Interna".

**Complexidade:** Tempo O(N+M) | Espaço O(N+M) para a lista final.

**Exemplo:**
- **Input:** `arr1 = [1, 2, 2, 2, 3]`, `arr2 = [2, 3, 4, 5]`
- **Output:** `[1, 2, 3, 4, 5]`

### 19. Subarrays com Máximo no Intervalo

**Descrição:** Determine o número total de subarrays contíguos onde o maior valor numérico caia estritamente no intervalo fechado `[L, R]`.

**Estratégia:** Use a propriedade de conjuntos: (Subarrays cujo Max ≤ R) - (Subarrays cujo Max < L).

**Passo a passo lógico:**

1. Crie uma função auxiliar `contaSubarraysValidos(array, Limite_K)`:
     - Inicialize `total = 0` e `janela = 0`.
     - Percorra cada elemento do array:
         - Se `array[i] <= Limite_K`, expanda a janela: `janela++` e adicione `total += janela`.
         - Se `array[i] > Limite_K`, zere a janela: `janela = 0`.
2. Na função principal: `retorne contaSubarraysValidos(arr, R) - contaSubarraysValidos(arr, L - 1)`.

**Complexidade:** Tempo O(N) | Espaço O(1).

**Exemplo:**
- **Input:** `array = [2, 0, 11, 3, 0]`, `L = 1`, `R = 10`
- **Output:** `4` (Subarrays válidos: `[2]`, `[2, 0]`, `[3]`, `[3, 0]`. O número 11 explode qualquer janela)

### 20. Maior Substring com K Caracteres Únicos

**Descrição:** Identifique o tamanho da maior cadeia de caracteres consecutiva contendo exatamente `K` caracteres totalmente distintos.

**Passo a passo lógico:**

1. Inicialize `esq = 0` e `dir = 0`. Crie `maior_tamanho = -1` e um dicionário para `[letra -> frequência]`.
2. O loop mestre avança `dir` a cada ciclo:
     - Coloque a letra atual no dicionário. Se já existir, aumente a frequência. Se for inédita, inicie em 1.
3. Se o número de chaves for menor que `K`, continue avançando `dir`.
4. Se o número de chaves for **igual** a `K`: Calcule largura `(dir - esq + 1)` e compare salvando se for maior.
5. Se o número de chaves **superar** `K`: Purge elementos a partir de `esq`:
     - Diminua a frequência do caractere que `esq` aponta.
     - Se a frequência atingir zero, apague a chave do mapa.
     - Avance `esq++`.

**Complexidade:** Tempo O(N) | Espaço O(K).

**Exemplo:**
- **Input:** `string = "aabbcc"`, `k = 2`
- **Output:** `4` (Janelas vencedoras: "aabb" ou "bbcc")

### 21. Remover e Inverter

**Descrição:** Fornecida uma string, remova a primeira letra repetida encontrada e revert a string. Repita até que só restarem caracteres distintos.

**Visão de Ouro:** Não inverta strings fisicamente. Simule apenas mudando a leitura para trás e para frente.

**Passo a passo lógico:**

1. Crie um dicionário rastreando a frequência de todos os caracteres.
2. Defina `esq = 0`, `dir = tamanho - 1` e `sentido_normal = Verdadeiro`.
3. Abra um loop enquanto `esq <= dir`:
     - **Fase Esquerda (Se `sentido_normal == Verdadeiro`):**
         - Analise o caractere em `esq`.
         - Tem frequência > 1? Delete (marque com `'#'`), apague `#` ao final, mude para `sentido_normal = Falso` e aplique `dir--`.
         - Frequência = 1? Avance `esq++`.
     - **Fase Direita (Se `sentido_normal == Falso`):**
         - Analise o caractere em `dir`.
         - Frequência > 1? Delete, mude para `sentido_normal = Verdadeiro` e avance `esq++`.
         - Frequência = 1? Recue `dir--`.
4. **Retorno:** Remova os marcadores `'#'`. Se `sentido_normal == Falso` ao final, reverta a string.

**Complexidade:** Tempo O(N) | Espaço O(N).

**Exemplo:**
- **Input:** `"abab"`
- **Output:** `"ba"`

### 22. O Problema da Celebridade

**Descrição:** Encontre a celebridade em uma festa: alguém que todos conhecem, mas que não conhece ninguém.

**Passo a passo lógico:**

1. Crie uma arena imaginária: `A = 0` (início) e `B = n - 1` (fim).
2. Loop enquanto `A < B`:
     - Chame `conhece(A, B)`.
     - Se Verdadeiro: "A" conhece "B", então "A" não é celebridade. Retire com `A++`.
     - Se Falso: "B" não é conhecido por "A", então "B" não é celebridade. Retire com `B--`.
3. Ao fim, `A == B`. A pessoa "A" é a celebridade potencial.
4. **Verificação:** Teste "A" com todos os outros. Se "A" conhecer alguém ou alguém não conhecer "A", retorne `-1`. Caso contrário, "A" é a celebridade.

**Complexidade:** Tempo O(N) | Espaço O(1).

**Exemplo:**
- **Input:**
    ```
    [[0, 1, 0],   <- Pessoa 0: conhece 1
     [0, 0, 0],   <- Pessoa 1: não conhece ninguém
     [0, 1, 0]]   <- Pessoa 2: conhece 1
    ```
- **Output:** Pessoa 1 é a celebridade

</p>

</details>

<details>
    <summary>🔴 Nível 3 - Difícil</summary>

<p>

### 23. Problema de Retenção de Água da Chuva

**Descrição:** Dado um array representando elevação de blocos, calcule quantas unidades cúbicas de água chovida serão confinadas entre os blocos.

**O Conceito:** Para qualquer bloco na posição `i`, a água acumulada é determinada por: `min(maximo_esq, maximo_dir) - altura_local`.

**Passo a passo lógico:**

1. Delimitação geográfica: `esq = 0` e `dir = tamanho - 1`.
2. Inicialize `pico_max_esq = 0`, `pico_max_dir = 0` e `agua_armazenada = 0`.
3. Loop enquanto `esq <= dir`:
     - **Se `terreno[esq] <= terreno[dir]`:** A parede direita é o limitador. Trabalhe com `esq`:
         - Se `terreno[esq] >= pico_max_esq`, atualize `pico_max_esq = terreno[esq]`.
         - Caso contrário, acumule água: `agua_armazenada += pico_max_esq - terreno[esq]`.
         - Avance `esq++`.
     - **Caso contrário:** A parede esquerda é o limitador. Trabalhe com `dir` (simetricamente):
         - Se `terreno[dir] >= pico_max_dir`, atualize `pico_max_dir = terreno[dir]`.
         - Caso contrário, acumule água: `agua_armazenada += pico_max_dir - terreno[dir]`.
         - Recue `dir--`.

**Complexidade:** Tempo O(N) | Espaço O(1).

**Exemplo:**
- **Input:** `array = [0, 1, 0, 2, 1, 0, 1, 3, 2, 1, 2, 1]`
- **Output:** `6`

### 24. Soma de Quatro - Verificar Quádruplo

**Descrição:** Verifique se existem 4 números em um array cuja soma seja igual a um alvo `X`.

**Estratégia:** Reduza O(N⁴) para O(N³) usando duas âncoras e Two Pointers.

**Passo a passo lógico:**

1. **Ordene o array**.
2. Laço externo com `i` de `0` a `n-4`.
3. Laço interno com `j` de `i+1` a `n-3`.
4. Defina `esq = j + 1` e `dir = n - 1`.
5. Loop com Two Pointers:
     - Calcule `Soma = array[i] + array[j] + array[esq] + array[dir]`.
     - Se `Soma == alvo`: Retorne Verdadeiro.
     - Se `Soma < alvo`: `esq++`.
     - Se `Soma > alvo`: `dir--`.

**Complexidade:** Tempo O(N³) | Espaço O(1).

**Exemplo:**
- **Input:** `array = [10, 2, 3, 4, 5, 9, 7, 8]`, `alvo = 23`
- **Output:** `Verdadeiro` (Quádruplo: `[3, 5, 7, 8]`)

### 25. Soma de Quatro – Todos os Quádruplos Distintos com Soma Dada

**Descrição:** Retorne **todos** os quádruplos distintos cuja soma seja igual ao alvo, sem duplicatas.

**Passo a passo lógico:**

1. **Ordene o array**.
2. Laço duplo (âncoras) com **bloqueios anti-clonagem**:
     - Se `array[i] == array[i-1]` (e `i > 0`), pule (`continue`).
     - Se `j > i + 1` e `array[j] == array[j-1]`, pule (`continue`).
3. Laço Two Pointers:
     - Se `array[i] + array[j] + array[esq] + array[dir] == alvo`:
         - Adicione o quádruplo à resposta.
         - Avance `esq++` e `dir--`.
         - **Bloqueios de movimento:** Enquanto `esq < dir` e `array[esq] == array[esq+1]`, incremente `esq`. Enquanto `esq < dir` e `array[dir] == array[dir-1]`, decremente `dir`.
     - Caso contrário, ajuste os ponteiros normalmente.

**Complexidade:** Tempo O(N³) | Espaço O(1) ou O(resultado).

**Exemplo:**
- **Input:** `array = [1, 0, -1, 0, -2, 2]`, `alvo = 0`
- **Output:** `[[-2, -1, 1, 2], [-2, 0, 0, 2], [-1, 0, 0, 1]]`

### Conclusão e Dicas Finais

A técnica de Dois Ponteiros é uma das ferramentas mais belas e poderosas da lógica de programação. Quando você olha para um problema que parece exigir O(N²), pergunte-se:

1. **Posso ordenar este array?** (O sort custa O(NlogN), frequentemente compensador)
2. **Tenho ponteiros opostos ou em paralelo para explorar a estrutura?** (Two Sum, Remove Duplicates)
3. **A solução requer uma janela que se expande e contrai?** (Sliding Window)

Pratique massivamente até automatizar a reação instintiva para estes padrões. Boa sorte em seus estudos!

</p>

</details>

