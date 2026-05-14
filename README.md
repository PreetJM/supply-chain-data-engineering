# End-to-End Supply Chain Data Engineering Pipeline

## 🚀 Project Overview
This project implements a modern data stack (MDS) to integrate and analyze supply chain data from three disparate sources: **ERP (Orders)**, **WMS (Warehouse)**, and **TMS (Logistics)**.

The pipeline automates the extraction of 180k+ records, transforms them into a **Star Schema** using dbt, and visualizes key performance indicators (KPIs) via a Metabase dashboard—all orchestrated by **Apache Airflow** within a **Docker** environment.

## 🏗️ Architecture
[Image of Data Engineering Pipeline Architecture]
The architecture follows the **Medallion Architecture** pattern:
1. **Raw Layer:** Python scripts ingest CSV data into a PostgreSQL 'Vault'.
2. **Staging Layer:** dbt cleans and casts data types.
3. **Intermediate Layer:** dbt joins the three business systems into a unified master table.
4. **Core Layer:** Final Star Schema consisting of Fact and Dimension tables.
5. **Analytics:** Metabase connects to the Core layer for business reporting.

## 🛠️ Tech Stack
- **Orchestration:** Apache Airflow
- **Transformation:** dbt (Data Build Tool)
- **Database:** PostgreSQL 15
- **Infrastucture:** Docker & Docker Compose
- **Language:** Python 3.13 (Pandas, SQLAlchemy)
- **Visualization:** Metabase

## 📊 Dashboard Insights
### 1. Financial Performance (ERP)
A breakdown of profits across product categories, identifying "Fishing" and "Cleats" as high-margin drivers.
[Insert your Donut Chart Screenshot here]

### 2. Logistics Efficiency (TMS)
Analysis of average delivery days per carrier to monitor shipping performance.
[Insert your Carrier Bar Chart Screenshot here]

### 3. Warehouse Volume (WMS)
Identification of high-volume departments (Fan Shop, Apparel) to optimize inventory placement.
[Insert your Sales Bar Chart Screenshot here]

## ⚙️ Setup Instructions
1. Clone the repository: `git clone https://github.com/yourusername/supply-chain-pipeline.git`
2. Place the `supply_chain_data.csv` in the `/data` folder.
3. Run the stack: `docker-compose up --build -d`
4. Access Airflow at `localhost:8080` to trigger the `supply_chain_automation` DAG.
5. Access Metabase at `localhost:3000` to view the dashboard.
