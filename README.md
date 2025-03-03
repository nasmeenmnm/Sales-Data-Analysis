# 📊 E-Commerce Sales Dashboard (Power BI)

## 📍 Overview  
This Power BI project presents an **E-Commerce Sales Dashboard** designed to analyze sales, customer insights, profitability, and shipping performance. The dashboard helps businesses make data-driven decisions using **interactive visualizations and DAX calculations**.

## 📂 Dataset  
- **Source:** Global Superstore Dataset  
- **Key Columns:** Order ID, Product Name, Customer Name, Category, Sub-Category, Sales, Profit, Discount, Shipping Cost, Order Date, Ship Date, and Country.  

## 📈 Key Features  
🔹 **Sales Analysis:**  
- Top 10 best-selling products (Bar Chart)  
- Monthly sales trends (Line Chart)  
- Sales contribution by product category (Pie Chart)  

🔹 **Customer Insights:**  
- Customer distribution by country (Map Visualization)  
- Top 10 customers by total sales (Table with Ranking)  

🔹 **Profitability Analysis:**  
- Profit vs. Sales comparison (Scatter Plot)  
- Profit by product category (Clustered Column Chart)  

🔹 **Shipping Performance:**  
- Impact of shipping cost on profit (Scatter Plot)  
- Average processing time for orders  

🔹 **Advanced Tooltips:**  
- **Customer Count by Country**  
- **Profit by Country**  

## 📌 DAX Measures Used  
```DAX
Total Sales = SUM('Global-Superstore'[Sales])
Total Profit = SUM('Global-Superstore'[Profit])
Avg Sales per Customer = DIVIDE([Total Sales], DISTINCTCOUNT('Global-Superstore'[Customer Name]))
Avg Processing Time = AVERAGEX('Global-Superstore', DATEDIFF('Global-Superstore'[Order Date], 'Global-Superstore'[Ship Date], DAY))
