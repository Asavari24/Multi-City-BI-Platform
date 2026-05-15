# Multi-City-BI-Platform
Multi-City Business Licensing BI Platform
A dimensional data model unifying business-license open data from New York City, Chicago, and Washington DC into a single analytics-ready target, designed to answer 10+ business questions on licensing activity, industry distribution, geographic concentration, and renewal trends.
Built as the individual project for DAMG 7370 — Designing Advanced Data Architectures for Business Intelligence at Northeastern University.

Problem
Each city's open data portal publishes business-licensing data on its own schema. A regulator, urban analyst, or franchise strategist who wants a cross-city view has to first reconcile three different column sets, naming conventions, and data-quality issues before any meaningful analysis can begin.
This project standardizes those three heterogeneous sources into one star schema, profiles every column for quality issues, and traces source-to-target lineage so the model is auditable and extensible.

Tech stack

Databricks — profiling notebooks and data exploration
DQX — column-level data quality checks and validation rules
ER Studio — dimensional modeling and entity-relationship diagrams
TSV — raw source format from open data portals


Approach

Profile — Loaded each city's raw TSV into Databricks and ran DQX checks to inventory datatypes, widths, null patterns, and column-level quality issues across all three sources.
Map — For every business question, identified which source columns from each city feed it, and documented the transformation logic needed to harmonize them into a unified target column.
Model — Designed a star schema in ER Studio with facts and dimensions chosen specifically to support all 10+ business questions, ensuring consistent business logic across cities.


Business questions supported

Active vs inactive license distribution — segregated by city and aggregated across all cities
Predominant industries receiving business licenses
Top 5 geographic areas (by zip code and by street name) within each city by license volume
License-issuance trend over time
License-abandonment trends
Seasonal variations in issuance
Business counts by urgency category (immediate, high, medium, low)
Inactive businesses with contact details for renewal outreach
Top 10 organizations by franchise ownership, per city
Distribution of businesses by duration (years) since license issuance


Repository structure
.
├── notebooks/
│   └── profiling_dqx.ipynb         # Databricks DQX profiling notebook
├── docs/
│   ├── data_issues_inference.pdf   # Column-level quality findings
│   ├── source_to_target_mapping.xlsx  # Three-source → target lineage
│   └── data_dictionary.md          # Datatypes and widths per column
├── model/
│   └── star_schema_erd.png         # ER Studio export of the dimensional model
└── README.md

Data sources

New York City Open Data — Business Licenses
City of Chicago Data Portal — Business Licenses
Washington DC Open Data — Basic Business Licenses

Raw TSV exports are not committed due to size; refer to the respective open data portals for the source files.

Author
Asavari Shejwal — M.S. Software Engineering Systems, Northeastern University
