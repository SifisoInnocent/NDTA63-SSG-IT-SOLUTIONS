NDTA63-SSG-IT-SOLUTIONS
South Africa: Analysing the Relationship Between Tertiary Education Enrolment and Unemployment
This repository contains the complete codebase and analysis pipeline for the group assignment in NDTA63 – Data Analysis and Visualisation at the Diploma in ICT programme.
________________________________________
📌 Project Overview
This project investigates the relationship between tertiary education enrolment and unemployment in South Africa using two World Bank Open Data indicators:
•	School enrolment, tertiary (% gross)
•	Unemployment, total (% of total labour force) (modelled ILO estimate)
The analysis pipeline includes:
•	Data loading, cleaning, and merging using Pandas
•	Numerical analysis and correlation using NumPy
•	Visualisation with Matplotlib and Seaborn
•	Database storage and querying with SQLite
•	Excel export with formatting for reporting
________________________________________
📂 Repository Structure
text
NDTA63-SSG-IT-SOLUTIONS/
├── SSG Datasets/                    # Raw and cleaned datasets
│   ├── education/                   # Education CSV files
│   └── unemployment/                # Unemployment CSV files
├── analysis.ipynb                   # Main Jupyter Notebook with all code
├── charts/                          # Generated plots (optional output)
├── database/                        # SQLite database file (if generated)
├── requirements.txt                 # Python dependencies
├── README.md                        # This file
└── LICENSE                          # GNU GPL v2.0
________________________________________
📊 Datasets
The datasets are sourced from the World Bank Open Data portal:
•	Education dataset: API_SE.TER.ENRR_DS2_en_csv_v2_34068.csv
•	Unemployment dataset: API_SL.UEM.TOTL.ZS_DS2_en_csv_v2_33398.csv
Both datasets were filtered for South Africa (Country Name == "South Africa") and cleaned to include only years with valid observations in both indicators.
________________________________________
🛠️ Installation & Requirements
1. Clone the repository
bash
git clone https://github.com/Sifisolnnocent/NDTA63-SSG-IT-SOLUTIONS.git
cd NDTA63-SSG-IT-SOLUTIONS
2. Set up a virtual environment (optional but recommended)
bash
python -m venv venv
source venv/bin/activate   # On Windows: venv\Scripts\activate
3. Install dependencies
bash
pip install -r requirements.txt
4. Launch Jupyter Notebook
bash
jupyter notebook
Then open analysis.ipynb.
________________________________________
📦 Dependencies
The code requires the following Python packages:
•	pandas
•	numpy
•	matplotlib
•	seaborn
•	openpyxl
•	sqlite3 (built-in)
These are listed in requirements.txt.
________________________________________
🚀 Running the Analysis
1.	Load and clean data – Cells 1–14 read the CSV files, extract South Africa, reshape from wide to long format, and merge both indicators by year.
2.	Numerical analysis – Cells 23–33 compute descriptive statistics, correlation, and perform array operations using NumPy.
3.	Visualisation – Cells 34–45 generate eight publication ready plots (line chart, scatter plot, regression plot, histogram, boxplot, bar chart, heatmap).
4.	Database integration – Cells 46–67 create a SQLite database, insert the cleaned data, run SELECT/UPDATE/DELETE queries, and reload the data into Pandas.
5.	Excel export – Cells 68–79 write the final dataset to an Excel file with header and numeric formatting.
________________________________________
📈 Key Findings
•	Mean tertiary enrolment (1991–1994 & 2012–2023): 19.02%
•	Mean unemployment rate: 26.87%
•	Pearson correlation coefficient: 0.8314 (strong positive association)
Note: Correlation does not imply causation. The observed relationship may be influenced by other economic, demographic, and labour market factors.
________________________________________
👥 Group Members
Name	Student Number
Bongani Collen Shongwe	202414381
Ayanda Andile Sibiya	202401043
Tshepo Tjakame	202411606
Sifiso Innocent Lukhele	202401735
Mxolisi Maseko	202423100
Luxolo Ndwanyaza	202352814
Karabo Seboko	202400157
________________________________________
________________________________________
🙏 Acknowledgements
•	Lecturer: Melvin Kisten
•	Course: NDTA631 – Data Analysis and Visualisation
•	Data source: World Bank Open Data
•	Original template repository by iammelvink/NDTA63
________________________________________
🔗 Links
•	GitHub Repository: SifisoInnocent/NDTA63-SSG-IT-SOLUTIONS: This is the codebase produced for the NDTA63 Data Analysis and Visualization course
•	Video Demonstration: WhatsApp Video 2026-08-23 at 17.14.51.mp4 - Google Drive
•	World Bank Data: Data360 – South Africa
