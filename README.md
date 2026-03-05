# NYC Airbnb Price Analysis

This project explores the New York City Airbnb listings dataset and builds a simple machine learning model to understand the factors that influence listing prices.

The goal of this project is not only to build a predictive model but also to practice structured data analysis: cleaning raw data, exploring patterns, engineering useful features, and evaluating model behavior.

---

## Dataset

The dataset used in this project is the NYC Airbnb listings dataset.

You can download it from Kaggle:
https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data

After downloading, place the CSV file in the project root directory before running the notebook.

The dataset contains information about Airbnb listings in New York City, including:

- Listing price
- Room type
- Neighborhood group (borough)
- Number of reviews
- Host information
- Last review date
- Reviews per month

Each row represents a single listing.

---

## Project Goals

This project focuses on three main questions:

- What factors appear to influence Airbnb listing prices?
- How do price distributions vary across boroughs and room types?
- Can simple machine learning models reasonably predict listing prices?

---

## Analysis Steps

The project follows a typical data analysis workflow:

1. Data cleaning and preprocessing
2. Exploratory data analysis (EDA)
3. Feature engineering
4. Model training and evaluation

---

## Data Cleaning Decisions

Several cleaning steps were required to prepare the dataset:

- Converted `last_review` to a datetime format
- Filled missing text fields (`name`, `host_name`) with placeholders
- Treated missing `reviews_per_month` values as 0 (no reviews)
- Removed invalid or non-positive prices
- Applied log transformation to price to reduce skew
- Capped extreme price outliers at the 99th percentile

---

## Exploratory Analysis

Several visualizations were used to better understand the dataset:

- Distribution of listings across boroughs
- Price distributions (raw and capped)
- Price comparisons by room type
- Host behavior and pricing patterns

These plots helped reveal structural patterns in the NYC Airbnb market.

---

## Feature Engineering

Some additional features were created to capture useful patterns:

- `price_log1p` – log-transformed price for stable modeling
- `price_capped` – price capped at the 99th percentile to reduce extreme outliers
- `host_listing_count` – number of listings per host
- `is_professional_host` – indicator for hosts with multiple listings
- `days_since_last_review` – time since the most recent review

---

## Modeling

Two models were trained to predict log-transformed price:

- Linear Regression
- Random Forest Regressor

The models were trained using a preprocessing pipeline that:

- Imputes missing numeric values using the median
- Scales numeric features
- Imputes categorical features using the most frequent value
- One-hot encodes categorical variables

---

## Key Insights

Some high-level observations from the analysis:

- Airbnb supply is heavily concentrated in Manhattan and Brooklyn.
- Entire homes and apartments tend to command significantly higher prices than private rooms.
- Professional hosts appear more frequently in higher price ranges, though the difference is not dramatic.
- Price distributions are highly skewed, making log transformation important for modeling.
- Tree-based models performed slightly better than linear models, suggesting non-linear relationships in the data.

---

## Limitations

The model cannot capture several factors that likely influence price, such as:

- Exact geographic location
- Property quality and amenities
- Interior condition and photos
- Seasonal demand

Because these variables are missing, prediction accuracy remains limited.

---

## Project Structure

```
nyc-airbnb-price-analysis
│
├── nyc_airbnb_analysis.ipynb
└── README.md
```

---

## Tools Used

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn

---

## Purpose of This Project

This project was built as part of rebuilding and strengthening practical data analysis skills, focusing on:

- structured exploratory analysis
- feature engineering
- reproducible modeling workflows
- clear interpretation of results


  
