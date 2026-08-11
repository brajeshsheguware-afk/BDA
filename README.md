# Superstore Sales Data Analysis

## 📌 Project Overview

This project focuses on understanding, preprocessing, and analyzing the **Superstore Sales dataset** using Python.

The project includes data cleaning, statistical analysis, date conversion, delivery time calculation, category analysis, and Exploratory Data Analysis (EDA). Different visualizations are used to understand sales, profit, discount, and relationships between numerical variables.

The analysis was performed using **Google Colab**.

---

## 🎯 Objectives

* Understand the structure of the Superstore Sales dataset
* Inspect and clean the dataset
* Convert date columns into proper datetime format
* Calculate delivery days for each order
* Check for missing values
* Analyze sales and profit performance
* Study the effect of discounts on profit
* Identify important correlations
* Create meaningful data visualizations
* Extract useful business insights from the dataset

---

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Google Colab**
* **Google Drive**

---

## 📂 Dataset

**Dataset Name:** `samplesuperstore.csv`

The dataset contains:

* **10,194 records**
* **21 columns**

### Main Columns

* Row ID
* Order ID
* Order Date
* Ship Date
* Ship Mode
* Customer ID
* Customer Name
* Segment
* Region
* Category
* Sub-Category
* Product Name
* Sales
* Quantity
* Discount
* Profit

---

# 📌 Task 1 – Data Understanding & Preprocessing

## 1. Importing Libraries

Pandas and NumPy were imported for data processing and analysis.

```python
import pandas as pd
import numpy as np
```

---

## 2. Loading the Dataset

The `samplesuperstore.csv` file was loaded into a Pandas DataFrame.

```python
df = pd.read_csv("/content/drive/MyDrive/samplesuperstore.csv")
```

---

## 3. Dataset Inspection

The dataset structure was examined using:

```python
df.head()
df.info()
```

This helped to understand the columns, data types, number of records, and non-null values.

---

## 4. Statistical Analysis

The `describe()` function was used to obtain statistical information about numerical columns.

```python
df.describe()
```

This provides information such as:

* Count
* Mean
* Standard deviation
* Minimum value
* Maximum value
* Quartiles

---

## 5. Date Conversion

The `Order Date` and `Ship Date` columns were converted into datetime format.

```python
df['Order Date'] = pd.to_datetime(df['Order Date'])
df['Ship Date'] = pd.to_datetime(df['Ship Date'])
```

This makes date-based calculations and analysis easier.

---

## 6. Delivery Days Calculation

A new column named `Delivery Days` was created.

```python
df['Delivery Days'] = (
    df['Ship Date'] - df['Order Date']
).dt.days
```

This column represents the number of days taken between the order date and shipping date.

---

## 7. Category Analysis

The unique product categories were identified using:

```python
df['Category'].unique()
```

The dataset contains three major categories:

* Furniture
* Office Supplies
* Technology

---

## 8. Missing Value Analysis

Missing values were checked using:

```python
df.isnull().sum()
```

### Result

No missing values were found in the dataset.

---

# 📊 Task 2 – Exploratory Data Analysis & Visualization

The second task focuses on analyzing sales, profit, discount, category performance, and correlations between numerical variables.

---

## 1. Sales by Category

Total sales were calculated for each product category.

```python
category_sales = df.groupby('Category')['Sales'].sum()
category_sales
```

### Finding

**Technology** generated the highest total sales, with approximately **839,893.28**.

---

## 2. Sales by Category – Bar Chart

A bar chart was created to compare total sales between categories.

```python
category_sales.plot(
    kind='bar',
    figsize=(8,5)
)

plt.title("Sales by Category")
plt.ylabel("Total Sales")
plt.show()
```

---

## 3. Sales Distribution

A histogram was used to understand the distribution of sales values.

```python
plt.figure(figsize=(8,5))
sns.histplot(df['Sales'], bins=30)

plt.title("Sales Distribution")
plt.show()
```

This visualization helps identify common sales ranges and high-value sales observations.

---

## 4. Profit by Category

A bar plot was created to compare average profit across categories.

```python
sns.barplot(
    data=df,
    x="Category",
    y="Profit"
)

plt.title("Profit by Category")
plt.show()
```

This helps compare the profitability of Furniture, Office Supplies, and Technology.

---

## 5. Sales Distribution by Category

Average sales were compared across different product categories.

```python
sns.barplot(
    data=df,
    x="Category",
    y="Sales"
)

plt.title("Sales Distribution by Category")
plt.show()
```

---

## 6. Profit Distribution

A boxplot was used to understand the overall distribution of profit.

```python
sns.boxplot(
    data=df,
    y="Profit"
)

plt.title("Profit Distribution")
plt.show()
```

The visualization helps identify:

* Profit variation
* Negative profit values
* Extreme profit values
* Possible outliers

---

## 7. Profit Variation Across Categories

A category-wise boxplot was created.

```python
sns.boxplot(
    data=df,
    x="Category",
    y="Profit"
)

plt.title("Profit Variation Across Categories")
plt.show()
```

This shows the median, spread, and outliers for each category.

---

## 8. Discount Analysis

The unique discount values were identified using:

```python
df["Discount"].unique()
```

Discount values range from **0 to 0.8**.

---

## 9. Impact of Discount on Profit

A scatter plot was created to study the relationship between discount and profit.

```python
sns.scatterplot(
    data=df,
    x="Discount",
    y="Profit"
)

plt.title("Impact of Discount on Profit")
plt.show()
```

### Finding

The correlation between Discount and Profit is approximately **-0.219**, indicating a weak negative relationship.

---

# 🔗 Correlation Analysis

## 1. Selecting Numerical Columns

Numerical columns were selected using:

```python
numeric_df = df.select_dtypes(
    include="number"
)
```

---

## 2. Correlation Matrix

The correlation matrix was calculated using:

```python
corr = numeric_df.corr()
corr
```

### Important Correlations

| Variables              | Correlation |
| ---------------------- | ----------: |
| Sales – Profit         |       0.481 |
| Discount – Profit      |      -0.219 |
| Sales – Quantity       |       0.198 |
| Quantity – Profit      |       0.066 |
| Delivery Days – Profit |      -0.004 |

---

## 3. Correlation Heatmap

A heatmap was created to visualize relationships between numerical variables.

```python
sns.heatmap(
    corr,
    annot=True
)

plt.title("Correlation Heatmap")
plt.show()
```

The heatmap makes positive and negative relationships between variables easier to understand.

---

# 📈 Visualizations Created

The following visualizations were created during the analysis:

1. **Sales by Category** – Bar Chart
<img width="721" height="560" alt="image" src="https://github.com/user-attachments/assets/ecbb467f-21e0-430b-93f6-7f4de38f5cda" />

2. **Sales Distribution** – Histogram
<img width="704" height="470" alt="image" src="https://github.com/user-attachments/assets/83286714-81ff-4cb4-a040-eaec336bc70c" />

3. **Profit by Category** – Bar Plot
<img width="571" height="455" alt="image" src="https://github.com/user-attachments/assets/771e60f9-8187-41b7-ab66-19440a3f5819" />

4. **Sales Distribution by Category** – Bar Plot
<img width="571" height="455" alt="image" src="https://github.com/user-attachments/assets/89a0ad53-ce32-4894-83e0-4d968ce029d3" />

5. **Profit Distribution** – Boxplot
<img width="592" height="416" alt="image" src="https://github.com/user-attachments/assets/bd18f3ca-dfa6-43b5-afef-6a6e32f986ec" />

6. **Profit Variation Across Categories** – Boxplot
<img width="592" height="455" alt="image" src="https://github.com/user-attachments/assets/ceb42ca1-7b50-40d1-afb6-6b158a2a0b0b" />

7. **Discount vs Profit** – Scatter Plot
<img width="592" height="455" alt="image" src="https://github.com/user-attachments/assets/a0debac4-1e7f-457e-a20d-1e7cc7fec981" />

8. **Correlation Heatmap**
<img width="609" height="518" alt="image" src="https://github.com/user-attachments/assets/cc1e84bd-dc9f-4133-be17-9079a7b2d175" />

---

# 🔑 Key Findings

* The dataset contains **10,194 records and 21 columns**.
* No missing values were found.
* The dataset contains three major categories: **Furniture, Office Supplies, and Technology**.
* Technology generated the highest total sales.
* Sales and Profit have a moderate positive correlation of approximately **0.481**.
* Discount and Profit have a weak negative correlation of approximately **-0.219**.
* The dataset contains negative profit values.
* Several profit outliers are present.
* Delivery Days has almost no relationship with Profit, with a correlation of approximately **-0.004**.
* Category-wise sales and profit performance varies across the dataset.

---

# 📁 Project Structure

```text
Superstore-Sales-Analysis/
│
├── samplesuperstore.csv
├── Superstore_Sales_Analysis.ipynb
├── README.md
│
└── visualizations/
    ├── sales_by_category.png
    ├── sales_distribution.png
    ├── profit_by_category.png
    ├── profit_distribution.png
    ├── profit_variation.png
    ├── discount_vs_profit.png
    └── correlation_heatmap.png
```

---

# 🚀 Future Scope

The project can be extended with:

* Monthly Sales Analysis
* Yearly Sales Analysis
* Regional Sales Analysis
* Sub-Category Analysis
* Customer Segment Analysis
* Top 10 Products
* Top Customers
* Sales Forecasting
* Profit Prediction
* Customer Analysis
* Interactive Dashboard

---

# 🎯 Conclusion

The Superstore Sales dataset was successfully understood, preprocessed, and analyzed using Python.

Task 1 focused on data understanding, date conversion, delivery day calculation, category identification, and missing value analysis.

Task 2 focused on Exploratory Data Analysis and visualization of sales, profit, discount, and correlations.

The analysis provides useful insights into category performance, profitability, discount impact, and relationships between numerical variables. The prepared dataset can be used for further analysis, forecasting, and dashboard development.

---

## 👨‍💻 Author

**K. Brajesh Sheguware**

BCA Student | Aspiring Software Developer

### Skills Used

Python | Pandas | NumPy | Matplotlib | Seaborn | Data Analysis
