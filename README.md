
# IMDB_GROUP_PROJ 🎬  
### TEAM 10 MID TERM PROJECT  

## 📌 Project Overview
This project involves building a complete Data Engineering Pipeline for IMDb datasets using Azure Data Factory (ADF), Snowflake, and Power BI. The goal is to design an end-to-end architecture that extracts raw IMDb data, transforms it into a dimensional model, and presents insights through business intelligence dashboards.

---

## 📂 Project Repository Structure
```
IMDB_GROUP_PROJ/
│
├── dataflow/              # Dataflow definitions in ADF for transformations
├── dataset/               # Dataset references in ADF for each TSV file
├── factory/               # ADF Factory configuration
├── linkedService/         # Connections to Blob Storage & Snowflake
├── pipeline/              # Pipelines for ingestion and loading into Snowflake
├── publish_config.json    # ADF ARM template publish configuration
└── README.md              # Project documentation
```

---

## 🔗 Data Source  
IMDb public datasets (TSV format, UTF-8, gzip compressed) obtained from:  
[IMDb Datasets](https://www.imdb.com/interfaces/)

### Files used:
- title.akas.tsv.gz
- title.basics.tsv.gz
- title.crew.tsv.gz
- title.episode.tsv.gz
- title.principals.tsv.gz
- title.ratings.tsv.gz
- name.basics.tsv.gz

---

## 🛠️ Process Workflow  

1. **Ingestion Phase (Bronze Layer)**  
   - Upload raw gzipped IMDb TSV files to Azure Blob Storage.
   - Create corresponding datasets in ADF referencing Blob Storage paths.

2. **Data Cleaning & Transformation (Silver Layer)**  
   - Create ADF Data Flows to handle:
     - Null handling (`\N` → NULL/standard formats)
     - UTF-8 encoding issues
     - Column structure validation
     - Trimming whitespaces
     - Splitting multi-valued columns (e.g., genres, professions)
     - Mapping surrogate keys where required

3. **Dimensional Modeling (Gold Layer)**  
   - Design star-schema using ER Studio.
   - Create Bridge and Fact tables (e.g., Bridge_Title_Genre, Fact_Title_Ratings)
   - Load cleaned data into Snowflake dimensional model using ADF pipelines.

4. **Linked Services Setup**
   - Connection between ADF ↔ Azure Blob ↔ Snowflake configured via ADF Linked Services.

5. **Orchestration**
   - ADF Pipelines execute in order: Raw → Cleaned → Modeled → Snowflake.

6. **Visualization & Insights**
   - Power BI dashboards built on top of Snowflake models:
     - Crime genre trends
     - Ratings analysis by title types
     - Director and cast insights

---

## 📊 Tools & Technologies
- Azure Data Factory (ADF)
- Azure Blob Storage
- Snowflake
- Power BI
- Alteryx (Profiling/Cleansing)
- ER Studio (Data Modeling)

---

## ✅ Outcomes & Key Takeaways
- Successfully implemented Medallion Architecture.
- Designed a reusable ADF pipeline for any similar structured TSV datasets.
- Enhanced proficiency in end-to-end cloud-based ETL processing.
- Produced actionable insights using Power BI dashboards.

---

## 👨‍💻 Contributors
- Ganesh Paparaju
- Priyanka Satish Kumar
- Akash Malhotra

---

## 📬 Contact  
For any queries or collaborations, reach out via GitHub or LinkedIn.
