# India House Price Prediction Using Machine Learning

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Overview

This project aims to predict house prices in India using various machine learning regression techniques. The model is trained on a curated subset of the [India Housing Prices Dataset](https://www.kaggle.com/datasets/ankushpanday1/india-house-price-prediction/data) sourced from Kaggle. The dataset captures diverse aspects of the Indian real estate market, including property types, pricing trends, geographic locations, and available amenities, offering valuable insights across multiple Indian states.

**Key Features:**

* **Data Exploration and Preprocessing:**  Conducted exploratory data analysis (EDA) to understand data distributions, identify patterns, and handle missing values, followed by preprocessing steps to prepare the data for modeling.
* **Model Training:**  Implemented and compared multiple regression models, including Linear Regression, Decision Tree Regressor, Random Forest Regressor, and XGBoost, to identify the best-performing approach.
* **Hyperparameter Tuning:**  Applied hyperparameter optimization techniques for all models, with an emphasis on Grid Search to fine-tune the XGBoost model for improved performance.
* **Performance Evaluation:**  Evaluated model performance using standard regression metrics such as Mean Absolute Error (MAE), Mean Squared Error (MSE), Root Mean Squared Error (RMSE), and R² score, enabling a comprehensive comparison across models.

## Dataset

The model was trained using the [India Housing Prices Dataset](https://www.kaggle.com/datasets/ankushpanday1/india-house-price-prediction/data) available on Kaggle.

> The India Housing Prices Dataset contains 2.5 lakh rows and 23 columns, offering detailed insights into housing market trends across various Indian states. It includes attributes related to property types, pricing, location, and amenities, making it suitable for analysis ranging from basic descriptive statistics to advanced machine learning applications.


## Business Applications

This house price prediction model can be valuable for:

- 🏘️ **Real Estate Agents**: Quickly generate accurate property price estimates based on location and key features.
- 💰 **Property Investors**: Make informed, data-driven investment decisions across different Indian states.
- 🏦 **Banks & Lenders**: Support reliable property valuation for mortgage approvals and loan assessments.
- 🏗️ **Property Developers**: Analyze market trends and optimize pricing strategies for upcoming projects.
- 🏡 **Home Buyers**: Obtain fair price estimates to make confident purchasing decisions.
- 📊 **Market Analysts**: Examine housing market trends and pricing patterns across diverse Indian regions.

The model's high accuracy (99.6% R² score with XGBoost) makes it a reliable tool for stakeholders in the Indian real estate market to make informed decisions.

## Methodology

The project followed a structured machine learning workflow consisting of the following stages:

1. **Exploratory Data Analysis (EDA):**  An initial analysis was performed to understand the dataset structure, examine feature distributions, detect patterns, and uncover relationships between variables relevant to house price prediction.
2. **Data Preprocessing:** To prepare the data for modeling, several preprocessing steps were applied:
    * **Dropping Unnecessary Columns:** Irrelevant or redundant features that did not contribute to predictive performance were identified and removed.
    * **Ordinal Encoding:** Ordinal categorical variables were encoded into numerical values while preserving their inherent order.
    * **Data Sampling:**  Due to computational constraints, a subset of approximately 100,000 records was sampled from the original dataset to ensure efficient model training without compromising performance.
    * **One-Hot Encoding:** Remaining nominal categorical features were transformed using One-Hot Encoding via DictVectorizer, converting them into a numerical format suitable for machine learning algorithms.
3. **Model Training and Evaluation:**
    * Multiple regression models were trained and compared:
        * Linear Regression
        * Decision Tree
        * Random Forest
        * XGBoost
    * Parameter tuning for each model to optimize performance.
    * Grid Search was specifically used to fine-tune the hyperparameters of the XGBoost model.
4. **Performance Evaluation:**  Evaluation of each trained model using the following metrics:
    * **Mean Absolute Error (MAE):** Average absolute difference between the predicted and actual prices.
    * **Mean Squared Error (MSE):** Average of the squared differences between the predicted and actual prices.
    * **Root Mean Squared Error (RMSE):** Square root of the MSE, providing an error metric in the original unit of the target variable.
    * **R-squared (R2):**  A statistical measure representing the proportion of the variance in the dependent variable that is predictable from the independent variables.

## Results

The following performance metrics were achieved by the trained models:

| Model | MAE | MSE | RMSE | R² Score |
|-------|-----|-----|------|----------|
| Linear Regression | 80.95 | 10127.17 | 100.63 | 0.49 |
| Decision Tree | 7.90 | 101.53 | 10.07 | 0.994 |
| Random Forest | 50.59 | 3902.59 | 62.47 | 0.804 |
| XGBoost | 7.07 | 81.86 | 9.04 | 0.995 |

### Bar Plot Comparison of Models

![Model's Result Using Bar Plot](https://github.com/Krishnakanth834/india-home-price-ml/blob/main/img/model_comparison_bar_chart.png)

### Radar Chart Models Comparison
![Model's Result Using Radar](https://github.com/Krishnakanth834/india-home-price-ml/blob/main/img/model_comparison_radar_chart.png)

## How to Use the Model

### Prerequisites

- **Pipenv:** For managing Python environments and dependencies.
- **Docker:** For containerized deployment of the model.
- **Flask:** For app/webservice.

### Running Locally

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/Krishnakanth834/india-home-price-ml
   navigate to the cloned directory
   ```

2. **Setup Environment:**
   ```bash
   pipenv install
   pipenv shell
   ```

3. **Run the Model:**
   
   Note: You may have to run `python train.py` if the model_.bin doesn't validate on your end.
   
   ```bash
   python predict.py
   ```
   This will start a local server where you can send requests to get predictions.

4. **Testing Predictions:**

   You can use predict_test.py to test the predictions.
   
   ```bash
   python predict_test.py
   ```
   This will return a predicted house priced based on the stored data in the file.

### Docker Deployment

To deploy using Docker:

1. **Build the Docker Image:**
   ```bash
   docker build -t india-house-price-predictor .
   ```

2. **Run the Docker Container:**
   ```bash
   docker run -p 9696:9696 india-house-price-predictor
   ```

   The model will be accessible and can get the predicted price at `http://localhost:9696/predict`.

   ![Front end](https://github.com/Krishnakanth834/india-home-price-ml/blob/main/img/frontend.png)
This Dockerfile sets up a Python 3.11 environment, installs Pipenv, and copies the required files into the container. It then exposes port 9696 and sets up the Waitress server to serve the model.


### Interacting with the Model

When testing the model, you can use the following JSON structure for a student's data:


```json
{
'State': 'telangana',
 'City': 'warangal',
 'Property_Type': 0.0,
 'BHK': 1,
 'Size_in_SqFt': 2059,
 'Price_per_SqFt': 0.24,
 'Year_Built': 1995,
 'Furnished_Status': 2.0,
 'Floor_No': 0,
 'Total_Floors': 26,
 'Age_of_Property': 30,
 'Nearby_Schools': 7,
 'Nearby_Hospitals': 6,
 'Public_Transport_Accessibility': 0.0,
 'Parking_Space': 'no',
 'Security': 0.0,
 'Amenities': 'garden, pool, gym, playground, clubhouse',
 'Facing': 2.0,
 'Owner_Type': 'broker',
 'Availability_Status': 'under_construction'
}
```
Use predict_test.py to send test queries to your model:

- Use `predict_test.py` to send test queries to your model:
  ```bash
  python predict_test.py
  ```

  Modify this script to format your input data as per the model's expectations.

## Contributions

Contributions to improve the model, enhance feature sets, or optimize the deployment process are welcome. Please submit a pull request with a clear description of your changes.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgements

- Special thanks to Kaggle for providing the dataset.

---

This README provides a comprehensive guide to understanding, using, and deploying the Depression Prediction Model. For any issues or further information, feel free to open an issue in this repository.
