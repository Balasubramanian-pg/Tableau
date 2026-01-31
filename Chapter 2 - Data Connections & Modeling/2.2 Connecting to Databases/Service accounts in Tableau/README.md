# Service accounts in Tableau

Canonical documentation for Service accounts in Tableau. This document defines the conceptual model, terminology, constraints, and standard usage patterns.

> [!NOTE]
> This documentation is implementation-agnostic and intended to serve as a stable reference.

## 1. Purpose and Problem Space

Service accounts in Tableau exist to address the need for automated, programmatic access to Tableau resources, such as workbooks, data sources, and sites. The class of problems they address includes scheduling tasks, integrating with external systems, and automating administrative tasks. When service accounts are misunderstood or inconsistently applied, risks and failures can arise, including unauthorized access, data breaches, and system instability. This section is descriptive, not instructional, and provides a foundation for understanding the importance of service accounts in Tableau.

## 2. Conceptual Overview

The conceptual model of service accounts in Tableau consists of three major components: authentication, authorization, and delegation. Authentication refers to the process of verifying the identity of a service account, while authorization determines the level of access granted to the service account. Delegation involves granting a service account the ability to act on behalf of another user or system. These components relate to one another in that authentication is a prerequisite for authorization, and delegation is a specialized form of authorization. The outcome of this model is to provide secure, controlled access to Tableau resources, enabling automation and integration while minimizing security risks.

## 3. Scope and Non-Goals

The explicit boundaries of this documentation are as follows:

**In scope:**
* Conceptual model of service accounts in Tableau
* Authentication and authorization mechanisms
* Delegation and impersonation

**Out of scope:**
* Tool-specific implementations (e.g., Tableau Server, Tableau Online)
* Vendor-specific behavior (e.g., Microsoft Active Directory, Google Workspace)
* Operational or procedural guidance (e.g., creating service accounts, configuring permissions)

> [!IMPORTANT]
> Out-of-scope items may be addressed in companion or derivative documentation.

## 4. Terminology and Definitions

The following terms are used throughout this document:

| Term | Definition |
|------|------------|
| Service account | A dedicated account used for automated, programmatic access to Tableau resources |
| Authentication | The process of verifying the identity of a service account |
| Authorization | The process of determining the level of access granted to a service account |
| Delegation | The act of granting a service account the ability to act on behalf of another user or system |
| Impersonation | A specialized form of delegation, where a service account assumes the identity of another user |

> [!TIP]
> Definitions should avoid contextual or time-bound language and remain valid as the ecosystem evolves.

## 5. Core Concepts

The fundamental ideas that form the basis of service accounts in Tableau are:

### 5.1 Authentication
Authentication is the process of verifying the identity of a service account. This can be achieved through various mechanisms, such as username and password, API keys, or certificates. Authentication is a critical component of the conceptual model, as it ensures that only authorized service accounts can access Tableau resources.

### 5.2 Authorization
Authorization determines the level of access granted to a service account. This can include permissions to view, edit, or delete workbooks, data sources, or sites. Authorization is based on the service account's role and permissions, which are defined by the Tableau administrator.

### 5.3 Concept Interactions and Constraints
The core concepts interact in the following ways:
* Authentication is a prerequisite for authorization.
* Delegation is a specialized form of authorization.
* Impersonation is a specialized form of delegation.
Constraints include:
* Service accounts must be authenticated before accessing Tableau resources.
* Service accounts must be authorized to access specific resources.
* Delegation and impersonation must be explicitly granted by the Tableau administrator.

## 6. Standard Model

The standard model for service accounts in Tableau is based on the following structure and behavior:

### 6.1 Model Description
The standard model consists of three tiers: authentication, authorization, and delegation. Authentication verifies the identity of the service account, while authorization determines the level of access granted. Delegation enables the service account to act on behalf of another user or system.

### 6.2 Assumptions
The standard model assumes:
* A secure authentication mechanism is in place.
* Authorization is based on a role-based access control (RBAC) model.
* Delegation and impersonation are explicitly granted by the Tableau administrator.

### 6.3 Invariants
The following properties must always hold true within the standard model:
* Service accounts are authenticated before accessing Tableau resources.
* Service accounts are authorized to access specific resources.
* Delegation and impersonation are used only when explicitly granted by the Tableau administrator.

> [!IMPORTANT]
> Deviations from the standard model must be explicitly documented and justified.

## 7. Common Patterns

The following patterns are commonly associated with service accounts in Tableau:

### Pattern A: Automated Scheduling
- **Intent:** Automate tasks, such as refreshing workbooks or sending notifications.
- **Context:** When tasks need to be performed on a regular schedule.
- **Tradeoffs:** Convenience and efficiency vs. potential security risks if not properly configured.

## 8. Anti-Patterns

The following anti-patterns are commonly observed in service account implementations:

> [!WARNING]
> These anti-patterns frequently lead to correctness, maintainability, or scalability issues.

### Anti-Pattern A: Overly Permissive Service Accounts
- **Description:** Service accounts with excessive permissions, allowing them to access sensitive resources.
- **Failure Mode:** Unauthorized access to sensitive data or system instability.
- **Common Causes:** Lack of proper authorization or delegation.

## 9. Edge Cases and Boundary Conditions

The following edge cases and boundary conditions may challenge the standard model:

> [!CAUTION]
> Edge cases are often under-documented and a common source of incorrect assumptions.

* Service accounts with multiple roles or permissions.
* Delegation and impersonation across multiple sites or organizations.
* Service accounts with conflicting authorization rules.

## 10. Related Topics

The following topics are adjacent, dependent, or prerequisite to service accounts in Tableau:

* Tableau Server administration
* Tableau Online administration
* Role-based access control (RBAC)
* Authentication and authorization mechanisms

## 11. References

The following five authoritative external references substantiate or inform this topic:

1. **Tableau Server Administration Guide**  
   Tableau Software  
   https://help.tableau.com/current/server/en-us/get-started.htm  
   *Justification:* Official Tableau documentation for server administration.
2. **Tableau Online Administration Guide**  
   Tableau Software  
   https://help.tableau.com/current/online/en-us/get-started.htm  
   *Justification:* Official Tableau documentation for online administration.
3. **Role-Based Access Control (RBAC)**  
   National Institute of Standards and Technology (NIST)  
   https://csrc.nist.gov/projects/role-based-access-control  
   *Justification:* Authoritative source on RBAC.
4. **OAuth 2.0 Specification**  
   Internet Engineering Task Force (IETF)  
   https://tools.ietf.org/html/rfc6749  
   *Justification:* Standard specification for OAuth 2.0.
5. **Service Account Security Best Practices**  
   Google Cloud  
   https://cloud.google.com/iam/docs/service-accounts-best-practices  
   *Justification:* Industry-recognized best practices for service account security.

> [!IMPORTANT]
> These references are normative unless explicitly marked as informative.

## 12. Change Log

| Version | Date | Description |
|---------|------|-------------|
| 1.0 | 2026-01-31 | Initial documentation |

---