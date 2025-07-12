
# 🚗 Mileage Prediction – Fuel Efficiency Forecasting for Automotive Insights

## 🔍 Overview

This project builds a predictive model to estimate vehicle fuel efficiency (Miles Per Gallon - MPG) using machine learning. It uncovers key factors affecting mileage and enables data-driven decision-making in **automotive design**, **regulatory compliance**, and **consumer advisory**.

> 📈 **Business Value:**  
> Automakers and consumers alike demand better mileage. Accurate predictions help engineers optimize vehicle design, inform buyers about performance trade-offs, and allow policymakers to evaluate environmental impact based on car specs.

---

## 📌 Business Objectives

- **Estimate fuel efficiency** from vehicle specs to guide engineering and marketing strategies.
- **Identify key mileage influencers** (like weight and horsepower) to support optimization.
- **Compare modeling techniques** (linear vs. polynomial regression) for forecasting accuracy.
- **Enable data-driven decisions** across R&D, sales, and policy domains.

---

## 🧾 Dataset

Source: [Auto MPG Dataset](https://archive.ics.uci.edu/ml/datasets/Auto+MPG) — UCI ML Repository

Features:
- **Numerical:** MPG, Cylinders, Displacement, Horsepower, Weight, Acceleration
- **Categorical:** Model Year, Origin, Car Name

---

## ⚙️ Workflow Summary

1. **Data Preparation & Cleaning**
   - Handled null values (e.g., in `horsepower`)
   - Encoded categorical values (e.g., `origin`)
   - Scaled continuous variables for uniformity

2. **Exploratory Data Analysis (EDA)**
   - Analyzed correlation between features and MPG
   - Identified negative relationships (e.g., heavier cars → lower mileage)

3. **Modeling**
   - Applied **Linear Regression** and **Polynomial Regression**
   - Evaluated using MAE, MAPE, and R²

4. **Optimization**
   - Improved prediction by capturing feature interactions using polynomial features

---

## 🔍 Key Insights

| Insight | Business Impact |
|--------|------------------|
| Weight, horsepower, and displacement **negatively correlate** with MPG | Guide lightweight material selection and performance tuning |
| Polynomial model captured **non-linear patterns** | Improves design-stage simulations for fuel economy |
| Horsepower alone doesn’t guarantee lower mileage | Useful for balancing performance and efficiency in design |

---

## 📊 Model Performance

| Metric | Linear Regression | Polynomial Regression |
|--------|-------------------|------------------------|
| Mean Absolute Error (MAE) | 3.57 MPG | **3.20 MPG** |
| Mean Absolute % Error (MAPE) | 16.5% | **14.2%** |
| R² Score | 0.646 | **0.672** |

✅ **Conclusion:** Polynomial regression yields better predictive accuracy. The model can serve as a foundation for simulating design changes and comparing fuel efficiency across prototypes.

---

## 💼 Use Cases

- **Automotive OEMs**: Predict MPG in early design phases
- **Environmental Agencies**: Estimate fleet emissions based on engine specs
- **Used Car Platforms**: Provide intelligent MPG predictions for listings
- **Consumers**: Compare vehicles based on likely fuel costs

---

## 📁 Folder Structure

```
├── data/               # Dataset & raw files
├── notebooks/          # EDA & modeling notebooks
├── models/             # Trained models (optional)
├── results/            # Visualizations and metrics
├── requirements.txt    # Dependencies
└── README.md           # This file
```

---

## 🚀 How to Use

1. **Clone the repo & install requirements:**
   ```bash
   git clone https://github.com/yourusername/mileage-prediction.git
   cd mileage-prediction
   pip install -r requirements.txt
   ```

2. **Run EDA and preprocessing**  
   Inspect dataset and clean missing values.

3. **Train model:**
   ```python
   python train_model.py
   ```

4. **Evaluate predictions:**
   Output includes MAE, MAPE, and R².

5. **Predict new data:**
   Use the `predict.py` script or notebook to test unseen vehicle specs.

---

## 📈 Visualization Example

*(Insert EDA charts, pairplots, or regression fits here)*

---

## 🧠 Future Work

- Integrate real-time vehicle specs API for dynamic predictions  
- Use ensemble methods (e.g., Random Forest, XGBoost)  
- Deploy model via Streamlit dashboard for live user interaction

---

## 🤝 Contributing

Got ideas to improve this or apply it to a real-world business use case? Contributions, issues, and forks are welcome!

---

## 📄 License

MIT License. See `LICENSE` file for details.

---

## 📦 Full Code Workflow

### 🧹 Data Preprocessing & Exploration

```python
# Preview dataset
dp.head(10)
dp.nunique()
dp.info()
dp.describe()
dp.corr()
pd.isnull(dp).sum()
dp.dropna(inplace=True)
```

### 📊 Data Visualization

```python
import seaborn as sns
sns.pairplot(x_vars=['displacement', 'horsepower', 'weight', 'acceleration', 'mpg'], y_vars=['mpg'], data=dp)
```

---

## 🧠 Model Training – Linear Regression

```python
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.preprocessing import StandardScaler

# Define feature set and target
X_scaled = StandardScaler().fit_transform(X)
y = y

# Split data
X_train, X_test, y_train, y_test = train_test_split(X_scaled, y, test_size=0.3, random_state=42)

# Train model
lr = LinearRegression()
lr.fit(X_train, y_train)
print("Intercept:", lr.intercept_)
print("Coefficients:", lr.coef_)
```

### 📈 Predict & Evaluate – Linear Model

```python
y_pred = lr.predict(X_test)

from sklearn.metrics import mean_absolute_error, mean_absolute_percentage_error, r2_score

print("MAE:", mean_absolute_error(y_test, y_pred))
print("MAPE:", mean_absolute_percentage_error(y_test, y_pred))
print("R²:", r2_score(y_test, y_pred))
```

---

## 🔁 Model Upgrade – Polynomial Regression

```python
from sklearn.preprocessing import PolynomialFeatures

poly = PolynomialFeatures(degree=2, interaction_only=True, include_bias=False)
X_train2 = poly.fit_transform(X_train)
X_test2 = poly.transform(X_test)

lr.fit(X_train2, y_train)
y_pred_poly = lr.predict(X_test2)

print("MAE (poly):", mean_absolute_error(y_test, y_pred_poly))
print("MAPE (poly):", mean_absolute_percentage_error(y_test, y_pred_poly))
print("R² (poly):", r2_score(y_test, y_pred_poly))
```

---

## 🧪 Sample Output from Linear Model Predictions

```text
[30.297, 24.728, 32.778, 31.271, 26.183, ..., 23.660, 21.511, 17.443]
```

## 🧪 Sample Output from Polynomial Model Coefficients

```text
array([-2.52, -6.00, -1.20, -1.28, 1.70, 0.08, 0.84, 0.84, -1.06, 0.39])
```

