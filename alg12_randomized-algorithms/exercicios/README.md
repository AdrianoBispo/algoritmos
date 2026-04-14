# Lista de Exercícios - Algoritmos Randomizados

O objetivo desta lista é fortalecer a sua lógica de programação explorando uma das áreas mais fascinantes da computação. Algoritmos randomizados utilizam uma fonte de aleatoriedade como parte de sua lógica, permitindo que problemas complexos sejam resolvidos de forma mais rápida ou com menos memória em comparação com abordagens puramente determinísticas.

**Conceitos Fundamentais:**

- **Algoritmos de Las Vegas:** Sempre produzem a resposta correta, mas o tempo de execução é aleatório (ex: Randomized QuickSort).
- **Algoritmos de Monte Carlo:** Têm um tempo de execução determinístico e rápido, mas possuem uma pequena probabilidade (controlável) de retornar uma resposta incorreta (ex: Algoritmo de Freivalds).
- **Rejection Sampling (Amostragem de Rejeição):** Técnica de gerar um número em um intervalo maior e rejeitar os resultados que caem fora do intervalo desejado.

Sinta-se à vontade para implementar as soluções utilizando a linguagem de programação de sua preferência (C, C++, Java, Python, JavaScript, Go, Ruby, etc.). Recomenda-se tentar entender a base matemática antes de ir para o código.

<details>
    <summary>🟢 Nível 1 - Fácil</summary>

Nesta seção, focaremos em manipulação direta de geradores de números pseudoaleatórios (PRNGs), conversão de probabilidades e distribuições simples.

### 1. Gerar um dos 3 valores de acordo com probabilidades dadas

**Descrição:** Você receberá três valores inteiros e suas respectivas probabilidades de ocorrência (a soma das probabilidades deve ser exatamente 100). Escreva uma função que retorne um desses valores, respeitando as probabilidades fornecidas.

**Aplicação Prática:** Muito comum no desenvolvimento de jogos (ex: _Loot drops_ ou _Gacha systems_), onde um item comum tem 70% de chance de cair, um raro 25% e um lendário 5%.

**Passo a Passo:**

1. Crie uma função que aceite três números (`v1`, `v2`, `v3`) e três probabilidades correspondentes (`p1`, `p2`, `p3`).
2. Calcule os "limites cumulativos". O limite 1 é `p1`. O limite 2 é `p1 + p2`.
3. Utilize o gerador padrão da sua linguagem para criar um número aleatório inteiro `R` entre 1 e 100 (inclusivo).
4. Verifique a faixa onde `R` caiu:
     - Se `R <= p1`, retorne `v1`.
     - Se `R > p1` e `R <= (p1 + p2)`, retorne `v2`.
     - Caso contrário (se `R > p1 + p2`), retorne `v3`.

**Dica de Implementação:** Para arrays genéricos de tamanho `N`, você pode usar um laço para somar as probabilidades até que a soma ultrapasse o valor sorteado `R`.

**Input:** Valores: `[10, 22, 35]`, Probabilidades: `[20, 30, 50]`

**Output:** Ao rodar a função 1000 vezes, o retorno esperado deve ser o número `10` em aproximadamente 200 vezes, `22` em ~300 vezes e `35` em ~500 vezes.

### 2. Gerar 0 e 1 com probabilidade de 25% e 75%

**Descrição:** Construa um gerador que retorne o número `0` com 25% de probabilidade e o número `1` com 75% de probabilidade. Você pode usar o gerador aleatório padrão da sua linguagem.

**Conceito:** Isso simula uma moeda "viciada" (biased coin). É a base para gerar distribuições desiguais a partir de uma distribuição uniforme.

**Passo a Passo:**

1. Utilize uma função de geração de números aleatórios uniforme que retorne um valor em ponto flutuante entre 0.0 e 1.0 (como `Math.random()` do JavaScript ou Java).
2. Armazene esse valor em uma variável `R`.
3. Avalie o limite matemático: como queremos 25%, o ponto de corte é 0.25.
4. Se `R < 0.25`, retorne `0`.
5. Se `R >= 0.25`, retorne `1`.

**Dica de Implementação:** Alternativamente, se usar inteiros de 1 a 100, retorne 0 se o número for de 1 a 25, e 1 se for de 26 a 100. Ambas as lógicas estão corretas.

**Input:** Nenhum. Apenas a invocação da função.

**Output:** `0` (em ~25% das chamadas) ou `1` (em ~75% das chamadas).

### 3. Implementar rand3() usando rand2()

**Descrição:** Suponha que você tenha acesso exclusivo a uma função restrita `rand2()` que gera apenas `0` ou `1` (com 50% de probabilidade cada). Crie uma função `rand3()` que gere `0`, `1` ou `2` com distribuição perfeitamente uniforme (33.3% para cada) usando APENAS a `rand2()`.

**Técnica Chave:** Isso introduz o conceito de _Rejection Sampling_. Como 3 não é potência de 2, não podemos simplesmente mapear bits diretamente sem distorcer as probabilidades.

**Passo a Passo:**

1. Chame `rand2()` duas vezes para gerar um número binário de 2 bits: `(rand2() << 1) | rand2()` ou matematicamente `2 * rand2() + rand2()`.
2. Os resultados possíveis são `0` (00), `1` (01), `2` (10) e `3` (11), cada um com exatos 25% de chance.
3. Como queremos resultados de 0 a 2, verificamos o valor obtido. Se for 0, 1 ou 2, aceitamos e retornamos.
4. Se o resultado for 3, _rejeitamos_ e voltamos ao passo 1 (use um laço `while`).

**Input:** Nenhum. (O programa deve consumir apenas chamadas de `rand2()`).

**Output:** `0`, `1` ou `2` de forma garantidamente equiprovável.

### 4. Paradoxo do Aniversário

**Descrição:** O Paradoxo do Aniversário mostra o quão contraintuitiva a matemática pode ser: em um grupo surpreendentemente pequeno, a chance de duas pessoas compartilharem o aniversário cresce rapidamente. Escreva um programa que calcule o número mínimo de pessoas em uma sala para atingir uma probabilidade `P` desejada.

**Aplicação Prática:** Usado em Criptografia para demonstrar colisões de Hash (Ataque do Aniversário), provando que precisamos de hashes muito grandes para evitar duplicações acidentais.

**Passo a Passo:**

1. Defina um contador `pessoas = 1`. A probabilidade de todos terem aniversários diferentes começa em 1.0 (100%).
2. Inicie um laço `while`. A cada iteração, adicione uma pessoa (`pessoas++`).
3. Calcule a probabilidade do novo indivíduo ter um aniversário _diferente_ de todos os presentes: `(365 - (pessoas - 1)) / 365.0`.
4. Atualize a probabilidade de todos serem diferentes multiplicando a probabilidade atual pelo fator calculado no passo anterior.
5. A probabilidade de _haver uma colisão_ é: `1.0 - probabilidade_todos_diferentes`.
6. Quando essa colisão ultrapassar o input fornecido pelo usuário, interrompa o laço e retorne `pessoas`.

**Input:** Probabilidade alvo em formato decimal ou percentual (ex: `0.50` para 50%).

**Output:** Para `0.50`, a saída correta será `23`. (Com apenas 23 pessoas há 50% de chance de colisão!).

### 5. Valor esperado de um array

**Descrição:** O valor esperado (ou expectativa) de uma variável aleatória é a média ponderada de todos os seus valores possíveis. Escreva um algoritmo que calcule essa métrica com base em um array de eventos e suas probabilidades.

**Passo a Passo:**

1. Verifique as restrições: O array de probabilidades deve somar exatamente 1.0 e ter o mesmo comprimento do array de valores. Se não tiverem, trate o erro adequadamente.
2. Inicialize uma variável `valor_esperado` com ponto flutuante igual a `0.0`.
3. Utilize um laço `for` para iterar sobre os índices `i` de 0 até `tamanho - 1`.
4. Em cada iteração, multiplique o valor na posição `i` pela probabilidade na posição `i` (`valores[i] * probabilidades[i]`).
5. Adicione este produto ao `valor_esperado`.
6. Retorne o acumulador `valor_esperado` ao fim do laço.

**Input:** `Valores = [10, 20, 30]`, `Probabilidades = [0.2, 0.5, 0.3]`

**Output:** `21.0`. (O cálculo é: `10*0.2 + 20*0.5 + 30*0.3 = 2 + 10 + 9 = 21`).

### 6. Embaralhar um baralho de cartas

**Descrição:** Dado um array representando um baralho tradicional de 52 cartas em ordem crescente, crie uma função que embaralhe-o de forma que todas as permutações sejam igualmente prováveis.

**Atenção:** Implementações ingênuas geram viés estatístico. Faremos a versão básica que introduz o aluno ao pensamento correto.

**Passo a Passo:**

1. Carregue um array de 52 elementos (ex: números de 1 a 52).
2. Comece um laço do final do array para o começo. Faça uma variável `i` ir de `51` até `1`.
3. Para cada iteração no índice `i`, gere um índice pseudoaleatório `j` no intervalo fechado de `0` a `i`.
4. Troque (swap) o elemento em `array[i]` com o elemento sorteado em `array[j]`.
5. O algoritmo garante que as cartas no fim do array já estão em posições fixas, randomizando as restantes.

**Input:** Array ordenado `[1, 2, 3, ..., 52]`.

**Output:** Array contendo os mesmos elementos alterados aleatoriamente, ex: `[42, 3, 17, 51, 8, ...]`.

### 7. Gerar CAPTCHA e verificar

**Descrição:** CAPTCHA (_Completely Automated Public Turing test to tell Computers and Humans Apart_) é muito usado em segurança web. Crie um protótipo de sistema que gera uma string de desafio pseudoaleatória alfanumérica e permita validação contra uma entrada do usuário.

**Passo a Passo:**

1. Defina o conjunto do universo. Crie uma string contendo o "alfabeto" permitido: `A-Z`, `a-z`, `0-9`.
2. Para gerar o CAPTCHA, inicialize uma string vazia `desafio`.
3. Faça um laço que rode `n` vezes (onde `n` é o comprimento pedido).
4. Em cada rodada, gere um índice aleatório de `0` até `tamanho do alfabeto - 1`. Acrescente o caractere desse índice à string `desafio`.
5. Exiba o `desafio` no console de forma clara.
6. Leia o input via console digitado pelo usuário.
7. Aplique a verificação lógica. Retorne `Booleano`.

**Input:** Um tamanho de string `n` (ex: `6`) para geração. Depois, simule o input do usuário.

**Output:** Um texto gerado, por exemplo, "zX91Qp", seguido pelo resultado: `True` (se correto) ou `False` (se houver erro).

### 8. Índice do elemento de maior ocorrência com probabilidade igual

**Descrição:** Você precisa recomendar um elemento que ocorre com maior frequência. Se houver empate, o sistema deve ser justo e escolher aleatoriamente entre os elementos mais frequentes.

**Passo a Passo:**

1. Inicialmente, use um mapa ou dicionário para calcular a frequência de todos os elementos e descobrir qual é a frequência máxima.
2. Descubra a contagem de ocorrência mais alta.
3. Faça uma segunda passagem iterando pelo array. Toda vez que encontrar um elemento cuja frequência geral for igual à máxima, armazene seu índice em um array auxiliar chamado `candidatos`.
4. Com a lista de `candidatos` fechada, gere um índice aleatório `R` indo de `0` a `tamanho_dos_candidatos - 1`.
5. Retorne o valor contido em `candidatos[R]`.

**Input:** `array = [1, 2, 2, 3, 2, 4, 1, 1]` (Note que o `1` e o `2` aparecem três vezes cada).

**Output:** A lógica deve agrupar as localizações do `1` e do `2` e retornar uma delas randomicamente.

### 9. Busca Binária Randomizada

**Descrição:** A busca binária convencional sempre testa o "meio" de um array ordenado. A Busca Binária Randomizada seleciona o pivô testado de forma aleatória dentro dos limites de pesquisa.

**Passo a Passo:**

1. Certifique-se de que o algoritmo receba um array previamente ordenado.
2. Inicie os dois limites: ponteiro `inicio = 0` e ponteiro `fim = tamanho_do_array - 1`.
3. Use um laço `while (inicio <= fim)`.
4. Gere um valor `pivô = numero_aleatorio(inicio, fim)`.
5. Se `array[pivô] == alvo`, retorne o `pivô`.
6. Se `array[pivô] > alvo`, modifique `fim = pivô - 1`.
7. Se `array[pivô] < alvo`, modifique `inicio = pivô + 1`.
8. Se o `inicio` ultrapassar o `fim`, o alvo não está lá. Retorne `-1`.

**Input:** Array ordenado `[2, 5, 8, 12, 16, 23, 38, 56, 72, 91]`, Alvo `23`.

**Output:** A função deve retornar o Índice `5`.

</details>

<details>
    <summary>🟠 Nível 2 - Médio</summary>

Aqui, a complexidade matemática e algorítmica se eleva. Utilizaremos aleatoriedade para otimizar ordenação (QuickSort), simular processos complexos (Monte Carlo) e corrigir viés estocástico.

### 10. Criar uma moeda justa a partir de uma moeda viciada

**Descrição:** Este problema foi formulado por John von Neumann. Imagine que você tem uma função `moedaViciada()` que retorna `0` com uma probabilidade desconhecida _p_ e `1` com probabilidade _(1-p)_ (por exemplo, 70% Coroa e 30% Cara). Usando APENAS chamadas dessa função, crie uma função `moedaJusta()` que garanta exatos 50% de chance para cara ou coroa.

**Passo a Passo:**

1. O segredo de von Neumann foca em "pares independentes". Se você joga a moeda viciada duas vezes, as probabilidades dos resultados conjuntos são:
     - 0 seguido de 0: p×p
     - 1 seguido de 1: (1−p)×(1−p)
     - 0 seguido de 1: p×(1−p)
     - 1 seguido de 0: (1−p)×p

2. Observe que as probabilidades de obter `(0,1)` e `(1,0)` são estritamente iguais, independentemente do viés _p_.
3. Lance a `moedaViciada()` duas vezes, lendo em sequência `L1` e `L2`.
4. Se `L1 == 0` e `L2 == 1`, retorne `0`.
5. Se `L1 == 1` e `L2 == 0`, retorne `1`.
6. Se saírem resultados idênticos (00 ou 11), repita todo o processo usando um laço `while (true)`.

**Input:** Nenhum dado.

**Output:** `0` ou `1` com distribuição de 0.5 perfeita (50%).

### 11. Embaralhar um array usando Fisher-Yates (Knuth Shuffle)

**Descrição:** O algoritmo de Fisher-Yates é considerado o estado da arte para permutações pseudoaleatórias justas. Seu objetivo é provar o design de memória in-place, garantindo complexidade de tempo linear O(N) e espaço O(1) constante.

**Passo a Passo:**

1. O algoritmo divide o array em duas partes: elementos já selecionados para a permutação e elementos que faltam selecionar.
2. Inicie o loop com a variável `i` indo do último índice até `1` (percorra de trás para frente).
3. Obtenha um inteiro randômico `j` no intervalo `0 <= j <= i`.
4. Troque simultaneamente o conteúdo em `array[i]` com o que está em `array[j]`.
5. A cada iteração, o elemento que vai parar na extremidade de trás "congela" e não volta a ser mexido.

**Input:** Array original (ex: `[10, 20, 30, 40, 50]`).

**Output:** O mesmo array modificado para conter uma permutação justa aleatória (ex: `[30, 50, 10, 40, 20]`).

### 12. Número esperado de tentativas até o sucesso

**Descrição:** Aplicação pura de distribuição geométrica. Dada a probabilidade percentual (ou fracionária) de sucesso em um cenário qualquer, simule empiricamente quantas tentativas precisam ocorrer em média até obter esse sucesso.

**Passo a Passo:**

1. O valor teórico esperado é o recíproco da probabilidade: Esperança = `1 / p`. Salve isso em `valor_teorico`.
2. Para provar se isso é verdade, crie uma simulação de Monte Carlo rodando 100.000 vezes.
3. Para cada simulação, inicialize `tentativas = 1`. Sorteie um número. Se falhar, adicione `tentativas++` e jogue novamente em um `while`. Se for sucesso, o laço para e `tentativas` se junta à variável global `soma_tentativas`.
4. Ao final das 100.000 simulações, faça `soma_tentativas / 100000.0` para extrair a média empírica.
5. Imprima e compare a simulação com a matemática teórica.

**Input:** Probabilidade de sucesso `p` (ex: `0.125` representando 1/8).

**Output:** Valor simulado (próximo de `8.00`) e Teórico (`8.00`).

### 13. Sugeridor de Senha Forte

**Descrição:** Sistemas atuais exigem políticas rigorosas de senha. Escreva um programa que gere uma senha cumprindo 100% dos requisitos (conter 4 classes de caracteres), possua um tamanho mínimo e seja imprevisível.

**Conceito de Segurança:** Em produção séria, deveríamos importar CSPRNGs (Cryptographically Secure PRNGs), como `secrets` no Python ou `crypto.getRandomValues()` no JavaScript. Contudo, usaremos a lógica aqui.

**Passo a Passo:**

1. Crie 4 bancos de dados de strings: Letras maiúsculas, minúsculas, dígitos e símbolos.
2. Defina uma lista de caracteres em branco que será a nova senha.
3. Como requisito inicial obrigatório, pegue 1 caractere randômico de CADA um dos 4 bancos e insira na lista.
4. Para as posições restantes (do tamanho `n - 4`), concatene todos os 4 bancos em uma única "super string" e tire caracteres aleatórios dali até preencher o tamanho `n`.
5. Problema grave: Sua senha tem um padrão detectável. Solução: Passe o algoritmo Fisher-Yates na sua lista de senha para mascarar essas posições.
6. Converta a lista final em string e retorne.

**Input:** Número inteiro do tamanho requisitado `n = 14`.

**Output:** Uma string forte, caótica e desordenada como `"aK9#zQm$pL2*B7"`.

### 14. QuickSort usando Pivô Aleatório

**Descrição:** O clássico QuickSort brilha na complexidade de tempo médio O(NlogN). Porém, se você fornece um array já ordenado e o pivô é sempre o canto do array, a performance cai para O(N²). Implemente o _Randomized QuickSort_ que imuniza o algoritmo contra ataques determinísticos.

**Passo a Passo:**

1. Estruture a lógica macro do QuickSort: recebe o array, índice `inicio` e `fim`. Retorna se `inicio >= fim`.
2. A principal mudança ocorre na rotina de particionamento.
3. Calcule `índice_randomico = random(inicio, fim)`.
4. Force uma troca do valor neste índice com o elemento em `fim`.
5. Siga o particionamento normal (Lomuto) escolhendo o elemento em `fim` como pivô.
6. Chame QuickSort recursivamente para `inicio` até `pivô - 1` e `pivô + 1` até `fim`.

**Input:** Um array desfavorável como `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, ... 1000]`.

**Output:** O array é ordenado perfeitamente sem sobrecarregar a pilha de recursão.

### 15. Operações em Matrizes Esparsas

**Descrição:** Em simulações físicas ou Machine Learning, trabalha-se com Matrizes Esparsas: grades gigantes onde 99% do conteúdo é zero. Escreva uma representação lógica e calcule uma operação de adição.

**Passo a Passo:**

1. Crie uma estrutura `MatrizEsparsa` que armazena dados apenas onde há valores relevantes (um Dicionário/Map onde as chaves são coordenadas como `"linha,coluna"` e o valor interno é o dado).
2. Para popular testes, defina dimensões (1000×1000) e insira apenas 20 pontos sorteando aleatoriamente (linha, coluna e um valor flutuante).
3. Faça a operação de Adição `M1 + M2`. Se a coordenada existir em ambas, some. Se existir em apenas uma, copie. Tudo que é "0" será ignorado.

**Input:** Duas matrizes esparsas randomizadas.

**Output:** O dicionário fundido com eficiência temporal ligada apenas à contagem de elementos não-zero.

### 16. Estimando o Valor de Pi usando Monte Carlo

**Descrição:** O número irracional π (aprox. 3.14159) pode ser estimado geometricamente. Utilizaremos a algoritmo de Monte Carlo (atirar dardos aleatórios) para aproximar π.

**Conceito Teórico:** A área de um círculo é A=π×r². A área de um quadrado envolta é 4×r². A razão é π/4. Ao atirar dardos aleatórios, a estatística nos dá a aproximação.

**Passo a Passo:**

1. Inicie um valor alto para `N` simulando "tiros" (ex: N = 10 milhões). Inicie `dardos_no_circulo = 0`.
2. Em um `for loop` extensivo de 0 até `N`:
3. Gere um valor `x` randômico de 0.0 até 1.0.
4. Gere um valor `y` randômico de 0.0 até 1.0.
5. Calcule a distância do "dardo" em relação a (0,0). Verifique se `x² + y² ≤ 1.0`.
6. Se verdadeiro, o dardo perfurou a área circular e incremente `dardos_no_circulo`.
7. Faça a equação `Pi_Estimado = 4.0 * ((float)dardos_no_circulo / N)`.

**Input:** Quantidade `N` desejada (menos iterações significam menos precisão).

**Output:** Algo entre `3.141...` e `3.142...`. Conforme a máquina roda simulações maiores, as casas decimais de precisão se tornam definitivas.

### 17. Implementar rand12() usando rand6() em uma linha

**Descrição:** Dado um gerador uniforme `rand6()` que devolve valores de 1 a 6, construa uma expressão em uma única linha capaz de transformar a distribuição garantindo um resultado de 1 até 12.

**Entendimento Prévio:** Somar `rand6() + rand6()` gerará curva de Bell, concentrando ao redor de 7. Multiplicação por 2 gera apenas números pares.

**Passo a Passo:**

1. Para dobrar a área sem distorcer probabilidade, use bits binários para alterar distribuições.
2. Use o módulo par/ímpar sobrepondo chamadas: `(rand6() % 2)` gera uma "moeda" com 0 ou 1.
3. A lógica é: `(Resultado_do_Bloco * Multiplicador) + Valor_Base`.
4. Equação Final: `((rand6() % 2) * 6) + rand6()`. O bloco da esquerda gera `0` ou `6`. O lado direito acrescenta `1` a `6`. Unindo, ele pode gerar uniformemente `1` a `12`.

**Input:** Utilização fechada das chamadas `rand6()`.

**Output:** Resultados contínuos `[1,2,3,4,5,6,7,8,9,10,11,12]`, provando expansão não paramétrica.

</details>

<details>
    <summary>🔴 Nível 3 - Difícil</summary>

Este bloco foca em manipulação extrema de distribuições, fluxos contínuos de dados (Reservoir Sampling), probabilidades em grafos (Corte Mínimo) e verificação probabilística com tolerância a falhas.

### 18. Gerar Inteiro de 1 a 7 com Probabilidade Igual

**Descrição:** Você tem `rand5()` (entre 1 e 5) e deseja expandir para `rand7()`. Como 7 não divide matrizes limpas geradas por múltiplos de 5, usaremos _Rejection Sampling_ pesado.

**Passo a Passo:**

1. Imagine uma tabela 2D de tamanho 5×5 combinando duas chamadas. A tabela tem 25 células (1 a 25).
2. Para traduzir duas chamadas linearmente: `val = 5 * (rand5() - 1) + rand5()`. Todo valor de 1 a 25 tem chance unânime (1/25).
3. O múltiplo de 7 seguro é 21 (7 × 3). Mapeie 1 a 21 sem privilégios.
4. Use laço infinito `while (true)`. Calcule o polinômio.
5. Se `val > 21`, ignore a rodada brutalmente (~16% de rejeição). O ciclo reata.
6. Senão, retorne `(val % 7) + 1`.

**Input:** Dependência em API limitante de gerador.

**Output:** Entrega nivelada de 1 a 7 inclusos, sem distorções.

### 19. Implementar Gerador random-0-6 Usando random-0-1

**Descrição:** Semelhante ao `rand3() usando rand2()`, pede-se gerar inteiros de 0 até 6 de forma uniforme usando apenas `rand01()`.

**Passo a Passo:**

1. Calcule quantos estados a solução abrange: 7 possibilidades.
2. Descubra a menor potência de 2 que supera: 2³=8 abriga 7. Combine 3 chamadas.
3. Componha numericamente: `(bit3 * 4) + (bit2 * 2) + (bit1 * 1)`.
4. Os retornos abrangem 0 a 7, todos com 12.5%.
5. Aplique Amostragem de Rejeição: descartar se resultado for 7.
6. Se 0 a 6, retorne.

**Input:** Ausência total, dependência dos bits aleatórios.

**Output:** Distribuição achatada de 0 a 6.

### 20. Número Aleatório de um Fluxo, com Espaço O(1) (Reservoir Sampling I)

**Descrição:** Você recebe um fluxo contínuo (streaming) cujo tamanho final NUNCA se consolida até acabar. Indique qual arquitetura extrai um único pacote preservando espaço O(1).

**Conceito:** Se o fluxo é contínuo e você não pode armazenar nada além do selecionado, como garantir que o milésimo dado tenha a mesma probabilidade do primeiro?

**Passo a Passo:**

1. Extraia o primeiro item e salve em `resultado`. Eleja `contador = 1`.
2. Para toda transmissão continuada: avance `contador`.
3. Invoque gerador: `j` no intervalo `[0, contador - 1]`.
4. Se `j == 0`, sobrescreva `resultado` com o novo item.
5. Pela indução, na N-ésima etapa, o dado novo subsiste com exatos 1/N de chance.

**Input:** Simulação despachando fluxo contínuo.

**Output:** Captura unitária desprovida de viés de posição.

### 21. Gerador de Números com Distribuição Arbitrária Ponderada

**Descrição:** Frequente em balanços de RPGs ou motores de IA. Como desenvolver um sistema que respeita prioridades baseadas em Pesos. Valores com peso 10 materializam 10 vezes mais frequentes do que peso 1.

**Passo a Passo:**

1. Processe conversão primária do array de "pesos", desenvolvendo "Cálculos de Prefixos Acumulados". Se `pesos: [1, 3, 2]`, resulta em `prefix_sum: [1, 4, 6]`.
2. Verifique o limiar global (6) e sorteie números até esse total.
3. Para otimizar em limites colossais, implemente Busca Binária na matriz `prefix_sum`.
4. Repasse as saídas associadas pelos indexadores.

**Input:** `Itens: ["Ouro", "Madeira", "Carvão"]`, `Pesos: [20, 50, 80]`.

**Output:** Retornos proporcionais seguindo a probabilidade ponderada.

### 22. Reservoir Sampling (Geral)

**Descrição:** Seleção aleatória de k elementos de um fluxo de N elementos onde N nunca será revelado, resolvendo em espaço O(k) otimizado.

**Passo a Passo:**

1. Inicialize lista `reservatorio` dimensionada com tamanho k.
2. Transfira integralmente os k primeiros limites ao buffer principal.
3. Inicie a partir do cursor `i = k + 1`.
4. A cada ciclo, gere `j` aleatório entre `0` e `i`.
5. Se `j < k`, substitua `reservatorio[j]` com `stream[i]`.
6. Término: entrega controlada do array.

**Input:** Stream e `k = 5` por exemplo.

**Output:** Array do tamanho k perfeitamente distribuído.

### 23. Linearidade da Expectativa

**Descrição:** Consagre por ensaio empírico computacional a propriedade: _E[X + Y] = E[X] + E[Y]_, mostrando que o princípio aditivo mantém integridade mesmo com variáveis correlacionadas.

**Passo a Passo:**

1. Estabeleça as médias teóricas de duas amostras independentes (ex: Dado com 6 faces e outro com 4).
2. Valor acumulador de alta magnitud de ciclos iterativos (10⁶ ou mais).
3. Efetue ciclo gerador com amostragem aleatória controlada.
4. Registre as somas das instâncias parciais.
5. Divida as cargas somadas pelo total de laços. Imprima a igualdade.

**Input:** Dois escopos de limiares diferentes.

**Output:** Demonstração que ambos convergem ao infinito com precisão de 4+ casas decimais.

### 24. Algoritmo de Karger para Corte Mínimo

**Descrição:** Em topologias de grafos não orientados, existe o _Corte Mínimo Global_: as menores arestas cuja remoção paralisa todo o sistema em duas partições disjuntas. O Algoritmo estocástico de David Karger aborda isso via probabilidade orgânica. _Atenção:_ É algoritmo Monte Carlo, necessitando repetição para alta confiabilidade.

**Passo a Passo:**

1. Defina representação topológica de grafos com listas de adjacência.
2. Mantenha iteratividade enquanto quantitativo de "nós" ainda exceder 2.
3. Aleatoriamente selecione uma aresta.
4. "Contração": Mescle os dois vértices conectados gerando um _super nó_. Mantenha arestas remanescentes ligadas.
5. Em operações, garanta filtragem purgando "Loops" (rotas que retornam para si mesmas).
6. Após terminar, mensure quantidade de arestas resultantes entre os 2 super pontos.
7. Encapsule iterando múltiplas vezes para confirmar o menor corte global.

**Input:** Matrizes topológicas representativas.

**Output:** O número absoluto do corte global.

### 25. Nó Aleatório de uma Lista Encadeada

**Descrição:** Solução especializada do Reservoir Sampling em "Linked List", ignorando alocamentos contíguos. O tamanho é desconhecido no começo.

**Passo a Passo:**

1. Abstenha referencial `k=1`. Assuma `resultado` como ponteiro Head.
2. Estabeleça travessia cega através de `next` até encontrar `NULL`.
3. Mantenha contador "n" incrementado para cada nó.
4. Ao referenciar nó n, gere número aleatório entre `[0, n-1]`.
5. Se `R == 0`, mude `resultado` para o nó atual.
6. Retorne quando a lista terminar.

**Input:** Lista como `10 -> 20 -> 30 -> 40 -> 50`.

**Output:** 20% de probabilidade para cada nó.

### 26. Nó Aleatório de uma Árvore

**Descrição:** Desafio hierárquico em "Binary Search Tree" permitindo equiparidade probabilística em todos os nós sem favorecer ramos densos.

**Passo a Passo:**

1. Otimização: Reescrever nós incluindo referências paramétricas. Na pré-parametrização das sub-raízes, crie contagem do peso armazenando "Tamanho dos filhos".
2. Posicionado na invocação Root, gere número estatístico com limitante contíguo de `[1, Tamanho armazenado]`.
3. Direcionamento recursivo: Verifique se sorteado reside na área do filho Esquerdo (se sorteado <= Tamanho Esquerdo). Redirecione recursivamente.
4. Se resultado iguala (Tamanho Esquerdo + 1), obteve êxito. Retorne o nó.
5. Sem acerto, delegue computação recursiva na área direita.

**Input:** Árvores desbalanceadas estruturais.

**Output:** Devolução equânime sem desvio numa matriz.

### 27. Algoritmo de Freivalds para Verificar Produto Matricial

**Descrição:** Aplicação de Algoritmo Monte Carlo para tolerância de performance em verificação matricial. Ao ter output C, teste velozmente se C = A×B evitando O(N³) determinístico e entregando O(N²) probabilístico.

**Passo a Passo:**

1. Traduza verificação em álgebra: A∗B∗r−C∗r\=0.
2. Construa estruturalmente um limitador unificado randomizado `r`, preenchido entre 0 e 1.
3. Propague cálculos sem fazer AxB. Encontre P1​ calculando B∗r.
4. Proceda encontrando P2​ calculando A∗P1​.
5. Compute limítrofe final P3​ verificando C∗r.
6. Iterando componentes dos vetores, confirme igualdade entre P2​ e P3​. Qualquer diferença encerra retornando "Falso".
7. Se similares, aumente confiabilidade iterando K vezes com novas sementes (Monte Carlo reduz taxa de erro pela metade a cada K).

**Input:** Matrizes A, B e a C.

**Output:** Resultados booleanos com tolerância probabilística.

### 28. Gerador de Labirinto Acíclico Aleatório

**Descrição:** Aplicação em malhas geradoras espaciais aleatórias para videogames (Perfect Mazes sem ilhas). Abordando Backtracker iterativo.

**Passo a Passo:**

1. Construa matriz bidimensional representativa populada de estruturas isoladas (paredes lotando o espaço 2D).
2. Estipule origem do "Start". Assinale a quebra com parâmetro "Aberto".
3. Extraia conjunto de nós cardeais (Cima, Baixo, Esquerda e Direita) baseado no atual iterador.
4. Aplique Fisher-Yates shuffle sobre direções misturando ordem.
5. Processe varredura para referências em todas as direções embaralhadas. Se a malha direcional for inexplorada e fechada: demula barreiras, torne abertas e reinicie recursão DFS passando nova coordenada.

**Input:** Grade X,Y em inteiros.

**Output:** Tabela preenchida atestando 0/1 limitando percursos labirínticos acíclicos.

</details>

