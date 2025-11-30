# 🌸 RetailOps ERP: Serverless Retail Intelligence Platform

![GCP](https://img.shields.io/badge/Google_Cloud-4285F4?style=for-the-badge&logo=google-cloud&logoColor=white)
![BigQuery](https://img.shields.io/badge/BigQuery-Data_Warehouse-4285F4?style=for-the-badge&logo=google-cloud&logoColor=white)
![Apps Script](https://img.shields.io/badge/Apps_Script-Frontend-4285F4?style=for-the-badge&logo=google&logoColor=white)
![Looker Studio](https://img.shields.io/badge/Looker-Visualization-4285F4?style=for-the-badge&logo=looker&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)

> **A full-stack ERP and Analytics ecosystem designed to modernize operations for a boutique retailer.**
> *Replaced legacy paper workflows with a Serverless Cloud Architecture.*

---

## 🏗️ Architecture

This project implements a **Modern Data Stack** using entirely serverless components on GCP. It features a custom "Time Machine" pricing engine (SCD Type 2) to accurately track historical revenue against changing inflation/markup rules.

```mermaid
graph LR
    User((Staff)) -->|Input/Search| WebApp["Custom Web App<br>(Apps Script + Tailwind)"]
    WebApp -->|JSON| Sheets[("Google Sheets<br>Operational DB")]
    
    subgraph "Google Cloud Platform (BigQuery)"
        Sheets -->|External Table| Staging["Staging Layer<br>(Raw Data)"]
        Staging -->|Scheduled Query| Prod["Production Layer<br>(Cleaned Fact Tables)"]
        Prod -->|SQL Views| Semantic["Semantic Layer<br>(Business Logic)"]
    end
    
    Semantic -->|Viz| Looker["Looker Studio<br>Dashboard"]
    
    style WebApp fill:#e6fffa,stroke:#38b2ac,stroke-width:2px
    style Prod fill:#ebf8ff,stroke:#4285f4,stroke-width:2px
    style Looker fill:#fff5f5,stroke:#f56565,stroke-width:2px
