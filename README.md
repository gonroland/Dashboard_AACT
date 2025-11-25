🧬 Clinical Trials Analytics Dashboard (AACT)

An end-to-end Power BI project analyzing global clinical trial data using the AACT (Aggregate Analysis of ClinicalTrials.gov) database.
This dashboard provides insights into study design quality, clinical conditions, geographical distribution, phases, sponsors, and enrollment trends of interventional trials worldwide.

📌 Project Overview

This project simulates a real-world analytics environment for pharmaceutical and biotech use cases.
The goal is to understand activity, trends, and design rigor behind clinical trials registered in ClinicalTrials.gov, using real data exported from AACT.

The dashboard is structured as a multi-page Power BI report covering:

Trial phases

Study design (randomization, masking, purpose)

Conditions & therapeutic areas

Enrollment metrics

Sponsor insights

Geographic distribution

KPI cards derived from DAX

🎯 Objectives

This project demonstrates:

✔ Data modeling with multiple fact tables (studies, designs, conditions, facilities, sponsors)
✔ Cleaning and normalization of clinical trial metadata
✔ Creation of high-value KPIs for the pharma industry
✔ Advanced DAX (relationships, TREATAS, conditional measures, % metrics)
✔ Dashboard UX design following healthcare analytics standards
✔ Use of AACT “Flat Files” export (2GB+) as a real dataset for BI
🗂 Dataset: AACT (ClinicalTrials.gov)

Source: https://aact.ctti-clinicaltrials.org

This dataset contains >500,000 clinical studies across multiple files. The project uses the following core tables:

AACT Table	Description
studies	Main study metadata (phase, status, enrollment, dates)
conditions	Medical conditions assigned to each study
designs	Study design: allocation, masking, intervention model, primary purpose
sponsors	Lead and collaborator information
facilities	Geographic metadata (country, city, site)

Data was imported using Power Query, cleaned, normalized, and transformed into a star schema.

🧱 Data Model (Star Schema)
Fact tables

studies

designs

conditions

sponsors

facilities

Dimension tables

DimDate (generated via CALENDAR)

🔗 Key relationships

All tables connect through:

nct_id ←→ nct_id


Cross-filter: Both (avoid duplicates using DISTINCTCOUNT)

📊 Dashboard Pages
1️⃣ Overview

Total Studies

Study Type distribution

Phases

Status

Enrollment KPIs

Timeline of studies initiated per year

<img width="1334" height="751" alt="Screenshot 2025-11-25 131159" src="https://github.com/user-attachments/assets/f45baf16-736d-499a-bb3e-bc8e694f7c4f" />

2️⃣ Phases & Status

Completion Rate %

Termination Rate %

Avg Duration (days)

Table of phase-wise performance

100% stacked bars for status distribution

<img width="1313" height="734" alt="Screenshot 2025-11-25 132018" src="https://github.com/user-attachments/assets/777293b5-b74c-4de7-a765-dac32eea4357" />

3️⃣ Conditions

KPIs:

Total Conditions

Studies per Condition

Avg Enrollment per Condition

Enrollment Top 5

Word Cloud of top conditions

Table: TOP 20 conditions

Filtro por Phase, Status, Study Type

<img width="1311" height="737" alt="Screenshot 2025-11-25 132633" src="https://github.com/user-attachments/assets/04219f22-fa48-4d78-90ce-11d12b5064dc" />

4️⃣ Study Design

Total Studies by Allocation (Randomized / Non-randomized)

Randomization Rate %

Total Studies by Primary Purpose

Total Studies by Masking (None, Single, Double, Triple, Quadruple)

Allocation by Phase

<img width="1320" height="739" alt="image" src="https://github.com/user-attachments/assets/79c18988-589a-4354-97d5-3f06ce18b751" />

5️⃣ Geography

Map: studies per country

Table of top recruiting countries

Enrollment heatmap

Slicers: Phase, Status, Study Type

<img width="1314" height="736" alt="image" src="https://github.com/user-attachments/assets/fccfc4f4-94ee-4718-883c-5be321a811af" />

6️⃣ Sponsors

Top sponsors (Industry vs NIH vs Academic)

Lead vs collaborator

Studies per sponsor

Sponsor class comparison

<img width="1312" height="736" alt="image" src="https://github.com/user-attachments/assets/1c30db50-f2a2-4606-945d-4063f488f082" />

📐 Key KPIs & DAX

Here are some of the main measures used in the project:

Total Studies =
COUNTROWS(studies)

Total Studies Distinct =
DISTINCTCOUNT(studies[nct_id])

Randomization Metrics:
Randomized Studies =
CALCULATE(
    DISTINCTCOUNT(designs[nct_id]),
    designs[allocation] = "RANDOMIZED"
)

Randomization Rate % =
DIVIDE(
    [Randomized Studies],
    [Total Studies Distinct]
)

Conditions:
Total Conditions =
DISTINCTCOUNT(conditions[name])

Studies per Condition =
CALCULATE([Total Studies], ALLEXCEPT(conditions, conditions[name]))

🧪 Technologies Used

Power BI Desktop

Power Query (M Language)

DAX

AACT Open Clinical Trials Database

GitHub

📜 License

This project is for educational and portfolio demonstration purposes only.
AACT datasets remain under their own license and terms of use.

🙌 Author

Gonzalo Rolando
Data Analytics & Power BI Developer
Clinical Research Analytics (AACT) | Pharma BI Solutions

