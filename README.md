# SoilCropPredictor
# Sowing Success: How Machine Learning Helps Farmers Select the Best Crops

## Overview
This project assists farmers in choosing optimal crops by analyzing soil metrics (nitrogen, phosphorous, potassium, and pH) using machine learning. The dataset `soil_measures.csv` contains these measurements along with the corresponding best crop for each field.

## Data Description
- **Columns**:
  - `N`: Nitrogen content ratio
  - `P`: Phosphorous content ratio
  - `K`: Potassium content ratio
  - `pH`: Soil pH value
  - `crop`: Target variable (optimal crop)

## Libraries Used
- **pandas (pd)**: Data manipulation and analysis
- **numpy (np)**: Numerical operations
- **matplotlib.pyplot (plt)**: Visualization
- **sklearn.linear_model.LogisticRegression**: Multinomial logistic regression
- **sklearn.model_selection**: Train-test split and GridSearchCV for hyperparameter tuning
- **sklearn.preprocessing.StandardScaler**: Feature standardization
- **sklearn.metrics**: Accuracy and classification report metrics

## Data Processing
- **Loading**: Data is loaded from `soil_measures.csv` into a pandas DataFrame.
- **Quality Check**: No missing values found (`crops.isna().sum()`).
- **Feature-Target Split**: Features (`N`, `P`, `K`, `pH`) separated from target (`crop`).

## Feature Preprocessing and Splitting
- **Standardization**: Features scaled using `StandardScaler`.
- **Split**: 80% training, 20% testing with `random_state=42`.

## Model Development
### Logistic Regression
- **Model**: Multinomial Logistic Regression with `solver='lbfgs'`, `max_iter=2000`, `class_weight='balanced'`, `random_state=42`.
- **Tuning**: GridSearchCV with `C` values [0.01, 0.1, 1, 10]; best `C=10`.
- **Evaluation**: Achieved 68.41% accuracy; detailed classification report generated.

### Feature Importance
- **Analysis**: Mean absolute coefficients from logistic regression plotted to show feature impact (N, P, K, pH).

### Random Forest
- **Model**: Random Forest Classifier with `random_state=42`, `class_weight='balanced'`.
- **Evaluation**: Achieved 80.68% accuracy on test set.

## Visualization
- **Feature Importance Plot**: Bar chart displaying the impact of each soil metric on crop prediction.

## Conclusion
Both models provide valuable insights, with Random Forest outperforming Logistic Regression. This approach helps farmers optimize crop selection based on soil conditions.
