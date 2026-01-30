# Multi-fact modeling

Canonical documentation for Multi-fact modeling. This document defines the conceptual model, terminology, constraints, and standard usage patterns.

> [!NOTE]
> This documentation is implementation-agnostic and intended to serve as a stable reference.

## 1. Purpose and Problem Space

Multi-fact modeling exists to address the complexities of representing and analyzing complex, multifaceted data in various domains, including business, science, and engineering. The class of problems it addresses includes data integration, data warehousing, and business intelligence. When multi-fact modeling is misunderstood or inconsistently applied, risks and failures arise, such as data inconsistencies, incorrect analysis, and poor decision-making. Inconsistent or incomplete data models can lead to incorrect insights, which in turn can result in suboptimal business strategies or incorrect scientific conclusions.

## 2. Conceptual Overview

The high-level mental model of multi-fact modeling consists of three major conceptual components: facts, dimensions, and hierarchies. Facts represent measurable events or phenomena, dimensions provide context for facts, and hierarchies define the relationships between dimensions. These components relate to one another through a star or snowflake schema, where facts are connected to dimensions, and dimensions are connected to each other through hierarchies. The outcomes of multi-fact modeling include a unified, consistent view of data, support for complex analysis and querying, and improved decision-making capabilities.

## 3. Scope and Non-Goals

Clarify the explicit boundaries of this documentation.

**In scope:**
* Conceptual foundations of multi-fact modeling
* Terminology and definitions
* Core concepts, including facts, dimensions, and hierarchies
* Standard model and common patterns

**Out of scope:**
* Tool-specific implementations, such as data warehousing software or business intelligence tools
* Vendor-specific behavior, such as proprietary data models or query languages
* Operational or procedural guidance, such as data governance or data quality management

> [!IMPORTANT]
> Out-of-scope items may be addressed in companion or derivative documentation.

## 4. Terminology and Definitions

Provide precise, stable definitions for all key terms used throughout this document.

| Term | Definition |
|------|------------|
| Fact | A measurable event or phenomenon, represented as a set of values |
| Dimension | A context for a fact, providing additional information about the fact |
| Hierarchy | A relationship between dimensions, defining a tree-like structure |
| Star Schema | A data model where a fact table is connected to dimension tables through foreign keys |
| Snowflake Schema | A data model where dimension tables are connected to each other through foreign keys, forming a more complex structure |

> [!TIP]
> Definitions should avoid contextual or time-bound language and remain valid as the ecosystem evolves.

## 5. Core Concepts

Explain the fundamental ideas that form the basis of this topic.

### 5.1 Facts
Facts represent measurable events or phenomena, such as sales transactions or website clicks. They are the core of the multi-fact model, providing the data for analysis and querying.

### 5.2 Dimensions
Dimensions provide context for facts, such as date, location, or product information. They help to filter, group, and analyze facts.

### 5.3 Concept Interactions and Constraints
Facts are connected to dimensions through foreign keys, and dimensions are connected to each other through hierarchies. The relationships between facts and dimensions are typically one-to-many, while the relationships between dimensions are typically many-to-one. Constraints, such as data types and nullability, are applied to facts and dimensions to ensure data consistency and quality.

## 6. Standard Model

Describe the generally accepted or recommended model for this topic.

### 6.1 Model Description
The standard model for multi-fact modeling is a star or snowflake schema, where a fact table is connected to dimension tables through foreign keys. The fact table contains the measurable events or phenomena, while the dimension tables provide context for the facts.

### 6.2 Assumptions
The standard model assumes that the data is structured and consistent, with well-defined facts and dimensions. It also assumes that the data is properly normalized, with minimal data redundancy.

### 6.3 Invariants
The standard model defines several invariants, including:
* Each fact is connected to at least one dimension
* Each dimension is connected to at least one fact
* The relationships between facts and dimensions are consistent and well-defined

> [!IMPORTANT]
> Deviations from the standard model must be explicitly documented and justified.

## 7. Common Patterns

Document recurring, accepted patterns associated with this topic.

### Pattern A: Star Schema
- **Intent:** To provide a simple, efficient data model for analysis and querying
- **Context:** When the data is relatively simple, with few dimensions and hierarchies
- **Tradeoffs:** Easy to implement and maintain, but may not support complex analysis or large amounts of data

### Pattern B: Snowflake Schema
- **Intent:** To provide a more complex, flexible data model for analysis and querying
- **Context:** When the data is complex, with many dimensions and hierarchies
- **Tradeoffs:** Supports complex analysis and large amounts of data, but may be more difficult to implement and maintain

## 8. Anti-Patterns

Describe common but discouraged practices.

> [!WARNING]
> These anti-patterns frequently lead to correctness, maintainability, or scalability issues.

### Anti-Pattern A: Denormalization
- **Description:** Storing redundant data in multiple tables, leading to data inconsistencies and maintenance issues
- **Failure Mode:** Data inconsistencies, poor performance, and maintenance issues
- **Common Causes:** Lack of understanding of data modeling principles, poor design, or inadequate testing

## 9. Edge Cases and Boundary Conditions

Explain unusual or ambiguous scenarios that may challenge the standard model.

> [!CAUTION]
> Edge cases are often under-documented and a common source of incorrect assumptions.

### Edge Case A: Handling Null Values
- **Description:** Null values in facts or dimensions, which can lead to data inconsistencies and analysis issues
- **Resolution:** Define clear rules for handling null values, such as using default values or ignoring null values

## 10. Related Topics

List adjacent, dependent, or prerequisite topics.

* Data warehousing
* Business intelligence
* Data governance
* Data quality management

## 11. References

Provide exactly **five** authoritative external references that substantiate or inform this topic.

1. **Data Warehousing for Dummies**  
   John Wiley & Sons  
   https://www.wiley.com/en-us/Data+Warehousing+For+Dummies-p-9781118993834  
   *Justification:* A comprehensive guide to data warehousing, including multi-fact modeling.
2. **The Data Warehouse Toolkit**  
   Ralph Kimball  
   https://www.kimballgroup.com/data-warehouse-toolkit/  
   *Justification:* A classic reference on data warehousing and multi-fact modeling.
3. **Star and Snowflake Schema**  
   IBM Knowledge Center  
   https://www.ibm.com/support/knowledgecenter/en/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0059255.html  
   *Justification:* A technical reference on star and snowflake schema, including design and implementation guidelines.
4. **Data Modeling Made Simple**  
   Steve Hoberman  
   https://www.stevehoberman.com/data-modeling-made-simple/  
   *Justification:* A practical guide to data modeling, including multi-fact modeling.
5. **The Official Microsoft SQL Server Documentation**  
   Microsoft  
   https://docs.microsoft.com/en-us/sql/sql-server/?view=sql-server-ver15  
   *Justification:* A comprehensive reference on SQL Server, including data modeling and multi-fact modeling.

> [!IMPORTANT]
> These references are normative unless explicitly marked as informative.

> [!CAUTION]
> If fewer than five authoritative references exist, explicitly state this.

## 12. Change Log

| Version | Date | Description |
|---------|------|-------------|
| 1.0 | 2026-01-30 | Initial documentation |

---

Note: This documentation is a comprehensive guide to multi-fact modeling, covering the conceptual model, terminology, constraints, and standard usage patterns. It is intended to serve as a stable reference for data modeling and analysis.