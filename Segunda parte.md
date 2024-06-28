# Introdução

Vamos agora discorrer sobre análise de regressão e as correlações de cada critério em relação à pontuação. Porém, antes vamos discutir sobre um ponto que deve ficar claro.

# Recapitulando…

A fórmula do aproveitamento é $AP=\frac{QP}{QT}\times100$, como $QT=114$ no nosso caso, temos então que $AP=\frac{QP}{114}\times100=QP\times\frac{100}{114}$. Portanto, **o aproveitamento é diretamente proporcional à pontuação**. Mais do que isso, **é totalmente dependente da pontuação**.

Vamos analisar os dois tipos de gráficos de cada critério. Primeiro, as frequências.

![Comparação](https://github.com/mths-andrade/brasileiro/assets/159069202/5983d256-9d49-4e2b-b28a-94eda73504e0)
A similaridade das duas distribuições de frequência é clara. Até as diferenças entre cada medida central são parecidas. Agora, vamos ver as médias de cada time. 

Mesma coisa, a semelhança é óbvia. As médias e valores são idênticos.

![Pontuação](https://github.com/mths-andrade/brasileiro/assets/159069202/22059268-a766-479e-ba7a-d7ae0b7c2a57)
![Aproveitamento](https://github.com/mths-andrade/brasileiro/assets/159069202/bb1e0b2f-5532-4e58-9337-554c004444d4)

# Correlação
Agora, vamos ver a matriz de correlação.

|  | Posição | Pontos | Vitórias | Empates | Derrotas | Saldo | Aproveitamento |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Posição | 1 | **-0.939** | -0.916 | 0.195 | 0.814 | -0.866 | -0.939 |
| Pontos | -0.939 | 1 | 0.973 | -0.195 | -0.873 | 0.923 | 1.000 |
| Vitórias | -0.916 | **0.973** | 1 | -0.418 | -0.736 | 0.879 | 0.973 |
| Empates | 0.195 | **-0.195** | -0.418 | 1 | -0.308 | -0.099 | -0.195 |
| Derrotas | 0.814 | **-0.873** | -0.736 | -0.308 | 1 | -0.846 | -0.873 |
| Saldo | -0.866 | **0.923** | 0.879 | -0.099 | -0.846 | 1 | 0.923 |
| Aproveitamento | **-0.939** | **1** | **0.973** | **-0.195** | **-0.873** | **0.923** | 1 |

Vemos que **os coeficientes de correlação do aproveitamento são iguais aos da pontuação**, mais uma vez confirmando a relação direta entre aproveitamento e pontuação.

Continuando, temos agora os gráficos de dispersão de cada critério, nas diagonais, cada distribuição de frequência e, na parte inferior, cada dispersão apresenta a concentração dos dados.
![pairplot](https://github.com/mths-andrade/brasileiro/assets/159069202/d0b3b716-ea45-4e6c-895b-31d8034cc71d)

Queremos avaliar a pontuação. Então, vamos ver mais detalhadamente essa categoria.

![pontuação](https://github.com/mths-andrade/brasileiro/assets/159069202/4adbc080-9a26-49fd-8eca-6dae6d363100)

Correlação total e positiva entre aproveitamento e pontuação até graficamente.

# Modelos de regressão

Vamos começar a verificar quais critérios influem na pontuação. Vou omitir o aproveitamento porque já verificamos a relação direta.

Criei funções para gerar cada modelo e outro para exibir os resultados.

## Posição
![image](https://github.com/mths-andrade/brasileiro/assets/159069202/6a846642-14c1-4d8a-a348-292ef822ff88)

O coeficiente de determinação da posição é 0.882, o que quer dizer que o modelo linear explica 88,2% da variação da pontuação, um ótimo ajuste. O p-valor do modelo é nulo, então há significância estatística nele.

Temos, logo depois dele, os intervalos de confiança. Agora vamos ver a reta ajustada do modelo.

De fato a reta estima razoavelmente bem a pontuação dada a posição.

$$
y=33.2-0.4x
$$

Podemos dizer que a posição é o primeiro fator que tem influência direta na pontuação, mesmo que negativa.

![Untitled](https://github.com/mths-andrade/brasileiro/assets/159069202/91c1ed68-8892-43c9-8823-2b2df8ba02ce)

## Vitórias
![image](https://github.com/mths-andrade/brasileiro/assets/159069202/986a5099-c3da-49c4-b8a3-ac901e5271f4)

O coeficiente de determinação das vitórias é 0.946, o que quer dizer que o modelo linear explica 94,6% da variação da pontuação, um ajuste quase perfeito. O p-valor do modelo é nulo, então há significância estatística nele.

Temos, logo depois dele, os intervalos de confiança. Agora vamos ver a reta ajustada do modelo.

A reta estima quase perfeitamente a pontuação dado o número de vitórias. Uma relação linear quase direta.

$$
y=-4.3+0.4x
$$

A vitória é outro dos fatores que têm influência direta na pontuação, dessa vez positiva.

![Untitled](https://github.com/mths-andrade/brasileiro/assets/159069202/ad5e206c-e88a-467c-900b-76346bc5c4fb)

## Saldo de gols
![Untitled](https://github.com/mths-andrade/brasileiro/assets/159069202/56b22a4e-bba6-40d8-a274-1f684c9a9cf1)

O coeficiente de determinação do saldo de gols é 0.853, então o modelo explica razoavelmente a pontuação, um bom ajuste. O p-valor do modelo é nulo, então há significância estatística nele.

Vamos ver a reta ajustada desse modelo. Ela estima bastante a pontuação dado o saldo de gols.

$$
y=-62.4+1.2x
$$

O saldo de gols é mais um dos fatores que têm influência direta positiva na pontuação.

![Untitled](https://github.com/mths-andrade/brasileiro/assets/159069202/e8d63b59-b79a-4e71-87d2-2815ff336d65)

Lembrando dos histogramas da parte 1, temos dois critérios que se aproximam de uma **distribuição normal**: os empates e, principalmente, as derrotas. Vamos fazer uma avaliação mais detalhada deles.

## Empates
![image](https://github.com/mths-andrade/brasileiro/assets/159069202/bd83940b-88c6-4ada-b176-1a9ad60d4931)

O coeficiente de determinação dos empates é 0.038, então o modelo explica quase nada da pontuação, como já devia ser esperado. O p-valor do modelo é nulo, então há significância estatística nele.

Nem podemos chamar de ajuste, vamos apenas ver a reta desse modelo.

Dados totalmente dispersos em volta da reta.

O p-valor do teste Omnibus, como vemos acima, é de 0.803, muito maior que 0.05, nosso nível de significância, então os resíduos do modelo não se distribuem como uma normal, um fato óbvio. O p-valor do teste Jarque-Bera, 0.891, confirma o mesmo fato.

![Untitled](https://github.com/mths-andrade/brasileiro/assets/159069202/a02d811e-d376-4298-ba17-4cc2f41ec9be)

Esse gráfico abaixo faz uma comparação de distribuições de probabilidade com a normal. Quando  as distribuições são muito próximas ou, até mesmo, iguais, esses valores, os pontinhos azuis, vão ficar bem em cima dessa reta vermelha, isso mostra que ela se distribui bem próximo de uma distribuição normal.

![Untitled](https://github.com/mths-andrade/brasileiro/assets/159069202/6d551ab4-0571-4d46-9606-2f13b9aa6ee2)

Os dados se aproximam bastante de uma distribuição normal. Além disso, a assimetria (skew) se aproxima bastante de zero, e a curtose (curtosis) é muito próxima de 3, evidenciando a semelhança com a normal.

## Derrotas

![image](https://github.com/mths-andrade/brasileiro/assets/159069202/324d36f7-6b22-4f1a-bf63-a114356ea9ea)

O coeficiente de determinação dos empates é 0.762, então o modelo razoavelmente bem a pontuação. O p-valor do modelo é nulo, então há significância estatística nele.

Vamos ver a reta ajustada desse modelo. Ela estima de certo jeito a pontuação dadas as derrotas.

O p-valor do teste Omnibus, como vemos acima, também é de 0.803, então os resíduos do modelo não se distribuem como uma normal, um fato óbvio de novo. Não é uma distribuição normal, só similar. 

O p-valor do teste Jarque-Bera, também de 0.891, confirma o mesmo fato.

A derrota é mais um dos fatores que têm influência direta negativa na pontuação.

![Untitled](https://github.com/mths-andrade/brasileiro/assets/159069202/bda91bea-d440-4af3-b45a-cfa1fae91150)

![Untitled](https://github.com/mths-andrade/brasileiro/assets/159069202/3579dc6d-759a-4b09-a33b-e670261af477)

Esses dados também se aproximam bastante de uma distribuição normal. A assimetria e a curtose têm os mesmos valores do modelo anterior, evidenciando a semelhança com a normal.

# Um exemplo de não normalidade

A distribuição de frequências da posição se afasta bastante de uma normal.

![image](https://github.com/mths-andrade/brasileiro/assets/159069202/52f9ef08-2c17-4397-82ed-2b38fe02d945)

# Mais algumas considerações

Vamos ver as regressões e distribuições de frequência das categorias relevantes para a pontuação.
![Untitled](https://github.com/mths-andrade/brasileiro/assets/159069202/79a5f74a-5deb-4c1d-845a-c2ca96534920)

![Untitled](https://github.com/mths-andrade/brasileiro/assets/159069202/6b848b9d-6172-4d70-8dfb-7468adb9e656)

Vemos que a distribuição das derrotas se assemelha à forma de sino de uma **distribuição normal**, assim como a dos empates, como visto abaixo.

![Untitled](https://github.com/mths-andrade/brasileiro/assets/159069202/e06c105a-5ebf-465c-aa82-1e2bf636ba21)

A reta de ajuste do aproveitamento explica perfeitamente a pontuação, porém o ajuste linear não é estatisticamente significativo pois o p-valor é muito grande.
![Untitled](https://github.com/mths-andrade/brasileiro/assets/159069202/7a777be5-b6fc-468b-a221-a65a8c853826)

Para terminar essa seção, vamos ver os boxplots de cada time de acordo com as pontuações e aproveitamentos. Temos gráfico semelhantes uma vez mais.

![Untitled](https://github.com/mths-andrade/brasileiro/assets/159069202/61faf0d4-5667-4141-b522-ca1ea717f84d)

![image](https://github.com/mths-andrade/brasileiro/assets/159069202/7ff7284d-bd4b-4446-9a72-3f8f595c2440)

# Conclusão

Temos que os critérios que influenciam **positivamente** na pontuação são as **vitórias** e o **saldo de gols**. Quanto maiores forem, **maior** será a pontuação. Os critérios que influenciam *negativamente* na pontuação são as *derrotas* e a *posição*. Quanto maiores forem, *menor* será a pontuação.

Além disso, **o aproveitamento depende diretamente da pontuação**, um fato óbvio, mas que comprovamos nesse texto.

Bom, aqui está o notebook do Colab com todos os comandos:
[brasileirão parte 2.ipynb](https://github.com/mths-andrade/brasileiro/blob/4a32f1b07a5a6ade5334feeb7457b789b5555e90/brasileir%C3%A3o_parte_2.ipynb).

Muito obrigado pela leitura de novo!
