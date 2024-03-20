# Rossmann Store Sales Prediction


<div align="center">
<img src="img/rossmann.jpg" width="500px">
</div>
</br>



# Problema de Negócio

A Rossmann, é uma rede de varejo farmacêutico estabelecida em 1972 em Hanover, Alemanha. Todos os meses é realizado uma reunião com todos os gerentes de lojas para apresentação de resultados.
Na reunião do último mês o CFO (Chief Financial Officer) solicitou aos gerentes que fizessem a predição das vendas de suas respectivas lojas para as próximas seis semanas. Essa solicitação tem como objetivo a destinação de parte do faturamento ser destinado para reforma das lojas.

A partir disso, iniciamos o planejamento da solução para auxiliar os gerentes nesta entrega.

Os dados são provenientes da competição do Kaggle disponível [clicando aqui](https://www.kaggle.com/c/rossmann-store-sales/data).

<br>

# Objetivo do projeto


<p align = 'left'>

Fazer a previsão de vendas para as próximas 6 semanas das 1.115 lojas disponíveis no dataset
<p>

<br>

# Justificativa

- **Por quê:** Dificuldade em determinar o valor do investimento para reformas de cada loja.
- **Como:** Com a método CRISP-DM.
- **O quê:** Um modelo Machine Learning para realizar a previsão de vendas de todas as lojas.

<br>

#  Premissas

As variáveis originais do conjuto de dados são:<br>

Variável | Definição
------------ | -------------
Store | identificador único da loja|
DayOfWeek | dia da semana (1 = segunda-feira / 7 = domingo)|
Sales | vendas/dia (objetivo)|
Customers | número de clientes no dia.|
Open | indica se a loja está aberta ou fechada (1 = aberta / 0 = fechada)|
Promo | se existe uma promoção no dia ( 1 indica que estava ocorrendo uma promoção nesta loja)|
StateHoliday | indica um feriado estadual (a = feriado público / b = feriado da páscoa / c = natal / 0 = nenhum tipo de feriado neste dia)|
SchoolHoliday | feriado escolar (1 = feriado escolar / 0 = não é feriado escolar)|
Store | identificador único da loja.|
StoreType | tipo da loja, diferencia entre 4 modelos de loja diferentes: a, b, c, d|
Assortment | descreve um nível de sortimento (a = básico / b = extra / c = estendido)|
CompetitionDistance | distância da loja do concorrente mais próxima.|
CompetitionOpenSinceMonth | fornece o mês aproximado em que o concorrente mais próximo foi aberto.|
CompetitionOpenSinceYear | fornece o ano aproximado em que o concorrente mais próximo foi aberto.|
Promo2 | Promo2 é uma promoção adicional para todas as lojas ( 0 = a loja não está participando / 1 = a loja está articipando)|
Promo2SinceWeek | descreve a semana do calendário em que a loja começou a participar do Promo2.|
Promo2SinceYear | descreve o ano do calendário em que a loja começou a participar do Promo2.|
PromoInterval | descreve os intervalos consecutivos em que a Promo2 é iniciada, nomeando os meses. Por exemplo, "fevereiro, maio, agosto, novembro" significa que cada rodada começa em fevereiro, maio, agosto, novembro de qualquer ano para essa loja.|

<br>

# Planejamento da Solução_

O planejamento da solução para este projeto se baseia no método CRISP-DM (Cross Industry Standard Process for Data Mining), que é uma metodologia cíclica e flexivel voltada para resolução de problemas que envolvem grande volume de dados que permite a entrega rápida de valor para os times de negócio.

Segue abaixo uma breve ilustração das principais etapas desse processo:

<br>
<div align="center">
<img src="img/crisp.png" width="700px">
</div>
<br>

# Insights

*Resumo dos insights durante análise exploratória de dados (EDA):*

**Gráfico para saber o número das vendas por ano.**

<br>
<div align="center">
<img src="Imagens/VendasAno.PNG" width="700px">
</div>
<br>

<br>
<div align="center">
<img src="Imagens/VariacaoVendasAno.PNG" width="700px">
</div>
<br>

**Nota:**
- Temos uma queda nas vendas ao decorrer dos anos, que precisa ser analisado, para não afetar as vendas de 2015.
- Mas comparando o mesmo período de meses entre 2014 e 2015 temos um aumento de 6%.
- No no de 2015 até o mês de julho temos um crescimento de 6%, mas seria importante analisar o comportamento das vendas de 2014, para compreender o motivo da queda das vendas.

**Gráfico para visualizar a soma das vendas por mês.**

<br>
<div align="center">
<img src="Imagens/VendasMes.PNG" width="700px">
</div>
<br>

**Nota:**
- Por meio deste gráfico podemos perceber que no mês de novembro e dezembro segue uma sequência de aumento das vendas que pode ser explicada pela Black Friday e Natal, com está visualização a empresa pode fazer um planejamento de qual mês é mais importante para empresa para deixar preparado o estoque.

**Gráfico para visualizar a soma das vendas por dia.**

<br>
<div align="center">
<img src="Imagens/VendasDias.PNG" width="700px">
</div>
<br>

**Nota:**
- Podemos perceber que as vendas no final do mês, apresenta uma queda bem acentuada nas vendas.

**Gráfico para visualizar a soma das vendas por dia da semana.**

<br>
<div align="center">
<img src="Imagens/VendasDiaSemana.PNG" width="700px">
</div>
<br>

**Nota:**
- Podemos ver que o menor pico de vendas é no domingo, esta é uma informação que precisa compreender melhor este comportamento.

**Gráfico para visualizar o número de cliente que vão na loja por mês.**

<br>
<div align="center">
<img src="Imagens/ClienteLoja.PNG" width="700px">
</div>
<br>

**Nota:**
- O aumento da média de cliente no mês de novembro e dezembro pode ser explicado pela Black Friday e Natal, com está visualização a empresa pode fazer um planejamento de qual mês é mais importante para empresa para deixar preparado o estoque e os funcionários.

**Gráfico para saber se a promoção afeta o número de cliente.**

<br>
<div align="center">
<img src="Imagens/ClientePromocao.PNG" width="700px">
</div>
<br>

**Nota:**
- Podemos afirmar que quando têm promoção o número de cliente não aumentam muito (147), porém o número de vendas aumenta consideravelmente, pode ser que vários clientes acabam combrando mais produtos.

**Gráfico para saber se a promoção afeta as vendas.**

<br>
<div align="center">
<img src="Imagens/VendasPromocao.PNG" width="700px">
</div>
<br>

**Nota:**
- Podemos perceber que quando temos promoção na loja as vendas aumentam cerca de 12%.

# Modelos de Machine Learning

1. Average Model
2. Linear Regressor
3. Linear Regressor Regularizaded (Lasso)
4. Random Forest Regressor
5. XGBoost Regressor

<br>

| Index | Model Name | MAE | MAPE | RMSE |
| ----- | ---------- | --- | ---- | ---- |
| 1 | Average Model | 1354.84 | 0.46 | 1835.02 |
| 2 | Linear Regression | 1867.09 | 0.29 | 2671.05 |
| 3 | Linear Regression - Lasso | 1891.70 | 0.29 | 2744.45 |
| 4 | Random Forest Regressor | 679.60 | 0.10 | 1011.12 |
| 5 | XGBRegressor | 	883.72 | 0.13 | 1274.23 |


<br>

# Performance dos Modelos de Machine Learning após cross validation

Comparando o desempenho dos modelos - Cross Validation.

<br>

| Index | Model Name | MAE | MAPE | RMSE |
| ----- | ---------- | --- | ---- | ---- |
| 1 | Linear Regression | 2081.73 +/- 295.63 | 0.3 +/- 0.02 | 2952.52 +/- 468.37 |
| 2 | Linear Regression - Lasso | 2116.38 +/- 341.5 | 0.29 +/- 0.01 | 3057.75 +/- 504.26 |
| 3 | Random Forest Regressor | 837.68 +/- 219.1 | 0.12 +/- 0.02| 1256.08 +/- 320.36 |
| 4 | XGBRegressor | 	1030.28 +/- 167.19 | 0.14 +/- 0.02 | 1478.26 +/- 229.79 |

<br>

**Nota:**

- Também podemos observar a tabela final e ver que Random Forest Regressor tem uma performance melhor que todos os outros modelos.

<br>

# Performance do Modelo Final após fine tunning

A métrica final do modelo ficou desta forma:

 <br>

| Index | Model Name | MAE | MAPE | RMSE |
| ----- | ---------- | --- | ---- | ---- |
| 1 | XGBoost Regressor | 770.21 | 0.12 | 1108.06 |

 <br>

# Resultado Negócio

Após a escolha do nosso algoritmo, somos capazes de visualizar alguns cenarios do ponto de vista de negócio.

 <br>

Loja|Predição €|Pior cenário €|MelhorCenário €|MAE|MAPE %
| ----- | ---------- | --- | ---- | ---- |---- |
55	|	172.468,20|	171.977,62|	172.958,78|	490,58|	10,20
932	|	282.757,31|	282.148,06|	283.366,56|	609,25|	7,83
638	|	232.906,75|	232.469,60|	233.343,90|	437,15|	6,75
642	|	137.029,94|	136.461,57|	137.598,31|	568,37|	17,99

 <br>

 **Nota:**

 - Na loja 638, a previsão é vender  232.469 euros nas próximas 6 semanas com um erro de 6,75%

 <br>

**Gráfico para visualizar a performance da predição em relação as vendas reais.**

 <br>
 <div align="center">
 <img src="Imagens/RealPrevisao.PNG" width="700px">
 </div>
 <br>

 O gráfico esta mostrando as seis semanas de teste e podemos ver que as predições ao longo do tempo esta bem próxima das vendas.

 <br>

# Conclusão

Com o modelo selecionado, treinado e avaliado com uma boa performance, chegou a hora de coloca-lo em produção. Para isso, optamos por disponibilizar as predições do projeto de forma online através do aplicativo de mensagens Telegram.

Neste aplicativo, o usuário deverá informar para um bot criado no Telegram o ID da loja a qual deseja obter a previsão de vendas nas próximas 6 semanas. Assim, o bot retornará uma mensagem com a previsão.

<div align="center">
<img src="img/telegramBot.gif" width="250px">
</div>
</br>

# Próximos passos

1. Temos uma queda nas vendas ao decorrer dos anos, que precisa ser analisado, para não afetar as vendas de 2015.
   - Mas comparando o mesmo período de meses entre 2014 e 2015 temos um aumento de 6%.


2. Registros que são outliers: 101.710.
    - Devemos depois fazer uma análise mais profunda porque nem tudo pode ser um outlier.


3. Podemos perceber que as vendas no final do mês, apresenta uma queda bem acentuada nas vendas, que precisa análisar.

4. Podemos ver que o menor pico de vendas é no domingo, esta é uma informação que precisa compreender melhor este comportamento.
