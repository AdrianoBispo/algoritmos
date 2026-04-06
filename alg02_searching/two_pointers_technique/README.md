A técnica dos **dois ponteiros** (ou **two-pointer technique**) é uma abordagem bastante eficiente utilizada em
problemas de algoritmos, principalmente quando lidamos com arrays ou listas. Ela envolve o uso de dois ponteiros (ou
índices) para percorrer o array de maneira otimizada, geralmente com o objetivo de reduzir o tempo de execução, ao invés
de usar uma abordagem mais "bruta" com loops aninhados.

### O que é a técnica dos dois ponteiros?

Imagine que você tem uma lista ou array com vários elementos e precisa resolver algum problema que envolva dois
elementos em posições diferentes dessa lista. A ideia básica da técnica dos dois ponteiros é colocar dois índices em
posições diferentes (geralmente no início e no final) e movê-los de forma coordenada (normalmente, um para a direita e o
outro para a esquerda) até que se encontrem ou até que o problema seja resolvido.

### Para que serve a técnica dos dois ponteiros?

A técnica serve para **otimizar a busca e a manipulação de dados** dentro de um array ou lista. Em vez de percorrer o
array de maneira lenta com loops aninhados, você pode usar os dois ponteiros para realizar a tarefa de maneira mais
eficiente, com complexidade **O(n)** em vez de **O(n²)**.

### Quando utilizar a técnica dos dois ponteiros?

Você pode usar a técnica dos dois ponteiros quando:

- Você está lidando com um array **ordenado** ou pode ordená-lo.
- O problema envolve **duas partes** do array e você precisa realizar operações com elas (como encontrar pares, somar
  elementos, ou verificar condições entre elementos).
- Você precisa otimizar o tempo de execução e evitar soluções mais lentas com loops aninhados.

### Exemplo 1: **Soma de dois números que resultam em um valor alvo**

Vamos imaginar o seguinte problema: você tem um array de números **ordenado** e quer encontrar dois números que somados
resultem em um valor alvo.

### Exemplo em Java:

```java
public class TwoPointerExample {

    public static boolean hasPairWithSum(int[] arr, int target) {
        int left = 0; // Ponteiro no início do array
        int right = arr.length - 1; // Ponteiro no final do array

        while (left < right) {
            int sum = arr[left] + arr[right]; // Soma dos elementos apontados pelos ponteiros

            if (sum == target) {
                System.out.println("Par encontrado: " + arr[left] + " + " + arr[right] + " = " + target);
                return true;
            } else if (sum < target) {
                left++; // Aumenta o ponteiro esquerdo para somar valores maiores
            } else {
                right--; // Diminui o ponteiro direito para somar valores menores
            }
        }

        return false; // Caso nenhum par seja encontrado
    }

    public static void main(String[] args) {
        int[] arr = {1, 3, 4, 6, 8, 10};
        int target = 12;

        if (!hasPairWithSum(arr, target)) {
            System.out.println("Nenhum par encontrado.");
        }
    }
}
```

### Explicação do exemplo:

- Temos um array **ordenado** `[1, 3, 4, 6, 8, 10]` e queremos encontrar dois números que somem 12.
- O ponteiro **esquerdo** começa no início do array (`left = 0`), e o ponteiro **direito** começa no final (
  `right = arr.length - 1`).
- A cada iteração:
    - Calculamos a soma dos elementos nos índices `left` e `right`.
    - Se a soma for igual ao **target** (neste caso, 12), encontramos o par e retornamos verdadeiro.
    - Se a soma for menor que o target, movemos o ponteiro esquerdo para a direita (`left++`), porque isso aumentará a
      soma.
    - Se a soma for maior que o target, movemos o ponteiro direito para a esquerda (`right--`), porque isso diminuirá a
      soma.
- Isso vai acontecendo até que os ponteiros se cruzem, garantindo que a busca é feita de maneira otimizada.

### Exemplo 2: **Reverter uma string**

Outro exemplo onde os dois ponteiros podem ser usados é para inverter uma string.

```java
public class TwoPointerReverse {

    public static String reverseString(String str) {
        char[] chars = str.toCharArray(); // Converte a string para um array de caracteres
        int left = 0;
        int right = chars.length - 1;

        while (left < right) {
            // Troca os caracteres
            char temp = chars[left];
            chars[left] = chars[right];
            chars[right] = temp;

            left++;
            right--;
        }

        return new String(chars); // Converte de volta para string
    }

    public static void main(String[] args) {
        String str = "hello";
        System.out.println(reverseString(str)); // Saída: "olleh"
    }
}
```

### Explicação:

- Usamos o **ponteiro esquerdo** (`left`) no início da string e o **ponteiro direito** (`right`) no final.
- A cada iteração, trocamos os caracteres nas posições apontadas por `left` e `right` e depois movemos os ponteiros para
  mais perto um do outro.
- Quando os ponteiros se cruzam ou se encontram, a string foi invertida.



### Resumo:

A técnica dos **dois ponteiros** é útil para otimizar problemas em arrays ou listas, especialmente quando há a
necessidade de realizar comparações ou somas entre elementos de diferentes posições. Ela funciona bem quando o array
está ordenado ou pode ser ordenado, e evita o uso de loops aninhados, melhorando a performance do algoritmo.

Use-a quando você precisar comparar ou manipular dois elementos em diferentes posições, com a vantagem de reduzir a
complexidade de tempo!
