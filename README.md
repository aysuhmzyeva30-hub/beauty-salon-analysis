# Beauty Salon Performance Dashboard 📊

An end-to-end Power BI business intelligence solution designed to track, analyze, and optimize the operational and financial performance of a beauty salon.

> ⚠️ **Data Confidentiality Notice:** The data source and the Power BI `.pbix` file are kept private to protect customer privacy and business confidentiality. All metrics, visuals, and methodologies are demonstrated below.

---

## 🎯 Project Objective
The main goal of this dashboard is to help salon stakeholders monitor daily revenue, track stylist (staff) performance, and identify peak hours/popular services to improve operational efficiency.

## 🛠️ Tech Stack & Skills Used
* **Power BI Desktop** - Data modeling & Visualization
* **Power Query** - ETL (Extract, Transform, Load) processes & Data cleaning
* **DAX (Data Analysis Expressions)** - Calculated columns and measures for custom KPIs

## 🖼️ Dashboard Preview

Here is a look at the interactive pages of the Power BI dashboard:

### Page 1: Stylist Performance Analysis (Usta Performansı Analizi)
This page focuses on individual stylist performance, analyzing which team members contribute most to salon sales, service delivery, and customer interactions.
![Dashboard Page 1](image.png)

### Page 2: Time & Trend Analysis (Zaman və Trend Analizi)
This page provides in-depth insights into financial trends over time, tracking monthly net profit, revenue vs. expenses, weekly performance, and a drill-down decomposition of net profit.
![Dashboard Page 2](dashboard_page2.png)

## 📈 Analytical Logic & DAX Formulas

Since the database contains separate cash inflow and outflow logs, custom measures and a dynamic calendar table were developed to build a relational data model and perform time-series analysis.

### 1. Key Business Metrics (Measures)

* **Ümumi Mədaxil (Total Revenue):**
  Calculates the total revenue generated from salon services.
  ```dax
  Umumi_medaxil = SUM('Kassa mədaxil'[Qazanc, AZN])
* **Ümumi Xərc (Total Expenses):**
  Calculates the total operational expenses of the salon.
   ```dax
  Umumi_xerc = SUM('Kassa xərclər'[Xərc, AZN])
* **Təmiz Mənfəət (Net Profit):**
  Calculates the net profit by subtracting total expenses from total revenue.
    ```dax
    Temiz_menfeet = [Umumi_medaxil] - [Umumi_xerc]
### 2.Dynamic Calendar Table (Time Intelligence)
 To enable advanced date filtering (slicers) and trend analysis across different tables, a custom Təqvim (Calendar) table was created using DAX:
 ```dax

 Teqvim = 
VAR MinDate = MIN('Kassa mədaxil'[Tarix])
VAR MaxDate = MAX('Kassa mədaxil'[Tarix])
RETURN
ADDCOLUMNS (
    CALENDAR (MinDate, MaxDate),
    "İl", YEAR([Date]),
    "Ay", FORMAT([Date], "MMMM"),
    "Ay Nömrəsi", MONTH([Date]),
    "Həftənin Günü", FORMAT([Date], "dddd")
)
```
## 🚀 Roadmap & Next Steps (Feedback Integration)

* **I am continuously improving this project. The upcoming updates will include:**

* **UI/UX Refinement: Redesigning color palettes and layouts for better readability and a more polished look based on stakeholder feedback.**

* **Performance Optimization: Optimizing complex DAX measures to reduce visual loading times.**

* **Advanced Analytics: Introducing customer retention and repeat-visit frequency analysis.**
