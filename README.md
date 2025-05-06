# **Atlantic Shores Offshore Wind Time Series Analysis**

This repository contains a Jupyter Notebook (`Atlantic_Shores_Offshore_Wind_timeseries.ipynb`) that performs initial data loading, cleaning, and analysis on a time series dataset related to the Atlantic Shores Offshore Wind project. The project focuses on preparing the data and visualizing temperature measurements over time.

## **Table of Contents**

* [Business Problem](#business-problem)
* [Solution](#solution)
* [Dataset](#dataset)
* [Methodology](#methodology)
* [Prerequisites](#prerequisites)
* [How to Run](#how-to-run)
* [Key Steps in the Code](#key-steps-in-the-code)
* [Results](#results)
* [Visualizations](#visualizations)
* [Future Improvements](#future-improvements)
* [License](#license)

## **Business Problem**

Analyzing time series data from offshore wind projects, such as environmental parameters like temperature, is crucial for understanding site conditions, validating sensor data, and potentially correlating with operational performance or environmental impact studies. Raw data often requires cleaning and structuring before meaningful analysis can be performed. This project addresses the initial steps of preparing such a dataset for further time series analysis.

## **Solution**

This project provides a basic data loading, cleaning, and preliminary visualization solution for the Atlantic Shores Offshore Wind time series data. The Jupyter Notebook demonstrates how to:

1.  Load data from an Excel file.
2.  Perform basic data cleaning by dropping irrelevant rows and columns and checking for duplicates.
3.  Inspect data types and handle missing values.
4.  Convert columns to appropriate data types (datetime and numeric).
5.  Extract time-based features (year, month, day, hour).
6.  Perform a simple aggregation (grouping by time) and visualize a key environmental parameter (`T_25`) against the day of the month using a bar plot.

This initial processing makes the data more accessible and provides a starting point for more in-depth time series analysis.

## **Dataset**

The project uses data from an Excel file named `ASOW-2.xlsx`. Based on the notebook, the dataset contains columns such as:

* `longitude`: Longitude coordinate.
* `latitude`: Latitude coordinate.
* `time`: Timestamp of the data point.
* `station`: Station identifier (dropped in the notebook as `wmo_platform_code` seems to contain similar info).
* `wmo_platform_code`: WMO platform code.
* `T_25`: Temperature measurement at 25m depth.

The dataset appears to contain time series data recorded at different locations (`longitude`, `latitude`, `wmo_platform_code`) over a period of time.

## **Methodology**

The analysis follows these main steps:

1.  **Load Libraries:** Import necessary Python libraries (`pandas`, `numpy`, `seaborn`, `matplotlib.pyplot`).
2.  **Load Data:** Read the `ASOW-2.xlsx` file into a pandas DataFrame, skipping the first row which appears to be header information not needed in the DataFrame.
3.  **Initial Data Cleaning:**
    * Drop the first row (`labels=0, axis=0`).
    * Drop the 'station' column (`axis=1, inplace=True`).
    * Check for and count duplicate rows (`.duplicated().sum()`).
4.  **Data Inspection:** Check data types (`.info()`) and unique values (`.nunique()`), and sum missing values per column (`.isna().sum()`).
5.  **Data Type Conversion:** Convert the 'time' column to datetime objects (`pd.to_datetime`) and the 'T_25' column to numeric type (`pd.to_numeric`).
6.  **Time-based Feature Extraction:** Extract 'year', 'month', 'day', and 'hour' from the 'time' column using `pd.DatetimeIndex`.
7.  **Data Aggregation:** Group the DataFrame by 'time' and count the entries for each timestamp (`.groupby('time').count()`).
8.  **Visualization:** Create a bar plot using seaborn to visualize the relationship between 'T_25' and 'day'.

## **Prerequisites**

Make sure you have Python installed. The following Python libraries are required:

```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
```

You can install these packages using pip:

```bash
pip install pandas numpy seaborn matplotlib openpyxl
```
Note: `openpyxl` is needed by pandas to read `.xlsx` files.

If you are using Google Colab or a similar environment, most of these libraries are likely pre-installed.

## **How to Run**

1.  Download the `ASOW-2.xlsx` dataset and the Jupyter Notebook (`Atlantic_Shores_Offshore_Wind_timeseries.ipynb`).
2.  Ensure both files are in the same directory, or update the file path in the notebook's data loading cell (`pd.read_excel('/content/ASOW-2.xlsx')`) to the correct location of the Excel file.
3.  Open the notebook in a Jupyter environment (like Jupyter Notebook, JupyterLab, or Google Colab).
4.  Run the cells sequentially. The notebook will execute the data loading, cleaning, feature extraction, and visualization steps.

## **Key Steps in the Code**

This section outlines the main logical steps performed in the Python script without including the code itself.

* Importing necessary libraries (`pandas`, `numpy`, `seaborn`, `matplotlib.pyplot`).
* Loading the data from the `ASOW-2.xlsx` Excel file, skipping the first row.
* Dropping the 'station' column.
* Checking for duplicate rows.
* Inspecting data types and non-null counts (`.info()`).
* Checking for missing values (`.isna().sum()`).
* Converting the 'time' column to datetime objects.
* Converting the 'T_25' column to numeric type.
* Grouping the DataFrame by 'time' and counting entries.
* Extracting 'year', 'month', 'day', and 'hour' from the 'time' column.
* Creating a bar plot of 'T_25' against 'day' using seaborn.

## **Results**

The notebook will output various results throughout the execution, including:

1.  A preview of the loaded DataFrame after dropping the first row.
2.  Information about the DataFrame, including data types and non-null counts (`.info()`).
3.  The count of duplicate rows.
4.  The number of unique values in each column.
5.  The sum of missing values per column.
6.  A preview of the DataFrame after adding the time-based features ('year', 'month', 'day', 'hour').
7.  A preview of the grouped data by 'time'.
8.  A bar plot visualizing the relationship between 'T_25' and 'day'.

## **Visualizations**

The script generates the following visualization:

* **Bar Plot of T_25 vs Day:** A bar plot showing the temperature at 25m depth (`T_25`) on the y-axis and the day of the month (`day`) on the x-axis. This visualization helps to see how the temperature varies across the days present in the dataset.

## **Future Improvements**

* Perform more detailed time series analysis, such as trend analysis, seasonality decomposition, or forecasting.
* Explore relationships between 'T_25' and other potential environmental factors or operational data if available.
* Analyze data from different stations/platforms separately or together.
* Create more sophisticated visualizations to show temperature patterns over time and across different locations.
* Implement anomaly detection on the time series data.
