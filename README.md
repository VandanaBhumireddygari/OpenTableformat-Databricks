## Project Overview
This project explores Open Table Formats using Databricks, PySpark, and Delta Lake. It covers data ingestion, transformation, storage optimization, and querying techniques.


---

## 📝 **Concepts Covered**
- ✅ Open Table Formats (Apache Iceberg, Delta Lake, Hudi)
- ✅ Working with Databricks & Spark Clusters
- ✅ Data ingestion into Databricks using **PySpark**
- ✅ **Delta Lake:** Data storage, ACID transactions, and performance optimizations
- ✅ **Delta Log:** Understanding transaction logs and metadata
- ✅ **Time Travel in Delta Lake:** Restoring previous versions of data
- ✅ **Schema Evolution & Changes**
- ✅ **DML Operations (MERGE, UPDATE, DELETE) in Delta Lake**
- ✅ **Spark Optimization Techniques** for efficient queries
- ✅ **Deletion Vectors & Structured Streaming** in Databricks

---

## 💻 **Python Scripts**
All relevant scripts used for ingestion, transformation, and querying Delta tables can be found in the `scripts/` directory.

📂 **Attached Python File:**

## Prerequisites
- Databricks account with a running cluster.
- Apache Spark installed.
- Access to a cloud storage or local file system for storing datasets.
- Jupyter Notebook or an IDE with PySpark support.



## Steps to Run

### 1. Load Data
```python
 df = spark.read.format("csv") \
     .option("header", True) \
     .option("inferSchema", True) \
     .load("/FileStore/tables/sales_data_first.csv")
 df.show()
```

### 2. Write Data to Delta Table
```python
 df.write.format("delta") \
    .mode("overwrite") \
    .option("path", "/FileStore/tables/sinkdata/sales_data_first_delta") \
    .save()
```

### 3. Query the Delta Table
```sql
SELECT * FROM delta.`/FileStore/tables/sinkdata/sales_data_first_delta`;
```

### 4. Time Travel (Versioning)
```sql
SELECT * FROM delta.`/FileStore/tables/sinkdata/sales_data_first_delta` VERSION AS OF 2;
```

### 5. VACUUM to Remove Old Versions
```sql
VACUUM delta.`/FileStore/tables/sinkdata/sales_data_first_delta` RETAIN 0 HOURS;
```

## Files Included
- **Open Table format.ipynb**: Jupyter Notebook with all code and explanations.
- **logs/scheduler/**: Log files from execution.
- **Python Scripts**: Attached Python files used in this project.

## Summary
This project demonstrates the use of Open Table Formats in Databricks with Delta Lake, covering ingestion, transformations, storage management, and querying techniques.

