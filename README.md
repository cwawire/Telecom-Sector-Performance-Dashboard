# 📡 Telecom Sector Performance Dashboard (Power BI)

![Power BI](https://img.shields.io/badge/Tool-Power%20BI-F2C811?style=for-the-badge\&logo=powerbi\&logoColor=black)
![DAX](https://img.shields.io/badge/Language-DAX-0176D3?style=for-the-badge)
![Analytics](https://img.shields.io/badge/Domain-Telecom%20Analytics-0EA5E9?style=for-the-badge)
![Status](https://img.shields.io/badge/Project-Completed-22C55E?style=for-the-badge)

---

##  Project Summary

This project is an executive-level Power BI dashboard designed to analyze and monitor telecom sector performance across:

* 📞 Traffic Analytics
* 📱 Mobile Market Performance
* 🌐 Broadband & Connectivity
* 🔐 Cybersecurity Threat Intelligence
* 📊 KPI Growth & Trend Analysis

The solution combines:

* advanced DAX modeling
* executive dashboard storytelling
* KPI normalization/indexing
* telecom operational analytics
* performance optimization techniques

into a recruiter-ready BI portfolio project.

---

## 🖼️ Dashboard Pages

## Overview

This project is an end-to-end Power BI dashboard designed to analyze and monitor key performance indicators (KPIs) across the telecommunications sector. The solution consolidates telecom operational, broadband, mobile market, traffic analytics, and cybersecurity performance metrics into a unified executive reporting experience.

The dashboard was built with a strong focus on:

* Executive storytelling
* KPI-driven analysis
* Clean visual hierarchy
* Telecom-specific analytical framing
* Performance optimization
* Professional dashboard design standards

The final solution contains multiple analytical report pages covering:

1. Executive Overview
2. Mobile Market Analysis
3. Traffic Analytics
4. Broadband & Connectivity Performance
5. Cybersecurity Threat Intelligence

---

# Project Objectives

The primary objective of this dashboard was to:

* Consolidate telecom sector KPIs into a single analytical platform
* Track quarterly telecom performance trends
* Compare KPI growth across business segments
* Monitor infrastructure and connectivity metrics
* Analyze subscriber and smartphone adoption trends
* Evaluate cybersecurity threat activity and advisory metrics
* Build a recruiter-ready BI portfolio project demonstrating:

  * Power BI dashboard design
  * DAX modeling
  * KPI storytelling
  * Executive visualization practices
  * Analytical problem-solving

---

# Dashboard Architecture

## Executive Overview

The Executive Overview page provides a high-level telecom sector summary.

### Core KPIs

* Total KPI Value
* Voice Traffic
* SMS Traffic
* Subscribers
* Broadband Growth
* QoQ Growth
* Mobile Money Growth

### Key Visuals

* Quarterly KPI Growth Comparison
* Indexed Telecom KPI Growth Trends
* Executive Insight Narrative

### Analytical Purpose

This page answers:

* Which telecom segments are growing the fastest?
* How are key KPIs evolving over time?
* Which categories dominate sector performance?

---

## Mobile Market Analysis

This page focuses on smartphone adoption and device market performance.

### Core KPIs

* Smartphone Value
* Smartphone Penetration %
* Smartphone Growth %

### Key Visuals

* Device Market Composition (Donut Chart)
* Quarterly Device Market Comparison
* Total Device Subscription Trend
* Smartphone Adoption Over Time

### Analytical Purpose

This page evaluates:

* Smartphone penetration growth
* Device market composition
* Subscriber adoption trends
* Smartphone vs feature phone market performance

---

## Traffic Analytics

This page focuses on telecom traffic distribution and traffic growth analysis.

### Core KPIs

* Voice Traffic
* SMS Traffic
* Roaming
* International Traffic

### Key Visuals

* Voice Traffic Growth Trend
* Traffic Share by Type
* QoQ Growth Comparison by KPI Category
* Indexed Traffic Growth Trends

### Analytical Purpose

This page helps analyze:

* Telecom traffic composition
* Growth across traffic categories
* Roaming performance
* International traffic patterns
* On-net vs off-net trends

---

## Broadband & Connectivity Performance

This page evaluates broadband infrastructure and utilization metrics.

### Core KPIs

* Broadband Subscribers
* Utilized Bandwidth
* Available Bandwidth
* QoQ Growth

### Key Visuals

* International Infrastructure Capacity
* Broadband Adoption Trend
* Bandwidth Utilization & Satellite Capacity

### Analytical Purpose

This section analyzes:

* Broadband adoption growth
* Network capacity utilization
* Undersea bandwidth infrastructure
* Satellite dependency trends
* International bandwidth availability

---

## Cybersecurity Threat Intelligence

This page focuses on cyber threat detection and advisory activity.

### Core KPIs

* Cyberthreat Cost

### Key Visuals

* Cyber Threat vs Advisory Distribution
* Cyber Threat Activity Comparison
* Cyber Threat Trend Over Time
* Cybersecurity KPI Table

### Analytical Purpose

This page evaluates:

* Threat detection trends
* Threat advisory activity
* Quarterly cybersecurity growth
* Threat intensity comparisons

---

# Data Preparation Process

## Data Cleaning

Several telecom datasets contained:

* Missing values
* Sparse quarterly reporting
* Inconsistent naming conventions
* Mixed KPI categories
* Operational duplicates

The following cleaning processes were performed:

### Standardization

* Standardized KPI category names
* Renamed inconsistent metrics
* Created cleaned metric fields

Example:

```DAX
Metric_Clean =
TRIM(Fact_TelecomKPIs[Metric])
```

---

## Date Table Creation

A custom Date Table was created to support:

* Quarterly analysis
* Year-quarter sorting
* Time intelligence calculations

### Key Date Fields

* Date
* Year
* Quarter
* Year Quarter
* YearQuarterSort

Example:

```DAX
Year Quarter =
FORMAT(DateTable[Date], "YYYY") & " Q" & FORMAT(DateTable[Date], "Q")
```

---

## Sorting Logic

To ensure proper quarter sequencing:

```DAX
YearQuarterSort =
YEAR(DateTable[Date]) * 10 + QUARTER(DateTable[Date])
```

This solved issues where Power BI sorted quarters alphabetically instead of chronologically.

---

# DAX Measures Created

## Total KPI Value

```DAX
Total KPI Value =
SUM(Fact_TelecomKPIs[Current_Value])
```

---

## Previous Quarter Value

```DAX
Previous Quarter Value =
SUM(Fact_TelecomKPIs[Previous_Quarter])
```

---

## QoQ Growth %

```DAX
QoQ Growth % =
DIVIDE(
    [Total KPI Value] - [Previous Quarter Value],
    [Previous Quarter Value]
)
```

---

## Indexed KPI Value

The indexed KPI measure normalized telecom KPI performance over time.

### Purpose

The indexed metric allows:

* Relative trend comparison
* Growth normalization
* Momentum analysis across categories

### Final Indexed Measure

```DAX
Indexed KPI Value =
VAR BaseQuarter =
    CALCULATE(
        MIN(DateTable[YearQuarterSort]),
        ALLSELECTED(DateTable)
    )

VAR BaseValue =
    CALCULATE(
        [Total KPI Value],
        FILTER(
            ALL(DateTable),
            DateTable[YearQuarterSort] = BaseQuarter
        )
    )

RETURN
DIVIDE([Total KPI Value], BaseValue) * 100
```

---

# Dashboard Design Process

## Initial Design Challenges

The initial dashboard versions suffered from:

* Overcrowded visuals
* Poor visual hierarchy
* Excessive tables
* Weak KPI storytelling
* Inconsistent chart selection
* Poor trend readability

The dashboard was redesigned iteratively using executive BI design principles.

---

# Visual Design Decisions

## 1. Replacing Tables with Comparative Charts

### Problem

Tables consumed large dashboard space and reduced readability.

### Solution

Replaced operational tables with:

* QoQ Growth Comparison charts
* Horizontal KPI comparison visuals

### Result

Improved:

* Executive readability
* KPI storytelling
* Visual hierarchy
* Dashboard professionalism

---

## 2. Horizontal Bar Charts for QoQ Comparison

### Problem

Vertical QoQ charts looked cramped and difficult to scan.

### Solution

Used horizontal clustered bar charts.

### Benefits

* Better ranking visibility
* Faster executive scanning
* Improved comparison readability

---

## 3. Sparse Data Visualization Challenges

### Problem

Metrics like:

* Undersea Bandwidth
* Satellite Bandwidth

had sparse quarterly values.

Using line charts created misleading continuity.

### Solution

Switched sparse metrics from:

* Line charts

To:

* Clustered column charts

### Result

The dashboard more accurately represented:

* discrete reporting periods
* infrastructure deployment changes
* irregular telecom capacity reporting

---

## 4. Indexed Trend Visuals

### Problem

Direct KPI comparisons were difficult because KPI scales varied significantly.

Example:

* Voice Traffic values were much larger than Mobile Money values.

### Solution

Created indexed KPI measures normalized to a base quarter.

### Result

This enabled:

* relative performance analysis
* trend normalization
* cross-category momentum comparison

---

## 5. Small Multiples Optimization

### Problem

Too many small multiples caused:

* cramped layouts
* weak readability
* visual fragmentation

### Solution

Reduced small multiple complexity and grouped related KPIs strategically.

### Result

Cleaner trend interpretation and stronger layout balance.

---

# Dashboard Performance Challenges

## 1. Report Slowdowns

### Problem

Performance degraded due to:

* too many card visuals
* layered KPI cards
* complex DAX calculations
* excessive small multiples

### Solution

Optimizations included:

* reducing visual count
* removing redundant cards
* simplifying KPI structures
* limiting expensive DAX calculations
* disabling unnecessary interactions

### Result

Improved:

* dashboard responsiveness
* filtering speed
* visual rendering performance

---

## 2. New Card Visual Issues

### Problem

The new Power BI Card visual caused:

* rendering delays
* stuck visual behavior
* limited formatting flexibility

### Solution

Reverted to simpler KPI card structures and removed unnecessary layered visuals.

### Key Lesson

Executive dashboards should prioritize:

* speed
* clarity
* responsiveness

over excessive visual complexity.

---

# Null and Sparse Data Handling

## Challenge

Several visuals displayed:

* false zero values
* misleading flat trends
* disconnected growth patterns

### Example

Missing broadband values appeared as:

```text
0 bandwidth
```

instead of missing data.

---

## Solution

Implemented:

* null filtering
* blank handling
* selective quarter filtering

Example logic:

```DAX
IF(
    ISBLANK([Total KPI Value]),
    BLANK(),
    [Total KPI Value]
)
```

---

# Color Palette & Design System

The dashboard uses a consistent telecom-inspired executive color palette.

## Core Colors

| Purpose           | Color   |
| ----------------- | ------- |
| Page Background   | #556E7F |
| Visual Containers | #243447 |
| KPI Cards         | #E5E7EB |
| Primary Accent    | #22D3EE |
| Secondary Accent  | #60A5FA |
| SMS Metrics       | #FACC15 |
| Positive Growth   | #22C55E |
| Negative Growth   | #EF4444 |
| Cybersecurity     | #8B5CF6 |
| Mobile Money      | #14B8A6 |

---

# Executive Design Principles Applied

The dashboard design intentionally followed executive BI design standards:

## 1. Visual Hierarchy

Each page follows:

```text
Title
→ Filters
→ KPI Cards
→ Executive Insight
→ Main Analytical Visuals
```

---

## 2. Minimal Visual Clutter

Avoided:

* excessive tables
* unnecessary gauges
* overloaded KPI cards
* decorative visuals

---

## 3. Strategic Chart Selection

Different visual types were matched to data behavior:

| Data Type                  | Visual Used           |
| -------------------------- | --------------------- |
| Sparse Infrastructure Data | Column Charts         |
| Continuous Adoption Trends | Line/Area Charts      |
| KPI Comparisons            | Horizontal Bar Charts |
| Market Composition         | Donut Charts          |
| Relative Momentum          | Indexed Trend Charts  |

---

# Key Lessons Learned

## 1. Simplicity Improves Executive Readability

Reducing clutter significantly improved:

* dashboard clarity
* storytelling quality
* analytical focus

---

## 2. Chart Selection Matters

Using incorrect chart types can create misleading interpretations.

Example:

* sparse telecom infrastructure metrics should not use continuous line charts.

---

## 3. Performance Is Part of Dashboard Quality

Fast dashboards provide a better user experience than overloaded dashboards.

Optimization became a critical part of the final solution.

---

## 4. Indexed KPIs Improve Comparative Analysis

Indexing telecom KPIs allowed:

* fair trend comparison
* normalized growth evaluation
* better executive insight generation

---

# Tools & Technologies Used

## Power BI

Primary dashboarding and visualization platform.

## DAX

Used for:

* KPI calculations
* growth metrics
* indexed trend logic
* dynamic formatting

## Power Query

Used for:

* data cleaning
* transformation
* preprocessing

---

# Potential Future Improvements

Future enhancements could include:

* Forecasting models
* Real-time telecom streaming data
* Geographic telecom coverage maps
* Drill-through analytics pages
* AI-generated telecom insights
* Predictive anomaly detection
* Automated cybersecurity alerts

---

# Repository Structure

```text
telecom-sector-dashboard/
│
├── datasets/
├── screenshots/
├── pbix/
├── dax-measures/
├── assets/
├── README.md
└── telecom_dashboard.pbix
```

---

# Screenshots

## Executive Overview

* KPI growth comparison
* Indexed KPI trends
* Executive telecom insights

## Mobile Market Analysis

* Smartphone penetration analysis
* Device market composition
* Adoption trends

## Traffic Analytics

* Traffic growth analysis
* Traffic composition
* Roaming and international traffic insights

## Broadband & Connectivity

* Infrastructure capacity
* Broadband adoption
* Utilization monitoring

## Cybersecurity Intelligence

* Threat detection analysis
* Cyber advisory tracking
* Threat trend monitoring

---

# Business Impact

This dashboard demonstrates how telecom operators and regulators can:

* monitor sector performance
* evaluate broadband growth
* track cybersecurity activity
* analyze telecom traffic behavior
* monitor infrastructure utilization
* compare KPI momentum across business segments

---

# Recruiter Notes

This project demonstrates practical skills in:

* Power BI dashboard development
* Executive dashboard design
* DAX modeling
* KPI normalization
* Data storytelling
* Telecom analytics
* Data visualization strategy
* Performance optimization
* Analytical problem-solving

The dashboard was intentionally designed to mirror:

* enterprise BI reporting standards
* executive telecom reporting structures
* operational KPI monitoring systems

---

# Author

Clyde Wawire

Data Analyst | Business Intelligence | Telecom Analytics | Power BI

LinkedIn: https://www.linkedin.com/in/clyde-wawire/
GitHub: https://github.com/cwawire
