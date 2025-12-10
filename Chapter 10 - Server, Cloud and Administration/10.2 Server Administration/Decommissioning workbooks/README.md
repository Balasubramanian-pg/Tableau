# Decommissioning workbooks

**Decommissioning Workbooks in Tableau Cloud**

**Introduction**
Decommissioning is the process of retiring workbooks that are no longer needed. A structured approach prevents clutter, reduces maintenance, and ensures users access only current data. It involves identification, communication, archival, and removal.

**Reasons for Decommissioning**
*   **Outdated Content**: The report is based on deprecated metrics or business processes.
*   **Low or No Usage**: The workbook has not been viewed in a significant time period.
*   **Replacement**: A new, improved workbook has superseded the old one.
*   **Source Data Unavailable**: The underlying data source is no longer accessible or supported.
*   **Resource Optimization**: Reduce server load and maintenance overhead.

**Decommissioning Process Steps**

**Step 1: Identification**
Find candidate workbooks for decommissioning.

**Methods:**
*   Use the "Unused Content" Admin view to list workbooks with zero views over a set period (e.g., 90 days).
*   Run the "Workbook and Data Source Connections" view to find workbooks tied to retired data sources.
*   Solicit input from business unit leads on outdated reports.
*   Check for workbooks with titles containing "OLD," "LEGACY," or "ARCHIVE."

**Step 2: Analysis and Dependency Check**
Before removal, assess impact.

**Actions:**
*   Use Tableau Catalog (if available) to perform an impact analysis. Check if the workbook is used as a data source for other content.
*   Review workbook properties. Note the owner, project location, and last modified date.
*   If a replacement exists, document the link to the new workbook.

**Step 3: Notification and Approval**
Communicate the planned decommissioning.

**Process:**
*   Contact the workbook owner listed in the properties. If no owner is active, contact the manager of the associated project or department.
*   State the proposed decommission date and reason.
*   Provide a grace period (e.g., two weeks) for stakeholders to object or download needed data.
*   Secure formal approval from the owner or department head.

**Step 4: Archival (Pre-Removal)**
Preserve a copy for compliance or historical reference.

**Options:**
*   **Move to Archive Project**: Change workbook permissions to "View" only and move it to a dedicated "Archive" project. This is the standard method.
*   **Export as TWBX**: Download a packaged workbook (.twbx file) to a secure network drive or document management system. This is for long-term records retention.
*   **PDF/Snapshot Export**: Save final dashboard views as static PDFs for legal or audit needs.

**Step 5: Final Actions**
Execute the decommission based on policy.

**Choices:**
*   **Deletion**: Permanently delete the workbook from Tableau Cloud. This is irreversible. Use for content with no legal or historical value.
*   **Archival In-Place**: Keep the workbook in its project but remove it from all user favorites and hide it from project views using permissions.

**Step 6: Communication of Change**
Inform users the content is gone and direct them to alternatives.

**Actions:**
*   If a replacement exists, update any links or navigation portals to point to the new workbook.
*   For deleted workbooks, consider a final site-wide or project-specific announcement.
*   Update any data catalog or inventory listing.

**Best Practices**

**Establish a Clear Policy**
*   Define criteria for decommissioning (e.g., zero views for 180 days).
*   Set standard timelines for notification periods and archival duration.
*   Document the approval chain.

**Use Project Structure for Lifecycle**
*   Create a dedicated "Archive" project with restricted "View Only" permissions.
*   Structure active projects to mirror business units for easier ownership identification.

**Automate Identification**
*   Schedule regular runs of the "Unused Content" Admin view. Export the list for review.
*   Use the Tableau REST API to build a custom report on workbook age and activity.

**Maintain an Inventory**
*   Keep a simple log or spreadsheet of decommissioned workbooks, including date, reason, and archive location.

**Permissions and Ownership**
*   Assign an "owner" to every project to act as a point of contact for orphaned workbooks.
*   Run periodic permission audits to ensure only active users have publishing rights.

**Common Challenges and Solutions**

**Challenge: Unknown or Departed Owners**
*   **Solution**: Assign project-level owners. If no owner can be identified, the business unit lead or site administrator makes the decommission decision.

**Challenge: Fear of Data Loss**
*   **Solution**: Emphasize the archival step. Communicate that data is preserved in source systems; only the report view is being retired.

**Challenge: User Resistance**
*   **Solution**: Provide ample notice and clear direction to replacement content. Highlight the benefit of a cleaner, more reliable reporting site.

**Post-Decommissioning**

**Monitor**
*   After a period, check if users are attempting to access old bookmarked URLs. Use web server logs or login attempts to gauge this.
*   Be prepared to temporarily restore or redirect if a critical need is discovered.

**Review Process**
*   Periodically assess the decommissioning policy itself. Adjust timeframes and criteria based on organizational feedback.

**Conclusion**
A systematic decommissioning process is essential for maintaining a healthy Tableau Cloud environment. It focuses on user communication, impact analysis, and secure archival. By treating workbook retirement as a standard operational procedure, organizations reduce risk, improve performance, and ensure users interact only with relevant, accurate data. The key is consistency, clear policy, and respect for user dependency on existing reports.
