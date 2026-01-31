# INCLUDE with dimensions vs measures

Canonical documentation for INCLUDE with dimensions vs measures. This document defines the conceptual model, terminology, constraints, and standard usage patterns.

> [!NOTE]
> This documentation is implementation-agnostic and intended to serve as a stable reference.

## 1. Purpose and Problem Space

The topic of INCLUDE with dimensions vs measures exists to address the complexities and nuances of data modeling, particularly in the context of business intelligence, data warehousing, and analytics. It aims to provide clarity on when to use INCLUDE with dimensions and when to use measures, and how these choices impact the overall data model and its usability. The class of problems it addresses includes data inconsistency, query performance issues, and difficulties in maintaining data integrity. Misunderstanding or inconsistent application of these concepts can lead to incorrect data analysis, poor decision-making, and significant maintenance overhead.

## 2. Conceptual Overview

The high-level mental model of INCLUDE with dimensions vs measures involves understanding the roles of dimensions and measures within a data model. Dimensions are descriptive categories used to analyze data (e.g., time, geography, product), while measures are quantitative values that are analyzed (e.g., sales, revenue, count). The INCLUDE clause is used to specify which dimensions or measures to include in a query or data model. The major conceptual components are:
- **Dimensions**: These provide the context for analysis.
- **Measures**: These are the values being analyzed.
- **INCLUDE Clause**: This determines what dimensions or measures are included.

These components relate to one another in that dimensions provide the framework for analyzing measures. The outcome the model is designed to produce is a robust, scalable, and maintainable data model that supports accurate and efficient data analysis.

## 3. Scope and Non-Goals

Clarify the explicit boundaries of this documentation.

**In scope:**
* Conceptual differences between dimensions and measures
* Usage patterns for INCLUDE with dimensions vs measures
* Best practices for data modeling

**Out of scope:**
* Tool-specific implementations (e.g., SQL Server, Oracle)
* Vendor-specific behavior
* Operational or procedural guidance (e.g., how to deploy a data model)

> [!IMPORTANT]
> Out-of-scope items may be addressed in companion or derivative documentation.

## 4. Terminology and Definitions

Provide precise, stable definitions for all key terms used throughout this document.

| Term | Definition |
|------|------------|
| Dimension | A descriptive category used for analysis (e.g., time, geography). |
| Measure | A quantitative value that is analyzed (e.g., sales, revenue). |
| INCLUDE Clause | A clause used to specify which dimensions or measures to include in a query or data model. |
| Data Model | A conceptual representation of the data, including its structure and relationships. |

> [!TIP]
> Definitions should avoid contextual or time-bound language and remain valid as the ecosystem evolves.

## 5. Core Concepts

Explain the fundamental ideas that form the basis of this topic.

### 5.1 Dimensions
Dimensions provide the context for analysis. They are typically categorical and are used to group or filter data. Examples include time (year, quarter, month), geography (country, region, city), and product categories.

### 5.2 Measures
Measures are the quantitative values being analyzed. They can be simple counts or more complex calculations like sums, averages, or ratios. Measures are often associated with specific dimensions, allowing for analysis across different contexts.

### 5.3 Concept Interactions and Constraints
Dimensions and measures interact in that dimensions provide the framework for analyzing measures. For example, analyzing sales (a measure) by region (a dimension) allows for insights into how sales performance varies geographically. Constraints include data integrity rules (e.g., ensuring each sale is associated with a valid region) and query performance considerations (e.g., optimizing queries to efficiently handle large datasets).

## 6. Standard Model

Describe the generally accepted or recommended model for this topic.

### 6.1 Model Description
The standard model involves clearly distinguishing between dimensions and measures and using the INCLUDE clause judiciously to specify which dimensions or measures are relevant for a particular analysis or data model. This approach ensures clarity, maintainability, and scalability of the data model.

### 6.2 Assumptions
Assumptions under which the model is valid include:
- Data is properly normalized and structured.
- Dimensions and measures are correctly identified and defined.
- The INCLUDE clause is used consistently and appropriately.

### 6.3 Invariants
Properties that must always hold true within the model include:
- Each measure is associated with at least one dimension.
- Each dimension has a clear and consistent definition.
- The INCLUDE clause does not contradict the data model's structure.

> [!IMPORTANT]
> Deviations from the standard model must be explicitly documented and justified.

## 7. Common Patterns

Document recurring, accepted patterns associated with this topic.

### Pattern A: Star Schema
- **Intent:** To optimize query performance by minimizing the number of joins required.
- **Context:** Data warehousing and business intelligence applications.
- **Tradeoffs:** Simplifies queries but may increase data redundancy.

## 8. Anti-Patterns

Describe common but discouraged practices.

> [!WARNING]
> These anti-patterns frequently lead to correctness, maintainability, or scalability issues.

### Anti-Pattern A: Mixing Dimensions and Measures
- **Description:** Incorrectly treating measures as dimensions or vice versa.
- **Failure Mode:** Leads to incorrect analysis and query results.
- **Common Causes:** Lack of clear definitions or misunderstanding of the data model.

## 9. Edge Cases and Boundary Conditions

Explain unusual or ambiguous scenarios that may challenge the standard model.

> [!CAUTION]
> Edge cases are often under-documented and a common source of incorrect assumptions.

Examples include handling null or missing values in dimensions or measures, and dealing with dimensions that have a large number of unique values.

## 10. Related Topics

List adjacent, dependent, or prerequisite topics.
- Data Modeling
- Business Intelligence
- Data Warehousing
- SQL and Query Optimization

## 11. References

Provide exactly **five** authoritative external references that substantiate or inform this topic.

1. **Data Warehousing for Dummies**  
   Oracle Corporation  
   https://www.oracle.com/technical-resources/articles/data-warehousing-for-dummies.html  
   *Justification:* Provides a foundational understanding of data warehousing concepts, including dimensions and measures.
2. **SQL Server Documentation: Using the INCLUDE Clause**  
   Microsoft Corporation  
   https://docs.microsoft.com/en-us/sql/relational-databases/indexes/create-indexes-with-included-columns?view=sql-server-ver15  
   *Justification:* Offers detailed guidance on using the INCLUDE clause in SQL Server.
3. **Kimball Group: Dimensional Modeling Techniques**  
   The Kimball Group  
   https://www.kimballgroup.com/data-warehouse-business-intelligence-resources/kimball-techniques/dimensional-modeling-techniques/  
   *Justification:* Presents best practices for dimensional modeling, including the use of dimensions and measures.
4. **Data Modeling Made Simple**  
   Steve Hoberman  
   https://www.data-modeling-made-simple.com/  
   *Justification:* Provides a comprehensive introduction to data modeling, including concepts related to dimensions and measures.
5. **The Data Warehouse Toolkit**  
   Ralph Kimball and Margy Ross  
   https://www.kimballgroup.com/data-warehouse-business-intelligence-resources/books/the-data-warehouse-toolkit/  
   *Justification:* Offers in-depth guidance on designing and implementing data warehouses, including the strategic use of dimensions and measures.

> [!IMPORTANT]
> These references are normative unless explicitly marked as informative.

> [!CAUTION]
> If fewer than five authoritative references exist, explicitly state this. In this case, five relevant references are provided.

## 12. Change Log

| Version | Date | Description |
|---------|------|-------------|
| 1.0 | 2026-01-31 | Initial documentation |

---

This documentation provides a comprehensive overview of INCLUDE with dimensions vs measures, covering conceptual models, terminology, constraints, and standard usage patterns. It serves as a stable reference for understanding and applying these concepts in data modeling and analysis.