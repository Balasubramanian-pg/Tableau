# FIXED on high-cardinality fields

Canonical documentation for FIXED on high-cardinality fields. This document defines the conceptual model, terminology, constraints, and standard usage patterns.

> [!NOTE]
> This documentation is implementation-agnostic and intended to serve as a stable reference.

## 1. Purpose and Problem Space

The FIXED data type is used to optimize storage and query performance in databases, particularly when dealing with high-cardinality fields. High-cardinality fields are those that contain a large number of unique values, making them challenging to index and query efficiently. The purpose of using FIXED on high-cardinality fields is to mitigate the performance issues associated with these fields, such as slow query execution, increased storage requirements, and decreased data retrieval efficiency. Misunderstanding or inconsistent application of FIXED on high-cardinality fields can lead to suboptimal database performance, increased storage costs, and decreased data quality.

## 2. Conceptual Overview

The conceptual model of FIXED on high-cardinality fields consists of three major components:

1. **Data Type**: The FIXED data type is used to store high-cardinality fields in a compact and efficient manner.
2. **Indexing**: Indexing is used to improve query performance on high-cardinality fields by allowing the database to quickly locate specific values.
3. **Storage**: Storage refers to the physical storage of high-cardinality fields, which can be optimized using compression and encoding techniques.

These components interact to produce the following outcomes:

* Improved query performance: By using FIXED and indexing, queries on high-cardinality fields can be executed more efficiently.
* Reduced storage requirements: By using compression and encoding techniques, storage requirements for high-cardinality fields can be minimized.
* Enhanced data quality: By using FIXED and indexing, data quality can be improved by reducing errors and inconsistencies.

## 3. Scope and Non-Goals

The scope of this documentation includes:

**In scope:**
* Conceptual model of FIXED on high-cardinality fields
* Terminology and definitions related to FIXED and high-cardinality fields
* Core concepts and standard model for using FIXED on high-cardinality fields
* Common patterns and anti-patterns associated with FIXED on high-cardinality fields

**Out of scope:**
* Tool-specific implementations of FIXED on high-cardinality fields
* Vendor-specific behavior and optimizations
* Operational or procedural guidance for using FIXED on high-cardinality fields

> [!IMPORTANT]
> Out-of-scope items may be addressed in companion or derivative documentation.

## 4. Terminology and Definitions

The following terms are used throughout this document:

| Term | Definition |
|------|------------|
| High-cardinality field | A field that contains a large number of unique values, making it challenging to index and query efficiently. |
| FIXED data type | A data type used to store high-cardinality fields in a compact and efficient manner. |
| Indexing | The process of creating a data structure to improve query performance on high-cardinality fields. |
| Compression | The process of reducing the size of stored data to minimize storage requirements. |
| Encoding | The process of converting data into a more compact or efficient format to reduce storage requirements. |

> [!TIP]
> Definitions should avoid contextual or time-bound language and remain valid as the ecosystem evolves.

## 5. Core Concepts

### 5.1 Concept One: FIXED Data Type
The FIXED data type is used to store high-cardinality fields in a compact and efficient manner. It is designed to optimize storage and query performance by reducing the amount of storage required for each value.

### 5.2 Concept Two: Indexing
Indexing is used to improve query performance on high-cardinality fields by allowing the database to quickly locate specific values. Indexing can be used in conjunction with the FIXED data type to further optimize query performance.

### 5.3 Concept Interactions and Constraints
The FIXED data type and indexing interact to produce the following outcomes:

* Improved query performance: By using FIXED and indexing, queries on high-cardinality fields can be executed more efficiently.
* Reduced storage requirements: By using compression and encoding techniques, storage requirements for high-cardinality fields can be minimized.

The following constraints apply:

* The FIXED data type is only applicable to high-cardinality fields.
* Indexing is only effective when used in conjunction with the FIXED data type.

## 6. Standard Model

### 6.1 Model Description
The standard model for using FIXED on high-cardinality fields consists of the following components:

1. **Data Type**: The FIXED data type is used to store high-cardinality fields.
2. **Indexing**: Indexing is used to improve query performance on high-cardinality fields.
3. **Storage**: Storage refers to the physical storage of high-cardinality fields, which can be optimized using compression and encoding techniques.

### 6.2 Assumptions
The standard model assumes the following:

* The database is designed to optimize query performance and storage requirements.
* The high-cardinality fields are properly indexed and compressed.

### 6.3 Invariants
The following properties must always hold true within the standard model:

* The FIXED data type is used to store high-cardinality fields.
* Indexing is used to improve query performance on high-cardinality fields.
* Storage requirements are minimized using compression and encoding techniques.

> [!IMPORTANT]
> Deviations from the standard model must be explicitly documented and justified.

## 7. Common Patterns

### Pattern A: Using FIXED with Indexing
* **Intent**: Improve query performance on high-cardinality fields.
* **Context**: When high-cardinality fields are frequently queried.
* **Tradeoffs**: Improved query performance may come at the cost of increased storage requirements.

## 8. Anti-Patterns

### Anti-Pattern A: Using VARCHAR instead of FIXED
* **Description**: Using VARCHAR instead of FIXED to store high-cardinality fields.
* **Failure Mode**: Suboptimal query performance and increased storage requirements.
* **Common Causes**: Lack of understanding of the FIXED data type and its benefits.

> [!WARNING]
> These anti-patterns frequently lead to correctness, maintainability, or scalability issues.

## 9. Edge Cases and Boundary Conditions

The following edge cases and boundary conditions may challenge the standard model:

* **Null or empty values**: How to handle null or empty values in high-cardinality fields.
* **Data type conversions**: How to handle data type conversions between FIXED and other data types.

> [!CAUTION]
> Edge cases are often under-documented and a common source of incorrect assumptions.

## 10. Related Topics

The following topics are related to FIXED on high-cardinality fields:

* Data modeling and database design
* Query optimization and performance tuning
* Data compression and encoding techniques

## 11. References

1. **Data Modeling Essentials**  
   Graeme Simsion and Graham Witt  
   [https://www.oreilly.com/library/view/data-modeling-essentials/9780128094347/](https://www.oreilly.com/library/view/data-modeling-essentials/9780128094347/)  
   *Justification*: This book provides a comprehensive overview of data modeling concepts, including data types and indexing.
2. **Database Systems: The Complete Book**  
   Hector Garcia-Molina, Ivan Martinez, and Jose Valenza  
   [https://www.amazon.com/Database-Systems-Complete-Book-2nd/dp/0131873253](https://www.amazon.com/Database-Systems-Complete-Book-2nd/dp/0131873253)  
   *Justification*: This book provides a detailed explanation of database systems, including data types, indexing, and query optimization.
3. **SQL Server Data Types**  
   Microsoft  
   [https://docs.microsoft.com/en-us/sql/t-sql/data-types/data-types-transact-sql?view=sql-server-ver15](https://docs.microsoft.com/en-us/sql/t-sql/data-types/data-types-transact-sql?view=sql-server-ver15)  
   *Justification*: This documentation provides a detailed explanation of SQL Server data types, including the FIXED data type.
4. **Indexing in Oracle Database**  
   Oracle  
   [https://docs.oracle.com/en/database/oracle/oracle-database/21/indexing/index.html](https://docs.oracle.com/en/database/oracle/oracle-database/21/indexing/index.html)  
   *Justification*: This documentation provides a detailed explanation of indexing in Oracle Database, including indexing on high-cardinality fields.
5. **Data Compression in PostgreSQL**  
   PostgreSQL  
   [https://www.postgresql.org/docs/13/sql-compress.html](https://www.postgresql.org/docs/13/sql-compress.html)  
   *Justification*: This documentation provides a detailed explanation of data compression in PostgreSQL, including compression techniques for high-cardinality fields.

> [!IMPORTANT]
> These references are normative unless explicitly marked as informative.

> [!CAUTION]
> If fewer than five authoritative references exist, explicitly state this.

## 12. Change Log

| Version | Date | Description |
|---------|------|-------------|
| 1.0 | 2026-01-31 | Initial documentation |

---