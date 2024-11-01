# Customer Segmentation Analysis

In the competitive landscape of e-commerce, understanding customer behavior is crucial for driving growth, increasing sales, and enhancing customer retention. This project, "Customer Segmentation Analysis," uses customer transaction data to segment customers, identify purchasing patterns, and derive actionable insights that will help the business develop targeted marketing strategies and improve decision-making processes.

## Project Overview

- Objective: The objective of this project is to segment customers based on their purchasing behavior, preferences, and demographic information. The segmentation will help the company understand different customer groups and develop strategies to increase customer engagement and revenue.

Key Questions/Requirements:

How can we classify customers based on their buying behavior? 

What are the main demographic and transactional characteristics of each customer segment?

What is the average purchase amount, and how does it vary across segments?

Which payment methods and product categories are preferred by different customer groups?

## Data Source

The data for this project was obtained from **Kaggle.com**, which provides various fictitious datasets for data analysis projects. The dataset contains records of customer transactions in an e-commerce store, including details such as Customer ID, Purchase Date, Product Category, Product Price, Units Sold, Total Purchase Amount, Payment Method, Customer Age, Gender, Returns, and Age Group.

## Data Cleaning

The data underwent several steps of cleaning to prepare it for analysis. This included:

Removing Duplicates: Any duplicate entries were identified and removed to ensure data integrity.

Handling Missing Values: Missing values were either filled (if appropriate) or excluded from analysis to maintain accuracy.

Standardizing Data Formats: Fields such as dates and numerical values were standardized for consistency.

## Data Preparation

Several columns were added to enhance the dataset for segmentation analysis and to facilitate additional insights. Below are the calculated columns and their respective formulas:

- Recency: Represents the number of days since the last purchase by each customer.

``Formula: =TODAY() - [Last Purchase Date]``

- Frequency: Counts the total number of transactions per customer.

``Formula: =COUNTIF([Customer ID Range], [Customer ID])``

- Monetary: Calculates the total purchase amount for each customer.

``Formula: =SUMIF([Customer ID Range], [Customer ID], [Total Purchase Amount])``

- RFM Score: Combines Recency, Frequency, and Monetary ranks to create an overall RFM score for each customer.

``Formula: =RANK([Recency Rank]) + RANK([Frequency Rank]) + RANK([Monetary Rank])``

- Segment: Segments customers based on RFM score into categories such as High, Medium, Low, etc.

## Analysis

### Exploratory Data Analysis (EDA)

- Descriptive Statistics:

Analyzed key metrics, such as mean, median, and standard deviation, for Total Purchase Amount, Recency, Frequency, and Customer Age.

- Regression Analysis:

A regression analysis was performed to understand the relationship between customer demographics (such as age) and their purchase amounts.

## Visualizations

The analysis involved various charts and visualizations to illustrate customer segmentation and preferences:

- Customer Segments (Bar Chart): Displays the distribution of customers across different segments (Bottom, Low, Medium, High, Top).

- Purchasing Behavior by Age Group (Column Chart): Shows the purchase amounts segmented by age groups (Adults, Seniors, Young Adults).

- Payment Method Preferences (Pie Chart): Illustrates the preferred payment methods (Cash, Credit Card, PayPal) used by customers.

- Total Purchase Amount Distribution by Segment (Pie Chart): Displays the distribution of total purchase amount by customer segment.

- Purchasing Behavior by Gender (Pie Chart): Compares the total purchase amount by gender.

- Spending Patterns by Payment Method (Stacked Column Chart): Shows how spending varies across different payment methods and product categories.

- Average RFM Scores by Segment (Line Chart): Compares the average RFM scores across different segments for Recency, Frequency, and Monetary values.

- Product Preferences by Gender (Stacked Column Chart): Illustrates preferences for different product categories across gender groups.

- Revenue Contribution by Category (Column Chart): Shows the revenue contribution of each product category.

## Insights

Based on the exploratory data analysis and visualizations, the following insights were derived:

- High and Medium Segments: A significant portion of customers fall within the "High" and "Medium" segments, indicating strong engagement among these groups.

- Preferred Product Categories: The "Home" and "Electronics" categories generate the highest revenue, suggesting that these categories have strong customer interest.

- Payment Methods: Credit cards and PayPal are the most popular payment methods, indicating that customers prefer cashless transactions.

- Age-Based Purchasing Behavior: Adults and Seniors represent the majority of the revenue contribution, with Young Adults showing lower purchasing activity.

- Gender-Based Preferences: Both male and female customers have similar preferences for product categories, with slight differences in their choices.

## Recommendations

Based on the insights gathered, the following recommendations are suggested to help the business enhance its strategies:

- Target High and Medium Segments: Focus marketing efforts on the "High" and "Medium" segments by offering loyalty rewards and exclusive promotions, as these segments are highly engaged.

- Promote Top Product Categories: Increase the visibility and marketing of "Home" and "Electronics" products through targeted ads, as they contribute significantly to the total revenue.

-Cashless Payment Options: Continue to promote credit card and PayPal options while exploring other digital payment methods to enhance customer convenience.

- Engage Younger Customers: Develop targeted marketing campaigns for young adults, perhaps with promotions, product bundles, or social media engagement to increase their purchase activity.

- Tailor Gender-Based Promotions: Create gender-specific marketing campaigns to attract male and female customers by highlighting their product preferences.

## Conclusion

The Customer Segmentation Analysis provides valuable insights into customer behavior and preferences in an e-commerce setting. By understanding key customer segments, their payment preferences, and product choices, the business can make informed decisions to improve customer retention and boost revenue. This dashboard serves as a foundation for targeted marketing, customer engagement strategies, and a deeper understanding of customer demographics.

