# Algoritmo de Busca Linear
**Definição Conceitual:** A busca linear é um algoritmo de busca fundamental que itera por uma lista de elementos um por
um, comparando cada elemento ao valor alvo. Se o valor alvo for encontrado, a busca para e retorna o índice do elemento.
Caso contrário, a busca continua até que o fim da lista seja alcançado, momento em que retorna -1 para indicar que o
valor alvo não foi
encontrado. Busca linear também é conhecida como **busca sequencial** .

**Analogia:** Imagine que você tem uma lista de nomes em um papel e quer encontrar um nome específico. Você começa do
primeiro nome e vai lendo um por um até encontrar o que procura. Isso é exatamente o que o algoritmo de busca linear
faz: ele percorre cada elemento de uma lista (ou array) até encontrar o que está procurando.

## Exemplo Visual

![Linear-search-algorithm-1.webp](..%2F..%2F..%2F..%2F..%2FAppData%2FLocal%2FTemp%2FLinear-search-algorithm-1.webp)
![Linear-search-algorithm-2.webp](..%2F..%2F..%2F..%2F..%2FAppData%2FLocal%2FTemp%2FLinear-search-algorithm-2.webp)
![Linear-search-algorithm-3.webp](..%2F..%2F..%2F..%2F..%2FAppData%2FLocal%2FTemp%2FLinear-search-algorithm-3.webp)

**Abaixo está a implementação do algoritmo de busca linear utilizando a linguagem Java com base nesse exemplo mostrado
acima:**

## Exemplo em Java

``` Java

public class BuscaLinear {
    public static int buscaLinear(int[] arr, int key) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == key) {
                return i; // Retorna o índice onde a chave foi encontrada
            }
        }
        return -1; // Retorna -1 se a chave não for encontrada
    }

    public static void main(String[] args) {
        int[] arr = {10, 50, 30, 70, 80, 20, 90, 40}; // Lista de Números
        int key = 30; // Valor a ser procurado
        
        int resultado = buscaLinear(arr, key);
        
        if (resultado != -1) {
            System.out.println("Elemento encontrado no índice: " + resultado);
        } else {
            System.out.println("Elemento não encontrado.");
        }
        
        // Output: Elemento encontrado no índice: 2
    }
}

```

## Em quais cenários devo utilizar o Algoritmo de Busca Linear?
1. **Pequenos conjuntos de dados:** Quando o conjunto de dados é relativamente pequeno (por exemplo, menos de algumas
   centenas de elementos), a busca linear pode ser eficiente porque o número de comparações necessárias é pequeno.
2. **Dados não classificados:** Ele é particularmente útil para dados não classificados, pois não requer
   nenhuma classificação prévia dos elementos.
3. **Implementação simples:** A busca linear é um dos algoritmos de busca mais simples de implementar, o que a torna
   adequada para iniciantes e fins educacionais.
4. **Natureza iterativa:** Por se tratar de um algoritmo iterativo, isso o torna fácil de entender e depurar.
5. **Aplicações em tempo real:** Em certas aplicações em tempo real, onde o conjunto de dados muda constantemente, a
   pesquisa linear pode ser mais eficiente do que outros algoritmos de busca que exigem pré-processamento ou
   classificação.
6. **Memória limitada:** A busca linear requer sobrecarga mínima de memória, pois ela só precisa armazenar o elemento
   atual que está sendo comparado. Isso a torna adequada para sistemas com recursos de memória limitados.

## Quais são as suas vantagens?
- **Simplicidade:** A busca linear é um dos algoritmos de busca mais simples de entender e implementar.
- **Eficiência para pequenos conjuntos de dados:** para pequenos conjuntos de dados, a pesquisa linear pode ser mais
  eficiente
  do que outros algoritmos de pesquisa que exigem pré-processamento ou classificação.
- **Dados não classificados:** a pesquisa linear pode ser usada para pesquisar dados não classificados sem qualquer
  classificação prévia.
- **Aplicações em tempo real:** a pesquisa linear pode ser útil em aplicações em tempo real, onde o conjunto de dados
  muda
  constantemente.
- **Sobrecarga de memória limitada:** a pesquisa linear requer sobrecarga de memória mínima, o que a torna adequada para
  sistemas com recursos de memória limitados.

## Quais são as suas desvantagens?
- **Ineficiência para grandes conjuntos de dados:** para grandes conjuntos de dados, a pesquisa linear pode ser
  ineficiente
  porque exige iteração por toda a lista para cada pesquisa.
- **Não adequado para dados classificados:** a pesquisa linear não é tão eficiente quanto outros algoritmos de
  pesquisa (por exemplo, pesquisa binária) para dados classificados.

## Complexidade de Tempo:
A complexidade de tempo é uma forma de medir quanto tempo o algoritmo leva para rodar, dependendo do tamanho da lista.

### Análise:
1. No pior caso, o algoritmo vai ter que percorrer todos os elementos da lista. Ou seja, se a lista tem `n` elementos, o
   algoritmo verifica todos eles até encontrar a chave ou concluir que ela não existe.

2. Se o elemento que estamos procurando está no último índice da lista ou não está presente, o algoritmo precisa passar
   por todos os elementos.

Então, a complexidade de tempo é O(n), onde `n` é o número de elementos na lista.

### Explicando através de Analogia:
Imagine que você está procurando uma chave em uma gaveta com vários compartimentos. Se a chave estiver no último
compartimento, você terá que abrir todos os compartimentos um por um. Isso é o que acontece na busca linear: no pior
caso, você verifica cada item até encontrar o que quer.

## Complexidade de Espaço:
A complexidade de espaço nos diz quanto de memória o algoritmo precisa para funcionar. A busca linear não se utiliza de
estruturas de dados adicionais (como listas ou mapas), ela apenas percorre o array informado. Ela usa uma quantidade
constante de
memória para armazenar algumas variáveis, como o índice i e o valor retornado, mas nada além disso.

Portanto, a complexidade de espaço é O(1), o que significa que ela precisa de uma quantidade constante de memória,
independentemente do tamanho da lista.

### Explicando através de Analogia:
Pensando na gaveta novamente: mesmo que a gaveta tenha muitos compartimentos, você só precisa de um espaço para
verificar se a chave está em cada compartimento, sem precisar de mais espaço.

## Dúvidas Frequentes

### 1. Quando o Algoritmo de Busca Linear é Preferido em Relação a Outros Algoritmos de Busca?
O algoritmo de busca linear é preferido quando a lista ou array não é classificado, ou quando o tamanho da entrada é
relativamente pequeno. É simples de implementar e não requer que os dados estejam em nenhuma ordem específica.

### 2. O Algoritmo de Busca Linear pode ser Aplicado a Outras Estruturas de Dados?
Sim, o algoritmo de busca linear pode ser aplicado não apenas a arrays ou listas, mas também a outras estruturas de
dados lineares, como listas encadeadas. O princípio permanece o mesmo: iterar por cada elemento até que o alvo seja
encontrado ou o fim seja alcançado.

### 3. O Algoritmo de Busca Linear é Adequado para Matrizes ou Listas Ordenadas?
Embora o algoritmo de busca linear ainda possa ser usado em arrays ou listas ordenadas, não é a opção mais eficiente. A
busca binária, por exemplo, é mais adequada para dados ordenados, pois tem uma complexidade de tempo de O(log n).

### 4. Quais são algumas aplicações reais do algoritmo de busca linear ?
O algoritmo de busca linear pode ser usado em cenários como busca por um valor específico em uma lista telefônica, busca
por um nome em uma lista não ordenada de contatos ou busca por um item em uma lista de compras. Ele é frequentemente
usado em cenários onde o tamanho dos dados é pequeno ou não se espera que cresça significativamente.

## Melhorando a Técnica de Busca Linear
O objetivo é que se o mesmo elemento for pesquisado novamente, a operação deve levar menos tempo. Portanto, em tal caso,
a Busca Linear pode ser melhorada usando os dois métodos a seguir:

- Transposition(Transposição)
- Move to Front(Mover para a frente)

### Transposition (Transposição):
Na transposição, se o elemento-chave for encontrado, ele é trocado para o elemento um índice antes de aumentar o número
de contagens de pesquisa para uma chave específica; a operação de pesquisa também otimiza e continua movendo o elemento
para o início da matriz, onde a complexidade do tempo de pesquisa seria de tempo constante.

**Por exemplo:** se o `array[]` for `{2, 5, 7, 1, 6, 4, 5, 8, 3, 7}` e a **chave a ser pesquisada for 4**, abaixo estão
os passos:

- Após procurar pela chave 4 , o elemento é encontrado no índice 5 do array fornecido após 6 comparações. Agora, após a
  transposição, o array se torna {2, 5, 7, 1, 4, 6, 5, 8, 3, 7}, ou seja, a chave com valor 4 vem no índice 4.
- Novamente após procurar pela chave 4 , o elemento é encontrado no índice 4 do array fornecido após 6 comparações.
  Agora, após a transposição, o array se torna {2, 5, 7, 4, 1, 6, 5, 8, 3, 7}, ou seja, a chave com valor 4 vem no
  índice 3.
- O processo acima continuará até que qualquer chave chegue à frente do array se o elemento a ser encontrado não estiver
  no primeiro índice.

**Abaixo está a implementação do algoritmo acima discutido:**

```Java

// Java program for transposition
// to improve the Linear Search 
// Algorithm
class GFG {

    // Structure of the 
// array
    static class Array {
        int[] A = new int[10];
        int size;
        int length;

        Array(int[] A, int size,
              int length) {
            this.A = A;
            this.size = size;
            this.length = length;
        }
    }

    ;

    // Function to print the 
// array element
    static void Display(Array arr) {
        int i;

// Traverse the array arr[]
        for (i = 0; i < arr.length; i++) {
            System.out.printf("%d ",
                    arr.A[i]);
        }
        System.out.printf("\n");
    }

    // Function that performs the Linear
// Search Transposition
    static int LinearSearchTransposition(Array arr,
                                         int key) {
        int i;

// Traverse the array
        for (i = 0; i < arr.length; i++) {
            // If key is found, then swap
            // the element with it's
            // previous index
            if (key == arr.A[i]) {
                // If key is first element
                if (i == 0)
                    return i;
                int temp = arr.A[i];
                arr.A[i] = arr.A[i - 1];
                arr.A[i - 1] = temp;
                return i;
            }
        }
        return -1;
    }

    // Driver Code
    public static void main(String[] args) {
// Given array arr[]
        int tempArr[] = {2, 23, 14, 5,
                6, 9, 8, 12};
        Array arr = new Array(tempArr,
                10, 8);

        System.out.printf("Elements before Linear" +
                " Search Transposition: ");

// Function Call for displaying
// the array arr[]
        Display(arr);

// Function Call for transposition
        LinearSearchTransposition(arr, 14);

        System.out.printf("Elements after Linear" +
                " Search Transposition: ");

// Function Call for displaying
// the array arr[]
        Display(arr);
    }
}

// This code is contributed by Princi Singh
```

### OUTPUT
- `Elements before Linear Search Transposition:  2 23 14 5 6 9 8 12`
- `Elements after Linear Search Transposition:  2 14 23 5 6 9 8 12`

## Move to Front/Head (Mover para Frente):
Neste método, se o elemento-chave for encontrado, ele será trocado diretamente pelo índice 0 , de modo que na próxima
vez consecutiva, a operação de busca pelo mesmo elemento-chave será de O(1) , ou seja, tempo constante.

Por exemplo: se o **array** `arr[]` for `{2, 5, 7, 1, 6, 4, 5, 8, 3, 7}` e a **chave a ser pesquisada for 4**, abaixo estão os
passos:

- Após procurar pela chave 4 , o elemento é encontrado no índice 5 do array fornecido após 6 comparações.
- Agora, após passar para a operação frontal, o array se torna {4, 2, 5, 7, 1, 6, 5, 8, 3, 7}, ou seja, a chave com valor 4 vem no
índice 0 .
- Novamente, após procurar pela chave 4 , o elemento é encontrado no índice 0 do array fornecido, o que reduz o espaço de
busca inteiro.

**Abaixo está a implementação do algoritmo acima discutido:**

```Java

// Java program for transposition
// to improve the Linear Search 
// Algorithm
class GFG {

    // Structure of the 
// array
    static class Array {
        int[] A = new int[10];
        int size;
        int length;

        Array(int[] A, int size,
              int length) {
            this.A = A;
            this.size = size;
            this.length = length;
        }
    }

    ;

    // Function to print the 
// array element
    static void Display(Array arr) {
        int i;

// Traverse the array arr[]
        for (i = 0; i < arr.length; i++) {
            System.out.printf("%d ",
                    arr.A[i]);
        }
        System.out.printf("\n");
    }

    // Function that performs the Linear
// Search Transposition
    static int LinearSearchTransposition(Array arr,
                                         int key) {
        int i;

// Traverse the array
        for (i = 0; i < arr.length; i++) {
            // If key is found, then swap
            // the element with it's
            // previous index
            if (key == arr.A[i]) {
                // If key is first element
                if (i == 0)
                    return i;
                int temp = arr.A[i];
                arr.A[i] = arr.A[i - 1];
                arr.A[i - 1] = temp;
                return i;
            }
        }
        return -1;
    }

    // Driver Code
    public static void main(String[] args) {
// Given array arr[]
        int tempArr[] = {2, 23, 14, 5,
                6, 9, 8, 12};
        Array arr = new Array(tempArr,
                10, 8);

        System.out.printf("Elements before Linear" +
                " Search Transposition: ");

// Function Call for displaying
// the array arr[]
        Display(arr);

// Function Call for transposition
        LinearSearchTransposition(arr, 14);

        System.out.printf("Elements after Linear" +
                " Search Transposition: ");

// Function Call for displaying
// the array arr[]
        Display(arr);
    }
}

// This code is contributed by Princi Singh
```

### OUTPUT
- `Elements before Linear Search Move To Front:  2 23 14 5 6 9 8 12`
- `Elements after Linear Search Move To Front:  14 23 2 5 6 9 8 12`

## Conclusão
A busca linear é um algoritmo de busca simples e eficiente que é particularmente útil para pequenos conjuntos de dados,
dados não classificados e aplicações em tempo real. Embora não seja tão eficiente quanto outros algoritmos de busca para
grandes conjuntos de dados classificados, sua simplicidade e facilidade de implementação o tornam uma ferramenta valiosa
em vários cenários.