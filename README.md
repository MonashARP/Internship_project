# EH Dashboard Analytics Project  
**DigitXL Internship (Monash University – 2025)**  

This repository contains all materials developed during my three-month internship with **DigitXL**, a Melbourne-based analytics consultancy.  
The project was completed for **EH** — a luxury wellness and retreat brand — with the goal of **building a reproducible analytics pipeline and interactive Looker Studio dashboard** to track and improve digital marketing performance.

---

## Project Overview

The core focus of this internship was to design an **integrated analytics ecosystem** that connects *Google Analytics 4 (GA4)* website data with *internal lead and sales records*, creating a unified view of EH’s marketing funnel.  

Using **R**, **Google Sheets**, and **Looker Studio**, this project established a fully automated framework that:
- Cleans and standardises marketing and sales data weekly  
- Blends GA4 event metrics with lead performance indicators  
- Generates reproducible reports and dashboards for actionable business insights  

The result is a **scalable and transparent reporting system** that DigitXL can adapt for other clients as a reusable dashboard template.

---

##  Problem Statement

EH’s marketing and CRM data were **fragmented across multiple sources**:  
- GA4 captured on-site behaviour (*page views*, *Book Now clicks*, *engagement metrics*).  
- Internal spreadsheets tracked leads, quotes, invoices, and payments.  

Because these datasets were disconnected, it was impossible to answer questions like:  
> *Which marketing channels actually bring qualified leads?*  
> *Where in the booking funnel do users drop off?*  
> *How efficient is the lead-to-payment process week by week?*

This project solved that by **centralising and connecting these data sources**, enabling EH to visualise the complete journey from awareness → conversion → payment.

---

## Objectives

1. **Define measurable KPIs** across GA4 and internal systems (e.g., Lead-to-Quote %, Hold-to-Paid %, Engagement Rate).  
2. **Fix the fragmented data journey** by mapping user drop-offs using GA4 events and Looker Studio funnels.  
3. **Build an automated Looker Studio dashboard** that updates weekly via structured Google Sheets.  
4. **Enable reproducibility** through R-based data cleaning, tidy formatting, and Quarto reporting.

---

## Methodology

### 1. Data Collection  
- GA4 data was exported via **Explorations → CSV**, capturing key user and event metrics (*Sessions*, *Users*, *Book Now clicks*, *Engagement Rate*).  
- Internal **Lead and Sales data** were collected weekly from the client’s CRM.  

### 2. Data Cleaning and Transformation (R)
- Used `tidyverse`, `lubridate`, and `janitor` to convert wide weekly data into **long/tidy format**:  

```
Week Start | Channel | Metric | Value
```

- Created consistent **Week Range** fields for joining with GA4 data.  
- Validated totals, handled duplicates, and ensured proper numeric types.  

### 3. Data Integration
- Processed Google Sheets were connected to **Looker Studio** via blending on *Week Start* and *Week Range*.  
- GA4 and CRM data were unified into one dataset — enabling direct performance comparisons.  

### 4. Dashboard Development (Looker Studio)
- Built KPI scorecards (*Total Leads*, *Conversion %*, *Book Now clicks*).  
- Created trend charts, channel performance tables, and funnel visualisations.  
- Added week-range dropdown filters for time-based analysis.  
- Used calculated fields for derived metrics like:  

```
Qualified Leads % = Qualified Leads / Total Leads
Engagement Efficiency = Sessions / Active Users
```

### 5. Automated Reporting
- All insights are consolidated in a **Quarto-generated PDF report** (`report/report.qmd`), ensuring reproducibility and version control.

---

## Key Outcomes

**Data Reproducibility:**  
Raw spreadsheets can be reprocessed automatically using R scripts (`scripts/01_clean_leads_sales.R`) — eliminating manual cleaning.  

**Integrated Dashboard:**  
A fully functional Looker Studio dashboard visualises weekly performance trends, campaign efficiency, and booking funnel drop-offs.  

**Actionable Insights:**  
The dashboard identified major conversion friction between *Retreat Page → Booking Page* and informed A/B testing for CTA placement and copy improvements.  

**Reusable Framework:**  
The data pipeline and dashboard template can be replicated for other DigitXL clients, forming the foundation of a **scalable BI framework**.

---

## Reproducibility Steps

Anyone can reproduce the pipeline using the following:

### 1. Clone and open the project
```
git clone https://github.com/MonashARP/Internship_project.git
cd Internship_project
```

### 2. Open in RStudio and restore dependencies
```
install.packages("renv")
renv::restore()
```

### 3. Add data
- Place raw client files in `data/raw/` (not tracked for confidentiality).  
- Optionally use the synthetic samples provided.

### 4. Run the processing pipeline
```
source("scripts/01_clean_leads_sales.R")
```

### 5. Render the report
```
source("scripts/03_render_report.R")
```

### 6. Open Looker Studio
- Connect the processed Google Sheet (`data/processed/leads_sales_long.csv`).  
- Blend with GA4 data using *Week Start* or *Week Range*.  
- Import visuals from the Looker dashboard template included in `/docs`.

---

## Tools & Technologies

| Category | Tools Used |
|-----------|------------|
| Data Cleaning & Analysis | **R**, `tidyverse`, `lubridate`, `janitor` |
| Data Visualisation | **Google Looker Studio** |
| Data Source | **Google Analytics 4 (GA4)** |
| Reporting | **Quarto (report.qmd → PDF)** |
| Version Control | **Git + GitHub** |
| Reproducibility | **renv** for R package management |

---

## How This Helps the Client

Through this project, **EH** now has:
- A **clear, data-driven view** of its lead-to-revenue funnel.  
- A dashboard that surfaces **marketing ROI**, **channel effectiveness**, and **conversion drop-offs** in real time.  
- A **reusable analytics framework** that DigitXL can customise for other clients.  
- Evidence-based insights supporting **A/B testing**, **UX redesigns**, and **targeted marketing campaigns**.

---

## Citation

If you reference or build upon this work, please cite:  
> Dhrafani, D. (2025). *EH Dashboard Analytics Report — A Reproducible Framework for GA4 and Looker Studio Integration.* DigitXL Internship, Monash University.  
> GitHub Repository: [https://github.com/MonashARP/Internship_project](https://github.com/MonashARP/Internship_project)

---

## License

This project is released under the **MIT License**, allowing reuse and modification with attribution.  
See the [LICENSE](LICENSE) file for details.
