# Analyzing Industry Carbon Emissions | SQL
This project aims to analyze carbon emissions across various industries using publicly available datasets. The goal is to identify trends, high-emission sectors, and potential areas for improvement using statistical methods and data visualization to view reporting.
## 📊 Dataset Overview

The dataset includes:
- Product-level carbon footprint (PCF)
- Company and industry group info

## 🛠️ Tools Used
- SQL
- PostgreSQL
- GitHub

## 🔍 Key Query
```sql
SELECT industry_group,
       COUNT(DISTINCT company) AS num_companies,
       ROUND(SUM(carbon_footprint_pcf), 1) AS total_industry_footprint
FROM product_emissions
WHERE year = (SELECT MAX(year) FROM product_emissions)
GROUP BY industry_group
ORDER BY total_industry_footprint DESC;
