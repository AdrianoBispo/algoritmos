![Algoritmos de Bitwise](../infograficos/Algoritmos%20de%20Bitwise.png)

**Algoritmos bitwise** em Estruturas de Dados e Algoritmos (DSA) envolvem manipular bits individuais das representações binárias de números para executar operações com eficiência. Esses algoritmos utilizam operadores bitwise como AND, OR, XOR, NOT, shift à esquerda e shift à direita.

### O que são algoritmos bitwise?

Algoritmos bitwise são algoritmos que operam em bits individuais dos dados, em vez de tipos maiores, como inteiros ou números de ponto flutuante. Eles manipulam bits diretamente, normalmente usando operadores bitwise como AND, OR, XOR, shift left, shift right e complemento.

### Algoritmos e operações bitwise comuns

A seguir estão alguns algoritmos e operações bitwise comuns:

- **AND bit a bit (&):** recebe dois números como entrada e realiza uma operação AND bit a bit sobre os bits correspondentes. Retorna 1 somente se ambos os bits forem 1; caso contrário, retorna 0.
- **OR bit a bit (|):** realiza uma operação OR bit a bit sobre os bits correspondentes de dois números. Retorna 1 se pelo menos um dos bits for 1.
- **XOR bit a bit (^):** realiza uma operação XOR bit a bit sobre os bits correspondentes de dois números. Retorna 1 se os bits forem diferentes e 0 se forem iguais.
- **NOT bit a bit (~):** realiza uma operação NOT bit a bit, que inverte cada bit da entrada (1 vira 0 e 0 vira 1).
- **Shift à esquerda (<<) e shift à direita (>>):** esses operadores deslocam os bits de um número para a esquerda ou para a direita por uma quantidade específica de posições. O shift à esquerda equivale a multiplicar o número por 2, enquanto o shift à direita equivale a dividir por 2.

### Aplicações de algoritmos bitwise

- **Manipulação de bits (definir, limpar, alternar bits):** operadores bitwise são frequentemente usados para manipular bits individuais de números. Isso inclui tarefas como definir bits (usando OR), limpar bits (usando AND com complemento), alternar bits (usando XOR com 1) e verificar o valor de um bit específico.
- **Armazenamento eficiente de dados:** algoritmos bitwise desempenham papel crucial em técnicas de compressão de dados como o Huffman coding. Eles conseguem representar e processar dados comprimidos com eficiência manipulando bits diretamente.
- **Criptografia:** muitos algoritmos criptográficos, como AES (Advanced Encryption Standard), DES (Data Encryption Standard) e SHA (Secure Hash Algorithm), utilizam operações bitwise para criptografia, descriptografia e hashing. Em particular, o XOR bitwise é muito usado em algoritmos de criptografia por sua simplicidade e eficácia.
- **Rede e tratamento de protocolos:** algoritmos bitwise são usados em protocolos de rede para tarefas como manipulação de endereços IP, mascaramento de sub-rede e análise de pacotes. Por exemplo, o AND bitwise é usado no mascaramento de sub-rede para determinar o endereço de rede a partir de um endereço IP e uma máscara de sub-rede.
- **Programação de sistemas em baixo nível:** operações bitwise são essenciais em programação de sistemas de baixo nível, em tarefas como controle de dispositivos, gerenciamento de memória e operações de E/S em nível de bit. Elas são usadas para manipular registradores de hardware, definir/limpar flags e otimizar código para desempenho.
- **Detecção e correção de erros:** algoritmos bitwise são empregados em técnicas de detecção e correção de erros, como CRC (Cyclic Redundancy Check) e códigos de Hamming. Essas técnicas usam XOR bitwise e outras operações para detectar e corrigir erros nos dados transmitidos.

### **Noções básicas**

- [Introdução aos algoritmos bitwise](https://www.geeksforgeeks.org/dsa/introduction-to-bitwise-algorithms-data-structures-and-algorithms-tutorial/)
- [Operadores bitwise em C/C++](https://www.geeksforgeeks.org/c/bitwise-operators-in-c-cpp/)
- [Operadores bitwise em Java](https://www.geeksforgeeks.org/java/bitwise-operators-in-java/)
- [Operadores bitwise em Python](https://www.geeksforgeeks.org/python/python-bitwise-operators/)
- [Operadores bitwise em JavaScript](https://www.geeksforgeeks.org/javascript/javascript-bitwise-operators/)
- [Tudo sobre manipulação de bits](https://www.geeksforgeeks.org/dsa/all-about-bit-manipulation/)
- [Mistério do endian little e big](https://www.geeksforgeeks.org/dsa/little-and-big-endian-mystery/)

### Dicas e truques de manipulação de bits

- [Manipulação de bits (táticas importantes)](https://www.geeksforgeeks.org/dsa/bits-manipulation-important-tactics/)
- [Hacks bitwise para programação competitiva](https://www.geeksforgeeks.org/competitive-programming/bitwise-hacks-for-competitive-programming/)
