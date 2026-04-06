### Algoritmo de Busca em Largura (BFS - Breadth-First Search)

O **BFS** é um algoritmo de busca usado em **grafos** e **árvores** que explora todos os vizinhos de um nó antes de
avançar para o próximo nível de profundidade.

#### Como Funciona:

- Começa com um nó de origem e visita todos os seus vizinhos antes de ir para o próximo nível de vizinhos.
- Utiliza uma **fila** para armazenar os nós a serem visitados, garantindo que os nós mais próximos sejam processados
  primeiro.

#### Passos:

1. Coloque o nó inicial na fila.
2. Enquanto a fila não estiver vazia:
    - Retire o primeiro nó da fila (nó atual).
    - Visite todos os vizinhos do nó atual que ainda não foram visitados e coloque-os na fila.
3. Repita até que todos os nós tenham sido visitados.

#### Complexidade:

- **Tempo**: O(V + E), onde V é o número de vértices (nós) e E é o número de arestas (conexões entre os nós).
- **Espaço**: O(V), pois precisamos armazenar os nós na fila.

#### Exemplo (em um grafo simples):

```python
from collections import deque

# Representação de um grafo como um dicionário de adjacências
grafo = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E']
}

# Algoritmo BFS
def bfs(grafo, inicio):
    visitados = set()  # Conjunto de nós visitados
    fila = deque([inicio])  # Fila para controlar a ordem de visitação
    
    while fila:
        vertice = fila.popleft()  # Retira o primeiro nó da fila
        if vertice not in visitados:
            print(vertice)  # Visita o nó
            visitados.add(vertice)  # Marca como visitado
            for vizinho in grafo[vertice]:
                if vizinho not in visitados:
                    fila.append(vizinho)  # Adiciona vizinho à fila

bfs(grafo, 'A')
```

#### Saída do exemplo:

```
A
B
C
D
E
F
```