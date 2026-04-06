### Algoritmo de Busca em Profundidade (DFS - Depth-First Search)

O **DFS** é outro algoritmo de busca usado em grafos e árvores, mas, ao contrário do BFS, ele vai o mais fundo possível
ao explorar os nós antes de retroceder.

#### Como Funciona:

- Começa no nó de origem e vai explorando até atingir um nó sem vizinhos não visitados (ou um nó terminal).
- Ao atingir um nó sem mais vizinhos a explorar, o algoritmo "volta" para o nó anterior e explora outros caminhos.

#### Passos:

1. Comece com o nó inicial e marque-o como visitado.
2. Recursivamente visite cada nó vizinho que ainda não foi visitado.
3. Quando não houver mais vizinhos a visitar, volte para o nó anterior.
4. Repita até que todos os nós tenham sido visitados.

#### Complexidade:

- **Tempo**: O(V + E), onde V é o número de vértices e E o número de arestas.
- **Espaço**: O(V), pois precisamos armazenar os nós na pilha de recursão ou em uma pilha explícita.

#### Exemplo (em um grafo simples):

```python
# Algoritmo DFS usando recursão
def dfs(grafo, vertice, visitados):
    print(vertice)  # Visita o nó
    visitados.add(vertice)
    for vizinho in grafo[vertice]:
        if vizinho not in visitados:
            dfs(grafo, vizinho, visitados)

grafo = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E']
}

visitados = set()
dfs(grafo, 'A', visitados)
```

#### Saída do Exemplo:

```
A
B
D
E
F
C
```

Aqui, o DFS vai até o fundo da árvore (ou grafo) antes de voltar e explorar outras possibilidades, enquanto o BFS
explora por níveis.