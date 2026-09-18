# NOx Prediction — Process-Aware Machine Learning

A machine learning pipeline for predicting **NOx emissions** from industrial process/sensor data.

## Overview

The dataset contains around **700 sensor/process variables**. Instead of directly training one model on all features, the pipeline first 
identifies the most relevant features and then accounts for different operating regimes of the process.

### Pipeline

```text
Raw Process Data
       ↓
Feature Selection
(Random Forest)
       ↓
~700 → ~180 Features
       ↓
Soft Clustering
       ↓
3 Process Regimes
       ↓
Assignment of membership weights (a vector showing how much a point is in a particular cluster) to each sample
       ↓
Separate Regression Models
       ↓
Taking weighted average from the 3 models (for a particular point) using membership scores and prediction from 3 models
       ↓
NOx Prediction
