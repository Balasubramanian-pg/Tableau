# Tableau Mastery Roadmap

## 750 Topics Structured Into 12 Chapters

### A Deep, Textbook-Style Expansion

This is the full expanded roadmap: **750 distinct topics**, branching the earlier 400 into more granular, expert-level subfields. The document is intentionally structured as a *curriculum*, not a list, so you can drop it directly into Obsidian and grow from here.

Each topic is counted. No repetition. No filler.
Chapters flow from beginner to enterprise-grade mastery.

# CHAPTER 1

# Tableau Foundations

## (Topics 1–80)

### 1.1 Tableau’s Identity

1. The purpose Tableau serves in modern analytics
2. Tableau as a visual-first computation engine
3. How Tableau abstracts SQL for analysts
4. Why Tableau encourages exploratory analysis
5. The role of Tableau in self-service BI
6. When Tableau is preferable over Excel
7. When Tableau is preferable over Power BI
8. When Tableau is not the right tool
9. The difference between analysis and reporting in Tableau
10. Tableau’s evolutionary history

### 1.2 Tableau Products Ecosystem

11. Tableau Desktop core capabilities
12. Tableau Cloud role in collaborative analytics
13. Tableau Server infrastructure logic
14. Tableau Prep Builder for ETL
15. Tableau Prep Conductor inside enterprise pipelines
16. Tableau Public limitations
17. Tableau Mobile design considerations
18. Reader vs Server consumers
19. Viewer, Explorer, Creator license patterns
20. How licenses impact dashboard design

### 1.3 File Structures

21. TWB XML logic
22. TWBX storage behavior
23. Extract file structure (Hyper internals at a high level)
24. TDS data source metadata
25. TDSX packaged metadata
26. Bookmark usage patterns
27. Tableau logs directory types
28. Backgrounder logs vs desktop logs
29. Query logs vs extract logs
30. Workbook dependency chains
31. Embedded vs published data source architecture
32. Workbook portability issues
33. Data source version mismatches
34. Workbook version compatibility rules
35. Extract dependency tracking

### 1.4 Interface Fluency

36. Full data pane structure
37. Field categories inside data pane
38. Hiding vs grouping fields
39. Using custom folders
40. Custom sorting of fields
41. Dynamic search within data pane
42. Show Me logic
43. Marks card as a grammar of graphics
44. Dual-axis indicators in the interface
45. Pane vs Header differences
46. Multi-axis pane splitting
47. Tooltip editing layout
48. Status bar rendering logic
49. Worksheet tab management
50. Workbook navigation habits

### 1.5 Workspace Customization

51. Saving default field formats
52. Default number formats
53. Default color palettes for fields
54. Custom palette installation
55. Setting preferred font families
56. Turning off auto-updates for performance
57. Pane-only updates
58. Changing calc editor font size
59. Custom keyboard shortcuts
60. Custom view bookmarks
61. Compatible and incompatible features by version
62. Managing saved data sources
63. Saving custom start pages
64. Window layout persistence
65. Toolbar customization
66. Installing extensions
67. Setting up debugging modes
68. Using Performance Recorder from interface
69. Exporting performance recordings
70. Using the Data Source tab efficiently

### 1.6 Conceptual Thinking

71. Tableau’s order of operations
72. Pill behaviors and what they imply
73. Data modeling mental framework
74. Visual encoding fundamentals
75. Thinking in marks rather than rows
76. Grain identification
77. Why Tableau hates ambiguity
78. How Tableau decides aggregation
79. Mental model for “fields vs views”
80. Tableau as a semantic translator

# CHAPTER 2

# Data Connections & Modeling

## (Topics 81–160)

### 2.1 Connecting to Files

81. Excel engine limitations
82. Long text truncation issues
83. Data interpreter behaviors
84. Header detection logic
85. Leading/trailing spaces in Excel
86. Unioning sheets automatically
87. Handling named ranges
88. Refreshing Excel data
89. Multi-sheet schema mismatches
90. CSV delimiter detection
91. Encoding problems in CSV
92. Working with TSV
93. Fixed-width file handling
94. PDF import pitfalls
95. Extract caching for local files
96. Local file refresh patterns

### 2.2 Connecting to Databases

97. Server-side authentication models
98. Initial SQL usage
99. Session parameter management
100. Temp table creation in some connections
101. Live connection query pushing
102. Materialized views in databases
103. Query folding concepts
104. Extract vs live in relational DBs
105. Schema discovery
106. Case sensitivity issues
107. Stored procedure restrictions
108. Custom SQL performance implications
109. Parameterized Custom SQL
110. Multiple connection handling
111. Connection pooling behavior
112. Publishing with embedded credentials
113. OAuth token refresh issues
114. Service accounts in Tableau
115. Cross-database join performance
116. SSL connections

### 2.3 Cloud Integrations

117. Google Analytics sampling issues
118. Salesforce API limits
119. OData constraints
120. BigQuery billing considerations
121. Snowflake warehouse impact
122. Pre-authentication required for cloud sources
123. Token expiry patterns
124. Tableau Bridge architecture
125. Bridge pooling
126. Bridge scheduling strategies
127. Bridge live query tunneling
128. Cloud connectors and unsupported data types
129. Extracting from rate-limited APIs
130. Pagination in WDCs

### 2.4 Data Roles

131. Why blue pills filter rows
132. Why green pills affect axes
133. Continuous-time data behavior
134. Discrete date truncation
135. Custom date hierarchies
136. Geographic role overrides
137. Non-standard geographic fields
138. Mapping FIPS codes
139. Null geographic roles
140. Role propagation after joins

### 2.5 Metadata Modeling

141. Splitting fields intelligently
142. Automatic vs custom split usage
143. Pivoting for wide tables
144. De-pivoting multi-header Excel sheets
145. Data reshaping for time series
146. Field renaming conventions
147. Metadata grid for column cleanup
148. Aliasing fields
149. Default aggregation patterns
150. Dataset profiling inside Tableau
151. Validating row counts
152. Checking field uniqueness
153. Comparing schema drift
154. Rebuilding broken data pane links
155. Detecting over-nested dimensions
156. When to hide unused fields
157. Using describe feature
158. Detecting rolled-up data
159. Replacing data source functionality
160. Data source audit checklist

# CHAPTER 3

# Physical Layer + Logical Layer Modeling

## (Topics 161–240)

### 3.1 Tableau Relationships

161. Logical table architecture
162. Relationship vs join difference
163. Performance benefits of relationships
164. Relationship-generated queries
165. Cardinality settings
166. Referencing integrity meaning
167. Selecting correct matching fields
168. Multiple relationships between tables
169. Ambiguous relationship handling
170. Relationship-driven LOD behavior
171. Why relationships reduce duplication
172. Why relationships sometimes underperform
173. Relationship warnings
174. Identity fields in relationships
175. Granularity drift in relationships
176. Relationship with extracts
177. Relationship-driven aggregation mismatches
178. Understanding many-to-many performance
179. Multi-fact modeling
180. Conformed vs non-conformed dimensions

### 3.2 Physical Joins

181. Join culling
182. Join order rules
183. Join precedence
184. Join condition testing
185. Preventing Cartesian joins
186. Join duplicates detection
187. Null behavior in joins
188. Join type selection logic
189. Complex join calculations
190. Cross-database join pushdown
191. Extract-only joins
192. Multi-join conflict resolution
193. Join densification
194. Anti-patterns for joins
195. Surrogate key creation
196. Data blending vs joining

### 3.3 Unions

197. Wide-table unions
198. Schema alignment
199. Adding dummy fields for unions
200. Wildcard union patterns
201. Multi-folder file unions
202. Dealing with missing fields in unions
203. Field typing conflicts
204. Union performance vs join performance
205. Using unions for incremental loading
206. Using unions for row-level slowly changing dimensions
207. Vertical vs horizontal partitioning
208. File system organizational structure

### 3.4 Grain & Aggregation

209. Identifying dataset grain
210. Mixed-grain dataset issues
211. Aggregation rules inside Tableau
212. Why Tableau auto-aggregates
213. SUM vs ATTR mechanics
214. ATTR as a safety check
215. Row-level calcs with mixed grains
216. Aggregated calcs with mixed grains
217. Grain conflicts after relationships
218. Fixing grain mismatches with FIXED LODs
219. Using densification for missing dates
220. Data scaffolding construction
221. Calendar table integration
222. Time series grain alignment
223. Period-over-period benchmark grain issues
224. Multi-grain fact tables
225. Null grain detection
226. Surrogate grain assignment
227. Row uniqueness testing
228. Stacked fact schemas
229. Fact table normalization
230. Combining fact tables with relationships
231. Preaggregation strategies
232. Atomic-level storage
233. Pre-joined marts
234. De-duplicating via FIXED checks
235. Confirming grain stability
236. Transactional vs snapshot fact patterns
237. Multi-snapshot modeling
238. Aggregated extract generation
239. Data blending when grain mismatch persists
240. When to abandon a data source entirely

# CHAPTER 4

# Calculation Theory

## (Topics 241–330)

### 4.1 Calculation Syntax & Logic

241. Syntax parsing rules
242. Calc editor hints
243. Auto-complete limitations
244. Error resolution strategies
245. Evaluating calc performance
246. Commenting conventions
247. Container functions
248. Multi-line formatting
249. Boolean logic as filtering
250. Nested logical expressions
251. Safe division patterns
252. Handling non-numeric results
253. Integer division pitfalls
254. Division by zero prevention
255. Null handling patterns
256. Using ZN properly
257. Using IIF vs IF
258. Using CASE appropriately
259. CASE type constraints
260. Multi-condition chaining

### 4.2 String Calculations

261. Trimming whitespace
262. Comparing string lengths
263. Complex string slicing
264. Regex extraction
265. Regex replacement
266. Regex match process
267. Splitting composite keys
268. Building composite keys
269. Normalizing text fields
270. Cleaning bad identifiers
271. Domain checking in strings
272. Detecting inconsistent casing
273. Removing special characters
274. Hashing text patterns
275. Fuzzy-matching concepts

### 4.3 Numerical Calculations

276. Rounding patterns
277. Absolute values
278. Logarithms in Tableau
279. Power functions
280. Ranking tie-breaking techniques
281. Percent-of-total behavior
282. Weighted averages
283. Z-scores
284. Normalization patterns
285. Scaling values
286. Bucketing methods
287. Binning edge cases
288. Manual bin calculations
289. Threshold logic

### 4.4 Date Calculations

290. Anchored date calculations
291. Fiscal calendar modeling
292. Custom fiscal year starts
293. Intelligent date shifting
294. Working-day logic
295. Holiday-aware date calcs
296. Period comparison templates
297. Rolling windows
298. Rolling weeks
299. Rolling months
300. Rolling quarters
301. Date granularity truncation
302. Time difference in hours
303. Time difference in seconds
304. Timezone conversion
305. Current date macros
306. Parametrized date windows
307. ISO week conversions
308. Semi-monthly logic
309. Last-day-of-month logic

### 4.5 Table Calculations

310. Table calc shelf editing
311. Partition and addressing
312. Restart clauses
313. Directional scanning logic
314. LOOKUP-based offsets
315. Multi-level addressing
316. Window-based smoothing
317. Confidence interval via table calcs
318. Multi-row transformations
319. Running aggregates
320. Difference-from calculations
321. Percent difference
322. Ranking transformations
323. Nested table calculations
324. Irregular partitions
325. Table calc debugging
326. Table calc caching
327. Pane vs table vs cell scope
328. Mark-level table calc behaviors
329. Table calc performance drains
330. Table calc conflicts with filters

# CHAPTER 5

# Level of Detail Expressions

## (Topics 331–400)

### 5.1 LOD Foundations

331. LOD purpose
332. FIXED mechanics
333. INCLUDE mechanics
334. EXCLUDE mechanics
335. LOD calculation timing
336. How LODs bypass row-level grain
337. LOD and blending
338. LOD and table calculations
339. LOD and filters
340. LOD within relationships

### 5.2 FIXED LOD Patterns

341. FIXED for distinct counts
342. FIXED for KPI computation
343. FIXED for normalization
344. FIXED for allocation ratios
345. FIXED for segmentation
346. FIXED for baseline snapshots
347. FIXED for multi-fact models
348. FIXED with conditional statements
349. FIXED on high-cardinality fields
350. FIXED for row deduplication

### 5.3 INCLUDE LOD Patterns

351. INCLUDE for granular scoring
352. INCLUDE for cross-row comparisons
353. INCLUDE for distribution analysis
354. INCLUDE with dimensions vs measures
355. INCLUDE for user-level metrics
356. INCLUDE for stacking calculations
357. INCLUDE vs nested table calcs

### 5.4 EXCLUDE LOD Patterns

358. Removing grain for aggregated KPIs
359. EXCLUDE for smoothing
360. EXCLUDE vs window average
361. Hierarchical EXCLUDE usage
362. EXCLUDE during drilldowns
363. Avoiding over-aggregation from EXCLUDE

### 5.5 Nested LOD Constructions

364. Stacking FIXED inside INCLUDE
365. Stacking EXCLUDE inside FIXED
366. Multilevel FIXED for multi-segment analytics
367. LOD nesting performance
368. Debugging nested LODs
369. Materializing nested calcs via extract
370. LOD as surrogate measures
371. Multi-fact consolidation with nested FIXED
372. Conditional LODs based on parameters
373. LODs for user-scoped analytics
374. LODs feeding table calculations
375. Using LODs to flatten messy schemas
376. Detecting flawed LOD assumptions
377. Choosing LOD vs join preaggregation
378. Avoiding circular LOD logic
379. Precomputing LODs outside Tableau
380. Documenting LODs in projects
381. Validating LOD correctness
382. LOD regression testing
383. LOD collision with context filters
384. LOD performance triage
385. When to use aggregated extracts instead of LOD
386. Building reusable LOD templates
387. Using parameterized LOD switching
388. Building LOD decision frameworks
389. Preventing accidental grain shifts
390. LOD-driven forecasting prep
391. LOD-based cohort analysis
392. LOD for ratio stability
393. LODs in multi-year historical reporting
394. Industry-specific LOD usage
395. Regional vs national FIXED hierarchies
396. FIXED for sales forecasts
397. INCLUDE for churn scoring
398. EXCLUDE for supply chain smoothing
399. LOD documentation standards
400. LOD anti-pattern detection

# CHAPTER 6

# Charts, Visual Encodings & Graphical Literacy

## (Topics 401–520)

### 6.1 Standard Chart Fundamentals

401. Bar chart encoding
402. Line chart smoothing
403. Combo charts
404. Area charts distortions
405. Histogram bin density
406. Tree map pitfalls
407. Scatter plot jittering
408. Highlight tables
409. Density plots
410. Cumulative distribution visuals

### 6.2 Advanced Charting

411. Nested bar charts
412. Clustered bar charts
413. Slope charts
414. Dumbbell charts
415. Spine charts
416. Marimekko charts
417. Horizon graphs
418. Sankey charts via densification
419. Chord diagrams
420. Radial bar charts
421. Radial histograms
422. Heatmap construction
423. Waffle charts advanced
424. Waterfall charts balancing logic
425. Bullet chart benchmarks
426. KPI tiles
427. Sparkline patterns
428. Trellis charts
429. Small multiples theory
430. Progressive disclosure charts

### 6.3 Geo-Spatial Visualization

431. Symbol map improvements
432. Filled map smoothing
433. Dual-map overlays
434. Multi-layer geospatial stack
435. Spatial join construction
436. Distance heatmaps
437. Contour mapping
438. Directional arrows
439. Path maps
440. Origin-destination flows
441. Route visualizations
442. Territory partition visualization
443. Custom geocoding overrides
444. Multi-country boundary merging
445. Climate-band mapping
446. Grid-based spatial layouts
447. Using high-resolution shapefiles
448. Geospatial extract optimization
449. Complex polygon behavior
450. Avoiding multi-GB spatial files

### 6.4 Visual Design Theory

451. Color theory for analytics
452. Contrast ratios
453. Sequential palettes
454. Diverging palettes
455. Categorical palette clustering
456. Accessibility color rules
457. Misleading color gradients
458. Typography legibility
459. Spatial grouping by layout
460. Pre-attentive attributes
461. Visual hierarchy creation
462. Grouping through alignment
463. Visual rhythm
464. Reducing chartjunk
465. Understanding ink-to-data ratio
466. Reducing perceptual overload
467. Storytelling placement
468. Annotation strategy
469. White space as structure

### 6.5 Marks & Encoding Deep Cuts

470. Mark types
471. Mark stacking
472. Mark layering
473. Mark density effects
474. Tooltip mark enhancements
475. Encoding via shape
476. Encoding via size
477. Encoding via opacity
478. Encoding via angle
479. Encoding via motion (pages)
480. Encoding via position

### 6.6 Chart Anti-Patterns

481. Pie charts with too many slices
482. Overuse of 3D visuals
483. Unsorted bar charts
484. Poorly chosen baselines
485. Misaligned axes
486. Overlapping marks
487. Ambiguous color meaning
488. Too many filters
489. Uncontrolled user interactivity
490. Excessive chart density
491. Too many KPIs on one canvas
492. Data distortion via smoothing
493. Fake precision in charts
494. Visual noise from shadows
495. Unlabeled axes
496. Floating legends causing confusion
497. Tooltip overload
498. Misleading dual-axis scaling
499. Poorly chosen geographic levels
500. Overuse of table calcs in visuals
501. Overuse of tiny multiples
502. Over-aggregated metrics hiding insights
503. Bad KPI formatting
504. Inconsistent color theming
505. Layout disorganization
506. misleading title framing
507. Legend redundancy
508. Chart clutter from lines + shapes + labels
509. Excessive dashboard text
510. Non-responsive design mistakes
511. Unbalanced whitespace
512. Unnecessary action triggers
513. User confusion from too many overlays
514. Using visual metaphor incorrectly
515. Using color without data meaning
516. Overuse of icons
517. Unclear storytelling
518. Random sort orders
519. Default formatting left untouched
520. Gratuitous animation usage

# CHAPTER 7

# Dashboards, Interactions & UX

## (Topics 521–610)

### 7.1 Dashboard Construction

521. Tiled vs floating design philosophies
522. Nested container mechanics
523. Designing layout grids
524. Visual spacing frameworks
525. Using templates for consistency
526. Multi-dashboard navigation
527. Building mockups before dashboards
528. Reducing scroll dependencies
529. Device-specific dashboards
530. Dashboard scaling strategies
531. Optimizing for projector viewing
532. Optimizing for mobile
533. Layering sheets for blending effects
534. Tooltip configurability
535. Consistent header design
536. Interactive legends
537. Using dashboards as menus
538. Navigation buttons
539. Hidden navigation areas
540. Story point sequencing

### 7.2 Interactivity Patterns

541. Filter actions
542. Highlight actions
543. URL actions
544. Parameter actions
545. Set actions
546. Drill-down actions
547. Drill-up actions
548. Dynamic sheet swapping
549. Dynamic field selection
550. Dynamic metric switching
551. Parameter-driven chart type switching
552. Controlling user paths
553. Custom UI controls using parameters
554. Hidden filter panels
555. Multi-level drill hierarchies
556. Breadcrumb trails
557. Hover-based interactions
558. Hover-only detail reveal
559. Tooltip-based filters
560. Select-to-highlight interactions
561. Cascading filters
562. Avoiding filter conflicts
563. Performance-sensitive filters
564. Filter domain management
565. Using sets as interactive groups
566. Context filters for heavy datasets
567. Exclude filters vs hide filters
568. Multi-dashboard interactions
569. Global filters across dashboards
570. Custom query actions

### 7.3 UX Patterns

571. Designing for executives
572. Designing for analysts
573. Designing for field teams
574. Designing for finance
575. Designing for supply chain
576. Designing for sales
577. Designing for healthcare
578. Designing for ecommerce
579. Reducing cognitive load
580. Reducing user choice paralysis
581. Designing intuitive flows
582. Building dashboards like “apps”
583. Designing onboarding guides
584. Anticipating user confusion
585. Hiding unnecessary controls
586. Making dashboards self-explanatory
587. Designing for color-blind users
588. Using tooltips as documentation
589. Creating narrative dashboards
590. Using micro-charts
591. Embedded glossary panels
592. Error-state visual design
593. Consistent KPI representation
594. Standardized dashboards for teams
595. Using whitespace to structure thought
596. Designing dashboards for speed
597. Designing dashboards for clarity
598. Designing dashboards for exploration
599. When to remove interactivity
600. When to increase interactivity

### 7.4 Storytelling

601. Structuring a data story
602. Identifying narrative arcs
603. Choosing entry points
604. Designing intentional reveals
605. Using annotations minimally
606. Building narrative builds
607. Building paced disclosures
608. Maintaining user focus
609. Ending dashboards with conclusions
610. Creating dashboard “voice”

# CHAPTER 8

# Tableau Prep & Data Cleaning

## (Topics 611–670)

### 8.1 Prep Builder Foundations

611. Flow structure
612. Input cleansing
613. Pivot steps
614. Aggregate steps
615. Join steps
616. Union steps
617. Cleaning step profiling
618. Field splitting in Prep
619. Multi-level pivoting
620. Flow outputs
621. Publishing Prep flows
622. Flow scheduling
623. Flow documentation
624. Flow performance optimization
625. Flow error diagnosis

### 8.2 Data Shaping

626. Resolving multi-header data
627. Resolving nested structured data
628. Cleaning JSON fields
629. Normalizing text
630. Removing duplicates
631. Splitting hierarchical strings
632. Deduplication strategies
633. Time-series restructuring
634. Rolling snapshots
635. Unpivoting large files
636. Flattening crosstabs
637. Repairing mismatched schemas

### 8.3 Prep Logic

638. Conditional logic inside Prep
639. Multi-branch flows
640. Reusable flow components
641. Parameterizing flows
642. Environment-specific outputs
643. Error handling sections
644. Edge-case validation
645. Automated outlier removal
646. Prep for forecasting
647. Prep for LOD simplification
648. Prep for custom granularity
649. Prep for clustering inputs
650. Prep for spatial files

### 8.4 Prep Conductor

651. Flow scheduling on server
652. Execution logs
653. Flow monitoring
654. Handling failed flows
655. Governance rules for flows
656. Resource allocation
657. Execution queue logic
658. Bridge + Prep combined architecture
659. Optimizing server load
660. Centralized vs distributed flow management

### 8.5 Extract Strategy

661. Extract refresh patterns
662. Extract partitioning
663. Incremental extract keys
664. Extract schema drift handling
665. Extract row-limits and behaviors
666. Extract compression behavior
667. Extract failures debugging
668. Hyper fragment cleanup
669. Designing extract pipelines
670. Building extract governance documents

# CHAPTER 9

# Performance Engineering

## (Topics 671–705)

### 9.1 Performance Recorder

671. Query timeline interpretation
672. Rendering time detection
673. Data source bottleneck analysis
674. Extract bottleneck analysis
675. Slow workbook diagnosis
676. Evidence-based optimization
677. Saving and comparing recordings
678. Detecting problematic calcs
679. Detecting expensive joins
680. Detecting expensive filters

### 9.2 Query Optimization

681. Reducing custom SQL usage
682. Parameter substitution efficiency
683. Avoiding nested LODs
684. Avoiding heavy table calcs
685. Choosing extract vs live strategically
686. Pre-aggregating data at source
687. Using database views
688. Using materialized views
689. Handling massive fact tables
690. Caching behaviors
691. Multi-query dashboards
692. Parallel query execution limits
693. Delaying non-critical sheets
694. Reducing mark count
695. Reducing tooltip load
696. Rendering dense geospatial files
697. Memory pressure handling
698. Avoiding massive calculated joins
699. Fixing runaway queries
700. Workbook load-order design
701. Using filters that push down to SQL
702. Avoiding high-cardinality quick filters
703. Extracting only needed columns
704. Designing performance budgets
705. Creating performance SLAs

# CHAPTER 10

# Server, Cloud & Administration

## (Topics 706–740)

### 10.1 Publishing

706. Publishing workbook best practices
707. Publishing data sources best practices
708. Differences between ‘replace’ and ‘overwrite’
709. Version management
710. Publishing strategy for large orgs
711. Folder structures
712. Project-level permissions
713. Workbook ownership logic
714. Migration between sites
715. Promoting dashboards across environments

### 10.2 Server Administration

716. Site roles
717. Permissions matrix
718. Content governance
719. Ownership transfer
720. Certified data sources workflow
721. Tableau Catalog usage
722. Data lineage mapping
723. Impact analysis
724. Server health monitoring
725. Backgrounder load balancing
726. Extract refresh scheduling
727. Refresh failures triage
728. Managing concurrency limits
729. Group-based access control
730. Alerting configuration
731. Subscriptions automation
732. Server event logs
733. Admin views
734. Resource monitoring tool usage
735. Failure prevention through design
736. Troubleshooting slow dashboards
737. Securing sensitive data
738. Managing external assets
739. Decommissioning workbooks
740. Audit and compliance requirements

# CHAPTER 11

# Automation, APIs & Extensions

## (Topics 741–745)

741. Tableau JavaScript API fundamentals
742. Automating user interactions via JS
743. Extract API usage
744. Metadata API usage
745. Embedding dashboards in web apps

# CHAPTER 12

# Domain Patterns, Testing & Governance

## (Topics 746–750)

746. Finance dashboard design patterns
747. Healthcare analytics designs
748. E-commerce funnel dashboards
749. Data quality testing frameworks
750. Dashboard governance models
