<<<<<<< HEAD
# Air Quality Prediction System with Feature Store

**ID2223 Scalable Machine Learning and Deep Learning - Lab 1**

A serverless machine learning system for predicting PM2.5 air quality levels using Hopsworks Feature Store, implementing a complete MLOps workflow from data ingestion to model deployment and monitoring.

## Lab Overview

This lab builds an air quality forecasting service that:
- Collects historical and real-time PM2.5 measurements and weather data
- Stores features in Hopsworks Feature Store for versioning and reproducibility
- Provides monitoring dashboards and visualizations
- Implements GitHub Actions for continuous predictions

### Completion Status

This project has successfully completed all requirements:

- Feature backfill pipeline with historical data
- Daily feature pipeline for continuous data updates
- ML training pipeline with model versioning
- Batch inference pipeline generating 7-day forecasts
- Automated deployment with GitHub Actions
- Monitoring visualizations (forecast and hindcast plots)
- Feature Store integration with Hopsworks

## Team Members
- **Zhihan Zhao** (zhihanzh@kth.se)
- **Renda Guo** (grenda@kth.se)

## Lag Features

Temporal lag features are critical for time-series forecasting as they capture historical patterns and temporal dependencies in air quality data. Our system implements three lag features to improve prediction accuracy.

### Feature Engineering

We created the following lag features to capture temporal patterns:

| Feature | Description | Purpose |
|---------|-------------|---------|
| `pm25_lag1` | PM2.5 value from 1 day ago | Captures immediate past trend |
| `pm25_lag2` | PM2.5 value from 2 days ago | Captures short-term patterns |
| `pm25_lag3` | PM2.5 value from 3 days ago | Captures medium-term patterns |

### Model Input Features

- **With lag features (7 features)**: pm25_lag1, pm25_lag2, pm25_lag3, temperature, precipitation, wind_speed, wind_direction
- **Without lag features (4 features)**: temperature, precipitation, wind_speed, wind_direction

## Results

### Model Performance Comparison

| Configuration | MSE | R² Score | Improvement |
|--------------|-----|----------|-------------|
| **Without lag features** (baseline) | 3915.33 | -2.38 | - |
| **With lag features** (our model) | 1279.91 | -0.105 | **67.3% reduction in MSE** |

The addition of lag features reduced prediction error by 67.3%, demonstrating the importance of temporal dependencies in air quality forecasting.

### Hindcast Comparison

The hindcast plots show predicted vs actual PM2.5 values over time, with the logarithmic scale highlighting air quality categories.

<table>
<tr>
<td width="50%">

**With Lag Features**

![Hindcast with Lag Features](figure/Prediction%20with%20lag%20feature.png)

Model captures temporal patterns more accurately, with predictions (purple line) closely following actual values (black line).

</td>
<td width="50%">

**Without Lag Features**

![Hindcast without Lag Features](figure/Prediction%20without%20lag%20feature.png)

Baseline model without temporal features shows larger prediction errors and fails to capture day-to-day variations.

</td>
</tr>
</table>

### Feature Importance Analysis

Feature importance scores reveal how lag features dominate prediction performance.

<table>
<tr>
<td width="50%">

**With Lag Features**

![Feature Importance with Lag](figure/Feature%20importance%20with%20lag%20feature.png)

- **pm25_lag1**: 1007 (most important)
- **pm25_lag2**: 791
- **temperature_2m_mean**: 744
- **pm25_lag3**: 710

Lag features account for ~60% of total importance.

</td>
<td width="50%">

**Without Lag Features**

![Feature Importance without Lag](figure/Feature%20importance%20without%20lag%20feature.png)

- **temperature_2m_mean**: 1590 (most important)
- **wind_speed_10m_max**: 1379
- **wind_direction_10m_dominant**: 1284

Weather features become primary predictors, but overall performance is significantly worse.

</td>
</tr>
</table>

### Key Findings

1. **Lag features are critical**: pm25_lag1 alone contributes more than any single weather feature
2. **Temporal patterns dominate**: Past PM2.5 values are stronger predictors than weather conditions
3. **Combined approach works best**: Lag features + weather data provide optimal accuracy
4. **Practical impact**: 67% MSE reduction translates to more reliable air quality forecasts
=======
# Air Quality Prediction System with Feature Store

**ID2223 Scalable Machine Learning and Deep Learning - Lab 1**

A serverless machine learning system for predicting PM2.5 air quality levels using Hopsworks Feature Store, implementing a complete MLOps workflow from data ingestion to model deployment and monitoring.

## Lab Overview

This lab builds an air quality forecasting service that:
- Collects historical and real-time PM2.5 measurements and weather data
- Stores features in Hopsworks Feature Store for versioning and reproducibility
- Provides monitoring dashboards and visualizations
- Implements GitHub Actions for continuous predictions

### Completion Status

This project has successfully completed all requirements:

- Feature backfill pipeline with historical data
- Daily feature pipeline for continuous data updates
- ML training pipeline with model versioning
- Batch inference pipeline generating 7-day forecasts
- Automated deployment with GitHub Actions
- Monitoring visualizations (forecast and hindcast plots)
- Feature Store integration with Hopsworks

## Team Members
- **Zhihan Zhao** (zhihanzh@kth.se)
- **Renda Guo** (grenda@kth.se)

## Lag Features

Temporal lag features are critical for time-series forecasting as they capture historical patterns and temporal dependencies in air quality data. Our system implements three lag features to improve prediction accuracy.

### Feature Engineering

We created the following lag features to capture temporal patterns:

| Feature | Description | Purpose |
|---------|-------------|---------|
| `pm25_lag1` | PM2.5 value from 1 day ago | Captures immediate past trend |
| `pm25_lag2` | PM2.5 value from 2 days ago | Captures short-term patterns |
| `pm25_lag3` | PM2.5 value from 3 days ago | Captures medium-term patterns |

### Model Input Features

- **With lag features (7 features)**: pm25_lag1, pm25_lag2, pm25_lag3, temperature, precipitation, wind_speed, wind_direction
- **Without lag features (4 features)**: temperature, precipitation, wind_speed, wind_direction

## Results

### Model Performance Comparison

| Configuration | MSE | R² Score | Improvement |
|--------------|-----|----------|-------------|
| **Without lag features** (baseline) | 3915.33 | -2.38 | - |
| **With lag features** (our model) | 1279.91 | -0.105 | **67.3% reduction in MSE** |

The addition of lag features reduced prediction error by 67.3%, demonstrating the importance of temporal dependencies in air quality forecasting.

### Hindcast Comparison

The hindcast plots show predicted vs actual PM2.5 values over time, with the logarithmic scale highlighting air quality categories.

<table>
<tr>
<td width="50%">

**With Lag Features**

![Hindcast with Lag Features](docs/air-quality/assets/img/hindcast_with_lag.png)

Model captures temporal patterns more accurately, with predictions (purple line) closely following actual values (black line).

</td>
<td width="50%">

**Without Lag Features**

![Hindcast without Lag Features](docs/air-quality/assets/img/hindcast_without_lag.png)

Baseline model without temporal features shows larger prediction errors and fails to capture day-to-day variations.

</td>
</tr>
</table>

### Feature Importance Analysis

Feature importance scores reveal how lag features dominate prediction performance.

<table>
<tr>
<td width="50%">

**With Lag Features**

![Feature Importance with Lag](docs/air-quality/assets/img/feature_importance_with_lag.png)

- **pm25_lag1**: 1007 (most important)
- **pm25_lag2**: 791
- **temperature_2m_mean**: 744
- **pm25_lag3**: 710

Lag features account for ~60% of total importance.

</td>
<td width="50%">

**Without Lag Features**

![Feature Importance without Lag](docs/air-quality/assets/img/feature_importance_without_lag.png)

- **temperature_2m_mean**: 1590 (most important)
- **wind_speed_10m_max**: 1379
- **wind_direction_10m_dominant**: 1284

Weather features become primary predictors, but overall performance is significantly worse.

</td>
</tr>
</table>

### Key Findings

1. **Lag features are critical**: pm25_lag1 alone contributes more than any single weather feature
2. **Temporal patterns dominate**: Past PM2.5 values are stronger predictors than weather conditions
3. **Combined approach works best**: Lag features + weather data provide optimal accuracy
4. **Practical impact**: 67% MSE reduction translates to more reliable air quality forecasts
>>>>>>> 860199821400f1f022e3772f9d172df95cab5e0f
