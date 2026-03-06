Rohan Misra 
IPM06134
SEC - B
Set 3


Air Quality Data Analysis: Anomaly Detection, Classification, and Model Robustness
Project Overview
This notebook performs a comprehensive analysis of air quality data, focusing on detecting anomalies, categorizing pollution levels, training supervised classification models, and investigating the impact of anomalies on model robustness. The analysis is conducted on two distinct datasets: a synthetic dataset to illustrate the methodology and a real-world dataset (AQI_daily_2024_Manoharpur_Agra_UPPCB_2024.xlsx) to apply the learned techniques.

Analysis Steps
1. Data Loading and Preprocessing
Dataset 1 (Synthetic): A dummy CSV file air_quality_data.csv was created and loaded into a pandas DataFrame. The 'Timestamp' column was converted to datetime objects and set as the DataFrame index. Numerical features were scaled using StandardScaler.
Dataset 2 (Real-world): The Excel file /content/AQI_daily_2024_Manoharpur_Agra_UPPCB_2024.xlsx was loaded, reshaped from wide to long format, and a proper datetime index was created. Missing AQI values were imputed using forward and backward fill, and the 'AQI' feature was scaled.
2. Anomaly Detection (DBSCAN)
DBSCAN (Density-Based Spatial Clustering of Applications with Noise) was applied to detect anomalies in the preprocessed data. Parameters were tuned (eps, min_samples) to achieve meaningful anomaly detection.
Dataset 1: Initially, all points were labeled as anomalies with default parameters. After tuning to eps=1.5, min_samples=3, 44 out of 100 data points were identified as anomalies.
Dataset 2: 3 anomalies were detected using eps=0.5 and min_samples=5 in the scaled AQI data.
3. Pollution Category Creation
Discrete pollution categories ('Low', 'Moderate', 'High') were created based on the 33rd and 66th percentiles of an average pollution metric (for Dataset 1) or the scaled AQI (for Dataset 2). This transformed the problem into a multi-class classification task.
4. Supervised Classifier Training and Evaluation
Three classification models (Decision Tree, XGBoost, and Neural Network) were trained and evaluated using the created pollution categories as the target variable.
Standard metrics like Accuracy and F1-score were used, along with confusion matrices for visualization.
5. Anomaly Impact Investigation
Models (specifically Neural Networks) were retrained on
