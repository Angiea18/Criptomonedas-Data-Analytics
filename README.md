## PROYECTO INDIVIDUAL Nº2 - DATA ANALYTICS

Cryptocurrency Market Data Analytics

![Cripto](https://github.com/Angiea18/Criptomonedas-Data-Analytics/blob/main/src/criptomonedas.jpg)


**`by Angie Arango Zapata`**


## Contexto

En este proyecto se presenta un análisis exhaustivo del mercado de criptomonedas utilizando datos de la [**`API CoinGecko`**](https://www.coingecko.com/es/api/documentation). El análisis se enfoca en 13 criptomonedas seleccionadas según su **capitalización** y **estabilidad**. 

Para realizar el análisis, se seleccionaron 13 criptomonedas siguiendo dos criterios específicos: la capitalización y la estabilidad. La **`capitalización`** se alude al valor completo del mercado de una criptomoneda en particular, en tanto que la **`estabilidad`** se relaciona con las variaciones de precio que experimenta a lo largo del período analizado.


Se han escogido las siguientes criptomonedas en función de su capitalización:

- Bitcoin (BTC)
- Ethereum (ETH)
- Binance Coin (BNB)
- XRP (XRP)
- Dogecoin (DOGE)

Asimismo, se han seleccionado estas criptomonedas considerando su estabilidad:

- DAI (DAI)
- Binance USD (BUSD)
- TrueUSD (TUSD)
- Frax (FRAX)
- Decentralized Dollar (USDD)
- Pax Dollar (USDP)

Aquellas criptomonedas que se encuentran en ambas categorías son:

- Tether (USDT)
- USD Coin (USDC)


## Objetivo

Comprender y evaluar el comportamiento del mercado de criptomonedas en un período determinado con el fin de informar decisiones de inversión y estrategias financieras. A través de la recopilación y análisis de datos, se busca identificar patrones, tendencias y oportunidades en el mercado de criptomonedas, así como mitigar riesgos potenciales.

A través de este análisis, se pretende examinar los siguientes Indicadores Clave de Rendimiento **`(KPIs)`**:

- Porcentaje de Cambio en el Mercado de Capitalización por Moneda:
Muestra la variación en el valor total de una criptomoneda en términos porcentuales.

- Cambio Precio Promedio por Moneda:
Indica la fluctuación porcentual en el precio promedio ponderado de una criptomoneda.

- Volumen Total Negociación por Moneda:
Refleja la cantidad total de una criptomoneda comprada o vendida en un período determinado.


## Extracción de la información

Los datos fueron obtenidos de la API CoinGecko. Una vez realizada la selección de las monedas, se procedió a realizar solicitudes a la API utilizando Python. Esto se logró mediante la creación de funciones personalizadas. A partir de estos datos, se construyeron dos DataFrames: uno con 8 monedas caracterizadas por su estabilidad **df_stable** y otro con 5 monedas de mayor capitalización **df_top**.

[stablecoins](https://github.com/Angiea18/2-proyecto-individual-DataAnalytics/blob/main/stablecoins.ipynb)

[topcurrency](https://github.com/Angiea18/2-proyecto-individual-DataAnalytics/blob/main/top_currency.ipynb)

Finalmente se creo un DataFrame **`df_cryptocurrency`** en el que se unieron los otros dos ya mencionados y a este se le realizo el proceso de EDA y el dashboard. 

[cryptocurrency](https://github.com/Angiea18/2-proyecto-individual-DataAnalytics/blob/main/cryptocurrency_EDA.ipynb)


## EDA

En nuestro proceso, hacemos uso de diversas librerías que son esenciales para llevar a cabo un análisis exploratorio de datos de manera efectiva. Algunas de las librerías clave que utilizamos son:

* requests
* locale
* pandas
* matplotlib.pyplot 
* seaborn

En el proceso de análisis exploratorio de datos, ejecutamos las siguientes etapas:

1. Carga y unión de datos: Importamos archivos CSV de los dataframes individuales para cada grupo de monedas y los fusionamos en un único dataframe df_cryptocurrency.

2. Limpieza de datos: Realizamos varias tareas de limpieza, entre las que destacan:

* Conversión del tipo de dato de la columna "Date" al formato datetime, lo que facilita el análisis temporal.
* Verificación de la existencia de duplicados y datos nulos, constatando que no existieran anomalías en los datos.
* Formateo de números: Hacemos uso de la librería 'locale' para asegurarnos de que los números se muestren de manera comprensible, en especial cuando se trata de precios en USD y los valores de MarketCap y TotalVolume, que cuentan con separadores de miles.

3. Visualizaciones: Creamos diversas visualizaciones que nos ayudan a entender mejor los datos:

 - Scatter plot: Esta gráfica visualiza la relación entre el precio, el capital de mercado y el volumen total de diferentes criptomonedas, lo que puede ayudar a identificar patrones y relaciones.
 - Gráfico de líneas con áreas: Este tipo de gráfico es ideal para representar la evolución y las tendencias de las criptomonedas a lo largo de un período de tiempo.
 - Matriz de correlación: Utilizamos esta herramienta para descubrir patrones y relaciones más complejas en los precios de las criptomonedas.

Finalmente, concluimos el proceso guardando el dataframe resultante en un archivo CSV llamado *cryptocurrancy_final.cvs*, el cual posteriormente utilizamos para alimentar un dashboard que facilita la visualización y comprensión de los datos de manera interactiva y efectiva.

El EDA se encuentra [aquí](https://github.com/Angiea18/2-proyecto-individual-DataAnalytics/blob/main/cryptocurrency_EDA.ipynb)


## Dashboard

# Importación de datos.

Una vez importado el csv cryptocurrency_final, se optó por dividir el dataset en 1 tabla de hecho y 2 tablas de dimensiones según las siguientes variables elegidas del dataset:

*Cripto_Id*: identifcando las monedas con su nombre, categoria, símbolo y posición en el raking de capitalización del mercado.

*Price* [Precio]: colocando los precios de cada moneda con la fecha correspondiente.

*Cryptocurrency*: tabla de hecho que muestra por cada registro una fecha a partir del 01-08-2023 hasta el 15-08-2023 para cada una de las monedas del dataset, su MarketCap y TotalVolume.

Una vez efectuadas las creaciones de tablas y algunas transformaciones mínimas en **`Power Query`**, procedimos a unir las tablas en la vista "Modelo" mediante la clave primaria de cada tabla con la tabla de transacciones creando un esquema estrella. 

A su vez creamos la tabla *calendario* para poder ser utilizada en funciones de inteligencia de tiempo y mayor nivel de agregación de datos.

El modelo quedó de la siguiente forma:

![Modelo](https://github.com/Angiea18/Criptomonedas-Data-Analytics/blob/main/src/Modelo.png)

## Modelado 

El dashboard consta de 1 portada y 4 páginas navegables a través de una botonera de navegación.

## Portada

En esta página introductoria, se presenta el informe "Análisis de Criptomonedas" y se indica el autor responsable de su creación. Sirve como punto de partida para explorar los datos y los hallazgos presentados en el informe.

![Portada](https://github.com/Angiea18/Criptomonedas-Data-Analytics/blob/main/src/Portada.png)

##  Panorama General
En esta página se brinda una visión general del análisis de criptomonedas. Se presentan varios aspectos clave, como el `"Total de Monedas"` incluidas en el análisis. Además, se muestra el `"Ranking"` de las criptomonedas según su capitalización de mercado, lo que permite identificar rápidamente las monedas más influyentes. El `"Mercado de Capitalización por Moneda"` ilustra la distribución de valor entre las diferentes criptomonedas. También se destacan los valores extremos de `"Precio Mínimo"` y `"Precio Máximo"` por moneda, lo que proporciona una comprensión inmediata de la variabilidad de los precios. El análisis temporal se explora mediante el `"Precio de las Criptomonedas según la Fecha"`, mientras que el `"Volumen Total por Criptomoneda" `revela la actividad de negociación en el mercado.

![Panorama](https://github.com/Angiea18/Criptomonedas-Data-Analytics/blob/main/src/Panorama.png)

## Detalles de las Criptomonedas
Esta página se enfoca en los detalles más específicos de las criptomonedas analizadas. Se resaltan los extremos de `"Máximo Volumen Total"` y `"Mínimo Volumen Total"`, lo que arroja luz sobre las monedas más y menos negociadas. La `"Volatilidad del Precio"` ofrece información sobre la variabilidad en los precios de las criptomonedas. El `"Volumen Total de Negociación por Moneda"`  refleja la actividad de compra y venta para cada criptomoneda, mientras que el `"Cambio Promedio Diario por Moneda"` presenta las fluctuaciones diarias de precio.

![Detalles](https://github.com/Angiea18/Criptomonedas-Data-Analytics/blob/main/src/Detalles.png)

## KPIs
Esta página alberga los **`Indicadores Clave de Desempeño (KPIs)`** más relevantes del análisis. El `"Porcentaje de Cambio de Mercado de Capitalización por Moneda"` muestra la evolución de la capitalización de mercado para cada criptomoneda. El `"Porcentaje de Cambio en el Precio Promedio"` refleja cómo los precios han variado en el tiempo. Finalmente, el `"Volumen Total de Negociación por Moneda"` detalla el nivel de actividad comercial. Estos KPIs proporcionan una instantánea rápida de los aspectos cruciales del análisis de criptomonedas.

![KPIs](https://github.com/Angiea18/Criptomonedas-Data-Analytics/blob/main/src/KPIs.png)



## Conclusiones

- **Porcentaje de Cambio en el Mercado de Capitalización por Moneda:** La mayoría de las criptomonedas experimentaron un crecimiento en su capitalización de mercado, indicando un interés continuo en estas monedas líderes. Sin embargo, algunas monedas como `BUSD` y `TUSD` registraron disminuciones significativas en su capitalización.

- **Porcentaje de Cambio en el Precio Promedio:** Los precios promedio de las criptomonedas tuvieron variaciones diversas. Mientras algunas como `BTC` y las `stablecoins` mantuvieron su estabilidad, otras como `XRP` experimentaron caídas notables en su precio promedio.

- **Volumen Total de Negociación por Moneda:** El aumento general en el volumen de negociación refleja un mayor interés y actividad comercial en el mercado de criptomonedas. Algunas criptomonedas destacadas experimentaron aumentos notables en su volumen total de negociación.
