# Loan Default Risk Analysis Dashboard

### Exploring loan default patterns and borrower risk indicators with Python, Power BI, and DAX

<p align="left">
  <img src="https://img.shields.io/badge/Python-Data%20Preparation-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?style=for-the-badge&logo=powerbi&logoColor=black" alt="Power BI">
  <img src="https://img.shields.io/badge/DAX-Measures%20%26%20KPIs-5A4FCF?style=for-the-badge" alt="DAX">
  <img src="https://img.shields.io/badge/Project-Portfolio%20Analysis-1F6FEB?style=for-the-badge" alt="Project">
</p>

---

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Business Problem](#-business-problem)
- [Project Objectives](#-project-objectives)
- [Dataset Overview](#-dataset-overview)
- [Key Variables](#-key-variables)
- [Data Preparation](#-data-preparation)
- [Dashboard Preview](#-dashboard-preview)
- [Dashboard Features](#-dashboard-features)
- [Key Metrics](#-key-metrics)
- [Dynamic Analysis](#-dynamic-analysis)
- [Credit Score and DTI Risk Analysis](#-credit-score-and-dti-risk-analysis)
- [Initial Observations](#-initial-observations)
- [Analytical Workflow](#-analytical-workflow)
- [Tech Stack](#-tech-stack)
- [Repository Structure](#-repository-structure)
- [Getting Started](#-getting-started)
- [Limitations and Interpretation](#-limitations-and-interpretation)
- [Future Improvements](#-future-improvements)
- [Author](#-author)

---

## 🎯 Project Overview

How can loan portfolio data be turned into a clearer view of default risk?

This project explores loan default patterns across borrower characteristics, financial indicators, and loan attributes. Using **Python for data preparation** and **Power BI for analysis and visualization**, I built an interactive, single-page dashboard that brings key portfolio metrics and risk comparisons together.

The dataset contains **2,000 loan records and 31 variables**, including credit score, debt-to-income ratio (DTI), loan-to-value ratio (LTV), loan amount, interest rate, credit utilization, past delinquencies, employment type, loan type, and other borrower and loan details.

The aim is to make it easier to explore questions such as:

- What proportion of the recorded loans are marked as defaulted?
- How does the default rate vary across loan types and credit score bands?
- How do debt burden and credit quality look when examined together?
- How has the recorded default rate changed across application years?
- Which segments may warrant closer investigation?

> **Project scope:** This is a descriptive risk-analysis and dashboarding project. It explores patterns in the available data; it is not a predictive credit-scoring model and does not establish that a variable causes default.

---

## 💼 Business Problem

Loan portfolios contain borrowers with different financial circumstances and loan characteristics. Reviewing raw rows or isolated metrics makes it difficult to compare these groups consistently.

A useful risk dashboard should bring together:

- **Portfolio overview** — loan volume and recorded defaults
- **Borrower indicators** — credit score, debt burden, and credit utilization
- **Loan characteristics** — loan type, loan amount, and interest rate
- **Time-based analysis** — how the recorded default rate varies by application year
- **Segment comparisons** — where default rates differ across selected categories

This dashboard was designed to provide one interactive place to explore these dimensions and support further investigation.

---

## 🎯 Project Objectives

- Prepare the loan dataset for analysis using Python.
- Preserve meaningful missing values rather than treating every blank as an error.
- Create interpretable bands for selected financial indicators.
- Build key portfolio measures using DAX.
- Compare default rates across borrower and loan segments.
- Explore the relationship between credit score bands and DTI bands.
- Make the report interactive through slicers and a dynamic **Analyse By** selector.
- Present the results in a compact, executive-style Power BI dashboard.

---

## 📊 Dataset Overview

| Dataset detail | Description |
|---|---|
| Loan records | 2,000 |
| Variables | 31 |
| Target field | `Default_Flag` |
| Target meaning | `0` = non-default, `1` = default |
| Data preparation | Python / Pandas |
| Analysis and visualization | Power BI |
| Measures and calculations | DAX |

### Target variable: `Default_Flag`

| Value | Meaning |
|---:|---|
| `0` | Non-default |
| `1` | Default |

The dashboard uses this field to calculate the number of recorded defaults and the default rate.

---

## 🧾 Key Variables

The dataset includes variables from several analytical groups. The exact fields available for a particular analysis depend on the supplied dataset.

| Category | Example variables | Why they matter |
|---|---|---|
| Credit profile | `Credit_Score` | Compares default rates across credit-score ranges |
| Debt burden | `DTI_Ratio_Pct` | Represents debt payments relative to income |
| Collateral | `LTV_Pct`, `Collateral_Type` | Supports analysis of loan amount relative to collateral value, where applicable |
| Credit behaviour | `Credit_Utilization_Pct`, `Past_Delinquencies_24M` | Adds context about credit usage and prior delinquency history |
| Loan attributes | `Loan_Type`, `Loan_Amount`, `Interest_Rate` | Supports comparison across loan products and loan sizes |
| Borrower profile | `Employment_Type`, `Age`, `Gender` | Enables segment-level comparisons |
| Location | `State`, `City_Tier` | Enables geographic category analysis |
| Time | `Application_Date`, `Application_Year` | Supports analysis across application years |
| Outcome | `Default_Flag` | Identifies recorded default status |

---

## 🧹 Data Preparation

Python and Pandas were used to prepare the dataset before importing it into Power BI.

The preparation process included:

- Reviewing data types and column values.
- Checking missing values and their meaning.
- Validating numerical fields used in analysis.
- Creating categorical bands for selected numerical variables.
- Preparing the dataset for Power BI visuals and measures.

### Handling meaningful missing values

One important example is `LTV_Pct`. Loan-to-value is relevant when a loan is secured against collateral. For unsecured loans, an LTV value may not be applicable.

For that reason, these missing values should not automatically be replaced with zero. Keeping them blank avoids suggesting that an unsecured loan has an LTV of 0%.

---

## 🖥️ Dashboard Preview

![Loan Default Risk Analysis Dashboard]([assets/loan_default_risk_dashboard.png](https://github.com/Vanshika26Ramjas/loan_default_risk_analysis/blob/main/dashboard/loan_default_risk_dashboard.png))

*Interactive Power BI report showing portfolio KPIs, default-rate comparisons, the yearly trend, additional financial indicators, and credit-score segmentation.*

> **To display the preview on GitHub:** save the dashboard screenshot as `loan_default_risk_dashboard.png` inside an `assets/` folder in this repository. If you use a different filename or folder, update the image path above.

---

## 📊 Dashboard Features

The dashboard uses a dark, executive-style layout to keep the main metrics and comparisons together on one page.

### 1. Interactive Filters

The sidebar includes filters for:

- Application Year
- Employment Type
- Loan Type
- City Tier

These filters allow the displayed metrics and visuals to be explored for selected parts of the portfolio. A reset control is also included in the report.

### 2. Portfolio KPI Cards

The top row highlights five key metrics:

| KPI | Purpose |
|---|---|
| Total Loans | Counts the loan records included in the current filter context |
| Defaulted Loans | Counts records where `Default_Flag = 1` |
| Default Rate | Measures recorded defaults as a share of the included loan records |
| Average Loan Amount | Shows the average loan amount |
| Average Credit Score | Shows the average credit score |

### 3. Default Rate by Selected Dimension

The main horizontal bar chart works with the **Analyse By** selector. It can compare default rates across available dimensions, including:

- Loan Type
- Credit Score Band
- DTI Band
- LTV Band
- Employment Type
- Age Group
- City Tier
- State

This avoids needing a separate main chart for every dimension.

### 4. Default Rate Trend

The line/area visual compares the default rate across application years, helping users inspect changes over time.

### 5. Defaulted vs Non-Defaulted

The donut chart shows the share of records marked defaulted versus non-defaulted in the current filter context.

### 6. Additional Financial Indicators

Five supporting cards display:

- Average DTI
- Average LTV
- Average Interest Rate
- Average Credit Utilization
- Average Past Delinquencies

These metrics provide additional context alongside the default-rate visuals.

### 7. Default Rate by Credit Score

The credit-score chart compares default rates across the defined credit score bands, from Poor to Excellent.

---

## 🧮 Key Metrics and DAX

DAX measures are used to calculate the main KPIs. The following examples use the Power BI table name `Loan Default Risk`; update the table or column names if yours differ.

### Total Loans

```DAX
Total Loans =
COUNTROWS('Loan Default Risk')
```

### Defaulted Loans

```DAX
Defaulted Loans =
CALCULATE(
    COUNTROWS('Loan Default Risk'),
    'Loan Default Risk'[Default_Flag] = 1
)
```

### Default Rate

```DAX
Default Rate =
DIVIDE(
    [Defaulted Loans],
    [Total Loans],
    0
)
```

Format the `Default Rate` measure as a percentage in Power BI.

### Average Loan Amount

```DAX
Average Loan Amount =
AVERAGE('Loan Default Risk'[Loan_Amount])
```

### Average Credit Score

```DAX
Average Credit Score =
AVERAGE('Loan Default Risk'[Credit_Score])
```

These measures respond to the active filter context when used in interactive report visuals.

---

## 🔄 Dynamic Analysis: “Analyse By”

The dynamic selector lets the user change the category used in the main default-rate chart without duplicating the visual.

For example, a user can switch from loan type to credit score band, then to employment type or city tier, and compare the resulting default rates.

This design keeps the report compact while making it easier to explore different questions.

---

## 🔥 Credit Score and DTI Risk Analysis

Credit score and debt-to-income ratio describe different aspects of a borrower's financial profile:

- **Credit score** provides an indicator of credit history and creditworthiness.
- **DTI** represents the share of income committed to debt obligations.

Examining both together can provide more context than analysing either variable alone.

The Credit Score × DTI matrix is intended to compare default rates across combinations of these bands. Conditional formatting can make relatively higher and lower values easier to spot.

This matrix should be interpreted as a **descriptive comparison**. A high rate in a segment does not, by itself, prove that either factor caused the defaults, and segment sizes should be considered alongside the rates.

---

## 💡 Initial Observations

The dashboard screenshot shows the following values for the displayed portfolio view:

| Observation | Value shown |
|---|---:|
| Total loan records | 2,000 |
| Defaulted loans | 253 |
| Overall default rate | 12.65% |
| Average loan amount | ₹9,00,585 |
| Average credit score | 716.26 |
| Average DTI | 43.0% |
| Average LTV | 72.0% |
| Average interest rate | 11.3% |
| Average credit utilization | 42.0% |
| Average past delinquencies | 0.23 |

### 1. Default rate differs across loan types

In the displayed view, **Business Loans** have the highest default rate among the loan types shown. This makes loan type a useful dimension for further investigation.

### 2. Default rate varies across credit score bands

The screenshot shows a higher default rate in the **Poor** credit score band than in the **Excellent** band. This highlights why comparing borrower segments can be useful when exploring portfolio risk.

### 3. The yearly trend is not uniform

The chart shows the default rate declining between 2022 and 2024, followed by an increase in 2025. This is a useful pattern to investigate further, rather than assuming that the decline will continue.

> **Important:** These observations describe the values visible in the dashboard screenshot. They may change when filters are applied, and should not be interpreted as causal conclusions or predictions about future defaults.

---

## 🔁 Analytical Workflow

```text
Raw Loan Dataset
       │
       ▼
Review and Understand Data
       │
       ▼
Clean and Prepare with Python
       │
       ▼
Create Analytical Bands
       │
       ▼
Import into Power BI
       │
       ▼
Build DAX Measures
       │
       ▼
Create Interactive Visuals
       │
       ▼
Compare Default Rates
       │
       ▼
Explore Portfolio Risk Patterns
```

---

## 🛠️ Tech Stack

| Tool | Role in the project |
|---|---|
| Python | Data cleaning and preparation |
| Pandas | Data manipulation and validation |
| Power BI | Interactive dashboard and visual analysis |
| DAX | KPI calculations and measures |
| Git & GitHub | Version control and project documentation |

---

## 📁 Repository Structure

A recommended structure for the repository is:

```text
loan-default-risk-analysis/
│
├── assets/
│   └── loan_default_risk_dashboard.png
│
├── data/
│   └── loan_default_risk_cleaned.csv
│
├── python/
│   └── loan_data_cleaning.ipynb
│
├── powerbi/
│   └── loan_default_risk_dashboard.pbix
│
├── requirements.txt
└── README.md
```

*The folder and file names above are suggested. Keep only the files that you actually upload, and adjust the README paths to match your repository.*

**Data note:** Only publish the dataset if you have permission to share it. If the source data is restricted or sensitive, omit it and document how to obtain an approved copy instead.

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/Vanshika26Ramjas/loan-default-risk-analysis.git
cd loan-default-risk-analysis
```

### 2. Install Python dependencies

If you have included a Python cleaning notebook, install its dependencies:

```bash
pip install pandas numpy jupyter
```

Alternatively, if you create a `requirements.txt` file, install the listed dependencies with:

```bash
pip install -r requirements.txt
```

### 3. Run the data preparation notebook

```bash
jupyter notebook
```

Open the notebook inside the `python/` folder and run the cells using your permitted source dataset.

### 4. Open the Power BI report

Open the `.pbix` file inside the `powerbi/` folder using Power BI Desktop.

If the report asks for a data source, update the file path or reconnect it to the permitted dataset location.

---

## ⚠️ Limitations and Interpretation

- This project is focused on descriptive analysis and visualization, not predictive modelling.
- Observed relationships do not prove causation.
- Default rates can be unstable for segments with very few loans; always consider the number of records alongside a rate.
- The dashboard's metrics depend on the selected filters and the data available.
- Missing LTV values may be structurally meaningful for unsecured loans and should not automatically be treated as zero.
- The results reflect this dataset and should not be generalized to every lender or borrower population.

---

## 🔮 Future Improvements

Potential next steps include:

- Adding segment loan counts alongside default rates.
- Adding drill-through views for selected loan categories.
- Improving tooltips to show both rates and record counts.
- Adding data refresh documentation.
- Comparing more borrower and loan segments.
- Exploring predictive modelling as a separate extension, if appropriate data and validation are available.

---

## 👩‍💻 Author

### Vanshika Kumar

Statistics (Hons.) | Ramjas College, University of Delhi

Interested in applying statistics, programming, and business intelligence to practical analytical problems.

**Tools and skills:** Python · SQL · Power BI · Tableau · Excel · DAX · Statistics · Data Visualization

- **GitHub:** [Vanshika26Ramjas](https://github.com/Vanshika26Ramjas)
- **LinkedIn:** [Vanshika Kumar](https://www.linkedin.com/in/vanshika-kumar09/)

---

⭐ If you find this project interesting, feel free to explore the repository and connect with me.

*Built with Python, Power BI, DAX, and a focus on understanding loan portfolio risk.*

