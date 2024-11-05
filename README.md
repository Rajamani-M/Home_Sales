
# Home Sales Analysis with SparkSQL

This project uses SparkSQL to analyze home sales data and calculate key metrics. The analysis includes creating temporary views, caching data for performance optimization, partitioning data for efficient storage, and comparing runtimes on cached versus uncached queries. This project was developed in Google Colab.

## Table of Contents
- [Project Overview](#project-overview)
- [Technologies Used](#technologies-used)
- [Analysis Steps](#analysis-steps)
- [Results](#results)

## Project Overview

The goal of this project is to answer key questions about home sales using SparkSQL. The data is processed, cached, and partitioned to optimize performance, and insights are derived by querying various aspects of the home sales dataset, such as average prices based on different conditions.

## Technologies Used

- **PySpark**: For data processing, querying, and performance optimization.
- **Parquet**: For efficient storage of partitioned data.
- **Google Colab**: For running and developing the project in an interactive environment.
- **GitHub**: For version control and code hosting.

## Analysis Steps

### 1. Initial Data Setup

- **Data Load**: The `home_sales_revised.csv` file is loaded into a Spark DataFrame.
- **Temporary Table**: The DataFrame is registered as a temporary table named `home_sales`.

### 2. Analysis and Queries

Using SparkSQL, the following analyses were conducted:

1. **Average Price of Four-Bedroom Houses Sold per Year**  
   Calculate the average price for four-bedroom homes sold each year, rounded to two decimal places.

2. **Average Price for Homes Built per Year with Specific Attributes**  
   For each year built, calculate the average price of homes with:
   - 3 bedrooms and 3 bathrooms.
   - 3 bedrooms, 3 bathrooms, 2 floors, and a living area of at least 2,000 square feet.

3. **Average Price per "View" Rating**  
   Calculate the average price per "view" rating, rounded to two decimal places, for homes with an average price of at least $350,000. Runtime for this query was recorded and compared on cached versus uncached data.

### 3. Caching and Performance Optimization

- **Cache the Table**: The `home_sales` temporary table was cached to improve performance for repeated queries.
- **Runtime Comparison**: The runtime of the "view" rating query was measured before and after caching to demonstrate performance improvements.

### 4. Partitioning and Parquet Format

- **Partition by `date_built`**: The dataset was partitioned by the `date_built` column and saved in Parquet format for efficient storage.
- **Parquet Temporary Table**: The Parquet data was loaded into a new DataFrame and registered as a temporary table for querying.

### 5. Uncache and Clean Up

- **Uncache Table**: The `home_sales` table was uncached to free up memory.
- **Verification**: The uncached status of the table was confirmed.

## Results

1. **Average Prices by Year of Sale and Build**  
   Generated tables showing the average price for four-bedroom homes by year of sale and for homes with specific attributes by year built.

2. **Performance Gains with Caching**  
   Caching the table reduced query runtime significantly, as shown in the runtime comparisons.

3. **Partitioned Data Storage**  
   Partitioning the data by `date_built` and storing it in Parquet format demonstrated efficient storage and querying for specific year-built segments.

## Conclusion

This project demonstrates the power of SparkSQL for efficient data analysis on large datasets. By leveraging caching, partitioning, and Parquet formatting, we optimized performance and demonstrated how these techniques can accelerate query processing times.
