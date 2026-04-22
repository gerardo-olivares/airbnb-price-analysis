# 🏠 Análisis de Precios de Airbnb

Análisis exploratorio de datos (EDA) sobre el mercado de alquiler a corto plazo en 6 ciudades de Estados Unidos.

## 📊 Dataset
- 64,056 listings de Airbnb
- 6 ciudades: NYC, Los Ángeles, San Francisco, Chicago, Boston, Washington DC
- 29 variables incluyendo precio, tipo de habitación, ubicación y reseñas

## 🔍 Contenido del análisis
- Estadísticas descriptivas de todas las variables
- Distribución del precio y transformación logarítmica
- Precio por ciudad, tipo de habitación y número de habitaciones
- Mapa de correlaciones entre variables numéricas
- Distribución geográfica del precio por ciudad
- Ranking de variables con mayor poder predictivo

## 💡 Hallazgos principales
- `room_type` es el predictor más poderoso (eta² = 0.37)
- San Francisco es la ciudad más cara ($165/noche mediana)
- `accommodates` tiene la correlación más alta con el precio (r = 0.57)
- Las calificaciones no predicen el precio (r = 0.09)
- El precio escala de ~$100 (1 hab.) a $900+ (6 habitaciones)

## 🛠 Tecnologías
- Python, Pandas, NumPy
- Matplotlib, Seaborn
- Jupyter Notebook

## 📁 Archivos
- `EDA_Proyecto.ipynb` — Notebook completo con código y visualizaciones
