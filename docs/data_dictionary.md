# Saudi Arabia Crime Analysis — Data Dictionary

## Project Overview
End-to-end crime analytics dashboard for Saudi Arabia built in Tableau,
covering 48,505 cases from 2014–2023.

---

## Dataset: `saudi_crime_raw.csv`
Raw dataset with intentional data quality issues for cleaning demonstration.

| Column | Type | Description | Issues |
|---|---|---|---|
| Case_ID | String | Unique case identifier (e.g. SA-2014-000001) | ~2% duplicates |
| Arrest_Date | String | Date of arrest (YYYY-MM-DD) | ~3% invalid values (N/A, TBD, 0000-00-00) |
| Year_of_Arrest | Integer | Year extracted from Arrest_Date | Missing where date is invalid |
| Month_of_Arrest | String | Month name extracted from Arrest_Date | Missing where date is invalid |
| Region | String | Saudi region where arrest occurred | No issues |
| Nationality | String | Nationality of the arrested individual | ~5% missing |
| Age_at_Arrest | Integer | Age of individual at time of arrest | ~4% outliers (0, -1, 999) |
| Charge_1_Statute | String | Primary offence category | No issues |
| Charge_2_Statute | String | Sub-charge / offence detail | No issues |
| Charge_3_Statute | String | Legal disposition / outcome | ~1% missing |
| Charge_4_Statute | String | Enforcement agency | No issues |

---

## Dataset: `saudi_crime_clean.csv`
Cleaned dataset after 10-step pipeline. Ready for Tableau.

| Column | Type | Description |
|---|---|---|
| Case_ID | String | Unique case identifier |
| Arrest_Date | Date | Parsed and validated date |
| Year_of_Arrest | Integer | Year of arrest (2014–2023) |
| Month_of_Arrest | String | Full month name (January–December) |
| Region | String | One of 13 Saudi regions |
| Nationality | String | Nationality (missing filled as "Unknown / Refused") |
| Age_at_Arrest | Integer | Cleaned age (outliers replaced with median = 32) |
| Charge_1_Statute | String | Primary offence category |
| Charge_2_Statute | String | Sub-charge detail |
| Charge_3_Statute | String | Legal outcome (missing filled as "Not Recorded") |
| Charge_4_Statute | String | Enforcement agency |
| Age_Group | String | Derived age bracket (14-17, 18-24, 25-34, 35-44, 45-54, 55-64, 65+) |
| Quarter | String | Fiscal quarter (Q1, Q2, Q3, Q4) |

---

## Regions Covered (13)
Riyadh, Makkah, Madinah, Eastern Province, Asir, Tabuk, Hail,
Qassim, Jizan, Najran, Al Baha, Northern Borders, Al Jouf

## Nationalities Covered (10)
Saudi, Yemeni, Pakistani, Indian, Egyptian, Ethiopian,
Bangladeshi, Syrian, Filipino, Other / Refused

## Charge 1 — Primary Offence Categories
| Offence | Approx. Share |
|---|---|
| Drug Possession / Trafficking | 28% |
| Theft / Burglary | 18% |
| Assault / Battery | 13% |
| Illegal Residency / Visa Violation | 11% |
| Fraud / Financial Crime | 9% |
| Traffic & Road Violations | 7% |
| Domestic Violence | 6% |
| Public Intoxication | 4% |
| Cybercrime | 3% |
| Weapon Possession | 1% |

---

## Cleaning Pipeline Summary (`cleaning_pipeline.py`)

| Step | Action | Rows Affected |
|---|---|---|
| 1 | Drop full duplicate rows | ~1,000 |
| 2 | Parse invalid Arrest_Date strings → NaT | ~1,500 |
| 3 | Drop rows with no valid date | ~1,500 |
| 4 | Re-derive Year & Month from clean date | All |
| 5 | Replace age outliers with median (32) | ~2,000 |
| 6 | Fill missing Nationality → "Unknown / Refused" | ~2,500 |
| 7 | Fill missing Charge_3 → "Not Recorded" | ~500 |
| 8 | Strip & standardise all text columns | All |
| 9 | Add Age_Group column | All |
| 10 | Add Quarter column & sort by date | All |

**Raw records:** 50,000 → **Clean records:** 48,505

---

## Tableau Dashboard Sheets

| Sheet Name | Chart Type | Fields Used |
|---|---|---|
| KPI-1 Total Cases Filed | Text / KPI | COUNT(Case ID) |
| KPI-2 Total Regions Covered | Text / KPI | COUNTD(Region) |
| KPI-3 Most Common Offence | Text / KPI | MAX(Charge 2 Statute) |
| KPI-4 Most Affected Nationality | Text / KPI | MAX(Nationality) |
| Yearly Trend | Bar Chart | Year of Arrest, COUNT(Case ID) |
| Monthly | Line Chart | Month of Arrest, COUNT(Case ID) |
| Race | Pie / Donut Chart | Nationality, COUNT(Case ID) |
| Charge 2 Statute | Horizontal Bar | Charge 2 Statute, COUNT(Case ID) |

---

## Tools Used
- **Python** — pandas, numpy (data generation & cleaning)
- **Tableau Public** — dashboard & visualisation
- **Jupyter Notebook** — exploratory data analysis
- **GitHub** — version control & project documentation

---

*Note: This dataset is synthetically generated for educational and portfolio purposes,
modelled on publicly available Saudi Arabia demographic and crime statistics.*
