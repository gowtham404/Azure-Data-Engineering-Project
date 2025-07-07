# 🏗️ AdventureWorks Azure Data Engineering Project

This project simulates a full **end-to-end Azure Data Engineering pipeline** using the **AdventureWorks retail dataset**, showcasing ingestion from on-prem sources into a **modern Delta Lake architecture** on Azure.

The project follows a modular, layer-based data lake approach (Bronze → Silver → Gold) using Azure-native tools and frameworks like **Azure Data Factory**, **Azure Databricks**, **Delta Lake**, **Synapse**, and **Power BI** (optional extension).

---

## 🚀 Project Objectives

- Simulate real-world ETL workflows using public retail datasets
- Design a 3-layer Delta Lake architecture for scalable data processing
- Automate ingestion using ADF and config-driven logic
- Perform data transformation using PySpark and Databricks
- Create reporting-ready views in Synapse SQL or Spark SQL
- Showcase code modularity, reusability, and orchestration

---

## 🛠️ Tools & Technologies

| Layer            | Tool Used                     |
|------------------|-------------------------------|
| Ingestion        | Azure Data Factory (ADF)      |
| Storage          | Azure Data Lake Storage Gen2  |
| Processing       | Azure Databricks + PySpark    |
| Format           | Delta Lake                    |
| Modeling         | Bronze → Silver → Gold layers |
| Output Layer     | Synapse Analytics (SQL views) |
| Monitoring       | Git-based config + notebooks  |

---

## 🧩 Dataset

The project uses public **AdventureWorks** retail data including:

- Products, Categories, Subcategories
- Customers & Territories
- Sales data (2015–2017)
- Calendar information

---

## 📁 Project Structure

/Data/                            # Raw CSVs (Sales, Products, Customers, etc.)
/Config/git.json                  # Dynamic config for data ingestion logic
/silver_layer_refer.ipynb        # PySpark notebook for Silver layer transformations
/Create Views Gold.sql           # SQL views for curated Gold layer
/bronze_layer/                   # (Optional) Scripts for Bronze layer landing zone
/gold_layer/                     # Aggregated KPIs & analytical models

---

## 🔄 Pipeline Flow


graph TD
A[On-Prem SQL / CSVs] --> B[Azure Data Factory (ADF)]
B --> C[ADLS Gen2 - Bronze]
C --> D[Databricks PySpark - Silver]
D --> E[Databricks - Gold]
E --> F[Synapse Views / Power BI]

📊 Key Features
	•	Config-driven ingestion: git.json allows ADF to dynamically pull data from GitHub-hosted CSVs into target folders
	•	Modular Bronze/Silver/Gold architecture using Delta format
	•	Transformations include joins, casting, deduplication, and referential integrity checks
	•	Notebook-based development with reusable PySpark logic
	•	SQL view creation for business-ready data marts
	•	(Optional) Power BI dashboards can be layered over Synapse or Gold Delta tables

⸻

📌 How to Run
	1.	Clone this repo and upload data to your ADLS Gen2 container.
	2.	Deploy the git.json to configure ADF pipelines.
	3.	Run ADF to land Bronze data from CSVs.
	4.	Use silver_layer_refer.ipynb in Databricks to build the Silver layer.
	5.	Run SQL in Create Views Gold.sql to define final Gold-layer views.
	6.	(Optional) Connect Power BI to Synapse or Gold Delta tables for reporting.

⸻

📈 Output KPIs (Sample Ideas)
	•	Total Sales by Region, Category, Year
	•	YoY Growth by Subcategory
	•	High-Return Customers or Products
	•	Inventory Trends by Territory
