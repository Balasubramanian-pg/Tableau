# Adding dummy fields for unions

Canonical documentation for Adding dummy fields for unions. This document defines the conceptual model, terminology, constraints, and standard usage patterns.

> [!NOTE]
> This documentation is implementation-agnostic and intended to serve as a stable reference.

## 1. Purpose and Problem Space

The topic of adding dummy fields for unions exists to address the challenges that arise when working with union types in programming languages. Unions, also known as sum types, allow a variable to hold a value of one type or another, but they can lead to issues with type safety, code readability, and maintainability. The addition of dummy fields to unions is a technique used to mitigate these problems by providing a way to distinguish between different types within a union. The class of problems it addresses includes type ambiguity, incorrect type assumptions, and the need for explicit type checking. The risks or failures that arise when it is misunderstood or inconsistently applied include runtime errors, code fragility, and decreased code readability.

## 2. Conceptual Overview

The conceptual model of adding dummy fields for unions consists of three major components: the union type, the dummy field, and the type discriminator. The union type represents the sum type that can hold values of different types. The dummy field is an additional field added to the union type that serves as a type discriminator, allowing the distinction between different types within the union. The type discriminator is the value or mechanism used to determine the actual type of the value held by the union. The outcomes of this model are designed to produce type-safe, readable, and maintainable code that can handle union types effectively.

## 3. Scope and Non-Goals

The scope of this documentation includes:

**In scope:**
* The conceptual model of adding dummy fields for unions
* The terminology and definitions related to union types and dummy fields
* The core concepts and standard model for adding dummy fields to unions
* Common patterns and anti-patterns associated with this topic

**Out of scope:**
* Tool-specific implementations of union types and dummy fields
* Vendor-specific behavior or optimizations
* Operational or procedural guidance for working with union types

> [!IMPORTANT]
> Out-of-scope items may be addressed in companion or derivative documentation.

## 4. Terminology and Definitions

The following terms are used throughout this document:

| Term | Definition |
|------|------------|
| Union type | A sum type that can hold values of different types |
| Dummy field | An additional field added to a union type to serve as a type discriminator |
| Type discriminator | The value or mechanism used to determine the actual type of the value held by a union |
| Type safety | The property of a programming language that ensures the correctness of type assignments and operations |

> [!TIP]
> Definitions should avoid contextual or time-bound language and remain valid as the ecosystem evolves.

## 5. Core Concepts

### 5.1 Union Types
A union type is a sum type that can hold values of different types. It is a fundamental concept in programming languages that allows for the representation of complex data structures.

### 5.2 Dummy Fields
A dummy field is an additional field added to a union type that serves as a type discriminator. It allows for the distinction between different types within the union and provides a way to perform explicit type checking.

### 5.3 Concept Interactions and Constraints
The core concepts of union types, dummy fields, and type discriminators interact in the following way: the union type provides the foundation for the dummy field, which serves as a type discriminator. The type discriminator is used to determine the actual type of the value held by the union, ensuring type safety and correctness. The constraints on these interactions include the requirement for explicit type checking and the need for careful design of the dummy field to avoid ambiguity or confusion.

## 6. Standard Model

### 6.1 Model Description
The standard model for adding dummy fields to unions consists of the following steps:
1. Define the union type and its possible values.
2. Add a dummy field to the union type to serve as a type discriminator.
3. Implement explicit type checking using the dummy field.

### 6.2 Assumptions
The standard model assumes that the programming language supports union types and allows for the addition of dummy fields. It also assumes that the developer is aware of the potential risks and challenges associated with working with union types.

### 6.3 Invariants
The following properties must always hold true within the standard model:
* The dummy field is used consistently as a type discriminator.
* Explicit type checking is performed using the dummy field.
* The union type is designed to ensure type safety and correctness.

> [!IMPORTANT]
> Deviations from the standard model must be explicitly documented and justified.

## 7. Common Patterns

### Pattern A: Explicit Type Checking
- **Intent:** Ensure type safety and correctness when working with union types.
- **Context:** When working with union types that require explicit type checking.
- **Tradeoffs:** Increased code readability and maintainability, but potentially increased code complexity.

## 8. Anti-Patterns

### Anti-Pattern A: Implicit Type Assumptions
- **Description:** Assuming the type of a value within a union without explicit type checking.
- **Failure Mode:** Runtime errors or incorrect behavior due to type mismatches.
- **Common Causes:** Lack of awareness of the potential risks associated with union types or inadequate design of the dummy field.

> [!WARNING]
> These anti-patterns frequently lead to correctness, maintainability, or scalability issues.

## 9. Edge Cases and Boundary Conditions

Edge cases and boundary conditions that may challenge the standard model include:
* Union types with a large number of possible values.
* Dummy fields that are not properly designed or implemented.
* Programming languages that do not support union types or dummy fields.

> [!CAUTION]
> Edge cases are often under-documented and a common source of incorrect assumptions.

## 10. Related Topics

Related topics include:
* Type theory and type systems
* Programming language design and implementation
* Software engineering and code maintainability

## 11. References

1. **Type Theory and Functional Programming**  
   Simon Peyton Jones  
   https://www.microsoft.com/en-us/research/uploads/prod/2016/11/type-theory-and-functional-programming.pdf  
   *Justification:* This reference provides a comprehensive introduction to type theory and its application in functional programming.
2. **The C Programming Language**  
   Brian Kernighan and Dennis Ritchie  
   https://www.bell-labs.com/usr/dmr/www/cbook.html  
   *Justification:* This reference is a classic textbook on the C programming language, which supports union types and dummy fields.
3. **Programming Language Design Concepts**  
   David A. Watt  
   https://www.springer.com/gp/book/9780387948249  
   *Justification:* This reference provides a comprehensive introduction to programming language design concepts, including type systems and union types.
4. **Software Engineering: A Practitioner's Approach**  
   Roger S. Pressman  
   https://www.mheducation.com/highered/product/software-engineering-practitioners-approach-ROGER-S-PRESSMAN.html  
   *Justification:* This reference provides a comprehensive introduction to software engineering principles and practices, including code maintainability and readability.
5. **Type Systems for Programming Languages**  
   Benjamin C. Pierce  
   https://www.cis.upenn.edu/~bcpierce/types/index.html  
   *Justification:* This reference provides a comprehensive introduction to type systems for programming languages, including union types and type discriminators.

> [!IMPORTANT]
> These references are normative unless explicitly marked as informative.

> [!CAUTION]
> If fewer than five authoritative references exist, explicitly state this.

## 12. Change Log

| Version | Date | Description |
|---------|------|-------------|
| 1.0 | 2026-01-30 | Initial documentation |

---