# Conformed vs non-conformed dimensions

Canonical documentation for Conformed vs non-conformed dimensions. This document defines the conceptual model, terminology, constraints, and standard usage patterns.

> [!NOTE]
> This documentation is implementation-agnostic and intended to serve as a stable reference.

## 1. Purpose and Problem Space

The concept of conformed vs non-conformed dimensions exists to address the challenges of data integration and consistency in data warehousing and business intelligence. The class of problems it addresses includes data inconsistencies, inaccuracies, and incompleteness that arise when data from different sources is combined without proper standardization. The risks or failures that arise when this concept is misunderstood or inconsistently applied include incorrect reporting, poor decision-making, and decreased trust in the data. This documentation aims to provide a clear understanding of conformed and non-conformed dimensions, their differences, and the importance of conformed dimensions in ensuring data consistency and accuracy.

## 2. Conceptual Overview

The conceptual model of conformed vs non-conformed dimensions consists of two major components: conformed dimensions and non-conformed dimensions. Conformed dimensions refer to standardized dimensions that have been designed to be consistent across multiple data sources, ensuring that data can be accurately combined and analyzed. Non-conformed dimensions, on the other hand, refer to dimensions that have not been standardized and may have different structures, formats, or meanings across different data sources. The outcome of this model is to produce a unified view of the data, enabling accurate and consistent reporting and analysis.

## 3. Scope and Non-Goals

**In scope:**
* Definition and explanation of conformed and non-conformed dimensions
* Importance of conformed dimensions in data warehousing and business intelligence
* Standardization of dimensions across multiple data sources

**Out of scope:**
* Tool-specific implementations of conformed dimensions
* Vendor-specific behavior and recommendations
* Operational or procedural guidance for implementing conformed dimensions

> [!IMPORTANT]
> Out-of-scope items may be addressed in companion or derivative documentation.

## 4. Terminology and Definitions

| Term | Definition |
|------|------------|
| Conformed Dimension | A standardized dimension that has been designed to be consistent across multiple data sources, ensuring that data can be accurately combined and analyzed. |
| Non-Conformed Dimension | A dimension that has not been standardized and may have different structures, formats, or meanings across different data sources. |
| Dimension | A category or attribute of data that provides context and meaning, such as time, geography, or product. |
| Data Warehouse | A centralized repository that stores data from multiple sources, providing a single, unified view of the data. |

> [!TIP]
> Definitions should avoid contextual or time-bound language and remain valid as the ecosystem evolves.

## 5. Core Concepts

### 5.1 Conformed Dimensions
Conformed dimensions are standardized dimensions that have been designed to be consistent across multiple data sources. They provide a common language and framework for analyzing and reporting data, ensuring that data can be accurately combined and analyzed.

### 5.2 Non-Conformed Dimensions
Non-conformed dimensions are dimensions that have not been standardized and may have different structures, formats, or meanings across different data sources. They can lead to data inconsistencies, inaccuracies, and incompleteness, making it challenging to analyze and report data.

### 5.3 Concept Interactions and Constraints
Conformed dimensions interact with non-conformed dimensions by providing a standardized framework for analyzing and reporting data. The constraints of conformed dimensions include the need for standardization, consistency, and accuracy, while non-conformed dimensions are often characterized by a lack of standardization, inconsistencies, and inaccuracies.

## 6. Standard Model

### 6.1 Model Description
The standard model for conformed vs non-conformed dimensions consists of a centralized data warehouse that stores data from multiple sources, with conformed dimensions providing a standardized framework for analyzing and reporting data. The model assumes that data is integrated and transformed into a consistent format, enabling accurate and consistent reporting and analysis.

### 6.2 Assumptions
The assumptions under which the model is valid include:
* Data is available from multiple sources
* Data is integrated and transformed into a consistent format
* Conformed dimensions are standardized and consistent across multiple data sources

### 6.3 Invariants
The properties that must always hold true within the model include:
* Conformed dimensions are consistent across multiple data sources
* Data is accurately combined and analyzed using conformed dimensions
* Non-conformed dimensions are identified and addressed through standardization and transformation

> [!IMPORTANT]
> Deviations from the standard model must be explicitly documented and justified.

## 7. Common Patterns

### Pattern A: Standardizing Dimensions
- **Intent:** To provide a standardized framework for analyzing and reporting data
- **Context:** When integrating data from multiple sources
- **Tradeoffs:** Requires upfront investment in standardization, but enables accurate and consistent reporting and analysis

## 8. Anti-Patterns

### Anti-Pattern A: Using Non-Conformed Dimensions
- **Description:** Using non-conformed dimensions without standardization or transformation
- **Failure Mode:** Leads to data inconsistencies, inaccuracies, and incompleteness
- **Common Causes:** Lack of standardization, inadequate data integration, and insufficient data transformation

## 9. Edge Cases and Boundary Conditions

Edge cases and boundary conditions that may challenge the standard model include:
* Handling missing or null values in conformed dimensions
* Addressing inconsistencies in non-conformed dimensions
* Integrating data from sources with different data types or formats

> [!CAUTION]
> Edge cases are often under-documented and a common source of incorrect assumptions.

## 10. Related Topics

Related topics include:
* Data warehousing and business intelligence
* Data integration and transformation
* Data governance and quality

## 11. References

1. **Data Warehouse Design**  
   Ralph Kimball  
   https://www.kimballgroup.com/data-warehouse-design/  
   *Justification:* Provides a comprehensive overview of data warehouse design, including the importance of conformed dimensions.
2. **The Data Warehouse Toolkit**  
   Ralph Kimball and Margy Ross  
   https://www.kimballgroup.com/data-warehouse-toolkit/  
   *Justification:* Offers practical guidance on designing and implementing data warehouses, including the use of conformed dimensions.
3. **Data Governance**  
   Data Governance Institute  
   https://www.datagovernance.com/  
   *Justification:* Provides a framework for data governance, including the importance of standardization and conformed dimensions.
4. **Data Quality**  
   Data Quality Solutions  
   https://www.dataqualitysolutions.com/  
   *Justification:* Offers guidance on ensuring data quality, including the use of conformed dimensions to prevent data inconsistencies.
5. **Business Intelligence**  
   Business Intelligence Solutions  
   https://www.businessintelligencesolutions.com/  
   *Justification:* Provides an overview of business intelligence, including the importance of conformed dimensions in enabling accurate and consistent reporting and analysis.

> [!IMPORTANT]
> These references are normative unless explicitly marked as informative.

## 12. Change Log

| Version | Date | Description |
|---------|------|-------------|
| 1.0 | 2026-01-30 | Initial documentation |

---

Note: This documentation is a comprehensive guide to conformed vs non-conformed dimensions, providing a clear understanding of the concepts, terminology, and standard model. It is intended to serve as a stable reference for data warehousing and business intelligence professionals.