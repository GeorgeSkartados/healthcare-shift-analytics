# Healthcare Shift Analytics — Micro Project 01

## 1. Project Overview
This micro-project simulates a small healthcare staffing marketplace where nurses pick up shifts at different facilities. The goal is to understand how well shifts are being filled, which facilities and specialties struggle the most, how quickly shifts get accepted, and whether higher hourly pay leads to faster staffing.

The project demonstrates end-to-end analytical thinking using **SQL + Python (pandas, matplotlib) + SQLite + Jupyter Notebook**.

---

## 2. Data Model

The project uses four tables stored in a local SQLite database:

### **nurses**
- nurse_id (PK)
- name
- specialty (ICU, ER, General)
- city
- rating

### **facilities**
- facility_id (PK)
- name
- city
- type (hospital, clinic, nursing_home)

### **shifts**
- shift_id (PK)
- facility_id (FK → facilities)
- specialty
- shift_date
- start_time
- end_time
- hourly_rate
- status (open, filled, cancelled)

### **applications**
- application_id (PK)
- shift_id (FK → shifts)
- nurse_id (FK → nurses)
- applied_at
- status (applied, accepted, rejected, cancelled)

The schema and sample dataset are created directly inside the Jupyter Notebook using Python’s `sqlite3` library.

---

## 3. Business Questions

1. Which facilities consistently struggle to get their shifts filled?
2. Which nursing specialties face the toughest staffing challenges?
3. On average, how long do open shifts remain unfilled before a nurse accepts them?
4. Does offering a higher hourly rate actually lead to faster shift coverage?

These represent realistic operational questions for a healthcare shift marketplace.

---

## 4. Tech Stack

- **Language:** Python  
- **Database:** SQLite (`sqlite3`)  
- **Libraries:** pandas, matplotlib  
- **Environment:** Jupyter Notebook + Miniconda  
- **Version Control:** GitHub  

---

## 5. How to Run the Project

### **1. Create and activate a conda environment (recommended)**

```bash

2. Install dependencies

conda install jupyter pandas matplotlib -y

3. Launch the notebook

jupyter notebook

4. Run all cells from top to bottom

The notebook will:

create the SQLite database

build all tables

insert sample data

run SQL analytical queries

generate 2 charts (fill rate by facility & specialty)

6. Key Findings
Facility Performance

Three facilities share a 50% shift fill rate (Greenfield Clinic, North Dallas Hospital, Bayview Care Home).
Lone Star Medical Center is the only facility with a 100% fill rate.

Specialty Difficulty

General nursing shifts are the hardest to staff (33% fill rate), followed by ER (67%).
ICU shifts are consistently filled (100%), indicating stable availability.

Time to Fill

Shifts are typically accepted 0.1 to 1.5 days before they start, indicating tight lead times and occasional last-minute coverage.

Pay vs. Fill Speed

Higher hourly pay does not consistently lead to faster acceptance.
The highest-paid shift (70/hr) was accepted only 0.13 days before the shift, while a lower-paying shift (60/hr) was accepted 1.57 days before.
This suggests other factors — such as specialty supply or scheduling — have greater impact.

7. Visualizations (from notebook)

Bar Chart: Shift Fill Rate by Facility

Bar Chart: Shift Fill Rate by Specialty

Both charts are generated inside the notebook using matplotlib.

8. Possible Extensions

Add a realistic posted_at timestamp for true time-to-fill analysis

Expand dataset across more cities and a larger date range

Build dashboards in Power BI or Tableau

Predict fill probability using logistic regression

Add nurse reliability scoring models

Build a mini API (FastAPI) to expose analytics as endpoints

9. Project Files

healthcare_shift_analytics.ipynb — full analysis, SQL, visuals

README.md — documentation and summary


conda create -n microproj python=3.11 -y
conda activate microproj
