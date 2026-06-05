# Soil Feature Predictive Modeling for Crop Classification

This project identifies the single best soil feature for predicting crop types using Logistic Regression. It evaluates individual soil metrics—Nitrogen (N), Phosphorus (P), Potassium (K), and pH levels—by measuring their predictive performance using the weighted F1-score.

## Table of Contents
* [Overview](#overview)
* [Dataset](#dataset)
* [Installation & Dependencies](#installation--dependencies)
* [How It Works](#how-it-works)
* [Usage](#usage)

## Overview
The goal of this script is to determine which single soil condition is the most reliable indicator for crop selection. It trains a separate Multi-class Logistic Regression model for each individual feature, evaluates its accuracy on a test set, and identifies the feature with the highest weighted F1-score.

## Dataset
The project expects a CSV file named `soil_measures.csv` in the root directory. The dataset must contain the following columns:
* **`N`**: Nitrogen content ratio in soil
* **`P`**: Phosphorous content ratio in soil
* **`K`**: Potassium content ratio in soil
* **`ph`**: pH value of the soil
* **`crop`**: The target categorical label (e.g., wheat, rice, maize)

## Installation & Dependencies
To run this script, you need Python installed along with the required libraries. 

Install the dependencies using pip:
```bash
pip install pandas scikit-learn
```

## How It Works
1. **Data Preprocessing**: Loads the dataset and drops the target label (`crop`) to separate features (X) from the target (y).
2. **Data Splitting**: Partitions the data into an 80% training set and a 20% testing set using a fixed random seed (`random_state=42`) for reproducibility.
3. **Feature Evaluation**: Iterates through each soil feature (`N`, `P`, `K`, `ph`) to:
   * Train a Logistic Regression model on the single feature.
   * Predict the crop types on the test set.
   * Compute the weighted F1-score to account for any label imbalance.
4. **Selection**: Extracts the feature that achieved the maximum F1-score and stores it in the `best_predictive_feature` dictionary.

## Usage
Run the script in Code
```

### Expected Output
The script will output the individual performance of each feature followed by the top performer:
```text
F1-score for N: 0.09149868209906838
F1-score for P: 0.14761942909728204
F1-score for K: 0.23896974566001802
F1-score for ph: 0.04532731061152114

{'K': 0.23896974566001802}
```
