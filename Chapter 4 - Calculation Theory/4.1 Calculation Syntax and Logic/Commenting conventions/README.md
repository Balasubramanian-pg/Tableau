# Commenting conventions

Canonical documentation for Commenting conventions. This document defines the conceptual model, terminology, constraints, and standard usage patterns.

> [!NOTE]
> This documentation is implementation-agnostic and intended to serve as a stable reference.

## 1. Purpose and Problem Space

Commenting conventions exist to address the class of problems related to code readability, maintainability, and understandability. Inconsistent or poorly applied commenting conventions can lead to confusion, errors, and difficulties in code maintenance. The risks of misunderstanding or misapplying commenting conventions include decreased code quality, increased debugging time, and reduced collaboration among developers. This documentation aims to provide a clear understanding of commenting conventions to mitigate these risks.

## 2. Conceptual Overview

The conceptual model of commenting conventions consists of three major components: 
1. **Code Comments**: Human-readable annotations added to the code to explain its purpose, functionality, and behavior.
2. **Commenting Styles**: The formatting and structure used for comments, such as block comments, inline comments, and documentation comments.
3. **Commenting Guidelines**: The rules and best practices that dictate when, where, and how comments should be used.

These components relate to one another in that commenting styles provide the structure for code comments, and commenting guidelines dictate the appropriate use of commenting styles. The outcome of this model is to produce high-quality, readable, and maintainable code that effectively communicates its intent and functionality to developers.

## 3. Scope and Non-Goals

The scope of this documentation includes:
* **Commenting styles**: The various formats and structures used for comments in code.
* **Commenting guidelines**: The best practices and rules for using comments effectively.

Out of scope are:
* **Tool-specific implementations**: The specific features and functionalities of commenting tools and software.
* **Vendor-specific behavior**: The unique commenting conventions and requirements of specific vendors or platforms.
* **Operational or procedural guidance**: The step-by-step instructions for implementing commenting conventions in a specific development process.

> [!IMPORTANT]
> Out-of-scope items may be addressed in companion or derivative documentation.

## 4. Terminology and Definitions

| Term | Definition |
|------|------------|
| Code Comment | A human-readable annotation added to the code to explain its purpose, functionality, or behavior. |
| Commenting Style | The formatting and structure used for comments, such as block comments, inline comments, and documentation comments. |
| Commenting Guideline | A rule or best practice that dictates when, where, and how comments should be used. |

> [!TIP]
> Definitions should avoid contextual or time-bound language and remain valid as the ecosystem evolves.

## 5. Core Concepts

### 5.1 Code Comments
Code comments are the fundamental building blocks of commenting conventions. They provide explanations, justifications, and context for the code, making it easier for developers to understand and maintain.

### 5.2 Commenting Styles
Commenting styles refer to the various formats and structures used for comments. Common commenting styles include block comments, inline comments, and documentation comments. Each style has its own strengths and weaknesses, and the choice of style depends on the specific use case and context.

### 5.3 Comment Interactions and Constraints
Comment interactions and constraints refer to the relationships between comments and the code they annotate. Comments should be concise, accurate, and relevant, and should not duplicate information already present in the code. Comments should also be updated when the code changes to ensure consistency and accuracy.

## 6. Standard Model

### 6.1 Model Description
The standard model for commenting conventions consists of a set of guidelines and best practices that dictate when, where, and how comments should be used. The model includes rules for comment formatting, content, and placement, as well as guidelines for maintaining and updating comments.

### 6.2 Assumptions
The standard model assumes that comments are used to explain complex or non-obvious code, to provide context and justification for design decisions, and to facilitate collaboration and knowledge sharing among developers.

### 6.3 Invariants
The standard model includes the following invariants:
* Comments should be concise and to the point.
* Comments should be accurate and up-to-date.
* Comments should not duplicate information already present in the code.

> [!IMPORTANT]
> Deviations from the standard model must be explicitly documented and justified.

## 7. Common Patterns

### Pattern: Commenting Complex Code
- **Intent:** To explain complex or non-obvious code and make it easier to understand and maintain.
- **Context:** When the code is complex, nested, or uses advanced programming concepts.
- **Tradeoffs:** Comments may add overhead and maintenance costs, but they improve code readability and understandability.

## 8. Anti-Patterns

> [!WARNING]
> These anti-patterns frequently lead to correctness, maintainability, or scalability issues.

### Anti-Pattern: Over-Commenting
- **Description:** Adding excessive comments that duplicate information already present in the code or provide unnecessary explanations.
- **Failure Mode:** Over-commenting can lead to comment maintenance overhead, decreased code readability, and increased likelihood of comment-code inconsistencies.
- **Common Causes:** Lack of commenting guidelines, inexperienced developers, or excessive caution.

## 9. Edge Cases and Boundary Conditions

Edge cases and boundary conditions in commenting conventions include situations where comments are used to explain ambiguous or unclear code, or where comments are used to provide context for complex or domain-specific concepts.

> [!CAUTION]
> Edge cases are often under-documented and a common source of incorrect assumptions.

## 10. Related Topics

Related topics include:
* Code review and inspection
* Documentation and knowledge management
* Coding standards and best practices

## 11. References

1. **The Art of Readable Code**  
   Dustin Boswell and Trevor Foucher  
   [https://www.amazon.com/Art-Readable-Code-Practical-Techniques/dp/059680230X](https://www.amazon.com/Art-Readable-Code-Practical-Techniques/dp/059680230X)  
   *Justification:* This book provides practical techniques for writing readable code, including commenting conventions.
2. **Clean Code: A Handbook of Agile Software Craftsmanship**  
   Robert C. Martin  
   [https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)  
   *Justification:* This book provides a comprehensive guide to writing clean, maintainable code, including commenting conventions.
3. **Code Complete: A Practical Handbook of Software Construction**  
   Steve McConnell  
   [https://www.amazon.com/Code-Complete-Practical-Handbook-Construction/dp/0735619670](https://www.amazon.com/Code-Complete-Practical-Handbook-Construction/dp/0735619670)  
   *Justification:* This book provides a practical guide to software construction, including commenting conventions and coding standards.
4. **The Pragmatic Programmer: From Journeyman to Master**  
   Andrew Hunt and David Thomas  
   [https://www.amazon.com/Pragmatic-Programmer-Journeyman-Master/dp/020161622X](https://www.amazon.com/Pragmatic-Programmer-Journeyman-Master/dp/020161622X)  
   *Justification:* This book provides a comprehensive guide to software development best practices, including commenting conventions and coding standards.
5. **IEEE Standard for Software and System Test Documentation**  
   IEEE Computer Society  
   [https://standards.ieee.org/standard/829-2008.html](https://standards.ieee.org/standard/829-2008.html)  
   *Justification:* This standard provides guidelines for software and system test documentation, including commenting conventions and coding standards.

> [!IMPORTANT]
> These references are normative unless explicitly marked as informative.

## 12. Change Log

| Version | Date | Description |
|---------|------|-------------|
| 1.0 | 2026-01-31 | Initial documentation |

---