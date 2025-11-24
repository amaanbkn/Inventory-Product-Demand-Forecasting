# Inventory Product Demand Forecasting

This project contains a single Jupyter notebook, `forecasting.ipynb`, and a dataset `data.csv` used to explore and build simple demand-forecasting models.

Files
- `forecasting.ipynb` — notebook with the full analysis and modeling steps.
- `data.csv` — tabular sales data used by the notebook.
- `requirements.txt` — (optional) Python dependencies to install.

How to run (short)

1. Create and activate a Python environment and install dependencies:

```
python -m venv .venv
source .venv/Scripts/activate    # Windows (bash)
pip install -r requirements.txt
```

2. Open `forecasting.ipynb` and run cells in order. The notebook may save `final.png` as an output plot.

What I did in this project
- Loaded `data.csv` into a pandas DataFrame and inspected its structure.
- Filled missing values for numeric columns using column means.
- Created a composite `key` (week + store_id), dropped irrelevant columns, and aggregated rows by `key`.
- Engineered lag features (`day_1`..`day_4`) from `units_sold` and removed rows with NaNs created by shifting.
- Built the feature matrix `X` from lag columns and target `y` from `units_sold`.
- Performed a time-respecting train/test split (15% test, `shuffle=False`).
- Trained and evaluated two models: Random Forest and XGBoost (reported R² scores).
- Performed a randomized hyperparameter search (`RandomizedSearchCV`) for the Random Forest and evaluated adjusted R².
- Plotted predictions vs actuals and saved a diagnostic plot (`final.png`).

Notes
- If your dataset is smaller than some plotted index ranges (e.g., `start_idx = 500`), reduce those indices to avoid errors.
- Ensure `requirements.txt` includes at least: `numpy`, `pandas`, `seaborn`, `matplotlib`, `scipy`, `scikit-learn`, `xgboost`.

If you want, I can:
- generate a `requirements.txt` from the imports, or
- commit this README to the repository.
