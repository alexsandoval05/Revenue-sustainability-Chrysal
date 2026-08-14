#  **Profitability Analysis of the Implementation of Sustainability Projects at Chrysal**
🎯 **OBJECTIVE**

To define the annual profitability of implementing sustainability projects and review whether the investment is generating higher income.

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

[![sales-revenue.png](https://i.postimg.cc/ht93XvtM/sales-revenue.png)](https://postimg.cc/CRx4tFDf)

- It was found that there are 70 null values in "Sales_revenue_USD", which corresponds to 100% nulls. For this reason, we must conduct verification tests to determine how to handle them.
- **Sales Revenue USD:** Possibly right-skewed with an “outlier,” since the max is double the 75% value.
- **Production Cost:** Possibly a normal distribution, but this should be confirmed using a histogram.
- **Waste_kg and Disposal_waste_cost:** Possibly a skewed distribution or a left-side “outlier,” since the min is 10 times lower than the 25% value.


### 📈 Outliers

Evaluation of quartiles to identify outliers and determine the type of data distribution.

[![Outliers.png](https://i.postimg.cc/bw9cK3bC/Outliers.png)](https://postimg.cc/gxjThyg8)

[![revenue-per-product.png](https://i.postimg.cc/9f08JpBb/revenue-per-product.png)](https://postimg.cc/gw9H03QL)


**No dominance of trends by year and country is observed.**


Durante el primer dia el 72.18% de los clientes toman la decision de comprar.
Conversión en meses

Ratifica que la mayoria de los clientes compran en el primer mes.
### 💰Profit 

[![profit-per-year.png](https://i.postimg.cc/7Z6nkLTJ/profit-per-year.png)](https://postimg.cc/F7MLbNph)

[![sales-cost-per-country.png](https://i.postimg.cc/02Nw6B5X/sales-cost-per-country.png)](https://postimg.cc/3WPRV9v2)

[![profit-per-country.png](https://i.postimg.cc/6pynP1Dc/profit-per-country.png)](https://postimg.cc/Xr6rGxNB)


🧭 

📊 

Costo mensual por fuente

💸 CAC por Fuente
Costo de adquisicion por cliente

📉 ROMI
Retorno a la inversion

📉 POWER BI - Dashboard

[![Dashboard-Profitability-of-Sustainabiliy-od-Chrysal-products.png](https://i.postimg.cc/0N7MRgZ6/Dashboard-Profitability-of-Sustainabiliy-od-Chrysal-products.png)](https://postimg.cc/1g55wjkP)

## 🧰 Tools used
- Python: Data manipulation and analysis
- Pandas: Cleaning and Transformation
- Matplotlib & Seaborn: Data visualization
- NumPy & SciPy: Statistics and hypothesis testing
- Jupyter Notebook

## 🚀 Conclusions

It is observed that there are representative profit margins of 43% annually after deducting production costs and waste disposal costs.

No evidence was found of significantly higher profit trends by country, despite higher operating costs in locations such as the Netherlands. However, the overall global profit trend is increasing by approximately 7% annually.



