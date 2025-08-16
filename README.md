# Análisis Exploratorio de Series de Tiempo: IBM y WMT

## Resumen del proyecto

Este proyecto realiza un análisis exploratorio de series de tiempo utilizando los precios de cierre diarios de las acciones de **IBM** y **WMT** durante los últimos 5 años, con el objetivo de:

- Analizar la **correlación** entre ambas acciones.
- Descomponer las series en **tendencia, estacionalidad y residuo**.
- Evaluar la **estacionariedad** mediante la prueba de Dickey-Fuller (ADF).
- Aplicar **promedios móviles simples (SMA)** para pronósticos de corto plazo.
- Validar la precisión de los pronósticos mediante un **backtest**.

## Contenido del repositorio

- `Notebook.ipynb` → Jupyter Notebook con todo el análisis paso a paso, incluyendo gráficos y cálculos.
- Carpeta `figuras/` → contiene las imágenes generadas por el Notebook:
  - Gráficos de precios históricos
  - Descomposición STL
  - Correlogramas (ACF y PACF)
  - Promedios móviles
- `README.md` → resumen del proyecto y conclusiones.

## Análisis realizado

### 1. Correlación

- La correlación entre IBM y WMT es **0.959**, indicando que ambas acciones tienden a moverse en la misma dirección.  
- Gráficamente, se observa que las series presentan tendencias similares a lo largo del tiempo.

### 2. Descomposición de Series (STL)

- La descomposición separa la serie en **tendencia**, **estacionalidad** y **residuo**.
- Ambas acciones muestran una **tendencia creciente** y fluctuaciones diarias.
- La estacionalidad es leve, más perceptible en WMT.

### 3. Correlogramas

- Los gráficos de ACF y PACF muestran autocorrelación positiva en los primeros lags, lo que respalda el uso de promedios móviles para pronósticos simples.

### 4. Prueba de Dickey-Fuller

| Serie | ADF Statistic | p-value | Conclusión |
|-------|---------------|---------|------------|
| IBM   | -0.1944       | 0.9392  | No estacionaria |
| WMT   | 1.0250        | 0.9945  | No estacionaria |

- Ambas series **no son estacionarias**, mostrando tendencia y cambios en la media.

### 5. Promedios Móviles y Pronósticos

- Se calcularon SMA de 5 y 20 días.
- Pronósticos para el siguiente día usando SMA 20 días:

| Serie | Pronóstico (USD) |
|-------|-----------------|
| IBM   | 253.44          |
| WMT   | 99.49           |

- Los SMA capturan la tendencia general y suavizan el ruido diario.

### 6. Backtest SMA 20 días

| Serie | MAE (USD) | MAPE (%) |
|-------|-----------|-----------|
| IBM   | 5.12      | 3.29      |
| WMT   | 1.61      | 2.71      |

- La SMA es una herramienta confiable para pronósticos de corto plazo.
- IBM es más volátil que WMT, reflejándose en un MAE mayor.

## Recomendación de inversión

- **WMT**: recomendada para inversores conservadores, por su menor volatilidad y movimientos más predecibles.
- **IBM**: opción para inversores que toleran mayor riesgo y buscan potenciales rendimientos mayores, debido a su mayor volatilidad.

## Tecnologías y librerías usadas

- Python 3
- Jupyter Notebook
- `yfinance` → descarga de precios históricos
- `pandas` y `numpy` → manipulación de datos
- `matplotlib` y `seaborn` → visualización
- `statsmodels` → pruebas ADF y descomposición STL

## Cómo usar

1. Clonar el repositorio:
```bash
git clone https://github.com/EmmanuelRR-data-science/series-tiempo-ibm-walmart
