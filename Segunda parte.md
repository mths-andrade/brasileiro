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

![image](https://github.com/mths-andrade/brasileiro/assets/159069202/3b242116-1b7f-44f8-aecb-925481e766ad)

## Vitórias
![image](https://github.com/mths-andrade/brasileiro/assets/159069202/986a5099-c3da-49c4-b8a3-ac901e5271f4)

O coeficiente de determinação das vitórias é 0.946, o que quer dizer que o modelo linear explica 94,6% da variação da pontuação, um ajuste quase perfeito. O p-valor do modelo é nulo, então há significância estatística nele.

Temos, logo depois dele, os intervalos de confiança. Agora vamos ver a reta ajustada do modelo.

A reta estima quase perfeitamente a pontuação dado o número de vitórias. Uma relação linear quase direta.

$$
y=-4.3+0.4x
$$

Podemos dizer que a vitória é um dos fatores que têm influência direta na pontuação.

![image](https://github.com/mths-andrade/brasileiro/assets/159069202/41ba0c94-e414-41fc-af20-442bc3f9a0f7)

## Empates
## Derrotas
## Saldo de gols

