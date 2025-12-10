# Audit and compliance requirements

**Audit and Compliance Requirements in Tableau Cloud**

**Introduction**
Organizations using Tableau Cloud must meet internal and external audit and compliance requirements. These requirements focus on security, data governance, and user activity. Tableau Cloud provides features and data to support compliance efforts.

**Core Compliance Areas**
Compliance in Tableau Cloud covers three main areas.

**User Access and Authentication**
*   Control and verify who can access the system.
*   Track user authentication methods and sessions.

**Data Security and Governance**
*   Manage where data is stored (data residency).
*   Control permissions on data and content.
*   Track data lineage and movement.

**Activity Monitoring and Logging**
*   Record user and system actions.
*   Provide an immutable trail for forensic analysis.

**Key Tableau Cloud Features for Compliance**

**Authentication and Single Sign-On (SSO)**
*   **SAML-based SSO**: Integrate with identity providers like Okta, Azure AD, or Ping Identity. Centralizes user management and enforces corporate password policies.
*   **Two-Factor Authentication (2FA)**: An additional security layer for user sign-in. Can be required site-wide.
*   **Trusted Authentication**: Allows embedding Tableau content in other applications with controlled access.

**Administrative Audit Tools**
*   **Admin Audit Views**: Pre-built dashboards in the Admin Insights area. Track logins, content changes, and permission events.
*   **User Filters**: Audit views can be filtered by user, date range, or project to isolate specific activities.
*   **Data Source Connections View**: Monitors connections and credentials used in published workbooks.

**System Logs and Data Export**
*   **Site Export API**: Programmatically exports a comprehensive set of site data. This includes users, groups, projects, workbooks, data sources, and permissions.
*   **REST API**: Allows extraction of metadata for custom audit reporting.
*   **Login Access Log**: Administrators can download a CSV file of all user login attempts, including timestamps and IP addresses.

**Content and Data Governance Features**
*   **Permission Capabilities**: Granular control over user actions (View, Filter, Download, Save, etc.) at the project, workbook, and view level.
*   **Data Project Connections**: Centralize and manage connection credentials. Reduces the use of embedded passwords.
*   **Hyperlog (Tableau Catalog)**: Available with Data Management. Provides lineage tracking showing how data flows from source to workbook. Identifies upstream dependencies and downstream impacts.

**Meeting Specific Regulatory Requirements**

**General Data Protection Regulation (GDPR)**
*   **Right to Erasure**: Use the Site Export API to identify a user's content. Manually remove or anonymize their personal data.
*   **Data Residency**: Tableau Cloud data centers are in specific geographic regions. Organizations must select the correct region during initial setup.
*   **Access Logs**: Login logs help demonstrate secure access controls.

**SOC 2 / ISO 27001**
*   **Access Reviews**: Admin views help regularly review user accounts and permissions.
*   **Change Management**: Audit logs track publishing activity, permission changes, and data source updates.
*   **Incident Response**: Detailed logs support investigation of security events.

**Internal IT Controls**
*   **Segregation of Duties**: Permission capabilities allow restriction of user functions (e.g., a user can view data but not download it).
*   **Approval Workflows**: While not native, external processes can use permission controls to gate publishing to production projects.

**Audit Process with Tableau Cloud**

**Preparation**
*   Define the audit scope (e.g., specific user group, time period, project).
*   Identify relevant Tableau Cloud administrative users and stakeholders.

**Data Collection**
*   Use Admin Audit Views for initial high-level analysis.
*   Generate and download Login Access Logs for authentication audit.
*   Use the Site Export API or REST API to gather comprehensive metadata for detailed analysis.
*   For Data Management customers, use Tableau Catalog for data lineage reports.

**Analysis and Reporting**
*   Correlate login data with user activity logs.
*   Review permission changes for unauthorized modifications.
*   Verify data source credentials and connections for security.
*   Document findings and evidence.

**Remediation**
*   Deactivate unused accounts found in login reports.
*   Adjust permissions based on audit findings.
*   Update or remove embedded credentials in workbooks.

**Best Practices for Ongoing Compliance**

**Establish Regular Review Cycles**
*   Schedule quarterly reviews of user accounts and group memberships.
*   Perform monthly checks of Admin Audit Views for anomalous activity.
*   Review and archive login logs based on data retention policies.

**Implement Least Privilege Access**
*   Grant users only the permissions necessary for their role.
*   Use group-based permissions for easier management.
*   Restrict "Explorer (can publish)" and "Creator" roles.

**Maintain Documentation**
*   Document permission models for key projects and content.
*   Keep records of audit procedures and schedules.
*   Document data flows and sources using Tableau Catalog or manual diagrams.

**Leverage Automation**
*   Use the REST API to build automated scripts for routine audit data collection.
*   Set up external monitoring to alert on specific high-risk events from audit logs.

**Limitations and Considerations**
*   **Historical Data Limits**: Tableau Cloud retains activity logs for a finite period (typically 90-180 days). Long-term archiving requires proactive export.
*   **Manual Processes**: Some compliance actions, like data deletion for GDPR, require manual steps.
*   **Shared Responsibility Model**: Salesforce maintains the security *of* the cloud platform. Customers are responsible for security *in* the cloud (user management, data permissions, content security).

**Conclusion**
Tableau Cloud provides tools to support audit and compliance programs. Success relies on proactive use of admin views, APIs, and governance features. A structured approach with regular reviews of access, permissions, and activity logs is essential. Organizations must understand their data retention needs and supplement Tableau's native logging with external archiving where required. Proper configuration and ongoing management turn Tableau Cloud's capabilities into a controlled environment that meets internal and regulatory standards.
