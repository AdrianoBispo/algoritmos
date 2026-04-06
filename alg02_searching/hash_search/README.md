### Algoritmo de Busca por Hash (Hash Search)

A **busca por hash** usa uma estrutura de dados chamada **tabela hash** para armazenar e acessar valores de maneira
extremamente eficiente.

#### Como Funciona:

- A ideia principal por trás da busca por hash é **mapeamento direto**. A chave de cada valor (chave-valor) é passada
  por uma função hash, que gera um índice (ou "hash"). Esse índice é então usado para armazenar o valor em uma tabela de
  maneira que, para uma chave dada, você possa encontrar rapidamente o valor associado a ela.

  Por exemplo, considere uma tabela hash onde as chaves são strings e os valores são números. Se você deseja buscar o
  número associado à chave `"banana"`, a função hash calcula o índice correspondente à chave `"banana"`. Depois, você
  simplesmente acessa esse índice na tabela hash para obter o valor rapidamente.

#### Estrutura:

- **Função Hash**: Recebe uma chave como entrada e retorna um valor numérico (índice).
- **Tabela Hash**: Um array ou lista de buckets (geralmente um array de listas) onde os valores são armazenados. A
  função hash mapeia as chaves para os índices da tabela.

#### Complexidade:

- **Busca**: O(1) na melhor das hipóteses (caso não haja colisões de hash).
- **Inserção/Remoção**: O(1) na melhor das hipóteses.
- **Colisões**: Quando duas chaves diferentes têm o mesmo índice de hash, é preciso tratar essas colisões (com técnicas
  como encadeamento ou sondagem aberta).

## Usando Hash Table
Se a lista for grande e precisarmos realizar buscas frequentes, podemos criar uma tabela hash que mapeia cada elemento
para sua posição na lista. Dessa forma, podemos encontrar a posição de um elemento em tempo constante procurando seu
valor na tabela hash.

**Abaixo está a implementação do algoritmo acima discutido:**

```Java

import java.util.HashMap;
import java.util.Map;
import java.util.ArrayList;

class Gfg {
    static int linearSearchWithHashTable(ArrayList<Integer> arr, int target) {
        // Create a hash table to map each element to its position
        Map<Integer, Integer> hashTable = new HashMap<Integer, Integer>();
        for (int i = 0; i < arr.size(); i++) {
            hashTable.put(arr.get(i), i);
        }

        // Search for the target element in the hash table
        if (hashTable.containsKey(target)) {
            return hashTable.get(target);
        } else {
            return -1;
        }
    }

    public static void main(String[] args) {
        ArrayList<Integer> arr = new ArrayList<Integer>();
        arr.add(1);
        arr.add(5);
        arr.add(3);
        arr.add(9);
        arr.add(2);
        arr.add(7);
        int target = 9;

        int index = linearSearchWithHashTable(arr, target);
        if (index != -1) {
            System.out.println("Found " + target + " at index " + index);
        } else {
            System.out.println(target + " not found in the list");
        }
    }
}
```

### OUTPUT
`Encontrado 9 no índice 3`

### Explicação do código:

1. **Método** `linearSearchWithHashTable`:
- Ele recebe uma `ArrayList<Integer>` e um inteiro `target` como entrada.
- Um `HashMap` (`hashTable`) é criado, onde as chaves são os elementos do array e os valores são os índices desses
  elementos.
- O método percorre a lista (`arr`) e adiciona cada elemento e seu índice ao hash map.
- Depois de construir o hash map, o método verifica se o `target` é uma chave no hash map. Se encontrado, ele retorna o
  índice do `target`; caso contrário, retorna -1.

2. **Método** `main`:
- Inicializa uma `ArrayList` com alguns elementos inteiros.
- Define um valor `target` para procurar.
- Chama o método `linearSearchWithHashTable` para encontrar o índice do `target`.
- Imprime o resultado, seja o índice do alvo ou uma mensagem indicando que não foi encontrado.

### Resumo
O uso do `HashMap` é vantajoso quando você precisa realizar várias buscas em uma lista grande ou quando a lista é
imutável ou raramente muda. A tabela hash permite que você armazene os dados de forma a tornar as buscas muito mais
rápidas após a fase inicial de construção.