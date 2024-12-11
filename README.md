LSTM Autoencoder for Anomaly Detection in
Water Quality Data
**********************************************
Sofia Noemi Crobeddu and Sarker Modan Mohan
**********************************************
Master of Biometrics and Intelligent Vision
Universit´e Paris-Est Cr´eteil (UPEC)
December 11, 2024
**********************************************
Project Overview
This project focuses on anomaly detection in water quality data using Long
Short-Term Memory (LSTM) autoencoders. LSTM networks, a type of Re-
current Neural Network (RNN), are utilized to handle sequential time-series
data, capturing long-term dependencies. By integrating autoencoders, the
system employs unsupervised learning, compressing input data into a lower-
dimensional latent representation before reconstructing it to detect anoma-
lies.
The work was conducted as part of the Machine Learning II course
at Universit´e Paris-Est Cr´eteil (UPEC), under the supervision of Professor
Delphine Maugars.
Dataset
The dataset is sourced from the GECCO Challenge 2018: Online Anomaly
Detection for Drinking Water Quality and contains time-series data
from a German water company. Measurements span August to November
2016, recorded at one-minute intervals.
Variables
• Time: Timestamp of measurements.
• Tp: Water temperature (°C).
1
• Cl: Chlorine dioxide (mg/L).
• pH: Acidity level.
• Redox: Redox potential (mV).
• Leit: Electrical conductivity (μS/cm).
• Trueb: Turbidity (NTU).
• Cl2: Chlorine dioxide (alternative measurement, mg/L).
• Fm: Flow rate at line 1 (m³/h).
• Fm2: Flow rate at line 2 (m³/h).
• EVENT: Boolean indicator for pre-labeled anomalies (not used in the
unsupervised approach).
Note: EVENT labels are excluded for training to align with unsupervised
machine learning principles.
Exploratory Data Analysis (EDA)
Key steps in EDA include:
1. Descriptive statistics of quantitative variables (e.g., mean, standard
deviation).
2. Visualization of time series and anomalies.
3. Analysis of seasonal trends (monthly, daily, hourly patterns).
Model Architecture
The LSTM autoencoder has the following structure:
1. Encoder:
• Two LSTM layers (64 and 32 units).
• Reduces input sequences to a compact latent representation.
2. RepeatVector Layer:
2
• Reconstructs the latent vector into repeated sequences.
3. Decoder:
• Two LSTM layers (32 and 64 units).
• Reconstructs sequences to their original form.
4. Output Layer:
• Fully connected TimeDistributed(Dense) layer for each timestep.
Training
• Loss function: Mean Squared Error (MSE).
• Optimizer: Adam with a learning rate of 0.001.
• Training epochs: 50 (batch size: 64).
• Gradient clipping applied to stabilize training.
Results
Key Findings
• Threshold for anomaly detection set at the 95th percentile of recon-
struction errors.
• 1396 anomalies detected from 139,566 data points, closely matching
the 1726 EVENT-labeled anomalies in the dataset.
• High reconstruction errors indicate potential anomalies.
Visualization
Reconstruction errors were plotted against a threshold, revealing sparse anomaly
occurrences.
*********************************************************
References
1. GECCO Challenge 2018
2. MSE and MAE curves on ResearchGate
3. Towards Data Science
