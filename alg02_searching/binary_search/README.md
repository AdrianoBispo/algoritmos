![binnary-search-.webp](https://media.geeksforgeeks.org/wp-content/uploads/20240506155201/binnary-search-.webp)

A busca binária é um algoritmo de busca usado para encontrar a posição de um valor alvo dentro de uma matriz ordenada .
Ele funciona dividindo repetidamente o intervalo de busca pela metade até que o valor alvo seja encontrado ou o
intervalo esteja vazio. O intervalo de busca é dividido pela metade comparando o elemento alvo com o valor do meio do
espaço de busca.

## Variações do Algoritmo de Busca Linear
- [Meta Busca Binária]()
- [Busca Binária Unilateral]()
- [Busca Binária Onipresente]()

## Condições para aplicar o Algoritmo de Busca Binária em uma Estrutura de Dados

Para aplicar o algoritmo de busca binária:

- A estrutura de dados deve ser classificada.
- O acesso a qualquer elemento da estrutura de dados deve levar um tempo constante.

## Passo a Passo para Implementação do Algoritmo de Busca Binária

- Divida o espaço de busca em duas metades encontrando o índice do meio “mid” .
- Compare o elemento do meio do espaço de busca com a **chave** .
- Se a chave for encontrada no elemento do meio, o processo será encerrado.
- Se a chave não for encontrada no elemento do meio, escolha qual metade será usada como o próximo espaço de busca.
    - **Se a chave for menor** que o elemento do meio, **o lado esquerdo será usado** para a próxima pesquisa.
    - **Se a chave for maior** que o elemento do meio, **o lado direito será usado** para a próxima pesquisa.
- Esse processo continua até que a chave seja encontrada ou o espaço total de busca seja esgotado.

## Como funciona o Algoritmo de Busca Binária?

Para entender o funcionamento da busca binária, considere a seguinte ilustração:

Considere uma array `arr[] = {2, 5, 8, 12, 16, 23, 38, 56, 72, 91}` e o **alvo = 23** .
![Binary-Search-1.webp](https://media.geeksforgeeks.org/wp-content/uploads/20250219155359690903/Binary-Search-1.webp)
![Binary-Search-2.webp](https://media.geeksforgeeks.org/wp-content/uploads/20250219155359020153/Binary-Search-2.webp)
![Binary-Search-3.webp](https://media.geeksforgeeks.org/wp-content/uploads/20250219155358414164/Binary-Search-3.webp)
![Binary-Search-4.png](https://media.geeksforgeeks.org/wp-content/uploads/20250219155357890968/Binary-Search-4.png)

## Como implementar o algoritmo de busca binária?

O **Algoritmo de Busca Binária** pode ser implementado das duas maneiras a seguir

- Algoritmo de busca binária iterativa
- Algoritmo de busca binária recursiva

### Algoritmo de busca binária iterativa:

Aqui usamos um loop while para continuar o processo de comparação da chave e divisão do espaço de busca em duas metades.

```Java
// Java implementation of iterative Binary Search

import java.io.*;

class BinarySearch {

    // Returns index of x if it is present in arr[].
    int binarySearch(int arr[], int x) {
        int low = 0, high = arr.length - 1;
        while (low <= high) {
            int mid = low + (high - low) / 2;

            // Check if x is present at mid
            if (arr[mid] == x)
                return mid;

            // If x greater, ignore left half
            if (arr[mid] < x)
                low = mid + 1;

                // If x is smaller, ignore right half
            else
                high = mid - 1;
        }

        // If we reach here, then element was
        // not present
        return -1;
    }

    // Driver code
    public static void main(String args[]) {
        BinarySearch ob = new BinarySearch();
        int arr[] = {2, 3, 4, 10, 40};
        int n = arr.length;
        int x = 10;
        int result = ob.binarySearch(arr, x);
        if (result == -1)
            System.out.println(
                    "Element is not present in array");
        else
            System.out.println("Element is present at "
                    + "index " + result);
    }
}
```

**OUTPUT:** `Element is present at index 3`

### Algoritmo de busca binária recursiva:

Crie uma função recursiva e compare o meio do espaço de busca com a chave. E com base no resultado, retorne o índice
onde a chave é encontrada ou chame a função recursiva para o próximo espaço de busca.

```Java
// Java implementation of recursive Binary Search
class BinarySearch {

    // Returns index of x if it is present in arr[low..
    // high], else return -1
    int binarySearch(int arr[], int low, int high, int x) {
        if (high >= low) {
            int mid = low + (high - low) / 2;

            // If the element is present at the
            // middle itself
            if (arr[mid] == x)
                return mid;

            // If element is smaller than mid, then
            // it can only be present in left subarray
            if (arr[mid] > x)
                return binarySearch(arr, low, mid - 1, x);

            // Else the element can only be present
            // in right subarray
            return binarySearch(arr, mid + 1, high, x);
        }

        // We reach here when element is not present
        // in array
        return -1;
    }

    // Driver code
    public static void main(String args[]) {
        BinarySearch ob = new BinarySearch();
        int arr[] = {2, 3, 4, 10, 40};
        int n = arr.length;
        int x = 10;
        int result = ob.binarySearch(arr, 0, n - 1, x);
        if (result == -1)
            System.out.println(
                    "Element is not present in array");
        else
            System.out.println(
                    "Element is present at index " + result);
    }
}
```

**OUTPUT:** `Element is present at index 3`

## Análise de Complexidade

- **Complexidade de tempo:**
    - **Melhor caso:** O(1)
    - **Caso médio:** O(log N)
    - **Pior caso:** O(log N)
- **Espaço Auxiliar:** O(1), Se a pilha de chamadas recursiva for considerada, o espaço auxiliar será O(logN).

## Aplicações do Algoritmo de Busca Binária

- A busca binária pode ser usada como um bloco de construção para algoritmos mais complexos usados ​​em aprendizado de
  máquina, como algoritmos para treinar redes neurais ou encontrar os hiperparâmetros ideais para um modelo.
- Ele pode ser usado para pesquisas em computação gráfica, como algoritmos para traçado de raios ou mapeamento de
  texturas.
- Pode ser usado para pesquisar em um banco de dados.

## Vantagens da Pesquisa Binária

- A pesquisa binária é mais rápida que a pesquisa linear, especialmente para matrizes grandes.
- Mais eficiente do que outros algoritmos de busca com complexidade de tempo semelhante, como busca de interpolação ou
  busca exponencial.
- A pesquisa binária é adequada para pesquisar grandes conjuntos de dados armazenados na memória externa, como em um
  disco rígido ou na nuvem.

## Desvantagens da Pesquisa Binária

- A matriz deve ser classificada.
- A pesquisa binária exige que a estrutura de dados pesquisada seja armazenada em locais de memória contíguos.
- A busca binária exige que os elementos da matriz sejam comparáveis, o que significa que eles devem poder ser
  ordenados.

## Dúvidas

### A pesquisa binária pode ser aplicada a dados não numéricos?

Sim, a busca binária pode ser aplicada a dados não numéricos, desde que haja uma ordem definida para os elementos. Por
exemplo, ela pode ser usada para buscar strings em ordem alfabética.

### Quando a Pesquisa Binária deve ser usada?

A busca binária deve ser usada ao procurar um valor alvo em uma matriz ordenada, especialmente quando o tamanho da
matriz é grande. Ela é particularmente eficiente para grandes conjuntos de dados em comparação com algoritmos de busca
linear.

### A busca binária é sempre a melhor escolha para pesquisar em uma matriz ordenada?

Embora a pesquisa binária seja muito eficiente para pesquisar em matrizes classificadas, pode haver casos específicos em
que outros algoritmos de pesquisa sejam mais apropriados, como ao lidar com pequenos conjuntos de dados ou quando a
matriz é modificada com frequência.