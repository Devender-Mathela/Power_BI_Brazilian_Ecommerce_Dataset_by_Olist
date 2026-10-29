# Brazilian E-Commerce Analytics (Olist)

[![Power BI](https://img.shields.io/badge/Power_BI-DirectQuery-F2C811?logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Data_Modeling-336791?logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![Dataset](https://img.shields.io/badge/Kaggle-100k_Orders-20BEFF?logo=kaggle&logoColor=white)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

An end-to-end data analytics and business intelligence solution analyzing ~100k Brazilian e-commerce orders (2016–2018) across 9 relational tables to solve core operational and marketplace challenges.

---

## 🎯 Business Problem & Objectives

Olist connects small businesses across Brazil to leading marketplaces. Operating at scale revealed critical operational challenges:

1. **Logistics Bottlenecks & Delivery Delays**: Brazil's vast geography causes significant variance in shipping times and freight costs. The business needed to identify where, why, and how often orders breach estimated delivery windows.
2. **Impact of Delivery on Customer Satisfaction**: Negative reviews (1–2 stars) heavily correlate with delivery friction. Management needed clear visibility into whether ratings are driven by product defects or shipping delays.
3. **Revenue & Category Concentration**: High dependence on a few dominant states (e.g., São Paulo, Rio de Janeiro) and product categories creates business risk. Understanding regional demand helps optimize marketing and seller recruitment.
4. **Seller Performance & Fulfillment Quality**: Inconsistent seller performance impacts buyer retention. Identifying underperforming sellers and regional coverage gaps was critical to maintaining SLA standards.
5. **Payment Behavior & Credit Adoption**: Brazilian consumers heavily rely on installments and alternative payments (Boleto). Finance teams required visibility into payment method adoption and order values.

---

## 💡 Key Business Insights

- **Delivery Times Drive Ratings**: Orders delivered late experience a dramatic drop in customer review score (~1.6 avg rating vs. ~4.2 for on-time deliveries).
- **Geographic Concentration**: Southeast Brazil (SP, RJ, MG) accounts for over 65% of total GMV and order volume, while northern regions face higher freight costs and longer transit times.
- **Credit Card Installments Rule High-Ticket Items**: Over 70% of transactions use credit cards, with high-AOV categories relying heavily on multi-month installments.

---

## 📊 Executive Dashboard Preview

The solution includes a multi-page interactive Power BI report (`Brazilian_Ecommerce_Dataset.pbix`):

<p align="center">
  <img src="Dashboard%20Preview/1.%20Overview(Executive%20Dashboard).png" alt="Executive Overview Dashboard" width="80%">
</p>

### Report Pages:
- **1. Executive Overview**: Topline KPIs (GMV, Revenue, Orders, AOV, On-time %, Avg Rating).
- **2. Sales Trends**: YoY revenue trajectories, YTD performance, and 30-day rolling metrics.
- **3. Category & Product**: Volume vs. AOV scatter analysis, revenue share, and top-rated categories.
- **4. Customer Geography**: Regional demand heatmaps, state-by-state order concentrations.
- **5. Delivery & Logistics**: On-time delivery rates, transit duration, and regional delay hot-spots.
- **6. Reviews & Sentiment**: Sentiment breakdown (Positive/Neutral/Negative) vs. delivery timeliness.
- **7. Payments**: Payment mix (Credit Card, Boleto, Voucher, Debit) and installment distributions.
- **8. Seller Performance**: Active sellers, revenue per seller, and regional fulfillment coverage.
- **9. Drillthrough**: Deep-dive operational view filtered by category or seller.

---

## 🛠️ Architecture & Tech Stack

```
Kaggle Olist Dataset (9 CSVs)
       │
       ▼
PostgreSQL Database
  ├─ Schema DDL & Foreign Keys (`sql/Tables.sql`, `sql/ForeignKey.sql`)
  ├─ Optimized Indexes on Keys & Timestamps (`sql/Index.sql`)
  └─ Analytical Views (`sql/Views.sql` ➔ `bi_fact_sales`, `bi_fact_order`)
       │
       ▼
Power BI (DirectQuery + Import Mode for DimDate)
  ├─ Star Schema Modeling & DAX Measures (`sql/DAX Measures.txt`)
  └─ Interactive 9-Page Executive Report (`Brazilian_Ecommerce_Dataset.pbix`)
```

---

## 🚀 Quick Setup

1. **Database Setup**: Run `sql/Tables.sql`, `sql/CopyCSV.sql`, `sql/ForeignKey.sql`, `sql/Index.sql`, and `sql/Views.sql` in PostgreSQL.
2. **Open Dashboard**: Open `Brazilian_Ecommerce_Dataset.pbix` in Power BI Desktop.
3. **Connect Data Source**: Update PostgreSQL connection parameters under **Data source settings** to point to your local database.
