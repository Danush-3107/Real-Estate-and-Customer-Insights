# Real Estate and Customer Insights

A Python data analysis project that cleans, merges, and explores real estate sales data alongside customer demographics to uncover trends in buyer behavior, property pricing, and market segmentation.

## Overview

This project takes two raw datasets — customer records and property sales records — and transforms them into a single, analysis-ready dataset. It then performs descriptive statistics, grouped breakdowns, and a series of visualizations to answer practical business questions such as:

- Which customer age bracket has the most buyer potential?
- What is the most sought-after building type?
- Which building type commands the highest average price?
- Is there a relationship between customer age and property price?

## Project Structure

```
├── Real_Estate_and_Customer_Insights.ipynb   # Main notebook (cleaning + analysis)
├── customers.csv                             # Raw customer data (input, not included)
├── properties.csv                            # Raw property sales data (input, not included)
├── cleaned_real_estate_data.csv              # Cleaned, merged output dataset
└── README.md
```

## Data Sources

The notebook expects two input CSV files:

| File | Description |
|---|---|
| `customers.csv` | Customer-level data: ID, sex, birth date, mortgage status, etc. |
| `properties.csv` | Property-level data: ID, customer ID, price, building type, area, sale date, deal satisfaction, status, location |

> **Note:** File paths in the notebook are currently hardcoded (e.g. `C:/Users/Danush/Downloads/...`). Update these paths to match your local environment before running.

## Workflow

### 1. Data Cleaning
- Standardizes column names (removes hidden characters, lowercases, replaces spaces/symbols)
- Parses date fields (`birth_date`, `date_sale`) and coerces invalid entries to `NaT`
- Cleans currency-formatted price strings into numeric floats
- Normalizes text fields (lowercase, stripped whitespace)
- Encodes categorical fields (`sex`, `mortgage`) into binary numeric values
- Drops records with missing customer IDs and merges customers with properties on `customerid`
- Removes remaining rows with missing values
- Exports the cleaned dataset to `cleaned_real_estate_data.csv`

### 2. Exploratory Analysis
- Descriptive statistics on the cleaned dataset
- Binary encoding of sale status (`sold` flag)
- Aggregated totals and averages by **building type** (sold count, mortgage count, average area/price/deal satisfaction)
- Mapping of numeric building codes to readable labels (Apartment, Villa, Duplex, Studio, Penthouse)
- Breakdown of sales and mortgages by **country**
- Frequency, relative frequency, and cumulative frequency by **state**
- Customer age calculation (from birth date and sale date) and binning into age groups
- Price binning into 10 equal-width groups
- Covariance and correlation analysis between age and price

### 3. Visualizations
Built with `matplotlib` and `seaborn`:
- Scatter plot: Age vs. Property Price
- Bar charts: Average deal satisfaction by country and by state
- Line chart: Monthly revenue over time
- Pareto chart: Apartments sold by state (with cumulative % curve)
- Histogram: Customer age distribution
- Stacked bar chart: Yearly sales by building type

### 4. Data Interpretation
Answers four key business questions with supporting charts and inline insights:
1. Which age bracket has the most buyer potential
2. The most sought-after building type
3. The highest-priced building type
4. The relationship between customer age and property price

## Requirements

```
pandas
numpy
matplotlib
seaborn
jupyter
```

Install dependencies with:

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

## Usage

1. Place `customers.csv` and `properties.csv` in an accessible directory.
2. Update the file paths in the first code cell to point to your local files.
3. Launch Jupyter and run the notebook top to bottom:

```bash
jupyter notebook Real_Estate_and_Customer_Insights.ipynb
```

4. The cleaned dataset will be saved as `cleaned_real_estate_data.csv` in the working directory, and all charts will render inline.

## Key Insights (example findings)

- Identifies the customer age segment most likely to drive future sales, useful for targeted marketing.
- Highlights the most popular and most expensive building types, useful for inventory and pricing strategy.
- Quantifies whether age and price are linearly related, informing whether age-based pricing or targeting assumptions hold up.

## License

This project is intended for educational and portfolio purposes.
