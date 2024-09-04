# Mileage Prediction

Welcome to the Mileage Prediction project! This repository contains code and resources for predicting the mileage (MPG - Miles Per Gallon) of vehicles using machine learning techniques.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Dataset](#dataset)
- [Installation](#installation)
- [Usage](#usage)
- [Model](#model)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

## Introduction

The Mileage Prediction project aims to build a predictive model to estimate the fuel efficiency of vehicles based on various features such as engine size, weight, horsepower, and more. This can help in understanding factors affecting vehicle mileage and making informed decisions for better fuel economy.

## Features

- Data preprocessing and cleaning
- Exploratory Data Analysis (EDA)
- Feature engineering and selection
- Model training and evaluation
- Hyperparameter tuning
- Visualization of results

## Dataset

The dataset used in this project is the [Auto MPG dataset](https://archive.ics.uci.edu/ml/datasets/Auto+MPG) from the UCI Machine Learning Repository. It contains information on various technical aspects of cars, including:
- MPG (Miles per Gallon)
- Cylinders
- Displacement
- Horsepower
- Weight
- Acceleration
- Model Year
- Origin

## Installation

To get started with this project, follow these steps:

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/mileage-prediction.git
   cd mileage-prediction
   ```

2. **Create a virtual environment:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
   ```

3. **Install the required dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

## Usage

To run the mileage prediction model, follow these steps:

1. **Preprocess the data:**
   
  ```python
   dp.head(10)
  ```
   | mpg  | cylinders | displacement | horsepower | weight | acceleration | model_year | origin | name                       |
   |------|-----------|--------------|------------|--------|--------------|------------|--------|----------------------------|
   | 18.0 | 8         | 307.0        | 130.0      | 3504   | 12.0         | 70         | usa    | chevrolet chevelle malibu  |
   | 15.0 | 8         | 350.0        | 165.0      | 3693   | 11.5         | 70         | usa    | buick skylark 320          |
   | 18.0 | 8         | 318.0        | 150.0      | 3436   | 11.0         | 70         | usa    | plymouth satellite         |
   | 16.0 | 8         | 304.0        | 150.0      | 3433   | 12.0         | 70         | usa    | amc rebel sst              |
   | 17.0 | 8         | 302.0        | 140.0      | 3449   | 10.5         | 70         | usa    | ford torino                |
   | 15.0 | 8         | 429.0        | 198.0      | 4341   | 10.0         | 70         | usa    | ford galaxie 500           |
   | 14.0 | 8         | 454.0        | 220.0      | 4354   | 9.0          | 70         | usa    | chevrolet impala           |
   | 14.0 | 8         | 440.0        | 215.0      | 4312   | 8.5          | 70         | usa    | plymouth fury iii          |
   | 14.0 | 8         | 455.0        | 225.0      | 4425   | 10.0         | 70         | usa    | pontiac catalina           |
   | 15.0 | 8         | 390.0        | 190.0      | 3850   | 8.5          | 70         | usa    | amc ambassador dpl         |

 
  ```python
   dp.nunique()
  ```
This method helps us to find the non-null values count or the number of unique values present in the datasets

   | mpg          |    129 |
   |              |        |
   | cylinders    |      5 |
   | displacement |     82 |
   | horsepower   |     93 |
   | weight       |    351 |
   | acceleration |     95 |
   | model_year   |     13 |
   | origin       |      3 |
   | name         |    305 |
   |  dtype: int64 |

  ```python
   dp.info()
  ```
  | #  | Column       |Non-Null Count |  Dtype | 
  | ---| ------       |-------------- | -----  |
  | 0  | mpg          |  398 non-null |float64 |
  | 1  | cylinders    | 398 non-null  | int64  |
  | 2  | displacement | 398 non-null  |float64 |
  | 3  | horsepower   | 392 non-null  |float64 |
  | 4  | weight       | 398 non-null  | int64  |
  | 5  | acceleration | 398 non-null  |float64 |
  | 6  | model_year   | 398 non-null  | int64  |
  | 7  | origin       | 398 non-null  | object |
  | 8  | name         | 398 non-null  | object |
 
  ```python
   dp.describe()
  ```
  |       |  mpg       |	cylinders     | displacement  | horsepower |	weight	  | acceleration |	model_year|
  |-------|------------|-----------------|---------------|------------|------------|--------------|-------------|
  | count |	398.000000 |	398.000000	  |  398.000000	| 392.000000 |	398.000000 |  398.000000  | 398.000000  |
  | mean  |	23.514573  |	5.454774	     |  193.425879	| 104.469388 |	2970.42462 |	15.568090  |	76.010050 |
  |  std	 | 7.815984	  |   1.701004	     |  104.269838	| 38.491160	 | 846.841774 |	2.757689	  |    3.697627 |
  | min	 | 9.000000	  |   3.000000	     |  68.000000	   | 46.000000	 | 1613.00000 |	8.000000	  |   70.000000 |
  | 25%	 | 17.500000  |	4.000000	     |  104.250000	| 75.000000	 | 2223.75000 |	13.825000  |	73.000000 |
  | 50%	 | 23.000000  |	4.000000	     |  148.500000	| 93.500000	 | 2803.50000 |	15.500000  |	76.000000 |
  | 75%	 | 29.000000  |	8.000000	     |  262.000000	| 126.000000 |	3608.00000 |	17.175000  |	79.000000 |
  |max	 | 46.600000  |	8.000000	     |  455.000000	| 230.000000 |	5140.00000 |	24.800000  |	82.000000 |
  
  ```python
   dp.corr()
  ```
  |    |  mpg    |  cylinders | displacement | horsepower |  weight | acceleration | model_year | origin |                      name | 
  |----|---------|------------|--------------|------------|---------|--------------|------------|--------|---------------------------|
  | 0  |  18.0   |   8        |  307.0       |   130.0    |  3504   |  12.0        | 70         |  usa   | chevrolet chevelle malibu | 
  | 1  |  15.0   |   8        |  350.0       |   165.0    |  3693   |  11.5        |  70        |  usa   |         buick skylark 320 |
  | 2  |  18.0   |   8        |  318.0       |   150.0    |  3436   |  11.0        |  70        |  usa   |        plymouth satellite |
  | 3  |  16.0   |   8        |  304.0       |   150.0    |  3433   |  12.0        |  70        |  usa   |        amc rebel sst      |
  | 4  |  17.0   |   8        |  302.0       |   140.0    |  3449   |  10.5        |  70        |  usa   |        ford torino        |

  ```python
   pd.isnull(dp).sum()
  ```
  ```python
   dp.dropna()
  ```
  ```python
   sns.pairplot( x_vars=['displacement','horsepower','weight','acceleration','mpg'],y_vars=['mpg'], data=dp)
  ```

3. **Train the model:**
   ```python
   from sklearn.model_selection import train_test_split
   from sklearn.linear_model import LinearRegression
   from sklearn.preprocessing import StandardScaler


   X_scaled = StandardScaler().fit_transform(X) 
   y = y  


   X_train, X_test, y_train, y_test = train_test_split(X_scaled, y, test_size=0.3, random_state=42)
  
   print(X_train.shape, y_train.shape)
   
   lr = LinearRegression()
   lr.fit(X_train,y_train)

   lr.intercept_
   ```
   ```text
      23.725139778636965
   ```
   ```python
     lr.coef_
   ```
   ```text
      array([-1.04061664, -2.14102322, -4.02858566, -0.14389381])
   ```
   ```python
      y_pred =lr.predict(X_test)
      y_pred
   ```
   ```text
      array([30.29700847, 24.72839529, 32.77893004, 31.27178433, 26.18332869,
       30.19790285,  9.81526818, 29.58152065, 22.56385356, 33.14051592,
       13.23874517, 24.1391044 , 12.83017376, 30.14280976, 20.38189119,
       27.02039027, 23.57590536, 29.14144886, 27.30788492, 27.65446095,
       24.90558498, 31.16937391, 31.47571282, 18.86721149, 31.78148011,
       28.87714445, 25.22555967, 21.20195807, 32.54635112, 28.1290699 ,
       13.05421087, 22.96640113, 18.90765778, 27.64588509, 12.26835702,
       31.47347388, 12.76589319, 30.02083426, 14.3995173 ,  8.22494206,
       15.94191344, 30.53780211, 31.06244592, 29.44145151, 11.87276816,
        7.01517914, 22.00319607, 30.79931703, 28.60670965, 31.69623013,
       13.98299429, 28.38757853, 28.46369689, 29.32033768, 23.65251357,
       19.54780288, 21.69478155, 23.87779746, 27.91210094, 28.70335923,
        5.28311079, 23.53912511, 24.80800038, 25.40489967, 27.08954575,
       29.33975889, 26.41480722, 31.70667484, 20.92640591,  9.99481226,
       28.59957908, 13.05021743, 25.44966623, 29.92998514, 22.13493756,
       29.93984436, 14.80654324, 18.1203581 , 29.69181725, 19.89681623,
       26.92097788, 24.39817442, 14.56889101, 32.24976789, 10.69021645,
       32.53119954, 23.66055342, 21.5117776 , 17.44313289, 19.52904422,
       25.50826822, 24.72450197, 31.45077589, 27.50750213, 20.49309346,
       19.06208574, 24.3027989 , 10.59822645, 26.90717906, 25.06442375,
        7.99895928, 18.3540233 ,  9.15452582, 33.11858724, 30.35013518,
       31.2777188 , 33.08412398, 27.23506838, 25.0255399 , 16.76395043,
       31.64205288, 31.71792394, 28.99393827, 28.21748471, 31.51023039,
       26.48553666, 17.04106949, 23.91651035])
   ```
   
4. **Evaluate the model:**
   ```python
      from sklearn.metrics import mean_absolute_error,mean_absolute_percentage_error,r2_score
      from sklearn.preprocessing import PolynomialFeatures

      mean_absolute_error(y_test,y_pred)
   ```
   ```text
     3.571062458260172
   ```
   ```python
     mean_absolute_percentage_error(y_test,y_pred)
   ```
   ```text
      0.16585849039360423
   ```
   ```python
   r2_score(y_test,y_pred)
   ```
   ```text
   0.646
     3.571062458260172
   ```
   ```python
     mean_absolute_percentage_error(y_test,y_pred)
   ```
   ```text
      0.16585849039360423
   ```
   ```python
   r2_score(y_test,y_pred)
   ```
   ```text
   0.6464709361746057
   ```
   
6. **Predict mileage for new data:**
   ```python
      poly=PolynomialFeatures(degree=2, interaction_only=True, include_bias=False)
      X_test2=poly.fit_transform(X_test)
      X_train2=poly.fit_transform(X_train)

      lr.fit(X_train2, y_train)
      lr.coef_
   ```
   ```text
      array([-2.52368317, -6.00923236, -1.20614165, -1.28760869,  1.70981614,
        0.07979862,  0.84172331,  0.84342873, -1.06549005,  0.38737357])
   ```
   ```python
        y_pred_poly=lr.predict(X_test2)
       mean_absolute_error(y_test,y_pred_poly)
   ```
   ```text
     3.2029588018848485
   ```
   ```python
     mean_absolute_percentage_error(y_test,y_pred_poly)
   ```
   ```text
      0.14172552686749482
   ```
   ```python
      r2_score(y_test,y_pred_poly)
   ```
   ```text
     0.6726357867835955
   ```
## Results

The predictive model for mileage estimation yielded the following results:

1. **Linear Regression Model**:
   - **Mean Absolute Error (MAE)**:  3.571
   - **Mean Absolute Percentage Error (MAPE)**: 0.165
   - **R-Squared (R²)**: 0.646

2. **Polynomial Regression Model**:
   - **Mean Absolute Error (MAE)**: 3.202
   - **Mean Absolute Percentage Error (MAPE)**: 0.141
   - **R-Squared (R²)**: 0.672

These results indicate that both linear and polynomial regression models provide reasonable estimates for miles per gallon (mpg) based on vehicle features such as displacement, horsepower, weight, and acceleration. The polynomial regression model showed slight improvements in performance metrics compared to the linear regression model, suggesting that it captures non-linear relationships more effectively.

## Conclusion

 The predictive model for mileage estimation effectively utilizes linear and polynomial regression techniques to predict the miles per gallon (mpg) of vehicles based on key features such as displacement, horsepower, weight, and acceleration. The model demonstrated satisfactory performance metrics, including mean absolute error, mean absolute percentage error, and R-squared values, indicating a good fit for the data. These predictions can aid in understanding vehicle efficiency trends and support decision-making in automotive design and consumer choices. Future enhancements could include incorporating additional features and exploring more advanced modeling techniques to further improve prediction accuracy.

## Contributing

Contributions are welcome! If you have any suggestions, bug reports, or improvements, feel free to open an issue or submit a pull request.


Feel free to customize this README to better fit your project specifics!
