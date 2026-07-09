# Apache Cassandra on Ubuntu WSL using Docker

## 📌 Overview

This project demonstrates how to install and configure **Apache Cassandra** on **Ubuntu WSL** using **Docker**. It covers creating a Cassandra keyspace, creating tables, inserting sample data, and executing CQL (Cassandra Query Language) queries.

The experiment is designed to help beginners understand the basics of working with Cassandra in a Dockerized environment.

---

## 🎯 Objective

- Install Apache Cassandra on Ubuntu WSL
- Configure Cassandra using Docker Compose
- Create a Cassandra keyspace
- Create database tables
- Insert sample records
- Execute CQL queries
- Verify successful data retrieval

---

## 🛠 Technologies Used

- Ubuntu WSL
- Docker
- Docker Compose
- Apache Cassandra
- Cassandra Query Language (CQL)

---

## 📁 Project Structure

```
cassandra-exercise/
│
├── docker-compose.yml
├── cassandra-data/
└── README.md
```

---

## ⚙ Prerequisites

Before running this project, ensure you have:

- Windows Subsystem for Linux (WSL)
- Ubuntu installed on WSL
- Docker installed
- Docker Compose installed

---

## 🚀 Installation Steps

### 1. Create Project Directory

```bash
mkdir -p ~/cassandra-exercise
cd ~/cassandra-exercise
```

### 2. Create Docker Compose File

Create a file named:

```
docker-compose.yml
```

Add the Cassandra service configuration.

### 3. Start Cassandra

```bash
docker compose up -d
```

### 4. Verify Container

```bash
docker ps
```

### 5. Connect to Cassandra

```bash
docker exec -it cassandra cqlsh
```

---

## 🗄 Create Keyspace

```sql
CREATE KEYSPACE sparkify
WITH REPLICATION = {
'class':'SimpleStrategy',
'replication_factor':1
};
```

Use the keyspace:

```sql
USE sparkify;
```

---

## 📋 Create Table

```sql
CREATE TABLE song_info_by_session (
    session_id INT,
    item_in_session INT,
    artist TEXT,
    song TEXT,
    length DECIMAL,
    PRIMARY KEY (session_id, item_in_session)
);
```

---

## 📥 Insert Sample Data

```sql
INSERT INTO song_info_by_session
(session_id,item_in_session,artist,song,length)
VALUES
(100,1,'The Beatles','Hey Jude',7.11);

INSERT INTO song_info_by_session
(session_id,item_in_session,artist,song,length)
VALUES
(100,2,'Led Zeppelin','Stairway to Heaven',8.02);
```

---

## 🔍 Retrieve Data

```sql
SELECT * FROM song_info_by_session
WHERE session_id = 100;
```

---

## 📊 Expected Output

```
 session_id | item_in_session | artist         | song                  | length
------------+-----------------+----------------+-----------------------+--------
100         | 1               | The Beatles    | Hey Jude              | 7.11
100         | 2               | Led Zeppelin   | Stairway to Heaven    | 8.02
```

---

## 📚 Learning Outcomes

After completing this project, you will understand:

- Apache Cassandra architecture
- Docker-based deployment
- Keyspaces and tables
- CQL commands
- Data insertion and retrieval
- Working with distributed NoSQL databases

---

## ✅ Conclusion

This project successfully demonstrates the installation and configuration of Apache Cassandra on Ubuntu WSL using Docker. It provides a hands-on introduction to Cassandra's data model by creating keyspaces, tables, inserting records, and executing queries for efficient data retrieval.

---

## 👨‍💻 Author

**Jayman Prajapati**

Master's in Data Science

