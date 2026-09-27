<p align="center">
  <img src="assets/readme-banner.jpg" alt="Heart disease prediction project overview" width="100%" />
</p>

# Heart Disease Prediction

A machine-learning project that predicts whether a patient is likely to have heart disease from clinical measurements and examination data. The project is implemented as a Jupyter Notebook and compares several classification models after data cleaning, feature engineering, encoding, and scaling.

> **Medical disclaimer:** This project is for educational and research purposes only. It is not a medical device and must not be used for diagnosis, treatment, or clinical decision-making.

## Project Contents

| File | Description |
| --- | --- |
| `Heart_DP.ipynb` | Complete exploratory analysis, preprocessing, model training, and evaluation workflow. |
| `heart.csv` | Dataset containing patient records and the target label. |

## Dataset

The dataset contains **918 patient records** and the following columns:

| Column | Description |
| --- | --- |
| `Age` | Patient age in years. |
| `Sex` | Patient sex (`M` or `F`). |
| `ChestPainType` | Type of chest pain. |
| `RestingBP` | Resting blood pressure. |
| `Cholesterol` | Serum cholesterol level. |
| `FastingBS` | Fasting blood sugar indicator. |
| `RestingECG` | Resting electrocardiogram result. |
| `MaxHR` | Maximum heart rate achieved. |
| `ExerciseAngina` | Exercise-induced angina indicator. |
| `Oldpeak` | ST depression induced by exercise relative to rest. |
| `ST_Slope` | Slope of the peak exercise ST segment. |
| `HeartDisease` | Target variable: `1` indicates heart disease; `0` indicates no heart disease. |

## Workflow

The notebook follows this pipeline:

1. Loads and explores `heart.csv` using descriptive statistics and class counts.
2. Visualizes cholesterol and resting-blood-pressure distributions.
3. Removes outliers with the interquartile range (IQR) method for selected numerical features. This leaves **588 samples**.
4. Creates three additional features:
   - `Cholesterol_Age_Ratio`
   - `BP_Cholesterol_Ratio`
   - `Heart_Rate_to_Age`
5. One-hot encodes categorical variables and standardizes numerical features.
6. Splits the data into training (80%, 470 records) and testing (20%, 118 records) sets using `random_state=42`.
7. Trains and evaluates Logistic Regression, Random Forest, and XGBoost classifiers.
8. Plots model accuracy and selects Random Forest as the final model.

## Results

Recorded evaluation results from the notebook:

| Model | Test Accuracy |
| --- | ---: |
| Logistic Regression | 88.98% |
| Random Forest | **90.68%** |
| XGBoost | 88.98% |

The final Random Forest model achieved **90.68% accuracy** on the held-out test set. Results may differ if the dataset, preprocessing choices, package versions, or split configuration changes.

## Requirements

- Python 3.9 or later
- Jupyter Notebook or JupyterLab
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`
- `xgboost`

Install the dependencies with:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost jupyter
```

## How to Run

1. Clone or download this project.
2. Open a terminal in the project directory.
3. Install the required packages.
4. Start Jupyter:

   ```bash
   jupyter notebook
   ```

5. Open `Heart_DP.ipynb`.
6. Run all cells in order. Keep `heart.csv` in the same directory as the notebook.

## Possible Improvements

- Use a preprocessing pipeline fitted only on training data to prevent data leakage.
- Apply stratified splitting to preserve the target-class distribution.
- Tune model hyperparameters with cross-validation.
- Evaluate additional metrics such as ROC-AUC, precision-recall AUC, and calibration.
- Add a reproducible `requirements.txt` file and persist the trained model for inference.

## License

No license is currently specified. Add a license file before reusing or distributing this project.
