# Algoritmos Bitwise

****Algoritmos bitwise**** em Estruturas de Dados e Algoritmos (DSA) envolvem manipular bits individuais das representações binárias de números para executar operações com eficiência. Esses algoritmos utilizam operadores bitwise como AND, OR, XOR, NOT, shift à esquerda e shift à direita.

### O que são algoritmos bitwise?

Algoritmos bitwise são algoritmos que operam em bits individuais dos dados, em vez de tipos maiores, como inteiros ou números de ponto flutuante. Eles manipulam bits diretamente, normalmente usando operadores bitwise como AND, OR, XOR, shift left, shift right e complemento.

### Algoritmos e operações bitwise comuns

A seguir estão alguns algoritmos e operações bitwise comuns:

-   ****AND bit a bit (&):**** recebe dois números como entrada e realiza uma operação AND bit a bit sobre os bits correspondentes. Retorna 1 somente se ambos os bits forem 1; caso contrário, retorna 0.
-   ****OR bit a bit (|):**** realiza uma operação OR bit a bit sobre os bits correspondentes de dois números. Retorna 1 se pelo menos um dos bits for 1.
-   ****XOR bit a bit (^):**** realiza uma operação XOR bit a bit sobre os bits correspondentes de dois números. Retorna 1 se os bits forem diferentes e 0 se forem iguais.
-   ****NOT bit a bit (~):**** realiza uma operação NOT bit a bit, que inverte cada bit da entrada (1 vira 0 e 0 vira 1).
-   ****Shift à esquerda (<<) e shift à direita (>>):**** esses operadores deslocam os bits de um número para a esquerda ou para a direita por uma quantidade específica de posições. O shift à esquerda equivale a multiplicar o número por 2, enquanto o shift à direita equivale a dividir por 2.

### Aplicações de algoritmos bitwise

-   ****Manipulação de bits (definir, limpar, alternar bits):**** operadores bitwise são frequentemente usados para manipular bits individuais de números. Isso inclui tarefas como definir bits (usando OR), limpar bits (usando AND com complemento), alternar bits (usando XOR com 1) e verificar o valor de um bit específico.
-   ****Armazenamento eficiente de dados:**** algoritmos bitwise desempenham papel crucial em técnicas de compressão de dados como o Huffman coding. Eles conseguem representar e processar dados comprimidos com eficiência manipulando bits diretamente.
-   ****Criptografia:**** muitos algoritmos criptográficos, como AES (Advanced Encryption Standard), DES (Data Encryption Standard) e SHA (Secure Hash Algorithm), utilizam operações bitwise para criptografia, descriptografia e hashing. Em particular, o XOR bitwise é muito usado em algoritmos de criptografia por sua simplicidade e eficácia.
-   ****Rede e tratamento de protocolos:**** algoritmos bitwise são usados em protocolos de rede para tarefas como manipulação de endereços IP, mascaramento de sub-rede e análise de pacotes. Por exemplo, o AND bitwise é usado no mascaramento de sub-rede para determinar o endereço de rede a partir de um endereço IP e uma máscara de sub-rede.
-   ****Programação de sistemas em baixo nível:**** operações bitwise são essenciais em programação de sistemas de baixo nível, em tarefas como controle de dispositivos, gerenciamento de memória e operações de E/S em nível de bit. Elas são usadas para manipular registradores de hardware, definir/limpar flags e otimizar código para desempenho.
-   ****Detecção e correção de erros:**** algoritmos bitwise são empregados em técnicas de detecção e correção de erros, como CRC (Cyclic Redundancy Check) e códigos de Hamming. Essas técnicas usam XOR bitwise e outras operações para detectar e corrigir erros nos dados transmitidos.

### ****Noções básicas****

-   [Introdução aos algoritmos bitwise](https://www.geeksforgeeks.org/dsa/introduction-to-bitwise-algorithms-data-structures-and-algorithms-tutorial/)
-   [Operadores bitwise em C/C++](https://www.geeksforgeeks.org/c/bitwise-operators-in-c-cpp/)
-   [Operadores bitwise em Java](https://www.geeksforgeeks.org/java/bitwise-operators-in-java/)
-   [Operadores bitwise em Python](https://www.geeksforgeeks.org/python/python-bitwise-operators/)
-   [Operadores bitwise em JavaScript](https://www.geeksforgeeks.org/javascript/javascript-bitwise-operators/)
-   [Tudo sobre manipulação de bits](https://www.geeksforgeeks.org/dsa/all-about-bit-manipulation/)
-   [Mistério do endian little e big](https://www.geeksforgeeks.org/dsa/little-and-big-endian-mystery/)

### Dicas e truques de manipulação de bits

-   [Manipulação de bits (táticas importantes)](https://www.geeksforgeeks.org/dsa/bits-manipulation-important-tactics/)
-   [Hacks bitwise para programação competitiva](https://www.geeksforgeeks.org/competitive-programming/bitwise-hacks-for-competitive-programming/)

### ****Problemas fáceis em algoritmos bitwise****

-   [Representação binária](https://www.geeksforgeeks.org/dsa/binary-representation-of-a-given-number/)
-   [Desligar o bit 1 mais à direita](https://www.geeksforgeeks.org/dsa/turn-off-the-rightmost-set-bit/)
-   [Verificar se o k-ésimo bit está definido](https://www.geeksforgeeks.org/dsa/check-whether-k-th-bit-set-not/)
-   [Definir o k-ésimo bit](https://www.geeksforgeeks.org/dsa/set-k-th-bit-given-number/)
-   [Módulo pela potência de 2](https://www.geeksforgeeks.org/dsa/compute-modulus-division-by-a-power-of-2-number/)
-   [Número de ocorrências ímpares](https://www.geeksforgeeks.org/dsa/find-the-number-occurring-odd-number-of-times/)
-   [Potência de dois](https://www.geeksforgeeks.org/dsa/program-to-find-whether-a-given-number-is-power-of-2/)
-   [O único bit definido](https://www.geeksforgeeks.org/dsa/find-position-of-the-only-set-bit/)
-   [Somar strings bit a bit](https://www.geeksforgeeks.org/dsa/add-two-bit-strings/)
-   [Verificar overflow inteiro](https://www.geeksforgeeks.org/dsa/check-for-integer-overflow/)
-   [XOR sem usar XOR](https://www.geeksforgeeks.org/dsa/find-xor-of-two-number-without-using-xor-operator/)
-   [Verificar igualdade](https://www.geeksforgeeks.org/dsa/check-if-two-numbers-are-equal-without-using-arithmetic-and-comparison-operators/)
-   [Verificar sinais opostos](https://www.geeksforgeeks.org/dsa/detect-if-two-integers-have-opposite-signs/)
-   [Trocar dois números](https://www.geeksforgeeks.org/dsa/swap-two-numbers-without-using-temporary-variable/)
-   [Peasant russo](https://www.geeksforgeeks.org/dsa/russian-peasant-multiply-two-numbers-using-bitwise-operators/)

### ****Problemas médios em algoritmos bitwise****

-   [Bit definido mais significativo](https://www.geeksforgeeks.org/dsa/find-significant-set-bit-number/)
-   [Bit definido mais à direita](https://www.geeksforgeeks.org/dsa/position-of-rightmost-set-bit/)
-   [Contar bits definidos](https://www.geeksforgeeks.org/dsa/count-set-bits-in-an-integer/)
-   [Trocar bits](https://www.geeksforgeeks.org/dsa/swap-bits-in-a-given-number/)
-   [Rotacionar bits](https://www.geeksforgeeks.org/dsa/rotate-bits-of-an-integer/)
-   [Menor de três](https://www.geeksforgeeks.org/dsa/smallest-of-three-integers-without-comparison-operators/)
-   [Mínimo sem ramificação](https://www.geeksforgeeks.org/dsa/compute-the-minimum-or-maximum-max-of-two-integers-without-branching/)
-   [Menor potência de 2 maior ou igual a n](https://www.geeksforgeeks.org/dsa/smallest-power-of-2-greater-than-or-equal-to-n/)
-   [Programa para encontrar paridade](https://www.geeksforgeeks.org/dsa/program-to-find-parity/)
-   [Verificar se binário é palíndromo](https://www.geeksforgeeks.org/dsa/check-binary-representation-number-palindrome/)
-   [Gerar códigos Gray com n bits](https://www.geeksforgeeks.org/dsa/generate-n-bit-gray-codes/)
-   [Verificar se é esparso](https://www.geeksforgeeks.org/dsa/check-if-a-given-number-is-sparse-or-not/)
-   [Euclides quando % e / são caros](https://www.geeksforgeeks.org/dsa/euclids-algorithm-when-and-operations-are-costly/)
-   [Quadrado sem usar *, / e pow()](https://www.geeksforgeeks.org/dsa/calculate-square-of-a-number-without-using-and-pow/)
-   [CRC e divisão módulo 2](https://www.geeksforgeeks.org/dsa/modulo-2-binary-division/)
-   [Definir bits em um intervalo](https://www.geeksforgeeks.org/dsa/copy-set-bits-in-a-range/)
-   [Verificar se é bleak](https://www.geeksforgeeks.org/dsa/check-if-a-number-is-bleak/)
-   [Gray para binário e vice-versa](https://www.geeksforgeeks.org/dsa/gray-to-binary-and-binary-to-gray-conversion/)

### ****Problemas difíceis em algoritmos bitwise****

-   [Próximo maior com os mesmos bits definidos](https://www.geeksforgeeks.org/dsa/next-higher-number-with-same-number-of-set-bits/)
-   [Algoritmo de Karatsuba para multiplicação rápida](https://www.geeksforgeeks.org/dsa/karatsuba-algorithm-for-fast-multiplication-using-divide-and-conquer-algorithm/)
-   [Máximo XOR de subarray](https://www.geeksforgeeks.org/dsa/find-the-maximum-subarray-xor-in-a-given-array/)
-   [Maior sequência de 1s em binário com uma troca](https://www.geeksforgeeks.org/dsa/find-longest-sequence-1s-binary-representation-one-flip/)
-   [Menor e maior mais próximos com os mesmos bits definidos](https://www.geeksforgeeks.org/dsa/closest-next-smaller-greater-numbers-number-set-bits/)
-   [Bitmasking e programação dinâmica](https://www.geeksforgeeks.org/dsa/bitmasking-dynamic-programming-set-2-tsp/)
-   [Calcular a paridade](https://www.geeksforgeeks.org/dsa/compute-parity-number-using-xor-table-look/)
-   [Criptografia XOR deslocando o texto simples](https://www.geeksforgeeks.org/dsa/xor-encryption-shifting-plaintext/)
-   [Contar pares com pelo menos um dígito em comum](https://www.geeksforgeeks.org/dsa/count-pairs-array-least-one-digit-common/)
-   [Ponto flutuante para binário](https://www.geeksforgeeks.org/python/python-program-to-convert-floating-to-binary/)
-   [Algoritmo de multiplicação de Booth](https://www.geeksforgeeks.org/dsa/booths-multiplication-algorithm/)
-   [Pares com concatenação pandigital](https://www.geeksforgeeks.org/dsa/number-pairs-pandigital-concatenation/)
-   [n-ésimo número cuja forma binária é um palíndromo](https://www.geeksforgeeks.org/dsa/find-n-th-number-whose-binary-representation-palindrome/)
-   [Dois não repetidos em um array de repetidos](https://www.geeksforgeeks.org/dsa/find-two-non-repeating-elements-in-an-array-of-repeating-elements/)