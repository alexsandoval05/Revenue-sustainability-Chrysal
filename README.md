# 🌱 Profitability Analysis of the Implementation of Sustainability Projects at Chrysal

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?logo=powerbi&logoColor=black)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Wrangling-150458?logo=pandas)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557C)
![Seaborn](https://img.shields.io/badge/Seaborn-Statistical%20Viz-4C72B0)
![SciPy](https://img.shields.io/badge/SciPy-Hypothesis%20Testing-8CAAE6?logo=scipy)

 **Note:** This project uses a simulated dataset created for educational purposes as part of the TripleTen Data Analyst bootcamp. The data is inspired by the general business context of a company in the sustainability/manufacturing sector but does not represent actual financial figures, real transactions, or confidential information from any employer.

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
- **Power BI** — interactive dashboard for exploring profitability by country, product, and campaign
- **Pandas / NumPy** — cleaning, transformation, and aggregation
- **Matplotlib & Seaborn** — data visualization
- **SciPy (`ttest_ind`)** — statistical hypothesis testing
- **Jupyter Notebook** — analysis environment

---

## 📈 Main Results

### 🧑‍💻 Revenue Distribution & Data Quality

No null values were found in the `sales` table. The `costs` table had **~5% missing values**, concentrated in the product *Chrysal Flora F* (~34% of its records) — indicating a localized data-collection issue rather than randomness.

**Sales Revenue USD** shows a right-skewed distribution, with a maximum ~5x the 75th percentile — a clear sign of outliers that needed further investigation.

[![sales-revenue.png](https://i.postimg.cc/ht93XvtM/sales-revenue.png)](https://postimg.cc/CRx4tFDf)

### 📊 Outlier Detection (IQR)

Boxplot analysis shows the **Netherlands has no outliers** despite having the highest revenue values, while **Colombia does show outliers** in `sales_revenue`. These were treated by capping values at the upper IQR limit (winsorization) to avoid distorting downstream metrics.

[![Outliers.png](https://i.postimg.cc/bw9cK3bC/Outliers.png)](https://postimg.cc/gxjThyg8)

No clear dominance by year or country was found when comparing revenue per product — no single segment disproportionately drives the results.

[![revenue-per-product.png](https://i.postimg.cc/9f08JpBb/revenue-per-product.png)](https://postimg.cc/gw9H03QL)

### 💰 Profitability

**Revenue vs. total cost by country:**

[![sales-cost-per-country.png](https://i.postimg.cc/02Nw6B5X/sales-cost-per-country.png)](https://postimg.cc/3WPRV9v2)

**Gross profit by country** — the Netherlands leads with **~19.2M USD in gross profit**, about **25.7% higher** than Colombia, Ecuador, and Kenya. In margin terms this is even more striking: the Netherlands converts revenue into profit at a **69.7% margin**, versus 37.7% (Colombia), 33.7% (Ecuador), and 33.3% (Kenya) — likely influenced by the Euro exchange effect and higher purchasing power in Europe.

[![profit-per-country.png](https://i.postimg.cc/6pynP1Dc/profit-per-country.png)](https://postimg.cc/Xr6rGxNB)

**Yearly profitability trend** — looking at the actual computed margin (not just absolute profit), the company's margin has stayed **relatively stable, between 47% and 50%**, from 2023 through 2025, with a slight dip in 2024 (47.1%) before recovering to 49.5% in 2025.

[![profit-per-year.png](https://i.postimg.cc/7Z6nkLTJ/profit-per-year.png)](https://postimg.cc/F7MLbNph)

### 📣 Marketing Campaign Profitability

Profit by campaign type (Email marketing, Field campaign, Influencers Agro, Social Media):

[![Marketinf-profitability.png](https://i.postimg.cc/gk6GBVgm/Marketinf-profitability.png)](https://postimg.cc/tYp0sx0M)

An **independent t-test** was run to compare profit-per-sale between campaign types (e.g., Field campaign vs. Influencers Agro). **Result: p-value > 0.05** — there is **no statistically significant difference** in profitability between marketing campaign types, meaning investment channel alone does not explain profitability differences at the individual sale level, even though "Field campaign" and "Email marketing" show higher totals in absolute terms.

### 🔗 Correlation Heat Map

[![correlation-heat-map.png](https://i.postimg.cc/yWqCzGLD/correlation-heat-map.png)](https://postimg.cc/H8thw6Dm)

`sales_revenue` and `profit_per_sale` show a strong positive correlation (~1.0), consistent with their direct mathematical relationship. `production_cost` and `Disposal_waste_cost` show weaker relationships with overall profitability.

### 📉 Power BI Dashboard

A complementary interactive dashboard was built to explore profitability by country, product, and campaign:

[![Dashboard-Profitability-of-Sustainabiliy-od-Chrysal-products.png](https://i.postimg.cc/0N7MRgZ6/Dashboard-Profitability-of-Sustainabiliy-od-Chrysal-products.png)](https://postimg.cc/1g55wjkP)

---

## 🚀 Conclusions

- The **Netherlands is the most profitable market**, both in absolute gross profit (~19.2M USD) and in margin efficiency (69.7% vs. ~33–38% in the other countries).
- **Overall company profitability has stayed relatively stable** (~47%–50% margin) across 2023–2025, with only a small dip in 2024, based on the actual computed `margin_pct` values.
- **Colombia's sales revenue contained outliers**, addressed via IQR-based winsorization to ensure reliable metrics.
- **No statistical evidence** supports that any single marketing campaign type outperforms another in profit-per-sale (p-value > 0.05), even though Field campaigns and Email marketing lead in absolute totals.
- Missing values in waste disposal costs were concentrated in one product line (*Chrysal Flora F*), suggesting a data-collection gap rather than a systemic issue.

## 💡 Business Recommendations

- **Prioritize expansion in high-margin markets over channel optimization.** Since marketing campaign type showed no statistically significant effect on profit-per-sale (p-value > 0.05), investment decisions should focus on market selection and pricing strategy — where the Netherlands' 69.7% margin vs. ~33-38% elsewhere suggests structural, country-level drivers (e.g., pricing power, cost base) matter more than campaign mix.

- **Investigate the Netherlands' margin structure to replicate it.** A margin nearly double that of other markets warrants a deeper cost and pricing breakdown to identify which specific levers (currency effect, local production cost, distribution efficiency) could be partially replicated in Colombia, Ecuador, or Kenya.

- **Close the data-collection gap for Chrysal Flora F.** The concentration of missing waste-disposal cost records in a single product line (~34%) points to a process issue at the source, not a data quality fluke — worth a targeted audit before the metric is used for further financial reporting.

- **Maintain the current stable margin trend (47-50%) as a baseline, and monitor for the 2024 dip.** Since the year-over-year margin held steady with only a small 2024 decline, it's worth flagging whether that dip correlates with a specific event (cost spike, campaign change, currency shift) to confirm it was one-off rather than the start of a downward trend.

---

## 📁 Repository Structure

```
├── chrysal_profit_sustainability.ipynb   # Full analysis notebook
└── README.md
```

## ▶️ How to Run

```bash
pip install pandas numpy matplotlib seaborn scipy
jupyter notebook chrysal_profit_sustainability.ipynb
```
