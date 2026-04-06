# Algoritmo de Busca por Salto

Assim como a Binary Search , a Jump Search é um algoritmo de busca para matrizes ordenadas. A ideia básica é verificar
menos elementos (do que a busca linear ) pulando à frente por etapas fixas ou pulando alguns elementos em vez de
pesquisar todos os elementos.

Por exemplo, suponha que temos uma matriz arr[] de tamanho n e um bloco (a ser saltado) de tamanho m. Então, buscamos
nos índices arr[0], arr[m], arr[2m]…..arr[km], e assim por diante. Uma vez que encontramos o intervalo (arr[km] < x <
arr[(k+1)m]), realizamos uma operação de busca linear a partir do índice km para encontrar o elemento x.

## Etapas do Algoritmo

- Jump Search é um algoritmo para encontrar um valor específico em uma matriz classificada, saltando por determinados
  passos na matriz.
- Os passos são determinados pelo sqrt do comprimento da matriz.
- Aqui está um algoritmo passo a passo para a busca de salto:
- Determine o tamanho do passo m tomando o quadrado do comprimento da matriz n.
- Comece no primeiro elemento do array e pule m passos até que o valor naquela posição seja maior que o valor alvo.
- Uma vez que um valor maior que o alvo seja encontrado, execute uma busca linear começando do passo anterior até que o
  alvo seja encontrado ou fique claro que o alvo não está no array.
- Se o alvo for encontrado, retorne seu índice. Se não, retorne -1 para indicar que o alvo não foi encontrado no array.

**Exemplo de Aplicação com Java**

```Java
// Java program to implement Jump Search.
public class JumpSearch {
    public static int jumpSearch(int[] arr, int x) {
        int n = arr.length;

        // Finding block size to be jumped
        int step = (int) Math.floor(Math.sqrt(n));

        // Finding the block where element is
        // present (if it is present)
        int prev = 0;
        for (int minStep = Math.min(step, n) - 1; arr[minStep] < x; minStep = Math.min(step, n) - 1) {
            prev = step;
            step += (int) Math.floor(Math.sqrt(n));
            if (prev >= n)
                return -1;
        }

        // Doing a linear search for x in block
        // beginning with prev.
        while (arr[prev] < x) {
            prev++;

            // If we reached next block or end of
            // array, element is not present.
            if (prev == Math.min(step, n))
                return -1;
        }

        // If element is found
        if (arr[prev] == x)
            return prev;

        return -1;
    }

    // Driver program to test function
    public static void main(String[] args) {
        int arr[] = {0, 1, 1, 2, 3, 5, 8, 13, 21,
                34, 55, 89, 144, 233, 377, 610};
        int x = 55;

        // Find the index of 'x' using Jump Search
        int index = jumpSearch(arr, x);

        // Print the index where 'x' is located
        System.out.println("\nNumber " + x +
                " is at index " + index);
    }
}
```


