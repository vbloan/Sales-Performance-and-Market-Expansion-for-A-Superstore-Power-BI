# Sales Performance and Market Expansion for A Superstore | Power BI
<img width="1000" height="500" alt="Cover project github" src="https://github.com/user-attachments/assets/b6c02727-037e-4cf2-bf27-5cbacdb79df7" /> <br>

**Author:** Vu Bich Loan <br>
**Date:** September 2025 <br>
**Tool Used:** BI <br>

## Table of Contents
1. [📌Background & Overview](#background--overview)
2. [📂Dataset Overview](#dataset-overview)
3. [📊Visualizations & Key Insights](#visualizations--key-insights)
4. [🔎Final Conclusion and Recommendations](#final-conclusion-and-recommendations)
---

## 📌Background & Overview
**📖What is this project about?** <br>
This project aims to build a Power BI dashboard using the Superstore dataset to provide a comprehensive analysis of sales performance. The goal is to provide senior managers with data-driven insights to: <br>
- Understand current business performance <br>
- Optimize market expansion strategies <br>
- Identify strategic products for growth <br>

**👤Who is this project for?** <br>
✔️ Data Analysts & Business Analysts <br>
✔️ Digital Marketing Teams <br>
✔️ Sale Manager, Sale Team <br>

**❓Business Questions:** <br>
✔️ What is the current performance of Superstore? <br>
✔️ Which markets should Superstore expand into to increase revenue and ROI? <br>
✔️ Which products should be prioritized for strategic growth? <br>

## 📂Dataset Overview
### Data Description
- Source: Kaggle <br>
- Size: The Orders table contains 5,901 records. <br>
- Format: CSV <br>
### Normalize data
- To fulfill the project's goal of delivering actionable business insights, I initiated a comprehensive data analysis process. This began with data modeling, a crucial step for ensuring the integrity and scalability of the analysis. <br>
- The initial dataset was provided as a single, large table where all information—from customer details to order specifics and product data—was consolidated. This structure presented a significant challenge for efficient analysis due to data redundancy and the difficulty in establishing a clear relationship between different entities. <br>
- To resolve this, I performed a data normalization process. This involved splitting the original table into multiple, separate tables, which were then structured according to the Star Schema model. This approach is fundamental to building an effective data model in Power BI, as it enhances query performance, reduces data redundancy, and simplifies the creation of relationships. <br>
- Besides, a DimDate table named `Calendar` is created to perform time-intelligence analysis and simplify and standardize date-related calculations. <br>
- The final data model consists of four key tables, categorized as either Fact or Dimension tables: <br>
  - `Customers`, `Products`, `Returns`, `Calendar`: Dimension tables <br>
  - `Orders`: Fact table <br>
- By implementing this star schema, the data model became more organized and efficient. It enabled the creation of clear relationships between tables, allowing for powerful time intelligence and cross-table analysis, which was essential for generating the insights presented in this dashboard. <br>
### Table Used & Relationships
**1. Table Used** <br>
The dataset consists of **5 main tables** used to analyze: <br>
**👥Customers**
<details>
<summary><strong>Table 1: Customers</strong></summary>
  
|**Column Name**    | **Description**                                           |
|-------------------|-----------------------------------------------------------|
| `Customer ID`     | Unique identifier for each customer                       |
| `Customer Name`   | Full name of the customer                                 |
| `Segment`         | Type of customer (Consumer, Corporate, Home Office)       |

</details> 

**📦Products**
<details>
<summary><strong>Table 2: Products</strong></summary>
  
|**Column Name**       | **Description**            |
|----------------------|----------------------------|
| `Product ID`         | Unique identifier for each product |
| `Category`           | Category of the product            |
| `Sub-Category`       | Sub-category of the product        |
| `Product Name`       | Name of product                    |

</details> 

**🔄Returns**
<details>
<summary><strong>Table 3: Returns</strong></summary>

|**Column Name**       | **Description**            |
|----------------------|----------------------------|
| `Order ID`           | Unique identifier for each order |
| `Returns`            | Indicates whether the order was returned <br> - 1 indicates that the order was returned. <br> - 0 indicates that the order was not returned |

</details> 

**📅Calendar**
<details>
<summary><strong>Table 4: Calendar</strong></summary>

|**Column Name**       | **Description**            |
|----------------------|----------------------------|
| `Date`               | A unique and continuous list of dates from 01/01/2019 to 31/12/2020 |

</details> 

**🛒Orders**
<details>
<summary><strong>Table 5: Orders</strong></summary>
  
|**Column Name**          | **Description**                      |
|-------------------------|--------------------------------------|
| `Order ID`              | Unique identifier for each order     |
| `Order Date`            | Order creation Date                  |
| `Ship Date`             | Date when order was shipped          |
| `Customer ID `          | Customer reference                   |
| `Country`, `Region`, `State`, `City` | Geographical location   |
| `Product ID`            | Product reference                    |
| `Sales`                 | Revenue generated from the order     |
| `Quantity`              | Number of items ordered              |
| `Profit`                | Profit earned from the order         |
| `Payment Mode`          | Mode of payment (COD, Online, Cards) |

</details> 

**2. Table Relationships**

<img width="676" height="321" alt="image" src="https://github.com/user-attachments/assets/9cde6ce7-cfa1-4840-8f9e-ddb903ebe7a9" /> <br>

| **From Table**    | **To Table**    | **Join Key**        | **Relationship Type**                                      |
|-------------------|-----------------|---------------------|------------------------------------------------------------|
| `Orders`          | `Customers`     | `Customer ID `      | Many-to-One (one customer made many orders)                |
| `Orders`          | `Products`      | `Product ID`        | Many-to-One (one product in many orders)
| `Orders`          | `Returns`       | `Order ID`          | Many-to-One ( a single order ID can appear on multiple rows in the `Orders` table (representing different products), but a full order return is consolidated into a single entry in the `Returns` table|
| `Orders`          | `Calendar`      | `Order Date` (from `Orders` table) <br> `Date` (from `Calendar` table) | Many-to-One (many orders are created on a day) |

## 📊Visualizations & Key Insights <br>
### 📍Page 1: Overview <br>

<img width="634" height="358" alt="image" src="https://github.com/user-attachments/assets/ed7042ba-7c0e-405e-abb7-d790731c0b83" /> <br>

**🎯Target:** Analyze current sales performance <br>
**💡Key visuals and Insights:** <br>
**1. General remarks** <br>
- Revenue reached $1.57M and profit hit $175.26K, both increasing more than 100% YoY. → Growth was primarily driven by increased order volume, not by improved operational efficiency (profit margin decreased 22.75% YoY). <br>
- Customers increased only 21.16%, but orders surged 128.37%; Average Order Value (AOV) slightly increased at 21.42%. → Indicates strong repeat purchase behavior, with smaller but more frequent orders. <br>

**2. Revenue and Profit Margin by Segment** <br>
- The Consumer segment generated $0.75M, the highest among all segments. <br>
- Among segments, profit margin fluctuated from 11% to 12%. → Indicates steady demand. <br>

**3. Revenue and Profit Margin by Category** <br>
- Office-supplier products generated the highest revenue. → Suggests customers have a strong preference for office-supplier products. <br>
- However, tech products showed the highest profit margin → Indicated that there is potential for growth. <br>

**4. Revenue by Region and Category** <br>
- The West region showed the highest revenue. <br>
- Office-supplier products generated the highest revenue across all regions. → Suggests customers have a strong preference for office-supplier products over other categories. <br>

**5. Total Orders and Average Order Value (AOV) by Region** <br>
The number of orders was unevenly distributed across the regions. The West region had the highest number of orders at 961, followed by the East (844 orders), Central (711 orders), and South (487 orders). Despite the differences in order volume, the Average Order Value (AOV) across all regions was quite consistent, ranging from $475-$545 per order. <br>

### 📍Page 2: Market Analysis <br>

<img width="633" height="358" alt="image" src="https://github.com/user-attachments/assets/3a572b01-e25b-46a1-8d80-e57938ef0efe" /> <br>

**🎯Target:** Analyze sales performance among regions <br>
**💡Key visuals and Insights:** <br>
**1. Business Performance among regions** <br>
- Revenue grew across all regions in 2020. <br>
- Meanwhile, from 2019 to 2020, Profit Margin in the Central and South regions decreased significantly. In contrast, the East and West regions maintained a stable profit margin over the same period. <br>

**2.  Number of customers by Region** <br>
- New customers grew at a steady rate across all regions. However, there was a significant disparity in the number of returning customers. The West region had the highest number of returning customers (276), which indicates the strong performance of its customer loyalty programs.

**3. Total profit by Region and Category** <br>
- The West region showed the highest profit among the 4 regions. <br>
- Office-supplier products generated the highest profit across all regions. → Suggests that office-supplier products have high profitability over other categories. <br>

**4. Top states have the highest revenue** <br>
- California topped the revenue list, and it comes from the West region. <br>

**5. Order Quantity and Return Quantity by Region** <br>
- The West region topped the number of orders, returns, and return rate list. <br>
- The West region led the highest return rate (7.28%). → Other regions had stable return rates (1–3%). <br>

### 📍Page 3: Product Analysis <br>

<img width="634" height="359" alt="image" src="https://github.com/user-attachments/assets/3c0f9b9f-421d-4434-8bc4-cd37da3b2328" /> <br>

**🎯Target:** Analyze sales performance among products <br>
**💡Key visuals and Insights:** <br>
**1. Revenue and Profit Margin by Subcategory** <br>
- Phones lead in revenue, Envelopes and Fasteners lag behind in revenue. <br>
- Copier (71.61%), Accessories (20.72%), and Envelopes (21.21%) stand out for profit margins. While Table (-9.3%), Suppliers (-4.5%), and Bookcases (-0.06%) underperform with negative profit margins. <br>

**2. Top Subcategory has the highest profit** <br>
- Copiers and Accessories stand out as the most profitable items, generating $18K and $12K in profit, respectively. In contrast, Bookcases showed no profit, while both Supplies and Tables recorded a net loss. <br>

**3. Orders, Customers, Returns Rate by Subcategory** <br>
Although Copiers and Accessories are our most profitable items, the number of customers and orders is only average. In fact, Copiers have the lowest number of customers and orders among all subcategories. This suggests that these products have a very high profit margin per unit, compensating for their low sales volume. <br>

**4. Total Profit by Segment and Category** <br>
- Consumer is the largest and most profitable customer segment, generating the highest total profit. <br>
- The Technology category is the top profit driver across all customer segments. This indicates that technology products are highly profitable regardless of who the customer is. <br>

**5. Revenue and Profit by Ship Mode** <br>
- Standard Class is the most popular shipping method, generating the highest revenue and profit. → Shows that most customers prioritize cost over speed. <br>

## 🔎Final Conclusion and Recommendations

| **Strategy** | **Insights** | **Recommendations** |
|--------------|--------------|---------------------|
| **Market Expansion Strategy** | The West region is the key driver of business growth, combining strong profitability and customer loyalty. However, its high return rate poses a risk to sustainable performance. | - Strengthen return management and quality control in the West to reduce loss from returns. <br> -Leverage customer loyalty in the West by expanding retention programs to other regions. <br> - Replicate best practices from California’s sales strategy to boost revenue in underperforming states. |
| **Product Portfolio Optimization** | High profitability is concentrated in Copiers, Accessories, and the Technology category, while several subcategories (Tables, Supplies, Bookcases) weaken overall margins. | - Scale up Copiers and Accessories by expanding reach to more customers. <br> -  Reassess or phase out consistently unprofitable subcategories. <br> -  Leverage the Technology category’s strong performance to capture broader market opportunities. <br> - Maintain focus on Standard Class while testing premium delivery options for upselling. |
| **Operational Efficiency** | On the operational side, Standard Class shipping and COD payments dominate, reflecting customer preference for cost efficiency and convenience, but also creating pressure on logistics and cash-handling processes. | On the operational side, Standard Class shipping and COD payments dominate, reflecting customer preference for cost efficiency and convenience, but also creating pressure on logistics and cash-handling processes. |



