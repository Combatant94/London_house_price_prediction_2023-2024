# London-housing-price-model-2023-20240
This repository contains a Jupyter notebook that drives an end-to-end analysis of London house prices for 2023–2024.  
Key steps include:
- **Data cleaning:** Filtering to 2023–24 sales and filling in missing values thoughtfully.
- **Exploratory data analysis:** Visualizing price distributions, prices by property type (in £ millions), and the top 10 priciest postcodes.
- **Feature engineering:** Introducing `beds_per_sqm`, `baths_per_sqm`, `area_sq`, and `dist_center_km` to capture space efficiency and central-London premium.
- **Modeling:** Running OLS as a baseline, then applying RidgeCV, LassoCV, and ElasticNetCV to handle multicollinearity.
- **Evaluation:** Cross-validation and hold-out test results (Test R² ≈ 0.84, Test MAE ≈ £156 k).
Feel free to clone or fork this repo to reproduce all the charts and results.  
