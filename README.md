"""
Sales Data Analysis

This script performs basic data loading, exploration, cleaning, and visualization
on a sales dataset using pandas and matplotlib.

Features:
- Loads a CSV dataset from a URL
- Displays the first few rows of the data
- Checks for missing values and cleans them
- Shows data types and structure
- Generates a scatter plot: Units Sold vs. Total Revenue

Requirements:
- Python 3.x
- pandas
- matplotlib

To install the required libraries, run:
pip install pandas matplotlib

To run the script:
python sales_analysis.py
"""

import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset (Example: Supermarket Sales)
url = 'https://raw.githubusercontent.com/selva86/datasets/master/SupermarketSales.csv'
df = pd.read_csv(url)

# Display the first few rows
print("First 5 rows of the dataset:")
print(df.head())

# Display data structure
print("\nDataset Information:")
print(df.info())

# Check for missing values
print("\nMissing Values in Each Column:")
print(df.isnull().sum())

# Clean the dataset (drop or fill missing values)
df = df.dropna()  # or use df.fillna(value) to fill missing values

# Example: Scatter plot of Units Sold vs. Total Revenue
# First, check if the columns exist
if 'Quantity' in df.columns and 'Total' in df.columns:
    plt.figure(figsize=(10, 6))
    plt.scatter(df['Quantity'], df['Total'], alpha=0.7, color='purple')
    plt.title('Units Sold vs. Total Revenue')
    plt.xlabel('Units Sold')
    plt.ylabel('Total Revenue')
    plt.grid(True)
    plt.show()
else:
    print("\nRequired columns not found for plotting.")
