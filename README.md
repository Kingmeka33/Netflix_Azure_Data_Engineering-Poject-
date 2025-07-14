# ✈️ Cloud Data Engineering Pipeline with Databricks + DBT

## 📌 Project Overview

This project presents a full-scale, real-world **cloud data engineering solution** simulating an airline booking system. Built on **Databricks** and integrated with **DBT**, it follows the **Lakehouse architecture** using the **Medallion design pattern** (Bronze, Silver, Gold layers).

Key objectives:
- Design modular, scalable pipelines for ingestion, transformation, and business modeling.
- Demonstrate advanced **data engineering patterns** such as **incremental ingestion**, **SCD Type 1 management**, **CDC (Change Data Capture)**, and **star schema construction**.
- Build a **production-grade orchestration and transformation workflow** integrating Spark Structured Streaming, Delta Lake, and DBT.

---

## 🛠️ Tech Stack

| Technology               | Purpose                                                                 |
|--------------------------|-------------------------------------------------------------------------|
| **Databricks**           | Cloud compute platform for data engineering workloads                   |
| **Apache Spark**         | Distributed data processing engine                                      |
| **Structured Streaming** | Real-time data ingestion and transformation                             |
| **Delta Lake**           | ACID-compliant storage layer enabling versioning and upserts            |
| **Lakeflow (Delta Live Tables)** | Declarative pipeline framework for Silver layer transformations     |
| **Databricks Autoloader**| Scalable, schema-evolving file ingestion engine                         |
| **DBT Cloud**            | SQL-first modular transformation and DAG modeling                       |
| **Python**               | Parameterized logic for dynamic notebook generation                     |
| **SQL**                  | Business rule implementation and transformation                         |

---

## 🔁 Architecture: Medallion Data Flow
[ CSV Files ] --> [ Bronze Layer (Raw) ]
--> [ Silver Layer (Cleaned & Modeled) ]
--> [ Gold Layer (Dimensional Models & Fact Tables) ]

### 🔸 Bronze Layer
- Ingests raw flight booking data from CSV files using **Databricks Autoloader**
- Uses **Spark Structured Streaming** for incremental ingestion with **checkpointing** and **schema evolution**
- Supports dynamic ingestion logic with notebook parameterization

### 🔹 Silver Layer
- Implements **Lakeflow Declarative Pipelines (formerly Delta Live Tables)**
- Transforms data: casting types, filtering records, creating streaming tables
- Enforces **data quality expectations** such as not null constraints

### 🟡 Gold Layer
- Builds **star schema models** with **fact and dimension tables**
- Creates a **dynamic SCD Type 1 builder** for handling slowly changing dimensions:
  - Detects inserts vs updates using primary keys and `modify_date`
  - Assigns surrogate keys automatically
- Builds dynamic **fact table logic** by joining multiple dimensions
- Uses **Delta Lake merge + Auto CDC API** to ensure correct versioning and historical accuracy

---

## 🔄 Workflow Orchestration

- Uses **Databricks Workflows** to manage pipeline scheduling and dependencies
- Implements **control flow with loops and parameter widgets**
- Allows dynamic ingestion of any table or folder through reusable notebook templates

---

## 🔗 DBT Integration

- **Connected DBT Cloud to Databricks SQL Warehouse**
- Created **DBT models** for business rules and transformations on Gold layer data
- Built **DAGs**, added documentation, and managed version-controlled SQL workflows
- Enables data analysts to work independently in a clean SQL environment

---

## 📂 Sample Dataset Description

| File Name        | Description                              |
|------------------|------------------------------------------|
| `flights.csv`     | Flight-level transactional fact table     |
| `passengers.csv`  | Passenger-level dimension table           |
| `bookings.csv`    | Booking transactions with foreign keys    |
| `airports.csv`    | Airport metadata for enrichment           |

These datasets were processed in streaming and batch modes with **backdated records** to simulate CDC and upsert logic.

---

## 📈 Features & Highlights

### ✅ Incremental Ingestion with Autoloader
- Exactly-once delivery via **checkpointing**
- Schema evolution support
- Fast ingestion of large volumes of files

### 🔄 Dynamic SCD Type 1 Builder
- Fully reusable logic via parameterized notebooks
- Assigns surrogate keys
- Updates only changed records based on `modify_date`

### 🧠 CDC and Upsert Handling
- **Delta Merge logic** supports backfilled records
- Ensures no duplicate or out-of-order updates using **Auto CDC API**

### 🔧 Pipeline Parameterization
- Parameterized folder/table names using widgets
- Reduces hardcoding and enables **multi-domain reuse**

### 💎 SQL-Based Transformations with DBT
- Modular business layer modeling
- Data lineage visualization with **DBT DAGs**
- Full version control and documentation of logic

---

## 🧪 Real-World Challenges Addressed

- Managing schema evolution and late-arriving records
- Implementing **dimensional modeling** at scale
- Handling data quality constraints in streaming pipelines
- Designing **maintainable, production-level workflows**
- Enforcing **referential integrity** between facts and dimensions

---

## 📊 Screenshots

> (Add images here: Databricks pipelines, notebook outputs, DBT DAGs, and schema diagrams.)

---

## 🧭 How to Run (Coming Soon)

A complete step-by-step guide to:
- Setup a free Databricks workspace
- Upload raw CSV datasets to Volumes
- Configure and run Bronze → Silver → Gold pipelines
- Connect DBT Cloud and run SQL models

---

## 💼 Outcomes

By completing this project, I’ve gained mastery in:

- Cloud data pipeline design (Databricks + DBT)
- Real-time streaming ingestion with Autoloader
- Building reusable, parameterized pipelines
- Orchestration with Workflows and control flow logic
- SQL-first modular modeling with DBT
- Debugging, optimization, and production-level deployment strategies



