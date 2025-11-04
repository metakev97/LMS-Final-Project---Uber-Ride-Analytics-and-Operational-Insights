# Uber Ride Analytics and Operational Insights

## Project Overview

This project analyzes a dataset of Uber ride bookings in the National Capital Region of India to gain insights into booking patterns, ride completion, cancellations, and operational metrics. The goal is to identify factors influencing ride completion and provide actionable insights for improving operations.

## Dataset

The dataset used in this analysis is sourced from Kaggle: [Uber Ride Analytics Dashboard](https://www.kaggle.com/datasets/yashdevladdha/uber-ride-analytics-dashboard). It contains 148,770 ride bookings with various attributes, including:

- Date and Time of booking
- Booking ID, Customer ID
- Booking Status (Completed, Cancelled by Customer, Cancelled by Driver, etc.)
- Vehicle Type
- Pickup and Drop Locations
- Average Vehicle Arrival Time (Avg VTAT) and Average Trip Duration (Avg CTAT)
- Cancellation and Incomplete Ride details
- Booking Value and Ride Distance
- Driver and Customer Ratings
- Payment Method

## Analysis Plan

The analysis follows these steps:

1.  **Import Libraries:** Import necessary Python libraries (pandas, numpy, matplotlib, seaborn, kagglehub, os) for data manipulation, analysis, and visualization.
2.  **Data Import:** Download the dataset directly from Kaggle using `kagglehub`.
3.  **Exploratory Data Analysis (EDA):**
    *   **Data Profiling:** Examine the dataset's structure, data types, missing values, and summary statistics.
    *   **Column Renaming:** Standardize column names for better readability and usability.
    *   **Data Type Fixing:** Convert columns to appropriate data types (categorical, datetime, string, numeric).
    *   **Handling Missing Values:** Impute missing values in numerical columns (mean, zero) and categorical columns (creating an 'Unknown' or 'Unstated' category).
    *   **Removing Duplicates:** Check and remove any duplicate rows in the dataset.
    *   **Remove Outliers:** Identify and handle outliers in numerical features like `avg_vta`, `avg_cta`, `booking_value`, and `ride_distance` using the Interquartile Range (IQR) method.
4.  **Correlation Analysis:**
    *   Calculate the correlation matrix for relevant numerical features and a new 'is_completed' column (indicating if a ride was completed).
    *   Visualize the correlation matrix using a heatmap to understand relationships between variables and ride completion.
5.  **Build and Evaluate a Logistic Regression Model:**
    *   Build a logistic regression model to predict the likelihood of ride completion.
    *   Initially, a simple model using `avg_vta` as a predictor is explored to demonstrate the process. (Note: Further model development with more features is recommended for better predictive power).
6.  **Visualization and Insight Analysis:**
    *   **Feature Engineering:** Extract time-based features (year, month, day, weekday, season, time of day) from the date and time columns.
    *   Create a 'route' column by combining pickup and drop locations.
    *   Analyze and visualize key metrics and patterns, such as ride completion rates by vehicle type, time of day, location, etc. (This section is planned for further development in the notebook).
7.  **Export Data:** Export the processed DataFrame to a CSV file (`uber_analytic_data.csv`) for further analysis or visualization in business intelligence tools (Power BI)

## Key Findings
### Notebook's Analysis
*   The dataset contains 150,000 bookings with no duplicate rows found after initial checks.
*   Missing values were handled by imputation based on column type and context.
*   Outliers in numerical features were identified and removed.
*   Correlation analysis revealed strong positive correlations between `is_completed` and `booking_value` (0.61) and `ride_distance` (0.73).
*   The initial logistic regression model with `avg_vta` as the sole predictor shows a low R-squared value (0.037), indicating that this single feature is not sufficient to explain ride completion. Further analysis with more features is required for a robust predictive model.
### Power BI platform's Analysis
1.   Low Service Efficiency and Dominant Driver Cancellations
*   Completion Rate: The overall ride completion rate is low at 61.56%. Out of 144,000 total bookings, only 89,000 were completed.
*   Driver-Driven Failure: Cancellations initiated by the driver account for the largest proportion of failures at 18.78% of total bookings. Driver-cancelled rides make up 72% ($27K$) of all pure cancellations, confirming this as the primary focus area.
*   Systemic Issue: The high cancellation rates (consistently $\sim26\%$) are uniform across all vehicle types, indicating a platform-wide operational or policy challenge5.
*   Incomplete Ride Causes: Rides marked "Incomplete" are split almost equally among Vehicle Breakdown (33.35%), Customer Demand (33.93%), and Other Issues (32.72%).
2.   Vehicle and Demand Trends
*   Volume Leader: The Auto vehicle type dominates the market, accounting for nearly 25% of all booked rides.
*   Peak Demand Times: Booking demand peaks consistently during the Afternoon and Evening across all vehicle types.
*   Cancellation Timing: Cancellations also peak during the Evening and Afternoon hours.
3.   Revenue and Payment Metrics
*   Payment Dominance: UPI is the most critical and dominant payment method, significantly leading in revenue contribution and transaction volume across top destinations.
*   Revenue Volatility: The platform experienced a significant revenue dip in February.
## Recommendation
1.   Optimize Ride Failure Rate
*   Focus on Driver-Side Cancellation: Implement a robust system to monitor, audit, and penalize drivers who repeatedly cancel rides. Since driver reasons are evenly split, a comprehensive approach addressing all categories (customer relation, personal, and operational) is required.
*   Address Vehicle Reliability: Given that 'Vehicle Breakdown' accounts for a third of incomplete rides, enforce enhanced maintenance and support protocols for all drivers to ensure fleet reliability.
*   Enhance Driver Assignment: Boost operational resources and recruitment to reduce the 7.30% of rides where 'No Driver Found' and to mitigate driver unwillingness to accept requests16
2.   Stabilize Revenue and Payment Methods
*   Investigate Revenue Dip: Conduct a deep dive to analyze the severe revenue drop experienced in February to identify its root cause (e.g., market event, platform issue, competition) and develop preventative strategies for future stability.
*   Secure UPI Channel: Ensure maximum security and stability for the UPI payment gateway, recognizing its role as the most critical revenue channel.
*   Promote Uber Wallet: Launch an introduction campaign or promotion to increase the usage of 'Uber Wallet' to regain ground lost to UPI and Cash payments.
