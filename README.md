# 📺 OTT Viewer Engagement EDA

### Hotstar Business Scenario | Exploratory Data Analysis with Python

A portfolio-ready exploratory data analysis project examining **viewer engagement, watch completion, drop-off behaviour, and retention risk** across **33,171 synthetic OTT episode-level observations**.

> [!IMPORTANT]
> **Dataset Disclaimer:** This project does **not** use proprietary Hotstar data. The viewer-behaviour dataset is synthetic and intended for educational analysis. **Hotstar is used only as the business scenario.**

---

## 🎯 Project Objective

Imagine working as a **Data Analyst for Hotstar**. The content team wants to understand why viewers lose interest, which content characteristics are associated with stronger engagement, and which episodes deserve promotion or further investigation.

This project answers business questions such as:

- Which genres achieve the strongest engagement?
- Which genres show the highest observed drop-off?
- How are **hook strength** and **pacing** associated with watch completion?
- How does **cognitive load** relate to drop-off probability?
- Do episode duration, pauses, rewinds, and intro skipping reveal useful behavioural patterns?
- Which episodes and shows are strong candidates for promotion?
- Which content should be investigated for low completion or high retention risk?

---

## 📌 Executive Summary

| KPI / Finding | Result |
|---|---:|
| Dataset size | **33,171 records** |
| Source columns | **23** |
| Missing values | **0** |
| Exact duplicate rows | **0** |
| Average watch percentage | **56.81%** |
| Average episode duration | **37.66 min** |
| Highest average engagement genre | **Comedy — 77.38** |
| Highest observed drop-off genre | **Drama — 24.19%** |
| High retention-risk records | **14.48%** |
| Hook strength ↔ Watch % | **r ≈ 0.552** |
| Cognitive load ↔ Drop-off probability | **r ≈ 0.793** |
| Watch % ↔ Drop-off probability | **r ≈ -0.957** |
| Episode duration ↔ Watch % | **r ≈ -0.0004** |

**Main takeaway:** viewer completion, opening strength, pacing, cognitive load, and drop-off probability provide more useful signals in this synthetic dataset than episode duration alone.

---

## 🧰 Tech Stack

![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-Analysis-013243?logo=numpy&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557C)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-4C72B0)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)

### Assignment constraints

The analysis intentionally does **not** use:

`Scikit-learn` · `Plotly` · `Power BI` · `Tableau` · `Machine Learning` · `SciPy` · `Statsmodels`

The analytical workflow stays within **Python, NumPy, Pandas, Matplotlib, and Seaborn**.

---

## 🗂️ Repository Structure

```text
ott-viewer-engagement-eda/
│
├── 01_Business_Problem.ipynb
├── 02_Import_Libraries.ipynb
├── 03_Load_Dataset.ipynb
├── 04_Data_Understanding.ipynb
├── 05_Data_Cleaning.ipynb
├── 06_Univariate_Analysis.ipynb
├── 07_Bivariate_Analysis.ipynb
├── 08_Engagement_Analysis.ipynb
├── 09_Drop_Off_Analysis.ipynb
├── 10_Retention_Analysis.ipynb
├── 11_Season_and_Episode_Analysis.ipynb
├── 12_Correlation_Analysis.ipynb
├── 13_Top_Bottom_Content.ipynb
├── 14_Business_Insights.ipynb
│
├── OTT_Viewer_Engagement_Analysis_Report_Alok_Agarwal.pdf
├── ott_viewer_dropoff_retention_us_v1.0.csv
├── requirements.txt
├── .gitignore
└── README.md
```

### ⭐ Where to Start

Start with [01_Business_Problem.ipynb](01_Business_Problem.ipynb) and follow the 14 numbered notebooks in order to explore the workflow. Each stage is provided as a separate notebook.

For a report overview, open the [analysis report (PDF)](OTT_Viewer_Engagement_Analysis_Report_Alok_Agarwal.pdf).

---

## 🔍 Analysis Workflow

| # | Stage | Purpose |
|---:|---|---|
| 01 | Business Problem | Define the analytical and business objectives |
| 02 | Import Libraries | Configure the permitted Python stack |
| 03 | Load Dataset | Import and validate the source dataset |
| 04 | Data Understanding | Examine structure, types, distributions, and quality |
| 05 | Data Cleaning | Standardize and validate the analytical dataset |
| 06 | Univariate Analysis | Explore individual variables |
| 07 | Bivariate Analysis | Examine relationships between variables |
| 08 | Engagement Analysis | Analyze watch behaviour and engagement |
| 09 | Drop-Off Analysis | Identify drop-off patterns and risk signals |
| 10 | Retention Analysis | Investigate retention-risk behaviour |
| 11 | Season & Episode Analysis | Compare episode-level performance |
| 12 | Correlation Analysis | Quantify linear associations |
| 13 | Top / Bottom Content | Rank content using reliability-aware rules |
| 14 | Business Insights | Translate findings into recommendations |

---

## 🧹 Data Quality & Cleaning

The workflow includes:

- Column-name standardization to `snake_case`
- Text-field whitespace cleaning
- Numerical and categorical column identification
- Missing-value auditing
- Exact-duplicate auditing
- Numerical-range validation
- Binary-field validation
- Release-year validation
- Season and episode-number checks
- Blank categorical-value checks
- Repeated episode-key investigation

### Duplicate-handling decision

Repeated combinations of:

```text
show_id + season_number + episode_number
```

are treated as **repeated episode-level observations**, not automatically deleted. Records are removed only when they are confirmed to be exact duplicates.

This avoids destroying potentially meaningful observations.

---

## 📊 Engagement Analysis

The project constructs a custom engagement index:

```text
engagement_score =
(
    avg_watch_percentage
    + hook_strength × 5
    + pacing_score × 5
    + visual_intensity × 5
) / 2
```

> The engagement score is a **project-defined analytical index**. It is not a percentage, probability, or official Hotstar metric.

Because hook strength, pacing, and visual intensity are components of this score, relationships between those variables and the engagement index are partly structural. Independent measures such as **average watch percentage** are therefore also used when interpreting viewer behaviour.

---

## 🔑 Key Findings

### 1. Comedy leads average engagement

**Comedy** records the highest average engagement score at approximately **77.38**.

This makes it a strong category for further content-level investigation, but genre averages alone should not determine promotion decisions.

### 2. Drama has the highest observed drop-off

**Drama** shows the highest observed drop-off rate at approximately **24.19%**.

The result suggests that Drama episodes with weak completion deserve closer investigation.

### 3. High retention risk affects a meaningful share of observations

Approximately **14.48%** of episode-level records are classified as **High retention risk**.

These records provide a useful segment for targeted diagnostic analysis.

### 4. Stronger hooks correspond with better completion

Hook strength and average watch percentage show a moderate positive association:

```text
r ≈ 0.552
```

Opening strength is therefore a useful content diagnostic in this dataset.

### 5. Cognitive load is strongly associated with drop-off probability

```text
Cognitive load ↔ Drop-off probability: r ≈ 0.793
```

High cognitive load should receive additional attention when evaluating high-risk episodes.

### 6. Completion and drop-off move strongly in opposite directions

```text
Watch percentage ↔ Drop-off probability: r ≈ -0.957
```

Lower completion is strongly associated with higher drop-off probability in the supplied synthetic data.

### 7. Runtime alone is not a useful optimization signal

```text
Episode duration ↔ Watch percentage: r ≈ -0.0004
```

The dataset does not support the assumption that simply shortening episodes would improve completion.

---

## 🏆 Content Decision Framework

### Promotion candidates

Strong promotion candidates combine:

- **High engagement**
- **High watch completion**
- **Low drop-off probability**

Percentile-based thresholds are used so promotion is not determined by a single metric.

### Investigation candidates

Content deserves closer review when it combines signals such as:

- Low watch completion
- High drop-off probability
- High retention risk
- Weak hook strength
- Weak pacing
- High cognitive load

Show-level rankings also apply a minimum observation requirement to reduce the chance of presenting tiny samples as reliable top performers.

---

## 💡 Business Recommendations

1. **Use multiple signals for promotion decisions.**  
   Combine engagement, completion, and drop-off rather than ranking content using engagement alone.

2. **Prioritize low-completion/high-drop-off episodes for review.**  
   This combination provides one of the clearest content-investigation signals.

3. **Review opening hooks and pacing.**  
   These characteristics are useful diagnostic variables when watch completion is weak.

4. **Monitor cognitively demanding content.**  
   High cognitive load is strongly associated with drop-off probability in this synthetic dataset.

5. **Treat pause and rewind behaviour as secondary indicators.**  
   Use them alongside stronger completion and drop-off measures.

6. **Avoid optimizing episode length without supporting evidence.**  
   Runtime shows essentially no linear relationship with watch percentage here.

---

## 🚀 How to Run the Project

### 1. Clone the repository

Using GitHub CLI:

```bash
gh repo clone mightyalok00/ott-viewer-engagement-eda
cd ott-viewer-engagement-eda
```

Or using Git:

```bash
git clone https://github.com/mightyalok00/ott-viewer-engagement-eda.git
cd ott-viewer-engagement-eda
```

### 2. Create a virtual environment

**Windows (Command Prompt)**

```bat
python -m venv .venv
.venv\Scripts\activate
```

**Windows (PowerShell)**

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

**macOS / Linux**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install -r requirements.txt
```

### 4. Start Jupyter

```bash
jupyter notebook
```

Open `01_Business_Problem.ipynb` and follow the numbered notebooks through `14_Business_Insights.ipynb`. In each notebook, select the Python kernel for your virtual environment and run the cells from top to bottom.

Start Jupyter from the repository root and keep the CSV beside the notebooks. The analysis notebooks load it using a **relative path**, so no personal or machine-specific file path is required when run from this folder.

---

## 📦 Requirements

```text
numpy
pandas
matplotlib
seaborn
jupyter
ipykernel
```

---

## ⚠️ Analytical Limitations

- The dataset is **synthetic**.
- Hotstar is used **only as the business scenario**.
- Results must not be presented as actual Hotstar customer behaviour.
- Correlation does not establish causation.
- The engagement score is project-defined.
- Some engagement relationships are partly structural because several content variables contribute directly to the custom engagement index.
- Findings are best interpreted as **business hypotheses and investigation priorities**, not causal conclusions.
- Season-level comparison is limited where the supplied data does not provide sufficient variation.

---

## 🎓 Skills Demonstrated

`Python` · `Pandas` · `NumPy` · `Data Cleaning` · `Data Validation` · `EDA` · `Matplotlib` · `Seaborn` · `Correlation Analysis` · `Feature Construction` · `Aggregation` · `Content Ranking` · `Business Analysis` · `Data Storytelling`

---

## 👤 Author

### Alok Agarwal

**Data Science · Data Analytics · Digital Marketing**

This project is part of my portfolio demonstrating the ability to turn a business problem into a structured, reproducible, and decision-oriented exploratory data analysis.

---

### ⭐ If you found this project useful, consider starring the repository.
