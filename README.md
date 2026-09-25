# 👥 HR Analytics & Employee Management System

<p align="left">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" />
  <img src="https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white" />
  <img src="https://img.shields.io/badge/Plotly-3F4F75?style=for-the-badge&logo=plotly&logoColor=white" />
  <img src="https://img.shields.io/badge/Pipeline-ETL%20Automation-success?style=for-the-badge" />
</p>

An automated data pipeline and analytics solution built with Python to clean, impute, and consolidate disparate HR datasets, enabling automated workforce KPI reporting and interactive visualization.

---

## 📌 Problem Statement
HR and operations teams managed fragmented records across employee demographics, seniority levels, and project-based cost allocations. The data suffered from:
- Inconsistent schemas and missing financial/cost metrics.
- Slow, error-prone manual calculations in spreadsheets for bonus and promotion eligibility.
- Lack of centralized visualization into workforce distribution and department-level spend.

---

## 💡 Solution Architecture
This project implements an end-to-end Python processing pipeline that ingests raw HR exports, cleans anomalies, handles statistical data imputation, and outputs both analytical metrics and interactive Plotly visual charts.

```text
Raw Disparate CSVs / Data Exports
               │
               ▼
┌────────────────────────────────────────┐
│      Data Cleaning & Standardizing     │  <-- Pandas / NumPy
└────────────────────────────────────────┘
               │
               ▼
┌────────────────────────────────────────┐
│       Cost & Metric Imputation         │  <-- Expanding Window Averages
└────────────────────────────────────────┘
               │
               ▼
┌────────────────────────────────────────┐
│     Automated Business Logic & KPIs    │  <-- Bonus & Promotion Calculations
└────────────────────────────────────────┘
               │
               ▼
┌────────────────────────────────────────┐
│     Interactive Plotly Dashboards      │  <-- Visual Insights & Reporting
└────────────────────────────────────────┘
