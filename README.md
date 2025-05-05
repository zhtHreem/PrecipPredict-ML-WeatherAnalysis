# Weather Analysis - Rain Prediction

## Overview
This project aims to predict rainfall using weather data by employing machine learning and deep learning techniques. We leveraged feature selection methods and built predictive models to forecast precipitation based on meteorological variables such as temperature, humidity, and wind speed.

### Key Features
- **Feature Selection**: Identified the most relevant weather features for predicting rainfall.
- **Random Forest Regressor**: Used for initial feature importance analysis and regression model.
- **LSTM (Long Short-Term Memory)**: Applied deep learning to capture temporal patterns in weather data.
- **Performance Evaluation**: Compared the performance of Random Forest and LSTM models using RMSE and R².

## Training Details

### Feature Selection Methodology
To identify the most significant features for precipitation prediction, we used the following steps:

- **Random Forest Feature Importance**:
  - Random Forest Regressor was used to calculate feature importance scores.
  - The top features were ranked based on their contribution to prediction accuracy.
  - Key features: 
    - `Specific_Humidity_at_2_Meters_g_kg`
    - `Dew_Frost_Point_at_2_Meters_C`
    - `Relative_Humidity_at_2_Meters_%`
    - `Temperature_at_2_Meters_Maximum_C`
    - `Temperature_at_2_Meters_Minimum_C`

- **Dimensionality Reduction**:
  - Performed Principal Component Analysis (PCA) to reduce feature redundancy.
  - Found that 3 principal components explained 95% of the variance.

### Models Used, Hyperparameters Tuned, and Training Process

#### 1. Machine Learning Model: Random Forest Regressor
- **Base Model Implementation**:
  - Dataset split into 80% training and 20% testing.
  - Initial performance: RMSE = 0.787, R² = 0.535.

- **Hyperparameter Tuning**:
  - Grid Search CV with 5-fold cross-validation.
  - Best parameters found: `n_estimators=300`, `max_depth=None`, `min_samples_split=10`.
  - Improved performance: RMSE = 0.760, R² = 0.567.

#### 2. Deep Learning Model: LSTM Network
- **Base LSTM Architecture**:
  - Input shape: `(929, 1, 8)` (sequential time data with 8 features).
  - Initial performance: Training RMSE = 0.718, R² = 0.620; Testing RMSE = 0.652, R² = 0.686.

- **Hyperparameter Tuning**:
  - Best configuration after tuning: 3-layer LSTM with `[64, 32, 16]` units, dropout rate of 0.2, learning rate 0.0005.
  - Final performance: RMSE = 0.641, R² = 0.697.

### Key Insights
- **Model Comparison**: 
  - LSTM outperformed Random Forest by ~15.7% in RMSE and 23% in R².
  
- **Feature Importance**: 
  - Humidity-related features (e.g., `Specific_Humidity_at_2_Meters_g_kg`) were the most important predictors of precipitation.

- **Dimensionality**: 
  - Despite 7 original features, PCA reduced the complexity to just 3 components while retaining 95% of the variance.

- **Model Training Challenges**: 
  - LSTM model required careful tuning to avoid overfitting, utilizing dropout, batch normalization, and early stopping.

## Real-World Implementation

### Use Case: Agricultural Decision Support System
- **Application**: Weather forecasting system for optimizing irrigation, planting, and harvesting decisions in agriculture.
  
- **Components**:
  1. **Data Collection**: Automated weather data collection from stations.
  2. **Prediction Engine**: Implementation of the tuned LSTM model for forecasting precipitation.
  3. **User Interface**: Mobile app with visual representation of predictions for farmers.

- **Benefits**:
  - Optimized irrigation schedules based on rainfall predictions.
  - Better planning for crop planting and harvesting.
  - Improved risk management for extreme weather events.




