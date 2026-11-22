# herramientasbasicas-dupre-guadalupe3# <span style="color:#1E3A8A;">📊 Análisis de Ocupación, Tarifas y Cancelaciones en la Industria Hotelera</span>
#### *Análisis exploratorio del comportamiento de las reservas hoteleras*

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![UTN.BA](https://img.shields.io/badge/UTN.BA-e--Learning-blue?style=for-the-badge)

Este proyecto tiene como finalidad analizar los datos de reservas de dos tipos de establecimientos hoteleros, **City Hotel** y **Resort Hotel**, para identificar patrones relacionados con las tarifas, la anticipación de las reservas, las cancelaciones y la demanda a lo largo del año.

A través de un proceso de exploración, limpieza, transformación y visualización de datos, se busca obtener información que permita comprender mejor el comportamiento de las reservas y reconocer tendencias relevantes para la gestión hotelera.

---

### <span style="color:#2563EB;">📁 1. Origen de los datos</span>
Para desarrollar el proyecto se utilizó el conjunto de datos [**Hotel Booking Demand**](https://www.kaggle.com/datasets/jessemostipak/hotel-booking-demand), obtenido de **Kaggle**.  
El dataset original contiene **119.390 registros y 32 variables**, correspondientes a reservas de dos tipos de hoteles: *City Hotel* y *Resort Hotel*.

Entre las variables disponibles se encuentran:
* Tipo de hotel (`hotel`).
* Estado de cancelación de la reserva (`is_canceled`).
* Días de anticipación de la reserva (`lead_time`).
* Fecha de llegada (`arrival_date`).
* Cantidad de noches de estadía (`stays_in_weekend_nights`, `stays_in_week_nights`).
* Cantidad de huéspedes (`adults`, `children`, `babies`).
* Segmento de mercado (`market_segment`).
* Tarifa diaria promedio (`adr`).
* Estado final de la reserva (`reservation_status`).

---

### <span style="color:#2563EB;">🎯 2. Objetivo y preguntas de investigación</span>
El objetivo principal es analizar el comportamiento de las reservas hoteleras, identificando factores relacionados con las tarifas, las cancelaciones y la demanda según el tipo de establecimiento.

La investigación se organizó a partir de **cuatro preguntas principales**:
1. ¿Cómo se distribuyen las tarifas diarias promedio (ADR) de las reservas y en qué rango de precios se concentra la mayoría?
2. ¿Qué segmento de mercado genera la tarifa diaria promedio más elevada?
3. ¿Los clientes que cancelan sus reservas realizan la reserva con mayor o menor anticipación que aquellos que concretan su estadía?
4. ¿Cómo varía el volumen mensual de reservas a lo largo del año según el tipo de hotel?

---

### <span style="color:#2563EB;">🧹 3. Preparación y limpieza de los datos</span>
El proceso de preparación se realizó utilizando **Python y Pandas** en Google Colab. El dataset original contenía 119.390 registros y 32 columnas. Durante la revisión de calidad se identificaron y eliminaron las filas duplicadas exactas mediante el método `drop_duplicates()`, conservando **87.396 registros únicos**.

Se realizó el tratamiento de los valores nulos mediante los siguientes criterios:
* **`agent` y `company`:** se reemplazaron los valores faltantes por `0`.
* **`country`:** se reemplazaron los valores faltantes por `"Unknown"`.
* **`children`:** se reemplazaron los valores faltantes por `0`.

Posteriormente, se verificó que no quedaran valores nulos en el conjunto de datos, y se realizó la estandarización de variables de texto junto con la conversión de columnas numéricas a sus tipos de datos correspondientes.

---

### <span style="color:#2563EB;">⚙️ 4. Transformación de variables</span>
Para enriquecer el análisis se crearon nuevas variables a partir de las columnas originales:
* **`arrival_date`:** combina el año, mes y día de llegada para obtener una fecha completa.
* **`total_nights`:** calcula la cantidad total de noches, sumando las noches de semana y de fin de semana.
* **`total_guests`:** calcula la cantidad total de huéspedes, sumando adultos, niños y bebés.
* **`total_revenue`:** estima los ingresos de las estadías concretadas, considerando la tarifa diaria promedio y la cantidad de noches (asignando valor `0` a las reservas que no cumplen las condiciones establecidas en el cálculo).

---

### <span style="color:#2563EB;">🔎 5. Análisis exploratorio y visualizaciones</span>
Se desarrollaron cuatro visualizaciones para responder las preguntas de investigación:

* **Gráfico 1. Distribución del Precio por Noche (ADR):**  
  Se analizó la distribución de las tarifas diarias promedio para identificar los rangos de precios más frecuentes.  
  > 💡 **Hallazgo:** La mayor concentración de tarifas se encuentra aproximadamente entre **80 y 140 unidades monetarias**, con una distribución asimétrica positiva y algunos valores superiores a 200.

* **Gráfico 2. Tarifa Promedio por Segmento de Mercado:**  
  Se comparó la tarifa diaria promedio entre los distintos segmentos de mercado.  
  > 💡 **Hallazgo:** El segmento **Direct** presenta la tarifa promedio más elevada, con aproximadamente **115,3**, seguido por **Online TA**, con **114,7**. Los segmentos corporativos y grupales presentan valores inferiores a 90.

* **Gráfico 3. Días de Anticipación según Estado de Cancelación:**  
  Se comparó la anticipación con la que se realizan las reservas según hayan sido concretadas o canceladas.  
  > 💡 **Hallazgo:** Las reservas canceladas presentan una mediana de anticipación cercana a **80 días**, mientras que las reservas concretadas presentan una mediana aproximada de **40 días**, mostrando una asociación entre mayor anticipación y mayor presencia de cancelaciones.

* **Gráfico 4. Evolución Mensual de Reservas por Tipo de Hotel:**  
  Se analizó la cantidad de reservas según el mes de llegada y el tipo de establecimiento.  
  > 💡 **Hallazgo:** Ambos establecimientos presentan variaciones estacionales en el volumen de reservas. El **City Hotel** registra una cantidad superior de reservas en varios períodos del año, evidenciando diferencias en la demanda entre ambas tipologías. *(Nota: la cantidad de reservas no representa directamente la tasa de ocupación hotelera, ya que no contempla la capacidad total de habitaciones disponibles ni la duración de cada estadía).*

---

### <span style="color:#2563EB;">💡 6. Principales conclusiones</span>
El análisis permitió identificar distintos patrones en el comportamiento de las reservas hoteleras:
* Las tarifas presentan una marcada concentración en determinados rangos de precios, aunque coexisten reservas con valores más elevados.
* El segmento **Direct** registra la tarifa diaria promedio más alta, seguido de cerca por **Online TA**, lo que permite reconocer diferencias significativas asociadas a cada canal de comercialización.
* Las reservas canceladas presentan una mayor anticipación que las concretadas, posicionando al *lead time* como una variable clave para estudiar y gestionar cancelaciones.
* El análisis mensual demuestra variaciones estacionales y diferencias estructurales en la demanda entre *City Hotel* y *Resort Hotel* a lo largo del año.

---

### <span style="color:#2563EB;">🛠️ 7. Herramientas y metodología</span>

| Herramienta | Aplicación |
| :--- | :--- |
| **Python** | Procesamiento y análisis de datos |
| **Pandas** | Exploración, limpieza y transformación de datos |
| **NumPy** | Operaciones y creación de variables derivadas |
| **Matplotlib** | Construcción de visualizaciones |
| **Seaborn** | Análisis gráfico y visualización estadística |
| **Power BI** | Diseño de dashboard interactivo y métricas DAX |
| **Google Colab** | Desarrollo y documentación del proyecto |
| **GitHub** | Organización y publicación del proyecto |

---

### <span style="color:#2563EB;">📌 8. Alcance y consideraciones</span>
Para interpretar correctamente los resultados, es importante tener en cuenta que:
* El análisis parte de un dataset original de **119.390 registros** y conserva **87.396 registros únicos** tras eliminar duplicados exactos.
* Los valores nulos fueron tratados según los criterios establecidos durante la limpieza.
* Las variables derivadas se calcularon a partir de la información disponible en el dataset.
* La tarifa diaria promedio (`ADR`) y los ingresos estimados son indicadores diferentes.
* El volumen de reservas no equivale directamente a la tasa de ocupación hotelera.
* Las relaciones observadas entre variables son descriptivas y no implican necesariamente causalidad.

---

### <span style="color:#2563EB;">📂 9. Estructura del repositorio</span>

```text
herramientasbasicas-dupre-guadalupe/
│
├── data/
│   └── raw/
│       └── hotel_bookings.csv
│
├── notebooks/
│   └── Untitled16.ipynb
│
├── dashboard/
│   └── hotel_booking_dashboard.pbix
│
└── README.md

