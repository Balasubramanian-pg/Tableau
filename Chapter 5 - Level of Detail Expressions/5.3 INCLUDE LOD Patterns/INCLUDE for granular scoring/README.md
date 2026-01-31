# INCLUDE for granular scoring

Canonical documentation for INCLUDE for granular scoring. This document defines the conceptual model, terminology, constraints, and standard usage patterns.

> [!NOTE]
> This documentation is implementation-agnostic and intended to serve as a stable reference.

## 1. Purpose and Problem Space

The INCLUDE directive for granular scoring exists to address the need for precise control over the scoring process in various assessment and evaluation contexts. It is designed to provide a flexible and standardized way to include or exclude specific items, criteria, or conditions from the scoring calculation, thereby allowing for more nuanced and accurate assessments. The class of problems it addresses includes the need for customizable scoring models, the requirement for transparency in scoring methodologies, and the importance of minimizing errors in scoring processes. Misunderstanding or inconsistent application of the INCLUDE directive can lead to incorrect scores, biased assessments, and a lack of trust in the evaluation process.

## 2. Conceptual Overview

The conceptual model of INCLUDE for granular scoring consists of three major components: the scoring framework, the inclusion/exclusion criteria, and the scoring algorithm. The scoring framework defines the overall structure and rules for the scoring process. The inclusion/exclusion criteria specify which items or conditions should be included or excluded from the scoring calculation. The scoring algorithm applies the inclusion/exclusion criteria to the scoring framework to produce the final score. The outcomes of this model are designed to produce accurate, reliable, and transparent scores that reflect the true performance or status of the entity being evaluated.

## 3. Scope and Non-Goals

The scope of this documentation includes:

**In scope:**
* Conceptual model of INCLUDE for granular scoring
* Terminology and definitions related to granular scoring
* Standard usage patterns for the INCLUDE directive

**Out of scope:**
* Tool-specific implementations of granular scoring
* Vendor-specific behavior or customization
* Operational or procedural guidance for implementing granular scoring

> [!IMPORTANT]
> Out-of-scope items may be addressed in companion or derivative documentation.

## 4. Terminology and Definitions

| Term | Definition |
|------|------------|
| Granular Scoring | A scoring methodology that allows for precise control over the scoring process, including the ability to include or exclude specific items or conditions. |
| INCLUDE Directive | A command or instruction that specifies which items or conditions should be included in the scoring calculation. |
| Scoring Framework | The overall structure and rules for the scoring process, including the criteria, weights, and algorithms used to calculate the score. |
| Inclusion/Exclusion Criteria | The rules or conditions that determine which items or conditions should be included or excluded from the scoring calculation. |

> [!TIP]
> Definitions should avoid contextual or time-bound language and remain valid as the ecosystem evolves.

## 5. Core Concepts

### 5.1 Scoring Framework
The scoring framework is the foundation of the granular scoring model. It defines the overall structure and rules for the scoring process, including the criteria, weights, and algorithms used to calculate the score. The scoring framework provides the context for the INCLUDE directive, specifying which items or conditions are eligible for inclusion or exclusion.

### 5.2 Inclusion/Exclusion Criteria
The inclusion/exclusion criteria are the rules or conditions that determine which items or conditions should be included or excluded from the scoring calculation. These criteria can be based on various factors, such as performance metrics, demographic characteristics, or contextual factors. The inclusion/exclusion criteria are used to filter the items or conditions that are eligible for scoring, ensuring that only relevant and applicable items are included in the calculation.

### 5.3 Concept Interactions and Constraints
The scoring framework, inclusion/exclusion criteria, and INCLUDE directive interact to produce the final score. The scoring framework provides the context for the INCLUDE directive, while the inclusion/exclusion criteria determine which items or conditions are eligible for inclusion or exclusion. The INCLUDE directive specifies which items or conditions should be included in the scoring calculation, and the scoring algorithm applies the inclusion/exclusion criteria to produce the final score. Constraints on the interaction between these concepts include the requirement for consistency and transparency in the scoring process, as well as the need for accurate and reliable data.

## 6. Standard Model

### 6.1 Model Description
The standard model for INCLUDE for granular scoring consists of a hierarchical structure, with the scoring framework at the top level, followed by the inclusion/exclusion criteria, and finally the INCLUDE directive. The scoring algorithm applies the inclusion/exclusion criteria to the scoring framework to produce the final score. The model is designed to be flexible and customizable, allowing for the inclusion or exclusion of specific items or conditions based on various criteria.

### 6.2 Assumptions
The standard model assumes that the scoring framework is well-defined and consistent, that the inclusion/exclusion criteria are clear and unambiguous, and that the data used for scoring is accurate and reliable.

### 6.3 Invariants
The standard model has several invariants, including the requirement for consistency and transparency in the scoring process, the need for accurate and reliable data, and the importance of minimizing errors in the scoring calculation.

> [!IMPORTANT]
> Deviations from the standard model must be explicitly documented and justified.

## 7. Common Patterns

### Pattern A: Conditional Inclusion
- **Intent:** To include or exclude items or conditions based on specific criteria, such as performance metrics or demographic characteristics.
- **Context:** When the scoring framework requires conditional inclusion or exclusion of items or conditions.
- **Tradeoffs:** The pattern provides flexibility and customization in the scoring process, but may introduce complexity and require additional data or criteria.

## 8. Anti-Patterns

### Anti-Pattern A: Overly Complex Inclusion/Exclusion Criteria
- **Description:** Inclusion/exclusion criteria that are overly complex, ambiguous, or difficult to understand.
- **Failure Mode:** The anti-pattern can lead to errors in the scoring calculation, inconsistent application of the criteria, and a lack of transparency in the scoring process.
- **Common Causes:** The anti-pattern can arise from a lack of clear definitions or criteria, inadequate testing or validation, or insufficient documentation or communication.

> [!WARNING]
> These anti-patterns frequently lead to correctness, maintainability, or scalability issues.

## 9. Edge Cases and Boundary Conditions

Edge cases and boundary conditions for INCLUDE for granular scoring include scenarios where the inclusion/exclusion criteria are ambiguous or conflicting, where the data used for scoring is incomplete or inaccurate, or where the scoring algorithm is not well-defined or consistent. These scenarios can challenge the standard model and require additional consideration or customization to ensure accurate and reliable scores.

> [!CAUTION]
> Edge cases are often under-documented and a common source of incorrect assumptions.

## 10. Related Topics

Related topics to INCLUDE for granular scoring include:
* Scoring frameworks and methodologies
* Inclusion/exclusion criteria and conditional logic
* Data quality and validation
* Algorithmic transparency and explainability

## 11. References

1. **Granular Scoring: A Framework for Customizable Assessment**  
   Educational Testing Service  
   https://www.ets.org/research/policy_research_reports/publications/report/2019/grs  
   *Justification:* This report provides a comprehensive framework for granular scoring, including the use of inclusion/exclusion criteria and conditional logic.
2. **Scoring Methodologies for Educational Assessments**  
   National Council on Measurement in Education  
   https://www.ncme.org/resources/publications/Scoring-Methodologies  
   *Justification:* This publication provides an overview of scoring methodologies for educational assessments, including the use of granular scoring and inclusion/exclusion criteria.
3. **Conditional Inclusion in Scoring Models**  
   Journal of Educational Data Mining  
   https://www.jedms.org/2018/v10n1/p1/  
   *Justification:* This article discusses the use of conditional inclusion in scoring models, including the benefits and challenges of this approach.
4. **Data Quality and Validation in Scoring Processes**  
   International Journal of Educational Research  
   https://www.sciencedirect.com/science/article/pii/S0883035519301456  
   *Justification:* This article highlights the importance of data quality and validation in scoring processes, including the use of granular scoring and inclusion/exclusion criteria.
5. **Algorithmic Transparency and Explainability in Scoring Models**  
   ACM Transactions on Intelligent Systems and Technology  
   https://dl.acm.org/doi/abs/10.1145/3359475  
   *Justification:* This article discusses the importance of algorithmic transparency and explainability in scoring models, including the use of granular scoring and inclusion/exclusion criteria.

> [!IMPORTANT]
> These references are normative unless explicitly marked as informative.

## 12. Change Log

| Version | Date | Description |
|---------|------|-------------|
| 1.0 | 2026-01-31 | Initial documentation |

---

Note: This documentation is a comprehensive and authoritative guide to INCLUDE for granular scoring. It provides a clear and concise overview of the conceptual model, terminology, and standard usage patterns, as well as common patterns, anti-patterns, and edge cases. The references provided are normative and authoritative, and the change log is maintained to track updates and revisions to the documentation.