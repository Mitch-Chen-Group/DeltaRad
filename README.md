Markdown
# DeltaRad
Delta radiomics for precision CBI in NSCLC. 

This repository contains a two-step analytical workflow designed to extract, concatenate, and model temporal changes in radiomic features (delta radiomics) to predict patient response and overall survival following checkpoint blockade immunotherapy (CBI).

# Repository Contents
concatenateradiomicsfeatures.ipynb: Python-based Jupyter Notebook for preprocessing and feature engineering. Calculates delta absolute, delta relative, and delta symmetric changes from baseline and follow-up radiomic extraction data between two scripts.
Deltamodel-cleanforupload.Rmd: R Markdown script encompassing the complete machine learning and survival analysis pipeline. 

# Mixed Methods for Predictor Vector Development
The R pipeline (`Deltamodel-cleanforupload.Rmd`) employs a comprehensive suite of algorithms for feature selection and classification.
# Feature Selection (Dimensionality Reduction): Includes "Pearson", "Spearman", "Kendall", "MI", "LASSO", "ENet", "Boruta", "RFE", and "PCA".
# Classification Models:Includes "GLM", "KNN", "SVM", "NaiveBayes", "RandomForest", "NNET", "PLS", "Ridge", "LASSO", and "ElasticNet".

# Step 1: Data Concatenation (Python)
Create and activate the environment for the Python preprocessing step.

# 1. Create virtual environment:

conda create -n deltarad_prep python=3.10 -y
# 2. Activate the environment:

conda activate deltarad_prep
# 3. Install dependencies:

pip install pandas numpy jupyter
# 4 Run the Notebook:
Open concatenateradiomicsfeatures.ipynb in your Jupyter environment and execute the cells sequentially to output the final formatted .csv files for modeling. Update file paths as required

# Step 2: Machine Learning & Survival Pipeline (R) 
The predictive modeling is executed in RStudio.
Environment Setup: Ensure you have R (>= 4.4.1) installed.
Dependencies: Open Deltamodel-cleanforupload.Rmd. The script begins by loading necessary packages. Ensure the following core packages are installed:
R
install.packages(c("caret", "glmnet", "randomForest", "e1071", "pROC", "survival", "survminer", "Boruta", "FactoMineR"))
Execution:
Update the file paths in the script to point to the output .csv files generated in Step 1.
Run the script sequentially. The pipeline handles data scaling, highly correlated feature removal, recursive feature elimination, 10-fold cross-validation, and Kaplan-Meier survival stratification using maximally selected rank statistics.

Raman S. Ahluwalia
Version 1.0
