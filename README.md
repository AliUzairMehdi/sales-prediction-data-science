# Sales Analytics & Prediction – Data Science Project

This project is an end-to-end data science workflow built on a raw sales dataset. It covers the full pipeline expected from a junior data scientist:

- Data cleaning and preprocessing
- SQL database integration and querying
- Exploratory analysis and visual insights
- Machine learning classification model (predicting High-Value weekend orders)
- Sales forecasting (predicting next month’s revenue using regression)

---

## 📦 Dataset Description

Source: Synthetic CSV file generated with random but messy values.

Columns include:

| Column | Description |
|--------|-------------|
| OrderID | Transaction identifier (some duplicates) |
| CustomerName | Name of customer (some nulls) |
| Product | Product name |
| Category | Product category (inconsistent casing) |
| Quantity | Quantity ordered (can be missing or invalid) |
| UnitPrice | Price per item (can be negative or null) |
| OrderDate | Date of order (multiple formats) |
| PaymentMethod | Cash, Credit Card, PayPal, Unknown |
| *Derived:* Amount | Quantity × UnitPrice |

---

## ✅ Steps Performed

### 1. Data Cleaning (Pandas)

- Removed duplicate rows
- Standardized category names
- Filtered negative quantity or price values
- Removed rows with null CustomerName and invalid dates
- Filled missing PaymentMethod as “Unknown”
- Converted `OrderDate` into datetime + extracted Year, Month, Day, Weekday, Weekend
- Created `Amount` column

---

### 2. Load into SQLite

Imported the cleaned DataFrame into a SQLite database (`sales.db`) as a `sales` table to run SQL queries for analysis.

---

### 3. SQL Analytical Queries

Examples executed:

- Total revenue by category
- Top 5 customers by revenue
- Revenue by Month
- Revenue by Payment Method
- Monthly revenue trend

---

### 4. Machine Learning: Classification

**Objective:** Predict if an order is a *High-Value Weekend order*

- Feature engineering: created target `WeekendHighValue` = 1 if (Weekend=1 and Amount >= 1000) else 0
- One-hot encoded categorical features (Category, PaymentMethod)
- Model used: Logistic Regression
- Achieved accuracy: **100%** (small dataset, currently small scale)

---

### 5. Machine Learning: Sales Forecasting

**Objective:** Predict revenue for next month

- Grouped data by Year-Month to get total monthly revenue
- Added a `MonthIndex` feature
- Trained a Linear Regression model
- Predicted next month's sales from previous trend

---
