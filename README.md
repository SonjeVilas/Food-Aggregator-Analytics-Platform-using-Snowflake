# 🍽️ Food Aggregator Analytics Platform using Snowflake

<p align="center">

![Snowflake](https://img.shields.io/badge/Snowflake-29B5E8?style=for-the-badge&logo=snowflake&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-336791?style=for-the-badge&logo=postgresql&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)
![Data Engineering](https://img.shields.io/badge/Data%20Engineering-0A66C2?style=for-the-badge)
![Star Schema](https://img.shields.io/badge/Star%20Schema-Data%20Warehouse-success?style=for-the-badge)

</p>

---

# 📌 Project Overview

The **Food Aggregator Analytics Platform using Snowflake** is an end-to-end Data Engineering project that simulates the analytics platform of a food delivery company.

The project demonstrates how raw CSV data can be ingested into Snowflake, transformed through multiple processing layers, modeled into a Star Schema, and visualized using a Streamlit dashboard.

The primary goal is to build a scalable ELT pipeline capable of supporting business analytics and reporting.

---

# 🎯 Business Problem

Food delivery companies generate huge volumes of transactional data from customers, restaurants, menu items, deliveries, and orders.

Business teams require reliable and analytics-ready data to answer questions like:

- What is the total revenue?
- Which restaurants generate the highest sales?
- Which menu items are most popular?
- Which cities receive the highest number of orders?
- How many orders are delivered successfully?
- What is the average order value?

To answer these questions efficiently, data must be transformed into a structured analytical model.

---

# 🏗️ Project Architecture

The project follows a three-layer ELT architecture.

```
CSV Files
     │
     ▼
Internal Stage
     │
 COPY INTO
     │
     ▼
Stage Layer
     │
 Streams
     ▼
Clean Layer
     │
 Streams
     ▼
Consumption Layer
     │
Fact & Dimension Tables
     ▼
Business Views
     ▼
Streamlit Dashboard
```

---

## 🏗️ Project Architecture

<p align="center">
  <img src="Architecture/Data%20Flow%20Architecture.png" alt="Project Architecture" width="1000"/>
</p>

---

# ⭐ Data Warehouse Model

The Consumption layer is designed using a **Star Schema**.

Fact Table:

- ORDER_ITEM_FACT

Dimension Tables:

- CUSTOMER_DIM
- CUSTOMER_ADDRESS_DIM
- RESTAURANT_DIM
- RESTAURANT_LOCATION_DIM
- MENU_DIM
- DELIVERY_AGENT_DIM
- DATE_DIM

---

## ⭐ Star Schema

<p align="center">
  <img src="Architecture/Revenue%20Dashboard%20ER%20Diagram.png" alt="Star Schema" width="600"/>
</p>

---

# ⚙️ Technologies Used

| Technology | Purpose |
|------------|----------|
| Snowflake | Cloud Data Warehouse |
| SQL | Data Transformation |
| Snowflake Streams | Incremental Loading |
| MERGE | SCD Type 2 |
| Internal Stage | Data Ingestion |
| Streamlit | Dashboard |
| Git | Version Control |
| GitHub | Project Hosting |

---

# 📂 Repository Structure

```
Food-Aggregator-Analytics-Platform-using-Snowflake

│
├── Architecture
│
├── SQL
│
├── Sample Data
│
├── Screenshots
│
└── Streamlit
```

---

# 📁 SQL Scripts

| Script | Description |
|---------|-------------|
| 01_Create_Database.sql | Creates Database and Schemas |
| 02_Location_Dim.sql | Location Dimension |
| 03_Restaurant_Dim.sql | Restaurant Dimension |
| 04_Customer_Dim.sql | Customer Dimension |
| 05_Customer_Address_Dim.sql | Customer Address Dimension |
| 06_Menu_Dim.sql | Menu Dimension |
| 07_Delivery_Agent_Dim.sql | Delivery Agent Dimension |
| 08_Delivery.sql | Delivery Data |
| 09_Orders.sql | Orders Data |
| 10_Order_Items.sql | Order Items |
| 11_Date_Dim.sql | Date Dimension |
| 12_Order_Item_Fact.sql | Fact Table |
| 13_KPI_Views.sql | Business KPI Views |

---

# 📊 Dashboard

The project includes an interactive Streamlit Revenue Dashboard.

Dashboard Features:

- Total Revenue
- Total Orders
- Maximum Order Value
- Average Revenue Per Order
- Average Revenue Per Item
- Year-wise Filtering

---

## 📷 Dashboard Preview

```markdown
![Dashboard](Screenshots/Revenue_Dashboard.png)
```

---

# 📈 Business KPIs

The dashboard provides the following business metrics:

- Total Revenue
- Total Orders
- Average Order Value
- Maximum Order Value
- Average Revenue Per Item
- Revenue by Year

---

# 🚀 Snowflake Concepts Implemented

✅ Internal Stages

✅ File Formats

✅ COPY INTO

✅ Streams

✅ MERGE Statements

✅ Slowly Changing Dimension (SCD Type 2)

✅ Hash Keys

✅ Star Schema

✅ Fact & Dimension Modeling

✅ Business Views

✅ Streamlit Dashboard

---

# ▶️ How to Run

### Clone Repository

```bash
git clone https://github.com/SonjeVilas/Food-Aggregator-Analytics-Platform-using-Snowflake.git
```

### Open Snowflake

Execute SQL scripts in sequence.

```
01_Create_Database.sql

↓

Dimension Scripts

↓

Fact Table

↓

KPI Views
```

Deploy the Streamlit application from the **Streamlit** folder.

---

# 📚 Learning Outcomes

This project helped strengthen my understanding of:

- Snowflake Data Warehouse
- ELT Pipelines
- Data Warehouse Design
- Star Schema Modeling
- Slowly Changing Dimensions
- Incremental Data Loading
- SQL Transformations
- Streamlit Dashboard Development

---

# 🔮 Future Enhancements

- Snowflake Tasks
- Dynamic Tables
- Snowpark Python
- Cortex AI Integration
- Power BI Dashboard
- Automated Data Pipeline
- CI/CD Deployment

---

# 🙏 Acknowledgements

This project was inspired by educational content from the **Data Engineering Simplified** YouTube channel and accompanying Medium article.

The implementation has been organized, documented, and enhanced for learning and portfolio purposes.

---

# 👨‍💻 Author

**Vilas Sonje**

GitHub: https://github.com/SonjeVilas

LinkedIn: *(Add your LinkedIn profile here)*

---

# ⭐ If you found this project useful, consider giving it a Star!
