# Brazilian E-Commerce Sales Analysis

An end-to-end e-commerce sales analysis project using Microsoft Excel, Power Query, Power Pivot, and DAX, based on the **Brazilian E-Commerce Public Dataset by Olist**, sourced from Kaggle.

The project transforms raw transactional data into a structured analytical model and interactive dashboard designed to evaluate sales performance, customer behavior, product trends, seller performance, payment activity, and delivery operations.

**Dataset Source:** [Brazilian E-Commerce Public Dataset by Olist – Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

## 📌 Problem Statement

E-commerce platforms generate large volumes of transactional data across orders, customers, products, sellers, payments, and deliveries. Without proper analysis, it can be difficult to extract meaningful insights from this data and understand overall business performance.

This project aims to transform the raw Brazilian E-Commerce Public Dataset by Olist into a structured analytical model and interactive dashboard that can be used to evaluate sales performance, customer behavior, product trends, seller performance, payment activity, and delivery operations.

The analysis is designed to turn raw transactional data into actionable insights that can support data-driven business decisions.

## 🎯 Project Objectives

The main objectives of this project are to:

- Analyze revenue and order volume trends over time.
- Identify top- and underperforming product categories based on revenue and sales volume.
- Examine customer growth and repeat purchasing behavior.
- Evaluate seller performance across different regions.
- Analyze payment behavior and its contribution to revenue.
- Assess order processing and delivery performance, including delivery timelines and delays.

Perfect. Next is **Dataset & Source**.

markdown
## 📂 Dataset & Source

The analysis was conducted using the **Brazilian E-Commerce Public Dataset by Olist**, a publicly available dataset containing transactional data from the Brazilian e-commerce platform Olist.

### Dataset Source

**Kaggle:** [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

### Tables Used

The project incorporated the following relational tables:

- Orders
- Order Items
- Customers
- Products
- Sellers
- Payments
- Reviews

The **Geolocation** table was excluded because the analysis did not focus on spatial mapping, while the **Product Category Translation** table was excluded to keep the workflow focused on the core analytical requirements.

## 🗂️ Data Model & Structure

The dataset was transformed into a **Power Pivot star schema** to create a structured and efficient analytical model.

### Fact Tables

- **Orders** — Central transaction hub containing order-level information.
- **Order Items** — Lowest-grain fact table, with one row representing a product item within an order.

### Dimension Tables

- **Customers** — Customer information and location details.
- **Products** — Product attributes and categories.
- **Sellers** — Seller information and location details.
- **Payments** — Payment methods and transaction values.
- **Reviews** — Customer review information.
- **Date Table** — Calendar attributes used for time-based analysis.

### Key Relationships

The **Orders** table connects to Customers, Payments, Reviews, and Order Items through `order_id`.

The **Order Items** table connects to Products and Sellers through `product_id` and `seller_id`.

The **Date Table** connects to Orders using the order purchase date, enabling time-based analysis.

The model was designed to maintain clear relationships between transactional and descriptive data while avoiding unnecessary fact-to-fact relationships.


## 🧹 Data Cleaning & Transformation

The raw dataset was cleaned and transformed using **Microsoft Power Query** before being loaded into the Power Pivot data model.

The main transformation steps included:

- Standardized key columns and converted them to text where appropriate.
- Applied appropriate numeric data types to price, freight, and payment fields.
- Standardized date and time formats across the dataset.
- Trimmed text fields and checked for inconsistencies or misspellings.
- Preserved null delivery dates where they represented orders that had not been delivered, such as canceled or processing orders.
- Created a **Days to Delivery** calculation based on purchase and actual delivery dates.
- Created **Delay Days** to measure the difference between actual and estimated delivery dates.
- Created a **Delivery Flag** to classify delivered orders as early/on-time or late.
- Added time-based fields such as **Year** and **Month Name** from the purchase date.

These transformations prepared the data for consistent analysis and ensured that the Power Pivot model could support reliable calculations and interactive dashboard filtering.

## 📊 Analysis & KPI Framework

The analysis was primarily standardized around the **Order Items** fact table, which represents the lowest level of transaction detail. This ensured consistent filtering and aggregation across product, customer, seller, and order-related analysis.

### Core KPIs

- **Total Revenue** — Product-level revenue calculated from order item prices.
- **Total Orders** — Distinct count of orders.
- **Total Customers** — Distinct count of customers.
- **Active Sellers** — Distinct count of sellers.
- **Quantity Sold** — Number of order item records.
- **Average Order Value (AOV)** — Product revenue divided by total orders.
- **Total Shipping Cost** — Total shipping cost associated with order items.
- **Total Payment** — Total payment value recorded in the Payments table.

### Operational KPIs

- **Delivered Revenue %**
- **Non-Delivered Revenue %**
- **Delivered Orders %**
- **Late Delivery %**
- **Average Delay Days**

Additional growth and trend measures were created to evaluate changes in revenue, orders, quantity, customers, and AOV over time.

The separation of product-level metrics from payment-level metrics also provided flexibility for analyzing sales performance alongside broader financial information.

## 📊 Dashboard & Reporting

An interactive two-page dashboard was developed in Microsoft Excel using Power Pivot and DAX.

### Page 1 — Business Overview

The Business Overview page focuses on overall commercial performance and includes:

- Total Revenue
- Total Orders
- Total Customers
- Quantity Sold
- Average Order Value (AOV)
- Revenue and performance trends over time
- Top product categories by revenue
- Top customer states by revenue and order volume
- Early vs. late delivered orders

👉 [View Dashboard 1 — Business Overview](https://github.com/Onuohamichael00/Brazilian-E-Commerce-Analysis/blob/main/Dashboard%20Visuals/Olist%20dashboard%201.JPG)

### Page 2 — Operational Performance

The Operational Performance page focuses on fulfillment and delivery efficiency and includes:

- Delivered Revenue %
- Non-Delivered Revenue %
- Delivered Orders %
- Late Delivery %
- Average Order Value (AOV)
- Product revenue by order status
- Late vs. on-time delivery performance
- Seller state performance by revenue and orders
- On-time vs. late delivery revenue and order comparisons

A **Year timeline slicer** was incorporated to allow users to interactively filter the dashboard and analyze performance across different periods.

👉 [View Dashboard 2 — Operational Performance](https://github.com/Onuohamichael00/Brazilian-E-Commerce-Analysis/blob/main/Dashboard%20Visuals/Olist%20Dashboard%202.JPG)


## 🔍 Key Insights

### 💰 Overall Business Performance

The analysis generated approximately **$13.6M in product revenue** across **98.7K orders** and **98.9K customers**, with an average order value of approximately **$138**.

### 🛍️ Product Category Performance

The highest-performing product categories by revenue were:

- **beleza_saude** — approximately $1.3M
- **relogios_presentes** — approximately $1.2M
- **cama_mesa_banho** — approximately $1.0M

These categories represented some of the strongest contributors to overall product revenue.

### 📍 Geographic Performance

**São Paulo (SP)** was the strongest customer market, generating approximately **$5.2M in revenue** across **41.1K orders**.

Seller activity was also highly concentrated in São Paulo, generating approximately **$8.8M in seller revenue** and **70.2K seller orders**.

### 📈 Sales Trends

Revenue peaked in **May at approximately $1.5M**, while March, April, July, and August each recorded approximately $1.4M.

The lowest monthly revenue occurred in **September ($621K)**, followed by October ($712K) and December ($740K), indicating noticeable fluctuations in monthly demand.

### 🚚 Delivery & Fulfillment Performance

Overall fulfillment performance was strong, with:

- **96.8%** of product revenue associated with delivered orders.
- **97.2%** of orders delivered.
- **3.2%** of product revenue associated with non-delivered orders.
- Approximately **6.8%** of delivered orders classified as late.

Early deliveries generated approximately **$12.2M in revenue** across **89.4K orders**, while late deliveries accounted for approximately **$979K in revenue** across **6.5K orders**.

### ⭐ Customer Reviews

Customer review outcomes were predominantly positive:

- **Excellent:** 76.1K reviews
- **Bad:** 14.5K reviews
- **Average:** 8.2K reviews

This indicates a strong overall level of customer satisfaction within the analyzed dataset.

## 💡 Recommendations

Based on the analysis, the following recommendations were identified:

### 🚚 Improve Delivery Performance
Focus on reducing late deliveries by investigating operational bottlenecks, seller regions, and shipping partners that may contribute to delivery delays.

### 🛍️ Expand High-Performing Categories
Increase marketing, inventory allocation, and promotional efforts around strong-performing categories such as **beleza_saude**, **relogios_presentes**, and **cama_mesa_banho**.

### 📍 Reduce Geographic Concentration
Explore opportunities to increase customer acquisition and seller activity in other high-potential states such as **Rio de Janeiro (RJ), Minas Gerais (MG), and Paraná (PR)** to reduce dependence on São Paulo.

### 📦 Minimize Non-Delivered Orders
Strengthen fulfillment monitoring and cancellation management to reduce the approximately **3.2% of product revenue associated with non-delivered orders**.

### ⭐ Leverage Customer Satisfaction
Use the strong volume of positive reviews to support customer retention initiatives, loyalty programs, and referral strategies.

### 🤝 Optimize Seller Performance
Identify successful practices among high-performing sellers and regions and use these insights to improve seller performance across the wider marketplace.

### 📅 Plan for Seasonality
Monitor monthly revenue patterns to improve demand forecasting, inventory planning, and the timing of marketing campaigns.

## 🛠️ Tools & Skills

### Tools Used

- **Microsoft Excel**
- **Power Query**
- **Power Pivot**
- **DAX**

### Key Skills Demonstrated

- Data Cleaning & Transformation
- Data Modeling
- Star Schema Design
- DAX Measure Development
- KPI Development
- Time-Series Analysis
- Sales Performance Analysis
- Customer Analysis
- Product & Category Analysis
- Seller Performance Analysis
- Delivery & Operational Analysis
- Interactive Dashboard Development
- Data Visualization
- Business Insight Generation

## 📁 Project Documentation & Resources

The project files and supporting materials are available below:

- 📊 [View Completed Excel Workbook](https://docs.google.com/spreadsheets/d/1UWBY91E_imVi18iHmKHLebZsdRrs8kMs/edit?usp=sharing)
- 📄 [View Full Project Documentation](https://docs.google.com/document/d/1zo0tR1C_hQyhV4xJofY-BI5oEWNEgzk3/edit?usp=sharing)
- 🖼️ [View Dashboard Visuals](./Dashboard%20Visuals/README.md)

> **Note:** The raw dataset is not included in this repository due to its file size. It can be accessed from the original [Kaggle dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).

## 📌 Conclusion

This project demonstrates how Microsoft Excel can be used as a complete analytical tool to transform raw e-commerce data into meaningful business insights.

Through Power Query, Power Pivot, and DAX, the analysis combines data cleaning, data modeling, KPI development, and interactive visualization to evaluate sales performance, customer behavior, product trends, seller activity, and delivery operations.

The resulting dashboard provides a structured view of business performance and highlights opportunities for improving sales growth, fulfillment efficiency, geographic expansion, and customer retention.


## 👤 Author

**Michael Onuoha**

Data Analyst focused on transforming raw data into actionable business insights using **Microsoft Excel, Power Query, Power Pivot, DAX, and SQL**.

🔗 [Connect with me on LinkedIn](https://www.linkedin.com/in/michael-onuoha/)
