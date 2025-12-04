# Tableau Mastery Curriculum

## Full Exercise Framework for All 12 Chapters

### A Practical, Hands-On Companion to the 750-Topic Roadmap

This is not a repetition of the roadmap.
This is the **exercise book** — a structured set of **practical, buildable, hands-on exercises** designed to turn the 750-topic conceptual roadmap into real skill.

Each chapter contains multiple exercise categories, ranging from foundational drills to advanced enterprise scenarios.
Every exercise is deliberately actionable.

# CHAPTER 1

# Tableau Foundations

## Exercises

### 1.1 Interface & Navigation Drills

1. Open a blank workbook and identify every major UI component.
2. Rearrange the workspace to your preferred layout.
3. Create a custom color palette and apply it to a sample dataset.
4. Practice hiding/unhiding fields in the Data Pane.

### 1.2 Workbook Structure Exercises

5. Create a TWB and TWBX version of the same workbook and compare file sizes.
6. Publish a data source-only file and connect to it from a new workbook.
7. Break a workbook intentionally by removing a required file — observe the error messages.

### 1.3 Thinking in Tableau Exercises

8. Take a dataset and identify the “grain” before building visuals.
9. Build a worksheet without using “Show Me” to force intentional mark selection.
10. Practice switching fields between continuous and discrete and noting how views change.

### 1.4 Pill Behavior Exercises

11. Create a chart using only dimensions.
12. Create a chart using only measures.
13. Mix discrete and continuous pills intentionally to observe axis behavior.

# CHAPTER 2

# Data Connections & Modeling

## Exercises

### 2.1 File Connection Drills

14. Connect to an Excel file with merged headers and clean it.
15. Connect to a CSV file with inconsistent delimiters and fix the schema.
16. Combine multiple Excel sheets using a wildcard union.

### 2.2 Database Connection Exercises

17. Connect to a SQL Server table and run Initial SQL.
18. Publish a live data source with embedded credentials.
19. Replace a live connection with an extract and compare performance.

### 2.3 Metadata Exercises

20. Pivot a “wide” Excel dataset into long format inside Tableau.
21. Split a composite key (ex: “Region-State-City”) into 3 usable fields.
22. Use the Metadata Grid to refactor field names and types.

### 2.4 Grain & Integrity Exercises

23. Create a join that results in duplicate rows — diagnose the issue.
24. Fix duplicate rows using FIXED LOD logic.
25. Build a relationship model where cardinality matters and test the behavior.

# CHAPTER 3

# Physical Layer & Logical Layer

## Exercises

### 3.1 Relationship Modeling

26. Build a model with two fact tables and common dimensions.
27. Add ambiguous relationships and observe query folding.
28. Compare the same dashboard using relationships vs physical joins.

### 3.2 Join Mechanics

29. Create inner, left, right, and full outer joins using the same tables.
30. Introduce null join keys and observe the effects.
31. Create a join using a custom calculation (ex: LEFT([Code], 3)).

### 3.3 Union Workouts

32. Union multiple CSV files with slightly mismatched schemas.
33. Add dummy fields to make schemas compatible.
34. Build a union-based incremental load simulation.

### 3.4 Grain Stabilization

35. Create a scaffolding table to fill missing dates.
36. Build a time-series with irregular spacing and fix it via densification.
37. Create a fact/dimension structure and validate uniqueness.

# CHAPTER 4

# Calculation Theory

## Exercises

### 4.1 Basic Calculation Drills

38. Build 10 custom calculated fields covering all operators.
39. Create nested logical expressions and test all edge-cases.
40. Write reusable calculation templates.

### 4.2 String Calculation Workouts

41. Clean messy product names using REGEXP_REPLACE.
42. Extract domain names from email addresses.
43. Build fuzzy matching using text similarity logic.

### 4.3 Numeric Calculation Workouts

44. Build custom bins manually.
45. Create weighted average calculations for sales data.
46. Normalize values across dimensions.

### 4.4 Date Calculation Workouts

47. Create a dynamic date range using parameters.
48. Build fiscal calendars with custom quarter boundaries.
49. Write calculations for working days (excluding weekends).

# CHAPTER 5

# LOD Expressions

## Exercises

### 5.1 LOD Fundamentals

50. Rebuild an aggregated metric using FIXED.
51. Rebuild the same metric using INCLUDE.
52. Rebuild it again using EXCLUDE — compare differences.

### 5.2 FIXED LOD Applications

53. Find unique customers per region.
54. Compute customer lifetime value.
55. Build a model that removes double-counting with FIXED.

### 5.3 INCLUDE LOD Applications

56. Build per-row contribution percentages.
57. Build segment-level scoring.
58. Produce row-level enrichment for cohort tables.

### 5.4 EXCLUDE LOD Applications

59. Remove fine-grain detail for high-level KPIs.
60. Use EXCLUDE to compare actual vs aggregated baselines.

### 5.5 Nested LOD Workouts

61. Build nested LOD for multi-level segmentation.
62. Create nested FIXED inside INCLUDE for dense metrics.
63. Build a reusable LOD-based template for cohorts.

# CHAPTER 6

# Chart Construction

## Exercises

### 6.1 Standard Charts

64. Build bar, line, scatter, tree map, histogram from scratch.
65. Rebuild the same charts without Show Me.
66. Build sparkline KPIs with color logic.

### 6.2 Advanced Charts

67. Build a waterfall chart manually.
68. Create a dense Sankey using data densification.
69. Build a radial chart.
70. Build small multiples (trellis charts).

### 6.3 Geospatial Exercises

71. Load a shapefile and clean spatial fields.
72. Build multi-layer maps.
73. Create custom territories using polygons.
74. Perform spatial joins.

### 6.4 Visual Encoding

75. Encode meaning using only size.
76. Encode using color only.
77. Encode using position only.
78. Build a visualization with all marks deliberately chosen.

### 6.5 Chart Anti-Pattern Diagnosis

79. Break a dashboard using bad charts — then fix it.
80. Rebuild charts with correct encoding.

# CHAPTER 7

# Dashboards & UX

## Exercises

### 7.1 Dashboard Layout

81. Build a dashboard using tiled only.
82. Build the same dashboard using floating only.
83. Design a mobile-first layout.
84. Create a dashboard template for future use.

### 7.2 Interactivity

85. Build filter actions, highlight actions, URL actions.
86. Build a parameter-driven metric selector.
87. Build a drill-down tree hierarchy.
88. Build a sheet-switching panel using buttons.

### 7.3 UX Thinking

89. Take a cluttered dashboard and reduce cognitive load.
90. Create standardized KPI tiles across multiple dashboards.
91. Create a guided storytelling flow using annotations.

### 7.4 Storytelling

92. Build a narrative dashboard with supporting panels.
93. Use story points for a business walkthrough.
94. Convert a narrative dashboard into an exploratory dashboard.

# CHAPTER 8

# Tableau Prep

## Exercises

### 8.1 Prep Builder

95. Build a flow that cleans messy headers.
96. Build a multi-branch flow that normalizes data.
97. Build a flow that outputs both CSV and Hyper.

### 8.2 Data Cleaning

98. Remove duplicates using Prep logic.
99. Extract nested JSON values.
100. Normalize categorical values (ex: “NY,” “New York,” “N.Y”).

### 8.3 Flow Logic

101. Build a parameterized flow.
102. Build a flow that splits a field into 3 levels.
103. Build a flow for daily snapshot generation.

### 8.4 Prep Conductor

104. Publish a flow.
105. Schedule a flow.
106. Diagnose a failing flow.

### 8.5 Extract Strategy

107. Build incremental extract logic.
108. Build extract partitions.
109. Validate extract schema integrity.

# CHAPTER 9

# Performance Engineering

## Exercises

110. Run Performance Recorder on a slow dashboard.
111. Reduce mark count and measure improvement.
112. Replace expensive LODs with preaggregated fields.
113. Convert table calcs into equivalent LODs.
114. Compare performance: live vs extract vs materialized DB view.

# CHAPTER 10

# Server & Governance

## Exercises

115. Publish dashboards with different permission models.
116. Create a project hierarchy for a department.
117. Set row-level security with user filters.
118. Track content lineage.
119. Build a certified data source workflow.

# CHAPTER 11

# Automation & APIs

## Exercises

120. Use the JavaScript API to embed a dashboard.
121. Automate an extract refresh via API.
122. Query metadata via Metadata API.
123. Build a simple extension (hello-world).

# CHAPTER 12

# Domain-Specific & Testing

## Exercises

124. Build a finance P&L dashboard.
125. Build a healthcare patient outcome tracking dashboard.
126. Build a sales performance dashboard.
127. Build an ecommerce funnel visualization.
128. Build a QA checklist for dashboards.
129. Create a data quality test suite.
130. Build a version control template for multi-team development.
