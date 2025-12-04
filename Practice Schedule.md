# Daily Tableau Practice Schedule

## From Exercises To A Concrete Plan

Below is a structured daily schedule that uses the exercises we outlined and turns them into an 8 week, 5 day per week plan. Weekends are free for rest or catch up.

You can adjust the pace, but this assumes roughly 60 to 90 minutes of focused work per day.

I will reference exercise numbers from the earlier list where useful, but also restate what you actually do.

## Overview Of The 8 Week Plan

* Weeks 1 and 2: Foundations and interface, data connections, basic charts
* Weeks 3 and 4: Data modeling, calculations, LODs
* Weeks 5 and 6: Advanced charts, dashboards, UX and interactivity
* Week 7: Tableau Prep, data cleaning, extract strategies
* Week 8: Performance, Server, governance, domain projects and QA

You will touch almost all 130 exercises by the end.

## Week 1 – Foundations and Interface Fluency

### Goal

Get fully comfortable with the interface, workbook structure, basic Tableau thinking, and pill behavior.

### Day 1

* Exercise 1: Identify and label every major UI component in a blank workbook.
* Exercise 2: Rearrange the workspace to a layout that feels natural.
* Exercise 8: Take a small dataset and write down the grain before building anything.

### Day 2

* Exercise 3: Create and apply a custom color palette.
* Exercise 4: Practice hiding and unhiding fields in the Data Pane.
* Exercise 10: Switch fields between discrete and continuous and capture how the view changes.

### Day 3

* Exercise 5: Create TWB and TWBX versions of the same workbook, compare size and behavior.
* Exercise 6: Publish a data source only and connect from another workbook.
* Exercise 7: Intentionally break a workbook by moving or renaming source files, note the error patterns.

### Day 4

* Exercise 11: Build a worksheet using only dimensions.
* Exercise 12: Build a worksheet using only measures.
* Exercise 13: Mix discrete and continuous pills in various combinations and document the results.

### Day 5

* Exercise 9: Build a simple dashboard without Show Me, choosing marks manually.
* Combine Exercises 1 to 4 into a mini ritual: open workbook, set layout, hide noise fields, set palette.
* End-of-week reflection: write a short note on how Tableau’s interface and pills actually “think.”

## Week 2 – Data Connections, Metadata, and Grain

### Goal

Become fluent in connecting to files, cleaning headers, pivoting, and understanding grain and integrity.

### Day 6

* Exercise 14: Connect to an Excel file with messy headers, use data interpreter and then clean it.
* Exercise 15: Connect to a CSV with weird delimiters, fix the schema and field types.

### Day 7

* Exercise 16: Use a wildcard union to combine multiple Excel sheets.
* Exercise 20: Pivot a wide Excel dataset into a tall format.
* Exercise 21: Split a composite key field into separate usable fields.

### Day 8

* Exercise 17: Connect to SQL Server (or any RDBMS you have), use Initial SQL if possible.
* Exercise 18: Publish a live data source with embedded credentials.
* Exercise 19: Convert the same data source to an extract and compare responsiveness.

### Day 9

* Exercise 22: Use the Metadata Grid to clean names and data types across a data source.
* Exercise 23: Create a join that clearly produces duplicate rows, then explain why in writing.
* Exercise 24: Fix those duplicates using a FIXED LOD or other logic.

### Day 10

* Exercise 25: Build a relationship model where cardinality matters and test its behavior (filtering, aggregation).
* Rebuild a simple dashboard using the cleaned, modeled data from this week.
* End of week: Summarize what “grain” and “relationships vs joins” mean in your own words.

## Week 3 – Physical and Logical Modeling

### Goal

Understand relationships vs joins, unions, and grain stabilization in more complex setups.

### Day 11

* Exercise 26: Build a model with two fact tables and shared dimensions using relationships.
* Exercise 28: Build the same logic using physical joins and compare behavior.

### Day 12

* Exercise 27: Add ambiguous relationships and observe what happens to aggregations and filters.
* Exercise 29: Create inner, left, right, and full outer joins on the same two tables and document differences.

### Day 13

* Exercise 30: Introduce null join keys and test how each join type handles them.
* Exercise 31: Build a join using a custom join calculation and test correctness.

### Day 14

* Exercise 32: Union multiple CSV files with slightly different schemas.
* Exercise 33: Add dummy fields to align schemas and re-run the union.
* Exercise 34: Simulate an incremental load using unions and a date range.

### Day 15

* Exercise 35: Build a scaffolding table to fill missing dates in a time series.
* Exercise 36: Handle irregular time series via densification, then visualize them.
* Exercise 37: Create a basic fact/dimension structure, validate uniqueness of keys.

## Week 4 – Calculations and LODs

### Goal

Get comfortable with calculation syntax, string and date work, then move into LOD expressions.

### Day 16

* Exercise 38: Create at least 10 calculated fields covering arithmetic, logical, and simple conditional logic.
* Exercise 39: Create nested logical expressions with edge cases (null, zero, negative).

### Day 17

* Exercise 40: Write two or three reusable calculation templates (for example: safe division, null-safe KPI).
* Exercise 41: Clean messy product names using REGEXP_REPLACE or equivalent.
* Exercise 42: Extract domains from email addresses.

### Day 18

* Exercise 43: Build a simple fuzzy matching logic (even approximate) using string operations.
* Exercise 44: Build manual bins for a metric like sales, not using Tableau’s automatic bin feature.
* Exercise 45: Implement a weighted average over a grouping such as region or product.

### Day 19

* Exercise 46: Normalize values across dimensions (for example z score or min max scaling).
* Exercise 47: Use parameters to create a dynamic date range filter.
* Exercise 48: Build a fiscal calendar with custom fiscal quarters.

### Day 20

* Exercise 49: Implement working days only logic using dates and logic functions.
* Exercise 50: Rebuild an aggregated metric using FIXED.
* Exercise 51: Rebuild the same metric using INCLUDE and EXCLUDE and compare all three.

## Week 5 – LOD Mastery and Advanced Charts

### Goal

Make LODs instinctive and build more complex chart types.

### Day 21

* Exercise 53: Use FIXED to find unique customers per region.
* Exercise 54: Compute customer lifetime value using FIXED.
* Exercise 55: Remove double counting in some metric via FIXED.

### Day 22

* Exercise 56: Use INCLUDE for row-level contribution percentages.
* Exercise 57: Use INCLUDE to calculate segment level scores.
* Exercise 58: Use INCLUDE to enrich a cohort style table.

### Day 23

* Exercise 59: Use EXCLUDE to create a smoothed high level KPI from detailed data.
* Exercise 60: Build EXCLUDE based actual vs aggregated baseline comparison.

### Day 24

* Exercise 61: Construct a nested LOD for multi level segmentation (for example customer within region within country).
* Exercise 62: Build nested FIXED inside INCLUDE and observe performance.
* Exercise 63: Create a generic reusable LOD template specifically for cohort analysis.

### Day 25

* Exercise 64: Build basic bar, line, scatter, tree map, histogram manually.
* Exercise 65: Rebuild the same charts without Show Me again, this time faster.
* Exercise 66: Build a KPI panel with sparklines and color coded thresholds.

## Week 6 – Advanced Visuals, Dashboards, and UX

### Goal

Move from charts to interactive analytical experiences.

### Day 26

* Exercise 67: Build a waterfall chart for a revenue bridge.
* Exercise 68: Build a data densification based Sankey diagram.
* Exercise 69: Build a radial chart for a cyclical metric.

### Day 27

* Exercise 70: Build trellis (small multiples) charts for one metric across categories.
* Exercise 71: Load a shapefile and build a custom spatial visual.
* Exercise 72: Create a multi layer map with at least two different mark types.

### Day 28

* Exercise 73: Create custom territories using polygons.
* Exercise 74: Perform a spatial join and visualize the result.
* Exercise 75: Create a visualization that encodes meaning using only size.

### Day 29

* Exercise 76: Create another view that uses only color to encode change or status.
* Exercise 77: Build a view where position is the main encoding, color is secondary.
* Exercise 78: Review all views and explain which encoding works best for each use case.

### Day 30

* Exercise 79: Deliberately create a cluttered, bad dashboard with poor charts.
* Exercise 80: Refactor that dashboard into a clean, perceptually sensible version.

## Week 7 – Dashboards, Interactivity, and Tableau Prep

### Goal

Tie it all together with dashboards and interactivity, then add Tableau Prep and data cleaning.

### Day 31

* Exercise 81: Build a tiled only dashboard layout.
* Exercise 82: Build the same dashboard using floating layout.
* Exercise 83: Design a mobile layout for one of your existing dashboards.

### Day 32

* Exercise 84: Build a dashboard template you intend to reuse for future work.
* Exercise 85: Add filter, highlight, and URL actions to one dashboard.
* Exercise 86: Add a parameter driven metric selector.

### Day 33

* Exercise 87: Build drill down hierarchies (for example country to state to city).
* Exercise 88: Build sheet switching using parameter or buttons.
* Exercise 89: Take a cluttered dashboard and consciously reduce cognitive load.

### Day 34

* Exercise 90: Create standardized KPI tiles to reuse across multiple dashboards.
* Exercise 91: Create a guided story with annotations that leads a user through a finding.
* Exercise 92: Build a narrative dashboard for one business question.

### Day 35

* Exercise 95: In Tableau Prep, build a flow that fixes messy headers and field names.
* Exercise 96: Build a multi branch flow that normalizes categories.
* Exercise 97: Build a flow that outputs both CSV and Hyper from the same input.

## Week 8 – Prep Conductor, Extracts, Performance, Server, and Domain Projects

### Goal

Finish with automation, performance tuning, governance, and domain flavoured dashboards.

### Day 36

* Exercise 98: Use Prep to remove duplicates from a dataset.
* Exercise 99: Extract nested JSON into flat columns.
* Exercise 100: Normalize category labels across multiple input sources.

### Day 37

* Exercise 101: Build a parameterized Prep flow (for example filter by date or region).
* Exercise 102: Build a flow that splits a field into three hierarchy levels.
* Exercise 103: Build a daily snapshot generator flow.

### Day 38

* Exercise 104: Publish a Prep flow to Server or Cloud.
* Exercise 105: Schedule the flow and verify it executes successfully.
* Exercise 106: Intentionally break a flow and diagnose the error cause.

### Day 39

* Exercise 107: Implement incremental extract logic for a data source.

* Exercise 108: Configure extract partitions where appropriate.

* Exercise 109: Validate the extract schema against the source.

* Exercise 110: Run Performance Recorder on a complex dashboard.

* Exercise 111: Reduce mark count and measure performance improvement.

* Exercise 112: Replace some heavy LODs with preaggregated fields or views.

### Day 40

* Exercise 113: Convert table calculations to equivalent LODs where possible, compare performance.

* Exercise 114: Compare live vs extract vs materialized view driven dashboards for one use case.

* Exercises 124 to 127:

  * Build a finance P and L dashboard.
  * Build a healthcare outcomes or utilization dashboard.
  * Build a sales performance dashboard.
  * Build an ecommerce funnel visualization.

* Exercises 128 to 130:

  * Create a QA checklist for dashboards.
  * Create a data quality test suite.
  * Create a version control template for multi developer Tableau work.

## What To Do After These 8 Weeks

* Repeat some weeks at higher difficulty with larger and messier data.
* Turn your best dashboards into a portfolio.
* Start adopting governance practices even in your personal projects.
* Begin mentoring or explaining your dashboards to someone else. Teaching solidifies skill.
