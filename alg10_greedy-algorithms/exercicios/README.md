# Lista de Exercícios - Algoritmos Gananciosos (Greedy Algorithms)

Este documento contém uma lista de exercícios focada em Algoritmos Gananciosos, organizados por nível de dificuldade e por categorias de aplicação. O objetivo é fortalecer a lógica de programação. Você pode implementar as soluções na linguagem de sua preferência (C, C++, Java, Python, JavaScript, Go, etc).

<details>
    <summary>🟢 Nível 1 - Fácil</summary>

<p>

### 1. Mochila fracionária

**Descrição:** Dado um conjunto de itens com peso e valor, determine a quantidade máxima de valor que pode ser colocada em uma mochila de capacidade `W`. É permitido quebrar os itens (pegar frações deles).

**Passo a Passo:**
1. Calcule a razão `valor / peso` para cada item.
2. Ordene os itens em ordem decrescente com base nessa razão.
3. Iterando pelos itens ordenados, adicione a quantidade total do item se ele couber na mochila.
4. Se o item não couber inteiro, adicione a fração que preenche a capacidade restante e encerre.

**Entrada:** `W = 50`, Itens = `[(valor: 60, peso: 10), (valor: 100, peso: 20), (valor: 120, peso: 30)]`

**Saída:** `240.0`

### 2. Número mínimo de notas para uma soma dada

**Descrição:** Dado um valor, encontre o número mínimo de cédulas para formá-lo (exemplo: notas de 100, 50, 20, 10, 5, 2, 1).

**Passo a Passo:**
1. Ordene as notas em ordem decrescente.
2. Divida o valor pela maior nota possível e some a quantidade.
3. Pegue o resto e passe para a próxima nota menor.

**Entrada:** Valor = `121`

**Saída:** `3` (1x100, 1x20, 1x1)

### 3. Custo mínimo para reduzir o array a tamanho 1

**Descrição:** Dado um array, reduza-o a um único elemento realizando operações. Em cada passo, escolha dois elementos, remova-os e insira a soma deles. O custo da operação é a soma. Minimize o custo total.

**Passo a Passo:**
1. Insira todos os elementos do array em uma Fila de Prioridade (Min-Heap).
2. Enquanto a fila tiver mais de 1 elemento, remova os dois menores.
3. Some-os, adicione a soma ao custo total e insira o resultado de volta na fila.

**Entrada:** `[4, 3, 2, 6]`

**Saída:** `29` (Passos: 2+3=5 (custo 5). 4+5=9 (custo 9). 6+9=15 (custo 15). Total = 5+9+15 = 29)

### 4. Rotações mínimas para cadeado circular

**Descrição:** Você tem um cadeado circular com dígitos (0-9). Dada a combinação atual e a senha desejada, encontre o número mínimo de rotações para destrancar.

**Passo a Passo:**
1. Compare os dígitos da combinação atual com os da senha desejada, um por um.
2. Para cada posição, calcule a diferença absoluta direta: `abs(atual - desejado)`.
3. Calcule a distância rotacionando pelo outro lado: `10 - abs(atual - desejado)`.
4. Some o menor valor entre as duas opções para cada dígito ao total de rotações.

**Entrada:** Atual = `"285"`, Desejado = `"714"`

**Saída:** `11` (|2-7| reverso = 5; |8-1| reverso = 3; |5-4| direto = 1. Total = 9)

### 5. Máximo de números compostos para formar n

**Descrição:** Dado um inteiro `n`, encontre o número máximo de números compostos (não-primos maiores que 1) cuja soma seja exatamente `n`.

**Passo a Passo:**
1. O menor número composto é 4. Para maximizar a quantidade, use o máximo de 4s possível.
2. Se `n < 4`, retorne -1. Se `n % 4 == 0`, a resposta é `n / 4`.
3. Se resto = 1, resposta é `(n - 9) / 4 + 1`. Se resto = 2, `(n - 6) / 4 + 1`. Se resto = 3, `(n - 15) / 4 + 2`.

**Entrada:** `90`

**Saída:** `22`

### 6. Menor subconjunto com soma maior

**Descrição:** Dado um array de inteiros não negativos, encontre o tamanho do menor subconjunto cuja soma seja estritamente maior que a soma do restante do array.

**Passo a Passo:**
1. Calcule a soma total de todos os elementos do array.
2. Ordene o array em ordem decrescente.
3. Percorra o array somando os maiores elementos até a soma ser `> (soma_total - soma_atual)`.

**Entrada:** `[3, 1, 7, 1, 4]`

**Saída:** `2` (Subconjunto [7, 4] soma 11, o resto soma 5)

### 7. Distribuir cookies

**Descrição:** Você distribui cookies para crianças. Cada criança tem um fator de ganância `g` e cada cookie tem tamanho `s`. Maximize crianças contentes onde `s >= g`.

**Passo a Passo:**
1. Ordene o array de ganância e o array de tamanho dos cookies (crescente).
2. Use dois ponteiros: um para crianças, outro para cookies.
3. Se `cookie >= criança`, criança satisfeita (avança ambos os ponteiros). Senão, avança só o cookie.

**Entrada:** Crianças `[1, 2, 3]`, Cookies `[1, 1]`

**Saída:** `1`

### 8. Comprar o máximo de ações

**Descrição:** Dado preços de ações onde no dia `i` você pode comprar no máximo `i` ações. Com orçamento `K`, maximize as compras.

**Passo a Passo:**
1. Armazene pares `(preço, limite_de_compra)` baseados no dia.
2. Ordene os pares pelo menor preço.
3. Compre o máximo possível do preço atual limitando a `K / preço` e ao `limite_de_compra`. Deduza de `K`.

**Entrada:** Preços = `[10, 7, 19]`, `K = 45`

**Saída:** `4`

### 9. Soma máxima de diferenças consecutivas

**Descrição:** Reorganize os elementos de um array para maximizar a soma da diferença absoluta entre elementos consecutivos (de forma circular).

**Passo a Passo:**
1. Ordene o array.
2. Crie um array alternando menor não usado com maior não usado.
3. Some a diferença absoluta consecutiva, incluindo o último com o primeiro.

**Entrada:** `[4, 2, 1, 8]`

**Saída:** `18`

### 10. Custo mínimo e máximo para comprar tudo

**Descrição:** Para cada doce comprado, a loja dá `K` doces grátis. Ache o custo mínimo e máximo para comprar `N` doces.

**Passo a Passo:**
1. Ordene os preços.
2. Para Mínimo: Compre os mais baratos e pegue os mais caros de graça.
3. Para Máximo: Compre os mais caros e pegue os mais baratos de graça.

**Entrada:** Preços = `[3, 2, 1, 4]`, `K = 2`

**Saída:** Min: `3`, Max: `7`

### 11. Soma máxima igual em três pilhas

**Descrição:** Três pilhas de alturas variadas. Remova o topo até que a soma de todas seja igual e máxima.

**Passo a Passo:**
1. Calcule a soma de cada pilha.
2. Identifique qual tem a maior soma e remova o elemento do topo dessa pilha.
3. Repita até que as três somas se igualem.

**Entrada:** P1 = `[3,1,1,1]`, P2 = `[4,3]`, P3 = `[2,5,4]`

**Saída:** `5`

### 12. Subconjunto de produto mínimo de um array

**Descrição:** Dado um array, ache o subconjunto com o menor produto possível.

**Passo a Passo:**
1. Conte negativos, zeros e o maior negativo. Multiplique todos os valores não nulos.
2. Se há zeros e nenhum negativo, a resposta é `0`.
3. Se a quantidade de negativos for par, divida o produto total pelo maior negativo para deixá-lo negativo.

**Entrada:** `[-1, -1, -2, 4, 3]`

**Saída:** `-24` (Pega todos)

### 13. Maximizar a soma do array após K negações

**Descrição:** Negue `K` elementos do array para maximizar a soma total.

**Passo a Passo:**
1. Ordene o array.
2. Enquanto `K > 0` e houver números negativos, negue o menor número negativo, e `K--`.
3. Se `K` sobrou ímpar, negue o menor número absoluto do array.

**Entrada:** `[-2, 0, 5, -1, 2]`, `K = 4`

**Saída:** `10`

### 14. Soma mínima do produto de dois arrays

**Descrição:** Permute dois arrays A e B para minimizar a soma de `A[i] * B[i]`.

**Passo a Passo:**
1. Ordene o array A em ordem crescente.
2. Ordene o array B em ordem decrescente.
3. O produto de pequenos com grandes minimiza a soma global.

**Entrada:** A = `[3,1,1]`, B = `[6,5,4]`

**Saída:** `23` (1×6 + 1×5 + 3×4)

### 15. Soma mínima das diferenças absolutas de pares de dois arrays

**Descrição:** Ache o menor `soma(|A[i] - B[i]|)`.

**Passo a Passo:**
1. Ordene A em ordem crescente.
2. Ordene B em ordem crescente.
3. Some a diferença absoluta de posições correspondentes.

**Entrada:** A = `[4,1,8,7]`, B = `[2,3,6,5]`

**Saída:** `6`

### 16. Ordenar array com reversão em torno do meio

**Descrição:** Verifique se um array pode ser ordenado apenas revertendo um pedaço no meio.

**Passo a Passo:**
1. Ache a primeira irregularidade na esquerda e na direita.
2. Reverta esse pedaço entre a esquerda/direita e verifique se o array ficou ordenado.

**Entrada:** `[1, 2, 5, 4, 3]`

**Saída:** `True` (Revertendo [5, 4, 3])

### 17. Soma das áreas de retângulos possíveis para um array

**Descrição:** Array de comprimentos de gravetos. Maximize a área total dos retângulos possíveis. A diferença máxima entre pares é 1.

**Passo a Passo:**
1. Ordene o array em ordem decrescente.
2. Itere pareando elementos `A[i]` e `A[i+1]` se `A[i] - A[i+1] <= 1`. Quando achar 2 pares, calcule a área.

**Entrada:** `[10, 10, 10, 10, 11, 10, 11, 10]`

**Saída:** `110` (10×11)

### 18. Maior array lexicográfico com no máximo K trocas consecutivas

**Descrição:** Troque elementos vizinhos (máximo K vezes) para gerar o array "maior" visualmente (maiores na frente).

**Passo a Passo:**
1. Para cada posição, procure o maior elemento acessível num limite de K de distância.
2. Mova o maior para essa posição fazendo trocas consecutivas, reduza K pela distância e repita.

**Entrada:** `[1, 2, 4, 3]`, `K = 2`

**Saída:** `[4, 1, 2, 3]`

### 19. Partição em duas subarrays com diferença máxima de somas

**Descrição:** Divida em 2 arrays de tamanho K e (N – K), maximizando a diferença das somas.

**Passo a Passo:**
1. Ordene o array.
2. Para diferença máxima, uma metade deve ser a menor possível. Se `K < N/2`, some os K primeiros.

**Entrada:** `[8, 4, 5, 2, 10]`, `K = 2`

**Saída:** `17` (Soma(8,10,5)=23 menos Soma(2,4)=6)

</p>

</details>

<details>
    <summary>🟠 Nível 2 - Médio</summary>

<p>

### 20. Seleção de atividades

**Descrição:** Selecione o máximo de atividades sem sobreposição de tempo.

**Passo a Passo:**
1. Ordene as atividades pelo horário de término.
2. Aceite a primeira. Para a próxima, aceite se iniciar depois ou no mesmo momento que a anterior terminou.

**Entrada:** Início `[10, 12, 20]`, Fim `[20, 25, 30]`

**Saída:** `2`

### 21. Jump Game

**Descrição:** Array de alcance máximo de salto. Ache o mínimo de saltos para o fim.

**Passo a Passo:**
1. Acompanhe `alcance_atual` e `max_alcance` futuro.
2. Ao iterar, atualize `max_alcance`. Ao atingir `alcance_atual`, dê um salto e atualize `alcance_atual = max_alcance`.

**Entrada:** `[2, 3, 1, 1, 4]`

**Saída:** `2`

### 22. Sequenciamento de tarefas

**Descrição:** Tarefas com lucros e prazos (1 unidade de tempo cada). Maximize lucro.

**Passo a Passo:**
1. Ordene decrescente por lucro.
2. Agende a tarefa no tempo livre mais tarde possível antes do seu prazo.

**Entrada:** `[P:2/L:100, P:1/L:19, P:2/L:27, P:1/L:25]`

**Saída:** 2 tarefas, Lucro `127`

### 23. Fração egípcia

**Descrição:** Quebre uma fração em soma de frações unitárias distintas.

**Passo a Passo:**
1. Ache o teto de `dr/nr` (`t = dr/nr + 1`).
2. Adicione `1/t` à resposta.
3. Subtraia `1/t` de `nr/dr` e repita.

**Entrada:** `nr=2`, `dr=3`

**Saída:** `1/2 + 1/6`

### 24. Mesclar intervalos sobrepostos

**Descrição:** Mescle intervalos de tempo que colidem.

**Passo a Passo:**
1. Ordene pelo início.
2. Compare o início do atual com o fim do anterior. Atualize o fim para `max(fim1, fim2)` se sobrepor.

**Entrada:** `[[1,3], [2,6], [8,10]]`

**Saída:** `[[1,6], [8,10]]`

### 25. Número mínimo de termos de Fibonacci com soma K

**Descrição:** Mínimo de números de Fibonacci que somam K.

**Passo a Passo:**
1. Gere números de Fibonacci até `<= K`.
2. Subtraia gulosamente o maior Fibonacci menor ou igual ao K restante.

**Entrada:** `K = 17`

**Saída:** `3` (13+3+1)

### 26. Plataformas mínimas

**Descrição:** Mínimo de plataformas para que nenhum trem espere.

**Passo a Passo:**
1. Ordene array de chegadas e array de partidas separadamente.
2. Se chegada `<= `partida, `plat++`. Senão `plat--`. Guarde o máximo.

**Entrada:** Chega: `[900, 940]`, Parte: `[910, 1200]`

**Saída:** `1`

### 27. Custo mínimo para conectar n cordas

**Descrição:** Una n cordas. Custo é a soma dos comprimentos unidos.

**Passo a Passo:**
1. Use Min-Heap.
2. Retire os 2 menores, some, adicione custo e devolva a soma ao Heap.

**Entrada:** `[4, 3, 2, 6]`

**Saída:** `29`

### 28. Número máximo de trens

**Descrição:** Trens em diferentes plataformas. Maximize paradas.

**Passo a Passo:**
1. Agrupe por plataforma.
2. Para cada uma, aplique "Seleção de Atividades" ordenando por tempo de partida.

**Entrada:** Matriz `[chegada, partida, id_plataforma]`

**Saída:** Soma das atividades de todas as plataformas

### 29. Particionar de 1 a n em dois grupos com diferença mínima

**Descrição:** Divida {1..n} em 2 grupos com somas quase iguais.

**Passo a Passo:**
1. Alvo = `soma_total / 2`.
2. De n até 1, se couber no Alvo, vai pro Grupo 1; se não, Grupo 2.

**Entrada:** `n = 5`

**Saída:** G1={5,2}, G2={4,3,1}

### 30. Cortar papel no menor número de quadrados

**Descrição:** Papel `A x B`. Corte sempre o maior quadrado possível.

**Passo a Passo:**
1. O maior quadrado tem lado igual ao menor lado do papel atual.
2. Calcule quantos cabem (`maior / menor`), o resto é a nova dimensão.

**Entrada:** `13 x 29`

**Saída:** `9` quadrados

### 31. Diferença mínima em grupos de tamanho dois

**Descrição:** Forme pares num array `2n` para que max_soma e min_soma dos pares tenham diferença mínima.

**Passo a Passo:**
1. Ordene crescente.
2. Pareie `A[i]` com `A[2n - 1 - i]`. Compare as somas.

**Entrada:** `[1, 4, 3, 2]`

**Saída:** `0` (Pares dão soma 5 e 5)

### 32. Máximo de clientes satisfeitos

**Descrição:** Estoque limitado, atenda clientes que exigem quantidades exatas.

**Passo a Passo:**
1. Ordene as demandas crescentemente.
2. Atenda do menor para o maior até o estoque acabar.

**Entrada:** Estoque=10, Demandas=`[4,8,2,1,2]`

**Saída:** `4`

### 33. Vértices iniciais mínimos para percorrer a matriz

**Descrição:** Mova para células de valor `<=`. Ache de onde iniciar para cobrir tudo.

**Passo a Passo:**
1. Ordene células por valor decrescente.
2. Se não visitado, inicie DFS dali, adicione à lista de respostas e marque alcançáveis.

**Entrada:** `[[1,2,3], [2,3,1], [1,1,1]]`

**Saída:** Célula(s) com valor 3

### 34. Maior número palindrômico por permutação de dígitos

**Descrição:** Crie o maior palíndromo reorganizando dígitos de uma string.

**Passo a Passo:**
1. Frequência de 9 a 0.
2. Adicione metades nas bordas (maiores no início). O ímpar maior vai no meio.

**Entrada:** `"313551"`

**Saída:** `"531135"`

### 35. Menor número com n dígitos e soma dos dígitos

**Descrição:** Forme o menor número de M dígitos onde a soma é S.

**Passo a Passo:**
1. Reserve '1' para o primeiro dígito. `S -= 1`.
2. Do final pro início, preencha o dígito com o máximo possível até 9.

**Entrada:** `M=2`, `S=9`

**Saída:** `"18"`

### 36. Maior subsequência lexicográfica

**Descrição:** Subsequência onde cada char aparece `>= K` vezes.

**Passo a Passo:**
1. Conte chars. Escolha o maior lexicograficamente com contagem `>= K`.
2. Anexe de acordo com sua contagem original na string respeitando a ordem.

**Entrada:** `"bbaab"`, `K=2`

**Saída:** `"bbb"`

### 37. Escalonamento Shortest Job First (SJF)

**Descrição:** Ordene a execução dos processos para minimizar o tempo de espera.

**Passo a Passo:**
1. Ordene os processos pelo Tempo de Explosão (Burst Time) crescente.
2. Execute-os nessa ordem.

**Entrada:** Burst `[6, 8, 7, 3]`

**Saída:** Executa na ordem: P4(3), P1(6), P3(7), P2(8)

### 38. Algoritmo First Fit em gerenciamento de memória

**Descrição:** Aloque processos em blocos de memória, escolhendo o primeiro que caiba.

**Passo a Passo:**
1. Percorra a lista de blocos de memória da esquerda para a direita.
2. Se `bloco >= tamanho_processo`, aloque ali, diminua o bloco e passe pro próximo processo.

**Entrada:** Blocos `[100, 500, 200]`, Processo `[212]`

**Saída:** Vai para o bloco de `500`

### 39. Algoritmo Best Fit em gerenciamento de memória

**Descrição:** Escolha o bloco de memória mais justo para minimizar a sobra.

**Passo a Passo:**
1. Para cada processo, procure o menor bloco inteiro na memória tal que `bloco >= processo`.
2. Aloque e atualize o bloco.

**Entrada:** Blocos `[100, 500, 200]`, Processo `[212]`

**Saída:** Se houvesse `300`, iria pro 300. Aqui vai pro de `500`

### 40. Algoritmo Worst Fit em gerenciamento de memória

**Descrição:** Aloque sempre no MAIOR bloco disponível.

**Passo a Passo:**
1. Sempre procure e aloque o processo no bloco com a maior capacidade restante para evitar fragmentação.

**Entrada:** Blocos `[100, 500, 200]`, Processo `[212]`

**Saída:** Vai para o de `500`

### 41. Policiais pegam ladrões

**Descrição:** Matriz de P (Policiais) e T (Ladrões). Um policial pode pegar um ladrão a no máximo K passos. Maximize as prisões.

**Passo a Passo:**
1. Salve os índices de P e T em dois arrays separados.
2. Use dois ponteiros gulosos para ambos os arrays. Se `abs(P[i] - T[j]) <= K`, prendeu (avança ambos).
3. Senão, avance o menor índice para tentar aproximá-los.

**Entrada:** `arr = ['P', 'T', 'T', 'P', 'T']`, `K = 1`

**Saída:** `2`

### 42. Problema de encaixe de prateleiras

**Descrição:** Parede de comprimento L, prateleiras de larguras M e N (M < N). Priorize N e minimize a parede sem cobrir.

**Passo a Passo:**
1. Comece usando o número máximo possível de prateleiras grandes N.
2. Preencha o resto com prateleiras pequenas M. Guarde o espaço não utilizado.
3. Vá diminuindo a quantidade de N, testando se preencher com M gera menos espaço vazio.

**Entrada:** Parede=24, M=3, N=5

**Saída:** 3 de N e 3 de M (espaço vazio 0)

### 43. Atribuir ratos a buracos

**Descrição:** N ratos e N buracos no eixo X. Um rato por buraco. Minimize o tempo máximo que qualquer rato leva para se esconder.

**Passo a Passo:**
1. Ordene a posição dos ratos e as posições dos buracos.
2. Pareie `rato[i]` com `buraco[i]`.
3. O tempo máximo é o maior valor de `abs(rato[i] - buraco[i])` de todos os pares.

**Entrada:** Ratos=`[4, -4, 2]`, Buracos=`[4, 0, 5]`

**Saída:** `4`

</p>

</details>

<details>
    <summary>🔴 Nível 3 - Difícil</summary>

<p>

### 44. Minimizar a diferença máxima de altura

**Descrição:** Some ou subtraia K de cada item para minimizar a diferença entre máximo e mínimo (pode ficar negativo).

**Passo a Passo:**
1. Ordene o array. Itere considerando i como o corte: esquerda soma K, direita subtrai K.
2. Novo máx = `max(A[i-1]+K, A[n-1]-K)`. Mín = `min(A[0]+K, A[i]-K)`. Atualize a diferença.

**Entrada:** `[1, 5, 8, 10]`, `K = 2`

**Saída:** `5`

### 45. Minimizar a diferença máxima de altura (Variação Positiva)

**Descrição:** Igual ao problema 44, mas se a torre ficar negativa, ignore o passo.

**Passo a Passo:**
1. Idêntico ao anterior, mas na atualização De mínimo, pule a iteração se `A[i] - K < 0`.

**Entrada:** `[1, 15, 10]`, `K = 6`

**Saída:** `5`

### 46. Tornar o máximo igual com k atualizações

**Descrição:** Incremente elementos (máximo K vezes) para maximizar a frequência de um número.

**Passo a Passo:**
1. Ordene. Use Two Pointers.
2. Tente fazer a janela chegar ao valor de `A[direita]`. Custo = `tamanho * A[direita] - soma`. Se `<= K`, é válido.

**Entrada:** `[1, 2, 4]`, `K = 5`

**Saída:** `3`

### 47. Minimizar o fluxo de caixa entre amigos

**Descrição:** Minimize transações para quitar dívidas entre um grupo.

**Passo a Passo:**
1. Calcule o saldo líquido (Recebe - Paga).
2. Pegue quem deve mais e pague quem tem mais crédito. Cancele o menor valor. Repita.

**Entrada:** A deve $100 a B, B deve $50 a C

**Saída:** A paga $50 a B e $50 a C

### 48. Custo mínimo para cortar uma placa em quadrados

**Descrição:** Cortar matriz X,Y. Cada corte vertical é multiplicado por cortes horizontais já feitos e vice-versa.

**Passo a Passo:**
1. Ordene todos os custos de corte em ordem decrescente.
2. Faça o mais caro. Se for Vertical, custo = `V * pedaços_horizontais`. Atualize contadores.

**Entrada:** X=`[2,1,3,1]`, Y=`[4,1,2]`

**Saída:** `42`

### 49. Mínimo de arestas invertidas para criar caminho

**Descrição:** Em um grafo direcionado, inverta arestas para ir de Origem a Destino.

**Passo a Passo:**
1. Dê peso 0 para arestas normais e crie reversas com peso 1.
2. Aplique Dijkstra da Origem ao Destino. A distância é o número de inversões.

**Entrada:** Grafo direcionado: 0->1, 2->1, Caminho 0 a 2

**Saída:** `1` (Inverter 2->1)

### 50. Maior cubo deletando mínimo de dígitos

**Descrição:** Remova dígitos de um número enorme para formar o maior cubo perfeito.

**Passo a Passo:**
1. Gere cubos em string em ordem decrescente do limite para baixo.
2. Use Two Pointers para verificar se a string do cubo é subsequência da string número. Pare no primeiro que bater.

**Entrada:** `"4125"`

**Saída:** `"125"`

### 51. Reorganizar caracteres sem adjacentes iguais

**Descrição:** Rearranje letras para que letras iguais nunca se toquem.

**Passo a Passo:**
1. Max-Heap com frequências.
2. Retire 2, insira na string, diminua a frequência, devolva pro Heap.

**Entrada:** `"aaabc"`

**Saída:** `"abaca"`

### 52. Reorganizar string com distância D

**Descrição:** Letras iguais a pelo menos D posições de distância.

**Passo a Passo:**
1. Max-Heap + Fila de "Espera".
2. Use a letra e coloque na fila. Ela volta pro Heap após a fila andar D passos.

**Entrada:** `"aabbcc"`, `D = 3`

**Saída:** `"abcabc"`

### 53. Cobertura de conjunto (Set Cover)

**Descrição:** Escolha o mínimo de conjuntos que, na união, englobem todos os elementos do universo.

**Passo a Passo:**
1. Iterativamente pegue o subconjunto com o maior número de elementos ainda não cobertos.
2. Remova esses elementos da lista do universo e repita até cobrir tudo.

### 54. Empacotamento em bins (Bin Packing)

**Descrição:** Empacote itens de vários pesos em contêineres limitados para minimizar caixas. Use First Fit Descending.

**Passo a Passo:**
1. Ordene itens de maior peso para o menor.
2. Para cada item, coloque na primeira caixa com capacidade restante, senão abra nova.

### 55. Coloração de grafos

**Descrição:** Colora vértices de modo que vizinhos tenham cores diferentes usando mínimo de cores.

**Passo a Passo:**
1. Atribua cor 1 ao primeiro vértice.
2. Para cada outro vértice adjacente, escolha gulosamente a cor disponível de menor índice que não está sendo usada pelos seus vizinhos.

### 56. K-centers

**Descrição:** Coloque K antenas num mapa para minimizar a distância máxima que qualquer usuário ficará delas.

**Passo a Passo:**
1. Escolha o 1º centro aleatoriamente.
2. Para os K-1 centros, escolha sempre o nó na maior distância possível de qualquer um dos centros já alocados.

### 57. Superstring mais curta

**Descrição:** Combine fragmentos de strings em uma única e menor possível (usado em DNA).

**Passo a Passo:**
1. Compare todos os pares e ache qual tem o maior cruzamento de prefixo-sufixo.
2. Mescle os dois numa nova string e volte para a lista até ter só 1 string total.

### 58. Problema do caixeiro viajante usando MST

**Descrição:** Aproxime a rota mais curta passando por todas as cidades.

**Passo a Passo:**
1. Crie uma Árvore Geradora Mínima (Prim/Kruskal).
2. A resposta aproximada é fazer um caminho em Pré-ordem desta MST (Pulando vértices já visitados na viagem).

### 59. Árvore geradora mínima de Kruskal

**Descrição:** Ache a MST conectando todos os nós com peso mínimo.

**Passo a Passo:**
1. Ordene todas as arestas pelo peso em ordem crescente.
2. Adicione arestas iterativamente usando Union-Find para evitar ciclos gulosamente.

**Entrada:** Vértices = 4, Arestas ponderadas

**Saída:** MST correspondente

### 60. Árvore geradora mínima de Prim

**Descrição:** Ache a MST expandindo um único nó progressivamente.

**Passo a Passo:**
1. Inicie num nó qualquer, jogue suas vizinhanças num Min-Heap.
2. Sempre extraia a menor aresta que conecta um nó visitado a um não visitado.

**Entrada:** Grafo Ponderado

**Saída:** MST Ponderada

### 61. Árvore geradora mínima de Boruvka

**Descrição:** Outro algoritmo MST, ideal para computação paralela.

**Passo a Passo:**
1. Comece com cada vértice sendo seu próprio componente.
2. Para cada componente, ache a aresta mais barata de saída para outro componente. Una todos gulosamente até existir 1 único componente.

### 62. Algoritmo de menor caminho de Dijkstra

**Descrição:** Menor caminho de fonte única.

**Passo a Passo:**
1. Distância para a fonte = 0, para os outros = Infinito. Use Min-Heap ordenado pela distância atual.
2. Visite os adjacentes do nó mais próximo. Atualize gulosamente as menores rotas (Relaxamento).

### 63. Algoritmo de Dial

**Descrição:** Um Dijkstra otimizado se a margem de pesos nas arestas for muito pequena.

**Passo a Passo:**
1. Crie "Baldes" (Buckets) indexados pelo valor do peso funcionando como Fila de Prioridade em O(1).
2. Processe os baldes de menor índice gulosamente.

### 64. Custo mínimo para conectar todas as cidades

**Descrição:** Matriz 2D onde `M[i][j]` é custo para conectar cidade i à j. Conecte todas.

**Passo a Passo:**
1. Aplicação exata de MST de Prim ou Kruskal tratando a Matriz como lista de adjacência.
2. Soma dos pesos é o menor custo gulosamente alcançado.

### 65. Introdução ao problema de fluxo máximo

**Descrição:** Mande fluxo de S para T usando método de Ford-Fulkerson.

**Passo a Passo:**
1. Encontre um caminho de S a T gulosamente onde haja capacidade no grafo residual (BFS = Edmonds-Karp).
2. Empurre o fluxo limite dessa rota. Repita até não ter rotas.

### 66. Número de componentes cíclicos simples em um grafo não direcionado

**Descrição:** Ache quantos componentes formam perfeitamente um único anel.

**Passo a Passo:**
1. Percorra componentes com DFS/BFS.
2. Para ser um anel ganancioso, cada vértice deste componente deve ter grau exatamente 2.

### 67. Algoritmo ótimo de substituição de páginas

**Descrição:** Quando a RAM encher, remova a página que não será usada pelo maior tempo no futuro.

**Passo a Passo:**
1. Quando ocorrer page-fault e os frames estiverem cheios, olhe a sequência futura.
2. Elimine a página do frame que aparece mais longe no futuro (ou não aparece mais).

**Entrada:** Frames = 3, Array = `[7, 0, 1, 2, 0, 3, 0, 4]`

**Saída:** Substituições simuladas gulosamente olhando adiante

### 68. Escalonamento de tarefas com duas tarefas permitidas por vez

**Descrição:** Idêntico ao agendamento de tarefas (problema 22), mas a máquina aceita paralelismo = 2.

**Passo a Passo:**
1. Ordene tarefas por tempo de término.
2. Em vez de uma variável "último finalizado", use duas `(Fim1, Fim2)`. Aloque gulosamente no que terminar antes.

### 69. Trocas mínimas para balancear parênteses

**Descrição:** Array de colchetes. Ache o menor número de trocas adjacentes para balanceá-los.

**Passo a Passo:**
1. Percorra da esquerda para a direita mantendo contagem de `[` e `]`.
2. Se `]` exceder `[`, você achou um desequilíbrio. A distância para o próximo `[` não usado é a quantidade de trocas gulosas.

**Entrada:** `[]][][`

**Saída:** `2`

### 70. Fração egípcia (Implementação clássica)

**Descrição:** Repartir numerador/denominador nas maiores frações unitárias possíveis gulosamente.

**Passo a Passo:**
1. Ache `t = teto(denominador / numerador)`.
2. A fração é `1/t`. Subtraia do original e repita.

**Entrada:** `6/14`

**Saída:** `1/3 + 1/11 + 1/231`

### 71. Problema de conexão de água

**Descrição:** Encontre o diâmetro mínimo do tubo para conectar casas com canos onde existem tubulações de entrada e saída exclusivas.

**Passo a Passo:**
1. Procure casas que possuam cano de saída, mas não de entrada (início da rede).
2. Faça uma busca (DFS) até o fim dessa rede, rastreando o menor diâmetro visto no caminho.

**Entrada:** Tubos: 7->4(98), 5->9(72), 4->6(10)

**Saída:** 7->6(10), 5->9(72)

### 72. Problema de seleção de atividades (Clássico conceitual)

**Descrição:** Ache o subconjunto máximo de atividades mutuamente exclusivas em recursos de tempo.

**Passo a Passo:**
1. Ordene pelo tempo de término.
2. Itere pegando as atividades que iniciam >= término da anterior.

**Entrada:** Início: `[1, 3, 0, 5, 8, 5]`, Fim: `[2, 4, 6, 7, 9, 9]`

**Saída:** `4` atividades

### 73. Problema de sequenciamento de tarefas (Clássico com slots de tempo)

**Descrição:** Maximize o lucro executando tarefas antes de seu deadline.

**Passo a Passo:**
1. Ordene tarefas por lucro decrescente.
2. Aloque nos slots livres mais próximos e atrasados possíveis.

**Entrada:** A(deadline=2, lucro=100), B(1, 19), C(2, 27), D(1, 25)

**Saída:** Lucro: `127`

### 74. Codificação Huffman

**Descrição:** Construa a árvore de compressão de dados baseada nas frequências dos caracteres.

**Passo a Passo:**
1. Coloque todos os caracteres como nós-folhas em uma Fila de Prioridade (Min-Heap) usando frequência.
2. Remova os dois menores. Crie um novo nó interno cuja frequência é a soma deles.
3. Repita até restar um único nó (a raiz).

**Entrada:** chars = `['a','b','c','d']`, freqs = `[5, 9, 12, 13]`

**Saída:** Mapeamento ótimo de bits (ex: d:0, c:10, b:110, a:111)

### 75. Decodificação Huffman

**Descrição:** Dada uma string binária e a árvore de Huffman, reverta para o texto original.

**Passo a Passo:**
1. Comece no nó raiz da árvore.
2. Percorra bit a bit: se `0` vá para o filho esquerdo, se `1` vá para o direito.
3. Ao atingir uma folha, imprima o caractere e volte à raiz.

**Entrada:** `111110100` + Árvore

**Saída:** `"abcdd"`

### 76. Custo mínimo para processar m tarefas com custo de troca

**Descrição:** Processar N tarefas em M modos com custos de troca de máquina.

**Passo a Passo:**
1. Avalie apenas o custo local ganancioso de manter o modo atual versus mudar para outro (Custo config + Custo troca).

_(Exemplo dependente de matriz de custos)_

### 77. Tempo mínimo para concluir todos os trabalhos com restrições

**Descrição:** Tempo de execução de N trabalhos divididos entre K trabalhadores contíguos. Minimize tempo máximo.

**Passo a Passo:**
1. Use Busca Binária com Ganancioso: Chute um tempo médio.
2. Tente alocar gananciosamente operários sem passar do tempo chutado. Ajuste a busca.

**Entrada:** `[10, 20, 30, 40]`, `K = 2`

**Saída:** `60` (Opção 1: 10+20+30=60, Opção 2: 40)

</p>

</details>

