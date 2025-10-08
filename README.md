Uber 2024 — Ride Cancellation Modeling
Objective

The goal of this project is to predict why and when Uber rides get canceled by analyzing ride-level booking data.
This helps uncover customer and driver behavior patterns and identify operational inefficiencies that affect ride completion rates.

Dataset Overview

The dataset contains approximately 148,770 ride records from Uber’s 2024 operations.
It includes various vehicle types, payment methods, and cancellation reasons.

Summary

Total Bookings: 148,770

Completion Rate: 65.96%

Cancellation Rate: 25%

Customer Cancellations: 19.15%

Driver Cancellations: 7.45%

Vehicle Types: Go Mini, Go Sedan, Auto, eBike/Bike, UberXL, Premier Sedan

Time Coverage: Full Year 2024

Main Columns

Booking Status (Completed, Cancelled by Customer, Cancelled by Driver, etc.)

Avg VTAT – Average wait time for driver (minutes)

Avg CTAT – Average trip duration (minutes)

Booking Value – Total fare (₹)

Ride Distance – Distance traveled (km)

Payment Method – UPI, Cash, Credit Card, Uber Wallet, Debit Card

Ratings and Cancellation Reasons – Customer and driver feedback

Data Preparation
Cleaning

Standardized booking status text (e.g., lowercasing, removing spaces).

Filled missing numeric values with column means or zeros.

Replaced missing text fields (reasons, methods) with "Unknown".

Converted VTAT and CTAT from minutes to seconds.

Merged Date and Time into a single Booking Datetime column.

Feature Engineering

Created new derived columns to better capture behavior patterns:

Time-based features: Hour, Weekday, IsWeekend, IsRushHour

Behavioral flags: IsCash, ShortRide, HighValue

These features improved the ability to predict cancellations and reveal context behind them.

Modeling Approach

An end-to-end machine learning pipeline was built using scikit-learn.

Tasks

Binary Classification: Predict if a ride will be completed or canceled.

Multiclass Classification: Predict why it was canceled (Customer, Driver, No Driver, Incomplete).

Models

Logistic Regression (baseline model)

Random Forest Classifier (main model)

HistGradientBoosting (advanced comparison)

Pipeline Structure

Preprocessing: median imputation, scaling, and one-hot encoding

Modeling: used balanced class weights to handle label imbalance

Evaluation: accuracy, precision, recall, F1-score, and confusion matrices

Results
Binary Classification

Accuracy: ~95%

Precision/Recall: strong balance

Key Drivers: Total Duration, VTAT, Ride Distance, Booking Value

Multiclass Classification

Accuracy: ~89%

Key Insights:

Driver cancellations peak during rush hours.

Customer cancellations often occur due to incorrect addresses or delays.

“No driver found” happens mostly in low-demand areas.

Top Feature Importances

Total Duration (sec): 0.27

Avg VTAT (sec): 0.26

Ride Distance: 0.15

Avg CTAT (sec): 0.10

Booking Value: 0.06

Payment Method: 0.05

Hour: 0.04

(VTAT = wait time before trip, CTAT = trip duration)

Data Insights

UPI accounts for roughly 40% of total revenue, followed by Cash (25%).

Go Sedan and Auto rides make up the largest share of bookings.

Long wait times (VTAT > 10 minutes) sharply increase cancellation probability.

Driver-related issues and address mismatches are top cancellation causes.

Key Learnings

Wait time is the strongest single predictor of cancellations.

Time-based patterns (rush hours, weekends) enhance predictive reliability.

Combining EDA and machine learning gives both diagnostic and predictive insights.

Feature engineering significantly improves model explainability.

Tools and Technologies

Language: Python (Pandas, NumPy, Matplotlib, Seaborn, scikit-learn)

Visualization: Power BI, Tableau

Environment: Jupyter Notebook / Anaconda

Version Control: GitHub

Author

Christopher Jerman II
📧 chrissjerman@gmail.com
