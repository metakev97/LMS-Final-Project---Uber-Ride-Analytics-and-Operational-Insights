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
7.  **Export Data:** Export the processed DataFrame to a CSV file (`uber_analytic_data.csv`) for further analysis or visualization in business intelligence tools.

## Key Findings

*   The dataset contains 150,000 bookings with no duplicate rows found after initial checks.
*   Missing values were handled by imputation based on column type and context.
*   Outliers in numerical features were identified and removed.
*   Correlation analysis revealed strong positive correlations between `is_completed` and `booking_value` (0.61) and `ride_distance` (0.73).
*   The initial logistic regression model with `avg_vta` as the sole predictor shows a low R-squared value (0.037), indicating that this single feature is not sufficient to explain ride completion. Further analysis with more features is required for a robust predictive model.

## Recommendation

