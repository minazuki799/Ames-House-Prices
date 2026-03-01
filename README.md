<img width="1237" height="1084" alt="image_housing" src="https://github.com/user-attachments/assets/0d256193-69aa-4f3f-bf2c-cdeec64021ef" />
#Ames Housing Price Prediction (Kaggle)🏠
**Final Score:** 0.13 RMSE 

## 📌 Project Overview
This project predicts residential home prices in Ames, Iowa, using 81 explanatory variables. The goal was to build a robust regression model to minimize the **Root-Mean-Squared-Error (RMSE)** between the log of the predicted value and the log of the observed sales price.

## 🛠️ Tech Stack
* **Language:** Python
* **Libraries:** Pandas, NumPy, Scikit-learn, Seaborn, Matplotlib,swiftmltoolz(custom_made)
* **Models:** Stacking Regressor (Ensemble of [ XGBRegressor, SVR, Ridge,LassoCV(final_estimator)] )

## 📊 Key Insights from EDA
* **Target Distribution:** The house prices were right-skewed, so I applied a **Log-Transformation** to normalize the target.
* **Top Correlations:** Features like `OverallQual`, `GrLivArea`, and `GarageCars` showed the strongest positive correlation with `SalePrice`.

## ⚙️ Feature Engineering & Preprocessing
* **Missing Values:** Filled missing categorical data with "No" to indicate the abesence of the feature and numerical data with  0. A pipeline which imputes missing categorical data with the mode and missing numerical data with mean was implemented to act as a safeguard.
* **New Features:** Created `TotalSF` (Total Square Footage) by combining basement and floor areas to capture overall house size.
Created `House_age` (Age of the house) by subtracting the year the house was sold from the year it was built.
Created `HouseRemodel_age` (Age of the house after remodelling) by subtracting the year the house was sold from the year it was remodelled.
Created `TotalArea` (Total living area) by combining the ground living area in square feet with the basment area.
Created `TotalBaths` (Total no of baths) by combining the both the full and half baths above and below ground level.
Created `TotalPorshSF` (Total porsh area in square feet) by combining the all the porsh area in square feet[WoodDeckSF: Wood deck area in square feet, OpenPorchSF: Open porch area in square feet,EnclosedPorch: Enclosed porch area in square feet,3SsnPorch: Three season porch area in square feet,ScreenPorch: Screen porch area in square feet].

* **Encoding:** Used One-Hot Encoding and Ordinal_Encoding for categorical variables.

## 🚀 Model Selection
I initially trained [XGBRegressor, SVR, Ridge, LogisticRegression, RandomForestRegressor]  but consequently opted for a **Stacking Regressor** to ensemble the models. 
* **Base Models:** [XGBRegressor], [SVR], [Ridge]
* **Final Estimator:** [LassoCV]
* **Final Performance:** 0.13 RMSE on the public leaderboard.

## 📁 Repository Structure
* `notebooks/`: Contains main Jupyter Notebook.
* `data/`: Original Kaggle datasets (train.csv, test.csv,data_descrition.txt).
* `submissions/`: CSV files submitted to Kaggle.
