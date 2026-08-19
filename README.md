# 🌱 Profitability Analysis of the Implementation of Sustainability Projects at Chrysal

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Wrangling-150458?logo=pandas)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557C)
![Seaborn](https://img.shields.io/badge/Seaborn-Statistical%20Viz-4C72B0)
![SciPy](https://img.shields.io/badge/SciPy-Hypothesis%20Testing-8CAAE6?logo=scipy)

## 🎯 Objective

To define the annual profitability of implementing sustainability projects at Chrysal and to evaluate whether the investment is generating higher income, by analyzing sales, production/waste costs, and marketing campaigns across four countries: **Colombia, Ecuador, the Netherlands, and Kenya**.

---

## 📂 Project Description

This project covers the full data analytics workflow — inspection, cleaning, transformation, and analysis — of three data sources:

| Dataset | Content | Key fields |
|---|---|---|
| `Tabla1_Chrysal_sustainability.csv` | Sales orders by country, product, and date | `sales_revenue`, `production_cost_usd`, `pais`, `product_reference`, `campaign_id` |
| `Tabla2_Marketing_Campaign.csv` | Marketing campaign costs and type | `Marketing_cost`, `Marketing_campaign_type` |
| `Tabla3_Costs.csv` | Waste disposal costs by product | `Disposal_waste_cost`, `Product_reference` |

**Processes implemented:**
- Data cleaning: duplicate removal, null-value detection and imputation (median), date parsing (year/month extraction)
- Outlier treatment using the **IQR method** (winsorization applied to Colombia's sales revenue)
- Business metrics: `costo_total`, `gross_profit`, `% profit margin`, profit per sale
- Table integration (merge) across sales, costs, and marketing data using common keys
- Hypothesis testing (t-test) to compare profitability across marketing campaigns
- Correlation analysis between numeric business variables

---

## 🧰 Tools Used

- **Python** — data manipulation and analysis
- **Pandas / NumPy** — cleaning, transformation, and aggregation
- **Matplotlib & Seaborn** — data visualization
- **SciPy (`ttest_ind`)** — statistical hypothesis testing
- **Jupyter Notebook** — analysis environment

---

## 📈 Main Results

### 1️⃣ Data Quality & Distribution

No null values were found in the `sales` table. The `costs` table had **~5% missing values**, concentrated in the product *Chrysal Flora F* (~34% of its records) — indicating a localized data-collection issue rather than randomness.

- **Sales Revenue USD**: right-skewed distribution, with a maximum ~5x the 75th percentile — indicating outliers.
- **Production Cost**: close to a normal distribution.
- **Waste_kg / Disposal_waste_cost**: right-skewed, with the max roughly double the 75th percentile.

<p float="left">
  <img src="images/hist_revenue.png" width="32%" />
  <img src="images/hist_production_cost.png" width="32%" />
  <img src="images/hist_disposal_waste.png" width="32%" />
</p>

### 2️⃣ Outlier Detection (IQR)

Boxplot analysis shows the **Netherlands has no outliers** despite having the highest revenue values, while **Colombia does show outliers** in `sales_revenue`. These were treated by capping values at the upper IQR limit (winsorization) to avoid distorting downstream metrics.

<p float="left">
  <img src="images/boxplot_revenue_country.png" width="45%" />
  <img src="images/boxplot_disposal_product.png" width="45%" />
</p>

No clear dominance by year or category was found in the categorical variables (country, product, campaign type) — no single segment disproportionately drives the results.

### 3️⃣ Revenue vs. Cost by Country

[![sales-cost-per-country.png](https://i.postimg.cc/02Nw6B5X/sales-cost-per-country.png)](https://postimg.cc/3WPRV9v2)
![Revenue vs Cost by Country](images/revenue_cost_by_country.png)

### 4️⃣ Profitability by Country

The Netherlands leads with **~19.2M USD in gross profit**, well above the other three markets:
[![profit-per-country.png](https://i.postimg.cc/6pynP1Dc/profit-per-country.png)](https://postimg.cc/Xr6rGxNB)
![Profit by Country](images/profit_by_country.png)

Looking at **profit margin (%)** rather than absolute USD confirms the same pattern — the Netherlands converts revenue into profit far more efficiently (**69.7% margin**) than Colombia (37.7%), Ecuador (33.7%), or Kenya (33.3%), likely influenced by the Euro exchange effect and higher purchasing power in Europe:

![Margin % by Country](images/margin_pct_by_country.png)

### 5️⃣ Profitability Over Time

Looking at the actual computed yearly margin (not just absolute profit), the company's margin has remained **relatively stable, around 47%–50%** between 2023 and 2025, rather than showing a sharp decline — 2024 dipped slightly to 47.1% before recovering to 49.5% in 2025:

<p float="left">
  <img src="images/profit_per_year.png" width="45%" />
  <img src="images/margin_pct_by_year.png" width="45%" />
</p>

### 6️⃣ Marketing Campaign Profitability

Profit by campaign type (Email marketing, Field campaign, Influencers Agro, Social Media):

![Marketing Profitability](images/profit_by_campaign.png)

Breaking this down **by country and campaign type** together shows that "Field campaign" and "Email marketing" consistently generate the highest profit across all four countries, while "Influencers Agro" is the weakest performer everywhere:

![Profit by Country and Campaign](images/profit_country_campaign.png)

An **independent t-test** was run to compare profit-per-sale between campaign types (e.g., Field campaign vs. Influencers Agro). **Result: p-value > 0.05** — there is **no statistically significant difference** in profitability between marketing campaign types, meaning investment channel alone does not explain profitability differences at the individual sale level.

### 7️⃣ Correlation Heat Map

![Correlation Heat Map](images/correlation_heatmap.png)

`sales_revenue` and `profit_per_sale` show a strong positive correlation (~1.0), consistent with their direct mathematical relationship. `production_cost` and `Disposal_waste_cost` show weaker relationships with overall profitability.

---

## 🚀 Conclusions

- The **Netherlands is the most profitable market**, both in absolute gross profit (~19.2M USD) and in margin efficiency (69.7% vs. ~33–38% in the other countries).
- **Overall company profitability has stayed relatively stable** (~47%–50% margin) across 2023–2025, with a small dip in 2024 — this contradicts an earlier draft conclusion in the notebook and is based on the actual computed `margin_pct` values.
- **Colombia's sales revenue contained outliers**, addressed via IQR-based winsorization to ensure reliable metrics.
- **Field campaigns and Email marketing consistently outperform** Influencers Agro and Social Media in absolute profit across every country, but this difference is **not statistically significant** at the individual-sale level (p-value > 0.05).
- Missing values in waste disposal costs were concentrated in one product line (*Chrysal Flora F*), suggesting a data-collection gap rather than a systemic issue.

---

## 📁 Repository Structure

```
├── chrysal_profit_sustainability.ipynb   # Full analysis notebook
├── images/                                # Exported charts used in this README
└── README.md
```

## ▶️ How to Run

```bash
pip install pandas numpy matplotlib seaborn scipy
jupyter notebook chrysal_profit_sustainability.ipynb
```



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

📊 Marketing profitability after A/B Hypothesis test

[![Marketinf-profitability.png](https://i.postimg.cc/gk6GBVgm/Marketinf-profitability.png)](https://postimg.cc/tYp0sx0M)

💸 CORRELATION HEAT MAP

[![correlation-heat-map.png](https://i.postimg.cc/yWqCzGLD/correlation-heat-map.png)](https://postimg.cc/H8thw6Dm)

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



