# Identify data formats
## Structored data
Structured data is data that adheres to a fixed schema, so all of the data has the same fields or properties. Most commonly, the schema for structured data entities is tabular - in other words, the data is represented in one or more tables that consist of rows to represent each instance of a data entity, and columns to represent attributes of the entity.
## Semi-structured data
Semi-structured data does not adhere to a fixed schema, but still contains tags or markers to separate semantic elements and enforce hierarchies of records and fields within the data. Common semi-structured data formats include JSON, XML, and YAML. 
## Unstructured data
Unstructured data is data that does not have a pre-defined data model or is not organized in a pre-defined manner. Examples of unstructured data include text documents, images, audio files, and video files.
## Data storage
Organizations typically store data in structured, semi-structured, or unstructured format to record details of entities (for example, customers and products), specific events (such as sales transactions), or other information in documents, images, and other formats. The stored data can then be retrieved for analysis and reporting later.
There are two broad categories of data store in common use:
    -File stores
    -Databases
# Explore file Storage

## Delimiter text files
Delimiter-separated values (DSV) files are text files that use a specific character to separate individual values within a record. Common delimiters include commas (CSV), tabs (TSV), and pipes (|). DSV files are widely used for data exchange and storage due to their simplicity and human-readability. Each line in a DSV file typically represents a single record, with values separated by the chosen delimiter.
## JSON files
JavaScript Object Notation (JSON) is a lightweight data interchange format that is easy for humans to read and write, and easy for machines to parse and generate. JSON files are commonly used for storing and exchanging data between web applications and servers. JSON represents data as key-value pairs, arrays, and nested objects, making it flexible for representing complex data structures.
## eXtensible Markup Language (XML) files
eXtensible Markup Language (XML) is a markup language that defines a set of rules for encoding documents in a format that is both human-readable and machine-readable. XML files are commonly used for data storage and exchange, particularly in web services and configuration files. XML represents data using tags to define elements and attributes, allowing for hierarchical organization of data.
## Binary large objects (BLOB) files
Binary large objects (BLOB) files are used to store large amounts of binary data, such as images, audio, video, and other multimedia content. BLOB files are typically stored in databases or file systems and can be accessed and manipulated using specialized software or programming languages. BLOB files are useful for storing unstructured data that does not fit neatly into traditional data formats.
## Optimized file formats 
- avro: A row-based storage format that is compact and efficient for serialization and deserialization of data. Avro is commonly used in big data processing frameworks like Apache Hadoop and Apache Spark.
- parquet: A columnar storage format that is optimized for read-heavy workloads and analytical queries. Parquet files are highly efficient for storing and querying large datasets, making them popular in data warehousing and big data analytics.
- orc: Another columnar storage format that is designed for high-performance data processing. ORC files are optimized for read and write performance, making them suitable for big data processing frameworks like Apache Hive and Apache Spark.
- delta lake: An open-source storage layer that brings ACID transactions to big data workloads. Delta Lake is built on top of Apache Parquet and provides features like schema enforcement, time travel, and data versioning, making it ideal for building reliable and scalable data lakes.
## Relational databases
Relational databases are a type of database that organizes data into tables with rows and columns. Each table represents a specific entity, and the relationships between entities are established through primary and foreign keys. Relational databases use Structured Query Language (SQL) for data manipulation and retrieval. Common relational database management systems (RDBMS) include MySQL, PostgreSQL, Microsoft SQL Server, and Oracle Database.
## NoSQL databases 
NoSQL databases are a type of database that provides a flexible schema for storing and retrieving data. Unlike relational databases, NoSQL databases do not use tables with fixed columns and rows. Instead, they use various data models, such as document, key-value, column-family, and graph. NoSQL databases are designed to handle large volumes of unstructured or semi-structured data and provide high scalability and performance. Common NoSQL database systems include MongoDB, Cassandra, Redis, and Neo4j.
There are four common types of Non-relational database commonly in use.
### Key-value databases
    in which each record consists of a unique key and an associated value, which can be in any format.
### Document databases
    which store data as documents, typically in JSON or BSON format, allowing for flexible and hierarchical data structures.
### Column-family databases
    which organize data into columns rather than rows, enabling efficient storage and retrieval of large datasets.
### Graph databases
    which represent data as nodes and edges, allowing for complex relationships and connections between data points to be easily modeled and queried.
# Explore data processing
## Transactional data processing systems (OLTP)

Transactional data processing systems are designed to capture and manage real-time business events reliably and at high speed. Each operation is treated as a **transaction**, meaning a small, complete unit of work such as a payment, booking, or fund transfer. These systems prioritize fast read/write access and strong data integrity while supporting very high transaction volumes.

OLTP databases are optimized for **CRUD operations** (Create, Read, Update, Delete) and enforce strict guarantees to keep data correct even under heavy concurrency.

### ACID properties

Transactional systems rely on **ACID** principles to ensure reliability:

#### Atomicity  
Each transaction is executed entirely or not at all. Partial completion is never allowed.

#### Consistency  
Transactions move the database from one valid state to another, preserving rules and constraints.

#### Isolation  
Simultaneous transactions do not interfere with each other, preventing inconsistent intermediate states.

#### Durability  
Once committed, transaction results are permanently stored, even after failures or restarts.

OLTP systems are commonly used in operational or line-of-business applications where correctness, speed, and availability are critical — such as banking, retail, reservations, and enterprise systems.

## Analytical data processing systems

Analytical data processing systems are designed to analyze large volumes of historical business data to generate insights, trends, and metrics. Unlike transactional systems, analytics platforms are typically read-only or read-mostly and focus on querying aggregated data rather than processing individual transactions.

These systems enable organizations to understand performance over time using snapshots or historical datasets.

### Typical analytical architecture

Enterprise analytical systems often follow a layered architecture:

#### Data ingestion (ETL/ELT)  
Operational data is extracted, transformed, and loaded into centralized storage — typically a data lake — to prepare it for analysis.

#### Structured storage layer  
Data is organized into query-optimized structures such as:

- **Data warehouse** — relational schema optimized for analytical queries  
- **Data lakehouse** — hybrid architecture combining scalable storage with SQL-style structure  

Data may be denormalized to improve query performance.

#### Aggregation layer (OLAP) (Online Analytical Processing) 
Data can be pre-aggregated into multidimensional models where numeric measures are summarized across dimensions like time, customer, or product. This allows fast drill-down and roll-up analysis.

#### Consumption layer  
Users query analytical systems to generate dashboards, reports, visualizations, and models:

- Data scientists explore raw data  
- Analysts query warehouse tables  
- Business users consume aggregated dashboards  

### Storage components

#### Data lake  
Large-scale storage for raw or semi-structured data, optimized for flexibility and scalability.

#### Data warehouse  
Structured relational storage optimized for read-heavy analytical workloads.

#### Data lakehouse  
A hybrid model combining the scalability of a data lake with warehouse-style querying.

#### OLAP model  
Pre-aggregated multidimensional storage optimized for fast analytical queries.

Analytical processing systems prioritize historical insight, aggregation efficiency, and query performance to support decision-making and business intelligence.

## OLTP vs OLAP comparison

| Aspect | OLTP (Online Transaction Processing) | OLAP (Online Analytical Processing) |
|------|------|------|
| Primary purpose | Run day-to-day business operations | Analyze historical data for insights |
| Workload type | Transactional, high-frequency CRUD operations | Read-heavy analytical queries and aggregations |
| Data scope | Current, operational data | Historical, aggregated, multi-period data |
| Query pattern | Many small, simple transactions | Fewer but complex analytical queries |
| Performance focus | Low latency, fast writes and reads | Fast query performance over large datasets |
| Data structure | Highly normalized relational schema | Denormalized schemas, star/snowflake models, cubes |
| Concurrency model | High concurrent user transactions | Moderate concurrent analytical queries |
| Data integrity | Strict ACID guarantees | Consistency optimized for reporting accuracy |
| Update frequency | Continuous real-time updates | Periodic batch or streaming loads |
| Storage optimization | Write efficiency and transactional integrity | Read efficiency and aggregation performance |
| Typical users | Operational applications and end users | Analysts, data scientists, business intelligence users |
| Examples | Banking transactions, order processing, reservations | Sales reporting, trend analysis, forecasting |

## Explore job roles in the world of data

Modern organizations rely on multiple specialized roles to manage, protect, transform, and analyze data. While job titles may vary between companies, most responsibilities fall into three core data roles. In smaller organizations, a single person may perform multiple roles.

### Database administrator (DBA)

A database administrator is responsible for the design, implementation, maintenance, and operational reliability of database systems — both on-premises and in the cloud.

Key responsibilities include:

- Ensuring database availability and performance  
- Managing backups and disaster recovery  
- Implementing security and access controls  
- Granting or restricting user permissions  
- Maintaining operational stability  

The DBA focuses on protecting and optimizing the organization’s data infrastructure.

---

### Data engineer

A data engineer designs and manages systems that move, transform, and prepare data for analysis.

Key responsibilities include:

- Building data ingestion pipelines  
- Cleaning and transforming data  
- Integrating data across systems  
- Managing analytical data stores  
- Monitoring pipeline performance  
- Enforcing data governance and privacy  

Data engineers ensure that reliable, high-quality data flows efficiently throughout the organization.

---

### Data analyst

A data analyst converts raw data into meaningful insights that support business decision-making.

Key responsibilities include:

- Exploring datasets to identify trends  
- Creating reports and visualizations  
- Building analytical models  
- Translating business questions into data analysis  

Data analysts focus on extracting value from data to inform strategy and operations.

---

> **Note:**  
> These roles represent common divisions of responsibility. Many organizations also include related roles such as data scientists, data architects, and software engineers who contribute to broader data initiatives.
## Identify data services

Microsoft Azure provides a wide range of cloud services that support both transactional and analytical data workloads. These services allow organizations to store, process, move, analyze, and govern data at scale. While many tools exist, several core services form the foundation of modern cloud data architectures.

### Relational database services

Azure offers managed relational database platforms for transactional workloads:

- **Azure SQL** — managed SQL Server–based databases for operational applications  
- **Azure Database for MySQL, MariaDB, PostgreSQL** — managed open-source relational databases  

These services are commonly used to store application data and act as sources for analytics pipelines.

---

### Non-relational database services

- **Azure Cosmos DB** — globally distributed NoSQL database supporting document, key-value, column, and graph models  

Designed for highly scalable applications requiring low-latency access to non-relational data.

---

### Storage services

- **Azure Storage** — scalable object, file, and key-value storage  

Often used to build data lakes that store raw and semi-structured data for analytics.

---

### Data integration and pipeline services

- **Azure Data Factory** — orchestration service for building ETL/ELT pipelines  

Enables movement and transformation of data across systems.

---

### Unified analytics platforms

- **Microsoft Fabric** — end-to-end SaaS analytics platform combining data ingestion, lakehouse/warehouse analytics, BI, and AI  
- **Azure Databricks** — Spark-based analytics platform for large-scale data engineering and exploration  

These platforms support advanced analytics workflows.

---

### Real-time and big data analytics

- **Azure Stream Analytics** — real-time stream processing  
- **Azure Data Explorer** — high-performance analytics for log and telemetry data  

Used for time-sensitive and large-scale analytical scenarios.

---

### Data governance

- **Microsoft Purview** — enterprise data catalog and governance platform  

Helps track lineage, enforce policies, and ensure trustworthy data usage.

---

Azure data services work together to support the full lifecycle of data — from operational storage and ingestion to analytics, visualization, and governance.
## Azure data services — comparison table

| Service | Category | Primary purpose | Typical workload | Data model | Common users | When to use |
|---------|----------|----------------|------------------|------------|--------------|-------------|
| Azure SQL Database / Managed Instance / VM | Relational database | Transactional data storage | OLTP applications | Relational (SQL) | DBAs, data engineers, app developers | When you need reliable structured transactional storage |
| Azure Database for MySQL / MariaDB / PostgreSQL | Open-source relational database | Managed open-source transactional databases | OLTP applications | Relational (SQL + extensions) | DBAs, developers, data engineers | When using open-source stacks or platform compatibility is required |
| Azure Cosmos DB | NoSQL database | Globally distributed low-latency storage | High-scale operational workloads | Document, key-value, graph, column | Developers, data engineers | When you need massive scale, global replication, or flexible schemas |
| Azure Storage (Blob/Data Lake) | Storage platform | Scalable raw data storage | Analytical staging and archival | Files, objects, key-value | Data engineers | When building data lakes or storing large unstructured datasets |
| Azure Data Factory | Data integration | Data movement and transformation orchestration | ETL/ELT pipelines | Pipeline workflows | Data engineers | When automating ingestion and transformation pipelines |
| Microsoft Fabric | Unified analytics platform | End-to-end analytics environment | Lakehouse, warehouse, BI, AI analytics | Mixed analytical models | Data engineers, analysts | When you want a centralized analytics platform |
| Azure Databricks | Big data analytics | Large-scale Spark processing | Advanced analytics and data engineering | Distributed datasets | Data engineers, data scientists | When processing large datasets or running Spark workloads |
| Azure Stream Analytics | Real-time analytics | Streaming data processing | Event-driven analytics | Stream-based data | Data engineers | When analyzing real-time data streams |
| Azure Data Explorer | Big data analytics | Fast querying of log/telemetry data | Time-series analytics | Columnar/time-series | Analysts, engineers | When working with logs, IoT, or telemetry data |
| Microsoft Purview | Data governance | Data cataloging and lineage tracking | Governance and compliance | Metadata/catalog | Data governance teams, engineers | When managing enterprise data trust and compliance |


## Relational data modeling 

In a relational database, real-world entities (such as customers, products, or orders) are represented as tables. Each table stores structured data where every row represents a single instance of an entity, and every column defines a specific attribute.

All rows share the same structure, though some fields can be empty (NULL). Each column is assigned a datatype — such as text, numeric, or date/time — ensuring consistent and valid data storage according to database rules.
# Database Normalization

## What is Normalization?
Normalization is a process to design database schemas that **minimize data duplication** and **ensure data integrity**.

## Core Principles
1. **Entities → Tables**: Each entity has its own table.
2. **Attributes → Columns**: Each property of an entity has its own column.
3. **Primary Keys**: Unique identifier for each entity instance.
4. **Foreign Keys**: Link related entities through relationships.

## Example
- **Unnormalized Table**: Combines multiple entities in one table with repeated data.
- **Normalized Tables**:
  - Customer, Product, Order, LineItem tables
  - Attributes separated into columns
  - Foreign keys link orders to customers

## Benefits
- Eliminates data duplication
- Ensures data integrity
- Enables granular querying
- Enforces correct data types

## Keys
- **Primary Key**: Unique row identifier
- **Foreign Key**: Reference to another table’s primary key
- **Composite Key**: Unique combination of multiple columns
