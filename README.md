Uber 2024 — Ride Cancellation Modeling
Objective

Develop a predictive model to understand why and when Uber rides get canceled, identifying customer and driver behavior patterns to improve operational efficiency and reliability.

Dataset Overview

The dataset contains approximately 148,770 rides from Uber’s 2024 operations, covering multiple vehicle types and payment methods across India.

Metric	Value
Total Bookings	148,770
Completion Rate	65.96%
Cancellation Rate	25%
Customer Cancellations	19.15%
Driver Cancellations	7.45%
Vehicle Types	Go Mini, Go Sedan, Auto, eBike/Bike, UberXL, Premier Sedan
Time Coverage	Full Year 2024

Key Columns

Booking Status: Completed, Cancelled by Customer, Cancelled by Driver, etc.

Avg VTAT: Average wait time for driver (minutes)

Avg CTAT: Average trip duration (minutes)

Booking Value: Total fare amount (₹)

Ride Distance: Distance of trip (km)

Payment Method: UPI, Cash, Credit Card, Uber Wallet, Debit Card

Ratings and Reasons: Driver Rating, Customer Rating, Cancellation Reasons, Vehicle Type

Data Cleaning & Preparation

Goals

Standardized inconsistent booking statuses (lowercased and stripped spaces).

Handled missing values with appropriate methods:

Numeric features (ratings, distance, fare) → filled with mean or zero.

Text features (cancellation reasons) → replaced with "Unknown".

Converted VTAT/CTAT from minutes to seconds for modeling.

Combined Date and Time into a single Booking Datetime.

Engineered new time-based features:

Hour, Weekday, IsWeekend, IsRushHour

Added behavioral flags:

IsCash, ShortRide, HighValue

Modeling Approach

A full end-to-end ML pipeline was built using scikit-learn, covering data preprocessing, modeling, and evaluation.

Classification Tasks

Binary Model: Predict if a ride will be completed or canceled.

Multiclass Model: Predict why the ride was canceled (Customer, Driver, No Driver, Incomplete).

Models Implemented

Logistic Regression (baseline)

Random Forest Classifier

HistGradientBoosting (advanced comparison)

Pipeline Steps

Preprocessing: median imputation, scaling, and one-hot encoding

Model training: balanced class weights to handle label imbalance

Evaluation: accuracy, precision, recall, F1-score, and confusion matrix

Results
Binary Classification (Completed vs. Canceled)

Accuracy: ~95%

Precision/Recall: Strong balance

Key Drivers: Total Duration, VTAT, Ride Distance, Booking Value

Multiclass Classification (Cancellation Reasons)

Accuracy: ~89%

Insights:

Driver cancellations peak during rush hours.

Customer cancellations often stem from incorrect pickup details.

“No driver found” cases are more frequent in low-demand areas.

Top Feature Importances
Feature	Importance
Total Duration (sec)	0.27
Avg VTAT (sec)	0.26
Ride Distance	0.15
Avg CTAT (sec)	0.10
Booking Value	0.06
Payment Method	0.05
Hour	0.04

(VTAT = Wait time before trip, CTAT = Trip duration)

Data Insights

UPI accounts for nearly 40% of total revenue, followed by Cash (~25%).

Go Sedan and Auto dominate ride volume.

High wait times (VTAT > 10 min) are the most significant predictor of cancellation.

Driver-related issues and address mismatches are top cancellation reasons.

Key Learnings

Wait time (VTAT) is the strongest cancellation predictor.

Time-based features (rush hours, weekends) significantly enhance prediction accuracy.

Combining EDA and ML provides both diagnostic and predictive understanding.

Thoughtful feature engineering transforms raw data into actionable business metrics.

Tech Stack

Language: Python (Pandas, NumPy, Matplotlib, Seaborn, scikit-learn)
Visualization: Power BI, Tableau
Environment: Jupyter Notebook / Anaconda
Version Control: GitHub

Author

CJ II
📧 chrissjerman@gmail.com
