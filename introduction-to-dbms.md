# Introduction to DBMS: Detailed Student Notes

## Learning Objectives

After studying this chapter, you should be able to:

- Explain data, information, databases, and DBMS.
- Describe why database systems are preferred over ordinary file systems.
- Identify the advantages, disadvantages, and applications of DBMS.
- Compare hierarchical, network, relational, object-oriented, and NoSQL databases.
- Distinguish between a DBMS and an RDBMS.
- Recognize common DBMS products and their typical uses.

---

## 1. What Is Data?

**Data** is a collection of raw facts, figures, symbols, or observations. Raw data may not be useful until it is processed and organized.

### Examples

- `Asha`, `21`, and `Computer Science` are data about a student.
- `45000` is data representing a salary, but its meaning depends on context.
- A list of product codes, prices, and quantities is data about inventory.

### Data and Information

**Information** is processed, organized, and meaningful data.

For example:

- Data: `72, 85, 90`
- Information: `The student's average mark is 82.33.`

A DBMS helps convert stored data into useful information through queries, reports, and analysis.

### Types of Data

- **Structured data:** Organized in a fixed format, such as rows and columns in a table.
- **Semi-structured data:** Has some organization but does not follow a strict table format, such as JSON or XML.
- **Unstructured data:** Has no fixed database structure, such as images, videos, audio, and documents.

---

## 2. What Is a Database?

A **database** is an organized collection of related data that can be stored, accessed, managed, and updated efficiently.

A database is more than a collection of files. It also includes relationships, rules, and structures that help users work with data accurately.

### Example: College Database

A college database may contain:

- A `Student` table with student IDs, names, and email addresses
- A `Course` table with course IDs and course names
- An `Enrollment` table showing which student takes which course
- A `Result` table containing marks and grades

The tables are related through common fields such as `StudentID` and `CourseID`.

### Important Database Terms

- **Table:** A collection of related data arranged in rows and columns.
- **Row or record:** One complete item in a table, such as one student's details.
- **Column or attribute:** A property of an item, such as `StudentName`.
- **Field:** A single data value at the intersection of a row and column.
- **Schema:** The logical design or structure of a database.
- **Database instance:** The actual data stored in the database at a particular time.

---

## 3. What Is a DBMS?

A **Database Management System (DBMS)** is software that allows users and applications to create, store, organize, retrieve, update, and control data in databases.

The DBMS acts as an intermediary between users or application programs and the database.

```text
User or Application
        |
        v
      DBMS
        |
        v
    Database
```

### Main Functions of a DBMS

1. **Data definition:** Creates databases, tables, views, indexes, and other structures.
2. **Data manipulation:** Inserts, updates, deletes, and retrieves data.
3. **Data security:** Controls who can view or modify particular data.
4. **Data integrity:** Enforces rules so that incorrect data is rejected.
5. **Transaction management:** Ensures that related operations are completed correctly.
6. **Concurrency control:** Coordinates multiple users accessing data at the same time.
7. **Backup and recovery:** Restores data after hardware failures, software errors, or other problems.
8. **Query processing:** Interprets queries and chooses efficient execution methods.
9. **Metadata management:** Stores information about database objects, columns, constraints, and users.

### Examples of DBMS Software

- MySQL
- PostgreSQL
- Oracle Database
- Microsoft SQL Server
- MongoDB
- SQLite

---

## 4. Why Do We Need a DBMS?

Traditional file systems become difficult to manage when data is large, shared by many users, or frequently changed. A DBMS solves many of these problems.

### Reasons for Using a DBMS

- **Efficient storage:** Organizes large volumes of data systematically.
- **Fast retrieval:** Allows users to search and filter data with queries.
- **Data sharing:** Lets multiple users and applications access the same data.
- **Reduced duplication:** Avoids storing the same fact unnecessarily in many files.
- **Improved consistency:** Helps ensure that all users see correct and current data.
- **Security:** Provides authentication, roles, and permissions.
- **Integrity:** Enforces rules such as unique IDs and valid references.
- **Concurrent access:** Supports many users working at the same time.
- **Recovery:** Protects data against failures and accidental loss.
- **Data independence:** Allows changes to storage details without rewriting every application.

### Example

In a bank, a money transfer may involve subtracting money from one account and adding it to another. A DBMS can treat both operations as one transaction. If one operation fails, the DBMS can undo the other operation so that money is not lost or created accidentally.

---

## 5. File System vs DBMS

A **file system** stores data in separate files managed by the operating system. A **DBMS** provides a specialized system for storing, relating, querying, securing, and recovering data.

| Feature | File System | DBMS |
|---|---|---|
| Data organization | Separate files and folders | Structured databases and related objects |
| Redundancy | Often high | Reduced through good database design |
| Consistency | Difficult to maintain across files | Supported by constraints and transactions |
| Data sharing | Limited | Designed for controlled multi-user sharing |
| Querying | Requires custom programs | Supports query languages such as SQL |
| Security | Usually file-level permissions | Users, roles, privileges, and auditing |
| Relationships | Must be handled by application code | Represented using keys and relationships |
| Concurrency | Limited support | Locking and transaction mechanisms |
| Backup and recovery | Often needs separate tools | Usually built into the DBMS |
| Integrity rules | Enforced by programs | Enforced by database constraints and programs |
| Scalability | Becomes difficult as data grows | Designed for larger and shared systems |
| Cost and complexity | Simple and inexpensive for small tasks | More resources and administration may be required |

### File System Example

A school may keep student data in separate files for admissions, fees, and examinations. If a student's phone number changes, it may need to be updated in several files. Forgetting one file creates inconsistent information.

### DBMS Example

In a DBMS, student information can be stored once and referenced by admissions, fees, and examination modules. A single update can be reflected wherever the information is used.

---

## 6. Advantages of DBMS

### 6.1 Reduced Data Redundancy

Redundancy means unnecessary repetition of the same data. A properly designed database stores each important fact in an appropriate place and references it when needed.

### 6.2 Improved Data Consistency

When duplicate data is reduced, the chance of conflicting values is also reduced. For example, a customer's address is less likely to differ between two departments.

### 6.3 Data Security

A DBMS can assign different privileges to different users. For example:

- A student may view personal grades.
- A teacher may enter grades for assigned courses.
- An administrator may manage student records.

### 6.4 Data Integrity

Integrity rules prevent invalid data. Examples include:

- A student ID must be unique.
- A mark must be between 0 and 100.
- An enrollment cannot refer to a student who does not exist.

### 6.5 Data Sharing

Many departments and applications can use the same database while following controlled access rules.

### 6.6 Backup and Recovery

The DBMS can create backups and recover data after crashes, power failures, or accidental deletion.

### 6.7 Concurrency Control

When several users update the same data, the DBMS coordinates their operations to prevent incorrect results.

### 6.8 Data Independence

Applications do not always need to know how data is physically stored. Storage structures can change while the logical application interface remains stable.

### 6.9 Better Decision-Making

Queries and reports allow organizations to analyze current and historical data and make informed decisions.

---

## 7. Disadvantages of DBMS

- **Cost:** Commercial licenses, servers, storage, training, and administration may be expensive.
- **Complexity:** Database design, security, tuning, and recovery require skilled professionals.
- **Resource requirements:** A DBMS may use significant memory, CPU, and disk space.
- **Centralized risk:** If a critical database becomes unavailable, many applications may be affected.
- **Maintenance:** Software updates, backups, monitoring, and performance tuning are ongoing tasks.
- **Migration difficulty:** Moving data and applications to another DBMS can be complex.
- **Performance overhead:** A DBMS may be unnecessary for a tiny, single-user application.
- **Security exposure:** A successful attack on a central database may expose a large amount of information.
- **Incorrect design consequences:** Poor schema design or missing indexes can cause slow queries and inconsistent data.

The disadvantages do not mean that DBMSs should be avoided. They show why database selection, design, security, and administration are important.

---

## 8. DBMS Applications

DBMSs are used wherever organizations need to store and manage related information.

| Area | Typical Data |
|---|---|
| Banking | Accounts, transactions, loans, customers |
| Education | Students, courses, attendance, grades |
| Healthcare | Patients, doctors, appointments, prescriptions |
| E-commerce | Products, customers, carts, orders, payments |
| Telecommunications | Subscribers, plans, calls, usage, billing |
| Airlines and railways | Routes, schedules, reservations, tickets |
| Government | Citizens, taxes, licenses, public services |
| Manufacturing | Inventory, suppliers, production, shipments |
| Human resources | Employees, salaries, leave, recruitment |
| Libraries | Books, members, loans, returns, fines |
| Social media | Profiles, posts, comments, messages, relationships |
| Logistics | Warehouses, vehicles, deliveries, tracking |

---

## 9. Types of Databases

Databases can be classified by their data model, location, workload, or storage method.

### 9.1 Centralized Database

A centralized database is stored and managed at one main location. Users may access it through a network.

**Benefit:** Administration is simpler because data is kept in one place.

**Limitation:** A failure at the central location can affect all users.

### 9.2 Distributed Database

A distributed database stores data across multiple networked locations. The system may make the separate locations appear as one database to users.

**Benefits:** Better local access, availability, and scalability.

**Challenges:** Network failures, synchronization, and distributed transaction management.

### 9.3 Cloud Database

A cloud database runs on cloud infrastructure and is accessed through a network. Cloud providers may manage backups, scaling, availability, and maintenance.

### 9.4 Operational Database

An operational database supports the daily transactions of an organization, such as placing orders or recording payments.

### 9.5 Data Warehouse

A data warehouse stores integrated historical data for reporting, analytics, and decision-making. It is generally optimized for analysis rather than frequent small transactions.

### 9.6 Relational Database

A relational database stores data in tables and connects those tables using relationships. It is explained in detail below.

### 9.7 NoSQL Database

A NoSQL database uses non-relational models such as documents, key-value pairs, columns, or graphs. It is useful when data is large, distributed, or frequently changing.

---

## 10. Types of DBMS

### 10.1 Hierarchical DBMS

A **hierarchical DBMS** organizes records in a tree structure. Each child record usually has one parent, while one parent may have many children.

```text
University
├── Faculty of Science
│   ├── Computer Science
│   └── Physics
└── Faculty of Arts
    ├── History
    └── English
```

#### Characteristics

- Parent-child relationship
- One-to-many structure
- Navigation from the root toward lower levels

#### Advantages

- Easy to understand for tree-shaped data
- Fast navigation when relationships are fixed
- Useful for some organizational and directory structures

#### Limitations

- Difficult to represent many-to-many relationships
- Changes to the structure may require major redesign
- Data can become difficult to access if the required path is not known

#### Example

IBM Information Management System is a well-known historical example of a hierarchical database system.

### 10.2 Network DBMS

A **network DBMS** represents records as nodes connected by links. A record can have multiple parent records, so it supports more complex relationships than a hierarchical DBMS.

#### Characteristics

- Graph-like record structure
- Supports one-to-one, one-to-many, and many-to-many relationships
- Uses navigational links between records

#### Advantages

- Handles complex relationships
- Can provide efficient navigation
- More flexible than the hierarchical model

#### Limitations

- More difficult to design and maintain
- Applications may depend heavily on the physical structure
- Less common for modern general-purpose development

### 10.3 Relational DBMS

A **Relational Database Management System (RDBMS)** stores data in tables consisting of rows and columns. Tables are connected through keys.

#### Example

`Student` table:

| StudentID | StudentName | Department |
|---|---|---|
| 101 | Asha | Computer Science |
| 102 | Ravi | Physics |

`Enrollment` table:

| StudentID | CourseID | Semester |
|---|---|---|
| 101 | CS101 | 1 |
| 102 | PHY101 | 1 |

`StudentID` can identify a student in the `Student` table and refer to that student in the `Enrollment` table.

#### Important RDBMS Concepts

- **Primary key:** A column or group of columns that uniquely identifies each row.
- **Foreign key:** A column that refers to a key in another table.
- **Relationship:** An association between tables.
- **Constraint:** A rule that restricts invalid data.
- **SQL:** A language used to define, query, and manipulate relational data.
- **Normalization:** A design technique that reduces unnecessary repetition and update problems.

#### Advantages

- Clear and well-understood table structure
- Powerful queries using SQL
- Strong integrity and transaction support
- Mature tools, standards, and community support
- Suitable for many business applications

### 10.4 Object-Oriented DBMS

An **object-oriented DBMS (OODBMS)** stores data as objects, similar to objects in object-oriented programming languages.

An object can contain:

- **State:** Data or attributes
- **Behavior:** Methods or operations
- **Identity:** A unique object identity

#### Advantages

- Naturally represents complex objects such as engineering designs or multimedia
- Supports classes, inheritance, and reusable types
- Can reduce the mismatch between application objects and database objects

#### Limitations

- Smaller ecosystem than relational databases
- Fewer universally accepted standards
- May not be ideal for traditional table-based reporting

### 10.5 NoSQL DBMS

**NoSQL** databases are designed for flexible data models, high scalability, and specialized access patterns. NoSQL commonly means “not only SQL,” because some NoSQL systems also support SQL-like query features.

#### Main NoSQL Models

1. **Document database:** Stores records as JSON-like documents. Example: MongoDB.
2. **Key-value database:** Stores a value using a unique key. Example: Redis.
3. **Column-family database:** Stores data in column groups across distributed systems. Example: Apache Cassandra.
4. **Graph database:** Stores entities as nodes and their connections as relationships. Example: Neo4j.

#### Advantages

- Flexible or schema-on-read data models
- Suitable for large and rapidly changing datasets
- Often scales horizontally by adding servers
- Useful for high-volume distributed workloads

#### Limitations

- Query languages and features differ between products
- Transaction and consistency guarantees vary
- Flexible schemas can permit inconsistent data if application rules are weak
- Relationships and joins may be less convenient in some systems

---

## 11. DBMS vs RDBMS

A **DBMS** is a general term for software that manages databases. An **RDBMS** is a specific type of DBMS based on the relational model.

| Feature | DBMS | RDBMS |
|---|---|---|
| Meaning | General database management software | Relational database management software |
| Data model | May be hierarchical, network, object-oriented, relational, or another model | Relational model only |
| Storage | May use files, records, objects, or tables | Uses related tables |
| Relationships | Support varies | Represented using primary and foreign keys |
| Normalization | May or may not be used | Commonly used to reduce redundancy |
| Constraints | Support depends on the product | Commonly supports key, domain, and referential constraints |
| Transactions | Support varies | Typically provides robust transaction processing |
| Query language | Depends on the system | Usually supports SQL |
| Examples | Hierarchical, network, object, relational, and NoSQL systems | MySQL, PostgreSQL, Oracle Database, SQL Server |

### Key Exam Point

Every RDBMS is a DBMS, but every DBMS is not an RDBMS.

---

## 12. Popular DBMS Software

### 12.1 MySQL

**MySQL** is a popular open-source relational database system. It is widely used in websites, web applications, content management systems, and online services.

#### Common Features

- SQL support
- Transactions and indexes
- Replication and high availability options
- Multiple storage engines
- Strong ecosystem for web development

#### Typical Use

A small or medium web application may use MySQL to store users, products, orders, and payments.

### 12.2 PostgreSQL

**PostgreSQL** is an open-source object-relational database system known for reliability, standards compliance, extensibility, and advanced SQL capabilities.

#### Common Features

- Complex queries and joins
- Transactions and strong consistency
- Custom data types and extensions
- JSON and other semi-structured data support
- Full-text search and advanced indexing

#### Typical Use

PostgreSQL is suitable for applications that need complex queries, strong data integrity, and advanced data types.

### 12.3 Oracle Database

**Oracle Database** is a commercial enterprise relational database system used in many large and mission-critical organizations.

#### Common Features

- Strong security and access control
- High availability and recovery options
- Partitioning and performance tools
- Distributed database features
- Support for large workloads and enterprise applications

#### Typical Use

Banks, governments, and large corporations may use Oracle Database for critical financial, customer, and operational systems.

### 12.4 Microsoft SQL Server

**Microsoft SQL Server** is a relational database system developed by Microsoft. It works closely with Microsoft development, reporting, cloud, and business intelligence tools.

#### Common Features

- SQL querying and transaction processing
- Security and auditing
- Reporting and analytics tools
- High availability features
- Integration with Microsoft platforms and services

#### Typical Use

Organizations using Microsoft-based business applications often use SQL Server for finance, human resources, sales, and reporting systems.

---

## 13. Basic DBMS Concepts for Revision

### 13.1 Schema and Instance

- **Schema:** The design of the database, including tables, columns, relationships, and constraints.
- **Instance:** The actual data stored at a particular moment.

The schema usually changes less frequently, while the instance changes whenever records are inserted, updated, or deleted.

### 13.2 Data Integrity

Data integrity means that data remains accurate, valid, and consistent.

Common integrity rules include:

- **Entity integrity:** A primary key cannot be null and must uniquely identify a row.
- **Referential integrity:** A foreign key must refer to an existing related row or be null where permitted.
- **Domain integrity:** A value must belong to an allowed type or range.
- **User-defined integrity:** Organization-specific rules, such as an employee's joining date not being in the future.

### 13.3 Transaction and ACID Properties

A **transaction** is a logical unit of work, such as transferring money or placing an order.

ACID properties help make transactions reliable:

- **Atomicity:** All operations in a transaction happen, or none happen.
- **Consistency:** A transaction takes the database from one valid state to another valid state.
- **Isolation:** Concurrent transactions do not improperly interfere with each other.
- **Durability:** Once committed, the result remains saved even after a failure.

### 13.4 Data Independence

- **Physical data independence:** Changes to physical storage should not require changes to the logical design or application programs.
- **Logical data independence:** Changes to the logical schema should require minimal changes to user views and applications.

---

## 14. Quick Comparison of Database Models

| Model | Main Structure | Best Suited For | Main Limitation |
|---|---|---|---|
| Hierarchical | Tree | Strict parent-child data | Weak many-to-many support |
| Network | Linked records | Complex navigational relationships | Difficult maintenance |
| Relational | Tables | Structured business data and transactions | Schema changes may require planning |
| Object-oriented | Objects and classes | Complex object-based applications | Smaller ecosystem |
| NoSQL | Documents, key-values, columns, or graphs | Flexible and distributed data | Less uniform standards |

---

## 15. Important Advantages and Limitations at a Glance

### Advantages

- Organized data storage
- Faster searching and reporting
- Reduced redundancy
- Better consistency and integrity
- Security and access control
- Multi-user support
- Backup and recovery
- Transaction management

### Limitations

- Cost and complexity
- Need for trained administrators
- Hardware and software resource usage
- Maintenance and upgrade requirements
- Potential impact of central failures
- Possible security impact of a database breach

---

## 16. Frequently Asked Questions

### What is the difference between data and information?

Data is raw, unprocessed facts. Information is data that has been processed and given meaning.

### Is a database the same as a DBMS?

No. A database is the organized collection of data. A DBMS is the software used to create, manage, and access that database.

### Is SQL a DBMS?

No. SQL is a language used to work with many relational databases. MySQL, PostgreSQL, Oracle Database, and SQL Server are DBMS products that support SQL.

### Is every DBMS relational?

No. Hierarchical, network, object-oriented, and NoSQL systems are also types of DBMSs.

### Is every RDBMS a DBMS?

Yes. An RDBMS is a specialized type of DBMS that uses the relational model.

### When should a NoSQL database be considered?

A NoSQL database may be considered when the application needs flexible schemas, very large distributed workloads, high write throughput, or a specialized document, key-value, column, or graph model.

---

## 17. Short Answer Questions for Practice

1. Define data and information with an example.
2. What is a database?
3. Define DBMS.
4. List five functions of a DBMS.
5. Why is a DBMS preferred over a file system for large applications?
6. State four advantages of a DBMS.
7. State four disadvantages of a DBMS.
8. What is a hierarchical database model?
9. How is a network DBMS different from a hierarchical DBMS?
10. Explain the relational model.
11. What are primary keys and foreign keys?
12. What is an object-oriented DBMS?
13. Name four types of NoSQL databases.
14. Differentiate between DBMS and RDBMS.
15. Name four popular relational database products.
16. Explain the ACID properties of transactions.
17. What is data independence?
18. What is referential integrity?

---

## 18. Final Revision Summary

- **Data** is raw facts; **information** is processed and meaningful data.
- A **database** is an organized collection of related data.
- A **DBMS** is software that manages databases.
- DBMSs provide security, integrity, concurrency, backup, recovery, and efficient querying.
- A file system is simpler, but a DBMS is better for shared, secure, and large-scale data management.
- Major database models include hierarchical, network, relational, object-oriented, and NoSQL.
- An **RDBMS** stores data in related tables and commonly uses SQL.
- Every RDBMS is a DBMS, but not every DBMS is an RDBMS.
- MySQL, PostgreSQL, Oracle Database, and SQL Server are popular relational database systems.
- Good database design is essential for performance, consistency, security, and maintainability.
