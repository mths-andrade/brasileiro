# Introdução
Decidi remodelar o texto que fiz sobre o Campeonato Brasileiro. Temos 218 registros dos times do G13 na primeira divisão. Como alguns foram rebaixados, alguns times têm menos dados que outros.

Inicialmente, importei as bibliotecas apropriadas:

- Pandas, para dataframes;
- Numpy, para operações matemáticas.
- Matplotlib, para gráficos simples;
- Seaborn, para gráficos mais elaborados;
- Statsmodels, para operações estatísticas.

Os dados estão nesse arquivo CSV: [brasileiro_tab.csv](https://github.com/mths-andrade/brasileiro/blob/86cc409655a4a91da942848d34a1d179ec25fc6d/brasileiro_tab.csv)

Todo o processo está nesse notebook: [brasileirão final.ipynb](https://github.com/mths-andrade/brasileiro/blob/86cc409655a4a91da942848d34a1d179ec25fc6d/brasileir%C3%A3o%20final.ipynb)

Abaixo, temos as primeiras estatísticas descritivas:

|  | Posicao | Pontos | Vitorias | Empates | Derrotas | Saldo | Aproveitamento |
| --- | --- | --- | --- | --- | --- | --- | --- |
| count | 218.0 | 218.0 | 218.0 | 218.0 | 218.0 | 218.0 | 218.0 |
| mean | 7.8 | 57.5 | 15.8 | 10.2 | 12.1 | 7.3 | 50.4 |
| std | 4.9 | 10.5 | 3.8 | 2.7 | 3.6 | 13.7 | 9.2 |
| min | 1.0 | 27.0 | 5.0 | 3.0 | 3.0 | -30.0 | 23.7 |
| 25% | 3.2 | 50.0 | 13.0 | 8.0 | 10.0 | -1.0 | 43.9 |
| 50% | 7.0 | 56.0 | 15.0 | 10.0 | 12.0 | 7.0 | 49.1 |
| 75% | 12.0 | 65.0 | 18.0 | 12.0 | 14.0 | 17.0 | 57.0 |
| max | 20.0 | 90.0 | 28.0 | 17.0 | 22.0 | 49.0 | 79.0 |

A primeira linha fala da frequência dos registros, temos a mesma para todas as colunas. Depois, temos as médias e desvios padrão. As linhas seguintes falam dos quartis: mínimos, primeiros, segundos (medianas) e terceiros quartis, além dos máximos por último. Importante dizer que os dados foram arredondados, então não são valores exatos.

Atribuí cada média a uma variável e criei dataframes contendo a média de cada time por categoria. Agora, vamos às partes dos gráficos.

# Histogramas

## Posição
![Posição](https://github.com/mths-andrade/brasileiro/assets/159069202/d2faecdd-8320-42cc-884f-461ed1899ce5)

Começando com a posição, temos uma grande assimetria à direita. A média e a mediana são próximas, mas a moda, o terceiro lugar, é bem menor que ambos. Temos que a maioria das ocorrências se concentra até o sétimo lugar, entre elas, grande parte está no chamado G4. Podemos concluir que os times do G13 geralmente têm boas campanhas, no primeiro terço da tabela.

## Pontuação
![Pontuação](https://github.com/mths-andrade/brasileiro/assets/159069202/24c2e674-f41d-41f9-b071-82dda0001637)

Continuando com a pontuação, temos maior simetria comparado à posição. A maioria dos dados está entre 50 e 60 pontos, o que é reforçado com moda, média e mediana pertencendo a esse intervalo. Os times têm, em média, campanhas equivalentes ao fim da primeira metade da tabela em relação à pontuação.

## Vitórias
![Vitórias](https://github.com/mths-andrade/brasileiro/assets/159069202/dab50d25-e500-46b6-9a41-47982044266c)

Em relação ao número de vitórias, temos uma simetria bem razoável. A maioria dos registros está entre 10 e 15 vitórias, inclusive temos a moda igual à mediana, de 15 triunfos. A média está bem próxima delas. Novamente, esse intervalo equivale ao fim da primeira metade da tabela levando em conta as vitórias.

Temos um resultado curioso: há uma grande frequência de cerca de 20 vitórias, um número de um candidato ao título.

## Empates
![Empates](https://github.com/mths-andrade/brasileiro/assets/159069202/4a09a9c8-87bb-4c0e-9295-752d80aa5442)

Em relação ao número de empates, temos uma simetria ótima, já que moda e mediana são iguais, além da média também ser igual arredondando uma casa decimal. A maioria dos dados está entre 10 e 12 empates. Não podemos deduzir um comportamento em relação à tabela, já que times campeões tiveram campanhas com esses números, como o Palmeiras ano passado com 10 empates, ao mesmo tempo que times de meio de tabela.

## Derrotas
![Derrotas](https://github.com/mths-andrade/brasileiro/assets/159069202/6b2a86f6-bc7d-4951-bf69-0cd96aa83f88)

Com relação às derrotas, temos mais uma simetria ótima, esta quase perfeita já que moda e mediana são iguais, além da média estar muito próxima a elas. A maioria das ocorrências está entre 12 e 15 derrotas. No geral, esse intervalo equivale ao início da segunda metade da tabela observando as derrotas.

Essa categoria é a que mais se assemelha a uma distribuição normal (de sino), tanto numerica quanto graficamente.

## Saldo de gol
![Saldo de gol](https://github.com/mths-andrade/brasileiro/assets/159069202/40a3447b-9ca5-487f-8578-917f8aed011a)

Com relação ao saldo de gol, temos alguma simetria, com a média aproximadamente igual à mediana e a moda negativa. A maioria das ocorrências está entre 0 e 10 pontos de saldo de gol. Não podemos ter conclusões com relação a posições na tabela pois é um critério muito fluido, times campeões podem ter saldos de gol baixos.

Geralmente não temos saldos tão altos, como já desenvolvemos acima. Na verdade, é esperado, os times estão cada vez mais ofensivos.

## Aproveitamento
Antes de continuar com os histogramas, vou esclarecer o que é o aproveitamento de um time. Basicamente é a quantidade de pontos obtidos dividida pela quantidade total de pontos, em algum momento. No fim do campeonato, temos 38 jogos com 114 pontos disputados, então á fórmula é:

$$
AP=\frac{QP}{QT}\times100
$$

$AP$ é o aproveitamento, $QP$, a quantidade de pontos ganhos e $QT$, a quantidade total. Multiplicamos por 100 porque tal número é uma porcentagem.

![aproveitamento](https://github.com/mths-andrade/brasileiro/assets/159069202/1a361491-ac02-4da9-87fe-f6bbd21eb516)

Temos certa simetria avaliando os aproveitamentos dos times, mas não muita. As três medidas centrais são diferentes. Os registros se concentram entre 45 e  60%. Times campeões no geral têm aproveitamento acima de 60%, então podemos concluir que a maioria do G13 está na primeira metade da tabela nesse recorte.

# Análise das médias
Feitos esses histogramas, agora vamos avaliar as médias de cada time, seguindo a mesma ordem.

## Posição
![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/39c58546-bcb9-4649-a319-c8db800653f1/6e31479f-7da7-4f9f-82fb-2356102a215d/Untitled.png)

O Grêmio tem a melhor média de posição, isto é, a mais baixa. A pior média é a do Vasco, a mais alta.

Poucos times estão acima da média de posição, o que é um bom sinal.

## Pontuação
![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/39c58546-bcb9-4649-a319-c8db800653f1/43384e59-7237-4a9c-a1f2-932a6e1ac63b/Untitled.png)

O Flamengo tem a melhor média de pontuação, bem próximo de Grêmio e São Paulo, provavelmente a diferença é por conta de casas decimais. A pior média é a do Vasco.

Vários times estão acima da média geral de pontos.

## Vitórias
![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/39c58546-bcb9-4649-a319-c8db800653f1/a093b978-eb83-4282-9b57-d0cbc22b4ae2/Untitled.png)

O Grêmio tem a melhor média de vitórias, bem próximo do Flamengo, diferença de casas decimais. A pior média é a do Vasco.

Vários times também estão acima da média geral de vitórias.

## Empates
![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/39c58546-bcb9-4649-a319-c8db800653f1/ac562fd3-1454-4f5a-b8ab-4ae1c7f9c159/Untitled.png)

O Corinthians tem a melhor média de empates, bem próximo do Vasco, diferença de casas decimais. A pior média é a do Atlético Mineiro.

## Derrotas
![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/39c58546-bcb9-4649-a319-c8db800653f1/5589a7a6-26e6-4edc-a38f-ce68bf229e63/Untitled.png)

O São Paulo tem a melhor média de derrotas, a mais baixa. A pior média é a do Botafogo.

## Saldo de gol
![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/39c58546-bcb9-4649-a319-c8db800653f1/37af33bf-11a8-4c2b-bfce-54a82c82a393/Untitled.png)

O Grêmio tem a melhor média de saldo de gol. A pior média é a do Vasco, muito mais baixa que as outras.

Grande parte dos times está acima da média geral de saldo de gol.

## Aproveitamento
![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/39c58546-bcb9-4649-a319-c8db800653f1/9dd804b3-9d20-47ec-93a3-e2c95f18876d/Untitled.png)

O Flamengo tem a melhor média de aproveitamento. A pior média é a do Vasco.

Com isso, podemos terminar essa primeira parte resumindo as melhores e piores médias.

|  | Melhor média | Pior média |
| --- | --- | --- |
| Posição | Grêmio | Vasco |
| Pontos | Flamengo | Vasco |
| Vitórias | Grêmio | Vasco |
| Empates | Atlético Mineiro | Corinthians |
| Derrotas | São Paulo | Botafogo |
| Saldo | Grêmio | Vasco |
| Aproveitamento | Flamengo | Vasco |

O Grêmio é o time com mais melhores médias, três, sendo o mais equilibrado. O Vasco é o que tem mais piores médias, cinco, sendo o menos competitivo.
