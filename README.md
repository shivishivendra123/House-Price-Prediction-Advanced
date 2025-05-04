# `Conclusion`

## `Project Goal`
The goal of this project was to predict house sale prices in `Ames, Iowa` using machine learning models and to identify the best-performing model based on two key evaluation metrics: `R² score` and `Mean Absolute Error (MAE)`.

---

## `About the Dataset`
- The `Ames Housing` dataset contains `1,460` records of residential home sales between `2006` and `2010`.
- It includes over `80` features describing physical, location, and quality aspects of each property.
- The target variable used was the raw `SalePrice` (no log transformation was applied).

---

## `Feature Engineering and Preprocessing`

### `Combined and Engineered Features`
- Combined `FullBath`, `HalfBath`, and `BsmtFullBath` into a new feature: `Total_Bathrooms`.
- Calculated and combined `1stFlrSF`, `2ndFlrSF`, `GrLivArea`, and `TotalBsmtSF` into `OverallSF` to represent total usable indoor space.
- Removed high-null columns like `PoolQC`, `MiscFeature`, and `Alley`.
- Dropped columns where more than `90%` of values were the same (low variance), as they contributed little predictive value.

---

## `Models Used and Performance Summary`

| `Model`                              | `R² Score (Test)` | `MAE (Test)`       | `Notes`                                            |
|-------------------------------------|-------------------|--------------------|----------------------------------------------------|
| `Linear Regression`                 | `0.849`           | `$21,236`          | Strong baseline, simple and interpretable          |
| `Random Forest`                     | `0.822`           | `$20,212`          | Good performance, slight overfitting               |
| `XGBoost (all features)`            | `0.884`           | `$17,778`          | High-performing model using full feature set       |
| `XGBoost (top 150 RF features)`     | `0.889`           | `$17,286`          | Best overall performance with reduced feature set  |
| `Gradient Boosting`                 | `0.893`           | `$17,457`          | Highest `R²`, strong generalization                |

---

## `Final Takeaways`

- Feature combinations such as `Total_Bathrooms` and `OverallSF` improved predictive power.
- Removing `null-dominant` and `mode-dominated` features helped reduce overfitting and noise.
- The best overall result came from `XGBoost` using the `top 150 features` from `Random Forest`, achieving `R² = 0.889` and `MAE = $17,286`.
- `Gradient Boosting` gave the best `R² score = 0.893`, indicating excellent generalization.
- Even `Linear Regression` offered strong baseline performance (`R² = 0.849`).

---

## `Next Steps`

- Tune hyperparameters further using `GridSearchCV` or `Optuna`.
- Apply `SHAP` or `permutation importance` for model interpretability.
- Package and deploy the model as a `Flask`, `FastAPI`, or `Streamlit` web application.

---
