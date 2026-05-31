# Multi-City Business Licensing BI Platform
Multi-City Business Licensing BI Platform
A dimensional data model that unifies business-license open data from New York City, Chicago, and Washington, D.C. into a single, analytics-ready star schema — purpose-built to answer 10+ real business questions on licensing activity, industry distribution, geographic concentration, and renewal trends.

Highlights

Standardizes 3 heterogeneous open-data sources — each with its own schema, naming conventions, and quality issues — into one unified star schema
Column-level data-quality profiling with DQX across all sources before any modeling
Full source-to-target lineage documented, making the model auditable and extensible to new cities
Dimensional model designed to answer 10+ business questions for regulators, urban analysts, and franchise strategists.

The Problem
Each city's open-data portal publishes business-licensing data on its own schema. Anyone who wants a cross-city view — a regulator, an urban analyst, a franchise strategist — first has to reconcile three different column sets, naming conventions, and data-quality issues before any meaningful analysis can begin.
This project removes that barrier: it standardizes the three sources into one star schema, profiles every column for quality issues, and traces source-to-target lineage so the model is auditable and easy to extend.

Tech Stack
Tool                        Role  
Databricks                Profiling notebooks and data exploration
DQX                       Column-level data-quality checks and validation rules
Navicat                   Dimensional modeling and entity-relationship diagrams
TSV                       Raw source format from the open-data portals

Approach
1. Profile — Loaded each city's raw TSV into Databricks and ran DQX checks to inventory datatypes, field widths, null patterns, and column-level quality issues across all three sources.
2. Map — For every business question, identified which source columns from each city feed it, then documented the transformation logic needed to harmonize them into a single unified target column.
3. Model — Designed a star schema in ER/Studio with facts and dimensions chosen specifically to support all 10+ business questions, ensuring consistent business logic across cities.


Business Questions Answered

1. Active vs. inactive license distribution — by city and aggregated across all cities
2. Predominant industries receiving business licenses
3. Top 5 geographic areas (by ZIP code and by street name) per city, by license volume
4. License-issuance trends over time
5. License-abandonment trends
6. Seasonal variation in issuance
7. Business counts by urgency category (immediate, high, medium, low)
8. Inactive businesses with contact details for renewal outreach
9. Top 10 organizations by franchise ownership, per city
10. Distribution of businesses by duration (years) since license issuance


Repository Structure
.
├── notebooks/
│   └── profiling_dqx.ipynb             # Databricks DQX profiling notebook
├── docs/
│   ├── data_issues_inference.pdf       # Column-level quality findings
│   ├── source_to_target_mapping.xlsx   # Three-source → target lineage
│   └── data_dictionary.md              # Datatypes and widths per column
├── model/
│   └── star_schema_erd.png             # ER/Studio export of the dimensional model
└── README.md

Data Sources:

New York City — Business Licenses · NYC Open Data
Chicago — Business Licenses · Chicago Data Portal
Washington, D.C. — Basic Business Licenses · Open Data DC

Raw TSV exports are not committed due to size — pull the source files from the portals above.
