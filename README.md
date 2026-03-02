#  **Profitability Analysis of the Implementation of Sustainability Projects at Chrysal**
🎯 OBJECTIVE
Define the annual profitability of implementing sustainability projects and review whether the investment is generating higher income.

## 📂 Project Description
This project includes the inspection, cleaning, transformation, and analysis of three data sources::

Revenue Sales Order  (Tabla1_Chrysal_Sustainability_v2.csv)
Marketing campaign costs (Tabla2_Marketing_Campaign.csv)
Production and disposal waste costs (Tabla3_Costs_v2.csv)

Processes are implemented for:

-Data cleaning (dates, columns, duplicates).
-Temporal enrichment (day, week, month).
-Business metrics: CAC (Customer Acquisition Cost), conversion rate, monthly revenue.
-Visualizations to support the conclusions.

## 📈 Main Results
### 🧑‍💻 Ingreso en USD por venta de productos - Revenue-sustainability-Chrysal

<a href="https://postimages.org/" target="_blank"><img src="https://i.postimg.cc/XYkjXvLj/General-Revenue-USD.jpg" alt="General-Revenue-USD"></a><br><br>

- It was found that there are 70 null values in "Sales_revenue_USD", which corresponds to 100% nulls. For this reason, we must conduct verification tests to determine how to handle them.
- **Sales Revenue USD:** Possibly right-skewed with an “outlier,” since the max is double the 75% value.
- **Production Cost:** Possibly a normal distribution, but this should be confirmed using a histogram.
- **Waste_kg and Disposal_waste_cost:** Possibly a skewed distribution or a left-side “outlier,” since the min is 10 times lower than the 25% value.


### 📈 Outliers

Evaluation of quartiles to identify outliers and determine the type of data distribution.

<a href="https://postimages.org/" target="_blank"><img src="https://i.postimg.cc/Z5xb0qH4/Revenue-Boxplot.jpg" alt="Revenue-Boxplot"></a><br><br>

<a href="https://postimages.org/" target="_blank"><img src="https://i.postimg.cc/sg4j12mV/Revenue-Boxplot-Year.jpg" alt="Revenue-Boxplot-Year"></a><br><br>

**No dominance of trends by year and country is observed.**


Durante el primer dia el 72.18% de los clientes toman la decision de comprar.
Conversión en meses

Ratifica que la mayoria de los clientes compran en el primer mes.
### 💰Profit 

<a href="https://postimages.org/" target="_blank"><img src="https://i.postimg.cc/Hk9YjLzT/Profit-per-year-PCT.jpg" alt="Profit-per-year-PCT"></a><br><br>

<a href="https://postimages.org/" target="_blank"><img src="https://i.postimg.cc/fbWwdh21/usd-profit-per-year.jpg" alt="usd-profit-per-year"></a><br><br>


🧭 

📊 

Costo mensual por fuente

💸 CAC por Fuente
Costo de adquisicion por cliente

📉 ROMI
Retorno a la inversion

## 🧰 Herramientas Utilizadas
- Python: manipulación y análisis de datos
- Pandas: limpieza y transformación
- Matplotlib & Seaborn: visualización de datos
- NumPy & SciPy: estadísticas y prueba de hipótesis
- Jupyter Notebook
## 🚀 Conclusion
El informe muestra resultados positivos generales, con un LTV mayor que el CAC, indicando ganancias por encima del margen del 50%. Sin embargo, las fuentes de marketing con mayor uso generan menor retorno, siendo la fuente 3 la de mayor costo y menor retorno, mientras que la fuente 10 tiene el menor costo y mayor retorno.

Se destaca la necesidad de volumen de clientes, ya que la alta tasa de conversión del primer día (72.18%) sugiere que la prioridad debe ser atraer usuarios a la página. El tiempo promedio de visita (10 minutos) y la frecuencia semanal indican una decisión de compra rápida una vez que el cliente ingresa.

Mensualmente, las ventas disminuyeron en noviembre de 2017 (mes 6), a pesar de ser el segundo mes con mayor inversión en publicidad, lo que requiere investigación (posiblemente relacionado con la falta de eventos relevantes). El ingreso promedio por venta es de $8.62, y el valor de vida promedio del cliente es de $18.92, lo que implica que realizan más de una compra. Se enfatiza la importancia del volumen de clientes y el alcance.



