# 💻 Digital Health & Workplace Productivity | Power BI Analytics

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-2E7D32?style=for-the-badge)
![Power Query](https://img.shields.io/badge/Power_Query-107C41?style=for-the-badge&logo=microsoftexcel&logoColor=white)
![Data Analytics](https://img.shields.io/badge/Data_Analytics-003B57?style=for-the-badge)

## 📌 Project Overview

This project builds an interactive Business Intelligence solution designed to measure how hyperconnectivity and daily screen exposure impact employee stress levels, sleep recovery, and workplace productivity across **3,500 evaluated cases** (24 behavioral and demographic features).

Using **Power Query** and **Power BI (DAX)**, raw survey records were cleaned and modeled to isolate critical exposure thresholds and quantify the protective effect of physical activity against digital burnout.

## 🖼️ Dashboard Preview

![Dashboard Preview](dashboard_preview.png)

## 🛠️ Tech Stack & Architecture

- **Power Query (M):** Data cleaning, type standardization, cohort segmentation, and validation across 3,500 records.
- **Power BI Data Model:** Tabular analytical model optimized for dynamic slicing by role, region, age group, and daily device usage.
- **DAX Engine:** Custom risk flags, baseline comparisons, and executive KPIs centralized for interactive storytelling.

```text
[ Cleaned CSV (3,500 rows) ] ──► [ Power Query ETL ] ──► [ Power BI Tabular Model ] ──► [ DAX Executive Dashboard ]
```

## 📐 Core DAX Measures
Business logic and burnout risk KPIs were built directly into the 'Salud y Bienestar' reporting model:

- Total Evaluated Cases:
```dax
Total Evaluados = COUNTROWS('Salud y Bienestar')
```

- High-Risk Cases:
```dax
Casos Alto Riesgo = 
CALCULATE(
    COUNTROWS('Salud y Bienestar'),
    'Salud y Bienestar'[high_risk_flag] = 1
)
```

- High-Risk Population Percentage:
```dax
% Alto Riesgo = 
DIVIDE([Casos Alto Riesgo], [Total Evaluados], 0)
```

- Average Daily Screen Time (Hours):
```dax
Prom Horas Pantalla = AVERAGE('Salud y Bienestar'[device_hours_per_day])
```

## 💡 Key Business Insights
1. Critical Screen Exposure Threshold: Burnout risk probability escalates sharply above 10 hours of daily device usage, jumping from baseline rates under 15% to over 60% (reaching 100% in peak exposure ranges).
2. Sleep & Recovery Deficit: High-risk profiles average nearly 1 hour less sleep per night (6.5h vs. 7.4h) and score 21% lower in reported sleep quality.
3. The Exercise Buffer: Regular physical activity (5+ days/week) produces a measurable drop in baseline stress scores and stabilizes sleep quality above 2.8 / 4.0.

## 📁 Repository Structure
```text
├── DSH_Salud_Digital_Bienestar_v1.0.pbix
├── salud_digital_bienestar_raw.csv
├── dashboard_preview.png
└── README.md
```
