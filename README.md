# IEORE-4004-Beacon-High-School

This repository contains the implementation, cleaned data, and optimization results for **Project I: Eliminating Child Care Deserts in New York State** — the Fall 2025 course project for *IEOR E4004 Optimization Models and Methods*.

---

## 🧮 Project Overview

This project aims to help the **New York State (NYS)** government eliminate *child care deserts* — areas where the number of available child care slots is insufficient relative to the population of children.

The optimization is carried out in **two parts**:

### **Part 1 — Idealistic Budgeting Model**
An optimistic estimate of the **minimum total cost** required to eliminate child care deserts:
- New facilities can be built anywhere.
- Existing facilities can be expanded by up to **120% of capacity** (or 500 slots).
- Expansion cost = baseline \$20,000 + \$200 × (current slots).
- Additional \$100 per slot for children aged 0–5 for equipment.

**Objective:**  
Minimize total cost while ensuring all ZIP codes meet state coverage thresholds:
- 0–12 coverage ≥ 50% (high-demand) or 33% (normal-demand)
- 0–5 coverage ≥ 66%

---

### **Part 2 — Realistic Expansion and Location Model**
A more practical version introducing:
- **Piecewise expansion costs** based on scale:
  - Up to 10%: \$20,000 + \$200 per slot  
  - 10–15%: \$20,000 + \$400 per slot  
  - 15–20%: \$20,000 + \$1,000 per slot
- **Distance constraint:** Minimum 0.06 miles between any two facilities.

**Objective:**  
Minimize total cost while satisfying spatial and demand constraints.

---

## 🧠 Data Sources

Raw data were provided in the course materials and cleaned before optimization.

| File | Description |
|------|--------------|
| `population.csv` | ZIP-level population of children aged 0–5, 5–12 |
| `employment_rate.csv` | Employment rate by ZIP |
| `avg_individual_income.csv` | Average income per ZIP |
| `child_care_regulated.csv` | Existing child care facilities and capacities |
| `potential_locations.csv` | Candidate sites for new facility construction |

All cleaned versions are stored in the `cleaned_data/` folder.

---

## ⚙️ Implementation

- **Language:** Python  
- **Solver:** [Gurobi Optimizer](https://www.gurobi.com/)  
- **Environment:** Jupyter Notebook  
- **Key Libraries:** `gurobipy`, `pandas`, `numpy`, `matplotlib`

