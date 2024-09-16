# Zomato Power BI Report

This repository contains a comprehensive Power BI report developed for Zomato. The report is designed to provide insights into key business metrics, user performance, and city-wise performance analytics. It comprises three main pages: an overview of sales trends, a user performance dashboard, and a city-level performance dashboard. The report also features dynamic Top N filters for flexible data analysis.

---

## Page 1: Main Metrics and Sales Trends

The first page of the report gives an overview of key business metrics, including sales, quantity, orders, and user ratings. It also includes several slicers to filter the data, along with visual elements to present trends and top-performing segments.

### Features

- **Key Metrics Section:**
  - The metrics shown here include:
    - **Amount:** Total sales amount.
    - **Quantity:** Number of items sold.
    - **Orders:** Total number of orders placed.
    - **Ratings:** Overall user ratings.
    
- **Slicers for Filtering:**
  - **Quantity and Amount Slicers:** Allows filtering the data based on the number of items sold and the total amount.
  - **Sales Categories:** There are slicers for different categories of sales:
    - **Veg Sales**, **Non-Veg Sales**, and **Other Sales**, giving the user the flexibility to analyze specific types of sales.

- **Top N Filters:**
  - There are dynamic Top N filters implemented using a DAX rank table. The available filters include:
    - Top 100, Top 50, Top 20, Top 10, and Top 5 countries by sales.
    - The corresponding bar chart updates based on the selected Top N filter to display the top-performing countries.

- **Yearly Sales Trend Line Graph:**
  - A line graph that illustrates the trend of sales over time, allowing users to spot patterns and identify growth or decline on a yearly basis.

### Interaction
Users can interact with this page by selecting different slicers (e.g., by sales categories or by Top N) to filter the data dynamically. The visuals will update in real-time based on the selections made.

### Screenshots

![Page 1 Screenshot](path/to/screenshot1.png)

---

## Page 2: User Performance Dashboard

The second page focuses on analyzing user performance by showcasing KPIs related to user activity, orders, and ratings. Additionally, it provides insights into the demographics of users, such as age and gender.

### Features

- **KPIs (Key Performance Indicators):**
  - The following KPIs are displayed:
    - **Active Users:** The number of users actively interacting with the platform.
    - **User Count:** The total number of registered users.
    - **Orders:** The total number of orders placed by users.
    - **Ratings:** The average ratings provided by users.

- **User Demographics:**
  - A **Stacked Column Chart** is used to break down users by age group. This allows for analysis of which age groups are the most active on the platform.
  
- **Gained and Lost Users by Gender:**
  - Two bar charts display user retention and loss:
    - **Gained Users by Gender:** This chart shows how many new users have been added over time, broken down by gender.
    - **Lost Users by Gender:** Similarly, this chart shows the number of users who have stopped using the platform, also broken down by gender.

### Interaction
Users can monitor KPIs to get an instant overview of user activity. They can explore demographic insights and trends based on the age and gender data visualized in the charts.

### Screenshots

![Page 2 Screenshot](path/to/screenshot2.png)

---

## Page 3: City Performance Dashboard

The third page offers insights into how Zomato is performing at a city level. It displays important metrics like sales value, order count, and active users across different cities.

### Features

- **Performance Table:**
  - A comprehensive table lists key performance indicators for each city, including:
    - **Sale Value:** Total sales value generated from each city.
    - **Orders:** The total number of orders placed from each city.
    - **Active Users:** The number of active users in each city.

- **Clustered Bar Charts:**
  - Three clustered bar charts offer a visual comparison of city performance:
    - **Sale Value by City:** Visualizes the total sales value generated from different cities.
    - **Rating Count by City:** Shows the number of user ratings submitted from each city.
    - **Active Users by City:** Displays the number of active users in each city.

### Interaction
Users can explore the city-level performance data to analyze how different cities contribute to overall performance. The bar charts make it easy to compare metrics like sales value, user ratings, and active users across cities.

### Screenshots

![Page 3 Screenshot](path/to/screenshot3.png)

---

## Top N Filters Implementation

To allow users to focus on specific top-performing segments, dynamic Top N filters have been implemented in this report. These filters enable users to analyze data for the top 5, 10, 20, 50, or 100 performing entries. This is achieved using a custom rank table created with DAX.

### DAX Code for Rank Table

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
