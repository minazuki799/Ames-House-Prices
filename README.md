<img width="1237" height="1084" alt="image_housing" src="https://github.com/user-attachments/assets/0d256193-69aa-4f3f-bf2c-cdeec64021ef" />

# Ames Housing Price Prediction (Kaggle) 🏠

**Final Score:** 0.13 RMSE 

## 📌 Project Overview
This project predicts residential home prices in Ames, Iowa, using 81 explanatory variables. The goal was to build a robust regression model to minimize the **Root-Mean-Squared-Error (RMSE)** between the log of the predicted value and the log of the observed sales price.

## 🛠️ Tech Stack
* **Language:** Python
* **Libraries:** Pandas, NumPy, Scikit-learn, Seaborn, Matplotlib.
* **Custom Tools:** `swiftmltoolz` — A custom-built utility library containing helper functions for automated data cleaning, missing value imputation, and model evaluation.
* **Models:** Stacking Regressor (Ensemble of XGBRegressor, SVR, Ridge, and LassoCV as the final_estimator).

## 📊 Key Insights from EDA
* **Target Distribution:** House prices were right-skewed, so I applied a **Log-Transformation** to normalize the target and improve model convergence.
* **Top Correlations:** Features like `OverallQual`, `GrLivArea`, and `GarageCars` showed the strongest positive correlation with `SalePrice`.

## ⚙️ Feature Engineering & Preprocessing
* **Missing Values:** Categorical data filled with "No" (feature absence); numerical data filled with 0. A safeguard pipeline was used to impute remaining categorical data with the mode and numerical data with the mean.
* **Feature Engineering:**
    * `TotalSF`: Combined basement and floor areas.
    * `House_age` & `HouseRemodel_age`: Calculated years from sale date to capture depreciation/updates.
    * `TotalArea`: Combined ground living area and basement area.
    * `TotalBaths`: Consolidated full and half baths above and below ground.
    * `TotalPorchSF`: Aggregated area from Wood Deck, Open Porch, Enclosed, 3-Season, and Screen porches.
* **Encoding:** Applied One-Hot Encoding and Ordinal Encoding where appropriate.

## 🚀 Model Selection
I evaluated multiple models including RandomForest and Logistic Regression before selecting a **Stacking Regressor** for the final submission.
* **Base Models:** XGBRegressor, SVR, Ridge
* **Final Estimator:** LassoCV
* **Final Performance:** 0.13 RMSE on the Kaggle Public Leaderboard.

## 📁 Repository Structure
* `notebooks/`: Contains the main Jupyter Notebook with EDA and modeling.
* `data/`: Original Kaggle datasets (`train.csv`, `test.csv`, `data_description.txt`).
* `submissions/`: CSV files submitted to Kaggle.
