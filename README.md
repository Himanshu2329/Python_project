# HR Analytics & Employee Project Cost Pipeline

## Problem Statement
HR and project tracking data often sits across separate tables with missing cost values, unsplit names, and rule-based level adjustments. This notebook demonstrates an end-to-end Python ETL and visualization workflow using Pandas, NumPy, and Plotly.

## Project Scope (Sample vs. Deployed)
This repository is a **self-contained sample/capstone workflow** built to demonstrate data cleaning, business-rule transformations, and interactive visualization—not a deployed production HR system. All records are generated locally inside Task 1 from small sample tables (**5 employees** `A001`–`A005`, **5 seniority rows**, and **14 project rows**).

## Dependencies & Setup
- Python 3.8+
- `pandas`
- `numpy`
- `plotly`
- `jupyter` (or VS Code / Google Colab)

Install all required packages before running:

    pip install -r requirements.txt

*(Or directly: `pip install pandas numpy plotly jupyter`)*

## How to Run (Run Order & First-Cell CSV Generation)
1. Download or clone this repository and open `Capstone_Project.ipynb` in Jupyter Notebook or VS Code.
2. **Run all cells in order from Task 1 to Task 10** (use **Restart & Run All** to avoid duplicate transformations).
3. **First-Cell CSV Generation:** Task 1 builds `employee_dictionary`, `seniority_dictionary`, and `project_dictionary` and writes `employee.csv`, `seniority.csv`, and `project.csv` to the working directory. Tasks 2–4 read directly from these generated CSV files, so Task 1 must execute first.

## Data Cleaning, Business Rules & Imputation Assumptions
- **Missing Cost Imputation (Task 2):** Missing `Cost` entries (`Project 5` and `Project 9`) are filled sequentially using `expanding().mean()` over all preceding rows (`3,250,500.0` for `Project 5`, then `2,210,312.5` for `Project 9`, which includes the earlier imputed value). This assumes row order is meaningful and avoids look-ahead leakage; in production datasets, imputing within project category or department is recommended.
- **Name Splitting & Table Joins (Tasks 3–4):** Splits `Name` into `First Name` and `LastName`, then merges employee, seniority, and project tables on `ID` into `Final`.
- **HR Business Rules (Tasks 5–8):**
  - Adds a **5% `Bonus`** on `Finished` projects.
  - Demotes `Failed` project rows by `+1` designation level and removes rows with `Designation Level > 4`.
  - Prefixes `First Name` with `Mr.` / `Mrs.` from `Gender`, then drops `Gender`.
  - Promotes employees with `Age > 29` by `-1` designation level.

## Output Highlights
- **Total Project Cost per Employee (Task 9):** Aggregates project costs across all 5 employees (`Mrs. Nina` leads at `9,500,000.0`, followed by `Mr. John` at `5,212,312.5`, `Mr. Tom` at `5,150,000.0`, `Mrs. Amy` at `3,850,500.0`, and `Mrs. Alice` at `2,680,000.0`).
- **City Filter (Task 10):** Lists unique employees in cities containing the letter `'o'` (`London` and `Newyork`).
- **Interactive 2x2 Plotly Dashboard (Task 10):** Visualizes (1) Total Project Cost per Employee, (2) Project Status Share, (3) Employee Age vs. Designation Level, and (4) Project Count by City.

<img width="1017" height="695" alt="image" src="https://github.com/user-attachments/assets/c0624ebe-8889-4519-ae5c-b416050a2b87" />
