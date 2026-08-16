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

