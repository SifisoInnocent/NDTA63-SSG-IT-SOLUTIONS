# NDTA63 – Data Analysis and Visualisation: South Africa Tertiary Education & Unemployment

**Group Assignment | Diploma in ICT | Examiner: Melvin Kisten**

[![License: GPL v2](https://img.shields.io/badge/License-GPL%20v2-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)
[![Made with Jupyter](https://img.shields.io/badge/Made%20with-Jupyter-orange?logo=Jupyter)](https://jupyter.org/try)
[![Python 3.13+](https://img.shields.io/badge/python-3.13+-blue.svg)](https://www.python.org/downloads/)

---

## 📌 Overview

This repository contains the complete codebase and analysis pipeline for the **NDTA631** group assignment. The project investigates the relationship between **tertiary education enrolment** and **unemployment** in South Africa using two World Bank Open Data indicators:

- **School enrolment, tertiary (% gross)** – `API_SE.TER.ENRR_DS2_en_csv_v2_34068`
- **Unemployment, total (% of total labour force) (modelled ILO estimate)** – `API_SL.UEM.TOTL.ZS_DS2_en_csv_v2_33398`

The analysis follows a complete end-to-end pipeline:
- **Data loading, cleaning & merging** – Pandas
- **Numerical analysis & correlation** – NumPy
- **Visualisation** – Matplotlib & Seaborn
- **Database storage & querying** – SQLite
- **Excel export with formatting** – OpenPyXL

> **Key Finding:** The Pearson correlation coefficient between tertiary enrolment and unemployment is **0.8314**, indicating a strong positive association over the observed years (1991–1994 & 2012–2023). **Correlation does not imply causation** – other economic, demographic and labour-market factors are likely at play.

---

## 🔗 Repository & Demo Links

| Item | Link |
|------|------|
| **Forked GitHub Repository** | [https://github.com/SifisoInnocent/NDTA63-SSG-IT-SOLUTIONS](https://github.com/SifisoInnocent/NDTA63-SSG-IT-SOLUTIONS) |
| **Video Demonstration** | [https://drive.google.com/file/d/1yaMrZnbGbRE8iWFVoVRFMR7HEHBwljg7/view?usp=sharing](https://drive.google.com/file/d/1yaMrZnbGbRE8iWFVoVRFMR7HEHBwljg7/view?usp=sharing) |
| **Original Fork Source** | [https://github.com/iammelvink/NDTA63](https://github.com/iammelvink/NDTA63) |

---

## 👥 Group Members

| Full Name | Student Number |
|-----------|----------------|
| Bongani Collen Shongwe | 202414381 |
| Ayanda Andile Sibiya | 202401043 |
| Tshepo Tjakame | 202411606 |
| **Sifiso Innocent Lukhele** | **202401735** |
| Mxolisi Maseko | 202423100 |
| Luxolo Ndwanyaza | 202352814 |
| Karabo Seboko | 202400157 |

---

## 📂 Repository Structure

```
NDTA63-SSG-IT-SOLUTIONS/
├── SSG Datasets/                    # Raw and cleaned datasets
│   ├── education/                   # Education CSV files from World Bank
│   └── unemployment/                # Unemployment CSV files from World Bank
├── SSG IT SOLUTIONS.ipynb                   # Main Jupyter Notebook with complete code

├── requirements.txt                 # Python dependencies
├── README.md                        # This file
└── LICENSE                          # GNU General Public License v2.0
```

---

## 📦 Dependencies

The following Python packages are required (listed in `requirements.txt`):

| Package | Purpose |
|---------|---------|
| `pandas` | Data loading, cleaning, merging, and analysis |
| `numpy` | Numerical computations, array operations, correlation |
| `matplotlib` | Core plotting and visualisation |
| `seaborn` | Statistical visualisations (heatmaps, regression plots) |
| `openpyxl` | Excel export with formatting and conditional styling |
| `sqlite3` | Built-in – database creation and querying |

---

## 🚀 Code Overview (analysis.ipynb)

The Jupyter Notebook is organised into **68 executable cells** across the following sections:

| Section | Cells | Description |
|---------|-------|-------------|
| **Setup** | 1–2 | Import libraries (Pandas, NumPy, Matplotlib, Seaborn) |
| **Data Loading** | 2–5 | Load World Bank CSV files with `skiprows=4` to bypass metadata |
| **Data Cleaning** | 6–14 | Extract South Africa, reshape from wide to long format using `melt()`, merge on Year, handle missing values |
| **NumPy Analysis** | 23–33 | Create arrays, compute mean, median, std, min, max, range, correlation (`np.corrcoef`), array reshaping |
| **Visualisation** | 34–45 | Generate line plots, scatter plots, regression plots, histograms, boxplots, bar charts, and correlation heatmap |
| **SQLite Database** | 46–67 | Create `combined_data` table, insert records, run SELECT/UPDATE/DELETE queries, reload into Pandas |
| **Excel Export** | 68–79 | Export to `.xlsx` with header formatting and numeric formatting |

---

## 📈 Key Results

| Metric | Education | Unemployment |
|--------|-----------|--------------|
| **Mean** | 19.02% | 26.87% |
| **Median** | 18.98% | 25.84% |
| **Standard Deviation** | 3.79% | 3.50% |
| **Minimum** | 11.85% (1991) | 23.07% (1994) |
| **Maximum** | 23.73% (2022) | 34.01% (2021) |
| **Range** | 11.88% | 10.94% |

- **Pearson Correlation Coefficient:** **0.8314** – a strong positive linear association
- Years with above-average unemployment: 2017, 2018, 2019, 2020, 2021, 2022, 2023

> **Context:** South Africa's gross tertiary enrolment rate (~19%) lags behind most global peers, while youth unemployment remains among the highest in the world. These trends highlight the complexity of the education-employment relationship in the country.

---

## 📊 Visualisation Gallery

The notebook generates the following charts (saved in the `charts/` directory):

1. **Line Chart** – Tertiary enrolment and unemployment over time (1991–2023)
2. **Scatter Plot** – Education vs Unemployment with regression line
3. **Correlation Heatmap** – Visual representation of the 0.8314 correlation
4. **Histograms** – Distribution of education enrolment and unemployment
5. **Box Plot** – Distribution comparison between the two indicators
6. **Bar Chart** – Average values comparison

---

## 💾 Database Integration (SQLite)

The pipeline creates a SQLite database (`ndta631_analysis.db`) with a `combined_data` table:

```sql
CREATE TABLE combined_data (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    year INTEGER NOT NULL UNIQUE,
    education REAL,
    unemployment REAL
);
```

**Operations demonstrated:**
- **INSERT** – Parameterised insertion of all 16 cleaned records
- **SELECT** – Query for years with unemployment above the average (ordered by rate)
- **UPDATE** – Safe, parameterised update (with before/after verification)
- **DELETE** – Temporary record insertion and safe deletion

---

## 📄 Excel Export

The final dataset is exported to `NDTA631_South_Africa_Analysis.xlsx` with:
- Bold, centred headers
- Numeric formatting to two decimal places
- Colour‑scale conditional formatting (low → green, high → red)

---

## 📝 Report

The accompanying group report (`NDTA631_Group_Assignment.docx`) provides:
- Executive Summary
- Data Preparation & Methodology
- Numerical Analysis (NumPy)
- Visualisation & Insights
- Database Integration (SQLite)
- Python/Excel Data Analysis
- Technical Challenges & Solutions
- Conclusion & References

---

## 🙏 Acknowledgements

- **Examiner:** Melvin Kisten – NDTA631, Diploma in ICT
- **Data Source:** World Bank Open Data – [Data360 South Africa](https://data360.worldbank.org/en/search?country=ZAF)
- **Original Template:** [iammelvink/NDTA63](https://github.com/iammelvink/NDTA63)
- **Libraries:** Pandas, NumPy, Matplotlib, Seaborn, OpenPyXL, SQLite

---

## 📜 License

This project is licensed under the **GNU General Public License v2.0** – see the [LICENSE](LICENSE) file for details.

---

## 📬 Contact

For any questions regarding this repository, please reach out to the group via the course coordinator or raise an issue on GitHub.

---

**Last Updated:** August 2026
