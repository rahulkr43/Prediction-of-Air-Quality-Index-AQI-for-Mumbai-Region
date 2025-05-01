# Mumbai Air Quality Index (AQI) Prediction

## Project Overview

This project aims to analyze and predict the Air Quality Index (AQI) in Mumbai, India, using machine learning techniques. It utilizes historical air quality data from the Central Pollution Control Board (CPCB) to build predictive models. The insights gained from this project can be valuable for understanding pollution trends, identifying hotspots, and potentially informing policy decisions.

## Dataset

The dataset was obtained from the CPCB's data repository, focusing on daily air quality measurements in Mumbai from January 1st, 2021 to July 31st, 2023. It initially included the following features:

- **Timestamp:** Date and time of measurement
- **Station:** Location of the monitoring station
- **Pollutants:** PM2.5, PM10, NO, NO2, NOx, NH3, SO2, CO, Ozone

**Feature Engineering:**

- **Calculated AQI:** Computed AQI value using the CPCB's AQI Calculator.
- **AQI Category:** Categorical representation of AQI (Good, Moderate, Poor, Unhealthy, Severe, Hazardous) based on predefined AQI ranges.

## Methodology

1. **Data Preprocessing:**
    - **Handling Missing Values:** A hierarchical imputation approach was employed to fill missing data points using quarterly, semester, 9-month, and yearly means, prioritizing seasonal patterns and data completeness.
    - **Data Normalization:** Min-Max scaling was applied to normalize pollutant features, ensuring they contribute equally to model training.
    - **Feature Engineering:** The "Calculated AQI" and "AQI Category" features were derived from raw pollutant concentrations using the CPCB's AQI calculation methodology.

2. **Data Visualization:**
    - Various visualizations were used to explore the data:
        - **Pairplots:** To examine relationships between pollutants and AQI categories. (See `pairplot.png` in the `visualizations` folder).
        - **Boxplots:** To compare pollutant distributions across stations. (See `boxplot.png` in the `visualizations` folder).
        - **Time Series Plots:** To track pollution trends over time for individual stations. (See `timeseries_plots` folder for individual station plots).
        - **Bar Plots:** To visualize average AQI levels across stations. (See `avg_aqi_barplot.png` in the `visualizations` folder).
        - **Treemaps:** To show pollutant distributions across stations. (See `mumbai_pollution_treemap.html` in the repository).
        - **Radar Charts:** To display average pollution levels for each station. (See `radar_chart.png` in the `visualizations` folder).


3. **Feature Selection & Multicollinearity:**
    - Variance Inflation Factor (VIF) was calculated to assess multicollinearity between features.
    - Features with high VIF were carefully considered to avoid potential issues in regression models.
    - SO2, NOx (ppb), and NO (µg/m³) were removed due to high multicollinearity.

4. **Model Development:**
    - Several regression models were trained and evaluated:
        - Linear Regression
        - Decision Tree Regressor
        - Random Forest Regressor
        - Support Vector Regressor (SVR)
        - K-Nearest Neighbors Regressor (KNN)
    - Model performance was assessed using metrics such as MAE, MSE, R², and Adjusted R².

## Results

**Model Performance Comparison:**

| Model                | MAE     | MSE     | R²      | Adjusted R² |
|----------------------|---------|---------|---------|-------------|
| Linear Regression    | 5.4368  | 89.8028 | 0.9761  | 0.9760      |
| Decision Tree        | 0.0356  | 0.3298  | 1.0000  | 1.0000      |
| Random Forest        | 0.6042  | 2.2241  | 0.9985  | 0.9985      |
| SVR                  | 10.6499 | 232.4619| 0.9489  | 0.9488      |
| KNN Regressor        | 3.2249  | 28.3222 | 0.9887  | 0.9887      |

**Key Insights:**

- The Decision Tree Regressor achieved the highest accuracy, closely followed by Random Forest.
- PM2.5, PM10, and NO2 were found to be the most significant predictors of AQI.
- Kurla and Mazagaon consistently recorded the highest pollution levels.
- Air quality generally worsens during winter months and improves during monsoon season.

## Usage

1. Clone this repository.
2. Install the required libraries: `pip install -r requirements.txt`
3. Run the Jupyter notebook or colab : ` AQI_Prediction.ipynb`

## Future Work

- Explore additional features and data sources, such as weather data and traffic patterns.
- Experiment with more advanced machine learning algorithms, such as deep learning models.
- Develop an interactive web application for real-time AQI prediction and visualization.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request.

## License

MIT License
