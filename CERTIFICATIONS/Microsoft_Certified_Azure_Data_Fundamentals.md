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
