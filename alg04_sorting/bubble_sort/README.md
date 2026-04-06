# Algoritmo de Ordenação: Bubble Sort

Bubble Sort é o algoritmo de classificação mais simples que funciona trocando repetidamente os elementos adjacentes se
eles estiverem na ordem errada. Este algoritmo não é adequado para grandes conjuntos de dados, pois sua complexidade de
tempo média e de pior caso são bem altas.

Classificamos o array usando múltiplas passagens. Após a primeira passagem, o elemento máximo vai para o final (sua
posição correta). Da mesma forma, após a segunda passagem, o segundo maior elemento vai para a penúltima posição e assim
por diante.
Em cada passagem, processamos apenas aqueles elementos que ainda não foram movidos para a posição correta. Após k
passagens, os maiores k elementos devem ter sido movidos para as últimas k posições.
Em uma passagem, consideramos os elementos restantes e comparamos todos os adjacentes e trocamos se o elemento maior
estiver antes de um elemento menor. Se continuarmos fazendo isso, obtemos o maior (entre os elementos restantes) em sua
posição correta.

## Como funciona o Bubble Sort?

![image](https://media.geeksforgeeks.org/wp-content/uploads/20240925153535/bubble-sort-1.webp)
![image](https://media.geeksforgeeks.org/wp-content/uploads/20240925153536/bubble-sort-2.webp)
![image](https://media.geeksforgeeks.org/wp-content/uploads/20240925153536/bubble-sort-3.webp)

Abaixo está a implementação do bubble sort utilizando a linguagem Java. Ele pode ser otimizado parando o algoritmo se o
loop interno não causou nenhuma troca.

```Java
// Optimized java implementation of Bubble sort

import java.io.*;

class GFG {

    // An optimized version of Bubble Sort
    static void bubbleSort(int arr[], int n) {
        int i, j, temp;
        boolean swapped;
        for (i = 0; i < n - 1; i++) {
            swapped = false;
            for (j = 0; j < n - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {

                    // Swap arr[j] and arr[j+1]
                    temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                    swapped = true;
                }
            }

            // If no two elements were
            // swapped by inner loop, then break
            if (swapped == false)
                break;
        }
    }

    // Function to print an array
    static void printArray(int arr[], int size) {
        int i;
        for (i = 0; i < size; i++)
            System.out.print(arr[i] + " ");
        System.out.println();
    }

    // Driver program
    public static void main(String args[]) {
        int arr[] = {64, 34, 25, 12, 22, 11, 90};
        int n = arr.length;
        bubbleSort(arr, n);
        System.out.println("Sorted array: ");
        printArray(arr, n);
    }
}
```

**OUTPUT:** `Sorted array: 11 12 22 25 34 64 90`

## Análise de Complexidade do Bubble Sort:

- **Complexidade de tempo:** O(n 2 )
- Auxiliary Space: O(1)

Consulte [Análise de complexidade do Bubble Sort](https://www.geeksforgeeks.org/time-and-space-complexity-analysis-of-bubble-sort/)
para obter detalhes.

## Vantagens do Bubble Sort:

- O Bubble Sort é fácil de entender e implementar.
- Não requer nenhum espaço de memória adicional.
- É um algoritmo de classificação estável, o que significa que elementos com o mesmo valor-chave mantêm sua ordem
  relativa na saída classificada.

## Desvantagens do Bubble Sort:

- A classificação por bolhas tem uma complexidade de tempo de O(n 2 ), o que a torna muito lenta para grandes conjuntos
  de dados.
- O bubble sort tem quase nenhuma ou limitada aplicação no mundo real. É usado principalmente em ambientes acadêmicos
  para ensinar diferentes maneiras de classificação.

## Principais Dúvidas

### Qual é o caso limite para Bubble Sort?

`O bubble sort leva o tempo mínimo (Ordem de n) quando os elementos já estão ordenados. Portanto, é melhor verificar se o
array já está ordenado ou não antes, para evitar a complexidade de tempo O(n 2 ).`

### A classificação acontece no Bubble Sort?

`Sim, o Bubble sort realiza a troca de pares adjacentes sem o uso de nenhuma estrutura de dados importante. Portanto, o algoritmo Bubble sort é um algoritmo in-place.`

### O algoritmo Bubble Sort é estável?

`Sim, o algoritmo de classificação por bolhas é estável.`

### Artigos Relacionados

- [Recursive Bubble Sort](https://www.geeksforgeeks.org/recursive-bubble-sort/)
- [Coding practice for sorting](https://www.geeksforgeeks.org/explore?page=1&category=Sorting&sortBy=submissions&itm_source=geeksforgeeks&itm_medium=main_header&itm_campaign=practice_header)
- [Quiz on Bubble Sort](https://www.geeksforgeeks.org/top-mcqs-on-bubblesort-algorithm-with-answers/)
- [Complexity Analysis of Bubble Sort](https://www.geeksforgeeks.org/time-and-space-complexity-analysis-of-bubble-sort/)

