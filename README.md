# House Prices Analysis Project

Detailed exploratory data analysis (EDA), robust data cleaning, and advanced feature engineering to prepare the dataset for predictive modeling.

## Project Overview

Project analyzes the famous Ames Housing dataset to understand how various architectural and location-based features impact house prices. It performed statistical analysis, handled significant missing data, and engineered high-impact features.

**Dataset Source:** [Kaggle - House Prices: Advanced Regression Techniques](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques/data?select=train.csv)

---

## Dataset Description

### File descriptions

- train.csv - the training set

### Data fields

Brief version of what you'll find in the data description file.

- SalePrice - the property's sale price in dollars. This is the target variable that you're trying to predict.
- MSSubClass: The building class
- MSZoning: The general zoning classification
- LotFrontage: Linear feet of street connected to property
- LotArea: Lot size in square feet
- Street: Type of road access
- Alley: Type of alley access
- LotShape: General shape of property
- LandContour: Flatness of the property
- Utilities: Type of utilities available
- LotConfig: Lot configuration
- LandSlope: Slope of property
- Neighborhood: Physical locations within Ames city limits
- Condition1: Proximity to main road or railroad
- Condition2: Proximity to main road or railroad (if a second is present)
- BldgType: Type of dwelling
- HouseStyle: Style of dwelling
- OverallQual: Overall material and finish quality
- OverallCond: Overall condition rating
- YearBuilt: Original construction date
- YearRemodAdd: Remodel date
- CentralAir: Central air conditioning
- Electrical: Electrical system
- 1stFlrSF: First Floor square feet
- 2ndFlrSF: Second floor square feet
- HalfBath: Half baths above grade
- Bedroom: Number of bedrooms above basement level
- Kitchen: Number of kitchens
- KitchenQual: Kitchen quality
- GarageType: Garage location
- GarageArea: Size of garage in square feet
- PoolArea: Pool area in square feet
- MoSold: Month Sold
- YrSold: Year Sold
- SaleType: Type of sale
- SaleCondition: Condition of sale






## Work Description
## 1. Exploratory Data Analysis (EDA)

Before cleaning, we performed an in-depth analysis of the 1,460 properties and 81 initial features.

* **Target Variable Transformation:** We identified that `SalePrice` was highly right-skewed. To stabilize variance and meet linear model assumptions, we applied a **Log-Transformation**.
* **Correlation Analysis:** Found that `OverallQual` and `GrLivArea` have the strongest linear relationship with house prices.
* **Data Sparsity:** Identified luxury features (e.g., `PoolQC`, `MiscFeature`) with >90% missing values, signaling they are rare market occurrences.



---

## 2. Data Cleaning

We implemented a systematic cleaning pipeline to ensure data integrity:

* **Outlier Removal:** Dropped properties with more than 4,000 sq. ft. of living area that had abnormally low prices to prevent model bias.
* **Missing Value Imputation:**
    * **Numerical:** Filled with the **Mean** value of the column.
    * **Categorical:** Filled with the **Mode** (most frequent value).
* **Noise Reduction:** Dropped low-variance features like `Street` and `Utilities` that provided no predictive signal.

---

## 3. Feature Engineering

Applying the 4 core methods of feature engineering to maximize predictive power:

### 3.1 Feature Construction
We synthesized fragmented data into comprehensive metrics:
* **TotalSF:** Combined Basement, 1st Floor, and 2nd Floor areas.
* **TotalBath:** Consolidated all full and half bathrooms into one count.
* **HouseAge:** Calculated from `YrSold` and `YearBuilt`.



### 3.2 Feature Transformation 
* Applying a logarithmic transformation to the SalePrice to achieve a normal distribution, as confirmed during the EDA stage.

### 3.3 Feature Extraction
* Extracted `SaleYear` as a categorical string. This allows the model to treat specific years as distinct economic periods rather than a simple linear trend.

### 3.4 Feature Selection & Encoding
* **One-Hot Encoding:** Converted all categorical text into numerical format, resulting in a final dataset of **287 features**.
* **Redundancy Check:** Dropped original variables that were already captured by engineered features to prevent multicollinearity.

---

## 4. Final Conclusion

Through cleaning and strategic feature engineering, we successfully transitioned from a raw, "noisy" dataset to a **refined feature matrix**. The dataset is now 100% numerical, normalized, and optimized for advanced machine learning algorithms.

---

## Technologies Used
* **Python** (Pandas, NumPy)
* **Visualization:** Matplotlib, Seaborn
* **Scikit-Learn:** Data preprocessing and encoding
