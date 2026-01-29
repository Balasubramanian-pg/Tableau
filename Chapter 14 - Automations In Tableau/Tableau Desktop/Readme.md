# Tableau Desktop Automations Using XML

<img width="888" height="585" alt="image" src="https://github.com/user-attachments/assets/c0d4c07b-d4ac-4774-ae72-2828f3fbd3b6" />

> [!WARNING]
> **What You CANNOT Do with XML Hacking**
>
> While powerful, there are limits:
>
> 1. **Creating Charts from Scratch**  
>    You can’t write a script to “make a bar chart.” The XML that defines marks, encodings, and pill arrangements is deeply complex and encoded. Modifying existing visuals is far safer than creating new ones.
>
> 2. **Generating Extracts**  
>    You cannot create `.hyper` data files by editing XML. The workbook XML only references the extract file location.
>
> 3. **Complex Logic Changes**  
>    Changing UI behavior such as converting a *Single Select Dropdown* into a *Multiple Values Slider* requires modifying multiple nested tags. This is usually faster and safer to do in Tableau Desktop.

### Formatting & Visual Consistency (The "Rebranding" Scripts)

1. **Mass Color Replacement**
   Scan the entire workbook XML and replace a specific HEX color value (for example `#1F77B4`) with a new brand color (for example `#E15759`) across sheets, titles, backgrounds, borders, and text.

2. **Global Font Standardizer**
   Replace all instances of a font family (for example `Arial`) with a standard corporate font (for example `Tableau Book`) to enforce consistency across titles, tooltips, axes, and text objects.

3. **Logo Swapper (Image Objects)**
   Locate all image zones (`type='bitmap'`) in dashboards and update the referenced file path so `old_logo.png` is replaced with `new_logo.png` everywhere.

### Content & Text Management (The "Click-Heavy" Scripts)

4. **Bulk Tooltip Disclaimer Injector**
   Append a standardized disclaimer such as *“Data is subject to change”* to the bottom of every tooltip by modifying tooltip XML definitions at scale.

5. **Title Format Enforcer**
   Standardize all worksheet titles by forcing center alignment and a specific font size (for example size 14) via worksheet layout metadata.

6. **Sheet Unhider**
   Instantly unhide every worksheet in the workbook by updating visibility or window-related XML attributes, making inherited workbooks easy to audit.

### Data & Calculation Management (The "Metadata Cleanup" Scripts)

7. **Calculated Field Extractor**
   Parse all calculated fields from `<column>` tags and export their names and formulas into a CSV to generate a complete data dictionary.

8. **Custom SQL Updater**
   Locate Custom SQL definitions in text-based relations and perform controlled string replacements, such as updating table names from `SALES_2023` to `SALES_2024`.

9. **Duplicate Field Name Cleaner**
   Remove suffixes like `(copy)` or numeric endings such as ` 1` from duplicated field names using regex-based caption cleanup.

### QA & Governance (The "Detective" Scripts)

10. **Hardcoded Filter Scanner**
    Scan filter definitions to detect suspicious hardcoded values, such as specific usernames, and flag them for security or governance review.

11. **Broken Reference Checker**
    Identify calculated fields referencing non-existent datasource IDs and report sheets affected by broken calculations (red exclamation marks).

### Example: The "Mass Color Swapper" Script
Here is a script that replaces one color with another across the entire workbook (borders, fonts, backgrounds, everything).

```python
import fileinput
import sys

# CONFIG
FILE_PATH = 'MyWorkbook.twb'
OLD_COLOR = '#1f77b4'  # The default Tableau Blue
NEW_COLOR = '#ff0000'  # Bright Red

def mass_color_replace():
    # We don't even need full XML parsing for this, 
    # a raw text replacement is often safer for colors 
    # to catch them in style tags, formatting tags, etc.
    
    print(f"Replacing {OLD_COLOR} with {NEW_COLOR} in {FILE_PATH}...")
    
    # Read file, replace text, write back
    # inplace=True creates a backup file automatically (.bak)
    with fileinput.FileInput(FILE_PATH, inplace=True, backup='.bak') as file:
        for line in file:
            print(line.replace(OLD_COLOR, NEW_COLOR), end='')
            
    print("Done! Backup saved as .bak")

if __name__ == "__main__":
    mass_color_replace()
```



> [!NOTE]
> **Summary Strategy**
>
> If you have to do something **once**, use the Tableau UI.  
> If you have to do something **50 times** (like aligning 50 icons, renaming 50 fields, or changing 50 colors), **use Python and XML**.


### Formatting & Visual Consistency ( The "Pixel Perfect" Scripts)
1.  **The "Padding Police":** Scan every container and object in the workbook and force **Outer Padding** to 0 and **Inner Padding** to 4 (or your standard) to remove unwanted whitespace.
2.  **Global Font Enforcer:** Find every instance of "Times New Roman" or default fonts in titles, axes, and headers and replace them with your company’s standard font (e.g., "Roboto").
3.  **Title Center-Aligner:** Loop through every worksheet placed on a dashboard and ensure the title alignment is set to `Center` instead of the default `Left`.
4.  **Logo Swapper:** Locate the image path for your company logo object on every dashboard and update it to a new file path (great for rebranding).
5.  **Dashboard Sizer:** Force every dashboard in a workbook to exact dimensions (e.g., 1920x1080) to ensure no "Automatic" sizing slips through.
6.  **Grid Liner:** Turn off all Grid Lines and Zero Lines on every sheet in the workbook instantly (the "Clean Look" script).

### Layout & Organization
7.  **The "Legend Aligner":** Find all floating legends and move them to a specific X/Y coordinate (like the top right corner) on every dashboard.
8.  **Container Renamer:** Programmatically rename layout containers based on their content (e.g., if it contains "Sales Sheet", rename the container "Sales Container") to make the Layout pane readable.
9.  **Floating to Tiled Converter:** (Advanced) Read coordinates of floating objects and calculate the nearest Tiled structure (hard, but possible for simple grids).
10. **Tab Reorder-er:** Sort the sheets and dashboards in the bottom tab bar alphabetically or by a specific naming convention (e.g., `DB_` first, `QC_` last).

### Content & Text Management
11. **Tooltip Disclaimer Injector:** Append a standard legal text string (e.g., *"Confidential Data - Do Not Share"*) to the bottom of the tooltip on every single sheet.
12. **Typo Hunter:** Export all static text (titles, text boxes, captions) to a CSV to run a spell-check, then inject the corrected text back in.
13. **Dynamic Title Updates:** Replace hardcoded years (e.g., "2023 Performance") in all titles with a parameter reference (e.g., `<Parameters.Year> Performance`).
14. **Alias Manager:** Extract all field aliases to Excel, clean them up, and write them back (easier than the Alias menu in Desktop).

### Data & Calculations
15. **The "Copy" Killer:** Find all fields ending in `(copy)` or ` 1`, ` 2` and strip the suffix to clean up the Data Pane.
16. **Comment Injector:** Add a standard comment block to the top of every Calculated Field XML (e.g., `// Author: Data Team // Date: 2024`) for governance.
17. **Calculation Prefixing:** Automatically add `c_` to the start of every calculated field name and update all references to it in other formulas so nothing breaks.
18. **Number Format Standardizer:** Find all currency fields and force them to 0 decimal places or specific currency symbols ($ vs £).
19. **Parameter Defaulter:** Reset the "Current Value" of all parameters to their "Default Value" (useful before publishing to ensure a clean state).

### Governance & Audit (The "Detective" Scripts)
20. **Custom SQL Extractor:** Scrape the XML to find every instance of Custom SQL and save them to `.sql` files for your DBAs to review.
21. **Hardcoded Filter Alert:** Scan all filters for hardcoded strings (e.g., `User = "John Doe"`) which might indicate a security flaw.
22. **Unused Field Finder:** List all columns in the datasource that are *never* referenced in any sheet, calculation, or tooltip (helps you reduce extract size).
23. **Broken Reference Scout:** Search for the XML tag that indicates a broken field (red exclamation mark) and list the sheet names where they exist.
24. **Complexity Scorer:** Count the number of Marks, Calculations, and Sheets per dashboard to generate a "Complexity Score" report for performance tuning.

### Migration & Environment
25. **Connection Switcher:** Change the Server Address and DB Name for all connections from "Staging_DB" to "Production_DB" in one go.
26. **Version Downgrader:** (The classic hack) Modify the `version='...'` tag in the XML header to try and open a v2024 file in v2023 Desktop (works if no new features are used).
27. **Workbook Merger:** Copy specific `<worksheet>` XML blocks from Workbook A and insert them into Workbook B (requires careful ID management).
28. **Extract Path Updater:** If you moved your local `.hyper` files to a new folder, update the file paths in the workbook without manually locating each one.

### Workflow Automations
29. **Sheet Un-hider:** Instantly unhide every sheet in the workbook (useful for debugging someone else's messy workbook).
30. **Action Auditor:** List all Dashboard Actions (Filters, URL actions) and their source/target sheets to visualize the navigation flow.

### Clean-Up & Optimization (The "Janitor" Scripts)
31. **The "Phone Layout" Destroyer:** Automatically delete the auto-generated "Phone" and "Tablet" layouts from every dashboard in the XML (these often break the design and are tedious to delete manually).
32. **Parameter Pruner:** Scan all parameters, check if they are referenced in any calculated field or filter, and delete the ones that are orphans.
33. **Folder Organizer:** Define a mapping (e.g., "Field starts with `Sales_` -> Move to Folder `Sales Metrics`") and have Python rearrange your Data Pane folder structure in the XML.
34. **Custom Shape Cleaner:** Identify shape files referenced in the workbook that represent "null" or "default" assignments and strip them out to reduce file size.
35. **Reference Line Labeler:** Find every reference line in the workbook and force the Label settings to `Value` or `Computation` instead of `None`.
36. **Axis Ranger:** Force all axes on specific charts (e.g., "Trends") to have `Fixed` start points of 0 instead of `Automatic` to prevent misleading visuals.
37. **Dual Axis Synchronizer:** Scan for dual-axis charts and check the XML flag for `synchronized='true'`. If it's false, force it to true (prevents the "misleading scale" error).
38. **ZN() Wrapper:** Automatically wrap every measure used in the view in a `ZN()` function within the XML logic to handle nulls as zeros without creating new calculated fields.
39. **Sort Order Enforcer:** Ensure that every specific dimension (e.g., "Month") is set to "Sort by Field" (e.g., "Date") rather than "Data Source Order".

### Localization & Translation (The "Enterprise" Scripts)
40. **The "Auto-Translator":** Extract all Dashboard Titles, Text Objects, and Parameter Display Names, run them through Google Translate API (via Python), and inject the translated text back into the XML for a Spanish/French version.
41. **Currency Symbol Swapper:** Regex replace all instances of `format='$#,##0'` with `format='€#,##0'` for regional deployment.
42. **Date Format Standardizer:** Force all date fields to use `dd/mm/yyyy` (UK/Global) instead of the default `mm/dd/yyyy` (US).

### Security & Compliance
43. **PII Scanner:** Scan all field names and custom SQL for keywords like "SSN", "CreditCard", "Email", or "Salary". Generate an alert report if found.
44. **RLS Verifier:** Check if the workbook connects to a sensitive datasource but *lacks* a User Filter or RLS calculation.
45. **Watermark Injector:** Inject a transparent background image object containing "CONFIDENTIAL" into the XML of every dashboard layer.
46. **Web Object Whitelister:** Scan for "Web Page" objects and extract the URLs to ensure no one is embedding unapproved or insecure sites (http vs https).
47. **Extract Encryption Checker:** (Server API) Audit all published data sources to ensure "Encryption at Rest" is enabled.

### DevOps & Version Control
48. **XML Diff / Change Log:** Compare the XML of `Sales_Dashboard_v1.twb` and `Sales_Dashboard_v2.twb` to generate a readable text report of exactly what changed (e.g., "Changed Color on Sheet 1", "Modified Calculation X").
49. **Logic Patcher:** You discovered a bug in a calculation used in 20 different workbooks. Write a script to find that specific formula string and replace it with the corrected one across all 20 files.
50. **Data Type Enforcer:** Ensure that specific fields (e.g., "Customer ID") are always set to `String` (to prevent commas) and not `Integer` in the metadata.
51. **Workbook Splitter:** Take a massive workbook with 50 dashboards and split it into 5 separate `.twb` files (Sales, HR, Marketing) by parsing and migrating specific `<dashboard>` and `<worksheet>` tags.
52. **Template Injector:** Insert a standard "Header" and "Footer" container (with copyright and logo) into a blank workbook to create a "Starter Template" automatically.

### Data Source Management
53. **Description Propagator:** Connect to your Data Warehouse (Snowflake/BigQuery) to get column descriptions, then inject them into the Tableau Field `description` tag so users see tooltips on hover in the Data Pane.
54. **Extract Filter auditor:** List all "Extract Filters" hidden in the XML to ensure you aren't accidentally excluding data at the connection level.
55. **Join Type Auditor:** Report on whether connections are using Inner, Left, or Right joins (often hidden in the UI until you check the Logical Layer).
56. **Unused Column Hider:** Analyze the usage of columns and modify the XML `<connection>` settings to "Hide" unused columns before creating an extract (improves performance).
57. **Relationship Nudger:** (Advanced) Modify the "Performance Options" in the Logical Data Model (Relationships) from "Many-to-Many" to "One-to-Many" if you know the cardinality, improving query speed.

### Server & User Automation (Tableau Server Client - TSC)
58. **The "Stale User" Booter:** List users who haven't logged in for 90 days and automatically unlicensed them to save seat costs.
59. **Subscription Cloner:** Copy all email subscriptions from one workbook to another (useful when replacing a report with a V2 version).
60. **Tag Manager:** Bulk apply tags (e.g., "Certified", "Finance") to all workbooks in a specific project.
61. **Extract Failure Pattern Detector:** Query the "Background Tasks" to find extracts that fail specifically on "Mondays" or "at 9 AM" to identify resource contention.
62. **Group Sync:** Script a sync between an internal API (HR system) and Tableau Server Groups if Active Directory isn't available.
63. **View Count Resetter:** (Hack) Re-publish a workbook with a slightly different name and delete the old one to "reset" view counts for a fresh launch.
64. **Permission Auditor:** Generate a matrix (CSV) showing `User | Workbook | Permission Level` for an audit.
65. **Custom View Deleter:** Delete all user-created "Custom Views" on a dashboard that are older than 1 year to declutter the server.
66. **Owner Changer:** Bulk update the "Owner" of 100 workbooks from "Employee A" (who left) to "Employee B".
67. **Thumbnail Generator:** Download the preview image of every dashboard via API to display in a custom internal company portal.

### Advanced UX Hacking
68. **Filter Scope Enforcer:** Find all filters on a dashboard and change their scope from "Only This Sheet" to "All Using This Data Source" in the XML.
69. **Navigation Button Styler:** Find all "Navigation" buttons and enforce a specific border radius, background color, and font style.
70. **URL Action Validator:** Extract all URL actions and run a Python `requests.get()` on them to ensure they don't return 404 errors.
71. **Dashboard Size Standardizer:** Identify dashboards set to "Range" and force them to "Fixed Size" (e.g., 1600x900) to ensure rendering speed.
72. **Floating Object "Snapper":** Round the X, Y, W, H coordinates of all floating objects to the nearest 10 pixels to make them look perfectly aligned on a grid.
73. **Transparent Sheet Maker:** Bulk set the background color of all worksheets to `None` (Transparent) to allow dashboard background images to show through.

### Testing & QA
74. **Filter Combination Tester:** Use Selenium + Python to open the dashboard in a browser and cycle through every filter combination to check for "No Data" blank screens.
75. **Performance Recording Parser:** specific Automate the parsing of Tableau Performance Recording workbooks to identify the slowest query without opening the file manually.
76. **Alert Threshold Checker:** Scan the XML for Data Driven Alerts and report what the threshold values are (e.g., "Alert if Sales < 5000").
77. **Empty Dashboard Detector:** Identify dashboards that have no sheets on them (work in progress) and flag them.
78. **Spelling Checker:** Extract all text from Text Objects and Titles, run a Python spell check, and report typos.

### Specific Weird Fixes
79. **"Automatic" Font Fixer:** Find any text formatted as "Automatic" color (which can appear black or white depending on background) and force it to a specific HEX code.
80. **Workbook Version Downgrader:** Script the hack to change the XML build version header so a newer workbook opens in an older Tableau Desktop (with risks).
