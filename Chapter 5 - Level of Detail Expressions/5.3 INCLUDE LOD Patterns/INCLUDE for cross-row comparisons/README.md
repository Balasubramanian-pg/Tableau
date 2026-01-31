# INCLUDE for cross-row comparisons

Canonical documentation for INCLUDE for cross-row comparisons. This document defines the conceptual model, terminology, constraints, and standard usage patterns.

> [!NOTE]
> This documentation is implementation-agnostic and intended to serve as a stable reference.

## 1. Purpose and Problem Space

The INCLUDE statement for cross-row comparisons exists to address the need for efficient and flexible data analysis across multiple rows in a dataset. This topic class of problems involves complex data relationships, aggregations, and filtering, which can lead to performance issues, incorrect results, or cumbersome query structures if not properly managed. The risks of misunderstanding or misapplying INCLUDE for cross-row comparisons include decreased query performance, incorrect data interpretation, and increased maintenance costs due to overly complex queries.

## 2. Conceptual Overview

The conceptual model of INCLUDE for cross-row comparisons involves several major components:
- **Data Source**: The dataset from which data is retrieved.
- **Comparison Criteria**: The conditions that define how rows are compared.
- **Aggregation Functions**: The methods used to combine data from multiple rows.
- **Filtering Conditions**: The rules that determine which rows are included in the comparison.

These components interact to produce outcomes such as aggregated values, filtered datasets, and sorted results, designed to facilitate insightful data analysis and reporting.

## 3. Scope and Non-Goals

Clarify the explicit boundaries of this documentation.

**In scope:**
* Conceptual model of INCLUDE for cross-row comparisons
* Terminology and definitions related to cross-row comparisons
* Standard usage patterns and best practices

**Out of scope:**
* Tool-specific implementations of INCLUDE (e.g., SQL dialects, programming languages)
* Vendor-specific behavior or optimizations
* Operational or procedural guidance for query optimization or database administration

> [!IMPORTANT]
> Out-of-scope items may be addressed in companion or derivative documentation.

## 4. Terminology and Definitions

| Term | Definition |
|------|------------|
| INCLUDE | A statement or clause used to specify columns or expressions to be included in a cross-row comparison. |
| Cross-Row Comparison | An operation that compares data across multiple rows in a dataset, often involving aggregation, filtering, or sorting. |
| Aggregate Function | A function that combines values from multiple rows into a single value, such as SUM, AVG, or COUNT. |

> [!TIP]
> Definitions should avoid contextual or time-bound language and remain valid as the ecosystem evolves.

## 5. Core Concepts

Explain the fundamental ideas that form the basis of this topic.

### 5.1 Concept One: Data Source
The data source is the foundation of any cross-row comparison, providing the dataset from which data is retrieved. This can be a database table, a view, or a result set from a previous query.

### 5.2 Concept Two: Comparison Criteria
Comparison criteria define how rows are compared, including the columns or expressions used for comparison and the conditions that must be met (e.g., equality, inequality).

### 5.3 Concept Interactions and Constraints
The data source, comparison criteria, and aggregate functions interact to produce the desired outcomes. Constraints such as data types, nullability, and indexing can affect the efficiency and accuracy of cross-row comparisons.

## 6. Standard Model

Describe the generally accepted or recommended model for this topic.

### 6.1 Model Description
The standard model for INCLUDE in cross-row comparisons involves specifying the data source, defining the comparison criteria, applying aggregate functions as necessary, and filtering the results based on specified conditions.

### 6.2 Assumptions
This model assumes that the data source is properly structured and indexed, that comparison criteria are well-defined and consistent, and that aggregate functions are appropriately chosen for the data types involved.

### 6.3 Invariants
Properties that must always hold true within this model include:
- Data integrity: The data source must be consistent and accurate.
- Comparison consistency: Comparison criteria must be applied uniformly across all rows.
- Aggregate function appropriateness: Aggregate functions must be suitable for the data types and the analysis goals.

> [!IMPORTANT]
> Deviations from the standard model must be explicitly documented and justified.

## 7. Common Patterns

Document recurring, accepted patterns associated with this topic.

### Pattern A: Using INCLUDE with Aggregate Functions
- **Intent:** To efficiently aggregate data across multiple rows based on specific conditions.
- **Context:** When the analysis requires combining values from multiple rows, such as calculating totals or averages.
- **Tradeoffs:** Improved query performance and readability versus potential increased complexity in defining the comparison criteria.

## 8. Anti-Patterns

Describe common but discouraged practices.

> [!WARNING]
> These anti-patterns frequently lead to correctness, maintainability, or scalability issues.

### Anti-Pattern A: Overly Complex Comparison Criteria
- **Description:** Using excessively complex or nested conditions for cross-row comparisons.
- **Failure Mode:** Leads to decreased query performance, increased risk of errors, and difficulty in maintaining or modifying the queries.
- **Common Causes:** Lack of proper data modeling, insufficient use of indexing, or inadequate optimization techniques.

## 9. Edge Cases and Boundary Conditions

Explain unusual or ambiguous scenarios that may challenge the standard model.

> [!CAUTION]
> Edge cases are often under-documented and a common source of incorrect assumptions.

Handling null values, dealing with duplicate rows, and managing data type conversions are common edge cases in cross-row comparisons.

## 10. Related Topics

List adjacent, dependent, or prerequisite topics.
- Data Modeling
- Query Optimization
- Aggregate Functions
- Data Filtering and Sorting

## 11. References

1. **SQL:2016**  
   International Organization for Standardization (ISO)  
   https://www.iso.org/standard/63555.html  
   *Justification:* Provides the standard specification for SQL, including clauses related to cross-row comparisons.
2. **Database Systems: The Complete Book**  
   Hector Garcia-Molina, Ivan Martinez, and Jose Valenza  
   https://www.db-book.com/  
   *Justification:* Offers comprehensive coverage of database systems, including data modeling, query optimization, and cross-row comparisons.
3. **Query Optimization**  
   Microsoft Docs  
   https://docs.microsoft.com/en-us/sql/relational-databases/query-optimization/  
   *Justification:* Discusses query optimization techniques, including those relevant to cross-row comparisons.
4. **Cross-Row Comparisons in SQL**  
   Oracle Documentation  
   https://docs.oracle.com/en/database/oracle/oracle-database/21/sqlrf/Cross-Row-Correlation.html  
   *Justification:* Provides specific guidance on cross-row comparisons in SQL, including the use of INCLUDE.
5. **Data Analysis Patterns**  
   Data Analysis Patterns  
   https://dataanalysispatterns.readthedocs.io/en/latest/  
   *Justification:* Offers patterns and best practices for data analysis, including those applicable to cross-row comparisons.

> [!IMPORTANT]
> These references are normative unless explicitly marked as informative.

## 12. Change Log

| Version | Date | Description |
|---------|------|-------------|
| 1.0 | 2026-01-31 | Initial documentation |

---

This documentation provides a comprehensive overview of INCLUDE for cross-row comparisons, covering its purpose, conceptual model, terminology, core concepts, standard model, common patterns, anti-patterns, edge cases, and related topics. It is designed to serve as a stable reference for understanding and applying INCLUDE in data analysis and query construction.