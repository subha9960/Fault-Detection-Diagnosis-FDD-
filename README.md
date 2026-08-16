Industrial Distillation Column FDD using Machine Learning

Currently working on: A physics-informed, industry-oriented machine learning framework for Fault Detection and Diagnosis (FDD) of continuous distillation columns.

📌 Project Overview

Distillation columns are complex, highly coupled chemical processes where faults can affect product quality, energy consumption, process stability, and safety.

This project aims to develop a machine-learning-based FDD system capable of:

Detecting whether the column is operating normally or under a fault.
Diagnosing the specific type of fault.
Identifying the most influential process variables behind each prediction.
Supporting future real-time industrial monitoring.

The project is currently focused on developing a realistic, physics-informed synthetic dataset that can be used to train and evaluate machine-learning models.

🎯 Objectives
1. Fault Detection

Binary classification:

Normal → 0
Fault  → 1
2. Fault Diagnosis

Multi-class classification of individual faults.

Planned fault scenarios include:

Feed-tray efficiency loss
Feed-flow disturbance
Feed-temperature disturbance
Feed-composition disturbance
Tray-efficiency degradation
Reflux-valve stiction
Reboiler-steam-valve stiction
Condenser fouling
Reboiler fouling
Cooling-water loss
Sensor faults
Other realistic process and actuator faults

The fault scenarios are inspired by the fault mechanisms discussed in recent distillation-column FDD studies.

⚙️ Process Variables

The dataset is designed around important industrial distillation variables such as:

Feed flow
Feed temperature
Feed pressure
Feed composition
Reflux flow
Reflux ratio
Column pressure
Column pressure drop
Tray temperatures
Top temperature
Bottom temperature
Reboiler duty
Condenser duty
Steam flow
Cooling-water flow
Reflux drum level
Bottom-sump level
Distillate flow
Bottoms flow
Product composition
Control-valve positions

These variables are selected based on the process variables and feature-selection results discussed in the reference studies.

🧠 Machine Learning Approach

The project will investigate several classical ML models:

                    Process Data
                         │
                         ▼
                Data Preprocessing
                         │
                         ▼
                 Feature Engineering
                         │
                         ▼
                  MRMR / Feature Selection
                         │
             ┌───────────┴───────────┐
             ▼                       ▼
      Fault Detection          Fault Diagnosis
       Normal / Fault          Specific Fault
             │                       │
             ▼                       ▼
     Gradient Boosting         Decision Tree
     Random Forest             Random Forest
     SVM                       Gradient Boosting
             │                       │
             └───────────┬───────────┘
                         ▼
                  SHAP / XAI
                         │
                         ▼
              Engineering Interpretation

A two-stage architecture using Gradient Boosting for detection and Decision Trees for diagnosis is supported by the second reference study.

📊 Dataset Design

The dataset is designed as time-series process data, rather than independent random samples.

It incorporates:

Process noise
Sensor uncertainty
Operating-load variation
Controller response
Fault onset
Fault progression
Incipient faults
Fault severity
Fault recovery
Sensor drift
Actuator disturbances
Missing measurements
Multiple fault episodes
Selected simultaneous faults

This is important because real industrial systems experience process noise, sensor uncertainty, actuator disturbances, process drift, communication delays, transient operation, and gradual fault evolution.

🔬 Explainable AI

The project will use:

SHAP
LIME
Feature importance
Permutation importance

The goal is not only to answer:

"Is there a fault?"

but also:

"Why does the model think there is a fault?"

SHAP analysis in the referenced studies identified variables such as feed flow, reflux flow/reflux ratio, reboiler duty, and feed composition as important diagnostic variables.

🏭 Industry-Level Focus

A major focus of this project is avoiding overly simple synthetic data.

The dataset is being designed so that:

Faults do not always appear as simple step changes.
Different faults can have overlapping signatures.
Normal operation contains realistic variation.
Controllers react to disturbances.
Some faults develop gradually.
Sensor faults are separated from actual process faults.
Train/test splitting is performed by fault episode to reduce temporal leakage.

This addresses limitations highlighted in recent experimental FDD work, where strong isolated perturbations can produce unrealistically well-separated fault classes.

🛠️ Technologies
Python
Pandas
NumPy
Scikit-learn
Matplotlib
Seaborn
SHAP
LIME
Machine Learning
Process Control
Chemical Engineering
📁 Planned Repository Structure
industrial-distillation-fdd-ml/
│
├── data/
│   ├── raw/
│   ├── processed/
│   └── engineered/
│
├── notebooks/
│   ├── 01_data_analysis.ipynb
│   ├── 02_eda.ipynb
│   ├── 03_feature_engineering.ipynb
│   ├── 04_fault_detection.ipynb
│   ├── 05_fault_diagnosis.ipynb
│   └── 06_shap_analysis.ipynb
│
├── src/
│   ├── data_generation.py
│   ├── preprocessing.py
│   ├── feature_engineering.py
│   ├── fault_detection.py
│   ├── fault_diagnosis.py
│   └── explainability.py
│
├── models/
│
├── reports/
│
├── requirements.txt
│
└── README.md
📈 Evaluation Metrics

The models will be evaluated using:

Accuracy
Precision
Recall
F1-score
Macro F1
Confusion Matrix
ROC-AUC where applicable
Inference time

Accuracy alone will not be used because industrial fault datasets can be imbalanced.

🚧 Current Status

Project Status: 🟡 In Progress

Currently working on:

Designing the industry-level synthetic dataset
Implementing realistic fault mechanisms
Adding dynamic process behaviour
Creating fault episodes and severity levels
Preparing the dataset for ML
Developing baseline classification models
Feature selection
SHAP-based model interpretation
📚 References
Roy, S. et al. “Enhanced Fault Detection and Diagnosis in Industrial Distillation Column Using Explainable Artificial Intelligence and Machine Learning.” International Journal of Prognostics and Health Management, 2025.
El Jattioui, M. et al. “A hybrid AI approach for fault detection and diagnosis in a continuous distillation process.” Chemical Product and Process Modeling, 2026. DOI: 10.1515/cppm-2025-0246.
👨‍💻 Project Status

Currently under development.

The objective is to develop a practical and interpretable ML-based FDD framework that can eventually support real-time monitoring and decision support for industrial distillation processes.
