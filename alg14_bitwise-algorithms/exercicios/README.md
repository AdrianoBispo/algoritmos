# Lista de Exercícios - Algoritmos de Bitwise

Este documento contém uma lista progressiva de problemas focados em manipulação de bits (Bitwise). O objetivo não é fornecer o código pronto, mas sim a descrição detalhada do problema, a intuição matemática por trás da solução, o algoritmo lógico passo a passo e os exemplos de entrada e saída. Este formato permite que você implemente a solução na sua linguagem de programação favorita (C, C++, Java, Python, JavaScript, Rust, Go, etc.).

### Por que estudar Algoritmos Bitwise?

Operações em nível de bit são executadas diretamente pela Unidade Lógica e Aritmética (ALU) do processador, tornando-as ordens de magnitude mais rápidas do que operações aritméticas tradicionais (como multiplicação, divisão ou módulo). Elas são amplamente utilizadas em:

-   **Sistemas Embarcados e Drivers:** Para ler, ligar ou desligar flags e sensores específicos em registradores de hardware.
    
-   **Criptografia e Redes:** Operações como `XOR` formam a base de cifras de fluxo, cálculos de paridade e verificação de redundância (CRC).
    
-   **Otimização de Memória e Processamento:** Estruturas como _Bitsets_ permitem armazenar 32 ou 64 valores booleanos em uma única variável inteira.
    
-   **Programação Dinâmica:** Técnicas de _Bitmasking_ reduzem drasticamente o espaço de estados em problemas combinatórios complexos (como o Caixeiro Viajante).

<details>
  <summary>🟢 Nível 1 - Fácil</summary>

### 1. Representação binária

-   **Descrição:** Dado um número inteiro decimal positivo, converta-o para sua representação binária em formato de string.
    
-   **Intuição:** A base 2 funciona em potências de 2. O resto da divisão por 2 (equivalente a `n & 1`) nos dá o bit menos significativo. Deslocar para a direita (`n >> 1`) divide o número por 2, preparando o próximo bit.
    
-   **Passo a Passo:**
    1. Crie uma estrutura mutável (array de caracteres, `StringBuilder` ou lista) para armazenar os bits.
    2. Inicie um laço enquanto `n > 0`.
    3. Obtenha o último bit: `bit = n & 1`.
    4. Adicione o bit à estrutura.
    5. Desloque o número: `n = n >> 1`.
    6. Inverta a estrutura para obter a ordem correta.
    
-   **Complexidade:** Tempo `O(log n)` | Espaço `O(log n)`
    
-   **Exemplo:** **Entrada:** `14` | **Saída:** `1110`

### 2. Desligar o bit 1 mais à direita

-   **Descrição:** Dado um inteiro, altere o seu bit `1` mais à direita para `0`, preservando todos os outros bits.
    
-   **Intuição:** Ao subtrair 1 de um número, todos os bits `0` à direita do bit `1` menos significativo tornam-se `1`, e esse bit `1` específico torna-se `0` (ex: `10100 - 1 = 10011`). Fazer um `AND` com o original anula essa parte alterada.
    
-   **Passo a Passo:**
    1. Subtraia 1 do número: `n - 1`.
    2. Aplique `AND`: `n & (n - 1)`.
    
-   **Complexidade:** Tempo `O(1)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `12` (1100) | **Saída:** `8` (1000)

### 3. Verificar se o k-ésimo bit está definido

-   **Descrição:** Verifique se o k-ésimo bit (da direita para a esquerda, começando em 1) de um número é igual a `1`.
    
-   **Intuição:** Crie uma máscara que isole apenas a posição desejada.
    
-   **Passo a Passo:**
    1. Desloque `1` para a esquerda `k - 1` vezes: `1 << (k - 1)`.
    2. Faça `AND` com o número: `n & máscara`.
    3. Se diferente de 0, o bit está definido.
    
-   **Complexidade:** Tempo `O(1)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `n = 5` (101), `k = 1` | **Saída:** `Verdadeiro`

### 4. Definir o k-ésimo bit

-   **Descrição:** Dado um número, mude o seu k-ésimo bit para `1`, preservando os outros bits.
    
-   **Intuição:** O operador `OR` (|) liga bits garantindo resultado `1` se pelo menos um for `1`.
    
-   **Passo a Passo:**
    1. Crie uma máscara: `1 << (k - 1)`.
    2. Aplique `OR`: `n | máscara`.
    
-   **Complexidade:** Tempo `O(1)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `n = 10` (1010), `k = 1` | **Saída:** `11` (1011)

### 5. Módulo pela potência de 2

-   **Descrição:** Calcule `n % d` sabendo que `d` é uma potência exata de 2.
    
-   **Intuição:** Se `d = 2^x`, então `d - 1` é um número com `x` bits `1` consecutivos. Os bits após esse ponto representam o resto.
    
-   **Passo a Passo:**
    1. Identifique que `d - 1` para `d = 2^x` gera uma máscara apropriada.
    2. Aplique `AND`: `n & (d - 1)`.
    
-   **Complexidade:** Tempo `O(1)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `n = 6` (0110), `d = 4` | **Saída:** `2`

### 6. Número de ocorrências ímpares

-   **Descrição:** Dado um array onde todos os elementos aparecem um número par de vezes, exceto um que aparece ímpar. Encontre esse elemento sem usar estruturas adicionais.
    
-   **Intuição:** O operador `XOR` garante que `x ^ x = 0` e `x ^ 0 = x`. Elementos pares se anulam.
    
-   **Passo a Passo:**
    1. Inicialize `resultado = 0`.
    2. Percorra todos os elementos: `resultado ^= array[i]`.
    3. Ao final, restará apenas o elemento ímpar.
    
-   **Complexidade:** Tempo `O(N)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `[1, 2, 3, 2, 3, 1, 3]` | **Saída:** `3`

### 7. Potência de dois

-   **Descrição:** Determine se um inteiro positivo é uma potência exata de 2.
    
-   **Intuição:** Potências de 2 têm exatamente um bit `1` (ex: 16 = 10000). `n & (n - 1)` remove esse bit único.
    
-   **Passo a Passo:**
    1. Verifique `n > 0`.
    2. Aplicar `n & (n - 1) == 0`.
    
-   **Complexidade:** Tempo `O(1)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `16` | **Saída:** `Verdadeiro`

### 8. O único bit definido

-   **Descrição:** Dado um número que é garantidamente uma potência de 2, encontre a posição (baseada em 1) do seu único bit.
    
-   **Intuição:** Inspecione posição por posição usando deslocamentos até zeragem.
    
-   **Passo a Passo:**
    1. Inicialize `posição = 1`.
    2. Enquanto `n > 0`: `n >>= 1`, `posição++`.
    3. Retorne `posição - 1`.
    
-   **Complexidade:** Tempo `O(log n)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `16` (10000) | **Saída:** `5`

### 9. Somar strings bit a bit

-   **Descrição:** Dadas duas strings binárias, retorne a soma em formato de string binária.
    
-   **Intuição:** Simule soma com "vai um" (carry) do final para o início.
    
-   **Passo a Passo:**
    1. Inicie dos finais das strings.
    2. Mantenha `carry = 0`.
    3. Processe: `soma = bit1 + bit2 + carry`, extraia resultado e carry.
    4. Inverta a string final.
    
-   **Complexidade:** Tempo `O(max(N, M))` | Espaço `O(max(N, M))`
    
-   **Exemplo:** **Entrada:** `"11", "1"` | **Saída:** `"100"`

### 10. Verificar overflow inteiro

-   **Descrição:** Detecte se `a + b` gera overflow em inteiros de 32 bits sem falhas.
    
-   **Intuição:** Overflow ocorre quando dois números de mesmo sinal resultam em sinal oposto.
    
-   **Passo a Passo:**
    1. Efetue `resultado = a + b`.
    2. Verifique: `(a > 0 && b > 0 && resultado < 0) || (a < 0 && b < 0 && resultado >= 0)`.
    
-   **Complexidade:** Tempo `O(1)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `a = 2147483640, b = 10` | **Saída:** `Overflow Detectado`

### 11. XOR sem usar XOR

-   **Descrição:** Replique `XOR` usando apenas `AND`, `OR` e `NOT`.
    
-   **Intuição:** XOR liga um bit se os operandos forem **diferentes**: `(x | y) & ~(x & y)`.
    
-   **Passo a Passo:**
    1. `parte_or = x | y`.
    2. `parte_and = x & y`.
    3. `resultado = parte_or & ~parte_and`.
    
-   **Complexidade:** Tempo `O(1)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `x = 3` (011), `y = 5` (101) | **Saída:** `6` (110)

### 12. Verificar igualdade

-   **Descrição:** Verifique se dois números são iguais sem usar operadores de comparação ou aritmética.
    
-   **Intuição:** `x ^ y = 0` se e somente se `x = y`.
    
-   **Passo a Passo:**
    1. `resultado = x ^ y`.
    2. Se `resultado == 0`, números são iguais.
    
-   **Complexidade:** Tempo `O(1)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `10, 10` | **Saída:** `Verdadeiro`

### 13. Verificar sinais opostos

-   **Descrição:** Descubra se dois números possuem sinais opostos.
    
-   **Intuição:** Em Complemento de Dois, o MSB (More Significant Bit) define o sinal. `XOR` entre números de sinais opostos resulta em número negativo.
    
-   **Passo a Passo:**
    1. `resultado = x ^ y`.
    2. Se `resultado < 0`, sinais são opostos.
    
-   **Complexidade:** Tempo `O(1)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `-1, 2` | **Saída:** `Verdadeiro`

### 14. Trocar dois números

-   **Descrição:** Execute swap entre duas variáveis sem temporária.
    
-   **Intuição:** XOR permite guardar informações combinadas de dois números em uma variável.
    
-   **Passo a Passo:**
    1. `a = a ^ b`.
    2. `b = a ^ b`.
    3. `a = a ^ b`.
    
-   **Casos de Borda:** Não use com índices iguais (zerará o valor).
    
-   **Complexidade:** Tempo `O(1)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `a = 5, b = 7` | **Saída:** `a = 7, b = 5`

### 15. Peasant russo (Multiplicação Russa)

-   **Descrição:** Multiplique dois inteiros usando adição, deslocamento e operações lógicas.
    
-   **Intuição:** Em binário, multiplicar é somar `a` nas posições onde `b` tem bit `1`.
    
-   **Passo a Passo:**
    1. `resultado = 0`.
    2. Enquanto `b > 0`:
       - Se `b & 1`: `resultado += a`.
       - `a <<= 1`, `b >>= 1`.
    
-   **Complexidade:** Tempo `O(log b)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `a = 18, b = 5` | **Saída:** `90`

</details>

<details>
  <summary>🟠 Nível 2 - Médio</summary>

### 16. Bit definido mais significativo

-   **Descrição:** Isole apenas o bit `1` mais à esquerda (MSB), zerando o resto.
    
-   **Intuição:** Espalhar MSB para direita criando máscara contínua de 1s, depois subtrair para isolar.
    
-   **Passo a Passo:**
    1. Espalhe MSB: `n |= (n >> 1); n |= (n >> 2); n |= (n >> 4); n |= (n >> 8); n |= (n >> 16)`.
    2. Isole: `resultado = n - (n >> 1)`.
    
-   **Complexidade:** Tempo `O(1)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `18` (10010) | **Saída:** `16` (10000)

### 17. Bit definido mais à direita

-   **Descrição:** Isole apenas o bit `1` mais à direita, zerando o resto.
    
-   **Intuição:** Propriedades do Complemento de Dois garantem que `n & -n` resulta no bit mais à direita.
    
-   **Passo a Passo:**
    1. `resultado = n & -n`.
    
-   **Complexidade:** Tempo `O(1)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `12` (1100) | **Saída:** `4` (0100)

### 18. Contar bits definidos (Algoritmo de Brian Kernighan)

-   **Descrição:** Conte quantos bits com valor `1` existem na representação binária.
    
-   **Intuição:** `n & (n - 1)` remove o bit `1` mais à direita. Repita até zerar.
    
-   **Passo a Passo:**
    1. `contador = 0`.
    2. Enquanto `n > 0`: `n &= (n - 1)`, `contador++`.
    
-   **Complexidade:** Tempo `O(K)` onde K é a quantidade de bits `1` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `13` (1101) | **Saída:** `3`

### 19. Trocar bits

-   **Descrição:** Troque bits nas posições pares com seus vizinhos ímpares.
    
-   **Intuição:** Use máscaras para isolar pares e ímpares, depois deslocar e combinar.
    
-   **Passo a Passo:**
    1. `pares = n & 0x55555555`.
    2. `impares = n & 0xAAAAAAAA`.
    3. `resultado = (pares << 1) | (impares >> 1)`.
    
-   **Complexidade:** Tempo `O(1)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `23` (00010111) | **Saída:** `43` (00101011)

### 20. Rotacionar bits

-   **Descrição:** Rotacione circularmente bits em um tamanho fixo.
    
-   **Intuição:** Armazene os bits que "saem" e reencaixe-os no outro lado.
    
-   **Passo a Passo:**
    1. `d = d % 32`.
    2. `parte_movida = (n << d)`.
    3. `parte_resgatada = (n >> (32 - d))`.
    4. `resultado = parte_movida | parte_resgatada`.
    
-   **Complexidade:** Tempo `O(1)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `n = 16` (8-bits), `d = 2` | **Saída:** `64`

### 21. Menor de três

-   **Descrição:** Encontre o menor entre três números sem usar `if/else` ou operadores de comparação.
    
-   **Intuição:** Conte "para baixo" simultaneamente até o primeiro alcançar zero.
    
-   **Passo a Passo:**
    1. Use loop enquanto `x && y && z`.
    2. Decremente os três e incremente contador.
    3. Retorne contador quando um zerar.
    
-   **Complexidade:** Tempo `O(min(x,y,z))` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `12, 15, 5` | **Saída:** `5`

### 22. Mínimo sem ramificação

-   **Descrição:** Encontre o mínimo entre dois inteiros sem `if/else`.
    
-   **Intuição:** Use máscara condicional convertendo comparação em 0 ou todos os bits 1s.
    
-   **Passo a Passo:**
    1. `y ^ ((x ^ y) & -(x < y))`.
    
-   **Complexidade:** Tempo `O(1)` sem branch prediction | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `x = 10, y = 15` | **Saída:** `10`

### 23. Menor potência de 2 maior ou igual a n

-   **Descrição:** Encontre a próxima potência de 2 ≥ n.
    
-   **Intuição:** Subtraia 1, preencha com 1s, adicione 1.
    
-   **Passo a Passo:**
    1. `n -= 1`.
    2. Espalhe: `n |= (n >> 1); n |= (n >> 2); n |= (n >> 4); n |= (n >> 8); n |= (n >> 16)`.
    3. `resultado = n + 1`.
    
-   **Complexidade:** Tempo `O(1)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `17` | **Saída:** `32`

### 24. Paridade

-   **Descrição:** Determine se a quantidade de bits `1` é par ou ímpar.
    
-   **Intuição:** Use Brian Kernighan alternando uma flag a cada bit `1` encontrado.
    
-   **Passo a Passo:**
    1. `paridade = 0`.
    2. Enquanto `n > 0`: `paridade ^= 1`, `n &= (n - 1)`.
    
-   **Complexidade:** Tempo `O(K)` onde K = quantidade de bits `1` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `7` (111) | **Saída:** `Ímpar`

### 25. Verificar se binário é palíndromo

-   **Descrição:** Verifique se a representação binária de um unsigned integer é palíndroma.
    
-   **Intuição:** Reconstrua o número invertido e compare.
    
-   **Passo a Passo:**
    1. `temp = n`, `reverso = 0`.
    2. Enquanto `temp > 0`: `reverso = (reverso << 1) | (temp & 1)`, `temp >>= 1`.
    3. Retorne `reverso == n`.
    
-   **Complexidade:** Tempo `O(log n)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `9` (1001) | **Saída:** `Verdadeiro`

### 26. Gerar códigos Gray com n bits

-   **Descrição:** Gere todas as sequências Gray Code onde números sequenciais diferem em apenas 1 bit.
    
-   **Intuição:** Para índice `i`, Gray Code = `i ^ (i >> 1)`.
    
-   **Passo a Passo:**
    1. Loop `i` de 0 a `2^n - 1`.
    2. Compute `gray = i ^ (i >> 1)`.
    3. Adicione à lista.
    
-   **Complexidade:** Tempo `O(2^n)` | Espaço `O(2^n)`
    
-   **Exemplo:** **Entrada:** `n = 2` | **Saída:** `[0, 1, 3, 2]`

### 27. Verificar se é esparso

-   **Descrição:** Classifique um número como "Esparso" se nunca houver dois bits `1` consecutivos.
    
-   **Intuição:** Verifique se `n & (n >> 1) == 0`.
    
-   **Passo a Passo:**
    1. `colisões = n & (n >> 1)`.
    2. Se `colisões == 0`, é esparso.
    
-   **Complexidade:** Tempo `O(1)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `5` (101) | **Saída:** `Verdadeiro`

### 28. MDC Binário (Stein)

-   **Descrição:** Calcule o Máximo Divisor Comum sem usar `%` ou `/`.
    
-   **Intuição:** Simplifique recursivamente: pares sofrem deslocamento, impares sofrem subtração.
    
-   **Passo a Passo:**
    1. Se `a == b`, retorne `a`.
    2. Se ambos pares: `return 2 * GCD(a >> 1, b >> 1)`.
    3. Se um ímpar: `return GCD(a >> 1, b)` (ou `GCD(a, b >> 1)`).
    4. Se ambos ímpares: `return GCD((a - b) >> 1, b)`.
    
-   **Complexidade:** Tempo `O(log(min(a,b)))` | Espaço `O(log(min(a,b)))`
    
-   **Exemplo:** **Entrada:** `14, 21` | **Saída:** `7`

### 29. Quadrado sem `*, /` e `pow()`

-   **Descrição:** Calcule x² usando apenas operações primitivas.
    
-   **Intuição:** Use recursão: x² = 4*(x/2)² se par, ou 4*a² + 4*a + 1 se ímpar (onde a = x >> 1).
    
-   **Passo a Passo:**
    1. `a = x >> 1`.
    2. Se par: `return quadrado(a) << 2`.
    3. Se ímpar: `return (quadrado(a) << 2) + (x << 1) + 1`.
    
-   **Complexidade:** Tempo `O(log n)` | Espaço `O(log n)`
    
-   **Exemplo:** **Entrada:** `5` | **Saída:** `25`

### 30. CRC Cyclic Redundancy Check

-   **Descrição:** Implemente verificação de redundância cíclica sem operações aritméticas.
    
-   **Intuição:** Realize divisão binária (XOR) iterativamente ao longo dos dados.
    
-   **Passo a Passo:**
    1. Concatene dados com zeros (quantidade = comprimento divisor - 1).
    2. Divida sucessivamente usando XOR até restar apenas o CRC.
    
-   **Exemplo:** **Entrada:** Dado: `100100`, Divisor: `1101` | **Saída:** `001`

### 31. Definir bits em um intervalo

-   **Descrição:** Copie bits de um número para outro dentro de um intervalo específico.
    
-   **Passo a Passo:**
    1. Crie máscara: `(((1 << (R - L + 1)) - 1) << (L - 1))`.
    2. Extraia de Y: `y_bits = y & máscara`.
    3. Limpe em X: `x = x & ~máscara`.
    4. Combine: `x = x | y_bits`.
    
-   **Complexidade:** Tempo `O(1)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `x = 10, y = 13, L = 2, R = 3` | **Saída:** `14`

### 32. Verificar se é Bleak

-   **Descrição:** Verifique se existe antecessor tal que `antecessor + popcount(antecessor) == n`.
    
-   **Intuição:** Busque em intervalo limitado de `n - log(n)` a `n - 1`.
    
-   **Passo a Passo:**
    1. Loop `i` de `n - 32` até `n - 1`.
    2. Se `i + popcount(i) == n`, retorne Falso.
    3. Se nenhum match, retorne Verdadeiro (Bleak).
    
-   **Complexidade:** Tempo `O(log n)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `3` | **Saída:** `Bleak`

### 33. Gray para Binário (Conversão)

-   **Descrição:** Decodifique Gray Code para binário.
    
-   **Intuição:** MSB permanece igual; para cada bit seguinte, XOR com o anterior.
    
-   **Passo a Passo:**
    1. `bin = gray`.
    2. Enquanto `gray >>= 1`: `bin ^= gray`.
    
-   **Complexidade:** Tempo `O(log n)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `7` (Gray: 0111) | **Saída:** `5` (Bin: 0101)

</details>

<details>
  <summary>🔴 Nível 3 - Difícil</summary>

### 34. Próximo maior com mesmos bits definidos (Snoob Algorithm)

-   **Descrição:** Encontre o próximo número inteiro que mantenha a mesma quantidade de bits `1`.
    
-   **Passo a Passo:**
    1. `rightOne = n & -n`.
    2. `nextHigherOneBit = n + rightOne`.
    3. `rightOnesPattern = n ^ nextHigherOneBit`.
    4. `rightOnesPattern = (rightOnesPattern / rightOne) >> 2`.
    5. `ans = nextHigherOneBit | rightOnesPattern`.
    
-   **Complexidade:** Tempo `O(1)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `156` | **Saída:** `163`

### 35. Algoritmo de Karatsuba para multiplicação

-   **Descrição:** Multiplique dois números com menor complexidade que O(N²).
    
-   **Intuição:** Divida recursivamente em partes menores.
    
-   **Complexidade:** Tempo `O(N^1.585)` 

-   **Exemplo:** **Entrada:** `10, 12` | **Saída:** `120`

### 36. Máximo XOR de subarray (TRIE)

-   **Descrição:** Encontre o máximo XOR entre pares de subarray.
    
-   **Intuição:** Use árvore TRIE binária com prefixos XOR.
    
-   **Passo a Passo:**
    1. Construa TRIE de 32 bits.
    2. Para cada prefixo, busque o bit inverso na TRIE.
    
-   **Exemplo:** **Entrada:** `[8, 1, 2, 12]` | **Saída:** `15`

### 37. Maior sequência de 1s com uma troca

-   **Descrição:** Encontre a maior sequência contígua de 1s permitindo uma mudança.
    
-   **Passo a Passo:**
    1. Mantenha histórico de sequências separadas por zeros.
    2. Teste preencher um zero permitido.
    3. Retorne máximo encontrado.
    
-   **Exemplo:** **Entrada:** `1775` | **Saída:** `8`

### 38. Menor e maior com mesmos bits definidos

-   **Descrição:** Encontre o número menor e maior mantendo a mesma quantidade de bits `1`.
    
-   **Intuição:** Use Snoob reverso para menor; Snoob normal para maior.
    
-   **Exemplo:** **Entrada:** `5` (101) | **Maior:** `6` (110) | **Menor:** `3` (011)

### 39. Problema do Caixeiro Viajante com Bitmasking

-   **Descrição:** Resolva TSP usando representação binária do conjunto de cidades visitadas.
    
-   **Complexidade:** Tempo `O(N² × 2^N)` | Espaço `O(N × 2^N)`

### 40. Paridade com Table Look-up

-   **Descrição:** Calcule paridade usando tabela pré-computada.
    
-   **Intuição:** Divida número em chunks; XOR suas paridades pré-calculadas.
    
-   **Complexidade:** Tempo `O(1)` com lookup | Espaço `O(256)`

### 41. Criptografia XOR com shift

-   **Descrição:** Cifre/decifre texto usando XOR com deslocamento.
    
-   **Intuição:** XOR é reversível; mesma operação decifra.

### 42. Contar pares com dígito em comum

-   **Descrição:** Conte pares que compartilhem pelo menos um dígito.
    
-   **Intuição:** Use bitmask para representar dígitos presentes.

### 43. Ponto flutuante para binário

-   **Descrição:** Converta número flutuante para representação binária (sinal, expoente, mantissa).
    
-   **Exemplo:** **Entrada:** `5.25` | **Saída:** `0 10000001 01010000000000000000000`

### 44. Algoritmo de multiplicação de Booth

-   **Descrição:** Multiplicação otimizada usando SAR (Shift Arithmetic Right).
    
-   **Exemplo:** **Entrada:** `M = -3, Q = 7` | **Saída:** `-21`

### 45. Pares com concatenação pandigital

-   **Descrição:** Encontre pares cuja concatenação use dígitos 1-9 exatamente uma vez.

### 46. n-ésimo número binário palíndromo

-   **Descrição:** Encontre o n-ésimo número cuja forma binária é palíndroma.
    
-   **Complexidade:** Tempo `O(1)` com fórmula direta
    
-   **Exemplo:** **Entrada:** `9` | **Saída:** `27`

### 47. Dois não repetidos em array de repetidos

-   **Descrição:** Encontre dois números que aparecem uma vez, resto aparece duas vezes.
    
-   **Passo a Passo:**
    1. XOR todos: `xor_total = array[i]^...`.
    2. Isole bit diferente: `bit = xor_total & -xor_total`.
    3. Separe em dois grupos por esse bit.
    4. XOR cada grupo.
    
-   **Complexidade:** Tempo `O(N)` | Espaço `O(1)`
    
-   **Exemplo:** **Entrada:** `[4, 2, 4, 5, 2, 3, 3, 1]` | **Saída:** `[5, 1]`

</details>
