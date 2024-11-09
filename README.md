# CUSTOMER SEGMENTATION ANALYSIS

In the competitive landscape of **e-commerce**, understanding customer behavior is crucial for driving growth, increasing sales, and enhancing customer retention. This project, "Customer Segmentation Analysis," uses **customer transaction data** to segment customers, identify purchasing patterns, and derive actionable insights using **Excel** that will help the business **develop targeted marketing strategies**and **improve decision-making processes**.

<br>

## TABLE OF CONTENT

- [Project Overview](#project_overview)
- [Data Source](#data_source)
- [Data Cleaning](#data_cleaning)
- [RFM Analysis]()
- [Customer Behavior Analysis](#customer_behavior_analysis)
- [Recommendations](#recommendations)
- [Conclusion](#conclusion)
  
<br>

## PROJECT OVERVIEW

The objective of this project is to **segment customers** based on their **purchasing behavior**, **preferences**, and **demographic information**. The segmentation will help the company understand different customer groups and develop strategies to increase customer engagement and revenue.

Key Questions/Requirements:

- How can we classify customers based on their **purchasing behavior**? 

- What are the main **demographic** and **transactional characteristics** of each customer segment?

- What is the **average purchase amount**, and how does it vary across segments?

- Which **payment methods** and **product categories** are preferred by different customer groups?

<br>

## DATA SOURCE

The data for this project was obtained from **Kaggle.com**, which provides various fictitious datasets for data analysis projects. The dataset contains records of **customer transactions in an e-commerce store**, including details such as Customer ID, Purchase Date, Product Category, Product Price, Units Sold, Total Purchase Amount, Payment Method, Customer Age, Gender, Returns, and Age Group.

<br>

<img width="608" alt="EXCEL DATASET" src="https://github.com/user-attachments/assets/2cf0b3cc-4935-49dd-ad94-0822a417cf17">

<br>

## DATA CLEANING

In preparing the dataset for analysis, I followed a structured data cleaning process to ensure **data quality** and **accuracy**. Here are the key steps I took:

**1. Check for Missing Values:**

- I carefully went through each column, applying filters to easily spot any missing values.

- For columns like **Returns**, where blanks might represent non-returned items, I decided to replace any **blank cells** with a **0**.

- To do this, I selected the Returns column, pressed ``Ctrl + H`` to open the Replace dialog, left the **Find what** field **"empty"**, and entered **"0"** in the **Replace with** field. I then clicked **Replace All** to quickly fill in the blanks.

**2. Convert Data Types:**

- I wanted to ensure that the **Purchase Date** column was in the correct **date format** for accurate date-based analysis.

- To standardize the date format, I selected the Purchase Date column, navigated to **Home > Number Format**, and chose **"Short Date"** to apply a consistent date format.

**3. Remove Duplicates:**

- To maintain the integrity of the data, I checked for any duplicate entries that could skew the analysis.

- I selected the entire dataset, went to **Data > Remove Duplicates**, and made sure all columns were selected. This step helped me eliminate any redundant records, ensuring that each customer transaction was **unique**.

By performing these steps, I was able to ensure that the data was **clean, accurate,** and **ready for meaningful analysis**.

<br>

## RFM ANALYSIS

After completing data cleaning, I proceeded with an RFM analysis (Recency, Frequency, and Monetary value), a method that helps identify the most valuable customers by evaluating their purchasing behaviors. This analysis offers a practical approach to segmentation, focusing on how customers shop rather than their demographic characteristics. Here is how each component is defined:

- **Recency**: Measures how recently a customer made a purchase. Calculated as the number of days since the customer’s last purchase.
- **Frequency**: Indicates how often a customer makes purchases. Counted as the total number of purchases per customer.
- **Monetary**: Represents the total amount a customer spends. Summed as the total purchase value for each customer.

<br>

### Step 1: Creating Recency, Frequency, and Monetary Columns

To build the RFM model, I first created the respective columns by setting up a Pivot Table:

1. **Pivot Table Creation**:
   - Selected the dataset and went to `Insert > PivotTable` to create a new pivot table in a separate worksheet.
2. **Configure the Pivot Table**:
   - Dragged `Customer ID` to the Rows area.
   - For **Recency**:
     - Added `Purchase Date` to the Values area and set its aggregation to `Max` to identify the most recent purchase date.
     - Renamed the field as “Last Purchase Date.”
   - For **Frequency**:
     - Added `Customer ID` again to the Values area and changed the aggregation to `Count` to show purchase frequency.
     - Renamed this field as “Frequency.”
   - For **Monetary**:
     - Added `Total Purchase Amount` to the Values area and set the aggregation to `Sum` to calculate the total spend.
     - Renamed the field as “Monetary.”

3. **Calculating Recency**:
   - Created a new column adjacent to the pivot table named “Recency.”
   - In cell E2, I entered the formula `=TODAY() - B2` to calculate the days since the last purchase.
   - Dragged the formula down to populate the Recency column for all rows.

<br>

### Step 2: Calculating Percentile Ranks for RFM Segmentation

To standardize the RFM metrics, I created percentile rank columns using the `PERCENTRANK.EXC` function:

1. **Recency Rank**:
   - Created a column titled “Recency Rank” in cell F1.
   - Applied the formula `=PERCENTRANK.EXC($E$2:$E$49662, E2, 1)*10` in cell F2 and filled it down the column.

2. **Frequency Rank**:
   - Created a column titled “Frequency Rank” in cell G1.
   - Used the formula `=PERCENTRANK.EXC($C$2:$C$49662, C2, 1)*10` in cell G2 and filled it down.

3. **Monetary Rank**:
   - Created a column titled “Monetary Rank” in cell H1.
   - Entered the formula `=PERCENTRANK.EXC($D$2:$D$49662, D2, 1)*10` in cell H2 and filled it down.

<br>

### Step 3: Calculating the Combined RFM Score

To summarize the RFM data:

1. **Create an RFM Score column**:
   - Titled cell I1 as “RFM Score.”
   - Used the formula `=F2 + G2 + H2` in cell I2 to combine the ranks and filled it down for all entries.

<br>

### Step 4: Segmenting Customers Based on RFM Score

To classify customers into segments:

1. **Create a Segment column**:
   - Named cell J1 as “Segment.”
   - Entered the formula `=IF(I2 >= 24, "Top", IF(I2 >= 18, "High", IF(I2 >= 12, "Medium", IF(I2 >= 6, "Low", "Bottom"))))` in cell J2 and applied it to the rest of the rows.

This process allowed me to generate key columns: Recency, Frequency, Monetary, their respective ranks, the combined RFM Score, and customer segments. Each value provides insights:

- **Recency**: Lower values indicate more recent activity.
- **Frequency**: Higher counts show more frequent purchases.
- **Monetary**: Higher totals represent greater customer spending.
- **RFM Score**: Combined scores reveal overall customer value.
- **Segment**: Categorizes customers into actionable groups, such as “Top” or “At-Risk.”

<br>
<br>

<img width="548" alt="RFM 1" src="https://github.com/user-attachments/assets/b7da3180-5627-4d80-ba4b-f8ad1f0ac42c">

<br>
<br>
<br>

<img width="654" alt="RFM 2" src="https://github.com/user-attachments/assets/ee029c5e-bc01-4e21-a6d4-95b8ac021d38">

<br>
<br>

After adding the necessary columns for the RFM analysis, I proceeded to analyze the data using several **visualization charts**: a column chart illustrating the number of customers per segment, a pie chart representing the total purchase distribution by segment, and a line chart displaying the average RFM scores across segments. These charts collectively offer a clear view of **customer patterns** and their contributions to the business, aiding in **strategic decision-making**. These visualizations are detailed below: 

#### 1. Customer Count by Segment(Column chart)

The column chart displays the distribution of customers across different segments. It highlights that the **'High'** segment has the **largest** customer base, followed by the **'Medium'** and **'Low'** segments, while the **'Bottom'** and **'Top'** segments have the **fewest** customers. This distribution provides insight into the concentration of customers in each category.

<br>

#### 2. Total Purchase Amount Distribution by Segment(Pie chart)

The pie chart illustrates the share of total purchases made by customers in each segment. The **'High'** and **'Medium'** segments contribute the **largest portions**, indicating they are responsible for the majority of revenue. The **'Low', 'Top'**, and **'Bottom'** segments contribute **smaller shares**, reflecting less significant purchase amounts from these groups.

<br>

#### 3. Average RFM Scores by Segment(Line chart)

The line chart illustrates the average recency, frequency, and monetary scores for each customer segment. The **'High'** and **'Top'** segments show the **highest scores** across all three dimensions, indicating strong purchasing behavior. The **'Bottom'** segment has the **lowest scores**, reflecting minimal engagement, while the **'Medium'** segment shows balanced but **moderate scores**. The **'Low'** segment has a **noticeable dip**, particularly in **frequency**, indicating **less frequent purchases.**

<br>

## CUSTOMER BEHAVIOR ANALYSIS

The "Customer Behavior Analysis" section provides insights into purchasing trends and preferences among different customer demographics and behaviors. This analysis includes detailed visualizations that reveal spending habits by age and gender, product preferences, revenue contributions by category, and payment method choices. The charts collectively **help illustrate key behavioral patterns**, offering a comprehensive **understanding of customer interactions** and **purchasing dynamics**. These visualizations are detailed below:

<br>

#### 1. Purchasing Behavior by Age Group:

The bar chart shows that **Seniors** are the **highest spenders**, followed closely by Adults. **Young Adults** have the **lowest total purchase amount**.
 
#### 2. Purchasing Behavior by Gender:

The pie chart shows that purchasing behavior by gender is nearly **equal**, with Males slightly leading in total purchase amount compared to Females.

#### 3. Product Preferences by Gender:

The stacked bar chart shows that both males and females have very **similar product preferences** across categories. The **total purchase amounts are nearly identical** for each gender in categories like Books, Clothing, Electronics, and Home products.

#### 4. Revenue Contribution by Category:

The bar chart shows that **Home products** contribute the **most** to revenue, followed closely by Clothing and Electronics. **Books** contribute the **least**, but still represent a significant portion of the total revenue.

#### 5. Payment Method Preferences:

The pie chart shows that **Credit Card** is the **most preferred** payment method, accounting for the largest share of total purchase amounts, closely followed by PayPal. **Cash** is the **least preferred** method among customers.

#### 6. Spending Patterns by Payment Method:

The stacked bar chart illustrates spending patterns across different product categories (Books, Clothing, Electronics, Home) based on the payment method used (Cash, Credit Card, PayPal).

The distribution of spending across product categories is consistent regardless of the payment method. Each payment method shows **similar patterns**, with **Home** and **Electronics** being the **dominant categories**, followed by Clothing and Books.

<br>
<br>

<img width="551" alt="EXCEL DASHBOARD" src="https://github.com/user-attachments/assets/1aa061a4-5d65-4610-b7d9-ab01dae1a831">

<br>
<br>

## RECOMMENDATIONS

Based on the comprehensive analysis of customer behavior and segmentation, the following actionable recommendations are proposed:

1. **Prioritize High and Medium Segments for Engagement:** Given that the 'High' and 'Medium' customer segments account for the majority of the total purchase amount and customer base, targeted marketing campaigns should focus on retaining and nurturing these valuable groups. **Personalized offers, loyalty programs**, and **exclusive promotions** could further enhance their engagement.

2. **Develop Strategies for Low and Bottom Segments:** While the 'Low' and 'Bottom' segments contribute less to revenue, strategic efforts such as **re-engagement campaigns** and **tailored incentives** can encourage more frequent purchases and higher spending. **Targeted email marketing, discounts**, or **product recommendations** could help convert these groups into higher-value customers.

3. **Capitalize on Demographic Insights:** Seniors are the highest spenders, followed by Adults. **Marketing strategies** should be tailored to cater to these age groups’ preferences. Additionally, since purchasing behavior by gender is nearly balanced, **promotions** and **product recommendations** should appeal to both male and female customers equally.

4. **Enhance Payment Method Options:** Credit Card and PayPal are the most preferred payment methods, with Cash being less favored. Ensure a seamless checkout experience for card and digital payment users by **optimizing the payment process** and **offering flexible payment options** to increase convenience and customer satisfaction.

5. **Focus on High-Performing Product Categories:** Home and Clothing products contribute the most to revenue. Consider **expanding the product range** within these categories or **introducing complementary products**. **Promotional campaigns** and **bundling options** for these top categories could further boost sales.

6. **Monitor Spending Patterns by Payment Method:** The analysis of spending patterns reveals consistent distribution across product categories regardless of the payment method used. Leverage this insight to **offer targeted promotions** tied to preferred payment methods, such as **cashback offers** or **discounts** for Credit Card and PayPal transactions.

<br>

## CONCLUSION

This Customer Segmentation Analysis has provided a **clear understanding of purchasing behavior** and **customer preferences** in an e-commerce setting. Through 'RFM analysis', customers were effectively segmented into actionable groups, revealing that 'High' and 'Medium' segments are the most valuable, while 'Bottom' and 'Low' segments present opportunities for growth through targeted re-engagement strategies. The 'Customer Behavior Analysis' further highlighted key insights, such as **age group spending trends**, **gender purchasing behavior**, and **product category performance**.

By leveraging these findings, the business can develop **data-driven marketing strategies to engage key customer segments, optimize product offerings**, and **enhance customer experiences**. This analysis not only aids in strategic decision-making but also sets a strong foundation for **boosting customer loyalty, maximizing revenue,** and **sustaining business growth**.



