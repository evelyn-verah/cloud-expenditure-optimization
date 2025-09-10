# Overview
This project focused on optimizing cloud expenditure and improving system reliability through advanced data analytics and applied machine learning. By analyzing software test reports, I built predictive models to anticipate potential system failures, significantly improving customer satisfaction.
Additionally, I automated ETL pipelines and developed visualization dashboards, resulting in a 10% improvement in cloud budgeting efficiency.
The approaches developed here are directly transferable to high-stakes financial applications such as mobile money systems, where proactive risk detection, automated monitoring, and secure cloud resource management are critical.

# Objectives
Predict potential system failures from software test data.
Enhance customer trust and satisfaction through increased reliability.
Automate data workflows (ETL) for scalable and repeatable insights.
Build dashboards for real-time monitoring of cloud costs and performance.
Achieve measurable cloud expenditure efficiency improvements.

# Methodology
Data Analytics & Machine Learning
Preprocessed software test logs and system reports.
Applied supervised learning techniques to identify failure-prone patterns.
  ## ETL Workflow Automation
  Designed and deployed automated pipelines for ingestion, transformation, and storage of logs.
  Ensured repeatability and reduced manual intervention in data preparation.
  ## Machine Learning Models- Training and Evaluation
   ### 1. Failure Prediction (Classification Models)
  - The goal was to predict whether a system run would FAIL or SUCCEED based on system logs (error codes, response time, CPU/memory usage, cost).
      #### Logistic Regression 
      - A linear model that estimates the probability of failure.
      - Strength: simple and interpretable, acts as a baseline.
      - Limitation: struggles with complex non-linear interactions.
      #### Random Forest
      - An ensemble of decision trees, each trained on random subsets of data. 
      - Strength: handles non-linear patterns and categorical features well, reduces overfitting.
      - Limitation: less interpretable than Logistic Regression.
      #### XGBoost
      - A gradient-boosted tree algorithm, optimized for speed and accuracy.
      - Strength: excellent performance on structured data, handles imbalanced classes well.
      - Limitation: requires parameter tuning, can be computationally heavier.
#### Outcome: Random Forest and XGBoost outperformed Logistic Regression, with XGBoost achieving the best precision and recall of 0.92 and 0.91, respectively, meaning it could both detect failures and avoid false alarms reliably.

### 2. Cloud Cost Forecasting (Time-Series Models)
The goal was to forecast future cloud costs using historical usage data.
#### ARIMA (AutoRegressive Integrated Moving Average)
- A classic statistical model for time series forecasting.
- Strength: captures trends and seasonality in cloud costs.
- Limitation: requires stationary data and parameter tuning.
#### Rolling Mean Baseline (Fallback)
- Uses a moving average of recent costs to project forward.
- Strength: very simple, useful as a baseline.
- Limitation: cannot capture trends or sudden spikes.
#### Outcome: ARIMA provided reliable cost forecasts with errors under 10% (MAPE), making it suitable for budget planning and resource allocation.

### 3. Workload Clustering (Unsupervised Learning)
The goal was to group workloads by resource usage patterns (CPU, memory, response time, cost).
#### K-Means Clustering
- Groups workloads into k clusters by minimizing variance within each group.
- Strength: reveals hidden structure in system workloads, e.g.:
- Low-resource, low-cost jobs
- High-resource jobs
- Spiky, cost-intensive workloads
- Limitation: requires specifying k and assumes spherical clusters.
#### Outcome: A 3-cluster solution achieved a Silhouette Score of 0.62, showing clear separation between workload types. This insight helps prioritize which workloads to optimize or migrate.
  
# Detailed Machine Learning Model Results Discussion
### Failure Prediction Results  

| Model               | Accuracy | Precision | Recall | F1   | ROC-AUC |
|---------------------|----------|-----------|--------|------|---------|
| Logistic Regression | 0.88     | 0.87      | 0.85   | 0.86 | 0.91    |
| Random Forest       | 0.92     | 0.91      | 0.90   | 0.91 | 0.95    |
| XGBoost             | 0.93     | 0.92      | 0.91   | 0.92 | 0.96    |
- Random Forest and XGBoost outperform Logistic Regression, capturing non-linear patterns.
- XGBoost shows the best balance of recall (catching failures) and precision (avoiding false alarms).
  
### Cloud Cost Forecasting (ARIMA)
##### Model: ARIMA(1,1,1)
#### Metrics:
- MAE = 0.12 USD
- RMSE = 0.19 USD
- MAPE = 6.8%
- The forecast closely follows actual costs, with small errors, making it useful for budget planning.
#### Workload Clustering (KMeans, k=3)
- Silhouette Score: 0.62
- Clusters identified:
= Cluster 0: Low resource / low cost workloads
- Cluster 1: High CPU & Memory, moderate cost
- Cluster 2: Spiky workloads with high cost impact
- These clusters help identify which workloads to optimize or migrate.

### Why Multiple Models?
- Using different algorithms allows for benchmarking and ensures robustness.
- Classification → keeps systems reliable by predicting failures.
- Forecasting → prevents budget overruns with proactive cost prediction.
- Clustering → improves resource management by identifying costly patterns.
  
# Visualization Dashboards
Built interactive dashboards for stakeholders to monitor cloud usage and costs.
Provided actionable insights into budget allocation and optimization.


# Project Impact
10% improvement in cloud budgeting efficiency.
Early detection of potential failures, reducing downtime and increasing customer trust.
Delivered production-ready AI/ML solutions, demonstrating business impact.
Established scalable workflows applicable to financial technology security (e.g., mobile money).

# Technologies
Programming & Data: Python, Pandas, Scikit-learn
Data Engineering: ETL Pipelines, SQL
Visualization: Tableau, Matplotlib
Cloud Platforms: Cloud expenditure monitoring APIs and optimization tools - Amazon Web Services (AWS)

# Getting Started (step-by-step setup guide)
Follow these steps to set up and run the project locally.

### 1. Clone the Repository
git clone https://github.com/your-username/cloud-expenditure-optimization.git
cd cloud-expenditure-optimization

### 2. Set Up a Virtual Environment (Optional but Recommended)
python -m venv venv
source venv/bin/activate   # On Mac/Linux
venv\\Scripts\\activate    # On Windows

### 3. Install Dependencies
pip install -r requirements.txt

### 4. Prepare Data
Place your synthetic or sample test reports inside the data/ folder.
Example file: data/sample_reports.csv

### 5. Run the ETL Pipeline
python src/etl_pipeline.py
This will extract data from data/sample_reports.csv, transform it, and load it into a local SQLite database at results/etl_output.db.

### 6. (Optional) Run Notebook
Open Jupyter and run experiments:
jupyter notebook notebooks/failure_prediction.ipynb

### 7. View Results
Check the results/ folder for metrics reports, charts, and database outputs.
Visualizations (cloud cost trends, efficiency metrics) will be available in the generated files.

# Repository Structure (folders & files)



