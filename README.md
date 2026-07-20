# 🏠 Toronto Shelter System Flow Analysis (2018-2026)

A full data analysis project exploring homelessness trends in Toronto's
shelter system across 8+ years of monthly data, covering 8 population
groups including Chronic, Refugees, Families, Youth, and Indigenous peoples.

This project covers the complete data analysis life cycle - from raw data
cleaning to exploratory analysis, visualization, and predictive modeling.

## 📁 Project Structure

    toronto-shelter-analysis/
    ├── data/
    │   ├── raw/                    # Original CSV file from Toronto Open Data
    │   └── processed/              # Cleaned dataset
    ├── scripts/
    │   ├── 01_data_cleaning.py     # Data cleaning and type fixing
    │   ├── 02_eda.py               # Exploratory data analysis
    │   ├── 03_visualization.py     # Charts and visualizations
    │   └── 04_modeling.py          # Regression modeling and forecasting
    ├── outputs/
    │   └── figures/                # All saved charts (PNG)
    ├── README.md
    └── requirements.txt


## 📊 Dataset

- **Source:** [Toronto Open Data - Toronto Shelter System Flow](https://open.toronto.ca/dataset/toronto-shelter-system-flow/)
- **Period:** January 2018 to June 2026
- **Records:** 780 rows, 20 columns
- **Population groups:** All Population, Chronic, Refugees, Families, Youth, Single Adult, Non-refugees, Indigenous

## 🔧 Tools & Libraries

- Python 3
- pandas
- matplotlib
- seaborn
- scikit-learn

Install dependencies:

    pip install pandas matplotlib seaborn scikit-learn


## 🔄 How to Run

Run the scripts in order from the project root directory:

    py scripts/01_data_cleaning.py
    py scripts/02_eda.py
    py scripts/03_visualization.py
    py scripts/04_modeling.py


## 🔍 Key Findings

### Data Cleaning
- Converted date column from string (e.g. "Jan-18") to proper datetime
- Converted population_group_percentage from string ("31.8%") to float
- Standardized all column names
- Added year and month columns for time-based analysis
- No missing values or duplicates found

### Exploratory Data Analysis
- Average of **9,644 people actively homeless** per month across all years
- Homelessness **dropped sharply in 2020** (avg 8,315) due to COVID-19 policies
- Numbers rebounded and **peaked at 11,780 in January 2025**
- **Single Adults** are the largest group (avg 6,299 per month)
- **Chronic homelessness** averages 4,819 per month - persistently high
- Monthly inflow **(1,223)** consistently exceeds outflow **(1,167)**
- Net gain of **56 people per month** - system is not keeping pace
- Most exits are through **became inactive (701)** not **moved to housing (466)**
- **61.1% male**, 37.6% female, 1.3% transgender/non-binary
- **Ages 35-44** are the largest age group (21.8%)
- **Children under 16** make up 12.8% of shelter users

### Modeling
| Model | R² | RMSE | CV R² |
|-------|----|------|-------|
| Linear Regression | 0.4539 | 902.15 | -2.2247 |
| Random Forest | 0.5005 | 862.85 | -1.8858 |

- **Random Forest** outperformed Linear Regression on all metrics
- Negative CV R² scores indicate the data has strong **temporal dependencies**
- Standard regression is limited here - this data is better suited to time series modeling
- **newly_identified** is the most important feature (importance = 0.298)
- 6-month linear trend forecast projects **~10,600-10,700** actively homeless through Dec 2026


## 📈 Visualizations

| # | Chart | Description |
|---|-------|-------------|
| 1 | Homeless Trend | Actively homeless 2018-2026 with COVID annotation |
| 2 | By Population Group | Average actively homeless per group |
| 3 | Shelter Flow | Monthly inflow vs outflow breakdown |
| 4 | COVID Impact | Yearly average with COVID years highlighted |
| 5 | Gender Breakdown | Pie chart of shelter user gender distribution |
| 6 | Age Breakdown | Average monthly count by age group |
| 7 | Chronic vs All | Chronic homelessness trend vs all population |
| 8 | Actual vs Predicted | Model performance comparison |
| 9 | Feature Importance | Random Forest feature ranking |
| 10 | Forecast | Historical trend + 6-month projection |

