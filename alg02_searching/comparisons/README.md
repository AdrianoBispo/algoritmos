# Comparações entre Diferentes Algoritmos de Busca
- [Pesquisa Linear vs Pesquisa Binária](#linear-vs-binaria)
- [Pesquisa de interpolação vs pesquisa binária](#interpolacao-vs-binaria)
- [Por que a Busca Binária é preferível à Busca Ternária?](#binaria-vs-ternaria)
- [A Busca Linear do Sentinel é melhor que a Busca Linear normal?](#linearSentinel-vs-linearNormal)

<h2 id="linear-vs-binaria">Algoritmo de Busca Linear vs Algoritmo de Busca Binária</h2>

**Pré-requisito:**
- [Busca Linear](../linear_search)
- [Busca Binária](../binary_search)

### Busca Linear
Suponha que o item esteja em um array em ordem aleatória e temos que encontrar um item. Então a única maneira de
procurar um item alvo é, para começar, a primeira posição e compará-lo ao alvo. Se o item estiver na mesma, retornaremos
a posição do item atual. Caso contrário, moveremos para a próxima posição. Se chegarmos à última posição de um array e
ainda não conseguirmos encontrar o alvo, retornamos -1. Isso é chamado de busca Linear ou Busca Sequencial.

#### Abaixo está a sintaxe do código para a busca linear:

```Java
/*package whatever //do not write package name here */

import java.io.*;

class Main {
    public static int liner(int arr[], int x) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == x)
                return i;
        }
        return -1;
    }
}
```

### Busca Binária
Em uma busca binária, no entanto, reduza sua busca pela metade assim que encontrar o meio de uma lista ordenada. O
elemento do meio é olhado para verificar se é maior ou menor que o valor a ser pesquisado. Consequentemente, uma busca é
feita em metade da lista fornecida.

#### Abaixo está a sintaxe do código para a pesquisa binária.:

```Java
/*package whatever //do not write package name here */

class GFG {
    public static int binary(int[] arr, int x) {
        int start = 0;
        int end = arr.length - 1;
        while (start <= end) {
            int mid = (start + end) / 2;
            if (x == arr[mid]) {
                return mid;
            } else if (x > arr[mid]) {
                start = mid + 1;
            } else {
                end = mid - 1;
            }
        }
        return -1;
    }
}
```

### Diferenças Importantes

| **Busca Linear**                                                        | **Busca Binária**                                                              |
|-------------------------------------------------------------------------|--------------------------------------------------------------------------------|
| Na pesquisa linear, os dados de entrada não precisam ser classificados. | Na pesquisa binária, os dados de entrada precisam estar em ordem classificada. |
| Também é chamada de busca sequencial.                                   | Também é chamada de busca de meio intervalo.                                   |
| A complexidade temporal da busca linear O(n).                           | A complexidade temporal da busca binária O(log n).                             |
| É possível usar uma matriz multidimensional.                            | Somente uma matriz unidimensional é usada.                                     |
| A pesquisa linear realiza comparações de igualdade.                     | A pesquisa binária realiza comparações de ordenação.                           |
| É menos complexo.                                                       | É mais complexo.                                                               |
| É um processo muito lento.                                              | É um processo muito rápido.                                                    |

### Vejamos um exemplo para comparar os dois:

**Busca linear para encontrar o elemento “J” em uma lista ordenada dada de AX**
![Linear.png](https://media.geeksforgeeks.org/wp-content/uploads/Linear.png)

**Pesquisa binária para encontrar o elemento “J” em uma lista ordenada dada de AX**
![binary-3.png](https://media.geeksforgeeks.org/wp-content/uploads/binary-3.png)

<h2 id="interpolacao-vs-binaria">Algoritmo de Busca de Interpolação vs Algoritmo de Busca Binária</h2>

A **Busca Binária** e a **Busca de Interpolação** são algoritmos de pesquisa eficientes para encontrar um valor em um
array ordenado. No entanto, elas se comportam de maneira diferente dependendo das características dos dados. Vamos
detalhar cada uma delas, comparando seu desempenho e fornecendo exemplos de implementação em Java.

### 1. Busca Binária
A **Busca Binária** é um algoritmo que divide repetidamente o array ordenado ao meio até encontrar o valor desejado. O
desempenho da busca binária é ótimo quando os dados estão ordenados, já que a cada iteração o número de elementos a
serem analisados diminui pela metade.

#### Complexidade:
- **Tempo**: O(log n), onde `n` é o número de elementos no array.
- **Espaço**: O(1), pois a busca binária usa apenas uma quantidade constante de memória extra.

#### Como funciona:
1. Inicia-se com os índices de início e fim do array.
2. Calcula-se o índice médio.
3. Se o valor procurado for igual ao valor no índice médio, o algoritmo retorna esse índice.
4. Caso contrário, decide-se se o valor procurado está à esquerda ou à direita do índice médio, ajustando os limites de
   busca.

#### Exemplo de Implementação em Java:

```java
public class BuscaBinaria {
    public static int buscaBinaria(int[] arr, int alvo) {
        int inicio = 0;
        int fim = arr.length - 1;

        while (inicio <= fim) {
            int meio = inicio + (fim - inicio) / 2;

            // Verifica se o alvo está no meio
            if (arr[meio] == alvo) {
                return meio;
            }

            // Se o alvo for maior, ignore a metade esquerda
            if (arr[meio] < alvo) {
                inicio = meio + 1;
            }
            // Se o alvo for menor, ignore a metade direita
            else {
                fim = meio - 1;
            }
        }

        // Se o alvo não for encontrado, retorna -1
        return -1;
    }

    public static void main(String[] args) {
        int[] arr = {1, 3, 5, 7, 9, 11, 13};
        int alvo = 7;
        int resultado = buscaBinaria(arr, alvo);
        System.out.println("Índice do alvo: " + resultado);
    }
}
```

### 2. Busca de Interpolação
A **Busca de Interpolação** é uma variação da busca binária, que tenta prever a posição do valor desejado com base no
valor da chave. Em vez de sempre dividir o array ao meio como na busca binária, a busca de interpolação usa uma fórmula
matemática para calcular uma posição "estimada" que pode ser mais próxima do valor procurado, se os dados forem
distribuídos uniformemente.

#### Complexidade:
- **Tempo**: O(log log n) no melhor caso (para distribuições uniformemente distribuídas), mas no pior caso pode ser O(n)
  se os dados não forem uniformemente distribuídos.
- **Espaço**: O(1), já que utiliza apenas uma quantidade constante de memória extra.

#### Como funciona:
1. Inicia-se com os índices de início e fim do array.
2. Calcula-se a posição estimada usando a fórmula:
   \[
   \text{pos} = \text{inicio} + \frac{(alvo - arr[inicio]) \times (\text{fim} - \text{inicio})}{arr[fim] - arr[inicio]}
   \]
3. Se o valor da posição estimada for igual ao valor procurado, retorna-se esse índice.
4. Se o valor estimado for maior ou menor que o valor procurado, ajusta-se os limites de busca.

#### Exemplo de Implementação em Java:

```java
public class BuscaInterpolacao {
    public static int buscaInterpolacao(int[] arr, int alvo) {
        int inicio = 0;
        int fim = arr.length - 1;

        while (inicio <= fim && alvo >= arr[inicio] && alvo <= arr[fim]) {
            // Estima a posição com base na interpolação
            int pos = inicio + ((alvo - arr[inicio]) * (fim - inicio)) / (arr[fim] - arr[inicio]);

            // Verifica se encontramos o alvo
            if (arr[pos] == alvo) {
                return pos;
            }

            // Se o alvo for maior, ignore a parte esquerda
            if (arr[pos] < alvo) {
                inicio = pos + 1;
            }
            // Se o alvo for menor, ignore a parte direita
            else {
                fim = pos - 1;
            }
        }

        // Se o alvo não for encontrado, retorna -1
        return -1;
    }

    public static void main(String[] args) {
        int[] arr = {1, 3, 5, 7, 9, 11, 13};
        int alvo = 7;
        int resultado = buscaInterpolacao(arr, alvo);
        System.out.println("Índice do alvo: " + resultado);
    }
}
```

### Comparação entre Busca Binária e Busca de Interpolação

#### 1. **Eficiência e Complexidade**:
- **Busca Binária**: A busca binária tem uma complexidade de O(log n), o que a torna muito eficiente para arrays
  grandes.
- **Busca de Interpolação**: Em seu melhor caso (dados uniformemente distribuídos), a complexidade pode ser O(log log
  n). No entanto, no pior caso, ela pode se degradar para O(n) caso os dados não sejam distribuídos uniformemente.

#### 2. **Desempenho em Dados Não Uniformes**:
- **Busca Binária**: Funciona bem em qualquer distribuição de dados, desde que o array esteja ordenado.
- **Busca de Interpolação**: Desempenha melhor quando os dados estão distribuídos de forma uniforme. Em casos de dados
  não uniformemente distribuídos, a busca de interpolação pode ser ineficiente e até mais lenta do que a busca binária.

#### 3. **Custo Computacional**:
- **Busca Binária**: O cálculo de "meio" é simples e rápido.
- **Busca de Interpolação**: O cálculo da posição estimada é mais complexo, mas pode ser mais eficiente se os dados
  forem uniformemente distribuídos.

#### 4. **Uso de Memória**:
Ambos os algoritmos possuem complexidade de espaço O(1), ou seja, não há diferença significativa no uso de memória.

#### 5. **Aplicabilidade**:
- **Busca Binária**: Mais segura e universal. Funciona bem para qualquer tipo de dados ordenados.
- **Busca de Interpolação**: Ideal quando se tem uma distribuição uniforme ou quase uniforme de dados, mas não é tão
  robusta em cenários mais gerais.

### Conclusão
- **Melhor escolha em termos de segurança e eficiência geral**: **Busca Binária**, pois é mais confiável e tem um
  desempenho estável, independentemente da distribuição dos dados.
- **Melhor escolha para distribuições uniformes**: **Busca de Interpolação**, pois ela pode ter um desempenho
  ligeiramente melhor em dados uniformemente distribuídos.

<h2 id="binaria-vs-ternaria">Por que a Busca Binária é preferível à Busca Ternária?</h2>

A Busca Binária é frequentemente preferida em relação à Busca Ternária devido a vários fatores, principalmente em termos
de eficiência e simplicidade. Aqui estão algumas razões pelas quais a Busca Binária costuma ser a escolha preferida:

### 1. **Busca Binária em Java**
A implementação da **Busca Binária** envolve verificar o valor médio da lista em cada iteração e ajustar os limites até
encontrar o valor ou esgotar a lista.

```java
public class BuscaBinaria {

    // Função para realizar a busca binária
    public static int buscaBinaria(int[] arr, int alvo) {
        int esquerda = 0;
        int direita = arr.length - 1;

        while (esquerda <= direita) {
            int meio = esquerda + (direita - esquerda) / 2;  // Evita overflow

            // Verifica se o alvo é o valor no meio
            if (arr[meio] == alvo) {
                return meio;  // Retorna o índice do valor encontrado
            }
            // Se o alvo for menor, ignora a metade direita
            if (arr[meio] > alvo) {
                direita = meio - 1;
            } else {
                // Se o alvo for maior, ignora a metade esquerda
                esquerda = meio + 1;
            }
        }

        return -1;  // Retorna -1 se o valor não for encontrado
    }

    public static void main(String[] args) {
        int[] arr = {1, 3, 5, 7, 9, 11, 13, 15, 17, 19};  // Lista ordenada
        int alvo = 7;

        int resultado = buscaBinaria(arr, alvo);
        System.out.println("Índice do valor encontrado: " + resultado);  // Esperado: 3
    }
}
```

#### Características da **Busca Binária**:
- A busca binária funciona dividindo a lista ao meio em cada iteração.
- A complexidade de tempo é **O(log n)**.
- Exige **apenas uma comparação** por iteração.
- A implementação é simples e direta.

---

### 2. **Busca Ternária em Java**
A **Busca Ternária** divide a lista em três partes, comparando o valor desejado com dois pontos no meio da lista, e
ajustando os limites com base nessas comparações.

```java
public class BuscaTernaria {

    // Função para realizar a busca ternária
    public static int buscaTernaria(int[] arr, int alvo) {
        return buscaTernariaRecursiva(arr, alvo, 0, arr.length - 1);
    }

    private static int buscaTernariaRecursiva(int[] arr, int alvo, int esquerda, int direita) {
        if (esquerda <= direita) {
            // Calculando os pontos intermediários
            int terco1 = esquerda + (direita - esquerda) / 3;
            int terco2 = direita - (direita - esquerda) / 3;

            // Verifica se o alvo é um dos pontos intermediários
            if (arr[terco1] == alvo) {
                return terco1;
            }
            if (arr[terco2] == alvo) {
                return terco2;
            }

            // Decide qual parte da lista procurar
            if (alvo < arr[terco1]) {
                return buscaTernariaRecursiva(arr, alvo, esquerda, terco1 - 1);  // Procura na primeira parte
            } else if (alvo > arr[terco2]) {
                return buscaTernariaRecursiva(arr, alvo, terco2 + 1, direita);  // Procura na terceira parte
            } else {
                return buscaTernariaRecursiva(arr, alvo, terco1 + 1, terco2 - 1);  // Procura na segunda parte
            }
        }
        return -1;  // Retorna -1 se o valor não for encontrado
    }

    public static void main(String[] args) {
        int[] arr = {1, 3, 5, 7, 9, 11, 13, 15, 17, 19};  // Lista ordenada
        int alvo = 7;

        int resultado = buscaTernaria(arr, alvo);
        System.out.println("Índice do valor encontrado: " + resultado);  // Esperado: 3
    }
}
```

#### Características da **Busca Ternária**:
- A busca ternária divide a lista em três partes, realizando duas comparações por iteração.
- A complexidade de tempo é **O(log₃ n)**, mas na prática, o ganho em desempenho é muito pequeno.
- Exige **duas comparações** por iteração.
- A implementação é um pouco mais complexa devido à necessidade de dividir a lista em três partes.

---

### 3. **Comparação Detalhada**

#### a. **Complexidade de Tempo**
- **Busca Binária**: A complexidade de tempo é **O(log n)**, já que a cada iteração a lista é dividida ao meio.
- **Busca Ternária**: A complexidade de tempo é **O(log₃ n)**, o que é ligeiramente mais eficiente teoricamente, pois o
  número de elementos é dividido em três partes, mas a diferença é marginal em termos de desempenho prático.

**Nota**: Embora O(log₃ n) seja mais "rápido" do que O(log n) em termos de crescimento assintótico, a constante
implícita e a sobrecarga adicional de duas comparações por iteração tornam a **Busca Binária** mais eficiente na
prática.

#### b. **Número de Comparações**
- **Busca Binária**: Em cada iteração, apenas **uma comparação** é feita (com o valor médio).
- **Busca Ternária**: Em cada iteração, **duas comparações** são feitas (com dois pontos médios).

Embora a Busca Ternária divida a lista mais rapidamente, o número de comparações adicionais pode afetar o desempenho em
listas muito grandes.

#### c. **Simplicidade e Implementação**
- **Busca Binária**: A implementação da Busca Binária é mais simples, fácil de entender e menos propensa a erros, com
  apenas um ponto médio a ser calculado por iteração.
- **Busca Ternária**: A Busca Ternária exige duas comparações por iteração e uma lógica um pouco mais complexa para
  determinar qual parte da lista continuar a busca. A implementação é mais difícil e o código é mais longo.

#### d. **Memória**
- Ambas as abordagens possuem **complexidade de espaço** O(1), ou seja, ambas ocupam uma quantidade constante de
  memória, já que não exigem estruturas adicionais além das variáveis de índice.

#### e. **Eficiência na Prática**
- **Busca Binária** é mais eficiente na prática devido ao menor número de comparações.
- **Busca Ternária** tem uma ligeira vantagem teórica em termos de número de iterações, mas a sobrecarga de comparações
  e a complexidade extra tornam a **Busca Binária** mais eficaz.

---

### Conclusão:
- **Busca Binária** é preferida na maioria das situações devido à sua simplicidade, maior eficiência em termos de
  comparações e facilidade de implementação.
- **Busca Ternária** pode ser útil em casos muito específicos onde você deseja dividir a lista de forma mais
  equilibrada, mas a sobrecarga extra de comparações torna-a menos eficiente na prática para listas grandes.

Em resumo, **Busca Binária** é geralmente mais rápida e simples, sendo a escolha preferencial em implementações de busca
em listas ordenadas.

<h2 id="linearSentinel-vs-linearNormal">A Busca Linear do Sentinel é melhor que a Busca Linear Normal?</h2>

A **Busca Linear** e a **Busca Linear com Sentinel** são duas variações do mesmo conceito de pesquisa em um array, onde
o objetivo é localizar um valor em uma sequência de elementos. Vamos analisar as diferenças entre as duas abordagens,
detalhar suas implementações em Java e compará-las em termos de eficiência.

### 1. **Busca Linear Normal**
A **Busca Linear** é o algoritmo mais simples de busca. Ele percorre todos os elementos do array, um a um, até encontrar
o valor procurado ou até terminar a busca sem sucesso. Esse algoritmo não exige que o array esteja ordenado e, portanto,
pode ser utilizado para qualquer tipo de dado.

#### Complexidade:
- **Tempo**: O(n), onde `n` é o número de elementos no array.
- **Espaço**: O(1), pois não requer memória adicional.

#### Como funciona:
1. Começa no primeiro elemento do array e vai até o último, verificando se o valor procurado está presente.
2. Se o valor for encontrado, o índice correspondente é retornado.
3. Se o valor não for encontrado após percorrer todo o array, retorna-se um valor indicativo de que o elemento não foi
   encontrado (como `-1`).

#### Exemplo de Implementação em Java (Busca Linear Normal):

```java
public class BuscaLinear {
    public static int buscaLinear(int[] arr, int alvo) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == alvo) {
                return i; // Retorna o índice onde o alvo foi encontrado
            }
        }
        return -1; // Retorna -1 se o alvo não for encontrado
    }

    public static void main(String[] args) {
        int[] arr = {2, 4, 6, 8, 10};
        int alvo = 6;
        int resultado = buscaLinear(arr, alvo);
        System.out.println("Índice do alvo: " + resultado);
    }
}
```

### 2. **Busca Linear com Sentinel**
A **Busca Linear com Sentinel** é uma variação da busca linear normal, em que adicionamos um **sentinela** ao final do
array. O sentinela é um valor especial, que garante que a busca sempre encontrará o alvo ou determinará o fim da
pesquisa sem precisar de uma verificação adicional no final de cada iteração.

#### Complexidade:
- **Tempo**: O(n), onde `n` é o número de elementos no array.
- **Espaço**: O(1), já que o algoritmo não requer memória extra além do array original (exceto pelo sentinela).

#### Como funciona:
1. Coloca-se o valor procurado (sentinela) no final do array, aumentando a segurança de não precisar fazer uma
   comparação adicional após o loop.
2. O algoritmo então percorre o array, comparando os elementos com o valor procurado.
3. O loop termina quando o sentinela (valor especial) é encontrado, garantindo que o valor procurado não seja perdido
   por uma comparação extra.
4. Ao final, se o valor procurado for encontrado, o índice correspondente é retornado.

#### Exemplo de Implementação em Java (Busca Linear com Sentinel):

```java
public class BuscaLinearSentinel {
    public static int buscaLinearSentinel(int[] arr, int alvo) {
        int n = arr.length;
        int sentinela = alvo; // Coloca o valor procurado como sentinela
        int temp = arr[n - 1]; // Salva o último valor do array
        arr[n - 1] = sentinela; // Coloca o sentinela no final do array

        int i = 0;
        while (arr[i] != sentinela) {
            if (arr[i] == alvo) {
                arr[n - 1] = temp; // Restaura o último valor do array
                return i; // Retorna o índice do valor procurado
            }
            i++;
        }

        arr[n - 1] = temp; // Restaura o último valor do array
        return -1; // Retorna -1 se o alvo não for encontrado
    }

    public static void main(String[] args) {
        int[] arr = {2, 4, 6, 8, 10};
        int alvo = 6;
        int resultado = buscaLinearSentinel(arr, alvo);
        System.out.println("Índice do alvo: " + resultado);
    }
}
```

### Comparação entre Busca Linear e Busca Linear com Sentinel

#### 1. **Desempenho e Complexidade de Tempo**
- **Busca Linear Normal**: Tem complexidade **O(n)**, o que significa que o tempo de execução aumenta linearmente com o
  tamanho do array. Em cada iteração, há uma verificação se o índice atual é o valor procurado.
- **Busca Linear com Sentinel**: Também tem complexidade **O(n)**, mas pode ser ligeiramente mais eficiente em termos de
  número de comparações, porque elimina a necessidade de uma verificação extra após o loop, que seria necessária na
  busca linear normal para verificar se o alvo foi encontrado ou não.

#### 2. **Número de Comparações**
- **Busca Linear Normal**: Faz **n + 1** comparações no pior caso (se o valor não for encontrado), uma a mais para
  verificar se o índice atual é o último do array.
- **Busca Linear com Sentinel**: A busca é interrompida assim que o sentinela é encontrado. No pior caso, o número de
  comparações é **n**, mas como não há uma verificação adicional após o loop, ela pode ser ligeiramente mais eficiente.

#### 3. **Espaço**
- **Busca Linear Normal**: Utiliza O(1) de espaço extra.
- **Busca Linear com Sentinel**: Embora o algoritmo utilize O(1) de espaço extra, a modificação do array (adicionando o
  sentinela) requer um pequeno uso de memória adicional para a variável do sentinela e para restaurar o valor do último
  elemento após a pesquisa.

#### 4. **Facilidade de Implementação**
- **Busca Linear Normal**: É mais simples e direta, sem necessidade de manipulação extra do array.
- **Busca Linear com Sentinel**: Exige um pouco mais de complexidade, já que envolve modificar o array temporariamente (
  adicionar o sentinela) e restaurar o valor original no final.

#### 5. **Casos de Uso**
- **Busca Linear Normal**: Pode ser usada quando a implementação simples é preferível ou quando o array é pequeno, ou
  ainda quando não é necessário otimizar o número de comparações.
- **Busca Linear com Sentinel**: É útil quando você deseja otimizar a quantidade de comparações feitas (principalmente
  em arrays grandes) e tem um pequeno custo adicional em termos de complexidade.

### Conclusão
- **Busca Linear Normal** é uma implementação mais simples, mais direta e eficaz quando você está lidando com um pequeno
  número de elementos ou quando não precisa se preocupar com otimizações de desempenho mínimas.
- **Busca Linear com Sentinel** pode ser ligeiramente mais eficiente, já que reduz o número de comparações feitas no
  loop, mas adiciona um pouco de complexidade no código devido ao uso do sentinela e à modificação temporária do array.

Em termos gerais, a **Busca Linear com Sentinel** pode ser considerada uma pequena melhoria de desempenho em cenários
onde o número de comparações é um fator importante, especialmente em arrays grandes. Para a maioria dos casos práticos,
no entanto, a **Busca Linear Normal** pode ser suficiente.

### Links de Referências
- [Busca Linear vs Busca Binária](https://www.geeksforgeeks.org/linear-search-vs-binary-search/)
- [Busca de Interpolação vs Busca Binária](https://www.geeksforgeeks.org/g-fact-84/)
- [Por que a Busca Binária é Preferível à Busca Ternária?](https://www.geeksforgeeks.org/binary-search-preferred-ternary-search/)
- [A Busca Linear do Sentinel é melhor que a Busca Linear normal?](https://www.geeksforgeeks.org/is-sentinel-linear-search-better-than-normal-linear-search/)
