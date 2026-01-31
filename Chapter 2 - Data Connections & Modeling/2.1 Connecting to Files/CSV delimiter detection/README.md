# CSV delimiter detection

Canonical documentation for CSV delimiter detection. This document defines the conceptual model, terminology, constraints, and standard usage patterns.

> [!NOTE]
> This documentation is implementation-agnostic and intended to serve as a stable reference.

## 1. Purpose and Problem Space

CSV (Comma Separated Values) files are widely used for data exchange between different systems. However, the choice of delimiter in CSV files can vary, leading to inconsistencies and errors when parsing these files. CSV delimiter detection is the process of automatically identifying the delimiter used in a CSV file. This topic exists to address the class of problems related to incorrect or inconsistent delimiter detection, which can result in data corruption, parsing errors, or incorrect data interpretation. The risks of misunderstanding or misapplying CSV delimiter detection include data loss, incorrect analysis, or system crashes.

## 2. Conceptual Overview

The conceptual model of CSV delimiter detection consists of three major components:
- **Delimiter detection algorithms**: These are the methods used to identify the delimiter in a CSV file. Common algorithms include heuristic-based approaches, statistical analysis, and machine learning models.
- **CSV file structure**: This refers to the organization and formatting of the data within the CSV file, including the use of quotes, escapes, and line breaks.
- **Parser or interpreter**: This is the component responsible for reading and processing the CSV file, using the detected delimiter to correctly separate the data fields.

These components interact to produce the outcome of accurately parsed CSV data, which can then be used for various purposes such as data analysis, import into databases, or further processing.

## 3. Scope and Non-Goals

Clarify the explicit boundaries of this documentation.

**In scope:**
* Conceptual models of CSV delimiter detection
* Algorithms and techniques for detecting delimiters
* Best practices for handling edge cases and errors

**Out of scope:**
* Tool-specific implementations of CSV delimiter detection (e.g., programming libraries or software applications)
* Vendor-specific behavior or proprietary solutions
* Operational or procedural guidance for using CSV files in specific contexts (e.g., data import/export procedures)

> [!IMPORTANT]
> Out-of-scope items may be addressed in companion or derivative documentation.

## 4. Terminology and Definitions

Provide precise, stable definitions for all key terms used throughout this document.

| Term | Definition |
|------|------------|
| Delimiter | A character used to separate data fields or values in a CSV file. |
| CSV (Comma Separated Values) | A file format used for exchanging tabular data, with each line representing a data record and each record consisting of fields separated by delimiters. |
| Heuristic | A method or technique used to solve a problem or make a decision, often based on experience, intuition, or probabilistic approaches. |

> [!TIP]
> Definitions should avoid contextual or time-bound language and remain valid as the ecosystem evolves.

## 5. Core Concepts

Explain the fundamental ideas that form the basis of this topic.

### 5.1 Delimiter Detection Algorithm
A high-level explanation of the methods used to identify the delimiter in a CSV file. These algorithms can be based on heuristics, statistical analysis, or machine learning models and are crucial for accurately parsing CSV data.

### 5.2 CSV File Structure
This concept refers to the organization and formatting of the data within the CSV file, including the use of quotes, escapes, and line breaks. Understanding the CSV file structure is essential for developing effective delimiter detection algorithms.

### 5.3 Concept Interactions and Constraints
Delimiter detection algorithms interact with the CSV file structure to identify the delimiter. Constraints include the need to handle various types of delimiters (e.g., comma, semicolon, tab), quotes, and escapes correctly. The choice of algorithm can depend on the specific characteristics of the CSV file and the requirements of the application using the detected delimiter.

## 6. Standard Model

Describe the generally accepted or recommended model for this topic.

### 6.1 Model Description
The standard model for CSV delimiter detection involves a multi-step process:
1. **Initial Guess**: Start with a common delimiter (e.g., comma) as an initial guess.
2. **Heuristic Analysis**: Apply heuristic rules to the CSV file content to adjust the delimiter guess. This may involve analyzing the frequency of different characters, the presence of quotes, and the structure of the data fields.
3. **Verification**: Verify the detected delimiter by parsing the CSV file and checking for consistency and correctness of the parsed data.

### 6.2 Assumptions
The standard model assumes that the CSV file is well-formed and follows common conventions for delimiter usage. It also assumes that the heuristic analysis can provide a reliable indication of the delimiter used.

### 6.3 Invariants
Properties that must always hold true within the model include:
- The detected delimiter must be a single character.
- The delimiter must be consistently used throughout the CSV file.
- The parsing process must correctly handle quotes, escapes, and line breaks.

> [!IMPORTANT]
> Deviations from the standard model must be explicitly documented and justified.

## 7. Common Patterns

Document recurring, accepted patterns associated with this topic.

### Pattern: Using a Default Delimiter
- **Intent**: Provide a fallback when the delimiter cannot be detected.
- **Context**: When the CSV file does not contain clear indicators of the delimiter, or when the detection algorithm is uncertain.
- **Tradeoffs**: May lead to incorrect parsing if the default delimiter does not match the actual delimiter used in the CSV file.

## 8. Anti-Patterns

Describe common but discouraged practices.

> [!WARNING]
> These anti-patterns frequently lead to correctness, maintainability, or scalability issues.

### Anti-Pattern: Assuming a Fixed Delimiter
- **Description**: Always assuming a specific delimiter (e.g., comma) without attempting to detect it.
- **Failure Mode**: Fails when the actual delimiter used in the CSV file is different from the assumed delimiter.
- **Common Causes**: Lack of consideration for variability in CSV file formats or overconfidence in the prevalence of a particular delimiter.

## 9. Edge Cases and Boundary Conditions

Explain unusual or ambiguous scenarios that may challenge the standard model.

> [!CAUTION]
> Edge cases are often under-documented and a common source of incorrect assumptions.

Examples include:
- CSV files with inconsistent delimiter usage.
- Files using non-standard characters as delimiters.
- Files with complex quoting or escaping rules.

## 10. Related Topics

List adjacent, dependent, or prerequisite topics.
- Data import/export formats and standards.
- Character encoding and Unicode support in CSV files.
- Data parsing and processing algorithms.

## 11. References

Provide exactly **five** authoritative external references that substantiate or inform this topic.

1. **RFC 4180**  
   Internet Engineering Task Force (IETF)  
   https://tools.ietf.org/html/rfc4180  
   *Justification*: This RFC provides a standard for the CSV file format, including recommendations for delimiter usage.
2. **CSV Specification**  
   CSV Standards Working Group  
   https://csv-spec.org/  
   *Justification*: This specification outlines the conventions and best practices for CSV files, including delimiter detection.
3. **Unicode Character Database**  
   Unicode Consortium  
   https://www.unicode.org/ucd/  
   *Justification*: Understanding Unicode characters is crucial for handling delimiter detection in files that may use non-ASCII characters as delimiters.
4. **Data Import and Export**  
   W3C  
   https://www.w3.org/TR/csv2/  
   *Justification*: This document discusses the importance of delimiter detection in the context of data import and export operations.
5. **Comma Separated Values (CSV) Format**  
   IANA  
   https://www.iana.org/assignments/media-types/text/csv  
   *Justification*: IANA's registration of the CSV media type includes considerations for delimiter usage and detection.

> [!IMPORTANT]
> These references are normative unless explicitly marked as informative.

## 12. Change Log

| Version | Date | Description |
|---------|------|-------------|
| 1.0 | 2026-01-31 | Initial documentation |

---