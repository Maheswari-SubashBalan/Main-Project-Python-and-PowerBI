# E-Commerce Order Sales Analysis

**Using Python and Power BI**

Data Analytics Final Project | Domain: Sales & E-commerce / Retail Analytics

---

## 📌 Project Overview

This project involves cleaning, transforming, and analysing raw e-commerce order data using Python (Pandas, NumPy, Matplotlib, Seaborn) and creating two interactive Power BI dashboards to derive meaningful business insights on sales performance, customer behaviour, and delivery operations.

## 🗂️ Data Source

- **Source:** Hugging Face — [`millat/e-commerce-orders`](https://huggingface.co/datasets/millat/e-commerce-orders)
- **DOI / License:** 10.57967/hf/5258 | MIT License
- **Timeline:** Orders placed between April 2024 and April 2025
- **Records Used:** Random sample of 1000 rows (from 10,000-row dataset), 15 original columns

## ❓ Problem Statement

- Identify meaningful patterns, trends, and insights from raw e-commerce order data using EDA.
- Clean, transform, and preprocess messy real-world order data — missing values, duplicates, outliers.
- Understand which product categories and customer segments drive the most revenue.
- Evaluate delivery performance and marketing channel/device effectiveness.

## 🛠️ Tools & Technologies

| Tool | Purpose |
|------|---------|
| **Python** (Pandas, NumPy, Matplotlib, Seaborn) | Data cleaning, transformation, feature engineering, EDA |
| **Power BI** | Data modelling, DAX calculations, interactive dashboards |

## 📋 Dataset Columns

**Original (15 columns):** `order_id`, `customer_id`, `product_id`, `category`, `price`, `quantity`, `order_date`, `shipping_date`, `delivery_status`, `payment_method`, `device_type`, `channel`, `shipping_address`, `billing_address`, `customer_segment`

**Engineered:** `total_amount`, `order_month` / `month_name` / `month_sort`, `order_year`, `shipping_delay_days`

## 🧹 Data Pre-Processing Steps

1. **Duplicate Removal** — Removed 80 duplicate rows (1000 → 920 rows)
2. **Datetime Conversion** — `order_date` & `shipping_date` → proper datetime format
3. **Missing Value Treatment** — Categorical → mode; Numeric → median
4. **Column Cleanup** — Dropped `billing_address` (duplicate of `shipping_address`)
5. **Outlier Treatment** — IQR method applied to `price` and `quantity` (capped, not dropped)
6. **Feature Engineering** — Created `total_amount`, `order_month`, `order_year`, `shipping_delay_days`, sort-key columns
7. **EDA** — 10 visualizations (univariate, bivariate, multivariate) with business interpretation

## 📊 Power BI Dashboards

### Dashboard 1: Sales & Revenue Performance
KPI cards (Total Revenue, Total Orders, AOV), Monthly Revenue Trend, Revenue by Category, Revenue by Category & Segment, AOV by Customer Segment, Revenue Share by Payment Method.
*Slicers: `category`, `customer_segment`*

### Dashboard 2: Customer, Channel & Delivery Operations
Total Customers, Orders by Delivery Status, Delivery Status by Category, Revenue by Marketing Channel, Order Fulfillment Funnel, Average Shipping Delay by Month, Revenue by Device Type, Price vs Quantity by Category.
*Slicer: `delivery_status`*

## 📈 DAX Measures

```dax
Total Revenue = SUM('ecommerce_orders_cleaned'[total_amount])
Total Orders = DISTINCTCOUNT('ecommerce_orders_cleaned'[order_id])
Average Order Value = DIVIDE([Total Revenue], [Total Orders])
Total Customers = DISTINCTCOUNT('ecommerce_orders_cleaned'[customer_id])
```

## 🔍 Key Insights

- **Total Revenue:** ~$489.40K from 900 qualifying orders | **AOV:** $543.77 | **Customers:** 702
- **Delivery status:** 68.8% Delivered, 20.8% Shipped, 5.3% Returned, 5.1% Pending
- **Top categories:** Toys ($102.5K) and Home ($87.8K) generate the highest revenue
- **VIP/Returning customers** have meaningfully higher AOV than New customers
- `total_amount` correlates strongly with `quantity` (0.68) and `price` (0.61); `price` vs `quantity` nearly independent (-0.03)
- **Shipping delay** shows almost no correlation with order size
- Monthly revenue is **seasonal** — peaked around June 2024, dipped April/August

## ✅ Recommendations

- Invest more marketing spend in Toys and Home; introduce bundle offers for Beauty
- Launch first-purchase incentives to raise New customer AOV
- Plan inventory/staffing ahead of seasonal peaks (e.g., June-type surge)
- Monitor Paid Search ROI against Organic/Social channels
- Investigate categories/payment methods with higher return rates

## 📁 Project Structure

```
├── data/
│   ├── ecommerce_orders_raw.csv
│   └── ecommerce_orders_cleaned.csv
├── notebooks/
│   └── DA_Final_Project_Ecommerce_EDA.ipynb
├── powerbi/
│   └── Ecommerce_Sales_Dashboard.pbix
├── report/
│   └── Ecommerce_Project_Report_Document.pdf
└── README.md
```

## 👤 Author

- **Maheswari Subash Balan**  
- GitHub: [@Maheswari-SubashBalan](https://github.com/Maheswari-SubashBalan)

---

## 📄 License

This project is for academic / educational purposes.  
Dataset license: MIT (Hugging Face – millat/e-commerce-orders)

## 🏁 Conclusion

The integration of Python and Power BI proved effective for end-to-end data analysis — from raw, messy order-level data to a fully interactive, decision-ready dashboard report. Python handled cleaning, validation, enrichment, and EDA; Power BI delivered two consolidated, interactive dashboards with DAX-driven KPIs, slicers, and clearly labelled visuals — providing a strong, data-backed foundation for decisions on marketing spend, customer retention, and inventory planning.
