# Sales Performance and Market Expansion for A Superstore | Power BI
<img width="1000" height="500" alt="Cover project github" src="https://github.com/user-attachments/assets/b6c02727-037e-4cf2-bf27-5cbacdb79df7" /> <br>

**Author:** Vu Bich Loan <br>
**Date:** September 2025 <br>
**Tool Used:** BI <br>

## Table of Contents
1. [📌Background & Overview](#background--overview)
2. [📂Dataset Overview](#dataset-overview)
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
| `Orders`          | `Customers`     | `Customer ID `      | Many-to-One
| `Orders`          | `Products`      | `Product ID`        | Many-to-One
| `Orders`          | `Returns`       | `Order ID`          | 
| `Orders`          | `Calendar`      | `Order Date` (from `Orders` table) <br> `Date` (from `Calendar` table) |




