# Sparkify Music Streaming Database using Apache Cassandra

## 📌 Overview

This project demonstrates how to design a **query-driven data model** in **Apache Cassandra** for a music streaming application called **Sparkify**. The database is optimized for specific queries by creating separate tables instead of relying on joins, following Cassandra's best practices.

The project includes creating a keyspace, designing query-specific tables, inserting sample data, and executing CQL queries to retrieve music streaming information efficiently. :contentReference[oaicite:0]{index=0}

---

## 🎯 Objectives

- Design a query-based data model in Apache Cassandra
- Create a Sparkify keyspace
- Create optimized tables for different query patterns
- Insert sample music streaming data
- Execute CQL queries for efficient data retrieval
- Understand Cassandra's query-driven database design

---

## 🛠 Technologies Used

- Apache Cassandra
- Cassandra Query Language (CQL)
- Docker
- Ubuntu WSL
- Docker Compose

---

## 📂 Database Schema

The project contains **three query-specific tables**:

### 1. Song Information by Session

Stores songs played during a particular session.

**Primary Key**

```
(session_id, item_in_session)
```

---

### 2. Song Playing History by User

Stores songs played by a specific user during a session.

**Primary Key**

```
((user_id, session_id), item_in_session)
```

---

### 3. Users Who Listened to a Song

Stores users who listened to a particular song.

**Primary Key**

```
(song, user_id)
```

---

## 🚀 Getting Started

### Create the Keyspace

```sql
CREATE KEYSPACE IF NOT EXISTS sparkify
WITH REPLICATION = {
'class':'SimpleStrategy',
'replication_factor':1
};

USE sparkify;
```

---

## 📋 Create Tables

Create the following tables:

- `song_info_by_session`
- `song_playing_history_by_user`
- `who_listened_to_song`

Each table is designed for a specific query pattern to achieve high-performance data retrieval.

---

## 📥 Insert Sample Data

Sample records include songs such as:

- Hey Jude
- Stairway to Heaven
- Comfortably Numb

and user listening history for multiple users.

---

## 🔍 Sample Queries

### Query 1

Retrieve all songs played during a session.

```sql
SELECT *
FROM song_info_by_session
WHERE session_id = 100;
```

---

### Query 2

Retrieve all songs played by a specific user during a session.

```sql
SELECT *
FROM song_playing_history_by_user
WHERE user_id = 1
AND session_id = 100;
```

---

### Query 3

Find all users who listened to a particular song.

```sql
SELECT *
FROM who_listened_to_song
WHERE song = 'Hey Jude';
```

---

## 📊 Expected Features

- Query-driven database design
- Optimized table structures
- Fast data retrieval
- Efficient partitioning
- Scalable NoSQL architecture
- Support for large-scale distributed applications

---

## 📚 Learning Outcomes

After completing this project, you will understand:

- Apache Cassandra data modeling
- Query-first database design
- Partition Keys
- Clustering Keys
- Primary Keys
- CQL operations
- UPSERT behavior
- Consistency levels in Cassandra
- Optimizing tables for specific queries

---

## 💡 Key Concepts

- Query-driven data modeling
- Denormalization
- Partition Key vs Clustering Key
- No JOIN operations
- High availability
- Horizontal scalability
- Distributed NoSQL databases

---

## ✅ Conclusion

This project successfully demonstrates the implementation of a query-driven music streaming database using Apache Cassandra. Three optimized tables were created to support different query patterns, sample data was inserted, and CQL queries were executed efficiently. The project highlights Cassandra's strength in scalable, high-performance data storage through query-specific table design. :contentReference[oaicite:1]{index=1}

---

## 👨‍💻 Author

**Jayman Prajapati**

Master's in Data Science
