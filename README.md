# Brake-by-Wire Failure Mode Prediction using Machine Learning Model

This project involves the simulation, preprocessing, and modeling of sensor data in a **Brake-by-Wire (BBW)** system to predict key failure indicators. Using synthetic data and a suite of regression models, we estimate values representing **Severity (S)**, **Occurrence (O)**, and **Detection (D)** — core elements of a Failure Mode and Effects Analysis (FMEA) framework.

## Project Objective

The aim is to develop a predictive model that helps identify potential failure modes in a Brake-by-Wire system using data from various sensors. This includes modeling:

* **Severity (S)**: The potential impact of a failure.
* **Occurrence (O)**: The likelihood of a failure occurring.
* **Detection (D)**: The probability of detecting the failure before it happens.

These values support proactive maintenance and risk mitigation in critical automotive systems.

## Data Generation

Synthetic sensor data was generated with Gaussian distributions for:

* `GasSensor_ppm`: Proxy for braking system gas emissions.
* `ForceSensor_N`: Applied mechanical force on brake pedal.
* `Temperature_C`: System temperature.
* `WheelSpeed_kmph`: Wheel speed during braking operation.

A total of 100 samples were simulated and stored in `sensor_data.csv`.

## Preprocessing and Feature Engineering

* Null value handling and standard scaling.
* Elbow method used for KMeans clustering to understand natural groupings in sensor patterns.
* Derived S, O, D values using domain-informed logic:

  * Severity calculated from gas and force sensor inputs.
  * Occurrence inversely related to wheel speed.
  * Detection based on deviation from average temperature.

All S, O, and D values were clipped and scaled to a 1–10 range, consistent with FMEA scoring.

## Modeling Approach

Several regression models were trained and evaluated:

* Linear Regression
* K-Nearest Neighbors
* Decision Tree Regressor
* Random Forest Regressor
* XGBoost Regressor

Each model was evaluated using:

* **Mean Squared Error (MSE)**
* **R² Score**

The models were applied independently for S, O, and D targets.

## Evaluation and Visualization

Visualizations included:

* Elbow plot for optimal cluster count.
* Bar plots comparing MSE and R² scores for each model.
* Sample prediction bar charts (top 10 samples).
* Distribution count plots for predicted categories.
* Scatter plot of `S_pred` vs `D_pred` to explore relationships.

## Results

The modeling revealed that ensemble methods like Random Forest and XGBoost provided higher accuracy across S, O, and D predictions. This indicates that nonlinear interactions exist among the sensor inputs that simple linear models could not capture effectively.

## Dataset Files

* `sensor_data.csv`: Raw simulated sensor data.
* `sensor_data_with_sod.csv`: Sensor data with engineered S, O, D values.
* `sensor_data_with_predictions.csv`: Dataset with predicted S, O, D values appended.

## Conclusion

This project demonstrates a scalable and interpretable approach to estimating potential failure risks in Brake-by-Wire systems using synthetic data and machine learning. By predicting severity, occurrence, and detection scores, automotive systems can be assessed more reliably for safety and maintenance priorities.

---
