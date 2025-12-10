# Certified data sources workflow

**Certified Data Sources Workflow in Tableau**

**Introduction**
A certified data source is a published data source that a trusted expert has validated. Certification signals to users that the data is reliable, well-modeled, and approved for use. This workflow involves multiple roles and steps to ensure data quality and trust.

**Purpose and Benefits**
*   **Establish Trust**: Users can confidently build reports from known-good data.
*   **Promote Consistency**: Encourages reuse of standardized data models across the organization.
*   **Improve Efficiency**: Reduces time spent by users validating and modeling raw data themselves.
*   **Clarify Ownership**: Assigns clear responsibility for data quality and definition.

**Key Roles**
*   **Data Source Owner/Creator**: The individual who creates, publishes, and maintains the data source. Often a data analyst or engineer.
*   **Certifier**: A trusted authority, like a data steward or senior analyst, who validates the data source. They have the "Certify" permission capability.
*   **Consumer**: Report builders and viewers who use the certified data source to create workbooks.

**Certification Workflow Steps**

**Step 1: Creation and Development**
*   The owner connects to raw data in Tableau Desktop.
*   They perform necessary data modeling: joins, blends, calculations, filters, and parameter creation.
*   They test the data source for accuracy and performance.
*   The owner publishes the data source to Tableau Cloud/Server to a development project.

**Step 2: Testing and Validation**
*   The owner and potential users test the published data source in staging or development environments.
*   Validation includes checking calculation logic, data freshness, row-level security, and query performance.
*   The owner addresses any issues found during testing.

**Step 3: Request for Certification**
*   The owner moves the data source to a governed production project.
*   They notify the designated certifier that the data source is ready for review.
*   This step is often an informal business process, not a system trigger.

**Step 4: Certification Review**
*   The certifier examines the data source.
*   **Review areas include**:
    *   Data accuracy and lineage.
    *   Appropriate use of row-level security.
    *   Clear field names and definitions (using descriptions).
    *   Sustainable refresh schedule and performance.
    *   Adherence to organizational naming conventions.
*   The certifier may request changes or approve.

**Step 5: Certification Action**
*   The certifier navigates to the data source on the web or in Catalog.
*   They click the "Certify" icon (a checkmark badge) on the data source's page.
*   The system marks the data source as certified. A badge appears next to its name throughout the platform.

**Step 6: Publication and Promotion**
*   The certified data source is available in the designated production project.
*   Owners should add metadata: a meaningful description, contact information, and refresh schedules.
*   Data leaders promote the new certified asset to report builders.

**Step 7: Ongoing Maintenance**
*   The owner monitors extract refreshes or live connection health.
*   They update the data source for schema changes or business logic updates.
*   Any modification may require re-validation or decertification, depending on the change's impact.
*   Regular audits ensure the data source remains accurate and performant.

**Technical Requirements and Permissions**

**Prerequisites for Certification**
*   The data source must be published to Tableau Cloud/Server.
*   The certifier must have the "Certify" permission capability on the data source or its project.
*   Use of Tableau Catalog (part of Data Management) is recommended for full lineage and impact analysis.

**Permission Model**
*   Certification capability is separate from "Write" or "Download" permissions.
*   Site Administrators can grant the certify capability to specific users or groups.
*   Permissions are typically set at the project level, applying to all content within it.

**Best Practices**

**Establish Clear Guidelines**
*   Define criteria for what makes a data source certifiable (completeness, accuracy, documentation, sustainability).
*   Create a runbook for owners detailing the development and testing process.
*   Document the review checklist for certifiers.

**Use Projects for Governance**
*   Maintain separate projects: **Development**, **Testing**, and **Certified Production**.
*   Set project permissions to enforce workflow stages (e.g., only certifiers can publish to the Certified Production project).

**Leverage Metadata and Catalog**
*   Require owners to populate descriptions for the data source and its fields.
*   Use Tableau Catalog to document lineage from source systems. This is critical for the certifier's review.
*   Publish refresh schedules and failure notifications.

**Manage the Lifecycle**
*   Implement a review schedule to periodically reconfirm certification status.
*   Decertify deprecated or out-of-date data sources.
*   Communicate changes or decertification to downstream users proactively.

**Common Challenges**
*   **Bottlenecks**: A single certifier can become a workflow bottleneck. Solution: Train multiple certifiers.
*   **Ownership Blur**: Lack of clear ownership after certification. Solution: Assign a primary and secondary contact in the data source description.
*   **Over-Certification**: Certifying too many sources dilutes the value. Solution: Apply strict business value criteria.

**Conclusion**
The certified data source workflow transforms data management from an ad-hoc process to a governed practice. It requires coordination between data owners, certifiers, and consumers. Success depends on clear criteria, defined roles, and supportive project-level permissions. When executed well, it builds a foundation of trusted, reusable data assets that accelerate analytics while maintaining control and quality. The workflow is not fully automated; it relies on human judgment and established organizational processes supported by Tableau's certification and permission features.
