# 1 Table of Contents

1. Table of Contents
2. Introduction to Visual First Computation
3. VizQL: The Visual Query Language Engine
4. The View as the Computation Context
5. Tiers of Computation in Tableau
6. The Hyper Data Engine Role
7. Headless Computation with VizQL Data Service (2025 Update)
8. Reasoning Summary
9. Points That Require Verification or Are Uncertain

# 2 Introduction to Visual First Computation

Tableau operates as a visual first computation engine, a paradigm where the visual arrangement of data fields determines the granularity and scope of database queries. Unlike cell based tools (Excel) or code based tools (Python, SQL), where computation is defined explicitly by formulas or scripts, Tableau derives computation logic directly from the graphical user interface. This architecture relies on VizQL (Visual Query Language), a proprietary technology that translates drag and drop actions into optimized database queries [1].

In this model, the visualization is not merely a display layer but the definition of the query itself. Every mark on a canvas represents a computed tuple resulting from a specific aggregation level. As of 2024 and 2025, this paradigm has evolved to include "Headless BI" capabilities, allowing the computation engine to be accessed programmatically via APIs while retaining the visual computation logic [2].

# 3 VizQL: The Visual Query Language Engine

VizQL serves as the translator between the user's visual actions and the underlying machine language (SQL, MDX, or TQL). It interprets the placement of fields on shelves (Rows, Columns, Filters) to construct a query pipeline.

## 3.1 The Translation Workflow

The process of converting a visual interaction into a computation involves distinct steps that define the resulting dataset.

**Step by Step Workflow**
1.  **Field Placement:** The user drags a discrete field (Dimension) to the Rows shelf. VizQL identifies this as a grouping key.
2.  **Aggregation Definition:** The user drags a continuous field (Measure) to the Text mark. VizQL defaults this to a summation operation (`SUM`).
3.  **Query Compilation:** The engine constructs a query where Dimensions become the `GROUP BY` clause and Measures become the aggregation in the `SELECT` clause.
4.  **Rendering:** The database returns the result set, and VizQL maps these values to visual properties (x position, y position, color, size).

**Comparison to Alternatives**
In a SQL first approach, an analyst must mentally construct the `GROUP BY` logic before writing code. In Tableau, the visual feedback loop is immediate. If the analyst removes a Dimension from the view, the engine immediately recomputes the query at a higher level of aggregation. This reduces the cognitive load required to perform multi pass aggregations [3].

**Implementation Note**
VizQL optimization ensures that only data required for the current visual state is queried. This is known as "Query Culling." If a dashboard contains hidden sheets or unused fields in a data source, they are excluded from the execution pipeline to conserve resources [1].

## 3.2 Visual Specifications as Logical Queries

The specific shelf where a field is placed dictates the logical role of that field in the computation.

*   **Rows/Columns:** These shelves define the primary breakdown of the data (the "headers" of the pivot table).
*   **Filters:** These act as the `WHERE` or `HAVING` clauses, reducing the domain of the computation.
*   **Detail:** Placing a dimension on the Detail card adds it to the `GROUP BY` clause without visualizing it as a header, effectively slicing the marks further without expanding the matrix structure.

# 4 The View as the Computation Context

In a visual first engine, the "View" (the combination of all active shelves) defines the Level of Detail (LOD) for the computation.

## 4.1 Granularity and Aggregation

The most critical concept in visual computation is that the presence or absence of a dimension pill determines the result of a calculation.

**Workflow for Controlling Granularity**
1.  **Coarse Granularity:** Place only `Region` on Rows and `Sales` on Text. The computation returns one value per Region.
2.  **Fine Granularity:** Add `Category` to Rows. The engine automatically recalculates to return one value per Region/Category pair.
3.  **Visual Verification:** The analyst verifies the logic by observing the number of marks (data points) displayed in the bottom left corner of the interface.

**Why It Matters**
This behavior prevents common aggregation errors found in spreadsheet tools, where summing a column that contains duplicate rows (due to joins) yields incorrect results. Tableau's visual first engine aggregates *after* the join logic is resolved, ensuring mathematical correctness relative to the visual display [4].

## 4.2 Z-Order and Order of Operations

The sequence in which Tableau computes values is strict and impacts how visuals render.

**The Query Pipeline Steps**
1.  **Extract Filters:** Reduces the data volume locally.
2.  **Data Source Filters:** Hides data from the workbook globally.
3.  **Context Filters:** Creates a temporary table or subset of data.
4.  **Dimension Filters:** Filters data prior to aggregation.
5.  **Aggregation:** The core computational step (SUM, AVG, MIN, MAX).
6.  **Table Calculations:** Post aggregation computations performed locally on the result set (e.g., Running Total) [5].

**Advanced Variation**
Users can manipulate this pipeline using Context Filters. By adding a Dimension filter to Context (turning the pill gray), the user forces that filter to execute *before* Fixed Level of Detail (LOD) expressions, altering the computation scope [5].

# 5 Tiers of Computation in Tableau

Tableau performs computations at three distinct tiers, each optimized for different stages of the analysis.

## 5.1 Tier 1: Row Level Computations

Row level calculations are performed on every single record in the underlying database *before* aggregation.

**Step by Step Implementation**
1.  Create a calculated field: `[Sales] - [Cost]`.
2.  The engine passes this logic to the database.
3.  For a SQL source, this becomes `SELECT (Sales - Cost) ...`.
4.  This is useful for normalizing data or creating bins/groups that act as dimensions.

**Practical Tip**
Avoid complex string manipulation at the row level if working with massive datasets, as this operation runs for every row. Materialize these calculations in the data source (ETL layer) when possible [3].

## 5.2 Tier 2: Aggregate Level Computations

These calculations occur at the granularity defined by the View.

**When to Use**
Use aggregation for ratios (e.g., `SUM(Profit) / SUM(Sales)`). This ensures the ratio is calculated on the total values for the group, rather than averaging the ratios of individual rows, which would be mathematically incorrect (Simpson's Paradox).

**Verification**
Tableau visualizes aggregated fields with an aggregation prefix (e.g., `SUM(Profit)`). If a field lacks this prefix in a visual (showing just `Profit`), it implies row level detail or a disaggregated view, which can be performance intensive [4].

## 5.3 Tier 3: Table Calculations (Visual Post Processing)

Table Calculations are unique to the visual first engine. They compute values based on the *relative position* of marks in the generated visual, rather than the intrinsic data structure.

**Step by Step Workflow**
1.  The database returns aggregated results to Tableau's cache.
2.  The user selects a "Quick Table Calculation" like "Percent Difference."
3.  The engine computes the value for Mark A by comparing it to Mark B (the previous mark).
4.  **Directionality:** The user must define the "Compute Using" direction (Table Across, Table Down). Changing this direction changes the result immediately without requerying the database.

**Why It Matters**
Table Calculations allow for "Second Pass Aggregation" (e.g., the average of a sum). They are essential for ranking, running totals, and moving averages, which are difficult to construct in standard SQL [5].

# 6 The Hyper Data Engine Role

Underpinning the visual computation is the Hyper Data Engine, an in memory, column store database technology optimized for fast ingest and analytical query processing.

## 6.1 Just in Time Compilation

Hyper uses LLVM (Low Level Virtual Machine) based Just in Time (JIT) compilation to optimize queries generated by VizQL.

**Workflow**
1.  VizQL generates a logical query tree based on the dashboard state.
2.  Hyper compiles this tree into custom machine code (bytecode) specifically for that query.
3.  The compiled code executes in parallel across available CPU cores.

**Comparison to TDE**
Legacy Tableau Data Extracts (TDE) were row oriented and slower at aggregation. Hyper is column oriented, meaning it reads only the specific columns required for the visual (e.g., just `Sales` and `Region`), ignoring unused columns like `Customer Name`. This aligns perfectly with the visual first approach where users often interact with only a subset of fields at a time [6].

# 7 Headless Computation with VizQL Data Service (2025 Update)

In late 2024 and throughout 2025, Tableau introduced the VizQL Data Service (VDS), essentially "headless" Tableau. This allows external applications to leverage the Tableau computation engine via API without rendering a visualization [2].

## 7.1 Decoupling Logic from Presentation

VDS permits developers to send a JSON payload defining dimensions, measures, and filters to the Tableau Cloud or Server API. The engine processes this request using the same VizQL logic used for dashboards and returns the computed data payload.

**Step by Step Workflow**
1.  **Define Model:** An analyst publishes a Data Source with calculated fields (e.g., `Net Profit Margin` with complex logic).
2.  **API Request:** A Python script sends a request to VDS: "Group by Region, Filter by Year 2025, Return Net Profit Margin."
3.  **Processing:** VizQL calculates the metric using the defined business logic, respecting all Tableau specific nuances (LODs, fiscal years).
4.  **Response:** The computed data is returned as JSON to the script.

**Why It Matters**
This transforms Tableau from purely a visualization tool into a centralized "Metrics Store." It ensures that a computation defined visually in Tableau (e.g., a complex churn rate calculation) yields the exact same number when queried by an automated slack bot or an embedded portal [7].

## 7.2 Integration with Tableau Pulse

Tableau Pulse, fully matured in the 2025 release cycle, utilizes this headless engine to generate "Metrics." Pulse automatically detects drivers and trends (e.g., "Sales are up because of the West region"). It relies on the visual first engine's ability to rapidly test multiple aggregation combinations (permutations of dimensions) to find statistically significant insights [2].

# 8 Reasoning Summary

This documentation characterizes Tableau as a "visual first" engine by tracing the lineage of a user interaction (drag and drop) through the VizQL translation layer to the final database query. The content distinguishes between the three tiers of computation (Row, Aggregate, Table Calc) which are fundamental to Tableau's architecture.

To satisfy the "post June 2024" requirement, I incorporated details on the **VizQL Data Service (VDS)** and **Tableau Pulse**. These features represent the most significant architectural shift in recent years, allowing the computation engine to be used "headlessly" via API (VDS) or through AI driven metrics (Pulse), as confirmed by search results referencing 2025 release notes and developer previews [2, 7]. The Hyper engine section explains the physical execution of these queries, ensuring the guide covers both the logical (VizQL) and physical (Hyper) layers.

Citations have been placed inline to support specific claims regarding the query pipeline, VDS, and the Hyper engine.

# 9 Points That Require Verification or Are Uncertain

1.  **VDS API Consistency:** The VizQL Data Service was in Developer Preview in late 2024 and General Availability in early 2025. The specific endpoint structure (URL paths) and payload keys (JSON schema) may have evolved slightly between the preview and the final 2025.1 release.
2.  **Hyper Parameter Tuning:** While Hyper automatically optimizes queries, specific advanced flags for memory management in the 2025 Server release may vary by deployment type (Linux vs. Windows containerization).
3.  **ASSUMPTION:** I assume the reader is using Tableau Cloud or Tableau Server 2025.1+ for the "VizQL Data Service" features. Users on older on premise versions (e.g., 2023.x) will not have access to these headless computation capabilities.

**References**
[1] Tableau Software, "VizQL Technology," Tableau.com.
[2] Tableau, "VizQL Data Service API," Tableau Help 2025.
[3] Salesforce, "Designing Efficient Workbooks," Tableau Whitepapers.
[4] Tableau, "Aggregation and Granularity," Tableau Training Manual.
[5] Salesforce/Tableau, "Tableau's Order of Operations," Help.Tableau.com, 2024.
[6] Tableau, "Hyper Data Engine Technology," Tableau Engineering Blog.
[7] Tableau, "Tableau Pulse and Metrics Layer," Release Notes 2024-2025.
