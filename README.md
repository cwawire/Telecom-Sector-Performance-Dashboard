# 📡 Kenya Telecom Sector Performance Dashboard

A multi-page Power BI dashboard analyzing Kenya’s telecommunications and ICT sector performance using official quarterly industry statistics published by the Communications Authority of Kenya (CA).

The project transforms raw telecom sector reports into an executive-level business intelligence solution covering:
- Mobile market growth
- Broadband adoption
- Telecom traffic analytics
- Cybersecurity trends
- Mobile money performance
- Infrastructure utilization

---

# 📌 Project Overview

Kenya is one of Africa’s most digitally advanced economies, with telecommunications infrastructure playing a central role in:
- Financial inclusion
- Internet accessibility
- Mobile banking
- Digital commerce
- Business communication
- National cybersecurity

This dashboard was built to analyze how Kenya’s ICT ecosystem evolved across multiple reporting periods using real-world sector statistics from the Communications Authority of Kenya.

The project focuses on converting dense regulatory reports into:
- Executive-friendly insights
- Interactive visual analytics
- Growth monitoring dashboards
- KPI-driven business intelligence

---

# 🎯 Project Objectives

The dashboard was designed to:

- Monitor telecom sector performance across reporting periods
- Track broadband and mobile adoption trends
- Analyze voice, SMS, and roaming traffic
- Visualize cybersecurity threat activity
- Compare quarterly KPI growth
- Build executive-level telecom intelligence visuals
- Demonstrate advanced Power BI and DAX capabilities

---

# 🗂 Dashboard Structure

## 1. Executive Overview
Provides a high-level summary of:
- Total telecom KPI performance
- QoQ growth comparisons
- Indexed KPI growth trends
- Broadband and mobile money growth indicators
- Telecom sector insights

### Key Insights
- Cybersecurity indicators recorded the strongest growth momentum
- Broadband metrics rebounded steadily after Q4 slowdown
- Voice traffic remained the dominant telecom KPI

---

## 2. Mobile Market Analysis
Analyzes:
- Smartphone adoption
- Device market composition
- Smartphone penetration rates
- Quarterly mobile market comparisons
- Device subscription growth trends

### Key Findings
- Smartphone subscriptions continued rising significantly
- Feature phones still maintain substantial market share
- Mobile penetration continues expanding across Kenya

---

## 3. Telecom Traffic Analytics
Tracks:
- Voice traffic trends
- SMS traffic performance
- Roaming activity
- International traffic patterns
- QoQ telecom traffic growth

### Key Findings
- Voice traffic remains dominant
- Roaming traffic showed strong growth
- International traffic experienced mixed performance

---

## 4. Broadband & Connectivity Performance
Monitors:
- Broadband adoption
- Utilized vs available bandwidth
- Undersea bandwidth trends
- Satellite bandwidth utilization
- Connectivity infrastructure growth

### Key Findings
- Broadband adoption continued increasing steadily
- Infrastructure utilization improved significantly
- Kenya’s international bandwidth capacity continues expanding

---

## 5. Cybersecurity Threat Intelligence
Analyzes:
- Cyber threat detections
- Threat advisories
- Threat growth comparisons
- Cybersecurity trend patterns

### Key Findings
- Cyber threat detections increased sharply
- Advisory activity also showed strong growth
- Growing digital adoption increases cybersecurity relevance

---

# 📊 Data Source

The dashboard uses official quarterly ICT sector statistics reports from the Communications Authority of Kenya.

## Reports Used
- Q1 FY2024/25 Sector Statistics Report
- Q2 FY2024/25 Sector Statistics Report
- Q3 FY2024/25 Sector Statistics Report
- Q4 FY2024/25 Sector Statistics Report
- Q1 FY2025/26 Sector Statistics Report
- Q2 FY2025/26 Sector Statistics Report

The reports follow International Telecommunications Union (ITU) standards for ICT and telecommunications statistics reporting.

---

# 🇰🇪 Why This Project Matters for Kenya

## 1. Mobile Money Leadership
Kenya is globally recognized for mobile financial services adoption.

The dashboard tracks mobile money subscription growth from:
- **40.6M subscribers**
to
- **51.3M subscribers**

This reflects the importance of:
- M-Pesa
- Airtel Money
- Digital payments
- Financial inclusion

---

## 2. Smartphone Growth & Digital Adoption
The project visualizes Kenya’s rapid transition toward smartphone usage.

Smartphone subscriptions increased from:
- **37.4M**
to
- **48.7M** across the reporting period.

This growth influences:
- Internet accessibility
- E-commerce
- Social media adoption
- Online learning
- Digital entrepreneurship

---

## 3. Broadband Infrastructure Expansion
The dashboard highlights Kenya’s investment in:
- Fibre infrastructure
- Broadband access
- Undersea cable systems
- International bandwidth

The reports reference infrastructure systems including:
- SEACOM
- TEAMS
- EASSy
- PEACE Cable

---

## 4. Telecom Usage Trends
Voice and SMS traffic analysis reveals evolving communication behavior across Kenya.

For example:
- On-net voice traffic increased from **22.2bn minutes** to **26.2bn minutes** across the reporting period.

The dashboard helps visualize:
- Consumer communication trends
- Telecom demand patterns
- Traffic growth behavior

---

## 5. Cybersecurity Relevance
As Kenya’s digital economy expands, cybersecurity monitoring becomes increasingly important.

The dashboard tracks:
- Threat detections
- Advisory trends
- Threat growth indicators

This reflects growing focus on:
- Digital infrastructure protection
- Fraud prevention
- Enterprise cybersecurity readiness

---

# 🛠 Tools & Technologies Used

| Tool | Purpose |
|---|---|
| Power BI | Dashboard development & visualization |
| Power Query | Data cleaning & transformation |
| DAX | KPI calculations & advanced measures |
| Excel / CSV | Intermediate data preparation |
| CA Sector Reports | Primary data source |

---

# 📈 Key DAX Measures Created

## Total KPI Value
```DAX
Total KPI Value =
SUM(Fact_TelecomKPIs[Current_Value])
```

## QoQ Growth %
```DAX
QoQ Growth % =
DIVIDE(
    [Total KPI Value] - [Previous Quarter Value],
    [Previous Quarter Value]
)
```

## Indexed KPI Trend
```DAX
Indexed KPI Value =
VAR BaseValue =
    CALCULATE(
        [Total KPI Value],
        FILTER(
            ALLSELECTED('DateTable'),
            'DateTable'[YearQuarterSort]
                =
            MIN('DateTable'[YearQuarterSort])
        ),
        ALLEXCEPT(
            Fact_TelecomKPIs,
            Fact_TelecomKPIs[KPI_Category]
        )
    )

RETURN
DIVIDE([Total KPI Value], BaseValue) * 100
```

---

# 🚧 Challenges Encountered & Solutions

## 1. Blank Indexed KPI Charts
### Problem
Indexed KPI trend visuals initially returned blank charts.

### Cause
Incorrect date context handling and missing quarter sorting logic.

### Solution
- Built a dedicated Date Table
- Added `YearQuarterSort`
- Refactored DAX context using:
  - `ALLSELECTED()`
  - `ALLEXCEPT()`
  - Base-period indexing logic

---

## 2. Sparse Broadband Infrastructure Data
### Problem
Undersea and satellite bandwidth data had limited reporting periods.

### Solution
Replaced line charts with column charts for sparse datasets to improve readability and avoid misleading visual trends.

---

## 3. Power BI Performance Issues
### Problem
The new Power BI card visual significantly slowed dashboard performance.

### Solution
- Replaced heavy visuals with standard KPI cards
- Reduced unnecessary interactions
- Simplified visuals
- Optimized DAX calculations

---

## 4. Visual Consistency Across Pages
### Problem
Maintaining consistent styling across multiple telecom report pages.

### Solution
Implemented:
- Shared color palette
- Consistent KPI card structure
- Uniform typography
- Reusable visual layouts

---

# 🎨 Dashboard Design Features

## Theme
- Dark executive dashboard theme
- Telecom-inspired blue/cyan palette
- Consistent typography & spacing

## Interactive Features
- Financial year slicers
- Quarter filters
- KPI category filtering
- Cross-visual interactions

## Visualization Types
- KPI cards
- Line charts
- Area charts
- Donut charts
- Clustered column charts
- QoQ comparison bars
- Indexed trend visuals

---

# 📚 Skills Demonstrated

This project demonstrates practical experience in:
- Business Intelligence
- Data Visualization
- Power BI Development
- DAX Calculations
- Data Modeling
- KPI Reporting
- Dashboard Storytelling
- Telecom Sector Analytics
- Data Transformation
- Executive Reporting

---

# 💼 Business Value

The dashboard can support:
- Telecom strategy analysis
- ICT performance monitoring
- Digital economy reporting
- Infrastructure planning
- Market trend analysis
- Executive decision-making

---

# 📸 Dashboard Preview

## Executive Overview
- Sector-wide KPI trends
- QoQ telecom growth comparisons
- Indexed KPI performance tracking

## Mobile Market Analysis
- Smartphone adoption trends
- Device composition insights

## Traffic Analytics
- Voice & SMS traffic analysis
- Roaming performance tracking

## Broadband & Connectivity
- Broadband adoption monitoring
- Infrastructure utilization tracking

## Cybersecurity Intelligence
- Threat activity monitoring
- Advisory growth tracking

---

# 🚀 Future Improvements

Potential future enhancements include:
- Real-time telecom API integration
- Geographic telecom coverage mapping
- Forecasting & predictive analytics
- Network operator benchmarking
- Drill-through analysis pages
- Advanced cybersecurity anomaly detection

---

# 👤 Author

**Clyde Wawire**  
Data Analytics | Business Intelligence | Financial & Strategy Analysis

This project was developed as part of a portfolio focused on:
- Business intelligence
- Data storytelling
- Sector analytics
- Executive dashboard reporting
- Real-world analytics projects
