# 3.1 Tableau Relationships

Canonical documentation for 3.1 Tableau Relationships. This document defines the conceptual model, terminology, constraints, and standard usage patterns.

> [!NOTE]
> This documentation is implementation-agnostic and intended to serve as a stable reference.

## 1. Purpose and Problem Space

Tableau relationships exist to facilitate the integration and analysis of data from multiple tables within a data visualization or business intelligence context. The class of problems it addresses includes data joining, filtering, and aggregation across different data sources. When misunderstood or inconsistently applied, Tableau relationships can lead to incorrect data analysis, inefficient data processing, and poor data visualization. The risks or failures that arise from this misunderstanding include data inconsistencies, performance issues, and incorrect business decisions.

## 2. Conceptual Overview

The major conceptual components of Tableau relationships include data tables, join types, and relationship rules. These components relate to one another through the establishment of relationships between tables, which enable the integration of data from multiple sources. The outcomes the model is designed to produce include accurate and efficient data analysis, flexible data visualization, and informed business decision-making.

## 3. Scope and Non-Goals

Clarify the explicit boundaries of this documentation.

**In scope:**
* Data table structures
* Join types (inner, outer, left, right, full outer)
* Relationship rules (e.g., data blending, join calculations)

**Out of scope:**
* Tool-specific implementations (e.g., Tableau Desktop, Tableau Server)
* Vendor-specific behavior (e.g., database management systems)
* Operational or procedural guidance (e.g., data governance, data quality)

> [!IMPORTANT]
> Out-of-scope items may be addressed in companion or derivative documentation.

## 4. Terminology and Definitions

Provide precise, stable definitions for all key terms used throughout this document.

| Term | Definition |
|------|------------|
| Data Table | A collection of related data, organized into rows and columns. |
| Join | A operation that combines rows from two or more tables based on a related column. |
| Relationship | A connection between two or more tables, enabling data integration and analysis. |
| Data Blending | A technique used to combine data from multiple tables, using a common column. |
| Join Calculation | A calculation that is performed on the joined data, to produce a new column or value. |

> [!TIP]
> Definitions should avoid contextual or time-bound language and remain valid as the ecosystem evolves.

## 5. Core Concepts

Explain the fundamental ideas that form the basis of this topic.

### 5.1 Data Tables
Data tables are the foundation of Tableau relationships, providing the structure and content for data analysis. Each data table has a unique set of columns and rows, which are used to establish relationships with other tables.

### 5.2 Join Types
Join types determine how data is combined from multiple tables. Common join types include inner, outer, left, right, and full outer joins. Each join type has its own set of rules and constraints, which affect the resulting data.

### 5.3 Concept Interactions and Constraints
The core concepts of data tables and join types interact through the establishment of relationships. These relationships are subject to constraints, such as data types, null values, and join conditions. The interactions between data tables and join types must be carefully managed to ensure accurate and efficient data analysis.

## 6. Standard Model

Describe the generally accepted or recommended model for this topic.

### 6.1 Model Description
The standard model for Tableau relationships involves establishing relationships between data tables using join types and relationship rules. This model enables the integration of data from multiple sources, facilitating accurate and efficient data analysis.

### 6.2 Assumptions
The standard model assumes that data tables are properly structured, with consistent data types and formatting. It also assumes that join conditions are well-defined and consistent.

### 6.3 Invariants
The standard model has several invariants, including:
* Data tables must have a unique primary key.
* Join conditions must be based on common columns.
* Relationship rules must be consistently applied.

> [!IMPORTANT]
> Deviations from the standard model must be explicitly documented and justified.

## 7. Common Patterns

Document recurring, accepted patterns associated with this topic.

### Pattern A: Data Blending
- **Intent:** To combine data from multiple tables, using a common column.
- **Context:** When data is spread across multiple tables, and needs to be integrated for analysis.
- **Tradeoffs:** Data blending can improve data analysis, but may also increase complexity and processing time.

## 8. Anti-Patterns

Describe common but discouraged practices.

> [!WARNING]
> These anti-patterns frequently lead to correctness, maintainability, or scalability issues.

### Anti-Pattern A: Over-Joining
- **Description:** Joining too many tables, resulting in complex and inefficient relationships.
- **Failure Mode:** Over-joining can lead to performance issues, data inconsistencies, and incorrect analysis.
- **Common Causes:** Lack of data governance, inadequate data modeling, and insufficient testing.

## 9. Edge Cases and Boundary Conditions

Explain unusual or ambiguous scenarios that may challenge the standard model.

> [!CAUTION]
> Edge cases are often under-documented and a common source of incorrect assumptions.

* Handling null values in join conditions
* Managing data type inconsistencies across tables
* Dealing with circular relationships between tables

## 10. Related Topics

List adjacent, dependent, or prerequisite topics.

* Data modeling
* Data governance
* Data quality
* Business intelligence

## 11. References

Provide exactly **five** authoritative external references that substantiate or inform this topic.

1. **Tableau Relationships**  
   Tableau Software  
   https://help.tableau.com/current/pro/desktop/en-us/relationships.htm  
   *Justification:* Official Tableau documentation on relationships.
2. **Data Blending in Tableau**  
   Tableau Software  
   https://help.tableau.com/current/pro/desktop/en-us/data_blending.htm  
   *Justification:* Official Tableau documentation on data blending.
3. **Joining Tables in Tableau**  
   Tableau Software  
   https://help.tableau.com/current/pro/desktop/en-us/joining_tables.htm  
   *Justification:* Official Tableau documentation on joining tables.
4. **Data Modeling for Business Intelligence**  
   Microsoft  
   https://docs.microsoft.com/en-us/power-bi/guidance/data-modeling  
   *Justification:* Microsoft documentation on data modeling for business intelligence.
5. **Data Governance and Quality**  
   IBM  
   https://www.ibm.com/analytics/data-governance  
   *Justification:* IBM documentation on data governance and quality.

> [!IMPORTANT]
> These references are normative unless explicitly marked as informative.

> [!CAUTION]
> If fewer than five authoritative references exist, explicitly state this.

## 12. Change Log

| Version | Date | Description |
|---------|------|-------------|
| 1.0 | 2026-01-30 | Initial documentation |

---

This documentation provides a comprehensive overview of Tableau relationships, including conceptual models, terminology, constraints, and standard usage patterns. It serves as a stable reference for understanding and implementing Tableau relationships in a variety of contexts.