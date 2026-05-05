# Optimizing-Emergency-Hospital-EH-Facility-Location-Using-the-P-median-model
Optimizing Emergency Hospital (EH) Facility Location Using the P-median model and Gurobi applications

## Project Overview

This project develops **Optimizing-Emergency-Hospital-EH-Facility-Location-Using-the-P-median-model** for urban healthcare planning. Unlike traditional distance-minimization approaches, this model incorporates **population vulnerability (age-based risk)** to improve healthcare accessibility for high-risk groups such as the elderly and infants.

The framework combines:
- Statistical demand estimation (Poisson GLM)
- Mathematical optimization (Capacitated P-Median model)
- Geographic visualization (GIS-based mapping)

The study is applied to Stockholm-based synthetic demographic and hospital data.

---

## Methodology

### 1. Demand Modeling (Poisson GLM)
Emergency demand is modeled using a Poisson regression framework based on demographic structure:

- Age groups: 0–5, 65+
- Gender-specific population counts
- Output: risk-weighted demand coefficients

**Key insight:**
Elderly populations contribute significantly higher demand intensity compared to general population groups.

### 2. Facility Location Optimization (Capacitated P-Median)

The objective is to minimize:
- Risk-weighted travel distance between demand nodes and hospitals

**Subject to:**
- Each demand node is assigned to exactly one facility
- Hospital capacity constraints
- Fixed number of facilities (p-median formulation)

**Solver:**
- Mixed Integer Programming (MIP)
- Implemented using **Gurobi Optimizer**

## Data

All datasets are manually constructed based on aggregated demographic patterns inspired by Statistics Sweden (SCB).

### `data/zip_data.csv`
Contains:
- Zip code centroids (latitude, longitude)
- Population distribution by age and gender

### `data/ehs_candidates.csv`
Contains:
- Candidate hospital locations in Stockholm
- Facility capacities

## Key Results

- Tested on 10 Stockholm zip-code regions and 8 hospital candidates
- Optimal facility configuration: **p = 4**

### Findings:
-  10.06% reduction in system-wide risk at optimal configuration
-  33% reduction in elderly travel distance
-  Facility locations shift toward high-risk suburban zones
-  Improved spatial equity compared to distance-only models

## Key Contribution

This project demonstrates that integrating **probabilistic demand modeling** with **deterministic optimization** significantly improves:
- Healthcare accessibility
- Equity in spatial planning
- Resource allocation efficiency

## Tech Stack
- Python
- Pandas / NumPy
- Statsmodels (Poisson GLM)
- Gurobi Optimizer (MIP)
- Matplotlib / GMPlot (Visualization)
## Prerequisites
Before running the artifact, ensure you have the following installed:
- Python 3.8+
- A valid **Gurobi License** (Academic licenses are available for free to students)

## Project Structure
project/
│
├── README.md
├── notebook.ipynb
├── requirements.txt
│
├── data/
│   ├── zip_data.csv
│   └── ehs_candidates.csv
│
├── results/
│   ├── maps/
│   └── figures/

## How to Run

```bash
pip install -r requirements.txt
```
Run notebook:
```bash
jupyter notebook
```
Or execute pipeline script (if converted):
```bash
python main.py
```
## Notes

- Data is synthetic and simplified for research demonstration
- The model is intended for academic and proof-of-concept use
- Real-world deployment would require validated healthcare datasets

## Conclusion

Incorporating risk-aware demand estimation into facility location planning leads to more equitable and efficient healthcare systems, especially for vulnerable populations.
