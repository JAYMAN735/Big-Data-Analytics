# Experiment 6: Weather Data Analysis Using Hadoop Streaming

## Overview

This project demonstrates how to analyze weather temperature data using **Hadoop Streaming** and **Python MapReduce**. The objective is to process weather records stored in HDFS and identify the **hottest** and **coldest** days using custom Mapper and Reducer scripts.

---

# Course Information

* **Course:** Big Data Analytics
* **Course Code:** Z1AMC 702

---

# Objective

Analyze weather temperature data using Hadoop Streaming and Python MapReduce to determine the hottest and coldest days from a weather dataset.

---

# Project Workflow

1. Create a weather dataset.
2. Expand the dataset for large-scale processing.
3. Create a Python Mapper to extract maximum temperatures.
4. Create a Reducer to identify the hottest day.
5. Execute the Hadoop Streaming job.
6. Create another Reducer to identify the coldest day.
7. Analyze the generated output.

---

# Dataset Format

Each record in the dataset follows the format:

```text id="w1"
Date,City,Maximum_Temperature,Minimum_Temperature
```

### Example

```text id="w2"
2024-01-01,Delhi,12,5
2024-01-04,Mumbai,28,20
2024-01-08,Chennai,32,25
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

```text id="w3"
Weather-Temperature-Analysis/
│
├── weather_data.txt
├── weather_large.txt
├── mapper_max_temp.py
├── reducer_max_temp.py
├── reducer_min_temp.py
└── README.md
```

---

# Hadoop Commands

## Create HDFS Input Directory

```bash id="w4"
hdfs dfs -mkdir -p /user/$USER/weather/input
```

## Upload Dataset

```bash id="w5"
hdfs dfs -put weather_large.txt /user/$USER/weather/input/
```

---

# Run Hadoop Streaming (Hottest Day)

```bash id="w6"
hadoop jar $HADOOP_HOME/share/hadoop/tools/lib/hadoop-streaming-*.jar \
-input /user/$USER/weather/input/weather_large.txt \
-output /user/$USER/weather/output \
-mapper "python3 mapper_max_temp.py" \
-reducer "python3 reducer_max_temp.py" \
-file mapper_max_temp.py \
-file reducer_max_temp.py
```

---

# View Output

```bash id="w7"
hdfs dfs -cat /user/$USER/weather/output/part-00000
```

---

# Run Hadoop Streaming (Coldest Day)

```bash id="w8"
hadoop jar $HADOOP_HOME/share/hadoop/tools/lib/hadoop-streaming-*.jar \
-input /user/$USER/weather/input/weather_large.txt \
-output /user/$USER/weather/output_min \
-mapper "python3 mapper_max_temp.py" \
-reducer "python3 reducer_min_temp.py" \
-file mapper_max_temp.py \
-file reducer_min_temp.py
```

---

# View Coldest Day Output

```bash id="w9"
hdfs dfs -cat /user/$USER/weather/output_min/part-00000
```

---

# Expected Results

The application identifies:

* Hottest day in the dataset
* Coldest day in the dataset
* Maximum temperature recorded
* Minimum temperature recorded

---

# Learning Outcomes

After completing this experiment, you will be able to:

* Understand the Hadoop Streaming framework.
* Develop custom Python Mapper and Reducer programs.
* Process weather datasets using distributed computing.
* Execute Hadoop Streaming jobs on HDFS.
* Analyze temperature data efficiently using MapReduce.

---

# Prerequisites

* Java JDK
* Apache Hadoop
* Python 3
* Hadoop Streaming
* Linux/Ubuntu Environment
* HDFS configured and running

---

# Conclusion

This experiment demonstrates how Hadoop Streaming integrates Python with the Hadoop ecosystem to perform distributed weather data analysis. By implementing custom Mapper and Reducer scripts, the project efficiently identifies the hottest and coldest days from a large weather dataset, showcasing the effectiveness of the MapReduce programming model for large-scale data processing.

