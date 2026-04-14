# Lista de Exercícios - Algoritmos Matemáticos

Esta lista foi elaborada para fortalecer a lógica de programação através de desafios matemáticos clássicos que fundamentam a computação moderna. O objetivo é que você implemente as soluções em qualquer linguagem de programação (C, C++, Java, Python, JavaScript, etc.), focando no fluxo de dados, na manipulação de variáveis e na eficiência algorítmica.

Dominar esses problemas ajuda a desenvolver o "pensamento computacional", essencial para resolver problemas complexos de engenharia de software e ciência de dados.

<details>
  <summary>🟢 Nível 1 - Fácil</summary>

<p>

_Foco: Sintaxe básica, laços simples, fórmulas diretas, lógica condicional, raízes e propriedades de divisibilidade._

### 1\. Soma dos Naturais

- **Descrição:** Calcular a soma acumulada de todos os números inteiros de 1 até um valor n definido pelo usuário. Este é o conceito básico de acumuladores em programação.
    
- **Passo a passo:**
  - 1. Receba um número inteiro positivo $n$.
  - 2. Abordagem A (Laço): Inicialize uma variável `soma = 0` e percorra de 1 a $n$, adicionando o índice à variável.
  - 3. Abordagem B (Matemática): Utilize a fórmula da Progressão Aritmética: $S = \frac{n(n+1)}{2}$. Esta abordagem é $O(1)$, ou seja, muito mais eficiente para números grandes.
    
- **Exemplo:** _Entrada: `5`_ | _Saída: `15`_ (Explicação: 1+2+3+4+5 = 15).

### 2\. Soma dos Quadrados dos Naturais

- **Descrição:** Calcular o resultado de $1^2 + 2^2 + 3^2 + ... + n^2$. Útil para entender como o crescimento exponencial impacta somatórios.
    
- **Passo a passo:**
  - 1.  Receba o valor limite $n$.
  - 2.  Utilize um laço de repetição ou a fórmula fechada: 6n(n+1)(2n+1)​.
  - 3.  Certifique-se de tratar casos onde n\=0 ou n\=1.
    
- **Exemplo:** Entrada: 
    ```
    3
    ```
     | Saída: 
    ```
    14
    ```
     (Explicação: 1 + 4 + 9 = 14).

### 3\. Enésimo Termo de uma PA

- **Descrição:** Em uma Progressão Aritmética, cada termo é o anterior somado a uma constante (razão). O desafio é encontrar um termo específico sem precisar listar todos os anteriores.
    
- **Passo a passo:**
    
      1.  Receba o termo inicial (a), a razão (r) e a posição desejada (n).
          
      2.  Aplique a lógica: para chegar no termo n, você partiu do primeiro e somou a razão n−1 vezes.
          
      3.  Cálculo: an\=a+(n−1)×r.
    
- **Exemplo:** Entrada: 
    ```
    a=2, r=3, n=5
    ```
     | Saída: 
    ```
    14
    ```
     (Série: 2, 5, 8, 11, **14**).

### 4\. Enésimo Termo de uma PG

- **Descrição:** Em uma Progressão Geométrica, os termos crescem por multiplicação. Este exercício exercita o uso de potências.
    
- **Passo a passo:**
    
      1.  Receba o valor inicial (a), a razão (r) e a posição (n).
          
      2.  A lógica fundamental é: an\=a×r(n−1).
          
      3.  Atenção: se r for grande, o valor de an pode ultrapassar a capacidade de um inteiro padrão (overflow).
    
- **Exemplo:** Entrada: 
    ```
    a=2, r=2, n=4
    ```
     | Saída: 
    ```
    16
    ```
     (Série: 2, 4, 8, **16**).

### 5\. Enésimo Número Triangular

- **Descrição:** Um número triangular Tn​ conta objetos arranjados em um triângulo equilátero. É visualmente a soma de 1 até n.
    
- **Passo a passo:**
    
      1.  Receba o nível n do triângulo.
          
      2.  O cálculo é idêntico à soma dos naturais: n(n+1)/2.
    
- **Exemplo:** Entrada: 
    ```
    4
    ```
     | Saída: 
    ```
    10
    ```
     (Visual: uma base de 4, sobreposta por 3, 2 e 1).

### 6\. Soma das Somas dos Números Naturais

- **Descrição:** Calcular o "somatório do somatório". Ou seja: S\=S1​+S2​+...+Sn​, onde Si​ é a soma de 1 até i.
    
- **Passo a passo:**
    
      1.  Receba n.
          
      2.  Use dois laços aninhados: o externo controla até qual número somamos, e o interno calcula a soma parcial.
          
      3.  Otimização: acumule a soma parcial em cada iteração do laço externo para evitar o reprocessamento.
    
- **Exemplo:** Entrada: 
    ```
    3
    ```
     | Saída: 
    ```
    10
    ```
     (Somas parciais: S1​\=1,S2​\=3,S3​\=6→1+3+6\=10).

### 7\. Contar Dígitos

- **Descrição:** Determinar a quantidade de algarismos que compõem um número inteiro. Essencial para algoritmos de processamento de texto e números.
    
- **Passo a passo:**
    
      1.  Receba o número N.
          
      2.  Enquanto N\>0, realize divisões sucessivas por 10 e conte as iterações.
          
      3.  Dica: Para N\=0, a contagem deve ser 1. Outra forma é usar a função logarítmica: floor(log10​(N))+1.
    
- **Exemplo:** Entrada: 
    ```
    1234
    ```
     | Saída: 
    ```
    4
    ```
    .

### 8\. Soma dos Dígitos

- **Descrição:** Somar individualmente cada algarismo de um número. Muito usado em algoritmos de validação (como Checksums).
    
- **Passo a passo:**
    
      1.  Receba N.
          
      2.  Extraia o último dígito usando o operador de resto (
          ```
          N % 10
          ```
          ).
          
      3.  Some esse dígito ao totalizador e atualize N para 
          ```
          N / 10
          ```
          .
          
      4.  Repita até que N seja zero.
    
- **Exemplo:** Entrada: 
    ```
    123
    ```
     | Saída: 
    ```
    6
    ```
     (1+2+3).

### 9\. Reverter Dígitos

- **Descrição:** Transformar o número 123 no número 321. Treina a manipulação de casas decimais.
    
- **Passo a passo:**
    
      1.  Inicialize 
          ```
          reverso = 0
          ```
          .
          
      2.  Em um laço: pegue o último dígito de N, multiplique o 
          ```
          reverso
          ```
           atual por 10 e some o dígito extraído.
          
      3.  Reduza N dividindo por 10.
    
- **Exemplo:** Entrada: 
    ```
    456
    ```
     | Saída: 
    ```
    654
    ```
    .

### 10\. K-ésimo Dígito em ab![]()  

- **Descrição:** Calcular a potência e identificar um dígito específico na sequência do resultado.
    
- **Passo a passo:**
    
      1.  Calcule R\=ab.
          
      2.  Para encontrar o k\-ésimo dígito da direita para a esquerda: divida R por 10(k−1) para "empurrar" o dígito desejado para a casa das unidades.
          
      3.  Aplique 
          ```
          % 10
          ```
           para isolar o dígito.
    
- **Exemplo:** Entrada: 
    ```
    a=3, b=3, k=1
    ```
     | Saída: 
    ```
    7
    ```
     (3³ = 27; o 1º dígito é 7).

### 11\. Número Palíndromo

- **Descrição:** Verificar se um número é simétrico (ex: 121, 44, 505).
    
- **Passo a passo:**
    
      1.  Armazene o valor original.
          
      2.  Gere o reverso do número (veja exercício 9).
          
      3.  Compare se 
          ```
          original == reverso
          ```
          . Se sim, retorne verdadeiro.
    
- **Exemplo:** Entrada: 
    ```
    121
    ```
     | Saída: 
    ```
    True
    ```
    ; Entrada: 
    ```
    123
    ```
     | Saída: 
    ```
    False
    ```
    .

### 12\. MDC (Máximo Divisor Comum)

- **Descrição:** Encontrar o maior divisor inteiro comum a dois números. Fundamental para simplificação de frações.
    
- **Passo a passo:**
    
      1.  Utilize o **Algoritmo de Euclides**: o MDC entre a e b é o mesmo que entre b e o resto de a/b.
          
      2.  Repita o processo até que o resto seja zero. O divisor atual será o MDC.
    
- **Exemplo:** Entrada: 
    ```
    12, 18
    ```
     | Saída: 
    ```
    6
    ```
    .

### 13\. MMC (Mínimo Múltiplo Comum)

- **Descrição:** Encontrar o menor número positivo que é múltiplo de ambos os valores.
    
- **Passo a passo:**
    
      1.  Calcule primeiro o MDC entre a e b.
          
      2.  Use a propriedade: MMC(a,b)\=MDC(a,b)∣a×b∣​.
    
- **Exemplo:** Entrada: 
    ```
    15, 20
    ```
     | Saída: 
    ```
    60
    ```
    .

### 14\. Somar duas Frações

- **Descrição:** Realizar a operação matemática de adição entre frações e apresentar o resultado simplificado.
    
- **Passo a passo:**
    
      1.  Calcule o denominador comum (MMC dos denominadores ou simplesmente b×d).
          
      2.  Ajuste os numeradores: (a×d)+(c×b).
          
      3.  Após obter a fração resultante, encontre o MDC entre o novo numerador e o novo denominador para simplificar o resultado final.
    
- **Exemplo:** Entrada: 
    ```
    1/2 + 1/4
    ```
     | Saída: 
    ```
    3/4
    ```
     (após simplificar 
    ```
    6/8
    ```
    ).

### 15\. Verificar se são Coprimos

- **Descrição:** Números coprimos (ou primos entre si) não compartilham nenhum divisor comum além do 1.
    
- **Passo a passo:**
    
      1.  Calcule o MDC dos dois números.
          
      2.  Se o resultado for exatamente 1, eles são coprimos.
    
- **Exemplo:** Entrada: 
    ```
    8, 15
    ```
     | Saída: 
    ```
    True
    ```
     (MDC é 1).

### 16\. Fatorial de um Número

- **Descrição:** Calcular o produto de todos os inteiros de 1 até n (n!). Base para problemas de permutação.
    
- **Passo a passo:**
    
      1.  Inicialize 
          ```
          resultado = 1
          ```
          .
          
      2.  Multiplique pelo índice de um laço que vai de 2 até n.
          
      3.  Considere que 0!\=1.
    
- **Exemplo:** Entrada: 
    ```
    5
    ```
     | Saída: 
    ```
    120
    ```
     (1_2_3_4_5).

### 17\. MDC de mais de 2 Números

- **Descrição:** Generalização do MDC para um conjunto de números.
    
- **Passo a passo:**
    
      1.  Receba uma lista ou array de números.
          
      2.  Calcule o MDC do primeiro par. Use o resultado para calcular o MDC com o próximo item da lista.
          
      3.  Continue até processar todos os elementos.
    
- **Exemplo:** Entrada: 
    ```
    [12, 18, 24]
    ```
     | Saída: 
    ```
    6
    ```
    .

### 18\. MMC de mais de 2 Números

- **Descrição:** Generalização do MMC para uma lista de números.
    
- **Passo a passo:**
    
      1.  Similar ao MDC: calcule o MMC dos dois primeiros elementos.
          
      2.  Use o resultado para calcular o MMC com o próximo.
    
- **Exemplo:** Entrada: 
    ```
    [2, 7, 3]
    ```
     | Saída: 
    ```
    42
    ```
    .

### 19\. Sequência de Padovan

- **Descrição:** Similar à Fibonacci, mas com a regra P(n)\=P(n−2)+P(n−3). As sementes iniciais são P(0)\=P(1)\=P(2)\=1.
    
- **Passo a passo:**
    
      1.  Use três variáveis para guardar os estados anteriores.
          
      2.  Em cada passo, a nova variável é a soma da retrasada com a anterior a ela.
          
      3.  Atualize as três variáveis para o próximo ciclo.
    
- **Exemplo:** Entrada: 
    ```
    n=6
    ```
     | Saída: 
    ```
    4
    ```
     (Série: 1, 1, 1, 2, 2, 3, **4**).

### 20\. Contagem de Pares Cúbicos

- **Descrição:** Descobrir quantos pares de números inteiros positivos (a,b) satisfazem a equação a3+b3\=n.
    
- **Passo a passo:**
    
      1.  Itere o valor de a de 1 até a raiz cúbica de n.
          
      2.  Para cada a, calcule o valor que b deveria ter: b\=3n−a3​.
          
      3.  Se b for um número inteiro positivo, incremente o contador.
    
- **Exemplo:** Entrada: 
    ```
    9
    ```
     | Saída: 
    ```
    1
    ```
     (Par: 1³ + 2³ = 1 + 8 = 9).

### 21\. Soma de 2, 22, 222...

- **Descrição:** Calcular a soma de uma sequência onde cada termo tem um dígito repetido a mais que o anterior.
    
- **Passo a passo:**
    
      1.  Receba o número de termos n.
          
      2.  Use uma variável 
          ```
          termo
          ```
           que começa com 2.
          
      3.  Em um laço de 1 a n: adicione 
          ```
          termo
          ```
           à 
          ```
          soma
          ```
           total e atualize o 
          ```
          termo
          ```
           fazendo 
          ```
          (termo * 10) + 2
          ```
          .
    
- **Exemplo:** Entrada: 
    ```
    3
    ```
     | Saída: 
    ```
    246
    ```
     (2 + 22 + 222).

### 22\. Soma de Quadrados Ímpares

- **Descrição:** Calcular a soma dos quadrados apenas dos números ímpares até o n-ésimo termo ímpar.
    
- **Passo a passo:**
    
      1.  Itere de i\=1 até n.
          
      2.  O n-ésimo número ímpar é dado por (2i−1).
          
      3.  Eleve esse valor ao quadrado e acumule na soma.
    
- **Exemplo:** Entrada: 
    ```
    2
    ```
     | Saída: 
    ```
    10
    ```
     (12+32).

### 23\. Soma de Série Decimal (0.6, 0.06...)

- **Descrição:** Somar termos onde a cada passo o 6 "escorrega" uma casa decimal para a direita.
    
- **Passo a passo:**
    
      1.  Note que cada termo i é 6/10i.
          
      2.  Acumule os valores em uma variável de ponto flutuante (double/float).
    
- **Exemplo:** Entrada: 
    ```
    2
    ```
     | Saída: 
    ```
    0.66
    ```
    .

### 24\. Enésimo Termo da Série (2, 12, 36...)

- **Descrição:** Identificar o padrão matemático por trás da sequência: 2,12,36,80,150...![]()  
    
- **Passo a passo:**
    
      1.  Observe que os termos seguem a fórmula n2+n3.
          
      2.  Calcule o resultado para o n fornecido.
    
- **Exemplo:** Entrada: 
    ```
    3
    ```
     | Saída: 
    ```
    36
    ```
     (32+33\=9+27).

### 25\. Raiz Digital

- **Descrição:** Reduzir um número a um único dígito somando seus algarismos repetidamente.
    
- **Passo a passo:**
    
      1.  Enquanto o número for maior que 9, aplique a lógica da "Soma dos Dígitos" (Exercício 8).
          
      2.  Otimização (Congruência): O resultado é sempre 1+(n−1)%9.
    
- **Exemplo:** Entrada: 
    ```
    98
    ```
     | Saída: 
    ```
    8
    ```
     (9+8=17 -> 1+7=8).

### 26\. Números de Fibonacci

- **Descrição:** Gerar o enésimo termo da famosa sequência onde cada número é a soma dos dois anteriores (0,1,1,2,3,5...).
    
- **Passo a passo:**
    
      1.  Trate os casos base F(0)\=0 e F(1)\=1.
          
      2.  Use um laço para calcular os próximos termos salvando apenas os dois últimos para economizar memória.
    
- **Exemplo:** Entrada: 
    ```
    6
    ```
     | Saída: 
    ```
    8
    ```
    .

### 27\. Números de Lucas

- **Descrição:** Variação da Fibonacci que começa com 2 e 1.
    
- **Passo a passo:**
    
      1.  Inicie 
          ```
          a = 2
          ```
           e 
          ```
          b = 1
          ```
          .
          
      2.  Aplique a mesma lógica de soma iterativa por n vezes.
    
- **Exemplo:** Entrada: 
    ```
    3
    ```
     | Saída: 
    ```
    4
    ```
     (Série: 2, 1, 3, **4**).

### 28\. Verificar Potência

- **Descrição:** Checar se um número y pode ser escrito como xk.
    
- **Passo a passo:**
    
      1.  Se x\=1, y deve ser 1.
          
      2.  Enquanto y%x\==0, divida y por x.
          
      3.  Se o resultado final for 1, então y é uma potência de x.
    
- **Exemplo:** Entrada: 
    ```
    x=2, y=16
    ```
     | Saída: 
    ```
    True
    ```
     (24\=16).

### 29\. Três Divisores

- **Descrição:** Identificar se um número tem exatamente três divisores positivos.
    
- **Passo a passo:**
    
      1.  Observe que apenas quadrados perfeitos de números primos possuem exatamente 3 divisores (1, o próprio primo e o quadrado).
          
      2.  Verifique se n​ é um número inteiro.
          
      3.  Se sim, verifique se essa raiz é um número primo.
    
- **Exemplo:** Entrada: 
    ```
    49
    ```
     | Saída: 
    ```
    True
    ```
     (Divisores: 1, 7, 49).

### 30\. Raiz Quadrada Inteira

- **Descrição:** Calcular o maior inteiro x tal que x2≤n. Não utilize funções prontas de raiz.
    
- **Passo a passo:**
    
      1.  Use busca binária: chute um valor entre 0 e n.
          
      2.  Se meio2 for maior que n, procure na metade inferior; caso contrário, salve o valor e procure na metade superior.
    
- **Exemplo:** Entrada: 
    ```
    11
    ```
     | Saída: 
    ```
    3
    ```
    .

### 31\. Coeficiente Binomial

- **Descrição:** Calcular de quantas formas podemos escolher r itens de um conjunto de n itens (nCr).
    
- **Passo a passo:**
    
      1.  Use a fórmula: n!/(r!×(n−r)!).
          
      2.  Dica de eficiência: nCr\=nC(n−r). Calcule apenas o menor lado.
    
- **Exemplo:** Entrada: 
    ```
    n=5, r=2
    ```
     | Saída: 
    ```
    10
    ```
    .

### 32\. Triângulo de Pascal

- **Descrição:** Construir as primeiras n linhas de uma estrutura onde cada número é a soma dos dois logo acima.
    
- **Passo a passo:**
    
      1.  Comece com uma lista 
          ```
          [1]
          ```
          .
          
      2.  Para a próxima linha, adicione 1 no início e no fim, e os elementos do meio são a soma de pares adjacentes da linha anterior.
    
- **Exemplo:** Entrada: 
    ```
    3
    ```
     | Saída: 
    ```
    [[1], [1,1], [1,2,1]]
    ```
    .

### 33\. Enésima Linha do Triângulo de Pascal

- **Descrição:** Obter diretamente os valores da linha n sem gerar o triângulo todo.
    
- **Passo a passo:**
    
      1.  Cada termo k na linha n é o coeficiente binomial nCk.
          
      2.  Calcule os termos usando a relação: termo(k)\=termo(k−1)×(n−k+1)/k.
    
- **Exemplo:** Entrada: 
    ```
    3
    ```
     | Saída: 
    ```
    [1, 3, 3, 1]
    ```
    .

### 34\. Números de Armstrong

- **Descrição:** Um número é de Armstrong se a soma de seus dígitos, cada um elevado à potência do número total de dígitos, for igual ao próprio número.
    
- **Passo a passo:**
    
      1.  Conte quantos dígitos o número possui (k).
          
      2.  Isole cada dígito e eleve a k.
          
      3.  Compare a soma total com o original.
    
- **Exemplo:** Entrada: 
    ```
    153
    ```
     | Saída: 
    ```
    True
    ```
     (13+53+33\=1+125+27\=153).

### 35\. Determinante de uma Matriz

- **Descrição:** Calcular o determinante para entender transformações lineares.
    
- **Passo a passo:**
    
      1.  Se for 2x2: (a×d)−(b×c).
          
      2.  Se for 3x3: Siga a regra de Sarrus ou expansão por cofatores.
    
- **Exemplo:** Entrada: 
    ```
    [[1,2],[3,4]]
    ```
     | Saída: 
    ```
    -2
    ```
    .

### 36\. Exponenciação Modular

- **Descrição:** Calcular (ab)%m. Essencial em criptografia RSA.
    
- **Passo a passo:**
    
      1.  Não tente elevar a a b diretamente se b for grande.
          
      2.  Use o algoritmo de **Exponenciação Binária**: se b é par, ab\=(ab/2)2. Se ímpar, a×ab−1.
          
      3.  Aplique o 
          ```
          % m
          ```
           em cada multiplicação intermediária.
    
- **Exemplo:** Entrada: 
    ```
    a=2, b=10, m=1000
    ```
     | Saída: 
    ```
    24
    ```
     (1024%1000).

### 37\. Verificar Quadrados Perfeitos

- **Descrição:** Confirmar se um número possui uma raiz quadrada exata.
    
- **Passo a passo:**
    
      1.  Encontre a raiz quadrada inteira (Exercício 30).
          
      2.  Verifique se raiz×raiz\==n.
    
- **Exemplo:** Entrada: 
    ```
    25
    ```
     | Saída: 
    ```
    True
    ```
    .

### 38 a 43. Divisibilidade (3, 4, 7, 11, 13, 29)

- **Descrição:** Criar testes lógicos para números gigantes representados como strings.
    
- **Exemplos de Lógica:**
    
      - **Por 4:** Verifique se os dois últimos caracteres da string formam um número divisível por 4.
          
      - **Por 11:** Subtraia a soma dos dígitos em posições ímpares da soma dos dígitos em posições pares. Se o resultado for múltiplo de 11, o número original também é.
    
- **Exemplo:** Entrada: 
    ```
    121, div por 11
    ```
     | Saída: 
    ```
    True
    ```
    .

</p>
</details>

<details>
  <summary>🟠 Nível 2 - Médio</summary>

<p>

_Foco: Primalidade, fatoração e algoritmos de busca espacial._

### 44\. Equações Diofantinas Lineares

- **Descrição:** Resolver ax+by\=c para x e y inteiros.
    
- **Passo a passo:**
    
      1.  Calcule g\=MDC(a,b).
          
      2.  Se c%g\=0, a equação não possui soluções inteiras.
    
- **Exemplo:** Entrada: 
    ```
    3x + 6y = 9
    ```
     | Saída: 
    ```
    True
    ```
    .

### 45\. Função Totiente de Euler (ϕ)

- **Descrição:** Quantos números menores que n não compartilham fatores comuns com ele?
    
- **Passo a passo:**
    
      1.  Itere de 1 a n e aplique o teste de coprimo (Exercício 15).
          
      2.  Otimização: ϕ(n)\=n×∏(1−1/p) para cada fator primo p de n.
    
- **Exemplo:** Entrada: 
    ```
    9
    ```
     | Saída: 
    ```
    6
    ```
     (1, 2, 4, 5, 7, 8).

### 46\. Peneira de Eratóstenes

- **Descrição:** Método eficiente para encontrar todos os números primos até um limite n.
    
- **Passo a passo:**
    
      1.  Crie um array de booleanos de tamanho n+1 iniciado como verdadeiro.
          
      2.  Para cada número p começando de 2: se ele for verdadeiro, marque todos os seus múltiplos (2p,3p...) como falso.
          
      3.  Os índices que permanecerem verdadeiros são os primos.
    
- **Exemplo:** Entrada: 
    ```
    10
    ```
     | Saída: 
    ```
    [2, 3, 5, 7]
    ```
    .

### 47\. Todos os Divisores

- **Descrição:** Encontrar todos os números que dividem n sem deixar resto.
    
- **Passo a passo:**
    
      1.  Percorra apenas até n​. Se i divide n, então n/i também divide.
          
      2.  Guarde ambos os resultados para evitar percorrer a lista inteira.
    
- **Exemplo:** Entrada: 
    ```
    12
    ```
     | Saída: 
    ```
    [1, 2, 3, 4, 6, 12]
    ```
    .

### 48\. Fatoração em Primos

- **Descrição:** Expressar um número como produto de seus componentes primos (12\=22×3).
    
- **Passo a passo:**
    
      1.  Divida por 2 enquanto for possível.
          
      2.  Depois, tente dividir por números ímpares começando de 3 até n​.
    
- **Exemplo:** Entrada: 
    ```
    12
    ```
     | Saída: 
    ```
    2, 2, 3
    ```
    .

### 49\. Maior Fator Primo

- **Descrição:** Isolar o maior valor resultante da fatoração do exercício anterior.
    
- **Passo a passo:**
    
      1.  Execute a fatoração e mantenha uma variável 
          ```
          maior
          ```
           que é atualizada a cada divisão bem-sucedida.
    
- **Exemplo:** Entrada: 
    ```
    15
    ```
     | Saída: 
    ```
    5
    ```
    .

### 50\. Fatorial de um Número Grande

- **Descrição:** Calcular fatoriais como 100! que têm centenas de dígitos.
    
- **Passo a passo:**
    
      1.  Use um array onde cada posição guarda um único dígito do resultado.
          
      2.  Realize a multiplicação escolar: multiplique cada dígito pelo multiplicador e propague o "vai um".
    
- **Exemplo:** Entrada: 
    ```
    20
    ```
     | Saída: 
    ```
    2432902008176640000
    ```
    .

### 51\. Maior Potência Divisível em Fatoriais

- **Descrição:** Dado n! e um número k, qual o maior expoente x tal que kx divide n!?
    
- **Passo a passo:**
    
      1.  Se k for primo, use a fórmula de Legendre: ⌊n/k⌋+⌊n/k2⌋+...![]()  
          
      2.  Se k for composto, analise seus fatores primos separadamente.
    
- **Exemplo:** Entrada: 
    ```
    n=5, k=2
    ```
     | Saída: 
    ```
    3
    ```
    .

### 52\. Último Dígito Não Nulo do Fatorial

- **Descrição:** Encontrar o algarismo significativo mais à direita do resultado de um fatorial.
    
- **Passo a passo:**
    
      1.  Ignore os zeros finais (que vêm de pares de 2 e 5).
          
      2.  Como há mais fatores de 2 que de 5, foque em remover os 5 e reduzir os 2 proporcionalmente.
    
- **Exemplo:** Entrada: 
    ```
    5
    ```
     | Saída: 
    ```
    2
    ```
     (120 -> 2).

### 53\. Conjunto Potência (Power Set)

- **Descrição:** Gerar todos os subconjuntos possíveis de um conjunto dado.
    
- **Passo a passo:**
    
      1.  Para um conjunto de n elementos, existem 2n subconjuntos.
          
      2.  Use um contador binário de 0 a 2n−1. Se o bit j estiver ligado no contador, inclua o elemento j da lista no subconjunto atual.
    
- **Exemplo:** Entrada: 
    ```
    [1, 2]
    ```
     | Saída: 
    ```
    [[], [1], [2], [1, 2]]
    ```
    .

### 54\. Somar Dois Polinômios

- **Descrição:** Representar e somar expressões como 2x2+3x+5.
    
- **Passo a passo:**
    
      1.  Use arrays onde o índice representa a potência de x e o valor é o coeficiente.
          
      2.  Garanta que o array resultante tenha o tamanho do maior grau entre os dois polinômios.
    
- **Exemplo:** Entrada: 
    ```
    [1, 2] + [3, 4, 5]
    ```
     | Saída: 
    ```
    [4, 6, 5]
    ```
    .

### 55\. Todas as Permutações de uma String

- **Descrição:** Listar todas as combinações de ordem dos caracteres de uma palavra.
    
- **Passo a passo:**
    
      1.  Utilize **Backtracking**: fixe um caractere e permute recursivamente o restante.
          
      2.  Lembre-se de trocar os caracteres de volta (swap) ao retornar da recursão.
    
- **Exemplo:** Entrada: 
    ```
    ABC
    ```
     | Saída: 
    ```
    ABC, ACB, BAC, BCA, CAB, CBA
    ```
    .

### 56\. Próxima Permutação

- **Descrição:** Rearranjar os elementos para formar a próxima maior sequência em ordem alfabética.
    
- **Passo a passo:**
    
      1.  Encontre o primeiro par de elementos da direita para a esquerda onde o anterior é menor que o próximo.
          
      2.  Troque o anterior pelo menor valor maior que ele à sua direita.
          
      3.  Inverta a parte da direita para garantir a menor ordem possível.
    
- **Exemplo:** Entrada: 
    ```
    123
    ```
     | Saída: 
    ```
    132
    ```
    .

### 57\. Verificar Números de Carmichael

- **Descrição:** Números compostos que enganam o teste de Fermat, parecendo primos.
    
- **Passo a passo:**
    
      1.  Verifique se n é composto.
          
      2.  Para todo a tal que MDC(a,n)\=1, verifique se an−1%n\=1.
    
- **Exemplo:** Entrada: 
    ```
    561
    ```
     | Saída: 
    ```
    True
    ```
    .

### 58\. Sequência de Collatz

- **Descrição:** A "conjectura 3n + 1": comece com um número e siga as regras até chegar a 1.
    
- **Passo a passo:**
    
      1.  Repita enquanto n\>1: se par, n\=n/2; se ímpar, n\=3n+1.
          
      2.  Conte quantos passos foram necessários.
    
- **Exemplo:** Entrada: 
    ```
    3
    ```
     | Saída: 
    ```
    7
    ```
     passos (3, 10, 5, 16, 8, 4, 2, 1).

### 59\. Caminhos Únicos em Grade

- **Descrição:** Em uma grade M×N, quantos caminhos existem do início ao fim movendo-se apenas para baixo e para a direita?
    
- **Passo a passo:**
    
      1.  Use uma matriz de programação dinâmica onde cada célula é a soma da célula acima com a da esquerda.
          
      2.  O resultado final está no canto inferior direito.
    
- **Exemplo:** Entrada: 
    ```
    3x3
    ```
     | Saída: 
    ```
    6
    ```
    .

### 60\. Enésimo Número de Fibonacci Par

- **Descrição:** Isolar apenas os termos pares da sequência de Fibonacci.
    
- **Passo a passo:**
    
      1.  Note que os pares seguem a regra EF(n)\=4×EF(n−1)+EF(n−2).
          
      2.  Inicie com 2 e 8.
    
- **Exemplo:** Entrada: 
    ```
    3
    ```
     | Saída: 
    ```
    34
    ```
     (2, 8, 34, 144...).

### 61\. Últimos 2 Dígitos do Enésimo Fibonacci

- **Descrição:** Encontrar o resto da divisão por 100 de um número de Fibonacci muito distante.
    
- **Passo a passo:**
    
      1.  Use o fato de que os restos de Fibonacci se repetem (Período de Pisano).
          
      2.  Aplique 
          ```
          % 100
          ```
           em cada soma do laço para manter os números pequenos.
    
- **Exemplo:** Entrada: 
    ```
    10
    ```
     | Saída: 
    ```
    55
    ```
    .

</p>
</details>

<details>
  <summary>🔴 Nível 3 - Difícil</summary>

<p>

_Foco: Otimização extrema e conceitos avançados._

### 62\. Problema de Josephus

- **Descrição:** Um problema clássico de sobrevivência em círculo onde cada k-ésima pessoa é eliminada.
    
- **Passo a passo:**
    
      1.  Identifique a estrutura recursiva: a posição do sobrevivente em um grupo de n é a posição no grupo de n−1 deslocada por k posições.
          
      2.  Use a fórmula: f(n,k)\=(f(n−1,k)+k)%n.
    
- **Exemplo:** Entrada: 
    ```
    n=7, k=3
    ```
     | Saída: 
    ```
    4
    ```
     (assumindo índice começando em 1).

### 63\. Problema dos Jarros de Água

- **Descrição:** Medir uma quantidade exata de água usando jarros sem marcação.
    
- **Passo a passo:**
    
      1.  O problema é resolvível se a meta d for múltiplo do MDC(jarro1,jarro2).
          
      2.  Use uma busca em largura (BFS) para explorar os estados de volume nos jarros.
    
- **Exemplo:** Entrada: 
    ```
    jarros 3L e 5L, meta 4L
    ```
     | Saída: 
    ```
    True
    ```
    .

### 64\. Peneira Segmentada

- **Descrição:** Encontrar primos em um intervalo \[L,R\] onde R é muito grande para caber na memória, mas o intervalo R−L é pequeno.
    
- **Passo a passo:**
    
      1.  Pré-calcule primos até R​.
          
      2.  Crie um array do tamanho do intervalo. Use os primos pré-calculados para "riscar" seus múltiplos dentro do intervalo \[L,R\].
    
- **Exemplo:** Entrada: 
    ```
    [100, 120]
    ```
     | Saída: 
    ```
    [101, 103, 107, 109, 113]
    ```
    .

### 65\. k-ésimo Fator Primo

- **Descrição:** Qual o k-ésimo componente da fatoração de n?
    
- **Passo a passo:**
    
      1.  Execute a fatoração completa (Exercício 48).
          
      2.  Armazene os fatores em uma lista e retorne o índice solicitado.
    
- **Exemplo:** Entrada: 
    ```
    12, k=3
    ```
     | Saída: 
    ```
    3
    ```
     (Fatores: 2, 2, 3).

### 66\. N-ésima Raiz

- **Descrição:** Calcular nm​ com alta precisão.
    
- **Passo a passo:**
    
      1.  Use o **Método de Newton**: xnovo​\=n1​×((n−1)×xatual​+xatualn−1​m​).
          
      2.  Repita até que a diferença entre o chute anterior e o novo seja mínima.
    
- **Exemplo:** Entrada: 
    ```
    n=3, m=27
    ```
     | Saída: 
    ```
    3
    ```
    .

### 67\. Soma dos Dígitos no Fatorial

- **Descrição:** Combinar o cálculo de fatoriais gigantes com a soma de dígitos.
    
- **Passo a passo:**
    
      1.  Implemente o "Fatorial de Número Grande" (Exercício 50).
          
      2.  Percorra o array final somando todos os seus elementos.
    
- **Exemplo:** Entrada: 
    ```
    10
    ```
     | Saída: 
    ```
    27
    ```
    .

### 68\. Problema do Egg Dropping

- **Descrição:** Determinar o menor número de testes necessários para descobrir de qual andar um ovo quebra, considerando que você tem ovos limitados.
    
- **Passo a passo:**
    
      1.  Monte uma tabela de Programação Dinâmica onde DP\[ovos\]\[tentativas\] é o número máximo de andares que podemos testar.
          
      2.  A relação é: DP\[i\]\[j\]\=DP\[i−1\]\[j−1\]+DP\[i\]\[j−1\]+1.
    
- **Exemplo:** Entrada: 
    ```
    2 ovos, 10 andares
    ```
     | Saída: 
    ```
    4
    ```
    .

### 69\. Próxima String (Lexicográfica)

- **Descrição:** Qual a menor string que vem logo após a atual no dicionário?
    
- **Passo a passo:**
    
      1.  Trate a string como um número em base 26.
          
      2.  Incremente o último caractere. Se passar de 'z', vire 'a' e leve o carry para o caractere anterior.
    
- **Exemplo:** Entrada: 
    ```
    abc
    ```
     | Saída: 
    ```
    abd
    ```
    .

**Dica para Estudos:** Ao implementar, tente primeiro a solução mais óbvia e depois procure a otimização matemática para entender por que alguns algoritmos são milhares de vezes mais rápidos que outros.

</p>
</details>
