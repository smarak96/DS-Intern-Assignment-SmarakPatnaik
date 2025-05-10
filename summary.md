# Equipment Energy Consumption Prediction

## Approach to the Problem

The goal of this project was to predict the equipment energy consumption in a manufacturing facility. The target variable, `equipment_energy_consumption`, is influenced by various environmental factors such as temperature, humidity, lighting, and other operational conditions.

Given my past experience in data preprocessing and feature engineering, I applied several key steps to ensure the dataset was clean and suitable for modeling:

1. **Handling Humidity Values**:
   - Humidity is a crucial feature in energy consumption predictions. Since negative humidity values are physically impossible, I removed any such values from the dataset to ensure that all humidity readings were valid and meaningful.

2. **Removing Extreme Outliers**:
   - Extreme outliers in the data can distort model performance. I used statistical methods such as IQR to identify and remove extreme outliers in features like temperature, humidity, and energy consumption. By doing so, I ensured that the model wasn’t overly influenced by rare data points that could lead to overfitting.

3. **Handling Invalid String Values**:
   - Some features in the dataset contained invalid string values. I identified and removed these invalid values. For example, non-numeric values in columns meant to represent numerical features were removed or replaced with appropriate defaults to ensure smooth model training.

4. **Model Selection**:
   - I tried all models like different models like Linear Regressor, Decision Tree Regressor, Random Forest Regressor, Neural Network,but the best performance was given by XGBoost regressor.  I performed hyperparameter tuning using RandomizedSearchCV to find the best parameters (such as `max_depth`, `learning_rate`, `subsample`, etc.) to improve model performance.

### Steps Taken:
1. **Data Preprocessing**:
   - Cleaned the data by handling missing values and invalid entries.
   
2. **Feature Engineering**:
   - Selected relevant features based on domain knowledge and feature importance scores from the model.
   
3. **Model Selection**:
   - Chose XGBoost Regressor, a powerful gradient boosting model, to predict energy consumption due to its effectiveness in handling non-linear relationships and feature interactions.
   
4. **Hyperparameter Tuning**:
   - Used RandomizedSearchCV to find the best hyperparameters for the XGBoost model, optimizing parameters like `max_depth`, `learning_rate`, `subsample`, and others.

5. **Model Evaluation**:
   - Evaluated the model's performance on test data using Mean Squared Error (MSE) and R-squared (R²) metrics.

## Key Insights from the Data
Based on the feature importance plot, the following insights were gathered:

- **Important Features**:
  - The most important features for predicting equipment energy consumption are `zone1_humidity`, `zone1_temperature`, and `zone2_temperature`, with very high importance scores of over 3500.
  - Features such as `hour`, `lighting_energy`, and `is_weekend` have lower importance, suggesting they have less influence on energy consumption.

- **Low Importance Features**:
  - Features like `is_weekend` and `lighting_energy` have minimal impact on energy consumption prediction, indicating that they do not strongly correlate with the target variable.

## Model Performance Evaluation
After training the XGBoost model with the best hyperparameters, the model's performance was evaluated as follows:

- **Mean Squared Error (MSE)**: 815.14
- **R-squared (R²)**: 0.57

These results suggest that while the model explains about 57% of the variance in equipment energy consumption, there is still room for improvement in its prediction accuracy.

## Recommendations for Reducing Equipment Energy Consumption
Based on the insights from the data and the model's performance, the following recommendations can be made for reducing energy consumption:

1. **Optimize Temperature Control**:
   - The high importance of temperature-related features indicates that optimizing the temperatures in different zones could lead to significant energy savings.


2. **Lighting Optimization**:
   - Although lighting energy is not highly significant in the model, improving lighting management (e.g using energy-efficient lighting and automation) could still offer potential savings, especially during non-peak hours.

## Conclusion
The model's results provide useful insights into which features contribute the most to equipment energy consumption. By focusing on optimizing temperature and humidity control, and exploring energy-saving strategies for lighting and operational hours, energy consumption can be effectively reduced, leading to cost savings and improved energy efficiency.
