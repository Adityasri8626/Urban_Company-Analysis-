
# Urban Company Data Analytics Project 📊

This project analyzes service data from **Urban Company** using SQL, Power BI, and Excel to extract actionable insights and business strategies. The focus was on understanding service demand, cost structure, and performance across cities and subservices.

---

## 📁 Dataset Summary

The dataset contains service-level data with fields such as:

- `city_name`
- `service_type`
- `subservice_name`
- `total_charge`
- `labour_charge`
- `material_charge`
- `labour_to_total_pct`

---

## 🧼 Data Cleaning

Cleaning and formatting steps were performed in **Excel** and **Python**:
- Removed nulls, duplicates
- Converted currency strings to numeric
- Calculated `labour_to_total_pct` = `(labour_charge / total_charge) * 100`
- Standardized column naming conventions

---

## 🧠 Business Problem Statement

Urban Company wants to:
- Identify which services and cities generate the most revenue
- Improve cost efficiency (especially labour-heavy services)
- Strategically expand in high-potential markets
- Optimize technician allocation and service pricing

---

## 🔍 SQL Analysis & Business Insights

All queries were executed in **BigQuery** (can run in any SQL engine). Below are the questions answered:

### 1️⃣ Highest Avg. Total Service Charge by City
```sql
SELECT city_name, ROUND(AVG(total_charge), 0) AS avg_total_charge
FROM urban_data
GROUP BY city_name
ORDER BY avg_total_charge DESC;
```
**Insight:** Lucknow tops with ₹1062 average service charge — potential for premium service expansion.

---

### 2️⃣ Top 10 Subservices by Total Revenue
```sql
SELECT subservice_name, SUM(total_charge) AS total_revenue
FROM urban_data
GROUP BY subservice_name
ORDER BY total_revenue DESC
LIMIT 10;
```
**Insight:** *Compressor 2 ton* repair leads with ₹3.95 Lakhs — high priority for promotion and technician specialization.

---

### 3️⃣ Service Types with Highest Labour % Cost
```sql
SELECT service_type, ROUND(AVG(labour_to_total_pct), 1) AS avg_labour_pct
FROM urban_data
GROUP BY service_type
ORDER BY avg_labour_pct DESC;
```
**Insight:** *Microwave repairs* have the highest labour share (38.4%) — improve training or automation.

---

### 4️⃣ Count of Labour-Heavy Services
```sql
SELECT COUNT(*) AS labour_heavy_services
FROM urban_data
WHERE labour_charge > material_charge;
```
**Insight:** 638 services are labour-heavy — opportunity to control cost via better technician workflows.

---

### 5️⃣ City-wise Total Revenue
```sql
SELECT city_name, SUM(total_charge) AS total_city_revenue
FROM urban_data
GROUP BY city_name
ORDER BY total_city_revenue DESC;
```
**Insight:** *Hyderabad, Chennai, and Pune* are top revenue cities (each over ₹1.7 Lakhs) — ideal for regional expansion.

---

## 📈 Power BI Dashboard

An interactive Power BI dashboard was built with:

- **KPIs:** Total Revenue, Avg. Charge, Labour-Heavy Service Count
- **Bar Charts:** Revenue by City, Top Subservices
- **Pie Charts:** Labour vs Material Dominant Services
- **Slicers:** City, Service Type, Labour %, Revenue Range
- **Line Chart:** Trend of total revenue (if date added)

🎯 **Power BI Storytelling:** Incorporated tooltips, dynamic filters, and data storytelling bookmarks.

---

## 📊 Key Insights & Recommendations

✅ **Focus on Top Services**
- Promote high-ticket services like Compressor 2 ton
- Upskill technicians for premium jobs

✅ **Leverage Premium Cities**
- Lucknow has highest avg charge — introduce premium plans

✅ **Expand High-Revenue Cities**
- Invest marketing and resources in Hyderabad, Pune, Chennai

✅ **Improve Technician Efficiency**
- 638 services are labour-heavy — optimize processes

✅ **Tiered Pricing Strategy**
- Create Basic–Standard–Premium models for better monetization

---

## 🧰 Tools Used

| Tool        | Purpose                          |
|-------------|----------------------------------|
| Excel       | Initial cleaning, formatting     |
| SQL (BigQuery) | Core analysis and insights     |
| Power BI    | Dashboard building and storytelling |
| Python (Optional) | Data formatting, cleaning helper |

---

## 📦 Repository Contents

- `urban_company_cleaned.xlsx` – Cleaned dataset
- `urban_insights.sql` – All SQL queries
- `dashboard.pbix` – Power BI dashboard file
- `README.md` – Project documentation

---

## 🔮 Future Scope

- Add customer satisfaction trends via `rating`
- Predict service demand with ML (Python)
- Build real-time dashboards in Power BI Service

---

## 👤 Author

**Aditya Srivastava**  
[GitHub](https://github.com/Adityasri8626) | [LinkedIn](https://www.linkedin.com/in/adityasrivastava26)
