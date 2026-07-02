# Hadoop Experiments (Experiment 1, 2 & 3)

## Overview

This repository contains three introductory Hadoop experiments completed as part of the **Big Data Analytics** course. The experiments cover Hadoop installation, basic HDFS commands, and the implementation of the Hadoop MapReduce WordCount program.

---

## Course Information

* **Course:** Big Data Analytics
* **Course Code:** Z1AMC 702

---

# Experiment 1: Hadoop Single Node Installation

## Objective

Install and configure Hadoop in a single-node environment and verify the successful execution of HDFS and YARN services.

## Procedure

* Install Java Development Kit (JDK).
* Download and extract Hadoop.
* Configure environment variables.
* Configure the following Hadoop configuration files:

  * `core-site.xml`
  * `hdfs-site.xml`
  * `mapred-site.xml`
  * `yarn-site.xml`
* Format the NameNode.
* Start HDFS services.
* Start YARN services.
* Verify running services using `jps`.
* Access Hadoop web interfaces.

## Commands Used

```bash
export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
export HADOOP_HOME=/usr/local/hadoop
export PATH=$PATH:$HADOOP_HOME/bin:$HADOOP_HOME/sbin

hdfs namenode -format
start-dfs.sh
start-yarn.sh
jps
```

## Expected Result

* Hadoop starts successfully.
* NameNode and ResourceManager are accessible.
* HDFS and YARN services are running correctly.

---

# Experiment 2: Hadoop Basic Commands

## Objective

Learn and execute basic Hadoop Distributed File System (HDFS) commands for file and directory management.

## Commands

### Create Directory

```bash
hdfs dfs -mkdir /demo
```

### Upload File

```bash
hdfs dfs -put sample.txt /demo
```

### List Files

```bash
hdfs dfs -ls /demo
```

### View File

```bash
hdfs dfs -cat /demo/sample.txt
```

### Download File

```bash
hdfs dfs -get /demo/sample.txt
```

### Delete File

```bash
hdfs dfs -rm /demo/sample.txt
```

### Delete Directory

```bash
hdfs dfs -rmdir /demo
```

## Expected Result

Successfully create, upload, view, download, and delete files and directories in HDFS.

---

# Experiment 3: Hadoop MapReduce WordCount

## Objective

Perform word frequency analysis on a text file using Hadoop's MapReduce WordCount example.

## Procedure

1. Create an input text file.
2. Upload the file to HDFS.
3. Execute the WordCount MapReduce job.
4. View the generated output.
5. Analyze the word frequencies.

## Commands

### Create Input File

```bash
echo "Big Data is the future of analytics" > sample.txt
```

### Create Input Directory

```bash
hdfs dfs -mkdir /input
```

### Upload File

```bash
hdfs dfs -put sample.txt /input
```

### Run WordCount

```bash
hadoop jar $HADOOP_HOME/share/hadoop/mapreduce/hadoop-mapreduce-examples-*.jar wordcount /input /output
```

### View Output

```bash
hdfs dfs -cat /output/part-r-00000
```

## Expected Result

The output displays the frequency of each word in the input file, demonstrating Hadoop's distributed processing capability.

---

# Prerequisites

* Java JDK 11 or later
* Apache Hadoop
* Ubuntu/Linux environment
* Terminal access
* HDFS configured correctly

---

# Learning Outcomes

After completing these experiments, you will be able to:

* Install and configure Hadoop in standalone/single-node mode.
* Work with HDFS commands.
* Understand Hadoop architecture.
* Execute MapReduce programs.
* Analyze distributed processing results using WordCount.

---

# Repository Structure

```
Hadoop-Experiments/
│
├── Experiment-1/
│   ├── Hadoop Installation
│   └── Configuration Files
│
├── Experiment-2/
│   └── HDFS Basic Commands
│
├── Experiment-3/
│   └── WordCount MapReduce
│
└── README.md
```

---

# Conclusion

These experiments provide a foundation in Apache Hadoop by covering installation, HDFS operations, and the execution of a basic MapReduce application. Together, they demonstrate the core concepts required to begin working with distributed storage and data processing in Hadoop.

