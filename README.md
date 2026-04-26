# 🇸🇦 Saudi Arabia Crime Analysis Dashboard 2026

An end-to-end data analytics project covering crime data across Saudi Arabia (2014–2023), built with Python and Tableau Public.

---

## 📊 Dashboard Preview

![Saudi Arab Crime Analysis Dashboard](docs/dashboard_preview.png)

> **Live Dashboard:** [View on Tableau Public](#) *(replace with your link)*

---

## 📁 Project Structure

```
SA-Crime-Analysis-2026/
│
├── data/
│   ├── saudi_crime_raw.csv          # Raw dataset (50,000 records with data issues)
│   └── saudi_crime_clean.csv        # Cleaned dataset (48,505 records, Tableau-ready)
│
├── notebooks/
│   ├── 01_generate_raw.ipynb        # Raw data generation
│   ├── 02_cleaning_pipeline.ipynb   # Step-by-step data cleaning
│   └── 03_eda.ipynb                 # Exploratory data analysis
│
├── scripts/
│   ├── generate_raw_data.py         # Standalone raw data generator
│   └── cleaning_pipeline.py         # Standalone cleaning pipeline
│
├── tableau/
│   └── SA_Crime_Dashboard.twbx      # Tableau workbook
│
├── docs/
│   ├── dashboard_preview.png        # Dashboard screenshot
│   └── data_dictionary.md           # Column definitions & data reference
│
├── .gitignore
└── README.md
```

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| Python (pandas, numpy) | Data generation & cleaning pipeline |
| Jupyter Notebook | EDA & step-by-step analysis |
| Tableau Public | Interactive dashboard & visualisation |
| GitHub | Version control & project hosting |

---

## 🔄 Data Pipeline

```
Raw Data (50,000 records)
        ↓
  10-Step Cleaning Pipeline
        ↓
Clean Data (48,505 records)
        ↓
  Tableau Dashboard
```

### Cleaning Steps
1. Drop duplicate rows
2. Parse & fix invalid date strings
3. Drop rows with no valid date
4. Re-derive Year & Month from clean date
5. Replace age outliers with median imputation
6. Fill missing Nationality → "Unknown / Refused"
7. Fill missing Charge 3 → "Not Recorded"
8. Strip & standardise all text columns
9. Add Age Group column
10. Add Quarter column & sort by date

---

## 📈 Dashboard Sheets

| Sheet | Chart Type | Insight |
|---|---|---|
| KPI-1 Total Cases Filed | KPI Card | 48,505 total cases |
| KPI-2 Total Regions Covered | KPI Card | 13 Saudi regions |
| KPI-3 Most Common Offence | KPI Card | Working Without Permit |
| KPI-4 Most Affected Nationality | KPI Card | Yemeni |
| Yearly Trend | Bar Chart | Cases per year 2014–2023 |
| Monthly Trend | Line Chart | Seasonal monthly pattern |
| Crime by Nationality | Pie Chart | Nationality breakdown |
| Top 10 Charges | Horizontal Bar | Most filed sub-charges |

---

## 🚀 How to Run

### 1. Clone the repo
```bash
git clone https://github.com/Sibtain28/SA-Crime-Analysis-2026.git
cd SA-Crime-Analysis-2026
```

### 2. Install dependencies
```bash
pip install pandas numpy
```

### 3. Generate raw data
```bash
python scripts/generate_raw_data.py
```

### 4. Run cleaning pipeline
```bash
python scripts/cleaning_pipeline.py
```

### 5. Open Tableau
- Open `tableau/SA_Crime_Dashboard.twbx` in Tableau Public
- Or import `data/saudi_crime_clean.csv` and build from scratch

---

## 📌 Key Findings

- **Peak Year:** 2014 had the highest number of cases (6,728)
- **Most Common Offence:** Working Without Permit (Illegal Residency)
- **Most Affected Nationality:** Yemeni nationals
- **Top Region:** Riyadh accounts for the highest case volume
- **Trend:** Cases dropped significantly in 2020–2021 (COVID-19 impact)

---

## ⚠️ Disclaimer

> This dataset is **synthetically generated** for educational and portfolio purposes only.
> It is modelled on publicly available Saudi Arabia demographic statistics and does not
> represent real individuals or actual crime records.

---

## 👤 Author

**Sibtain** — Full Stack Developer | Data Visualization & Analytics | Generative AI

[![GitHub](https://img.shields.io/badge/GitHub-Sibtain28-black?logo=github)](https://github.com/Sibtain28).
