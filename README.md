# Superstore Sales Data Understanding, Cleaning & Exploratory Analysis

## Overview

This project focuses on understanding, cleaning, and exploring the Superstore Sales dataset using Python and Pandas. The main objective is to prepare the dataset for further analysis by identifying data types, handling date columns, cleaning text values, and generating summary statistics.

## Objectives

* Load the Superstore Sales dataset.
* Understand the structure of the dataset.
* Convert date columns into datetime format.
* Clean and standardize categorical text values.
* Generate summary statistics for numerical data.
* Prepare the dataset for exploratory data analysis (EDA).

## Tools and Libraries

* Python
* Pandas
* NumPy
* Jupyter Notebook / Google Colab

## Dataset

The dataset contains sales records of a retail superstore, including:

* Order ID
* Order Date
* Ship Date
* Customer Details 
* Segment
* Category
* Sub-Category
* Product Information
* Sales
* Quantity
* Discount
* Profit

## Steps Performed

### 1. Data Loading

* Imported the dataset using the Pandas library.
* Loaded the CSV file into a DataFrame.

### 2. Data Inspection

Used the following functions to understand the dataset:

* `head()` – Displays the first few rows.
* `info()` – Shows column names, data types, and missing values.
* `describe()` – Provides statistical summaries of numerical columns.

### 3. Date Conversion

Converted the following columns into datetime format:

* Order Date
* Ship Date

This enables easy date-based analysis and calculations.

### 4. Data Cleaning

Cleaned categorical columns by:

* Removing leading and trailing spaces.
* Standardizing text formatting.
* Ensuring consistent values in:

  * Category
  * Sub-Category
  * Segment

### 5. Summary Statistics

Calculated summary statistics for numerical columns such as:

* Sales
* Quantity
* Discount
* Profit

Statistics include:

* Count
* Mean
* Standard Deviation
* Minimum
* Maximum
* Quartiles (25%, 50%, 75%)

## Project Outcome

After cleaning and understanding the dataset:

* Date columns are in the correct format.
* Categorical values are standardized.
* Numerical data has been summarized.
* The dataset is ready for Exploratory Data Analysis (EDA) and visualization.

## Future Enhancements

* Handle missing values.
* Detect and remove duplicate records.
* Identify outliers.
* Create visualizations using Matplotlib and Seaborn.
* Perform advanced sales and profit analysis.

## Author

**Brajesh Sheguware K**
