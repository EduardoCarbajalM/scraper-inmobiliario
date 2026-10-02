# 🏙️ CDMX Real Estate Analytics & ML: Detección Algorítmica de Oportunidades

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-4EA94B?style=for-the-badge&logo=mongodb&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Playwright](https://img.shields.io/badge/Playwright-2EAD33?style=for-the-badge&logo=playwright&logoColor=white)

## 📌 Visión General del Proyecto
Este proyecto es un pipeline integral de datos (End-to-End) diseñado para analizar el mercado de rentas residenciales en las zonas de mayor demanda de la Ciudad de México. A través de técnicas de Web Scraping, Ingeniería de Datos y Machine Learning, el sistema extrae anuncios en bruto, purifica la información, y utiliza algoritmos predictivos y no supervisados para detectar **propiedades subvaluadas (gangas)** y segmentar el mercado en clústeres reales.

Los datos procesados y exportados por este pipeline alimentan de forma directa un portafolio interactivo desarrollado en **React, Vite y Tailwind CSS**.

## ⚙️ Arquitectura y Fases del Pipeline (Jupyter Notebook)

El análisis está estructurado en 8 fases secuenciales orientadas a la escalabilidad y reproducibilidad:

1. **Extracción de Datos (Playwright):** Scraping automatizado del portal Inmuebles24, extrayendo dinámicamente precios, ubicaciones y metros cuadrados mediante expresiones regulares (Regex).
2. **ETL y Data Quality (Pandas & MongoDB):** Conexión a la base de datos NoSQL, casteo de tipos, creación de variables (`precio_por_m2`) y aplicación de filtros estrictos para eliminar *outliers* y errores de captura (Data Cleansing).
3. **Análisis Estadístico:** Cálculo de métricas de dispersión, promedios y generación del Top de zonas con mejor relación Costo-Beneficio.
4. **Renderizado Geoespacial (Folium & GeoPandas):** Cruce espacial con polígonos oficiales del Gobierno de la CDMX para generar un mapa web interactivo (`.html`).
5. **Persistencia de Datos:** Volcado automatizado de los DataFrames procesados a formato CSV para respaldos y auditoría.
6. **Detección de Anomalías de Precio (Regresión Lineal):** Cálculo de la línea teórica de mercado (Y = mX + b) para identificar propiedades con un precio real significativamente inferior al esperado según su tamaño y ubicación.
7. **Segmentación de Mercado (K-Means Clustering):** Estandarización de variables (`StandardScaler`) y aplicación de aprendizaje automático no supervisado para descubrir los 3 perfiles ocultos del mercado (Urbano, Premium y Anomalías).
8. **Inteligencia de Negocio (DataViz):** Generación de gráficas estáticas con Seaborn y exportación final en formato JSON para el consumo asíncrono desde el Frontend.

## 📊 Hallazgos Clave (Insights de Negocio)

* **La Paradoja del Centro:** A pesar de la percepción de zonas como Roma o Condesa, el análisis demostró que la colonia Centro posee el costo promedio por metro cuadrado más alto debido a la proliferación de micro-espacios.
* **Coyoacán como Retorno Óptimo:** La regresión lineal identificó a Coyoacán como el área de mayor viabilidad para el segmento accesible (< $25k MXN), ofreciendo la mejor proporción de metros cuadrados por peso invertido.
* **Regla Inmobiliaria Confirmada (Matriz de Correlación):** Se demostró una correlación negativa (-0.33) entre el tamaño del inmueble y su precio unitario, validando matemáticamente que los espacios reducidos tienen un sobreprecio por $m^2$.

## 🚀 Cómo ejecutar el proyecto localmente

1. Clona el repositorio:
   ```bash
   git clone [https://github.com/tu-usuario/bienes_raices_cdmx.git](https://github.com/tu-usuario/bienes_raices_cdmx.git)
   cd bienes_raices_cdmx