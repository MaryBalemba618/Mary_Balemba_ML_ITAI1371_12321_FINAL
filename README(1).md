# MARY_BALEMBA_ML_ITAI1371_12321_FINAL

## Final Machine Learning Project
**Course:** ITAI 1371 - Classic Machine Learning  
**Project:** Airbnb Price Prediction Using Regression Models  
**Student:** Mary Balemba

## Project Objective
This project predicts Airbnb listing prices using regression models. The target variable is `price`, so the project follows the regression methodology.

## Dataset
Dataset source: https://www.kaggle.com/datasets/arianazmoudeh/airbnbopendata

The final project uses `data/Airbnb_Cleaned_Data.csv`.

## Important Data Correction
During model validation, the original results produced an unusually high R² near 0.995. A sanity check found target leakage:

- `service_fee` was almost directly related to `price` (correlation ≈ 0.998).
- `fee_to_price_ratio` was derived from the target price.

Both variables were removed from the predictor set and every model was retrained.

## Train / Validation / Test Split
- Training: 70%
- Validation: 15%
- Test: 15%
- `random_state=42`

## Models Evaluated
1. Linear Regression
2. Decision Tree Regressor
3. Random Forest Regressor
4. Gradient Boosting Regressor
5. K-Nearest Neighbors Regressor
6. Average Ensemble of the Top 3 Validation Models
7. Bayesian Ridge

## Evaluation Metrics
- Mean Absolute Error (MAE)
- Mean Squared Error (MSE)
- R² Score

## Final Results

| Model | Validation MAE | Validation MSE | Validation R² | Test MAE | Test MSE | Test R² |
|---|---:|---:|---:|---:|---:|---:|
| **Random Forest Regressor** | **224.8594** | **76,542.1309** | **0.3031** | **223.6204** | **76,230.0658** | **0.3022** |
| Average Ensemble (Top 3) | 265.0385 | 94,914.7498 | 0.1358 | 264.3793 | 94,434.8006 | 0.1356 |
| Gradient Boosting Regressor | 285.9776 | 109,639.0844 | 0.0017 | 285.4698 | 108,927.2936 | 0.0029 |
| Bayesian Ridge | 286.3809 | 109,854.4222 | -0.0003 | 285.9414 | 109,253.1262 | -0.0001 |
| Linear Regression | 286.4297 | 109,880.4135 | -0.0005 | 285.9616 | 109,286.6749 | -0.0004 |
| K-Nearest Neighbors Regressor | 301.4466 | 128,800.5200 | -0.1728 | 302.7520 | 129,703.3286 | -0.1873 |
| Decision Tree Regressor | 252.5198 | 144,582.2790 | -0.3165 | 251.5091 | 144,107.3922 | -0.3191 |

## Best Model
**Random Forest Regressor** was selected as the final model.

- Test MAE: **223.6204**
- Test MSE: **76,230.0658**
- Test R²: **0.3022**

The test R² means Random Forest explained approximately 30.22% of the variation in Airbnb listing prices. Validation and test results were very similar, showing stable generalization.

## Repository Structure
```text
MARY_BALEMBA_ML_ITAI1371_12321_FINAL/
├── data/
│   └── Airbnb_Cleaned_Data.csv
├── notebooks/
│   └── Final_Project.ipynb
├── reports/
│   ├── Final_Project_Report.pdf
│   ├── Model_Comparison_Report.pdf
│   ├── Reflection_Journal.pdf
│   ├── ModelDiscussionGuidelines_FILLED_Mary_Balemba.xlsx
│   ├── final_model_comparison.csv
│   └── random_forest_feature_importance.csv
├── presentation/
│   ├── Final_Presentation.pptx
│   └── Final_Presentation.pdf
├── images/
│   ├── final_corrected_test_mae.png
│   ├── final_corrected_test_r2.png
│   └── random_forest_feature_importance.png
├── README.md
└── requirements.txt
```

## How to Run the Notebook
1. Install Anaconda or Python.
2. Recommended compatible environment:
   - NumPy 1.26.4
   - Pandas 2.2.2
   - Scikit-learn 1.5.1
3. Open `notebooks/Final_Project.ipynb` in Jupyter Notebook.
4. Run the notebook cells from top to bottom.
5. The notebook uses the relative dataset path `../data/Airbnb_Cleaned_Data.csv`.

## Final Deliverables
- Jupyter Notebook
- Cleaned CSV dataset
- Validation/Test model comparison PDF
- Full final project report PDF
- 4-slide presentation
- Reflection Journal
- Filled Model Discussion Guidelines spreadsheet
