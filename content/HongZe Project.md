Project step:
**📌 Rebar Demand Forecasting Project Plan**

### **1️⃣ Data Cleaning & Manipulation ✅ (Completed)**

- Merged multiple datasets (`df_rebar`, `df_cement`, `df_real_estate`, `df_infra`).
    
- Handled missing values (`NaN` and `NaT`).
    
- Aligned timestamps and ensured proper date formatting.
    
- Aggregated weekly rebar prices and ensured consistency.
    

### **2️⃣ Exploratory Data Analysis (EDA) & Regression Analysis 🔄 (In Progress)**

- Generated **descriptive statistics** for key variables.
    
- Created **correlation heatmaps** to identify important relationships.
    
- Conducted **multiple linear regression** to analyze variable influence on `rebar_demand`.
    
- Evaluated regression model performance using **R², MSE, and visualization**.
    

### **3️⃣ Feature Engineering ❗ (Next Step - Recommended Before Time Series Analysis)**

- **Lag Features:** Add past `rebar_demand` values as new predictors.
    
- **Rolling Window Features:** Compute moving averages for smoother trends.
    
- **Seasonality Encoding:** Apply **Sin-Cos encoding** for `month` & `week_of_month` to capture cyclic behavior.
    
- **Interaction Terms (Optional):** Explore relationships between economic indicators and demand.
    

### **4️⃣ Time Series Analysis 🔜 (Upcoming)**

- Check **stationarity** using the **ADF test**.
    
- Identify seasonal patterns and trends.
    
- Perform **time series decomposition** (Trend, Seasonal, Residuals).
    
- Visualize **historical demand trends** and detect anomalies.
    

### **5️⃣ Modeling & Forecasting 🔜**

- Test different models for predicting `rebar_demand`:
    
    - **Facebook Prophet** (trend + seasonality modeling).
        
    - **ARIMA/SARIMA** (statistical forecasting).
        
    - **XGBoost / CatBoost** (machine learning-based predictions).
        
    - **LSTM / GRU** (deep learning for long-term time series forecasting).
        
- Tune hyperparameters for optimal model performance.
    

### **6️⃣ Model Evaluation & Optimization 🔜**

- Compare models using:
    
    - **Root Mean Squared Error (RMSE)**
        
    - **Mean Absolute Percentage Error (MAPE)**
        
    - **Cross-validation scores**
        
- Select the **best model** based on accuracy & generalization.
    
- Fine-tune model parameters for better predictions.
    

### **Final Deliverables 📄**

- **Cleaned dataset** with engineered features.
    
- **Exploratory Data Analysis (EDA) report**.
    
- **Regression analysis results** (variable importance).
    
- **Time series analysis & forecasting models**.
    
- **Model evaluation & comparison report**.
    

---

**🚀 Next Steps:** ✅ Complete **EDA & Regression Analysis** 🔜 Implement **Feature Engineering** before moving to Time Series Analysis 📊 Proceed to **Modeling & Forecasting**

---

**📌 Let me know if you’d like to add any specific steps or focus on certain models!** 🎯