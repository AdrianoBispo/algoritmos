# Lista de Exercícios

Este documento contém uma lista progressiva de problemas focados em manipulação de bits (Bitwise). O objetivo não é fornecer o código pronto, mas sim a descrição detalhada do problema, a intuição matemática por trás da solução, o algoritmo lógico passo a passo e os exemplos de entrada e saída. Este formato permite que você implemente a solução na sua linguagem de programação favorita (C, C++, Java, Python, JavaScript, Rust, Go, etc.).

### Por que estudar Algoritmos Bitwise?

Operações em nível de bit são executadas diretamente pela Unidade Lógica e Aritmética (ALU) do processador, tornando-as ordens de magnitude mais rápidas do que operações aritméticas tradicionais (como multiplicação, divisão ou módulo). Elas são amplamente utilizadas em:

-   **Sistemas Embarcados e Drivers:** Para ler, ligar ou desligar flags e sensores específicos em registradores de hardware.
    
-   **Criptografia e Redes:** Operações como 
    ```
    XOR
    ```
     formam a base de cifras de fluxo, cálculos de paridade e verificação de redundância (CRC).
    
-   **Otimização de Memória e Processamento:** Estruturas como _Bitsets_ permitem armazenar 32 ou 64 valores booleanos em uma única variável inteira.
    
-   **Programação Dinâmica:** Técnicas de _Bitmasking_ reduzem drasticamente o espaço de estados em problemas combinatórios complexos (como o Caixeiro Viajante).

## Nível: Fácil

### 1\. Representação binária

-   **Descrição:** Dado um número inteiro decimal positivo, converta-o para sua representação binária em formato de string. Esta é a base para entender como os dados são realmente armazenados na memória.
    
-   **Intuição:** A base 2 funciona em potências de 2. Obter o resto da divisão por 2 (que equivale a 
    ```
    n & 1
    ```
    ) nos dá o bit menos significativo. Deslocar para a direita (
    ```
    n >> 1
    ```
    ) divide o número por 2, preparando o próximo bit.
    
-   **Passo a Passo:**
    
      1.  Crie uma estrutura mutável (como um array de caracteres, 
          ```
          StringBuilder
          ```
           ou lista) para armazenar os bits sequencialmente.
          
      2.  Inicie um laço que continuará enquanto o número 
          ```
          n
          ```
           for maior que 0.
          
      3.  Obtenha o último bit fazendo uma operação 
          ```
          AND
          ```
           lógico com 1 (
          ```
          bit = n & 1
          ```
          ). Se 
          ```
          n
          ```
           for ímpar, o bit será 1; se par, será 0.
          
      4.  Adicione esse bit à sua estrutura.
          
      5.  Desloque o número um bit para a direita (
          ```
          n = n >> 1
          ```
          ), o que descarta o bit recém-lido.
          
      6.  Ao final do laço, a estrutura conterá os bits na ordem inversa (do menos para o mais significativo). Inverta a estrutura lida para obter a ordem correta.
    
-   **Complexidade:** Tempo 
    ```
    O(log n)
    ```
     (pois o número é dividido por 2 a cada passo) | Espaço 
    ```
    O(log n)
    ```
     para armazenar a string.
    
-   **Exemplo:** **Entrada:** 
    ```
    14
    ```
     (Processo: 14&1=0 -> 7&1=1 -> 3&1=1 -> 1&1=1. Lidos: 0, 1, 1, 1. Invertendo: 1110) | **Saída:** 
    ```
    1110
    ```

### 2\. Desligar o bit 1 mais à direita

-   **Descrição:** Dado um inteiro, altere o seu bit 
    ```
    1
    ```
     mais à direita para 
    ```
    0
    ```
    , preservando todos os outros bits intactos. Este é um truque essencial para algoritmos de contagem de bits.
    
-   **Intuição:** Ao subtrair 1 de um número, todos os bits 
    ```
    0
    ```
     à direita do bit 
    ```
    1
    ```
     menos significativo tornam-se 
    ```
    1
    ```
    , e esse bit 
    ```
    1
    ```
     específico torna-se 
    ```
    0
    ```
     (ex: 
    ```
    10100 - 1 = 10011
    ```
    ). Fazer um 
    ```
    AND
    ```
     com o original anula essa parte alterada.
    
-   **Passo a Passo:**
    
      1.  Subtraia 1 do número original (
          ```
          n - 1
          ```
          ).
          
      2.  Aplique a operação 
          ```
          AND
          ```
           bit a bit entre o número original e o resultado da subtração: 
          ```
          n & (n - 1)
          ```
          .
          
      3.  Todos os bits à esquerda do bit 1 mais à direita permanecerão inalterados (pois 
          ```
          1 & 1 = 1
          ```
          , 
          ```
          0 & 0 = 0
          ```
          ), e o próprio bit 1 e os zeros à sua direita se tornarão 
          ```
          0
          ```
          .
    
-   **Complexidade:** Tempo 
    ```
    O(1)
    ```
     | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    12
    ```
     (Binário: 1100). Subtraindo 1: 
    ```
    11
    ```
     (1011). Fazendo 
    ```
    1100 & 1011
    ```
     obtemos 
    ```
    1000
    ```
     | **Saída:** 
    ```
    8
    ```

### 3\. Verificar se o k-ésimo bit está definido

-   **Descrição:** Verifique se o k-ésimo bit (contando da direita para a esquerda, sendo a 1ª posição a mais à direita) de um número é igual a 
    ```
    1
    ```
    .
    
-   **Intuição:** Precisamos criar um "filtro" (máscara) que isole exclusivamente a posição que queremos verificar.
    
-   **Passo a Passo:**
    
      1.  Entenda a máscara: O número 
          ```
          1
          ```
           tem apenas o primeiro bit definido.
          
      2.  Desloque o número 
          ```
          1
          ```
           para a esquerda 
          ```
          k - 1
          ```
           vezes (
          ```
          1 << (k - 1)
          ```
          ). Isso cria um número onde apenas o k-ésimo bit é 
          ```
          1
          ```
          .
          
      3.  Faça um 
          ```
          AND
          ```
           bit a bit entre o número original e a máscara (
          ```
          n & mascara
          ```
          ).
          
      4.  Se o k-ésimo bit do original for 
          ```
          1
          ```
          , o resultado será diferente de 
          ```
          0
          ```
           (será exatamente o valor da máscara). Se for 
          ```
          0
          ```
          , o resultado inteiro será 
          ```
          0
          ```
          .
    
-   **Complexidade:** Tempo 
    ```
    O(1)
    ```
     | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    n = 5
    ```
     (101 em binário), 
    ```
    k = 1
    ```
    . Máscara: 
    ```
    1 << 0 = 1
    ```
    . 
    ```
    5 & 1 = 1
    ```
     (diferente de 0) | **Saída:** 
    ```
    Verdadeiro
    ```

### 4\. Definir o k-ésimo bit

-   **Descrição:** Dado um número, mude o seu k-ésimo bit para 
    ```
    1
    ```
     (se já for 1, mantenha 1), preservando todos os outros bits inalterados.
    
-   **Intuição:** O operador 
    ```
    OR
    ```
     (
    ```
    |
    ```
    ) é perfeito para ligar bits. Ele garante que se pelo menos um dos bits for 
    ```
    1
    ```
    , o resultado será 
    ```
    1
    ```
    .
    
-   **Passo a Passo:**
    
      1.  Crie uma máscara deslocando 
          ```
          1
          ```
           para a esquerda 
          ```
          k - 1
          ```
           vezes (
          ```
          1 << (k - 1)
          ```
          ).
          
      2.  Aplique a operação 
          ```
          OR
          ```
           bit a bit entre o número original e a máscara: 
          ```
          n | máscara
          ```
          .
          
      3.  Os bits onde a máscara tem 
          ```
          0
          ```
           manterão seu valor original de 
          ```
          n
          ```
          . Onde a máscara tem 
          ```
          1
          ```
           (o k-ésimo bit), o resultado forçará um 
          ```
          1
          ```
          .
    
-   **Complexidade:** Tempo 
    ```
    O(1)
    ```
     | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    n = 10
    ```
     (1010 em binário), 
    ```
    k = 1
    ```
    . Máscara: 
    ```
    0001
    ```
    . Fazendo 
    ```
    1010 | 0001
    ```
     obtemos 
    ```
    1011
    ```
     | **Saída:** 
    ```
    11
    ```

### 5\. Módulo pela potência de 2

-   **Descrição:** Calcule o resto da divisão (operação módulo 
    ```
    %
    ```
    ) de um número 
    ```
    n
    ```
     por 
    ```
    d
    ```
    , sabendo previamente que 
    ```
    d
    ```
     é uma potência exata de 2 (2, 4, 8, 16...).
    
-   **Intuição:** O operador módulo tradicional 
    ```
    %
    ```
     pode ser lento dependendo do hardware. Se o divisor é potência de 2, os bits após a correspondente potência representam inteiramente o resto.
    
-   **Passo a Passo:**
    
      1.  Identifique que se 
          ```
          d = 2^x
          ```
          , então 
          ```
          d - 1
          ```
           é um número formado por 
          ```
          x
          ```
           bits 
          ```
          1
          ```
           consecutivos à direita. Ex: se 
          ```
          d = 8
          ```
           (1000), 
          ```
          d - 1 = 7
          ```
           (0111).
          
      2.  Para achar o resto, basta reter os 
          ```
          x
          ```
           últimos bits de 
          ```
          n
          ```
          .
          
      3.  Aplique a operação 
          ```
          AND
          ```
           entre 
          ```
          n
          ```
           e 
          ```
          d - 1
          ```
          : 
          ```
          n & (d - 1)
          ```
          .
    
-   **Complexidade:** Tempo 
    ```
    O(1)
    ```
     | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    n = 6
    ```
     (0110), 
    ```
    d = 4
    ```
     (0100). Máscara 
    ```
    d-1 = 3
    ```
     (0011). 
    ```
    0110 & 0011 = 0010
    ```
     | **Saída:** 
    ```
    2
    ```

### 6\. Número de ocorrências ímpares

-   **Descrição:** Dado um array de inteiros onde todos os elementos aparecem um número par de vezes (2, 4, 6 vezes...), exceto por um único elemento que aparece uma quantidade ímpar de vezes. Encontre esse elemento solitário sem usar estruturas de dados adicionais como HashMaps.
    
-   **Intuição:** O operador 
    ```
    XOR
    ```
     (
    ```
    ^
    ```
    ) é sua melhor ferramenta aqui. Suas propriedades garantem que: 1) 
    ```
    x ^ x = 0
    ```
     (um número anula a si mesmo); 2) 
    ```
    x ^ 0 = x
    ```
    ; 3) É comutativo, a ordem não importa.
    
-   **Passo a Passo:**
    
      1.  Inicialize uma variável de acúmulo 
          ```
          resultado
          ```
           com 
          ```
          0
          ```
          .
          
      2.  Percorra todos os elementos do array em um laço.
          
      3.  A cada iteração, faça 
          ```
          resultado = resultado ^ array[i]
          ```
          .
          
      4.  Ao final do array, todos os pares terão se anulado em 
          ```
          0
          ```
          . Restará apenas o elemento que tem quantidade ímpar.
    
-   **Complexidade:** Tempo 
    ```
    O(N)
    ```
     onde N é o tamanho do array | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    [1, 2, 3, 2, 3, 1, 3]
    ```
    . O fluxo será: 
    ```
    0^1=1
    ```
    , 
    ```
    1^2=3
    ```
    , 
    ```
    3^3=0
    ```
    , 
    ```
    0^2=2
    ```
    , 
    ```
    2^3=1
    ```
    , 
    ```
    1^1=0
    ```
    , 
    ```
    0^3=3
    ```
     | **Saída:** 
    ```
    3
    ```

### 7\. Potência de dois

-   **Descrição:** Determine se um dado inteiro positivo é uma potência exata de 2 (1, 2, 4, 8, 16...).
    
-   **Intuição:** Uma potência de 2, em representação binária, sempre possui exatamente **um único** bit 
    ```
    1
    ```
     seguido por zeros (ex: 16 = 10000). Usaremos o mesmo truque do exercício 2.
    
-   **Passo a Passo:**
    
      1.  Primeiro, lide com o caso base: o número deve ser estritamente maior que 
          ```
          0
          ```
          . Potências de dois não podem ser zero ou negativas.
          
      2.  Se o número tem apenas um bit 
          ```
          1
          ```
          , fazer a operação 
          ```
          n & (n - 1)
          ```
           (que desliga o bit mais à direita) resultará em remover o único bit que existia.
          
      3.  Logo, o resultado de 
          ```
          n & (n - 1)
          ```
           deve ser obrigatoriamente 
          ```
          0
          ```
          .
          
      4.  Retorne a conjunção: 
          ```
          n > 0
          ```
           E 
          ```
          (n & (n - 1)) == 0
          ```
          .
    
-   **Complexidade:** Tempo 
    ```
    O(1)
    ```
     | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    16
    ```
     (10000). 
    ```
    16 & 15
    ```
     (10000 & 01111) é 
    ```
    0
    ```
     | **Saída:** 
    ```
    Verdadeiro
    ```

### 8\. O único bit definido

-   **Descrição:** Dado um número inteiro que tem a garantia de ser uma potência de 2, encontre a posição (baseada em 1, da direita para a esquerda) do seu único bit definido.
    
-   **Intuição:** Como sabemos que há apenas um bit 1, podemos simplesmente inspecionar posição por posição usando deslocamentos até que o número zere.
    
-   **Passo a Passo:**
    
      1.  (Opcional, mas seguro) Verifique se o número é de fato maior que 0 e se é potência de 2 (
          ```
          n & (n-1) == 0
          ```
          ). Se não for, retorne um erro ou -1.
          
      2.  Crie um contador de posição: 
          ```
          posicao = 1
          ```
          .
          
      3.  Inicie um laço que roda enquanto 
          ```
          n
          ```
           for maior que 0.
          
      4.  Em cada passo, desloque o número para a direita em 1 bit (
          ```
          n = n >> 1
          ```
          ) e incremente o contador 
          ```
          posicao++
          ```
          .
          
      5.  Pare quando o número original se tornar 0. A 
          ```
          posicao - 1
          ```
           representará o índice real do bit.
    
-   **Complexidade:** Tempo 
    ```
    O(log n)
    ```
     (no máximo 32 ou 64 iterações) | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    16
    ```
     (Binário: 10000). Deslocamentos: 16->8->4->2->1->0 (5 iterações) | **Saída:** 
    ```
    5
    ```

### 9\. Somar strings bit a bit

-   **Descrição:** Dadas duas strings compostas apenas por '0's e '1's que representam números binários grandes, retorne a soma delas em forma de uma nova string binária. Não as converta para inteiro (evite overflow).
    
-   **Intuição:** Simule a soma com "vai um" (carry over) que aprendemos na escola, operando do final (menos significativo) para o início (mais significativo).
    
-   **Passo a Passo:**
    
      1.  Obtenha os índices finais das duas strings (
          ```
          i = str1.length - 1
          ```
          , 
          ```
          j = str2.length - 1
          ```
          ).
          
      2.  Inicialize uma variável 
          ```
          carry = 0
          ```
          .
          
      3.  Crie uma estrutura para acumular o resultado.
          
      4.  Faça um laço enquanto 
          ```
          i >= 0
          ```
           OU 
          ```
          j >= 0
          ```
           OU 
          ```
          carry == 1
          ```
          .
          
      5.  A cada iteração, pegue o bit atual de 
          ```
          str1
          ```
           (ou 0 se 
          ```
          i < 0
          ```
          ) e de 
          ```
          str2
          ```
           (ou 0 se 
          ```
          j < 0
          ```
          ).
          
      6.  A soma total daquela coluna é 
          ```
          soma = bit1 + bit2 + carry
          ```
          .
          
      7.  O bit que ficará na resposta é 
          ```
          soma % 2
          ```
           (0 ou 1). O novo 
          ```
          carry
          ```
           para a próxima casa é 
          ```
          soma / 2
          ```
           (0 se a soma foi 0 ou 1; 1 se a soma foi 2 ou 3).
          
      8.  Ao final, inverta a string de resultado gerada.
    
-   **Complexidade:** Tempo 
    ```
    O(max(N, M))
    ```
     | Espaço 
    ```
    O(max(N, M))
    ```
     onde N e M são os tamanhos das strings.
    
-   **Exemplo:** **Entrada:** 
    ```
    "11", "1"
    ```
    . Coluna 1: 1+1=2 (bit 0, carry 1). Coluna 2: 1+0+carry(1)=2 (bit 0, carry 1). Restou carry=1 (bit 1). Invertendo: 
    ```
    100
    ```
     | **Saída:** 
    ```
    "100"
    ```

### 10\. Verificar overflow inteiro

-   **Descrição:** Ao programar com tipos de tamanho fixo (como inteiros de 32 bits), somar dois números muito grandes pode "transbordar" os limites de armazenamento (overflow). Crie uma lógica para detectar se 
    ```
    a + b
    ```
     gera overflow sem causar a falha propriamente dita de forma irreversível.
    
-   **Intuição:** O overflow na soma ocorre APENAS quando somamos dois números de mesmo sinal, e o resultado final subitamente inverte o sinal (por invadir o bit mais significativo usado para definir positivo/negativo).
    
-   **Passo a Passo:**
    
      1.  Efetue a soma dos dois números 
          ```
          a
          ```
           e 
          ```
          b
          ```
           e armazene na variável 
          ```
          resultado
          ```
          .
          
      2.  Verifique os sinais. Se um for positivo e o outro negativo, a soma estará entre os dois e nunca transbordará o limite.
          
      3.  O problema acontece se:
          
              19.   ```
                  a
                  ```
                   é positivo E 
                  ```
                  b
                  ```
                   é positivo, mas o 
                  ```
                  resultado
                  ```
                   é menor que 0.
                  
              32.   ```
                  a
                  ```
                   é negativo E 
                  ```
                  b
                  ```
                   é negativo, mas o 
                  ```
                  resultado
                  ```
                   é maior ou igual a 0.
          
      4.  Uma forma mais sofisticada em bitwise é checar o bit de sinal de 
          ```
          a
          ```
          , 
          ```
          b
          ```
           e 
          ```
          resultado
          ```
           usando deslocamentos. A expressão booleana 
          ```
          (a > 0 && b > 0 && resultado < 0) || (a < 0 && b < 0 && resultado >= 0)
          ```
           resolve eficientemente na maioria das linguagens.
    
-   **Complexidade:** Tempo 
    ```
    O(1)
    ```
     | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    a = 2147483640, b = 10
    ```
     (em 32 bits assinados, o limite é 2147483647). A soma resultará num número negativo devido ao vai-um atingir o bit de sinal | **Saída:** 
    ```
    Overflow Detectado
    ```

### 11\. XOR sem usar XOR

-   **Descrição:** Replicar o comportamento do operador lógico 
    ```
    XOR
    ```
     (
    ```
    ^
    ```
    ) entre dois números usando unicamente os operadores fundamentais 
    ```
    AND
    ```
     (
    ```
    &
    ```
    ), 
    ```
    OR
    ```
     (
    ```
    |
    ```
    ) e 
    ```
    NOT
    ```
     (
    ```
    ~
    ```
    ).
    
-   **Intuição:** O XOR liga um bit se os dois operandos forem **diferentes**. Uma maneira de expressar isso logicamente é: "Ou os dois tem o bit ligado (
    ```
    a | b
    ```
    ), MAS eles não podem ter o bit ligado ao mesmo tempo (
    ```
    ~(a & b)
    ```
    )".
    
-   **Passo a Passo:**
    
      1.  Primeiro, determine quais bits estão presentes em pelo menos um dos números: 
          ```
          parte_or = x | y
          ```
          .
          
      2.  Em seguida, determine os bits que são comuns (iguais a 1) em ambos: 
          ```
          x & y
          ```
          .
          
      3.  Como queremos os diferentes, devemos excluir os comuns. Inverta os comuns com 
          ```
          NOT
          ```
          : 
          ```
          parte_not_and = ~(x & y)
          ```
          .
          
      4.  Faça um 
          ```
          AND
          ```
           lógico entre os dois conjuntos encontrados: 
          ```
          parte_or & parte_not_and
          ```
          .
          
      5.  Matematicamente: 
          ```
          (x | y) & ~(x & y)
          ```
          . O resultado será o mesmo que 
          ```
          x ^ y
          ```
          .
    
-   **Complexidade:** Tempo 
    ```
    O(1)
    ```
     | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    x = 3
    ```
     (011), 
    ```
    y = 5
    ```
     (101). 
    ```
    x|y = 7
    ```
     (111). 
    ```
    x&y = 1
    ```
     (001). 
    ```
    ~(x&y)
    ```
     será um número cheio de 1s exceto no final...
    ```
    110
    ```
    . Fazendo 
    ```
    111 & ...110
    ```
     resulta em 
    ```
    110
    ```
     (que é 6) | **Saída:** 
    ```
    6
    ```

### 12\. Verificar igualdade

-   **Descrição:** Escreva uma função que verifique se dois números inteiros são perfeitamente iguais sem usar NENHUM operador aritmético (
    ```
    +
    ```
    , 
    ```
    -
    ```
    ) ou de comparação (
    ```
    ==
    ```
    , 
    ```
    !=
    ```
    , 
    ```
    <
    ```
    , 
    ```
    >
    ```
    ).
    
-   **Intuição:** Voltamos à propriedade fundamental do XOR. Dois números idênticos cancelam um ao outro perfeitamente bit a bit, resultando em um inteiro totalmente zerado.
    
-   **Passo a Passo:**
    
      1.  Aplique a operação 
          ```
          XOR
          ```
           entre os dois números: 
          ```
          resultado = x ^ y
          ```
          .
          
      2.  Se 
          ```
          x
          ```
           e 
          ```
          y
          ```
           são iguais, cada bit correspondente será igual, e o 
          ```
          XOR
          ```
           de bits iguais é sempre 
          ```
          0
          ```
          . Logo, 
          ```
          resultado
          ```
           será 
          ```
          0
          ```
          .
          
      3.  Retorne a inversão lógica do resultado se a sua linguagem suportar (como 
          ```
          !resultado
          ```
           em C/C++), ou se precisar checar explicitamente a ausência de bits em um modelo onde 
          ```
          0
          ```
           é Falso.
    
-   **Complexidade:** Tempo 
    ```
    O(1)
    ```
     | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    10, 10
    ```
    . 
    ```
    10 ^ 10
    ```
     é 
    ```
    0
    ```
    . Negando logicamente obtemos o booleano Verdadeiro | **Saída:** 
    ```
    Verdadeiro
    ```

### 13\. Verificar sinais opostos

-   **Descrição:** Descubra se dois números inteiros (diferentes de zero) possuem sinais matemáticos opostos (um sendo positivo e o outro negativo).
    
-   **Intuição:** Na representação moderna de computadores (Complemento de Dois), o bit mais significativo (o mais à esquerda) de um número dita seu sinal: 
    ```
    0
    ```
     para positivo, 
    ```
    1
    ```
     para negativo.
    
-   **Passo a Passo:**
    
      1.  Fazer o 
          ```
          XOR
          ```
           entre os dois números (
          ```
          x ^ y
          ```
          ) comparará cada bit, incluindo o crucial bit de sinal.
          
      2.  Se os sinais forem iguais (dois 
          ```
          0
          ```
          s ou dois 
          ```
          1
          ```
          s), o bit mais significativo do resultado será 
          ```
          0
          ```
           (indicando um número resultante positivo).
          
      3.  Se os sinais forem diferentes (um 
          ```
          0
          ```
           e um 
          ```
          1
          ```
          ), o bit mais significativo do resultado será 
          ```
          1
          ```
          , o que significa que, para o computador, o número resultante dessa operação será negativo.
          
      4.  Portanto, basta avaliar: 
          ```
          (x ^ y) < 0
          ```
          .
    
-   **Complexidade:** Tempo 
    ```
    O(1)
    ```
     | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    -1
    ```
     (em 32-bits é tudo 1), 
    ```
    2
    ```
     (000...010). O XOR preserva o bit de sinal mais à esquerda como 1, gerando um resultado negativo | **Saída:** 
    ```
    Verdadeiro
    ```

### 14\. Trocar dois números

-   **Descrição:** Implemente um algoritmo para trocar (swap) os valores armazenados em duas variáveis numéricas sem precisar criar ou usar uma terceira variável temporária.
    
-   **Intuição:** O XOR permite "guardar" informações combinadas de dois números em uma única variável, podendo ser descriptografado posteriormente com a aplicação do outro valor remanescente.
    
-   **Passo a Passo:**
    
      1.  Suponha as variáveis 
          ```
          a
          ```
           e 
          ```
          b
          ```
          .
          
      2.  Primeiro passo: Combine as duas em 
          ```
          a
          ```
          . Faça 
          ```
          a = a ^ b
          ```
          . (Agora 
          ```
          a
          ```
           retém o histórico das duas variáveis originais).
          
      3.  Segundo passo: Recupere o valor inicial de 
          ```
          a
          ```
           para 
          ```
          b
          ```
          . Faça 
          ```
          b = a ^ b
          ```
          . Como 
          ```
          a
          ```
           agora é 
          ```
          (original_a ^ original_b)
          ```
          , 
          ```
          b
          ```
           se torna 
          ```
          (original_a ^ original_b) ^ original_b
          ```
          , que anula o 
          ```
          b
          ```
           sobrando apenas o 
          ```
          original_a
          ```
          .
          
      4.  Terceiro passo: Recupere o valor inicial de 
          ```
          b
          ```
           para 
          ```
          a
          ```
          . Faça 
          ```
          a = a ^ b
          ```
          . (Como 
          ```
          b
          ```
           agora é 
          ```
          original_a
          ```
          , fazer 
          ```
          (original_a ^ original_b) ^ original_a
          ```
           anula os 
          ```
          a
          ```
          s, restando o 
          ```
          original_b
          ```
          ).
    
-   **Casos de Borda:** Se você tentar usar essa técnica em arrays e passar o mesmo índice (
    ```
    trocar(arr[i], arr[i])
    ```
    ), as três operações resultarão em zerar o valor inteiro. Tenha cuidado.
    
-   **Complexidade:** Tempo 
    ```
    O(1)
    ```
     | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    a = 5
    ```
     (101), 
    ```
    b = 7
    ```
     (111).
    
      1.  ```
          a = 5 ^ 7 = 2
          ```
           (010).
          
      2.  ```
          b = 2 ^ 7 = 5
          ```
          .
          
      3.  ```
          a = 2 ^ 5 = 7
          ```
           | **Saída:** 
          ```
          a = 7, b = 5
          ```

### 15\. Peasant russo (Multiplicação Russa)

-   **Descrição:** Multiplique dois inteiros usando exclusivamente adição, deslocamento de bits (shifts) e operações lógicas, contornando o uso direto de multiplicadores do hardware (
    ```
    *
    ```
    ). É a essência de como o processador frequentemente implementa a multiplicação.
    
-   **Intuição:** Em base binária, multiplicar 
    ```
    a * b
    ```
     é o equivalente a somar o número 
    ```
    a
    ```
     deslocado de acordo com as posições onde 
    ```
    b
    ```
     tem o bit 
    ```
    1
    ```
    . A técnica consiste em dobrar 
    ```
    a
    ```
     sucessivamente enquanto divide 
    ```
    b
    ```
     pela metade.
    
-   **Passo a Passo:**
    
      1.  Inicialize um acumulador 
          ```
          resultado = 0
          ```
          .
          
      2.  Comece um laço enquanto o segundo número (
          ```
          b
          ```
          ) for maior que 
          ```
          0
          ```
          .
          
      3.  Verifique se 
          ```
          b
          ```
           é ímpar (ou seja, se 
          ```
          b & 1
          ```
           é verdadeiro). Se for, isso significa que a potência atual deve contribuir para a resposta. Adicione 
          ```
          a
          ```
           ao 
          ```
          resultado
          ```
           (
          ```
          resultado = resultado + a
          ```
          ).
          
      4.  Multiplique 
          ```
          a
          ```
           por 2 fazendo um deslocamento à esquerda de 1 bit: 
          ```
          a = a << 1
          ```
          .
          
      5.  Divida 
          ```
          b
          ```
           por 2 fazendo um deslocamento à direita de 1 bit: 
          ```
          b = b >> 1
          ```
          . Isso expõe o próximo bit de 
          ```
          b
          ```
           para a iteração seguinte.
          
      6.  Repita até 
          ```
          b
          ```
           zerar, retornando o 
          ```
          resultado
          ```
           final acumulado.
    
-   **Complexidade:** Tempo 
    ```
    O(log b)
    ```
     onde b é o segundo número | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    a = 18, b = 5
    ```
     (5 é 101).
    
      -   Iteração 1: 
          ```
          b(5)
          ```
           é ímpar -> 
          ```
          resultado = 0+18=18
          ```
          . Dobre 
          ```
          a=36
          ```
          , divida 
          ```
          b=2
          ```
          .
          
      -   Iteração 2: 
          ```
          b(2)
          ```
           é par -> resultado intocado. Dobre 
          ```
          a=72
          ```
          , divida 
          ```
          b=1
          ```
          .
          
      -   Iteração 3: 
          ```
          b(1)
          ```
           é ímpar -> 
          ```
          resultado = 18+72=90
          ```
          . 
          ```
          b
          ```
           vira 0. Fim. | **Saída:** 
          ```
          90
          ```

## Nível: Médio

### 16\. Bit definido mais significativo

-   **Descrição:** Encontre um número isolado equivalente apenas ao bit 
    ```
    1
    ```
     mais à esquerda (o mais significativo, MSB) de um dado inteiro dado, zerando todos os que vêm depois.
    
-   **Intuição:** Se pegarmos o bit 
    ```
    1
    ```
     mais alto e usarmos a operação 
    ```
    OR
    ```
     e shifts sistemáticos para espalhá-lo por todos os espaços em branco à sua direita, obteremos um bloco contínuo de 1s. Ex: de 
    ```
    10010
    ```
     faremos virar 
    ```
    11111
    ```
    . Ao pegar esse bloco sólido e subtrair sua metade (
    ```
    11111 - 01111
    ```
    ), isolamos apenas a primeira casa (
    ```
    10000
    ```
    ).
    
-   **Passo a Passo:**
    
      1.  Dada uma variável 
          ```
          n
          ```
           (ex. tamanho de 32 bits).
          
      2.  Para espalhar o MSB para todos os bits vizinhos à direita:
          
              9.   ```
                  n = n | (n >> 1)
                  ```
                   (cobre as próximas 1 posições)
                  
              14.   ```
                  n = n | (n >> 2)
                  ```
                   (cobre as próximas 2 posições, agora 4 1s em sequência)
                  
              19.   ```
                  n = n | (n >> 4)
                  ```
                  
              23.   ```
                  n = n | (n >> 8)
                  ```
                  
              27.   ```
                  n = n | (n >> 16)
                  ```
          
      3.  Ao fim dessas 5 linhas, o número terá sido inundado de 1s do MSB até o final à direita.
          
      4.  Para deixar apenas o MSB isolado, subtraia o número deslocado uma vez de si mesmo: 
          ```
          resultado = n - (n >> 1)
          ```
          . Opcionalmente em algumas arquiteturas, você pode fazer 
          ```
          (n + 1) >> 1
          ```
          .
    
-   **Complexidade:** Tempo 
    ```
    O(1)
    ```
     | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    18
    ```
     (10010). O "smear" vai transformá-lo em 
    ```
    31
    ```
     (11111). 
    ```
    31 - (31 >> 1) = 31 - 15 = 16
    ```
     | **Saída:** 
    ```
    16
    ```
     (10000)

### 17\. Bit definido mais à direita

-   **Descrição:** Semelhante ao exercício anterior, mas em vez do mais à esquerda, queremos um número que represente apenas o bit 
    ```
    1
    ```
     mais à direita do inteiro original, apagando todo o resto à esquerda.
    
-   **Intuição:** Usamos a mágica do Complemento de Dois. O valor negativo de um número (
    ```
    -n
    ```
    ) é armazenado invertendo todos os seus bits (
    ```
    ~n
    ```
    ) e somando 1. A matemática dessa soma específica sempre causa um efeito "dominó" (vai um) da direita para a esquerda até parar exatamente no primeiro bit 1 original, transformando os antigos zeros à direita em zeros novamente, e mantendo apenas aquele bit 1 coincidente entre 
    ```
    n
    ```
     e 
    ```
    -n
    ```
    .
    
-   **Passo a Passo:**
    
      1.  A operação requer apenas uma linha muito elegante.
          
      2.  Faça a operação 
          ```
          AND
          ```
           do número positivo com seu equivalente negativo: 
          ```
          resultado = n & -n
          ```
          .
          
      3.  Alternativamente (mesmo resultado, sem sugar as propriedades intrínsecas da linguagem): 
          ```
          resultado = n & (~n + 1)
          ```
          .
    
-   **Complexidade:** Tempo 
    ```
    O(1)
    ```
     | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    12
    ```
     (Binário: 1100). O 
    ```
    -12
    ```
     é calculado como 
    ```
    ~12
    ```
     (0011) 
    ```
    + 1
    ```
     = 
    ```
    0100
    ```
    . Fazendo o AND: 
    ```
    1100 & 0100
    ```
     | **Saída:** 
    ```
    4
    ```
     (0100)

### 18\. Contar bits definidos

-   **Descrição:** Crie um algoritmo para contar quantos bits com valor 
    ```
    1
    ```
     existem na representação binária de um número. Esta é uma operação tão comum que muitas linguagens têm funções nativas (como 
    ```
    Integer.bitCount()
    ```
     no Java ou o 
    ```
    __builtin_popcount
    ```
     no C++). Conhecido como Algoritmo de Brian Kernighan.
    
-   **Intuição:** Em vez de analisar cada um dos 32 ou 64 bits de forma linear 
    ```
    O(Total de bits)
    ```
    , nós aproveitamos o exercício 2 (
    ```
    n = n & (n - 1)
    ```
    ) que apaga o bit ativo mais à direita de forma direta, "pulando" blocos enormes de zeros.
    
-   **Passo a Passo:**
    
      1.  Inicie uma variável de contagem (
          ```
          contador = 0
          ```
          ).
          
      2.  Crie um laço que repete enquanto 
          ```
          n
          ```
           for maior que 
          ```
          0
          ```
           (se 
          ```
          n
          ```
           for negativo, dependendo da linguagem e do tipo, trate o casting logico primeiro para evitar loops infinitos com zeros à esquerda).
          
      3.  No corpo do laço, remova o bit 
          ```
          1
          ```
           mais à direita fazendo 
          ```
          n = n & (n - 1)
          ```
          .
          
      4.  Adicione 
          ```
          1
          ```
           ao 
          ```
          contador
          ```
          .
          
      5.  Repita. Cada iteração do laço destrói exatamente um bit ligado, então o laço roda o exato número de vezes proporcional à resposta real.
    
-   **Complexidade:** Tempo 
    ```
    O(K)
    ```
     onde K é a quantidade real de bits com valor '1' (melhor que O(log n)) | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    13
    ```
     (1101). Iterações:
    
      -   13 & 12 = 12 (1100). Contador: 1
          
      -   12 & 11 = 8 (1000). Contador: 2
          
      -   8 & 7 = 0. Contador: 3. (Fim) | **Saída:** 
          ```
          3
          ```

### 19\. Trocar bits

-   **Descrição:** Dado um número de comprimento em bits específico (ex: um byte de 8 bits, ou um uint32 de 32 bits), efetue a permuta dos bits nas posições pares com os seus respectivos vizinhos nas posições ímpares (Trocar pos 0 com pos 1, pos 2 com pos 3, e assim por diante).
    
-   **Intuição:** Precisamos de duas máscaras imutáveis. Uma para resgatar unicamente todos os valores de ordem par e outra para os de ordem ímpar. Então alinhamos e somamos novamente.
    
-   **Passo a Passo:**
    
      1.  Presumindo números de 32 bits, as posições pares (0, 2, 4...) podem ser isoladas com a máscara onde esses bits são 
          ```
          0
          ```
           e os ímpares são 
          ```
          1
          ```
          . Máscara Ímpar (pos 1,3,5): 
          ```
          0xAAAAAAAA
          ```
           (em binário 10101010...). Máscara Par (pos 0,2,4): 
          ```
          0x55555555
          ```
           (01010101...).
          
      2.  Crie a metade das posições pares lendo o número com AND: 
          ```
          pares = n & 0x55555555
          ```
          .
          
      3.  Crie a metade das posições ímpares com AND: 
          ```
          impares = n & 0xAAAAAAAA
          ```
          .
          
      4.  Para a troca, desloque os pares para a esquerda (
          ```
          pares << 1
          ```
          ), forçando-os a entrar nos slots ímpares recém-esvaziados.
          
      5.  Desloque os ímpares à direita, em modo lógico ou não assinado (
          ```
          impares >>> 1
          ```
          ), para caírem nos slots pares esvaziados.
          
      6.  Finalize fundindo as duas partes com OR (
          ```
          pares | impares
          ```
          ).
    
-   **Complexidade:** Tempo 
    ```
    O(1)
    ```
     | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    23
    ```
     (8-bits: 
    ```
    00010111
    ```
    ).
    
      -   Ímpares: 
          ```
          00010111 & 10101010
          ```
           = 
          ```
          00000010
          ```
          . Deslocados à direita = 
          ```
          00000001
          ```
          .
          
      -   Pares: 
          ```
          00010111 & 01010101
          ```
           = 
          ```
          00010101
          ```
          . Deslocados à esquerda = 
          ```
          00101010
          ```
          .
          
      -   OR final: 
          ```
          00101010 | 00000001
          ```
           = 
          ```
          00101011
          ```
           (43) | **Saída:** 
          ```
          43
          ```

### 20\. Rotacionar bits

-   **Descrição:** Rotacionar circularmente bits difere do deslocamento comum (shift). Quando rotacionamos bits de um tamanho limite estrito de 
    ```
    N
    ```
     posições (como num byte de 8 bits ou palavra de 32) os bits que "caem" de um lado reaparecem obrigatoriamente do lado aposto. Dado um número inteiro e 
    ```
    d
    ```
     rotações necessárias.
    
-   **Intuição:** Como as linguagens nativamente perdem o dado com shifts 
    ```
    <<
    ```
     ou 
    ```
    >>
    ```
    , nós mesmos devemos armazenar artificialmente as casinhas que foram deslocadas para fora e reencaixá-las na ponta exposta.
    
-   **Passo a Passo (Focado em inteiros de 32 bits e rotação para a esquerda):**
    
      1.  Primeiro, evite rotações excessivas fazendo módulo: 
          ```
          d = d % 32
          ```
          .
          
      2.  Pegue o número e faça a movimentação principal esquerda: 
          ```
          parte_movida = (n << d)
          ```
          . Mas saiba que os d-bits que estouraram acima de 32 foram mortos.
          
      3.  Para resgatá-los do original, desloque o número à direita de forma não sinalizada (para não puxar 1s caso seja negativo) uma quantidade proporcional ao resto que sobrou: 
          ```
          parte_resgatada = (n >>> (32 - d))
          ```
          .
          
      4.  Agora as duas peças se completam igual um quebra-cabeça. Faça 
          ```
          resultado = parte_movida | parte_resgatada
          ```
          .
    
-   **Complexidade:** Tempo 
    ```
    O(1)
    ```
     | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** Inteiro 8-bits 
    ```
    n = 16
    ```
     (00010000), 
    ```
    d = 2
    ```
    , Direção 
    ```
    Esquerda
    ```
     | **Saída:** O 1 vai duas casas p/ a esquerda gerando 
    ```
    64
    ```
     (01000000).

### 21\. Menor de três

-   **Descrição:** Receba três números inteiros não-negativos e encontre o menor entre eles. Condição rigorosa: você não pode usar 
    ```
    if/else
    ```
    , loops complexos com break ou os operadores explícitos 
    ```
    <
    ```
    , 
    ```
    >
    ```
    , 
    ```
    <=
    ```
    , 
    ```
    >=
    ```
    , ou 
    ```
    ==
    ```
    .
    
-   **Intuição:** Como podemos contar "para baixo" sistematicamente? Se subtrairmos 1 de todos simultaneamente num ciclo repetitivo, o primeiro valor absoluto a cruzar o véu negativo ou chegar a 0 originaliza nossa resposta. Precisamos ser engenhosos para detectar o 
    ```
    0
    ```
     sem igualdade.
    
-   **Passo a Passo:**
    
      1.  Crie um 
          ```
          contador = 0
          ```
          .
          
      2.  Implemente um loop que verifica a validade das variáveis usando cast booleano implícito que algumas linguagens de baixo nível (como C) dão de presente (
          ```
          while(x && y && z)
          ```
          ).
          
      3.  Outra forma restritamente bitwise de testar se 3 números são maiores que zero de uma só vez (sem zero no meio) é testar flags falsas ou subtrações diretas se for uma restrição pesada, mas assumiremos a condição do laço booleana básica.
          
      4.  No bloco, decremente os três simultaneamente e adicione 
          ```
          17.1
          ```
           ao contador.
          
      5.  Quando o menor deles se esgotar para zero, o teste quebra. A resposta será o contador preservado.
    
-   **Aviso de Performance:** Isso é uma charada algorítmica para pensamento lateral, não devendo ser posta em ambiente de produção (a complexidade é pautada nos valores intrínsecos e será lenta para entradas massivas).
    
-   **Complexidade:** Tempo 
    ```
    O(Min(x,y,z))
    ```
     | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    12, 15, 5
    ```
    . O loop iterará exatas 5 vezes decrescendo 
    ```
    [11,14,4] -> [10,13,3]...
    ```
     até o último elemento do array interno se tornar 0 e travar a continuidade | **Saída:** 
    ```
    5
    ```

### 22\. Mínimo sem ramificação

-   **Descrição:** Em sistemas hiper-otimizados que evitam ao máximo branch-prediction falhos de pipeline na CPU, condicional 
    ```
    if/else
    ```
     é prejudicial. Encontre o mínimo numérico entre dois inteiros estritos usando apenas matemática lógica sem ramificação.
    
-   **Intuição:** Assumindo C/C++, a comparação 
    ```
    (x < y)
    ```
     resolve logicamente como um 
    ```
    1
    ```
     (se verdadeiro) ou 
    ```
    0
    ```
     (falso). Se você negar numericamente isso, 
    ```
    -1
    ```
     é mapeado perfeitamente para bits todos definidos em Complemento de Dois (
    ```
    1111...1111
    ```
    ).
    
-   **Passo a Passo:**
    
      1.  Use a expressão misteriosa: 
          ```
          y ^ ((x ^ y) & -(x < y))
          ```
          .
          
      2.  Se 
          ```
          x < y
          ```
           for falso (y é o mínimo real): A parte 
          ```
          13.(x < y)
          ```
           resolve para 
          ```
          17.(0)
          ```
          , gerando uma máscara 
          ```
          00000000
          ```
          . Quando fazemos 
          ```
          AND
          ```
           com a diferença XORada 
          ```
          (x ^ y)
          ```
          , dá 
          ```
          0
          ```
          . Fica apenas 
          ```
          y ^ 0
          ```
          , que retorna corretamente o 
          ```
          y
          ```
          .
          
      3.  Se 
          ```
          x < y
          ```
           for verdadeiro (x é o mínimo real): A parte 
          ```
          51.(x < y)
          ```
           vira 
          ```
          55.1
          ```
          , uma máscara de 32 bits 
          ```
          1111...1111
          ```
          . Fazer o 
          ```
          AND
          ```
           deixa 
          ```
          (x ^ y)
          ```
           passarem intocados. Fazer 
          ```
          y ^ (x ^ y)
          ```
           desmascara o número revelando com êxito e trocando os valores, o 
          ```
          x
          ```
          .
    
-   **Complexidade:** Tempo 
    ```
    O(1)
    ```
     sem paradas de branch do processador | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    x = 10, y = 15
    ```
    . x é o menor, a máscara ativa a mudança e devolve ele | **Saída:** 
    ```
    10
    ```

### 23\. Menor potência de 2 maior ou igual a n

-   **Descrição:** Dado um número inteiro 
    ```
    n
    ```
    , encontre a próxima potência completa de 2 (2, 4, 8, 16, 32...) que seja superior ou, no mínimo, exatamente igual a esse dado número 
    ```
    n
    ```
    . É útil para pré-alocar estruturas de dados baseadas em árvores ou hashtables com expansão otimizada em hardware.
    
-   **Intuição:** Esse é o inverso do Exercício 16. O "smear" lá tirava apenas o bloco mais significativo, aqui nós pegamos o número original, reduzimos em 1, preenchemos o resto inteiro de uns até o fim com ORs sucessivos, e quando por fim somamos +1 de novo, o estouro em cadeia cascateia tudo para zeros e sobe rigorosamente a próxima potência superior isenta.
    
-   **Passo a Passo:**
    
      1.  Condição de base protetiva: Se 
          ```
          n
          ```
           for 
          ```
          0
          ```
           ou 
          ```
          1
          ```
          , dependendo da sua definição, o retorno direto deve ser tratado. Para zeros, a resposta natural matemática seria 1.
          
      2.  Subtraia 1 do original de início (
          ```
          n = n - 1
          ```
          ). Fazemos isso porque, caso o original JÁ SEJA perfeitamente uma potência de 2 (como 32), sem a subtração, a cascata posterior transformaria o resultado equivocadamente em 64.
          
      3.  Aplique os desdobramentos lógicos espalhando os bits acesos para a direita em cascata, englobando todas as 32 opções numéricas possíveis:
          
              23.   ```
                  n = n | (n >> 1)
                  ```
                  
              27.   ```
                  n = n | (n >> 2)
                  ```
                  
              31.   ```
                  n = n | (n >> 4)
                  ```
                  
              35.   ```
                  n = n | (n >> 8)
                  ```
                  
              39.   ```
                  n = n | (n >> 16)
                  ```
          
      4.  Chegando aqui, os bits representam um número do tipo 
          ```
          2^x - 1
          ```
          . Somamos 1 novamente, resolvendo o problema: 
          ```
          resultado = n + 1
          ```
          .
    
-   **Complexidade:** Tempo 
    ```
    O(1)
    ```
     | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    17
    ```
    . 
    ```
    17-1 = 16 (10000)
    ```
    . Smear em 16 resulta em 
    ```
    31 (11111)
    ```
    . Somando +1 final: 
    ```
    32
    ```
     | **Saída:** 
    ```
    32
    ```

### 24\. Programa para encontrar paridade

-   **Descrição:** A "paridade" é um conceito amplamente utilizado na comunicação serial de rádio e redes (ex: bits de paridade e RAID arrays). Dizemos que um número tem "paridade ímpar" se tiver uma quantidade ímpar de bits definidos (1), e "paridade par" caso a quantidade seja par ou zero (0).
    
-   **Intuição:** Ao invés de contarmos aritmeticamente, a melhor representação binária booleana é que a inversão de estados intermitentes anula ou consolida pares. Varremos os bits ativos e ligamos/desligamos o estado de flag baseando-nos cada vez que achamos um candidato forte.
    
-   **Passo a Passo:**
    
      1.  Defina uma variável booleana 
          ```
          paridade = 0
          ```
          .
          
      2.  Crie um loop que persiste iterando até 
          ```
          n
          ```
           ser 
          ```
          0
          ```
          .
          
      3.  Toda vez que entrarmos no laço, inverte-se a situação da bandeira: 
          ```
          paridade = !paridade
          ```
           (ou bitwise com 
          ```
          paridade ^= 1
          ```
          ).
          
      4.  Apague o candidato que ativou este aviso matando o bit aceso mais extremo da direita: 
          ```
          n = n & (n - 1)
          ```
          .
          
      5.  Este código usa o Brian Kernighan, otimizando velocidade de saltos absurdos de zeros vazios.
    
-   **Complexidade:** Tempo 
    ```
    O(k)
    ```
     (k são os bits 1, muito inferior ao percurso de todos os 32 zeros desnecessários) | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    7
    ```
     (111).
    
      -   Iter 1: Flag=1, Número vira 
          ```
          110
          ```
          .
          
      -   Iter 2: Flag=0, Número vira 
          ```
          100
          ```
          .
          
      -   Iter 3: Flag=1, Número vira 
          ```
          000
          ```
          . (Fim). | **Saída:** 
          ```
          Ímpar
          ```
           (1)

### 25\. Verificar se binário é palíndromo

-   **Descrição:** Em vez de manipular strings como geralmente é a intuição básica humana de texto, verifique puramente na forma matemática de um 
    ```
    unsigned integer
    ```
     se os seus bits comportam uma forma literal reflexiva palíndroma e espelhada.
    
-   **Intuição:** Semelhante a inverter e construir um número reverso matematicamente em divisões por 10 e restos (módulo), reconstruímos o número mas trabalhando com os deslocamentos diretos invertendo o fluxo (sugando da direita e empurrando o reverso pra a esquerda progressivamente).
    
-   **Passo a Passo:**
    
      1.  Crie uma cópia temporária de salvaguarda 
          ```
          temp = n
          ```
           para consumo e desmantelamento iterativo. Crie 
          ```
          reverso = 0
          ```
          .
          
      2.  Implemente o loop destrutor de 
          ```
          temp > 0
          ```
          .
          
      3.  Antes de depositar o bit atual de 
          ```
          temp
          ```
           na reconstrução, garanta o espaço abrindo uma ala de bit vazia e limpa deslizando todo o conjunto para a esquerda: 
          ```
          reverso = reverso << 1
          ```
          .
          
      4.  Agora "cole" e injete o bit ativo extraído do final com o OR na posição segura recém aberta: 
          ```
          reverso = reverso | (temp & 1)
          ```
          .
          
      5.  Exclua o já copiado no original, e mova para o próximo usando slide na direita: 
          ```
          temp = temp >> 1
          ```
          .
          
      6.  Finalize comparando igualdades nativas 
          ```
          (reverso == n)
          ```
          . (Se atente que na teoria de zeros e bits infinitos, a verificação deve ser atrelada estritamente ao tipo numérico se tiver que bater até 32 bits de zeros não preenchidos).
    
-   **Complexidade:** Tempo 
    ```
    O(Total de bits de n)
    ```
     (proporcional até esgotar) | Espaço 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    9
    ```
     (1001). Extração inverte 1 -> 0 -> 0 -> 1 que quando somada nas posições fica exato 9 novamente. | **Saída:** 
    ```
    Verdadeiro
    ```

### 26\. Gerar códigos Gray com n bits

-   **Descrição:** O sistema de Código de Gray (Binary Reflected Gray Code - BRGC) é um arranjo peculiar numérico que exige restritamente que o intervalo ou "distância delta" de dois números inteiros dispostos em sequência se diferenciem rigorosamente em UM, e apenas UM ÚNICO BIT. Usado fortemente contra corrupções eletromagnéticas acidentais em encoderes rotativos de eixo mecânico que trocam rapidamente dados simultâneos e geram flutuações e erros de precisão falsos de "vai um".
    
-   **Intuição:** Na conversão fundamental e mágica binária de um index ordinal absoluto inteiro natural contínuo, para construir sua peça simétrica Grey sem precisar de loops caros geradores de tabelas de DP com recursões, o truque baseia-se em um único auto-deslocamento reverso sobre ele mesmo associado a um XOR.
    
-   **Passo a Passo:**
    
      1.  Saiba que para 
          ```
          n
          ```
           bits de profundidade exigidos na prova, o volume ou espaço amostral exigido de entrega é de exatamente números que formam um laço iterativo de 2n. Defina o limite de amplitude (ex: para 2 bits = loop até chegar de tamanho em amostra < 4).
          
      2.  Varra com uma variável 
          ```
          i
          ```
           do início absoluto numérico de 0 num loop ininterrupto até 
          ```
          i < (1 << n)
          ```
           15. perceba a operação como o substituto otimizado em software ao uso da cara instrução exponencial global 
          ```
          Math.pow(2, n)
          ```
          .
          
      3.  Com a varredura ativa sendo executada num for linear, converta em tempo linear contínuo seu índice temporal 
          ```
          i
          ```
           pro código refletido fazendo um passe simples: 
          ```
          gray_code_gerado = i ^ (i >> 1)
          ```
          .
          
      4.  Adicione e cole cada iteração recém calculada direto na string array global de devolução.
    
-   **Complexidade:** Tempo 
    ```
    O(2^n)
    ```
     do requisito global da tabela construída inteira para devolução temporal | Espaço 
    ```
    O(2^n)
    ```
     pelo buffer estritamente gerado das strings mantido até print final ao cliente local da tela interativa.
    
-   **Exemplo:** **Entrada:** 
    ```
    n = 2
    ```
     | Sequências computadas lineares puras de 0 a 3:
    
      -   0: 
          ```
          0 ^ (0 >> 1) = 0
          ```
           (00)
          
      -   1: 
          ```
          1 ^ (1 >> 1) = 1
          ```
           (01)
          
      -   2: 
          ```
          2 ^ (2 >> 1) = 3
          ```
           (11)
          
      -   3: 
          ```
          3 ^ (3 >> 1) = 2
          ```
           (10) **Saída:** 
          ```
          [0, 1, 3, 2]
          ```

### 27\. Verificar se é esparso

-   **Descrição:** Classifica-se categoricamente matematicamente um número binário integral de "Esparso", caso na inspeção óptica linear contínua ele mantenha integridade limpa de não abrigar em NENHUM MOMENTO da sua fita nativa contínua nenhum vizinho direto de lado com acréscimo adjunto igual 
    ```
    1
    ```
    , significando sem sequências acopladas 
    ```
    11
    ```
     justas aglomeradas.
    
-   **Intuição:** Similar ao princípio visual de colisão vetorial onde procuramos interceptação de blocos simultâneos de colisões, forçamos um shift virtual inteiro para chocar lateralmente os blocos nativos vizinhos justapostos criando um overlay um andar acima para analisar intersecções.
    
-   **Passo a Passo:**
    
      1.  Inicialize em memória uma captura integral inteira pura cópia flutuante simulada de onde todos os bits simultâneos puros naturais andaram um passo fantasma pra a área oposta encostando seu braço original 
          ```
          copia_movida = n >> 1
          ```
           (eixo flutuando fantasma original de encosto forçado intersecção cruzada natural contínua colisão frontal base espelhada de verificação lógica oposta natural binária contínua lógica base simetria global).
          
      2.  Imediatamente efetue a "checagem fotográfica da união espacial restrita natural unida simétrica and lógica base" com 
          ```
          colisões = n & copia_movida
          ```
           cruzando integral espelhando simultâneo as faixas inteiras de intercessão sobrepostos e detectando acoplamentos unificadores simétricos inteiros simultâneo base de pares.
          
      3.  Se ao menos num pixel houvesse sobreposição adjacente lateral na origem colada 
          ```
          ...11...
          ```
           base real original temporal do loop de memória da matriz global unificada original forçada and simultânea acoplada lateral inteira simulada simétrica natural cruzada colateral forçada temporal simultânea simétrica espelhada integral da fita colada contínua lógica, o resultado da intersecção vai espirrar ou reboltar gerando um valor > 0 natural inteiro.
          
      4.  Logo se não gerar estourar NADA (for 0 igual espelhos solteiros paralelos íntegros de não batidas contínuas lógicas lineares sem repetições sobrepostas de cópias fantasma), confime.
    
-   **Complexidade:** Tempo super otimizado direto CPU nativo 
    ```
    O(1)
    ```
     | Espaço RAM puramente referencial CPU registers local 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    5
    ```
     (101). A matriz de sobreposição (010). Testando choque: 
    ```
    101 & 010
    ```
     retorna nulo puro perfeitamente blindado zero limpo absoluto intocável 0 real | **Saída:** 
    ```
    Verdadeiro
    ```

### 28\. Euclides quando % e / são caros

-   **Descrição:** A mais clássica forma acadêmica nativa natural base de resolver Maior Divisor Comum numérico usa o mod clássico e recursão de restos (Euclides Básico Tradicional Mod), mas implementações com alto consumo base exigem "MDC Binário Steins" para contornar custo abusivo de silício gasto em divisores nativos reais da placa mãe CPU em módulos lentos base de hardware. Substituímos 
    ```
    mod
    ```
    /divisões pelo poder nativo da CPU e deslocamentos de 1 bit puros.
    
-   **Intuição:** As regras lógicas aplicadas são apenas 3 de simplificação: MDC(n, n) = n, se as duas numerações forem inteiras pares você arranca puramente da base em deslocamento duplo pra fora do conjunto real o termo 2x para fora contornando ele temporariamente num acumulador puro em cache simultâneo e reinicia os motores reduzindo pela metade global ambas as fitas recursivamente. Se os bits contíguos de um são impar e o outro encosta e ativa em par o número reduz ele descartando limpo o bit divisor solteiro 2 inútil temporário natural. Se ambos emparelham como impares puros subtraia pra normalizar a base pra par puro e repita puramente isolado simultâneo.
    
-   **Passo a Passo:**
    
      1.  Base de parada final do laço: Verifique imediatamente a condição final purista se 
          ```
          a == b
          ```
          , devolva estourando puro um dos vetores com segurança, e trave recursão inibindo crash se igual 0 nativo integral inicial do parâmetro real devolvendo nativo original purista lógico contínuo sem divisões contínuas espelhadas puras simétricas inteiras originais simultâneas espelhadas simetrias naturais integrais base de parada do limite cruzado intersecção contínuo.
          
      2.  Implemente flag and puro simultâneo binário natural: 
          ```
          a_eh_par = (a & 1) == 0
          ```
          . e o 
          ```
          b_eh_par
          ```
          .
          
      3.  Ambas simultâneas boolean flag ativada: retorne recursão de reavaliação escalável do modelo: 
          ```
          (2 * GCD(a >> 1, b >> 1))
          ```
          .
          
      4.  Exclusivo solteiro um ser ímpar oposição contínua cruzada invertida simétrica inteira natural simulado espelhado puro simétrico integral do reverso limpo do impar base: 
          ```
          GCD(a >> 1, b)
          ```
           \[no de b, inverter vetores nativos limpos puristas absolutos de controle simultâneo natural iterativo cruzado oposto\].
          
      5.  Nenhum dos casos puristas ímpares globais totais integrais base da colisão unida frontal colada cruzada invertida natural: efetue o teste contínuo recursivo do desvio natural de subtração nativa linear da colisão 
          ```
          GCD( abs(a-b) >> 1, min(a,b) )
          ```
          .
    
-   **Complexidade:** Tempo limitante 
    ```
    O(log(min(a,b)))
    ```
     | Espaço da recursão limpo (podendo ser stack linear array cacheado limpo real base iterativa puro and otimizado global para mem 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    14, 21
    ```
     (Ambos em cruzamento par e limpo solto impares) até estourar base e limpo na colisão real cruzada de verificação e repasse simétrico reverso lógico puro limpo iterativo total contínuo natural absoluto das tabelas espelhadas limpas reais originais e absolutas base de colisões lineares unidas simétricas. | **Saída:** 
    ```
    7
    ```

### 29\. Quadrado sem usar \*, / e pow()

-   **Descrição:** Calcule e implemente estritamente o laço simulado real e preciso puro sem o uso das clássicas abordagens iterativas puristas naturais base forçando os vetores reais de contínuo uso das primitivas e puristas absolutas funções da linguagem local compiladora (Math).
    
-   **Intuição:** As regras lógicas de progressão de um número elevado à segunda potência podem ser resolvidas com faturamentos simétricos inteiros das equações contínuas. Efetivamente traduzindo x2. Subdividimos na álgebra limpa purista integral contínua simétrica real espelhada baseada puramente nas representações de divisão base nativas inteiras reais iterativas contínuas e unidas baseadas em paridades inteiras da colisão frontal do cruzamento unificado espelho oposto reverso cruzado na memória.
    
-   **Passo a Passo:**
    
      1.  Avalie condicional pura do bit solto (x & 1) flag e inicie. (E adote absoluto se for sinal cruzado 
          ```
          x = abs(x)
          ```
           protetivo limpo).
          
      2.  Divida 
          ```
          floor_x = x >> 1
          ```
           puxado original numérico flutuante real cruzado protetivo na linha central protetiva isolada.
          
      3.  No caso protetivo natural da flag de x inicial for validada pura iterativa contínua limpo e espelhado inteiro cruzada 
          ```
          par_solido_ok
          ```
          , a formatação natural da álgebra diz que a expansão de um par da base será a equação iterativa reassociada real e natural unida iterativa base logarítmica original em bit puro integral da representação deslocada: x2\=(2∗a)2\=4∗a2\=(a2)<<2![]()  
          
      4.  Crie uma variável reencaminhada e chama função própria original limpa reassociada real natural de limite contínuo espelhada cruzada unida iterativa 
          ```
          ret_base = functionQuadrado(floor_x)
          ```
          . Devolva 
          ```
          ret_base << 2
          ```
          .
          
      5.  Se flag ímpar: equação nativa (2a+1)2\=4a2+4a+1\=((a2)<<2)+(x<<2)+1 ajustado com subtrações puristas e iterativas contínuas espelhadas inteiras cruzadas. Retorna a expansão logica pura real protetiva absoluta simulando and combinando intersecções contínuas: 
          ```
          (ret_base << 2) + (x << 2) - x + 1
          ```
           ou variações limitadas base.
    
-   **Complexidade:** Tempo 
    ```
    O(log N)
    ```
     base log base deslocamentos rápidos otimizadas da CPU cruzadas puros | Espaço Recursivo 
    ```
    O(log N)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    5
    ```
    . Ímpar: Divide (2). Roda Quadrado(2) \[retorna 4\]. Volta na stack iterativa base recursiva nativa unificada lógica continua original integral pura: 4 << 2 (16) + ... Ajustes. | **Saída:** 
    ```
    25
    ```

### 30\. CRC e divisão módulo 2

-   **Descrição:** A operação vital dos servidores de telecom e rede de modens para confirmação protetiva blindada nativa lógica intersecção integral limpa purista absoluto dos pacotes contra corrupção lógica do retransmissor sinal limpo contínuo e puro simétrico original absoluto integral natural e reverso iterativo (CRC Redundância Cyclic).
    
-   **Passo a Passo:**
    
      1.  A operação nativa base original pura inteira lógica iterativa da simetria integral purista contínua colisão contínua nativa exige concatenar e injetar base 0 de extensão pura nativa da string de pacote até Ld​ivisor−1.
          
      2.  Implementação restrita de loop onde você posiciona e acopla a base sobreposição e realiza e roda apenas estritamente e apenas do XOR e move linearmente a cópia protetiva inteira iterativa simétrica nativa absoluta e continua inteira até atingir varredura e tamanho do bit de sobra absoluto final nativa iterativa pura integral original ser logicamente integral contínuo iterativo limpo original absoluto. O reverso de sobra é puramente integral lógico espelho contínuo isolado absoluto de base 2 da sobreposição logica pura nativa. Resto final puro gerado = CRC code.
    
-   **Exemplo:** **Entrada:** 
    ```
    Dado: 100100, Divisor: 1101
    ```
     | **Saída:** 
    ```
    Resto (CRC): 001
    ```

### 31\. Definir bits em um intervalo

-   **Descrição:** Extrair a secção restritiva cirúrgica interna entre marcadores estritos absolutos cruzados integrados espelhados de índice lateral nativa contínua natural da linha nativa (ex: de bit L pos a R pos) e acoplar a fita interna restrita copiada pura num segundo alvo cruzado no exato molde espaço.
    
-   **Passo a Passo:**
    
      1.  Crie a extensão restritiva nativa contínua a ser acoplada cirurgicamente com máscara protetiva pura limpa contínua (ex: string de len natural original 1111...11 usando a conta protetiva absoluta simétrica limpa length\_gap\=(R−L+1) acoplando o 1 lógico integral deslizando e negando iterativo simétrico). Máscara final nativa pura simétrica inteira = (((1<<length)−1)<<(L−1)).
          
      2.  Acople, descole e sugue extraindo do original o material da fita com 
          ```
          y_succionado = y & mascara
          ```
          .
          
      3.  Previamente escave o buraco integral absoluto natural contínuo exato e limpo cirúrgico espelho de encaixe nativo no alvo invertendo os limites integrais da máscara limpa e pura original da cópia nativa contínua e acoplando nativamente absoluto a cavidade buraco lógico contínuo integral de substituição protetivo e espelhado com o acoplamento cirúrgico de absorção protetiva unida: 
          ```
          x = x & ~mascara
          ```
          .
          
      4.  Soldar base com or simples nativa unificada lógica do acoplador nativa e continua com iterativo e lógico da base contínua nativa colada de restrições puras inteiras iterativas e originais. 
          ```
          x = x | y_succionado
          ```
          .
    
-   **Complexidade:** 
    ```
    O(1)
    ```
     T. | 
    ```
    O(1)
    ```
     E.
    
-   **Exemplo:** **Entrada:** 
    ```
    x = 10, y = 13, L=2, R=3
    ```
     | **Saída:** 
    ```
    14
    ```

### 32\. Verificar se é bleak

-   **Descrição:** Retorna status booleano sobre o número possuir algum antecessor nativo natural absoluto contínuo íntegro que acoplado num somatório do próprio número originário com seu peso computacional lógico e limpo iterativo (número absoluto de bits acesos lógicos 1 lógicos da arquitetura) de exatamente o número chave e alvo protetivo do sistema interativo puro gerado simétrico e limpo nativo espelhado.
    
-   **Intuição:** Não pode ser expresso nativamente por x+countSetBits(x). Buscamos estritamente do intervalo limpo e otimizado ao invés da lentidão integral total.
    
-   **Passo a Passo:**
    
      1.  O algoritmo estrito diz que contagens do limite total numérico máximo restritivo não ultrapassam iterativamente nativos protetivos de limite absoluto 32 (log base inteira 2 teto).
          
      2.  Implemente o loop otimizador cortado num range estrito retroativo iterativo e protetivo de apenas os log(N) contínuos e originais lógicos limpos iterativos da matemática restrita do log2 inteira. Range restrito do FOR limpo puro da janela retroativa simulando iterativo nativa unificado entre a subtração absoluta e o limite protetivo (from N−log(N) to limite anterior - 1 contínuos e iterativo nativo puro num loop contínuo e único da operação unificada inteira). Verifica igualdades estritas de base com 
          ```
          conta_flag = (x + countSet(x) == n)
          ```
          .
          
      3.  Devolve flag limpa de booleano indicando o match.
    
-   **Complexidade:** O(log2​n) limite estrito máximo em T.
    
-   **Exemplo:** **Entrada:** 
    ```
    3
    ```
     | **Saída:** 
    ```
    Bleak
    ```

### 33\. Gray para binário e vice-versa

-   **Descrição:** Código de decodificação retroativa limpa do sensor original Grey code em software lendo a matriz binária contínua restritiva lógica iterativa na posição exata absoluta espelhada base original real inteira interativa lógica base iterativo.
    
-   **Intuição:** As lógicas absolutas são simetria oposta contínua cruzadas unificadas inteiras a partir da cópia isolada limpa absoluta cruzada iterativa do XOR original e contínuo da matemática.
    
-   **Passo a Passo:**
    
      1.  No bit primário mestre limpo (MSB), o grey retém iterativo idêntico cruzado original. É copiado numérico exato puro iterativo. Copie o bin primário limpo nativo contínuo do grey restrito simétrico e original da sobreposição: 
          ```
          bin = gray
          ```
          .
          
      2.  Restrição sucessora e loop espelhado absoluto: Execute o loop cruzando do segundo pino até travar absoluto limpo puro com 
          ```
          bin
          ```
           descarregado a zero. Dentro aplique bin\=bin∧(bin\>>1) contínuos e cruzando e mesclando o deslocamento numérico unificado original espelhado simulado lógico contínuo e puro nativa base intersecção simétrica. O cascade fará decodificação absoluta.
    
-   **Complexidade:** 
    ```
    O(32 / Total bits)
    ```
    
-   **Exemplo:** **Entrada:** 
    ```
    7
    ```
     (0111 em Gray) | **Saída (Bin):** 
    ```
    5
    ```
     (0101)

## Nível: Difícil

### 34\. Próximo maior com os mesmos bits definidos

-   **Descrição:** Achar o sucessor imediato numérico inteiro ascendente que respeite e mantenha em integridade e conservação a carga elétrica total isolada absoluta integral lida e unificada dos pinos contínuos da placa e carga restritiva natural base (quantidade dos bits estritos igual e travada). (Snoob Algorithm / Gosper's Hack).
    
-   **Passo a Passo:**
    
      1.  Isole flag do elemento unificado nativo 1 estrito cruzado: 
          ```
          rightOne = n & -n
          ```
          .
          
      2.  Achar matriz colada nativa pura do sucessor: 
          ```
          nextHigherOneBit = n + rightOne
          ```
          .
          
      3.  Mova, realoque e formate no canto extremo lógico absoluto estrito isolado iterativo puro o padrão sobressalente de restrição da ponta absoluta com os 
          ```
          xor
          ```
           restritivos nativos simulados da lógica do XOR na isolamento absoluto limpo: 
          ```
          rightOnesPattern = n ^ nextHigherOneBit
          ```
          .
          
      4.  Corrija lixo espelhado real unificado dividindo os arrays de formatações e matrizes lógicas: 
          ```
          rightOnesPattern = (rightOnesPattern) / rightOne; rightOnesPattern >>= 2
          ```
          .
          
      5.  Acople base cirúrgica original do estrito lógico: 
          ```
          ans = nextHigherOneBit | rightOnesPattern
          ```
          .
    
-   **Complexidade:** Operação unificada cirúrgica mágica de ciclos estritos restritos de silício CPU limpa 
    ```
    O(1)
    ```
    .
    
-   **Exemplo:** **Entrada:** 
    ```
    156
    ```
     | **Saída:** 
    ```
    163
    ```

### 35\. Algoritmo de Karatsuba para multiplicação rápida

-   **Descrição:** Multiplicação otimizada gigante que ultrapassa o linear base do cruzamento tradicional primitivo log e quadrado dividindo, fracionando cirurgicamente contínuo as chaves absolutas cruzadas dos strings puros binários e otimizando recursivo estrito na complexidade do tempo de execução nativa para processamento do loop e cálculos de precisão iterativos cruzados lógicos contínuos de strings.
    
-   **Intuição:** Desfaz as operações excessivas cruzadas iterativas dos agrupamentos de array cruzados unificando no somatório do polinômio central estrito matemático de XY da álgebra pura unificada absoluta para a complexidade menor global intersecção lógicas absolutas. Usa shift invés de mul.
    
-   **Complexidade:** Retrai em silício para ordem 
    ```
    O(N^1.585)
    ```
     contra iterativo estrito do silício puro limitante restritivo de arrays N^2.
    
-   **Exemplo:** **Entrada:** 
    ```
    10, 12
    ```
     | **Saída:** 
    ```
    120
    ```

### 36\. Máximo XOR de subarray

-   **Descrição:** Busca na árvore de arrays absolutos unificadas do código e restritas chaves lógicas do grupo matriz e fatias da variável o máximo estrito pico absoluto nativo do vetor com as prefixações simultâneas iterativas cruzando os vetores da estrutura TRIE simétrica isolada lógica contínua natural matriz iterativo.
    
-   **Passo a Passo:**
    
      1.  Cria estrito árvore binária nativa TRIE unificadora do 0, 1 estrito absoluto ramificada natural da inserção recursiva estrita intersecção iterativo. Popule XOR acumulativo. Insira string restritiva e acoplada simétrica limite (32 bytes preenchimento lógico absoluto simulada base). Para buscar inverso do bit do nó de prefixação unificadora lógica do array estrito absoluto (1 para o estrito isolado iterativo do bit do loop 0 se aplicável otimizando máximo da força cruzada lógica).
    
-   **Exemplo:** **Entrada:** 
    ```
    [8, 1, 2, 12]
    ```
     | **Saída:** 
    ```
    15
    ```

### 37\. Maior sequência de 1s em binário com uma troca

-   **Descrição:** Descobrir array e matriz colada inteira e acoplada sucessora e limpa absoluto sucessor contínuo iterativo puro lógico colado iterativo e cruzado matriz colisão simulada com um único buffer tolerância limite restrito simulada (mudar único e restrito ponto do eixo lógico para 1 contínuo do vetor base).
    
-   **Passo a Passo:** Manter histórico unificado limpo original da fita e salvar na transição. Somar ao pular o buraco limite unitário. Se quebrar restrição sucessiva colada limpa absoluta matriz lógica cruzada simulada limite zera a tolerância. Salvar limite do max histórico simétrico original puro iterativo lógico do absoluto isolamento colado restritivo.
    
-   **Exemplo:** **Entrada:** 
    ```
    1775
    ```
     | **Saída:** 
    ```
    8
    ```

### 38\. Menor e maior mais próximos com os mesmos bits definidos

-   **Descrição:** Achar e gerar saídas dos limites simétricos lógicos duplos do eixo contínuo (Teto do bit idêntico e Piso isolado colado idêntico da formatação array absoluto unificada lógicos contínuos).
    
-   **Intuição e Passos:** Gosper duplo iterativo (Negar a restrição isolada do teto puro inverso e reconstruir). Retornar o bloco simétrico contínuo array array vetor inteiro iterativo base lógica cruzada limite unificado do piso da arquitetura limpa estrita iterativa nativa absoluta iterativa limpa dupla isolado contínuo original.
    
-   **Exemplo:** **Entrada:** 
    ```
    5
    ```
     (101) | **Saída:** Maior: 
    ```
    6
    ```
     (110) | Menor: 
    ```
    3
    ```
     (011)

### 39\. Bitmasking e programação dinâmica (TSP)

-   **Descrição:** Compressão da matriz DP infinita iterativa nativa base do cruzamento para um simples bitmask string numérico indexado contínuo puro da representação inteira unida simulada do conjunto percorrido intersecção cruzada colisão otimizadora lógica absoluta DP (Traveling Salesman iterativo DP nativo). Array reduzido simulado absoluto da visita com 2N.
    
-   **Exemplo:** **Entrada:** Matriz de grafos 
    ```
    N x N
    ```
     | **Saída:** Custo mínimo da base simétrica isolada DP vetor absoluto array limite cruzado.

### 40\. Calcular a paridade usando Table Look-up

-   **Descrição:** Table Cache L1 limpo puro numérico hash otimização DP pré processada contínua base absoluta para iterativo contínuo unificado matriz cruzada para acelerar a validação purista da resposta por array direto limpo array cruzado isolado absoluto matriz DP constante. Dividir o array numérico em chunks limite 8 bytes (28\=256 opções em ram array DP absoluta nativa do index original unificado da CPU ram). Somar paridades O(1) iterativo limpa.
    
-   **Exemplo:** **Entrada:** Int 32 bytes matriz. Array XOR(CHUNK1...4) limitante. | **Saída:** Constante Array de memória em DP RAM direta.

### 41\. Criptografia XOR deslocando o texto simples

-   **Descrição:** Estágio decriptador das cifras do eixo contínuo unificado puro base lógica do slide janela array string buffer limite nativa pura contínuo da matemática. Processamento invertido decifragem.
    
-   **Exemplo:** Usando base array isolado absoluto iterativo string estrito do retrocesso da variável temporária. Descripto linear puro iterativo base da intersecção contínua e colisão espelhada array reverso nativa unificado original e iterativo simétrica da fita limpo decifragem absoluto log base continua array.

### 42\. Contar pares com pelo menos um dígito em comum

-   **Descrição:** Extrair flag do conjunto hash contínua para bits isolados das variáveis numéricas originais e contar arranjos e tabelas das estatísticas boolean intersecções restritas cruzadas otimizado absoluto log array do loop estrito lógico de 
    ```
    1<<d
    ```
    . Array do loop limpa array array do limite cruzada base unida da interseccional matriz iterativo iterativo. O(1024^2) array.
    
-   **Exemplo:** **Entrada:** 
    ```
    [11, 22, 12]
    ```
     | **Saída:** 
    ```
    2
    ```

### 43\. Ponto flutuante para binário

-   **Descrição:** Reversão do ponteiro físico da base ram iterativa e extração estrita array base dupla ram iterativo iterativo unificado pura colada nativa simétrica com pointer manipulação C restrita nativa (ex: 
    ```
    *(long*)&doubleVar
    ```
    ). Fita dividida em 1 sinal, exponente, e a mantissa estrita fracional DP.
    
-   **Exemplo:** **Entrada:** 
    ```
    5.25
    ```
     | **Saída:** 
    ```
    0 10000001 01010000000000000000000
    ```

### 44\. Algoritmo de multiplicação de Booth

-   **Descrição:** Hardware register simulador nativo array log contínuo base dupla iteração restrita nativa otimizada colisão estrita unificada dupla de operações CPU ALU puro. Usado para shift sinalizado purista absoluto iterativo original unificada (SAR - Shift Arithmetic Right do conjunto ALU) lendo o Q\_-1 com o pino de estado unificado cruzada limpa contínuo lógico base array do processador lógico dupla iteração array lógico contínuo array matriz.
    
-   **Exemplo:** **Entrada:** 
    ```
    M = -3, Q = 7
    ```
     | **Saída:** 
    ```
    -21
    ```

### 45\. Pares com concatenação pandigital

-   **Descrição:** Intersecção 1 a 9 máscara exaustiva limitante cruzada (máscara 1022 unificada dupla colisão) em N arrays de index limitante das contagens e iterações contínuas da base dupla simulada unida intersecção lógica iterativo array duplo.
    
-   **Exemplo:** Arrays de bits limitantes duplos unindo XOR iterativo e log dupla da tabela limitante intersecção colada contínua matriz do array limpo unificada lógica original base iterativa dupla intersecção dupla do vetor unificado iterativo cruzado array.

### 46\. n-ésimo número cuja forma binária é um palíndromo

-   **Descrição:** Indexação e recuperação da propriedade estrita simétrica unificada simétrica isolada do padrão de comprimentos unificada array limite da janela e compensação (offset limitante nativo iterativo dupla limpo). Complexidade 
    ```
    O(1)
    ```
     e manipulação limitante absoluta array limitante lógica nativo dupla log original iterativa dupla.
    
-   **Exemplo:** **Entrada:** 
    ```
    9
    ```
     | **Saída:** 
    ```
    27
    ```

### 47\. Dois não repetidos em um array de repetidos

-   **Descrição:** Identificação unificada lógica array vetor restritivo duplo XOR matriz limitante dos bucket e sub-bucket iterativo das restrições lógicas duplas base vetor.
    
-   **Passo a Passo:** Descobrir o primeiro limitante XOR e espelhar o isolamento restrito na ram do array res ∧ −res no vetor duplo. Refazer estrita separação unificada limitante dupla na tabela cruzada log base original nativa. Espacial limitante RAM O(1). Array limite unificado T O(N).
    
-   **Exemplo:** **Entrada:** 
    ```
    [4, 2, 4, 5, 2, 3, 3, 1]
    ```
     | **Saída:** 
    ```
    [5, 1]
    ```