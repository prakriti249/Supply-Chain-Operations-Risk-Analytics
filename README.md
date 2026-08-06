# 📦 Supply Chain Performance Analysis & Dashboard

An end-to-end analytics project that cleans, explores, and visualizes the **DataCo Global Supply Chain dataset** to uncover the drivers of late deliveries and their impact on profitability — delivered as a Python/Jupyter analysis and an interactive Power BI dashboard.

---

## 🔍 Overview

Late deliveries are one of the biggest hidden costs in supply chain operations. This project analyzes **172,765 orders** to answer three core business questions:

1. **How bad is the late-delivery problem, and what does it cost?**
2. **Which regions, shipping modes, and customer segments are most affected?**
3. **When (month, day, hour) do delays spike, and can they be predicted?**

The workflow starts in Python (data cleaning + exploratory analysis) and ends in Power BI (an executive-level, interactive dashboard) so the findings can be explored by non-technical stakeholders.

---

## 🗂️ Repository Structure

```
├── Supply_Chain.ipynb                 # Data cleaning + EDA notebook (Python)
├── Supply_chain_analysis_db.pbix      # Power BI dashboard
├── cleaned_supply_chain.csv           # Cleaned dataset (output of the notebook)
└── README.md
```

---

## 📊 Dataset

- **Source:** [DataCo Smart Supply Chain Dataset](https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis) (Kaggle)
- **Size:** ~180K raw orders → 172,765 after cleaning
- **Granularity:** One row per order item, covering order dates, shipping dates, shipping mode, customer segment, region, product category, and profit per order

### Data Cleaning (in `Supply_Chain.ipynb`)
- Dropped 33 columns that were personally identifiable (customer name/email/address), redundant, or had zero variance (e.g. `Product Status`, `Benefit per order`)
- Removed cancelled orders (not relevant to delivery-time analysis)
- Converted order/shipping date columns to proper datetime format
- Engineered new features:
  - `Order Processing Time` — actual days taken to ship
  - `Delay` — actual processing time minus scheduled shipment days
  - `Is_Delayed` — boolean flag for late orders
  - `order_month`, `order_day`, `order_hour` — for time-based trend analysis
  - `Profitability Flag` — Profit / Loss / Break-even, based on order profit

---

## 📈 Exploratory Analysis Highlights

- **On-time delivery rate:** 45.3% — more than half of all orders (54.7%) arrive late
- **90th percentile delay:** 3 days beyond the scheduled shipment window
- **Total profit:** $7.5M generated, against **$2.1M in losses tied to delayed orders**
- Late delivery rates broken down by **region, shipping mode, customer segment, order status, and department**, with top-driver analysis per region
- Delay-rate trends across **month, day of week, and hour of day** to spot seasonal/operational patterns
- Profit-per-delay-day analysis to quantify how much each additional delay day costs the business

Visualizations were built with `matplotlib` and `seaborn`, using a consistent viridis-based color theme for a clean, professional look.

---

## 📉 Power BI Dashboard

`Supply_chain_analysis_db.pbix` turns the analysis into an interactive, single-page **Supply Chain Performance Dashboard**.

**KPI Cards**
- Total Orders
- Delayed Orders
- On-Time Delivery %
- Late Delivery %
- Average Delay (Days)

**Visuals**
| Visual | Insight |
|---|---|
| Line chart — Late Delivery Rate by Month | Seasonal trend in delays across the year |
| Bar chart — Late Delivery Rate by Shipping Mode | Which shipping modes underperform |
| Bar chart — Late Delivery Rate by Region | Geographic hotspots for delays |
| Donut chart — Profitability Distribution | Split of Profit / Loss / Break-even orders |

**Interactive Filters (Slicers)**
- Order Region
- Shipping Mode
- Customer Segment
- Department Name

The report uses a modern, Microsoft Fluent–inspired design system for an executive-ready look and feel.

---

## 🛠️ Tech Stack

- **Python:** pandas, numpy, matplotlib, seaborn
- **Jupyter Notebook** for data cleaning & EDA
- **Power BI Desktop** for the interactive dashboard (DAX measures, slicers, KPI cards)

---

## ▶️ How to Run

1. Clone this repo
2. Download the [DataCo Supply Chain Dataset](https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis) and place `DataCoSupplyChainDataset.csv` in the project folder
3. Open `Supply_Chain.ipynb` in Jupyter and run all cells — this produces `cleaned_supply_chain.csv`
4. Open `Supply_chain_analysis_db.pbix` in **Power BI Desktop** and refresh the data source to point at the cleaned CSV

---

## 👤 Author

**Prakriti**
B.Tech Biotechnology, Birla Institute of Technology (BIT), Mesra
📧 prakritik016@gmail.com | 💻 [github.com/prakriti249](https://github.com/prakriti249)
