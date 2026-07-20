# Appliance Energy Prediction - Time-Series Forecasting

Predicts household appliance energy consumption (Wh) using multivariate time-series data (indoor/outdoor temperature, humidity, weather, and time-based features) recorded at 10-minute intervals over 137 days (Candanedo et al., 2017 dataset).

## Project Structure

```
├── data/{raw,processed}/       # Raw CSV and processed datasets
├── notebooks/
│   ├── 01_EDA.ipynb
│   ├── 02_preprocessing_feature_engineering.ipynb
│   ├── 03_baseline_models.ipynb
│   ├── 04_deep_learning_models.ipynb
│   └── 05_optimization.ipynb
├── models/                     # Saved trained models and scalers
├── reports/                    # Final report and figures
├── requirements.txt            # Python dependencies
└── README.md
```

## Setup & Dependencies

### Prerequisites
* Python 3.9+

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/gamodyarajasooriya/appliance-energy-prediction-dl-.git
   cd appliance-energy-prediction-dl-
   ```

2. Create and activate a virtual environment:
   * **Windows:**
     ```bash
     python -m venv energy_env
     energy_env\Scripts\activate
     ```
   * **macOS / Linux:**
     ```bash
     python3 -m venv energy_env
     source energy_env/bin/activate
     ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## How to Run

Run the notebooks in order from `01` to `05`. Each notebook saves its outputs (processed CSVs, trained models, figures) which are automatically loaded by the next step.

1. `notebooks/01_EDA.ipynb` — Exploratory Data Analysis & visual diagnostics
2. `notebooks/02_preprocessing_feature_engineering.ipynb` — Outlier treatment, Box-Cox transform, scaling & feature engineering
3. `notebooks/03_baseline_models.ipynb` — Baseline ML models (Linear Regression, Random Forest, XGBoost)
4. `notebooks/04_deep_learning_models.ipynb` — Deep learning models (LSTM, GRU, CNN-GRU)
5. `notebooks/05_optimization.ipynb` — Optuna hyperparameter tuning & final model evaluation

## Key Results

| Model | MAE (Wh) | RMSE | MAPE | R² |
|---|---|---|---|---|
| **XGBoost (tuned) — BEST MODEL** | **17.91** | **44.86** | **14.61%** | **0.744** |
| Random Forest | 21.47 | 52.67 | 16.50% | 0.647 |
| LSTM (tuned, MinMaxScaler) | 26.17 | 62.52 | 22.06% | 0.493 |
| Naive baseline | 26.25 | 65.75 | 21.90% | 0.450 |
| CNN-GRU | 31.49 | 73.43 | 25.24% | 0.300 |
| GRU | 32.14 | 82.20 | 25.68% | 0.123 |
| Linear Regression | 39.00 | 131.88 | 26.40% | -1.214 |

Full methodology, EDA, feature engineering, and experimental results are documented in `reports/report.pdf`.

## Note on Model Files
Trained model files exceeding GitHub's 100MB limit are excluded via `.gitignore`. Re-run notebooks 03–05 to regenerate all models locally.

## References
Candanedo, L., Feldheim, V., Deramaix, D. (2017). *Data driven prediction models of energy use of appliances in a low-energy house.* Energy and Buildings, 140, 81–97.
