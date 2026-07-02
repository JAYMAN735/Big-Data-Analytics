# Experiment 7: Sales Analysis – Top Products Using Hadoop Streaming

## Overview

This project demonstrates how to perform **city-wise product sales analysis** using **Hadoop Streaming** and **Python MapReduce**. The application processes sales records stored in HDFS, aggregates product sales for each city, and identifies the **top-selling product** in every city using custom Mapper and Reducer scripts.

---

# Course Information

* **Course:** Big Data Analytics
* **Course Code:** Z1AMC 702

---

# Objective

Analyze sales data using Hadoop MapReduce and determine the highest-selling product for each city by aggregating total product sales.

---

# Project Workflow

1. Prepare custom Python Mapper and Reducer scripts.
2. Upload the sales dataset to HDFS.
3. Execute the Hadoop Streaming job.
4. Aggregate sales for each city-product pair.
5. Identify the top-selling product in every city.
6. Display the final results.

---

# Dataset Format

Each sales record contains:

```text id="s7a1"
Date,Product,Price,City
```

### Example

```text id="s7a2"
2024-01-01,Laptop,65000,Mumbai
2024-01-02,Mouse,1200,Delhi
2024-01-03,Keyboard,2500,Bangalore
```

---

# Technologies Used

* Apache Hadoop
* Hadoop Streaming
* Python 3
* HDFS
* Linux Shell

---

# Project Structure

```text id="s7a3"
Sales-Analysis-Top-Products/
│
├── sales_products_large.txt
├── mapper_city_products.py
├── reducer_city_products.py
└── README.md
```

---

# Hadoop Commands

## Create Input Directory

```bash id="s7a4"
hdfs dfs -mkdir -p /user/$USER/sales_products/input
```

## Upload Dataset

```bash id="s7a5"
hdfs dfs -put sales_products_large.txt /user/$USER/sales_products/input/
```

## Remove Previous Output (Optional)

```bash id="s7a6"
hdfs dfs -rm -r -skipTrash /user/$USER/sales_products/city_output
```

## Run Hadoop Streaming Job

```bash id="s7a7"
hadoop jar $HADOOP_HOME/share/hadoop/tools/lib/hadoop-streaming-*.jar \
-files mapper_city_products.py,reducer_city_products.py \
-input /user/$USER/sales_products/input/sales_products_large.txt \
-output /user/$USER/sales_products/city_output \
-mapper "python3 mapper_city_products.py" \
-reducer "python3 reducer_city_products.py"
```

## View Output

```bash id="s7a8"
hdfs dfs -cat /user/$USER/sales_products/city_output/part-00000
```

---

# MapReduce Logic

## Mapper

* Reads each sales record.
* Extracts **City**, **Product**, and **Price**.
* Emits a composite key in the format:

```text id="s7a9"
City_Product    Price
```

## Reducer

* Groups records by the composite key.
* Calculates total sales for each product within a city.
* Compares product totals.
* Outputs the highest-selling product for every city.

---

# Expected Output

The output displays the top-selling product for each city, for example:

```text id="s7a10"
TOP PRODUCT PER CITY:
========================================
Mumbai: Laptop (₹1,250,000.00)
Delhi: Keyboard (₹875,000.00)
Bangalore: Monitor (₹920,000.00)
```

---

# Learning Outcomes

After completing this experiment, you will be able to:

* Develop custom Python Mapper and Reducer programs.
* Use composite keys in Hadoop MapReduce.
* Perform grouping and aggregation using distributed processing.
* Analyze city-wise product sales efficiently.
* Apply Hadoop Streaming to solve real-world analytics problems.

---

# Prerequisites

* Java JDK
* Apache Hadoop
* Hadoop Streaming
* Python 3
* Linux/Ubuntu Environment
* HDFS configured and running

---

# Applications

This project demonstrates a practical use case applicable to:

* E-commerce analytics
* Retail sales analysis
* Product performance tracking
* Regional sales reporting
* Business intelligence dashboards

---

# Conclusion

This experiment demonstrates how Hadoop Streaming can be used with Python to perform city-wise product sales analysis. By using composite keys and distributed aggregation, the MapReduce application efficiently identifies the top-selling product in each city, providing valuable insights for business decision-making and large-scale sales analytics.

