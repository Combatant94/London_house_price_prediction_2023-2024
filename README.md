# London‐Housing‐Price‐Model 2023–2024

This repository holds a Jupyter notebook that walks through a complete data pipeline for predicting London house prices in 2023–2024. Below is what you’ll find:

- **Data Cleaning**  
  We begin by keeping only 2023–24 sales and thoughtfully filling or dropping missing values so that every variable is ready for analysis.

- **Exploratory Data Analysis**  
  Visualizations reveal how prices distribute across London, compare by property type (in £ millions), and highlight the top 10 most expensive postcodes.

<img width="630" height="470" alt="image" src="https://github.com/user-attachments/assets/1f578841-0bbb-4540-a745-a9fa5e48d0ac" />
<img width="1189" height="590" alt="image" src="https://github.com/user-attachments/assets/bf91496b-ec6b-4465-bafd-870f61c8d317" />

<img width="859" height="545" alt="image" src="https://github.com/user-attachments/assets/40b5b842-9d38-45d0-8712-37f59ca7f2b6" />

- **Feature Engineering**  
  To give our model more insight, we create:
  - `beds_per_sqm` and `baths_per_sqm` (showing how efficiently space is used)  
  - `area_sq` (to capture diminishing returns of size)  
  - `dist_center_km` (straight‐line distance to Charing Cross, spotting the city‐centre premium)

- **Modeling**  
  We fit a straightforward OLS regression first. Then, to address multicollinearity and improve stability, we run:
  - **RidgeCV**  
  - **LassoCV**  
  - **ElasticNetCV**
<img width="1189" height="490" alt="image" src="https://github.com/user-attachments/assets/17887b66-96ee-4e30-a583-0a2b607974b5" />

- **Evaluation**  
  A 5‐fold cross‐validation shows a Test R² of around 0.84 and an average error (MAE) of about £ 156 k. We also validate these results on a held‐out test set.


  <img width="581" height="453" alt="image" src="https://github.com/user-attachments/assets/ddc67f8d-7ece-4e54-8296-289ad1e02228" />


Feel free to **clone or fork** this repository if you want to reproduce all the charts, tables, and model outputs—or to build on it for your own projects!
