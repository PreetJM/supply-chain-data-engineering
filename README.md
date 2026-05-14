# End-to-End Supply Chain Data Engineering Pipeline

## 🚀 Project Overview
This project implements a modern data stack (MDS) to integrate and analyze supply chain data from three disparate sources: **ERP (Orders)**, **WMS (Warehouse)**, and **TMS (Logistics)**.

The pipeline automates the extraction of 180k+ records, transforms them into a **Star Schema** using dbt, and visualizes key performance indicators (KPIs) via a Metabase dashboard—all orchestrated by **Apache Airflow** within a **Docker** environment.

## 🏗️ Architecture
```mermaid
graph TD
    subgraph Source_Layer
        CSV[(Supply Chain CSV)]
    end

    subgraph Ingestion_Layer
        Python[Python Ingestion Script]
    end

    subgraph Infrastructure
        Docker[Docker Container City]
        Airflow[Airflow Orchestrator]
    end

    subgraph Storage_Warehouse
        PG[(PostgreSQL Vault)]
        subgraph dbt_Transformation
            STG[Staging View]
            INT[Intermediate Join]
            CORE[Star Schema: Fact & Dims]
        end
    end

    subgraph Analytics_Layer
        Metabase[Metabase BI Dashboard]
    end

    CSV --> Python
    Python --> PG
    Airflow --> Python
    Airflow --> dbt_Transformation
    PG --> STG
    STG --> INT
    INT --> CORE
    CORE --> Metabase
