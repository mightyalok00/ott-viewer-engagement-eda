# OTT Viewer Engagement EDA — Hotstar Business Scenario

## Overview
This project performs exploratory data analysis on **33,171 synthetic OTT episode-level records** to understand viewer engagement, watch completion, drop-off, and retention risk. Hotstar is used only as the business scenario; the dataset is not proprietary Hotstar data.

## Local Project Copy Path
`D:\project\_2\_Ott\_Viewer\_Engagement\_Analysis`

Keep all notebooks and the CSV together in that directory.

## Tools
- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn

No machine learning, Scikit-learn, Plotly, Power BI, Tableau, or external statistical libraries are used.

## Data Quality
- 33,171 rows
- 23 source columns
- 0 missing values
- 0 exact duplicate rows
- Binary/range/type checks included
- `release_year` validated before integer conversion in the cleaning workflow

## Key Findings
- **Comedy** has the highest average engagement score: **77.38**.
- **Drama** has the highest drop-off rate: **24.19%**.
- **14.48%** of records are classified as High retention risk.
- Hook strength vs watch percentage: **r ≈ 0.552**.
- Pacing vs engagement: **r ≈ 0.566**.
- Cognitive load vs drop-off probability: **r ≈ 0.793**.
- Watch percentage vs drop-off probability: **r ≈ -0.957**.
- Episode duration vs watch percentage is essentially zero (**r ≈ -0.0004**), so runtime alone is not a useful optimization signal here.

## Notebook Structure
1. `01_Business_Problem.ipynb`
2. `02_Import_Libraries.ipynb`
3. `03_Load_Dataset.ipynb`
4. `04_Data_Understanding.ipynb`
5. `05_Data_Cleaning.ipynb`
6. `06_Univariate_Analysis.ipynb`
7. `07_Bivariate_Analysis.ipynb`
8. `08_Engagement_Analysis.ipynb`
9. `09_Drop_Off_Analysis.ipynb`
10. `10_Retention_Analysis.ipynb`
11. `11_Season_and_Episode_Analysis.ipynb`
12. `12_Correlation_Analysis.ipynb`
13. `13_Top_Bottom_Content.ipynb`
14. `14_Business_Insights.ipynb`

## Business Recommendations
- Promote content only when high engagement is supported by high watch completion and low drop-off probability.
- Investigate episodes combining low completion with high drop-off probability.
- Review hook strength and pacing when engagement is weak.
- Pay special attention to high cognitive load in High-risk episodes.
- Treat pause behavior as a secondary diagnostic signal.
- Do not assume shorter episodes will improve completion; this dataset does not support that conclusion.

## Limitations
This is synthetic educational data. Correlation is not causation, the engagement score is project-defined, and the findings should not be represented as actual Hotstar customer behavior.

## Portfolio Value
The project demonstrates data loading, validation, cleaning, univariate and bivariate EDA, feature construction, grouping/aggregation, correlation analysis, visualization, ranking, business interpretation, and recommendation writing using the tools permitted by the brief.

---

## Expert Data-Science Revision

This version strengthens analytical rigor while remaining strictly within the assignment constraints.

### Added
- Professional data-quality summary
- Memory-usage inspection
- Show-ID and episode-key validation
- Reusable numeric range validation
- Mean + median + standard deviation + sample-size reporting
- Engagement index interpretation
- Optional normalized 0–100 engagement score
- Genre summaries with observation counts
- Show-level scorecards with minimum-sample filtering
- Episode progression analysis
- High-risk vs other-episode comparison
- Correlation strength labels with non-causal interpretation
- Business content segmentation
- Explicit promotion and investigation rules
- Reliability-aware show rankings

### Strict Tool Constraint

Used only:
- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn

Not used:
- Scikit-learn
- Plotly
- Power BI
- Tableau
- Machine Learning
- Statistical libraries beyond NumPy/Pandas

### Local Windows Project Path

`D:\project\_2\_Ott\_Viewer\_Engagement\_Analysis`


### Naming Standards Added

The revised notebooks now include reusable functions for clean DataFrame naming:

- `clean_column_name()` — converts labels to snake_case
- `standardize_column_names()` — cleans all column names
- `rename_columns_with_mapping()` — supports controlled business-friendly renaming
- `set_row_index_name()` — gives the index a descriptive name such as `row_id`
- `reset_row_numbers()` — safely renumbers rows after filtering or cleaning

The project deliberately keeps field names such as `avg_watch_percentage` and `drop_off_probability` because they already follow good Python naming conventions and match the supplied project brief.


### Final Expert Audit — v3

Additional methodological corrections:

- Show-level grouping now uses `show_id + title`, preventing distinct shows with the same title from being merged.
- The dataset contains two titles (`Doctor Who` and `Doraemon`) that map to multiple show IDs.
- Repeated `show_id + season_number + episode_number` combinations are described as repeated episode observations, not automatically deleted duplicates.
- Variable roles are separated into identifiers, binary indicators, categorical variables, ordinal/discrete numeric variables, and continuous numeric variables.
- Hook/pacing/visual-intensity relationships are primarily evaluated against observed `avg_watch_percentage` to avoid circular conclusions from correlating components with a composite engagement index that already contains them.


### Kernel-Safe v4

This version is optimized for Jupyter stability. Saved notebook outputs were cleared, scatterplots are capped at 5,000 points, large previews are limited, Matplotlib figures are closed after display, garbage collection is used after heavy sections, and unnecessary deep copies are avoided.

Recommended local workflow: open one notebook at a time, use **Kernel > Restart Kernel and Run All Cells**, then close that notebook before running the next chart-heavy notebook.
