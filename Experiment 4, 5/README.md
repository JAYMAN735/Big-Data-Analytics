# Hadoop Experiments 4 & 5

##  Overview

## This repository contains two Hadoop experiments completed as part of the **Big Data Analytics** course. These experiments demonstrate advanced Hadoop concepts, including processing multiple files using the built-in MapReduce **WordCount** program and implementing **custom MapReduce** applications using **Hadoop Streaming** with Python.

#  Course Information

* **Course:** Big Data Analytics
* **Course Code:** Z1AMC 702

---

# Experiment 4: Word Count of Multiple Files Using Hadoop MapReduce

## Objective

Perform a Word Count operation on multiple text files stored in HDFS using the Hadoop MapReduce framework and display the frequency of each word.

## Procedure

1. Create multiple input text files.
2. Verify the files.
3. Create an input directory in HDFS.
4. Upload all files to HDFS.
5. Execute the Hadoop WordCount MapReduce program.
6. View the generated output.

## Commands Used

### Verify Input Files

```bash id="r4f1"
ls -la file*.txt
```

### Create HDFS Directory

```bash id="r4f2"
hdfs dfs -mkdir -p /jayman/hadoop_file/input
```

### Upload Files

```bash id="r4f3"
hdfs dfs -put *.txt /jayman/hadoop_file/input/
```

### Run WordCount

```bash id="r4f4"
hadoop jar $HADOOP_HOME/share/hadoop/mapreduce/hadoop-mapreduce-examples-*.jar wordcount /jayman/hadoop_file/input /jayman/hadoop_file/output
```

### Display Output

```bash id="r4f5"
hdfs dfs -cat /jayman/hadoop_file/output/part-r-00000
```

## Expected Output

The output file contains each unique word along with its frequency across all input files.

---

# Experiment 5: Custom MapReduce Using Hadoop Streaming

## Objective

Analyze a large sales dataset (50,000 records) using custom Python Mapper and Reducer scripts with Hadoop Streaming to demonstrate the MapReduce paradigm and extract meaningful business insights.

## Features

* Generate a realistic sales dataset
* Create custom Python Mapper
* Create custom Python Reducer
* Execute Hadoop Streaming jobs
* Analyze city-wise sales
* Perform monthly sales analysis
* Evaluate product performance
* Visualize results

---

## Workflow

1. Generate a dataset containing 50,000 sales records.
2. Write a Python Mapper to calculate sales by city.
3. Write a Python Reducer to aggregate city-wise sales.
4. Test Mapper and Reducer locally.
5. Upload the dataset to HDFS.
6. Execute Hadoop Streaming.
7. Analyze the generated output.
8. Perform additional monthly and product-wise analysis.

---

## Dataset Fields

Each record contains:

* Date
* Product
* Price
* City
* Customer ID
* Quantity

---

## Technologies Used

* Apache Hadoop
* Hadoop Streaming
* Python 3
* HDFS
* Linux Shell

---

## Hadoop Commands

### Create Input Directory

```bash id="r5f1"
hdfs dfs -mkdir -p /user/$USER/sales/input
```

### Upload Dataset

```bash id="r5f2"
hdfs dfs -put sales_data.csv /user/$USER/sales/input/
```

### Verify Upload

```bash id="r5f3"
hdfs dfs -ls /user/$USER/sales/input/
```

### Local Testing

```bash id="r5f4"
head -20 sales_data.csv | python3 mapper_city_sales.py | sort | python3 reducer_city_sales.py
```

---

## Project Structure

```text
Hadoop-Streaming/
│
├── generate_sales.py
├── mapper_city_sales.py
├── reducer_city_sales.py
├── sales_data.csv
├── input/
├── output/
└── README.md
```

---

## Business Insights Generated

The Hadoop Streaming application provides insights such as:

* Highest sales city
* Monthly sales trends
* Product performance
* Average transaction value
* City-wise sales comparison

---

## Learning Outcomes

After completing these experiments, you will be able to:

* Execute Hadoop MapReduce on multiple input files.
* Understand how Hadoop processes data in parallel.
* Develop custom Mapper and Reducer programs using Python.
* Execute Hadoop Streaming jobs.
* Analyze large datasets using distributed processing.
* Extract meaningful business insights from big data.

---

## Prerequisites

* Java JDK
* Apache Hadoop
* Python 3
* Hadoop Streaming
* Linux/Ubuntu Environment
* HDFS configured and running

---

# Conclusion

These experiments extend the understanding of Hadoop beyond the basic WordCount example by introducing multi-file processing and custom MapReduce development using Hadoop Streaming. The experiments demonstrate how Python can be integrated with Hadoop to process large datasets efficiently and generate valuable analytical insights from distributed data processing.

