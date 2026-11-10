# House Price Prediction – King County, USA

Final project for the **IBM Data Analysis with Python** certification.

## Objective
Predict residential house prices in King County (Seattle area) from features such as living area, building grade, bathrooms, floors and waterfront view, simulating the work of an analyst at a real estate investment trust.

## Dataset
House sales in King County, May 2014 – May 2015 (~21,600 records, 21 variables).
Source: [Kaggle – House Sales Prediction](https://www.kaggle.com/harlfoxem/housesalesprediction), slightly modified by IBM for the course (includes missing values in `bedrooms` and `bathrooms`).

## Methodology
1. **Data cleaning:** dropped identifier columns; imputed missing values in `bedrooms` (13) and `bathrooms` (10) with the column mean.
2. **Exploratory analysis:** floor distribution, price outliers by waterfront view, correlation of each feature with price.
3. **Modeling:** simple and multiple linear regression, polynomial pipeline (StandardScaler + PolynomialFeatures + LinearRegression) and Ridge regression.
4. **Evaluation:** 85/15 train-test split, R² computed on test data.

## Results

| Model | R² | Evaluated on |
|---|---|---|
| Linear regression (`long`) | 0.0005 | Training |
| Linear regression (`sqft_living`) | 0.49 | Training |
| Multiple linear regression (11 features) | 0.66 | Training |
| Polynomial pipeline (11 features) | 0.75 | Training |
| Ridge (11 features) | 0.65 | Test |
| Ridge + polynomial degree 2 | **0.70** | Test |

## Key findings
- Living area is the strongest predictor of price (correlation 0.70), followed by building grade (0.67) and above-ground area (0.61).
- Combining 11 features raises R² from 0.49 (living area alone) to 0.66.
- On unseen data, adding polynomial terms to Ridge regression improves R² from 0.65 to **0.70**.

## Limitations and next steps
- Training and test scores are mixed in the table above; a fair comparison would score every model on the test set.
- Missing values were imputed with the mean; the median or a more careful approach could be tested.
- Other models (random forest, gradient boosting) and cross-validation could be explored.

## Tools
Python · pandas · NumPy · seaborn · matplotlib · scikit-learn

## How to run
```bash
git clone <repo-url>
cd king-county-house-price-prediction
pip install -r requirements.txt
jupyter notebook House_Sales_in_King_County_USA.ipynb
```

## Author
**Laura Sofia Guerrero** – Industrial Engineer | [LinkedIn](https://www.linkedin.com/in/laura-sof%C3%ADa-guerrero-734582302/)
