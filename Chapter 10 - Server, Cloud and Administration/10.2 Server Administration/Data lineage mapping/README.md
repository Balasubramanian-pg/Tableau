# Data lineage mapping

**Data Lineage Mapping in Tableau**

**Introduction**
Data lineage mapping tracks the flow of data from its original source to its final form in a dashboard. It provides a visual record of data origins, transformations, and dependencies. This is critical for impact analysis, debugging, and governance.

**Purpose and Value**
*   **Impact Analysis**: See which dashboards and metrics are affected by a change to a source system.
*   **Trust and Transparency**: Understand how data is calculated and where it comes from.
*   **Debugging**: Quickly trace errors back to their source.
*   **Compliance and Auditing**: Document data provenance for regulatory requirements.
*   **Onboarding**: Help new users understand data relationships.

**Core Components of Lineage**
A lineage map typically shows:
*   **Upstream Sources**: Original databases, files, applications, and external APIs.
*   **Intermediate Steps**: Data preparation tools (Tableau Prep, custom SQL), joins, blends, and calculations.
*   **Downstream Assets**: Published data sources, workbooks, dashboards, and derived metrics.

**Tableau Tools for Lineage Mapping**

**Tableau Catalog (Data Management Feature)**
Catalog provides automated lineage within the Tableau ecosystem.

**What It Captures**
*   Connections to external source systems (e.g., Snowflake, Salesforce).
*   Published data sources and their upstream dependencies.
*   Workbooks and their connected data sources.
*   Flows built in Tableau Prep.
*   Custom SQL used in extracts or live queries.

**Key Catalog Views**
*   **Lineage Diagram**: Interactive graph showing upstream and downstream links for a selected asset.
*   **Impact Analysis**: Lists all dependent workbooks and views for a selected data source.
*   **Column-Level Lineage**: For some data sources, traces specific fields to their source columns.

**Limitations**
*   Catalog lineage is primarily limited to assets managed within Tableau Cloud/Server.
*   Deep lineage into complex ETL tools or source system transformations may not be captured without manual notes.

**Manual Documentation Methods**
When automated tools are insufficient, manual methods are required.

**Common Approaches**
*   **Embedded Metadata**: Use Tableau's description fields on data sources, workbooks, and fields to note origins.
*   **Data Dictionary**: Maintain a separate document or wiki listing key data assets, their sources, and logic.
*   **Diagramming Tools**: Use tools like Lucidchart or Visio to create and maintain lineage maps.

**Best Practices for Implementation**

**Establish Ownership**
*   Assign an owner for each primary data source and key metric.
*   The owner is responsible for maintaining accurate lineage documentation.

**Integrate with Development Workflow**
*   Make updating lineage or descriptions part of the publishing checklist.
*   Require impact analysis via Catalog before modifying a certified data source.

**Communicate and Train**
*   Train developers to use Tableau Prep for reproducible data prep, as its steps are captured in Catalog.
*   Teach users how to read lineage diagrams to find trustworthy data.

**Standardize and Simplify**
*   Encourage use of published, certified data sources over embedded one-off connections.
*   Reduce complex, nested custom SQL in workbooks in favor of published data source logic.

**Lineage for Key Scenarios**

**Scenario 1: Modifying a Source System**
*   **Action**: Use Catalog's impact analysis on the connected data source.
*   **Result**: Generate a list of all affected workbooks. Notify their owners.

**Scenario 2: Debugging a Metric Discrepancy**
*   **Action**: Open the workbook's lineage view.
*   **Result**: Trace the metric's calculation back through the data source to the original tables. Check for filters, joins, or calculation logic at each step.

**Scenario 3: Auditing for Compliance**
*   **Action**: Export documentation from Catalog and combine with manual source system metadata.
*   **Result**: Produce a report showing full data provenance for regulated reports.

**Advanced Considerations**

**Cross-Platform Lineage**
For data that moves through multiple systems (e.g., ERP -> Data Lake -> Tableau), Catalog's view is partial. A unified metadata management platform may be necessary.

**Scheduled Lineage Updates**
Catalog lineage updates automatically upon publishing and refreshing. For live connections, it reflects the last known state.

**Performance Impact**
Extensive use of custom SQL or complex nested calculations can make lineage graphs difficult to interpret. Simplifying logic improves lineage clarity.

**Conclusion**
Data lineage mapping is a foundational practice for mature data environments. Tableau Catalog automates lineage for assets within its platform, providing crucial impact analysis and transparency. Effective lineage management requires combining this automated tooling with clear ownership, development policies, and supplemental manual documentation for external sources. The outcome is a more trustworthy, maintainable, and compliant analytics ecosystem.
