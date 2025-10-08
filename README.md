Uber 2024 — Ride Cancellation Modeling
Objective

Develop a predictive model to understand why and when Uber rides get canceled — identifying customer and driver behavior patterns while improving operational efficiency.

Dataset Overview

This dataset captures ~148,770 rides from Uber’s 2024 operations across multiple vehicle types and payment methods.

Metric	Value
Total Bookings	148,770
Completion Rate	65.96%
Cancellation Rate	25%
Customer Cancellations	19.15%
Driver Cancellations	7.45%
Vehicle Types	Go Mini, Go Sedan, Auto, eBike/Bike, UberXL, Premier Sedan
Time Coverage	Full Year 2024

Key Columns:

Booking Status: Completed, Cancelled by Customer, Cancelled by Driver, etc.

Avg VTAT: Average wait time for driver (min)

Avg CTAT: Average trip duration (min)

Booking Value: Total fare (₹)

Ride Distance: Distance (km)

Payment Method: UPI, Cash, Credit Card, Uber Wallet, Debit Card

Driver/Customer Ratings, Cancellation Reasons, Vehicle Type

Data Cleaning & Preparation

Goals:

Standardize booking statuses (lowercase, consistent naming)

Handle missing values intelligently:

Filled numeric columns (ratings, distance, fare) with mean/0

Replaced text-based missing values with “Unknown”

Converted VTAT/CTAT from minutes to seconds

Combined Date and Time into a single Booking Datetime

Engineered new time features:

Hour, Weekday, IsWeekend, IsRushHour

Added behavioral flags:

IsCash, ShortRide, HighValue

Modeling Approach

Implemented an end-to-end ML pipeline using scikit-learn:

Binary Classification: Predict if a ride will be completed or canceled

Multiclass Classification: Predict why it was canceled (Customer, Driver, No Driver, Incomplete)

Models Used:

Logistic Regression (Baseline)

Random Forest Classifier

HistGradientBoosting (Advanced comparison)

Pipeline Steps:

Preprocessing: Median imputation, scaling, and one-hot encoding

Modeling: Balanced class weights to address label imbalance

Evaluation: Accuracy, precision, recall, F1-score, confusion matrix

Results
Binary Model (Completed vs Canceled)

Accuracy: ~95%

Precision/Recall Balance: Strong

Key Drivers: Total Duration, VTAT, Ride Distance, Booking Value

Multiclass Model (Cancellation Reasons)

Accuracy: ~89%

Insights:

Driver cancellations dominate during peak hours

Customer cancellations linked to wrong address or driver not moving

“No driver found” more common in low-density areas

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

UPI is the most used payment method (~40% of total revenue)

Cash ranks second (~25%)

Go Sedan and Auto lead in total bookings

Driver-related issues and wrong addresses are top cancellation reasons

High wait times (VTAT > 10 min) significantly increase cancellation likelihood

Key Learnings

Wait time (VTAT) is the strongest predictor of cancellations

Time-based features (rush hours, weekends) improve model reliability

Combining EDA and ML enables both diagnostic and predictive insights

Feature engineering transforms raw operational data into actionable metrics

Tech Stack

Language: Python (Pandas, NumPy, Matplotlib, Seaborn, scikit-learn)

Tools: Power BI / Tableau (for visualization)

Notebook: Jupyter / Anaconda

Version Control: GitHub

Author
CJ II
chrissjerman@gmail.com