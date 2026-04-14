# Lista de Exercícios - Algoritmos Geométricos

Esta lista contém 66 exercícios clássicos de geometria computacional e matemática aplicada, cuidadosamente divididos por nível de dificuldade. O objetivo é fortalecer a lógica de programação através de descrições focadas na resolução passo a passo, abstraindo a linguagem de programação. Você pode implementar as soluções utilizando a linguagem de sua preferência (C, Python, Java, JavaScript, C#, Kotlin, Go, etc.).

## Importante antes de começar (Boas Práticas em Geometria Computacional)

- **Precisão de Ponto Flutuante (Epsilon):** Ao lidar com números decimais (`float` ou `double`), nunca use a igualdade estrita (`a == b`). Use uma tolerância: `abs(a - b) < 1e-9`.
- **Evite Raízes Quadradas:** Cálculos de raiz quadrada (`sqrt`) são custosos. Compare distâncias ao quadrado ($d^2$) quando possível.
- **Aplicações Reais:** Estes conceitos são base para Motores de Jogos, GIS, CAD e Visão Computacional.

---

## Nível 1 - Fundamentos

<details>
    <summary>📐 Retas e Segmentos</summary>

### 1. Ponto médio de uma reta
**Descrição:** Encontrar o ponto que divide um segmento de reta pela metade.

**Passo a passo:**
1. Receba as coordenadas cartesianas de dois pontos: (x₁, y₁) e (x₂, y₂).
2. Calcule: xₘ = (x₁ + x₂) / 2 e yₘ = (y₁ + y₂) / 2.
3. O resultado é a nova coordenada (xₘ, yₘ).

**Complexidade:** O(1) | Espaço O(1)

**Entrada:** 
```
x1 = -1, y1 = 2, x2 = 3, y2 = -6
```

**Saída:** 
```
(1.0, -2.0)
```

### 2. Inclinação de uma reta
**Descrição:** Calcular o coeficiente angular (slope) de uma reta formada por dois pontos.

**Passo a passo:**
1. Receba as coordenadas dos dois pontos.
2. Se x₁ == x₂, a reta é vertical (inclinação indefinida).
3. Caso contrário: M = (y₂ - y₁) / (x₂ - x₁).

**Entrada:** 
```
x1 = 2, y1 = 1, x2 = 4, y2 = 5
```

**Saída:** 
```
2.0
```

</details>

<details>
    <summary>🔲 Retângulo e Quadrado</summary>

### 3. Área e perímetro de um retângulo
**Descrição:** Calcular a área e o perímetro de um retângulo.

**Passo a passo:**
1. Receba o comprimento (L) e a altura (W).
2. Área = L × W.
3. Perímetro = 2 × (L + W).

**Entrada:** 
```
L = 5, W = 4
```

**Saída:** 
```
Área = 20, Perímetro = 18
```

### 4. Verificar se um ponto está dentro de um retângulo
**Descrição:** Determinar se um ponto P(x,y) está dentro de um retângulo AABB.

**Passo a passo:**
1. Receba a âncora inferior-esquerda (xₘᵢₙ, yₘᵢₙ) e superior-direita (xₘₐₓ, yₘₐₓ).
2. Receba as coordenadas do ponto P(x, y).
3. Retorne `Verdadeiro` SE (x > xₘᵢₙ) E (x < xₘₐₓ) E (y > yₘᵢₙ) E (y < yₘₐₓ).

**Entrada:** 
```
Ret = (0, 0, 10, 10), P = (5, 5)
```

**Saída:** 
```
Verdadeiro
```

</details>

<details>
    <summary>⭕ Círculo</summary>

### 5. Circunferência de um círculo
**Descrição:** Calcular o perímetro de um círculo.

**Passo a passo:**
1. Receba o raio r.
2. C = 2 × π × r.

**Entrada:** 
```
r = 5
```

**Saída:** 
```
31.415
```

### 6. Área de um círculo
**Descrição:** Calcular a área interna de um círculo.

**Passo a passo:**
1. Receba o raio r.
2. A = π × r².

**Entrada:** 
```
r = 5
```

**Saída:** 
```
78.539
```

</details>

<details>
    <summary>🔺 Triângulo</summary>

### 7. Verificar se um triângulo é válido
**Descrição:** Determinar se três segmentos podem formar um triângulo válido (Desigualdade Triangular).

**Passo a passo:**
1. Receba os lados a, b, c.
2. Verifique: a + b > c, a + c > b, b + c > a.
3. Se todas as condições forem satisfeitas, o triângulo é válido.

**Entrada:** 
```
a = 7, b = 10, c = 5
```

**Saída:** 
```
Válido
```

### 8. Área de um triângulo
**Descrição:** Calcular a área interna de um triângulo usando suas coordenadas.

**Passo a passo:**
1. Receba as coordenadas A(x₁, y₁), B(x₂, y₂), C(x₃, y₃).
2. Aplique a Fórmula do Determinante: Área = |x₁(y₂ - y₃) + x₂(y₃ - y₁) + x₃(y₁ - y₂)| / 2.
3. O valor absoluto é mandatório para garantir área positiva.

**Entrada:** 
```
A = (0, 0), B = (20, 0), C = (10, 30)
```

**Saída:** 
```
300.0
```

</details>

---

## Nível 2 - Intermediário

<details>
    <summary>📐 Retas e Segmentos</summary>

### 9. Fórmula da seção (razão m:n)
**Descrição:** Encontrar o ponto que divide uma reta em uma proporção específica m:n.

**Passo a passo:**
1. Receba (x₁, y₁), (x₂, y₂), m, n.
2. X = (m × x₂ + n × x₁) / (m + n).
3. Y = (m × y₂ + n × y₁) / (m + n).
4. Verifique se (m + n) ≠ 0.

**Entrada:** 
```
x1 = 2, y1 = 4, x2 = 4, y2 = 6, m = 1, n = 1
```

**Saída:** 
```
(3.0, 5.0)
```

### 10. Reta passando por 2 pontos
**Descrição:** Encontrar a equação geral da reta no formato Ax + By + C = 0.

**Passo a passo:**
1. Receba P₁(x₁, y₁) e P₂(x₂, y₂).
2. A = y₂ - y₁.
3. B = x₁ - x₂.
4. C = -(A × x₁ + B × y₁).

**Entrada:** 
```
x1 = 3, y1 = 2, x2 = 2, y2 = 6
```

**Saída:** 
```
4x + 1y - 14 = 0
```

### 11. Interseção de duas retas
**Descrição:** Determinar o ponto exato onde duas retas se cruzam.

**Passo a passo:**
1. Receba os coeficientes A₁, B₁, C₁ e A₂, B₂, C₂.
2. Calcule Δ = A₁ × B₂ - A₂ × B₁ (determinante).
3. Se Δ ≈ 0, as retas são paralelas (sem interseção).
4. Caso contrário: x = (C₁ × B₂ - C₂ × B₁) / Δ, y = (A₁ × C₂ - A₂ × C₁) / Δ.

**Entrada:** 
```
A1 = 1, B1 = 1, C1 = 3, A2 = 1, B2 = -1, C2 = 1
```

**Saída:** 
```
(2.0, 1.0)
```

### 12. Verificar se dois segmentos se intersectam
**Descrição:** Avaliar se dois segmentos finitos possuem algum ponto em comum.

**Passo a passo:**
1. Receba as coordenadas dos 4 pontos.
2. Crie função auxiliar para calcular orientação via produto vetorial.
3. Dois segmentos se cruzam se as orientações forem diferentes para ambos os pares.
4. Lide com casos especiais de colinearidade.

**Entrada:** 
```
P1 = (1, 1), P2 = (10, 1), P3 = (1, 2), P4 = (10, 2)
```

**Saída:** 
```
Falso
```

</details>

<details>
    <summary>🔲 Retângulo, Quadrado e Círculo</summary>

### 13. Verificar se dois retângulos se sobrepõem
**Descrição:** Detectar colisão entre dois retângulos AABB.

**Passo a passo:**
1. Receba coordenadas de R₁ e R₂.
2. Verifique se não colidem: limite direito de R₁ < limite esquerdo de R₂, etc.
3. Se nenhuma condição de recusa for satisfeita, houve sobreposição.

**Entrada:** 
```
R1_L = (0, 10), R1_R = (10, 0), R2_L = (5, 5), R2_R = (15, 0)
```

**Saída:** 
```
Verdadeiro
```

### 14. Verificar se quatro pontos formam um quadrado
**Descrição:** Validar se 4 pontos formam um quadrado perfeito.

**Passo a passo:**
1. Calcule todas as 6 distâncias possíveis entre pares.
2. Ordene as distâncias ao quadrado.
3. Verifique se as 4 primeiras são idênticas (arestas) e as 2 últimas também são idênticas (diagonais).

**Entrada:** 
```
(20, 10), (10, 20), (20, 20), (10, 10)
```

**Saída:** 
```
Verdadeiro
```

### 15. Verificar se um ponto está em um setor circular
**Descrição:** Detectar se um ponto está dentro de um cone de visão (Field of View).

**Passo a passo:**
1. Verifique distância: se > raio, retorne `falso`.
2. Use `atan2()` para encontrar o ângulo do ponto.
3. Verifique se o ângulo está entre os limites do setor.

**Entrada:** 
```
Centro = (0, 0), Raio = 5, Ângulos = [0, 90], Ponto = (3, 3)
```

**Saída:** 
```
Verdadeiro
```

### 16. Verificar se dois círculos se tocam ou intersectam
**Descrição:** Detectar colisão entre dois círculos.

**Passo a passo:**
1. Calcule a distância D entre os centros.
2. Se D == r₁ + r₂, tocam externamente.
3. Se D < r₁ + r₂ e D > |r₁ - r₂|, intersectam.

**Entrada:** 
```
C1 = (0, 0, R1 = 2), C2 = (3, 0, R2 = 2)
```

**Saída:** 
```
Intersectam
```

### 17. Verificar se uma reta toca ou intersecta um círculo
**Descrição:** Determinar colisão entre uma reta infinita e um círculo.

**Passo a passo:**
1. Converta a reta para forma Ax + By + C = 0.
2. Calcule distância perpendicular: D = |Ax₀ + By₀ + C| / √(A² + B²).
3. Compare D com o raio: D > r = não intersecta, D == r = tangente, D < r = intersecta.

**Entrada:** 
```
Reta: 3x + 4y - 25 = 0, Círculo = (0, 0, Raio = 5)
```

**Saída:** 
```
Toca
```

</details>

<details>
    <summary>🔺 Triângulo</summary>

### 18. Verificar se um ponto está dentro de um triângulo
**Descrição:** Determinar se um ponto P está dentro dos limites de um triângulo ABC.

**Passo a passo:**
1. Calcule a área total do triângulo ABC.
2. Divida em três triângulos menores: PAB, PBC, PCA.
3. Se a soma das áreas menores ≈ área original, o ponto está dentro.

**Entrada:** 
```
A = (0, 0), B = (20, 0), C = (10, 30), P = (10, 15)
```

**Saída:** 
```
Verdadeiro
```

### 19. Todos os ângulos de um triângulo
**Descrição:** Encontrar os ângulos internos dado o tamanho dos três lados.

**Passo a passo:**
1. Identifique os lados como a, b, c.
2. Aplique Lei dos Cossenos: cos(C) = (a² + b² - c²) / (2ab).
3. Use `acos()` para obter o ângulo em radianos.
4. Converta para graus multiplicando por (180/π).
5. Repita para os outros ângulos.

**Entrada:** 
```
a = 3, b = 4, c = 5
```

**Saída:** 
```
90.0°, 53.13°, 36.87°
```

### 20. Circuncentro de um triângulo
**Descrição:** Encontrar o ponto equidistante dos três vértices (centro da circunferência circunscrita).

**Passo a passo:**
1. Calcule o ponto médio de dois lados.
2. Encontre a reta perpendicular para cada lado.
3. Resolva o sistema linear das duas mediatrizes.

**Entrada:** 
```
A = (6, 0), B = (0, 0), C = (0, 8)
```

**Saída:** 
```
(3.0, 4.0)
```

### 21. Terceiro lado do triângulo (Lei dos Cossenos)
**Descrição:** Calcular o terceiro lado dado dois lados e o ângulo entre eles.

**Passo a passo:**
1. Receba a, b e o ângulo C em graus.
2. Converta para radianos: Cᵣₐ𝒹 = C × (π/180).
3. Aplique c = √(a² + b² - 2ab × cos(Cᵣₐ𝒹)).

**Entrada:** 
```
a = 3, b = 4, ângulo = 90
```

**Saída:** 
```
5.0
```

</details>

<details>
    <summary>🔷 Quadrilátero</summary>

### 22. Perímetro de um paralelogramo
**Descrição:** Calcular o perímetro de um paralelogramo.

**Passo a passo:**
1. Receba os lados a e b.
2. Perímetro = 2 × (a + b).

**Entrada:** 
```
a = 4, b = 5
```

**Saída:** 
```
18
```

### 23. Área e perímetro de um trapézio
**Descrição:** Calcular área e perímetro de um trapézio.

**Passo a passo:**
1. Receba base maior B, base menor b, altura h, lados c e d.
2. Área = ((B + b) / 2) × h.
3. Perímetro = B + b + c + d.

**Entrada:** 
```
B = 10, b = 6, h = 4, c = 5, d = 5
```

**Saída:** 
```
Área = 32, Perímetro = 26
```

### 24. Verificar se quatro pontos formam um paralelogramo
**Descrição:** Validar se 4 pontos formam um paralelogramo.

**Passo a passo:**
1. Verifique se as diagonais se cruzam no ponto médio exato uma da outra.
2. Calcule o ponto médio de (A, C) e (B, D).
3. Se forem iguais, é um paralelogramo.

**Entrada:** 
```
(0, 0), (2, 0), (3, 2), (1, 2)
```

**Saída:** 
```
Verdadeiro
```

</details>

<details>
    <summary>🧊 Objetos 3D</summary>

### 25. Volume e área de superfície de um cone
**Descrição:** Calcular volume e área lateral de um cone.

**Passo a passo:**
1. Receba raio da base r e altura h.
2. Geratriz: l = √(r² + h²).
3. Volume = (1/3) × π × r² × h.
4. Área = π × r × l + π × r².

**Entrada:** 
```
r = 3, h = 4
```

**Saída:** 
```
Volume = 37.69, Área = 75.39
```

### 26. Volume e área de superfície de uma esfera
**Descrição:** Calcular volume e área de uma esfera.

**Passo a passo:**
1. Receba o raio r.
2. Volume = (4/3) × π × r³.
3. Área = 4 × π × r².

**Entrada:** 
```
r = 5
```

**Saída:** 
```
Volume = 523.59, Área = 314.15
```

### 27. Volume e área de superfície de um cuboide
**Descrição:** Calcular volume e área de um prisma retangular.

**Passo a passo:**
1. Receba comprimento L, profundidade C, altura A.
2. Volume = L × C × A.
3. Área = 2 × (LC + CA + AL).

**Entrada:** 
```
L = 2, C = 3, A = 4
```

**Saída:** 
```
Volume = 24, Área = 52
```

### 28. Volume e área de superfície de um cubo
**Descrição:** Calcular volume e área de um cubo.

**Passo a passo:**
1. Receba a aresta a.
2. Volume = a³.
3. Área = 6 × a².

**Entrada:** 
```
a = 3
```

**Saída:** 
```
Volume = 27, Área = 54
```

</details>

---

## Nível 3 - Avançado

<details>
    <summary>📐 Retas e Segmentos</summary>

### 29. Contar máximo de pontos na mesma reta
**Descrição:** Encontrar o número máximo de pontos colineares em um conjunto.

**Passo a passo:**
1. Para cada ponto como origem, calcule a inclinação em relação a todos os outros.
2. Use hash map para contar ocorrências de cada inclinação.
3. Armazene inclinações como frações reduzidas (usando MDC).
4. O máximo será a maior contagem + origem.

**Complexidade:** O(N² log(coord))

**Entrada:** 
```
[(1, 1), (2, 2), (3, 3), (4, 5)]
```

**Saída:** 
```
3
```

### 30. Número mínimo de retas para cobrir todos os pontos
**Descrição:** Calcular quantidade mínima de disparos em linha reta de uma origem para acertar todos os pontos.

**Passo a passo:**
1. Receba ponto origem (x₀, y₀) e lista de pontos.
2. Para cada ponto, calcule a inclinação simplificada pelo MDC.
3. Insira em um Set (sem duplicatas).
4. Retorne o tamanho do Set.

**Entrada:** 
```
origem = (0, 0), pontos = [(1, 1), (2, 2), (-1, -1), (2, 3)]
```

**Saída:** 
```
2
```

</details>

<details>
    <summary>🔺 Triângulo</summary>

### 31. Triângulo retângulo de área e hipotenusa
**Descrição:** Verificar se é possível formar um triângulo retângulo sabendo apenas área e hipotenusa.

**Passo a passo:**
1. Dado Área A e Hipotenusa H.
2. Para existir: H² ≥ 4A.
3. Se condição for satisfeita, o triângulo é possível.

**Entrada:** 
```
Área = 6, Hipotenusa = 5
```

**Saída:** 
```
Possível
```

### 32. Contar pontos inteiros dentro de um triângulo
**Descrição:** Contar quantos pontos de grade caem estritamente dentro de um triângulo.

**Passo a passo:**
1. Calcule a área do triângulo.
2. Para cada lado, calcule pontos na borda: MDC(|x₁ - x₂|, |y₁ - y₂|).
3. Use Teorema de Pick: I = Área - B/2 + 1 (onde I = interior, B = borda).

**Entrada:** 
```
(0, 0), (0, 5), (5, 0)
```

**Saída:** 
```
6
```

### 33. Área da circunferência circunscrita de triângulo equilátero
**Descrição:** Calcular a área da circunferência que envolve um triângulo equilátero.

**Passo a passo:**
1. Para triângulo equilátero de lado a: R = a / √3.
2. Área = π × R².

**Entrada:** 
```
lado = 6
```

**Saída:** 
```
37.699
```

### 34. Triângulos formados por N retas no plano
**Descrição:** Contar quantos triângulos são formados pelas interseções de N retas.

**Passo a passo:**
1. Combinações iniciais: C(N, 3).
2. Subtraia combinações de retas paralelas: C(retas_paralelas, 3).
3. Subtraia combinações de retas concorrentes no mesmo ponto.

**Entrada:** 
```
[y = x, y = -x, y = 2]
```

**Saída:** 
```
1
```

</details>

<details>
    <summary>🔲 Retângulo, Quadrado e Círculo</summary>

### 35. Número de retângulos em uma grade N×M
**Descrição:** Contar todas as combinações de retângulos em uma grade.

**Passo a passo:**
1. Combinações em 1D: 1 + 2 + ... + N = N(N+1)/2.
2. Expansão 2D: (N(N+1)/2) × (M(M+1)/2).

**Complexidade:** O(1)

**Entrada:** 
```
N = 2, M = 2
```

**Saída:** 
```
9
```

### 36. Área de um segmento circular
**Descrição:** Calcular a área da fatia circular abaixo de uma corda.

**Passo a passo:**
1. Receba raio r e ângulo θ em radianos.
2. Área do setor = (1/2) × r² × θ.
3. Área do triângulo = (1/2) × r² × sin(θ).
4. Segmento = Setor - Triângulo.

**Entrada:** 
```
Raio = 10, Ângulo = 90° (1.57 rad)
```

**Saída:** 
```
28.539
```

### 37. Área de círculo circunscrito a um quadrado
**Descrição:** Calcular a área da menor circunferência que envolve um quadrado.

**Passo a passo:**
1. Diagonal do quadrado: D = a√2.
2. Raio: R = D/2 = (a√2)/2.
3. Área = π × R².

**Entrada:** 
```
Lado = 4
```

**Saída:** 
```
25.132
```

### 38. Raio mínimo para k pontos
**Descrição:** Encontrar o raio mínimo de um círculo que contém pelo menos k pontos.

**Passo a passo:**
1. Use busca binária: Mín_R = 0, Máx_R = distância máxima.
2. Para cada R_teste, conte quantos pares conseguem ser englobados.
3. Ajuste limites até convergir.

**Entrada:** 
```
Pontos = [(0, 0), (1, 0), (0, 1)], k = 3
```

**Saída:** 
```
0.707
```

### 39. Varredura angular (máximo de pontos em círculo)
**Descrição:** Girar um círculo de raio fixo para capturar o máximo de pontos.

**Passo a passo:**
1. Para cada ponto como âncora, calcule os ângulos de entrada/saída.
2. Use varredura angular para contar pontos em cada posição.
3. Retorne o máximo encontrado.

**Entrada:** 
```
Pontos = [(1, 1), (2, 2), (3, 3)], Raio = 1.5
```

**Saída:** 
```
2
```

</details>

<details>
    <summary>🔷 Quadrilátero</summary>

### 40. Número de paralelogramos em grade de retas
**Descrição:** Contar paralelogramos formados pelas interseções de um grid.

**Passo a passo:**
1. Combinações horizontais: n(n-1)/2.
2. Combinações verticais: m(m-1)/2.
3. Total = (n(n-1)/2) × (m(m-1)/2).

**Entrada:** 
```
n = 5, m = 5
```

**Saída:** 
```
100
```

### 41. Encontrar coordenadas ausentes de um paralelogramo
**Descrição:** Dado 3 vértices, encontrar os 3 possíveis 4º vértices.

**Passo a passo:**
1. Dado A, B, C, calcule:
     - D₁ = A + B - C
     - D₂ = A + C - B
     - D₃ = B + C - A

**Entrada:** 
```
A = (0, 0), B = (2, 0), C = (0, 2)
```

**Saída:** 
```
(2, 2), (-2, 2), (2, -2)
```

### 42. Área máxima de um quadrilátero
**Descrição:** Encontrar a área máxima de um quadrilátero com lados dados (Fórmula de Brahmagupta).

**Passo a passo:**
1. Receba lados a, b, c, d.
2. Semiperímetro: S = (a + b + c + d) / 2.
3. Área = √((S-a)(S-b)(S-c)(S-d)).

**Entrada:** 
```
a = 1, b = 2, c = 1, d = 2
```

**Saída:** 
```
2.0
```

### 43. Encontrar ponto ausente do paralelogramo
**Descrição:** Dado 3 vértices em sequência, encontrar o 4º.

**Passo a passo:**
1. D.x = A.x + C.x - B.x.
2. D.y = A.y + C.y - B.y.

**Entrada:** 
```
A = (0, 0), B = (2, 0), C = (3, 2)
```

**Saída:** 
```
(1, 2)
```

</details>

<details>
    <summary>🧊 Objetos 3D</summary>

### 44. Perímetro de um cilindro
**Descrição:** Calcular o perímetro (contorno) de um cilindro em projeção 2D.

**Passo a passo:**
1. Receba diâmetro d e altura h.
2. Perímetro = 2(d + h).

**Entrada:** 
```
d = 5, h = 10
```

**Saída:** 
```
30
```

### 45. Volume e área de um tronco de cone
**Descrição:** Calcular propriedades de um cone decepado.

**Passo a passo:**
1. Receba raio maior R, raio menor r, altura h.
2. Geratriz: l = √(h² + (R-r)²).
3. Volume = (1/3)πh(R² + r² + R×r).
4. Área lateral = π×l(R + r).

**Entrada:** 
```
R = 4, r = 2, h = 6
```

**Saída:** 
```
Volume = 175.92
```

### 46. Volume de um elipsoide
**Descrição:** Calcular o volume de uma elipse em 3D.

**Passo a passo:**
1. Receba semi-eixos a, b, c.
2. Volume = (4/3) × π × a × b × c.

**Entrada:** 
```
a = 2, b = 3, c = 4
```

**Saída:** 
```
100.53
```

### 47. Volume de uma pirâmide
**Descrição:** Calcular volume de uma pirâmide.

**Passo a passo:**
1. Receba área da base B e altura h.
2. Volume = (1/3) × B × h.

**Entrada:** 
```
B = 10, h = 6
```

**Saída:** 
```
20.0
```

### 48. Quádrupla pitagórica
**Descrição:** Validar se 4 números satisfazem a² + b² + c² = d².

**Passo a passo:**
1. Ordene os 4 números.
2. Eleve os 3 menores ao quadrado e some.
3. Compare com o maior número ao quadrado.

**Entrada:** 
```
2, 3, 6, 7
```

**Saída:** 
```
Verdadeiro
```

### 49. Geração de esfera com algoritmo LS3/NS3
**Descrição:** Gerar malha tridimensional de uma esfera.

**Passo a passo:**
1. Loop duplo: ângulo azimutal (0 a 2π) e polar (0 a π).
2. Para cada interseção, converta para coordenadas 3D:
     - X = r × sin(polar) × cos(azimutal)
     - Y = r × sin(polar) × sin(azimutal)
     - Z = r × cos(polar)

**Entrada:** 
```
Raio = 1, Resolução = 0.5 rad
```

**Saída:** 
```
Matriz 3D de coordenadas
```

</details>

<details>
    <summary>⬠ Polígono e Casco Convexo</summary>

### 50. Verificar se ponto está dentro de polígono
**Descrição:** Usar Ray Casting para determinar se ponto está dentro de um polígono.

**Passo a passo:**
1. Dispare um raio infinito horizontal do ponto para fora.
2. Conte quantas arestas do polígono cruzam este raio.
3. Se ímpar: dentro. Se par: fora.

**Entrada:** 
```
Polígono = [(0,0), (0,4), (4,4), (4,0)], Ponto = (2,2)
```

**Saída:** 
```
Dentro
```

### 51. Área de polígono com n vértices (Fórmula de Shoelace)
**Descrição:** Calcular área de qualquer polígono simples (sem auto-interseção).

**Passo a passo:**
1. Ordene vértices sequencialmente.
2. Calcule diagonal primária: Σ(Xᵢ × Yᵢ₊₁).
3. Calcule diagonal secundária: Σ(Yᵢ × Xᵢ₊₁).
4. Área = |diagonal1 - diagonal2| / 2.

**Entrada:** 
```
[(0,0), (4,0), (4,3), (0,3)]
```

**Saída:** 
```
12.0
```

### 52. Casco convexo (Algoritmo de Jarvis/Gift Wrapping)
**Descrição:** Encontrar a envolvente convexa de um conjunto de pontos.

**Passo a passo:**
1. Inicie pelo ponto mais à esquerda.
2. Para cada iteração, encontre o ponto que forma maior ângulo anti-horário.
3. Continue até retornar ao ponto inicial.

**Complexidade:** O(N × H) onde H = número de vértices do casco

**Entrada:** 
```
[(0,3), (1,1), (2,2), (4,4), (0,0), (1,2), (3,1)]
```

**Saída:** 
```
[(0,3), (0,0), (3,1), (4,4)]
```

</details>

<details>
    <summary>🛠️ Problemas Padrão</summary>

### 53. Vértice, foco e diretriz de parábola
**Descrição:** Encontrar propriedades fundamentais de uma parábola y = ax² + bx + c.

**Passo a passo:**
1. Vértice X: Xᵥ = -b / (2a).
2. Vértice Y: Yᵥ = a(Xᵥ)² + b(Xᵥ) + c.
3. Foco: (Xᵥ, Yᵥ + 1/(4a)).
4. Diretriz: y = Yᵥ - 1/(4a).

**Entrada:** 
```
a = 1, b = -2, c = 1
```

**Saída:** 
```
Vértice = (1, 0), Foco = (1, 0.25), Diretriz: y = -0.25
```

### 54. Localização ótima (Mediana Geométrica)
**Descrição:** Encontrar ponto que minimiza distância total para N pontos.

**Passo a passo:**
1. Inicie com média das coordenadas.
2. Use algoritmo iterativo de Weiszfeld.
3. Atualize coordenadas em pequenos passos até convergência.

**Entrada:** 
```
[(0,0), (0,2), (2,0), (2,2)]
```

**Saída:** 
```
(1.0, 1.0)
```

### 55. Perímetro de formas em matriz binária
**Descrição:** Calcular perímetro de regiões de 1s em uma matriz.

**Passo a passo:**
1. Para cada célula com valor 1, verifique 4 vizinhos cardeais.
2. Cada vizinho que seja 0 (ou fora) contribui 1 ao perímetro.

**Entrada:**
```
[0, 1, 0, 0]
[1, 1, 1, 0]
[0, 1, 0, 0]
```

**Saída:** 
```
12
```

</details>

