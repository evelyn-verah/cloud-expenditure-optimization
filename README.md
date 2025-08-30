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

# ETL Workflow Automation
Designed and deployed automated pipelines for ingestion, transformation, and storage of logs.
Ensured repeatability and reduced manual intervention in data preparation.

# Visualization Dashboards
Built interactive dashboards for stakeholders to monitor cloud usage and costs.
Provided actionable insights into budget allocation and optimization.

# Results & Impact
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
cloud-expenditure-optimization/
│
├── data/                # Sample/synthetic datasets (no confidential data)
├── notebooks/           # Jupyter notebooks for ML experiments
├── src/                 # Source code: ETL, ML models, dashboards
│   ├── etl_pipeline.py
│   ├── ml_model.py
│   └── dashboard.py
├── docs/                # Documentation and exhibits
│   ├── Exhibit3.9_CardinalPeak_Project.pdf
│   └── architecture_diagram.png
├── results/             # Metrics, visualizations, and reports
│   ├── metrics_report.md
│   └── cost_savings_chart.png
├── requirements.txt     # Python dependencies
├── README.md            # Project overview (this file)
└── LICENSE              # License


