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
| Posição | 1.000 | -0.939 | -0.916 | 0.195 | 0.814 | -0.866 | -0.939 |
| Pontos | -0.939 | 1.000 | 0.973 | -0.195 | -0.873 | 0.923 | 1.000 |
| Vitórias | -0.916 | 0.973 | 1.000 | -0.418 | -0.736 | 0.879 | 0.973 |
| Empates | 0.195 | -0.195 | -0.418 | 1.000 | -0.308 | -0.099 | -0.195 |
| Derrotas | 0.814 | -0.873 | -0.736 | -0.308 | 1.000 | -0.846 | -0.873 |
| Saldo | -0.866 | 0.923 | 0.879 | -0.099 | -0.846 | 1.000 | 0.923 |
| Aproveitamento | -0.939 | 1.000 | 0.973 | -0.195 | -0.873 | 0.923 | 1.000 |
