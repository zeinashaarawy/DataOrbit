# DataOrbit Healthcare Provider Fraud Detection

## Project Overview
This capstone project with DataOrbit focuses on detecting fraudulent healthcare providers using Medicare data. Fraudulent activity costs the U.S. healthcare system billions annually, and our goal is to identify high-risk providers while maintaining interpretability and minimizing false positives.

## Dataset
The dataset includes:

- `Train_Beneficiarydata.csv`: Patient demographics, coverage, chronic conditions.
- `Train_Inpatientdata.csv`: Hospital admission claims.
- `Train_Outpatientdata.csv`: Outpatient visit and procedure claims.
- `Train_labels.csv`: Provider-level fraud labels (Yes/No).

**Key identifiers:** `BeneID` (patient), `Provider` (claims → fraud label).

## Project Pipeline

1. **Data Exploration** *(Zeina Shaarawy & Judy Hisham)*
   - Examined missing values, distributions, and correlations.
   - Aggregated claims to provider-level features (sum, mean, max, ratios).
   - Added derived features: total claims, claim per patient, deceased patient ratio, chronic condition ratio.
   - Visualized feature distributions and class imbalance.

2. **Modeling** *(Jana Saeed)*
   - Target variable: `potentialfraud` (1 = fraud, 0 = non-fraud)
   - Class imbalance addressed using SMOTE and class weighting.
   - Algorithms evaluated:
     - XGBoost (SMOTE & weighted)
     - Random Forest
     - Logistic Regression
     - Decision Tree
   - Hyperparameter tuning via `GridSearchCV`.
   - Best models saved in `./models`.

3. **Evaluation** *(Farah Sherif)*
   - Metrics: Precision, Recall, F1-score, ROC-AUC, PR-AUC.
   - Confusion matrices and curves generated.
   - Error analysis conducted:
     - False Positives (legitimate flagged)
     - False Negatives (fraud missed)
   - Suggestions for refinement: feature engineering, ensemble methods, threshold tuning.

## Usage

```bash
# Clone repo
git clone https://github.com/zeinashaarawy/DataOrbit.git
cd DataOrbit

# Run notebooks in order:
# 1. Exploration
notebooks/data_exploration.ipynb
# 2. Modeling
notebooks/02-modeling.ipynb
# 3. Evaluation
notebooks/03-evaluation.ipynb

```
## Folder Structure
DataOrbit/
├─ data/
│  ├─ Train_Beneficiarydata.csv
│  ├─ Train_Inpatientdata.csv
│  ├─ Train_Outpatientdata.csv
│  ├─ Train_labels.csv
│  └─ provider_final_features.csv
├─ models/
│  └─ saved models (.joblib)
├─ notebooks/
│  ├─ data_exploration.ipynb
│  ├─ 02-modeling.ipynb
│  └─ 03-evaluation.ipynb
├─ README.md


