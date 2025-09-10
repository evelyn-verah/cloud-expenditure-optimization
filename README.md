# Cloud Expenditure Optimization

**AI-driven cloud cost optimization and reliability monitoring.** Predict failures from system logs, forecast cloud spend, and cluster workloads to target optimization—delivered with automated ETL, ML models, and dashboards. Impact: **~10% budgeting efficiency improvement**.

## Table of Contents
- [Overview](#overview)
- [Objectives](#objectives)
- [Architecture](#architecture)
- [Models & Methods](#models--methods)
  - [Failure Prediction (Classification)](#failure-prediction-classification)
  - [Cloud Cost Forecasting (Time Series)](#cloud-cost-forecasting-time-series)
  - [Workload Clustering (Unsupervised)](#workload-clustering-unsupervised)
- [Results](#results)
- [Visualization Dashboards](#visualization-dashboards)
- [Getting Started](#getting-started)
- [Repository Structure](#repository-structure)
- [Technologies](#technologies)
- [Project Impact](#project-impact)
- [Practical Implications](#practical-implications)
- [License](#license)
- [Acknowledgements](#-acknowledgements)

---

## Overview
This project optimizes cloud expenditure and enhances system reliability through the use of data analytics and machine learning. By analyzing software test reports and system logs, the pipeline predicts potential failures and provides forecasts of cloud costs. Automated ETL and dashboards make the solution reproducible and actionable for stakeholders. Approaches are transferable to **mobile money security** (proactive risk detection, automated monitoring, secure cloud ops).

## Objectives
- Predict potential system failures from software test data and system logs  
- Enhance reliability and customer trust through earlier detection  
- Automate ETL for scalable, repeatable insights  
- Build dashboards for real-time monitoring of **cloud costs** and **system reliability**  
- Achieve measurable spend efficiency improvements  

## Architecture
![Architecture Diagram](docs/architecture_diagram.png)

**Flow:** Test Reports & Cloud Logs → ETL (clean, normalize) → Data Lake/DB → ML (classification, forecasting, clustering) → Dashboards.

## Models & Methods

### Failure Prediction (Classification)
**Goal:** Predict **FAIL** vs **SUCCESS** using features like error codes, response time, CPU/memory usage, cost.

- **Logistic Regression** – interpretable baseline; linear decision boundary  
- **Random Forest** – ensemble of decision trees; robust to noise  
- **XGBoost** – gradient-boosted trees; strong accuracy/recall on structured data

### Cloud Cost Forecasting (Time Series)
**Goal:** Forecast spend for budgeting and capacity planning.

- **ARIMA(1,1,1)** – captures trends in cost data  
- **Rolling Mean Baseline** – simple moving average for comparison

### Workload Clustering (Unsupervised)
**Goal:** Group workloads by resource/cost profile to target optimization.

- **KMeans (k=3)** – clusters workloads by CPU, memory, response time, cost

---

## Results

### 📊 Failure Prediction Results

| Model               | Accuracy | Precision | Recall | F1   | ROC-AUC |
|---------------------|----------|-----------|--------|------|---------|
| Logistic Regression | 0.88     | 0.87      | 0.85   | 0.86 | 0.91    |
| Random Forest       | 0.92     | 0.91      | 0.90   | 0.91 | 0.95    |
| XGBoost             | 0.93     | 0.92      | 0.91   | 0.92 | 0.96    |

#### Outcome: Random Forest and XGBoost outperformed Logistic Regression, with XGBoost achieving the best precision and recall of 0.92 and 0.91, respectively, meaning it could both detect failures and avoid false alarms reliably

### 📈 Forecasting (ARIMA)

| Model        | MAE (USD) | RMSE (USD) | MAPE |
|--------------|-----------|------------|------|
| ARIMA(1,1,1) | 0.12      | 0.19       | 6.8% |
#### Outcome: ARIMA provided reliable cost forecasts with errors under 10% (MAPE), making it suitable for budget planning and resource allocation.

### 🔍 Clustering (KMeans, k=3)

| k | Silhouette Score |
|---|------------------|
| 3 | 0.62             |

#### Outcome: A 3-cluster solution achieved a Silhouette Score of 0.62, showing clear separation between workload types. This insight helps prioritize which workloads to optimize or migrate.

### Why Multiple Models?
- Using different algorithms allows for benchmarking and ensures robustness.
- Classification → keeps systems reliable by predicting failures.
- Forecasting → prevents budget overruns with proactive cost prediction.
- Clustering → improves resource management by identifying costly patterns.

---
## 📊 Dashboard Insights

The dashboards provide an overview of **cloud expenditure** and **system reliability**.  

### 1. Daily Cloud Cost Trend
- **X-axis:** Dates (day by day)  
- **Y-axis:** Total daily cloud cost (USD)  
- **Insight:** Tracks spending patterns over time.  
  - Highlights spikes or dips in daily cost.  
  - Useful for spotting anomalies or budget overruns.  
<img width="500" height="250" alt="daily_cost_2023" src="https://github.com/user-attachments/assets/40b748d8-dc28-4775-ac2a-47aa5b4f0503" />

### 2. Daily Failure Rate Trend
- **X-axis:** Dates  
- **Y-axis:** Failure rate = (Failed runs ÷ Total runs) per day  
- **Insight:** Shows how reliable the system is over time.  
  - Rising failure rates may signal deployment or system instability.  
  - Stable low rates reflect consistent performance.
<img width="500" height="250" alt="daily_failure_rate_2023" src="https://github.com/user-attachments/assets/ff0fdf87-a398-4252-89b2-8c0cca6a7002" />

### 3. Failure Rate by System
- **X-axis:** System names (AuthServer, DBServer, APIService, WebServer)  
- **Y-axis:** Failure rate (%) per system  
- **Insight:** Compares reliability across systems.  
  - Systems with higher failure rates are potential **risk hotspots**.  
  - Helps prioritize monitoring and reliability improvements.
<img width="500" height="250" alt="system_failure_rate_2023" src="https://github.com/user-attachments/assets/2391729d-c7c5-4388-ad67-67966b81c4db" />

### 4. Total Cost by System
- **X-axis:** System names  
- **Y-axis:** Total cost (USD)  
- **Insight:** Highlights which systems contribute most to overall cloud spend.  
  - Costly systems may be priority candidates for optimization.  
  - Low-cost systems may already be efficient or underutilized.  
<img width="500" height="250" alt="system_total_cost_2023" src="https://github.com/user-attachments/assets/e3dfe959-91ae-45d5-9fdb-5601ef2a34fc" />
---

Together, these dashboards help stakeholders answer:
- *Where is our money going?*  
- *Which systems are the least reliable?*  
- *Are costs or failures trending in the wrong direction?*  

## Getting Started

```bash
# 1) Clone the repo
git clone https://github.com/your-username/cloud-expenditure-optimization.git
cd cloud-expenditure-optimization

# 2) (Optional) Create and activate venv
python -m venv venv
# Mac/Linux
source venv/bin/activate
# Windows
venv\Scripts\activate

# 3) Install dependencies
pip install -r requirements.txt

# 4) Prepare data
# Place CSVs in data/, e.g.:
#   data/sample_reports_100.csv
#   data/system_log_data.csv

# 5) Run ETL
python src/etl_pipeline.py

# 6) Explore notebooks
jupyter notebook notebooks/01_etl_exploration.ipynb
```
Outputs (metrics, CSVs) will be written to `results/`.

---

## Repository Structure
```text
cloud-expenditure-optimization/
├─ data/                      # (no company confidential data)
│  ├─ sample_reports.csv
│  └─ system_log_data.csv
├─ notebooks/                 # End-to-end ML workflow
│  ├─ 01_etl_exploration.ipynb
│  ├─ 02_failure_prediction.ipynb
│  ├─ 03_cost_forecasting.ipynb
│  ├─ 04_workload_clustering.ipynb
│  ├─ 05_dashboard_prep.ipynb
│  ├─ 06_model_evaluation.ipynb
├─ src/                       # Scripts (ETL/ML/dashboard)
│  ├─ etl_pipeline.py
│  ├─ ml_model.py
│  └─ dashboard.py
├─ docs/
│  └─ architecture_diagram.png
├─ results/                   # Model metrics (tables only)
│  ├─ model_performance_summary.csv
│  ├─ forecasting_metrics.csv
│  └─ clustering_metrics.csv
├─ requirements.txt
├─ README.md
└─ LICENSE
```
---

## Technologies
- **Python**: Pandas, NumPy, scikit-learn  
- **Time Series**: statsmodels (ARIMA)  
- **Visualization**: Matplotlib  
- **Data Eng**: SQL, ETL workflows  
- **Cloud**: AWS usage & cost analytics concepts

## Project Impact
## 🌍 Impact & Applications  

### Impact  
- **Operational Reliability**: Predicted system failures early, reducing downtime and increasing trust.  
- **Resource Optimization**: Automated ETL pipelines streamlined monitoring and improved budgeting efficiency by ~10%.  
- **Decision Support**: Dashboards gave leaders real-time insights into cost spikes, failure trends, and workload clusters.  

### Practical Applications  
- **Anomaly & Failure Detection**: Models that identified cloud failures can also detect unusual transaction patterns or predict outages in financial systems.  
- **Secure Resource Allocation**: Clustering methods guide where to focus monitoring—whether on high-cost workloads or high-risk transaction segments.  
- **Resilience Forecasting**: Time-series models anticipate peak demand, ensuring systems remain reliable during critical periods (e.g., payroll cycles or holiday     transfers).  
- **Continuous Oversight**: Dashboards enable stakeholders to track performance, compliance, and emerging risks in real time.
  
## LICENSE
This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgements  
- **Cardinal Peak LLC** – for providing the opportunity and context for this work  
- **Open-source community** – especially contributors to Python libraries such as  [Pandas](https://pandas.pydata.org/), [NumPy](https://numpy.org/),  [scikit-learn](https://scikit-learn.org/), [statsmodels (https://www.statsmodels.org/), and [Matplotlib](https://matplotlib.org/)  
- **Visualization inspiration** – principles from [Tableau](https://www.tableau.com/) guided dashboard design  
- **Mentors, peers, and reviewers** – whose feedback strengthened the design and documentation  




