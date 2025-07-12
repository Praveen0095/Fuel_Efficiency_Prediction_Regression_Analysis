
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
