# DSA3050_End_Sem
# 1. Project Title
**Advanced Power BI Examination: Healthcare Operations and Patient Flow Analytics**

---

# 2. Student Details
* **Student Name:** Mohamed
* **Admission Number / Student ID:** 006

---

# 3. Course Information
* **Course Code:** DSA 3050A
* **Class Name:** Advanced Business Intelligence & Data Visualization
* **Institution:** United States International University - Africa (USIU-Africa)

---

# 4. Project Overview
This project is a comprehensive end-to-end Business Intelligence solution developed as part of an advanced practical examination. The objective was to ingest, clean, model, and visualize raw healthcare data to provide hospital administration with an interactive command center. The resulting Power BI dashboard enables clinical directors and executives to monitor critical operational KPIs, such as patient volumes, average Length of Stay (LOS), and historical readmission rates.

---

# 5. Problem Statement
A large, multi-facility healthcare network is experiencing severe operational bottlenecks due to unpredictable patient flow and fluctuating ward capacities. Hospital administration lacks granular, data-driven visibility into how specific patient demographics, pre-existing comorbidities, and initial clinical vitals impact the overall length of hospitalization. Without this visibility, the network struggles to proactively allocate medical staff, manage bed capacity, and reduce costly patient readmissions.

---

# 6. Dataset Description
* **Source:** Kaggle (Microsoft Open-Source Data)
* **Domain:** Healthcare Analytics
* **Structure:** Originally acquired as a wide, 28-column flat file containing thousands of anonymized patient encounter records. 
* **Key Fields:** The dataset includes patient demographics (`gender`), dates (`vdate`, `discharged`), Boolean comorbidity flags (e.g., `asthma`, `dialysisren`), clinical admission labs (e.g., `glucose`, `bmi`), and routing information (`facid`).

---

# 7. Tools Used
* **Microsoft Power BI Desktop:** Used for the entire BI pipeline (Data ingestion, ETL, modeling, and visualization).
* **Power Query Editor:** Utilized for data cleaning, unpivoting, and structural transformations.
* **DAX (Data Analysis Expressions):** Used for creating custom calculated columns and advanced operational measures.
* **GitHub:** Used for version control, documentation, and final exam submission.

---

# 8. Steps Followed
1. **Data Acquisition:** Imported the raw flat file into Power BI via the Text/CSV connector.
2. **Data Cleaning & Transformation:** Utilized Power Query to promote headers, correct data types, remove duplicates, extract date components, and create conditional columns (e.g., LOS Categories).
3. **Data Modeling (Star Schema):** Duplicated the main query to vertically partition the data into a robust Star Schema, surrounding a central `Fact_Admissions` table with dimensional tables (`Dim_Patient_Profile`, `Dim_Clinical_Records`, `Dim_Facilities`, and `Dim_Date`).
4. **DAX Development:** Authored 8+ advanced DAX measures and 2 calculated columns to aggregate operational metrics and apply business logic.
5. **Dashboard Design:** Designed a 3-page interactive dashboard utilizing a high-contrast corporate theme, logical UI layouts, and advanced analytical AI visuals.

---

# 9. Dashboard Features
The interactive dashboard is divided into three distinct pages:
* **Page 1: Executive Summary:** Features high-level KPI cards, a donut chart for risk tier distribution, a time-series trend line for monthly admissions, and cross-facility comparative bar charts.
* **Page 2: Detailed Analysis:** Shifts focus to clinical root causes using a hierarchical drill-down chart (Facility -> Gender -> Comorbidity), a cross-tabulation matrix, a Key Influencers AI visual, and a Decomposition Tree.
* **Page 3: Insights and Performance Monitoring:** Tracks operational success against administrative targets using a Gauge visual (Target LOS = 4.5), highlights Month-over-Month growth, and isolates the "Bottom 3" performing facilities.
* **Global Interactivity:** Includes persistent global slicers, dynamic cross-filtering on all visuals, and custom hover tooltips for secondary data discovery.

---

# 10. Key DAX Measures
Several advanced DAX measures were authored to transition raw data into actionable KPIs, including:
* **`Total Encounters`**: `DISTINCTCOUNT('Fact_Admissions'[eid])`
* **`Average LOS`**: `AVERAGE('Fact_Admissions'[lengthofstay])`
* **`Readmission Rate %`**: Calculated using `DIVIDE` and `CALCULATE` to find the proportion of patients with prior readmission history.
* **`YTD Admissions`**: Utilized time-intelligence via `TOTALYTD`.
* **`MoM Admission Growth %`**: Calculated variance using `DATEADD` and DAX Variables (`VAR`).

---

# 11. Key Insights
1. **Geographical Bottlenecks:** Facility E is severely underperforming, with an average Length of Stay (5.16 days) that heavily exceeds the administrative target of 4.50 days.
2. **Compounding Risk:** High-risk patients routed to Facility E experience average stays of nearly 8 days, indicating a struggle to manage complex cases at this specific location.
3. **Clinical Drivers:** The AI Key Influencers visual identified that drops in patient glucose levels upon admission are statistically correlated with an increase in LOS by 1.1 days.
4. **Readmission Burden:** The network suffers from a massive 45% overall readmission rate, suggesting a systemic failure in post-discharge care protocols.

---

# 12. Challenges Encountered
* **Transforming Wide Data:** The original flat file contained 28 columns. It was challenging to logically group and separate these columns into functional 1-to-1 and 1-to-Many dimension tables without breaking referential integrity.
* **Handling Multiple Dates:** Each patient record had both an Admission Date and a Discharge Date. It required advanced modeling techniques to set up an active relationship for admissions and a secondary, inactive relationship for discharges to avoid filter conflicts.
* **DAX Context Transition:** Ensuring that the `Readmission Rate %` calculated correctly regardless of which slicer (Year, Facility, or Clinical Lab) was applied required careful manipulation of the filter context using the `CALCULATE` function.

---

# 13. Conclusion
This project successfully transitions thousands of raw clinical records into an enterprise-grade analytical tool. By establishing a rigorous Star Schema and authoring targeted DAX measures, the resulting dashboard provides healthcare administrators with immediate, actionable intelligence. Ultimately, this solution empowers the hospital network to address specific regional bottlenecks, predict patient flow based on clinical indicators, and actively optimize resource allocation to improve both patient care and operational efficiency.