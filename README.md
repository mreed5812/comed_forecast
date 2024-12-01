# Utility Forecast Project README

## **Project Overview**
This project focuses on analyzing and predicting electricity usage and costs for a residential household. The aim was to uncover the primary drivers of energy consumption and develop machine learning models to forecast future usage based on historical patterns and external factors such as weather and time-related variables. 

The project combines data exploration, feature engineering, and advanced modeling techniques to deliver actionable insights into what influences electricity usage the most.

---

## **Data Sources**
1. **Electricity Usage Data**:  
   - Downloaded directly from the user's ComEd account portal, providing daily electricity usage and associated cost information.

2. **Weather Data**:  
   - Extracted using the [Open-Meteo Historical Weather API](https://open-meteo.com/en/docs/historical-weather-api#start_date=2022-08-31&hourly=temperature_2m,relative_humidity_2m,dew_point_2m,apparent_temperature,precipitation,rain,snowfall,snow_depth,weather_code,cloud_cover&temperature_unit=fahrenheit&wind_speed_unit=mph&precipitation_unit=inch&timezone=America%2FChicago), with key metrics including:
     - Temperature (°C)
     - Dew Point (°C)
     - Humidity (%)
     - Precipitation (mm)
     - Snow Depth (cm)
     - Cloud Cover (%)

---

## **Project Workflow**
### **Step 1: Data Preparation**
- **Electricity Data Cleaning**:
  - Ensured consistency in data formatting, handled missing values, and verified integrity.
- **Weather Data Integration**:
  - Combined electricity usage with relevant weather metrics, aligning by date and time.

### **Step 2: Exploratory Data Analysis (EDA)**
- Explored correlations between electricity usage and weather/time features.
- Key insights:
  - Weak correlations with weather variables.
  - Strong short-term behavioral patterns, with recent usage emerging as the primary driver.

### **Step 3: Feature Engineering**
- Generated new features to improve model performance:
  - **Behavioral Features**: `previous_day_usage`, `previous_week_usage`.
  - **Weather Interactions**: `temp_humidity_interaction`, `cloud_daylight_interaction`.
  - **Derived Metrics**: `daylight_hours`, `daylight_hours_squared`.

### **Step 4: Machine Learning Models**
- **Gradient Boosting**:
  - Initial model for capturing non-linear relationships.
  - Achieved R² = 0.55 with optimized hyperparameters.
  - Feature importance showed `previous_day_usage` as the dominant predictor.
  
- **Random Forest**:
  - Used for comparison, achieving similar performance (R² = 0.55).
  - Validated the importance of recent usage patterns.

### **Step 5: Insights**
- Recent usage is the most reliable predictor, far outweighing weather variables.
- Behavioral consistency plays a stronger role in energy usage than environmental factors.

---

## **Next Steps**
1. **Incorporate Granular Data**:
   - Introduce device-level electricity tracking to better understand specific contributors to usage.
2. **Explore Additional Models**:
   - Experiment with deep learning or time-series-specific models like ARIMA or LSTM for more accurate forecasts.
3. **Build Real-Time Dashboards**:
   - Create interactive tools for monitoring and predicting electricity usage.

---

## **Project Requirements**
- **Python Libraries**:
  - `pandas`, `numpy`, `matplotlib`, `seaborn`
  - `scikit-learn` for modeling
  - `xgboost` for Gradient Boosting
- **Data Access**:
  - ComEd account portal for electricity usage data.
  - Open-Meteo API for historical weather data.

---

## **How to Use This Repository**
1. Clone the repository:
   ```bash
   git clone <repository_url>
   ```
2. Install the required Python libraries:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the Jupyter Notebook or script to process data and train models.
4. Replace the API and data paths with your own ComEd account data and Open-Meteo API access.

---

## **Acknowledgments**
- ComEd for providing detailed electricity usage data.
- Open-Meteo for offering a comprehensive historical weather API.

---

