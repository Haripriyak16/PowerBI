# Zomato Power BI Report

This repository contains a comprehensive Power BI report developed for Zomato. The report consists of three main pages: an overview of key metrics, user performance analysis, and city-level performance metrics.

## Page 1: Main Metrics and Sales Trends

This page provides an overall view of key business metrics, sales trends, and insights into user activity.

### Features

- **Key Metrics:**
  - Total **Amount**, **Quantity**, **Orders**, and **Ratings**.
  
- **Slicers for Filtering:**
  - Filter data based on **Quantity** and **Amount**.
  - Slicers for **Veg Sales**, **Non-Veg Sales**, and **Other Sales** to categorize sales data.

- **Top N Filters:**
  - Dynamic slicers for Top N entries (Top 100, Top 50, Top 20, Top 10, and Top 5). The bar chart displays data based on the selected Top N filter.

- **Yearly Sales Trend:**
  - A line graph displaying the sales trend over the years to identify growth patterns.

### Screenshots

![Page 1 Screenshot](path/to/screenshot1.png)

---

## Page 2: User Performance Dashboard

This page provides insights into user activity and demographics through KPIs and visualizations.

### Features

- **KPIs:**
  - **Active Users**, **User Count**, **Orders**, and **Ratings**.
  
- **User Demographics:**
  - **Stacked Column Chart** displaying users by age group.
  - **Bar Charts**:
    - Gained users by gender.
    - Lost users by gender.

### Screenshots

![Page 2 Screenshot](path/to/screenshot2.png)

---

## Page 3: City Performance Dashboard

This page focuses on the performance of different cities based on various metrics.

### Features

- **Performance Table:**
  - Displays **Sale Value**, **Orders**, and **Active Users** for each city.

- **Clustered Bar Charts:**
  - **Sale Value by City**.
  - **Rating Count by City**.
  - **Active Users by City**.

### Screenshots

![Page 3 Screenshot](path/to/screenshot3.png)

---

## Top N Filters Implementation

This report includes dynamic Top N filters, allowing users to filter data by the top 5, 10, 20, 50, or 100 entries. The `RankTable` used for this purpose is created using the following DAX expression:

```DAX
RankTable = 
DATATABLE(
    "Sort", INTEGER, 
    "Type", STRING, 
    "Number", INTEGER,
    {
        {0, "All", 0},
        {1, "Top 5", 5},
        {2, "Top 10", 10},
        {3, "Top 20", 20},
        {4, "Top 50", 50},
        {5, "Top 100", 100}
    }
)
