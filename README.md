# CS613-Machine-Learning
Final Project: Demand Forecasting

## A comprehensive machine learning system for predicting retail product demand and optimizing inventory management across multiple stores.

## Team Members
Manjiri Khodke, Sriram Suvaidhar, Khushi Patel, Mokshad Sankhe

## Problem Statement
The objective is to ensure each retail shop receives the optimal amount of stock at the right time. This system addresses two critical challenges:

-Stockouts: Avoiding situations where shops run out of products and lose customers
-Overstock: Preventing excess inventory that leads to unnecessary costs and wastage

The goal is to maintain a healthy balance in inventory levels, enabling shops to operate smoothly, meet customer demand, and minimize costs.

## Dataset
The project uses real-world retail data from the Google Cloud Public Marketplace in BigQuery:

Sales Data (Daily transactions)
-Fields: sales_date, dealer_code, product, qty, total_price

Stock Data (Daily inventory snapshots)
-Fields: benchmark_date, ec_id, product_name, inventory_qty

Scale: Multiple stores × multiple products × daily timestamps
Preprocessing: Data merging, missing value handling, and time-series structure creation

## Problem Formulation
This is formulated as a regression problem, not classification:
Target Variable: Continuous daily sales quantity
Rationale:
Inventory decisions require exact numerical quantities
Business needs precise unit counts for ordering
Natural numeric output (0, 1, 2, ... units)

## System Architecture

Data Input (CSV) -> Data Preprocessing (Merge, Feature Engineering, Train/Test Split) -> ML Models (LightGBM, XGBoost, Random Forest, SVR) -> Ensemble Model (Weighted Average) -> Evaluation (RMSE, WMAPE, R²) -> 7-Day Demand Forecasting -> Inventory Management (Safety Stock Rules) -> Output (Forecasts + Status Flags: CRITICAL LOW, LOW STOCK, OK, OVERSTOCK)

## Machine Learning Models used

LightGBM;
Support Vector Regression (SVR);
Complementary Models: XGBoost & Random Forest;
Ensemble Strategy

## Feature Engineering Strategy

The feature engineering strategy creates predictive signals across multiple domains:

Temporal Features- Day, month, quarter; Weekend indicators

Historical Patterns- Lagged variables (1-day, 7-day); Rolling averages

Store-Product Specificity- Unique identifier encoding; Historical averages and standard deviations per combination

Inventory Context- Ending stock levels; Turnover ratios

Price Signals- Average unit cost calculations

## RESULTS

LightGBM achieved the best overall performance with the lowest RMSE and WMAPE.

## Output
The system generates two key deliverables:

Forecast Output CSV: 7-day ahead sales predictions for each store-product combination
Inventory Recommendations: Actionable alerts with status flags: CRITICAL LOW; LOW STOCK; OK; OVERSTOCK

## Conclusion
This project demonstrates how machine learning can transform inventory management from reactive to proactive. By combining four complementary models into an ensemble system, we achieve highly accurate daily sales forecasts with a WMAPE of 1.09% using LightGBM. The system provides actionable restocking suggestions that help businesses:

-Reduce missed sales from stockouts
-Minimize waste from overstock
-Optimize inventory costs
-Improve customer satisfaction

## References
H. Malik, "A beginner's approach to time-series with working example: Demand forecasting │ Time series example with Kaggle," Medium, Jun. 11, 2024. [Online]. Available: https://medium.com/@humzahmalik/a-beginners-approach-to-time-series-with-working-example-c6bff9c24928

## License
This project was completed as part of academic coursework for CS613: Machine Learning.
