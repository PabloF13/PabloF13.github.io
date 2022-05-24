---
layout: post
title:  "Backtesting Dow 30 -Streamlit"
author: pablo
categories: [ Analisis Financiero, Streamlit ]
image: assets/images/Dow/inicio.png
featured: true
---

Vamos a crear una función que nos permita realizar backtesting en diferentes estrategias de trading en el índice Dow Jones 30. También, vamos a desarrollar funciones que nos sirvan de indicadores complementarios como el RSI, la volatilidad, la rentabilidad de los activos o la suma de los indicadores que nos proporciona la web Investing.com.

Además, vamos a utilizar el framework de visualización Streamlit para mostrarlo todo de una manera gráfica e interactiva.

### Backtesting

Dada una cartera y unas comisiones ficticias se muestran los retornos obtenidos desde la fecha seleccionada para las estrategias del cruce de medias móviles de 25, 50, 100 y 200 periodos.

![](/assets/images/Dow/backtesting.png)

### RSI y volatilidad

El RSI muestra un posible cambio de tendencia debido a la posible sobre compra o venta del activo. Esto es así cuando cruza las bandas tanto por arriba como por abajo.

![](/assets/images/Dow/rsi.png)

La volatilidad muestra la variación del precio del activo respecto a su media en el periodo de tiempo seleccionado.

![](/assets/images/Dow/volat.png)

### Indicadores Técnicos Investing.com

Esta función recoge la suma de los indicadores técnicos que nos ofrece la acción para cada uno de los 30 activos. Esta información la obtenemos gracias a la api de investing, *investpy*, y la podemos encontrar en la propia web [https://es.investing.com/technical/indicators](https://es.investing.com/technical/indicators)

![](/assets/images/Dow/itec.png)

### Rentabilidad

Se muestra la rentabilidad diaria, desde el cierre anterior y de las últimas 52 semanas.

![](/assets/images/Dow/rentabilidad.png)
