# 1 Table of Contents

1. Table of Contents
2. Introduction: Conceptual vs. Technical Distinctions
3. Developing for Reporting (Static Distribution)
4. Developing for Analysis (Interactive Exploration)
5. Bridging the Gap: Hybrid Workflows
6. Modern Approaches (2024-2025): Pulse and Viz Extensions
7. Reasoning Summary
8. Points That Require Verification or Are Uncertain

# 2 Introduction: Conceptual vs. Technical Distinctions

In the Tableau ecosystem, the terms "Analysis" and "Reporting" refer to two distinct technical approaches to data delivery, though they are often conflated in general conversation.

**Reporting** focuses on the distribution of static or near static facts. It answers the question "What happened?" The technical goal is often precise formatting, printability (PDF), and broad distribution to users who may not log into the platform interactively.

**Analysis** focuses on the interactive exploration of causes. It answers the question "Why did it happen?" The technical goal is speed, flexibility, and user driven filtering. This requires the user to be active within the interface, clicking marks, changing parameters, and drilling down into granular data.

Tableau was originally architected as an analysis tool (VizQL), but recent features introduced in 2024 and 2025 have significantly strengthened its reporting capabilities, particularly with the introduction of Table Viz Extensions and Tableau Pulse Digests [1].

# 3 Developing for Reporting (Static Distribution)

When building for reporting, the developer must prioritize layout stability, readability without interaction, and tabular data density.

## 3.1 Fixed Size Layouts and Pagination

Reports often need to be exported to PDF or PowerPoint. Tableau dashboards default to interactive sizing, which breaks pagination.

**Step by Step Workflow**
1.  **Set Dashboard Size:** Open the Dashboard pane and select **Size > Fixed Size**.
2.  **Define Dimensions:** Choose a standard paper size, such as **Letter Landscape (1100 x 850)** or **A4**. This ensures that when the server generates a PDF subscription, the aspect ratio matches the paper, preventing scrollbars from appearing in the printout.
3.  **Disable Interactivity:** For pure reporting, remove interactive elements like "Show/Hide Container" buttons that do not render in PDF exports.

**Why It Matters**
Dynamic sizing (Automatic) allows charts to resize based on the user's screen. In a reporting context, this causes misalignment when the content is exported to a static file format. Fixed sizing guarantees the output matches the design.

## 3.2 Advanced Tables with Viz Extensions (2024.2+)

Prior to 2024, creating Excel like tables in Tableau was difficult. The introduction of **Viz Extensions** has formalized reporting tables as a first class citizen.

**Step by Step Workflow**
1.  **Enable Extension:** In the Marks card, click the dropdown (default is Automatic) and select **Add Extension**.
2.  **Select Table Extension:** Choose the **Table Visualization** extension (published by Tableau).
3.  **Build the Report:** Drag dimensions and measures into the "Detail" or extension specific drop zones.
4.  **Format:** Use the extension's configuration menu to apply column specific widths, conditional formatting (color scales per column), and headers.

**Comparison to Legacy Methods**
Legacy methods required "Measure Names/Values" tricks or placeholder axes (`MIN(0)`) to create distinct columns. The Table Viz Extension allows for independent formatting of columns similar to a spreadsheet, which is the standard requirement for operational reporting [2].

## 3.3 PDF Subscriptions and Bursting

Reporting relies on "push" distribution rather than "pull" access.

**Implementation Workflow**
1.  **Create Subscription:** On Tableau Server/Cloud, click **Watch > Subscriptions**.
2.  **Format Selection:** Select **Format > PDF** (or Image and PDF).
3.  **View Options:** Choose "This View" or "Entire Workbook."
4.  **Bursting Logic:** To send different data to different users (Bursting), you must utilize **User Filters** (Row Level Security) on the data source. When the subscription runs, the server impersonates the recipient and generates a PDF containing only their allowed data.

# 4 Developing for Analysis (Interactive Exploration)

Analysis requires the developer to build "paths of inquiry" rather than static answers. This relies on Dashboard Actions and Parameters.

## 4.1 Parameter Actions for "What-If" Analysis

Parameter actions allow users to change a variable in a calculation by interacting with a visual.

**Step by Step Workflow**
1.  **Create Parameter:** Create a float parameter named `[Reference Line Value]`.
2.  **Create Reference Line:** Add a reference line to your chart linked to this parameter.
3.  **Define Action:** Go to **Dashboard > Actions > Add Action > Change Parameter**.
4.  **Configuration:** Set the Source Sheet to your trend chart. Set the Target Parameter to `[Reference Line Value]`. Set the Field to the axis value (e.g., `SUM(Sales)`).
5.  **Usage:** When a user clicks a point on the chart, the reference line moves to that value, instantly recalculating variances for all other marks relative to the selected point.

**Why It Matters**
This allows analysts to re-baseline data dynamically (e.g., "Compare all regions to the West region's performance") without altering the underlying SQL query or data structure.

## 4.2 Guided Drill Down Paths (Set Actions)

Drill downs allow users to move from summary to detail without leaving the context of the analysis.

**Implementation Note**
Use **Set Actions** rather than simple Filter Actions for asymmetric drill downs.
1.  **Create Set:** Create a set based on the `Category` dimension.
2.  **Calculation:** Create a field: `IF [Category Set] THEN [Sub-Category] ELSE [Category] END`.
3.  **Action:** Configure a Dashboard Set Action that adds the selected Category to the set upon clicking.
4.  **Result:** Clicking "Furniture" expands only the Furniture bar into its sub-categories (Chairs, Tables) while leaving "Office Supplies" collapsed. This maintains the comparative context which is lost in a standard "Filter and Jump" report [3].

# 5 Bridging the Gap: Hybrid Workflows

Most business environments require a hybrid approach. Tableau facilitates this through "Viz in Tooltip" and "Download to Crosstab."

## 5.1 Viz in Tooltip

This feature embeds an "Analysis" view inside a "Reporting" view.

**Workflow**
1.  Create a main reporting sheet (e.g., a map of Sales by State).
2.  Create a separate analysis sheet (e.g., a scatter plot of Profit vs. Discount).
3.  On the main sheet, open the Tooltip shelf.
4.  Select **Insert > Sheets > [Analysis Sheet]**.
5.  **Filter Propagation:** Ensure `<All Fields>` is set in the filter string. When a user hovers over "Texas" in the report, the tooltip renders the scatter plot filtered specifically for Texas.

## 5.2 Image Roles (Reporting in Analysis)

Introduced to bridge the gap between visual analysis and product reporting, Image Roles allow URL based images to be rendered dynamically in headers.

**Use Case**
An interactive inventory dashboard can display the actual product images in the row headers. This transforms an abstract bar chart into a SKU level report that merchandising teams can use for visual verification.

# 6 Modern Approaches (2024-2025): Pulse and Viz Extensions

The distinction between analysis and reporting has blurred with the release of Tableau Pulse and advanced Viz Extensions.

## 6.1 Tableau Pulse: Automated Reporting & Analysis

Tableau Pulse (General Availability Feb 2024, updated throughout 2025) offers a distinct "headless" experience that services both needs.

*   **As Reporting (Digests):** Pulse sends daily or weekly emails (Digests) containing key metrics. This is a pure reporting workflow (push distribution, static snapshot).
*   **As Analysis (Q&A):** Users can click into a metric from the digest to enter the Pulse web interface. Here, they can use "Ask" (Natural Language Query) to break down the metric by different dimensions (e.g., "Show this by Region"). This is an analysis workflow [4].

**2025 Feature Update**
As of 2025, Pulse metrics can be embedded directly into standard Tableau Dashboards. This allows a dashboard to contain a "Reporting" element (the strict metric card) alongside "Analysis" elements (custom visual exploration) [5].

## 6.2 Table Viz Extension

The Table Viz Extension (released late 2024) is the definitive feature for "Reporting" within Tableau.

**Capabilities**
*   **Conditional Formatting:** Excel style color scales per column.
*   **Pagination:** Better handling of large scrolling lists than native Tableau crosstabs.
*   **Search:** In cell searching for specific row values.

**Why It Matters**
Historically, developers were advised *not* to use Tableau for large tabular reports ("wall of data"). This extension explicitly enables that use case, acknowledging that tabular reporting is a valid analytical entry point for many finance and operations users [2].

# 7 Reasoning Summary

This documentation distinguishes "Reporting" and "Analysis" based on technical implementation (Fixed vs. Automatic sizing, Subscriptions vs. Actions) rather than just semantic definitions. The instruction prioritizes recent features that specifically address the "Reporting" gap in Tableau, notably the **Table Viz Extension** (confirmed released in version 2024.3) and **Tableau Pulse** (evolved throughout 2024/2025).

The inclusion of the "Hybrid" section acknowledges that modern dashboards often mix these modes. The workflows described (Fixed Size for PDF, Parameter Actions for What-If) are standard best practices verified against current Tableau desktop manuals.

Post June 2024 updates were verified via search, confirming the Table Viz Extension's capabilities (conditional formatting, column resize) and Pulse's dual nature (Digest vs. Exploration).

# 8 Points That Require Verification or Are Uncertain

1.  **Pulse in On-Premises Server:** Tableau Pulse is primarily a Tableau Cloud feature. Its availability on Tableau Server (Container/Linux) for 2025 releases is version dependent and may require specific "Advanced Management" licensing which varies by contract.
2.  **Table Viz Extension Backward Compatibility:** While the extension works in 2024.2+, its performance on extremely large datasets (1M+ rows) compared to native text tables is variable and depends on client side browser memory (Web Edit) vs. Desktop rendering.
3.  **ASSUMPTION:** The section on "Bursting" assumes the use of standard PDF subscriptions with User Filters. Third party tools (like VizAlerts) or pure API scripting are alternative methods not detailed here to maintain focus on native platform capabilities.

**References**
[1] Tableau, "Tableau Pulse Features," Tableau Release Notes 2024-2025.
[2] Tableau/Salesforce, "Table Visualization Extension," Tableau Exchange, late 2024.
[3] Tableau, "Set Actions," Tableau Help Documentation.
[4] InterWorks, "Tableau Pulse vs. Dashboards," April 2024.
[5] Tableau, "New Features in Tableau 2025," Official Blog, 2025.

