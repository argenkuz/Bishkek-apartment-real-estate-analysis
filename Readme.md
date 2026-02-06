#### **Table of Contents**
1. **Introduction**
2. **Data Description**
3. **Data Analysis**
4. **Visualizations**
5. **Conclusion**
6. **References**
---

### **1. Introduction**

Kyrgyzstan, a Central Asian country, has experienced significant urbanization and economic development in recent years. The real estate market in its capital, Bishkek, reflects these changes, with varying property prices influenced by factors such as location, size, and building type. This project aims to analyze a dataset of real estate listings to uncover key trends and predictors of property prices. The dataset was chosen for its relevance to understanding the dynamics of Kyrgyzstan's housing market and its potential to inform buyers, sellers, and policymakers.

---
https://www.kaggle.com/datasets/azamatkibekbaev/bishkek-house-price

### **2. Data Description**

The dataset used in this analysis contains real estate listings from Bishkek, Kyrgyzstan. It includes the following variables:

- **Price (`price`)**: The listing price of the property.
- **Area (`square`)**: The size of the property in square meters.
- **Price per square meter (`m2_price`)**: Calculated as `price / square`.
- **Number of Rooms (`rooms`)**: The number of rooms in the property.
- **District(`district`)**: The administrative district where the property is located.
- **Micro District (`micro_district`)**: 
- **Building Age (`building_age`)**: The age of the building in years.
- **Building Type (`building_type`)**: The construction material (e.g., brick, panel, monolithic).
- **Floor (`floor`)**: The floor number of the property.
- **Floors (`floors`)**: The total number of floors in the building.
- **Condition**: The condition of the property (e.g., renovated, good).
- **Floor to floors ratio (`floor_to_floors`)**: The ratio of the floor number to the total number of floors.
- **Is good floor (`is_good_floor`)**: A binary variable indicating if the property is on a desirable floor (e.g., not ground or top floor).
The dataset was sourced from publicly available real estate listings and preprocessed to handle missing values and outliers.

---
## 1. Data Collection

To build a reliable house price prediction model, it is essential to collect high-quality and relevant datasets.  
For this project, I focused on gathering data related to **real estate in Kyrgyzstan**, particularly in **Bishkek**,  
as well as supporting datasets that reflect **economic** and **demographic indicators** that may influence housing prices.

---

### 🔹 Main Dataset

- **Source**: *Kaggle / Local Open Data Portals / Real Estate Websites*  
- https://www.kaggle.com/datasets/azamatkibekbaev/bishkek-house-price
- **Filename**: `Bishkek.csv`  
- **Description**: This dataset contains listings of apartments for sale in Bishkek.  
  It includes the following features:

| Column Name       | Description                                                 |
|-------------------|-------------------------------------------------------------|
| `price`           | Total price of the apartment (in KGS)                       |
| `m2_price`        | Price per square meter                                      |
| `square`          | Total area of the apartment in square meters                |
| `rooms`           | Number of rooms                                             |
| `district`        | Administrative district of Bishkek                          |
| `micro_district`  | Sub-district or neighborhood within the city                |
| `building_type`   | Type of the building (e.g., panel, brick, monolithic)       |
| `floor`           | The floor the apartment is located on                       |
| `floors`          | Total number of floors in the building                      |
| `year`            | Year the building was constructed                           |
| `date`            | Date the listing was posted                                 |
| `source`          | Source website or platform from which the data was collected |
| `condition`       | Condition of the apartment (e.g., renovated, under repair)  |

---

This dataset provides detailed property-level information,  
which is essential for analyzing trends in the real estate market and for building accurate predictive models.

### **3. Data Analysis**

#### **Descriptive Statistics**
- **Price**: Mean = 72,511, Std. Dev. = 36,451, Min = 9,500, Max = 296,000.
- **Area**: Mean = 71.5 m², Std. Dev. = 34.2, Min = 10, Max = 347.
- **Price/m²**: Mean = 1026.6, Std. Dev. = 195.1, Min = 494, Max = 1,566.
- **Building Age**: Mean = 8.9 years, Std. Dev. = 47.02, Min = 0, Max = 75.

#### **Correlation Analysis**
- Strong correlation between:
  - **Price** and **Square** → `r = 0.90`
  - **Price** and **Price/m²** → `r = 0.27`


- Weak correlation :
  - **Price** and **Building age** → `r = -0.02`
  - **Square** and **Building age** → `r = -0.04`
  - **Square** and **price/m2** → `r = -0.13`
  - **Building age** and **Price/m²** → `r = 0.05`

- Weak correlation for floor-based features.

>  Heatmap confirms that **property size is the most important driver of price**.


---
# More effectively model which predicts price as much as possible 
###  Gradient Boosting Regressor Results
- **R² = 0.997**: The model explains **99.7%** of the variance in apartment price.
- **MSE = 3,391,739**: The average squared error between predicted and actual prices is relatively low, indicating **high prediction accuracy**.

---

### 🔍 Feature Importance
**Significant predictors:**
- `square`, `rooms`, `district`, `micro_district`, `condition`, `building_type`, `building_age`, `floor_to_floors`, `is_good_floor`.

**Non-significant predictors:**
- *None.* All selected features contribute meaningfully to predicting the price.

---

### 🧪 Hypothesis Testing
- **Building Type 1 vs 2**  
  → There is a statistically **significant difference** in prices based on building type (**p < 0.001**).

- **1st Floor vs 5th Floor**  
  → Apartment prices differ **significantly** depending on the floor (**p ≈ 0.0006**).

---
### Interpretation:

- The analysis confirms that property size is the most critical factor influencing prices.
- Other factors, such as location (district) and building type, also play significant roles.
- The weak correlation of building age with price suggests it has minimal impact on valuation.

This section should combine statistical insights with visual evidence to provide a comprehensive understanding of the dataset.

---

### Goal
- Building a machine learning model to effectively predict prices based on relatively recent data and verifying that the apartment price is appropriate.

---

###  Problem that our project helps for solving
1. **For Buyers**:  
   - Helps identify fair property prices based on size, location, and condition.  
   - Assists in comparing properties across districts and building types.  

2. **For Sellers**:  
   - Provides data-driven insights to set competitive prices.  
   - Highlights factors that increase property value, such as renovations or location.  

3. **For Policymakers**:  
   - Offers a better understanding of housing trends and affordability.  
   - Supports urban planning and housing policy development.  

4. **For Investors**:  
   - Identifies high-demand areas and profitable property types.  
   - Assists in predicting future market trends.  

By analyzing and predicting property prices, the project empowers stakeholders to make better financial and strategic decisions in Bishkek's real estate market.

---

### **4. Visualizations**

1. **Histograms**: Show the distribution of numeric features such as price and area. These highlight the skewness in price and the concentration of properties in specific size ranges.
2. **Boxplots**: Illustrate the variation in price across building types and floors, emphasizing the influence of these factors on pricing.
3. **Heatmap**: Displays the correlation matrix, confirming that property size is the most important driver of price.
4. **Scatter Plots**: Visualize the relationship between price and area, as well as price per square meter, highlighting the linear relationship between these variables.
5. **Bar Charts**: Compare average prices across different districts and building types, showcasing the impact of location and construction material on property values.
6. **Pay Charts**: Illustrate the distribution of prices across different conditions and building ages, revealing trends in property valuation based on these factors.

Each visualization provides insights into the dataset's structure and the relationships between variables, aiding in understanding the factors influencing property prices.

---

### **5. Conclusion**

This analysis highlights the key factors affecting real estate prices in Bishkek, Kyrgyzstan. Property size and condition are the most significant predictors of price, while building type and district also play important roles. The regression model developed in this project is effective for price prediction and market analysis. These findings can help stakeholders make informed decisions in the real estate market.

---

### **6. References**

1. Dataset: Publicly available real estate listings from Bishkek.
2. Tools: Python libraries such as Pandas, Matplotlib, Seaborn, and Statsmodels.
3. Additional Resources: Statistical analysis and machine learning documentation.

--- 
