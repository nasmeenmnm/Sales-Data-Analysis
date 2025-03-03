# 📊 E-Commerce Sales Dashboard (Power BI)

## 📍 Overview  
This Power BI project presents an **E-Commerce Sales Dashboard** designed to analyze **sales performance, customer insights, profitability, and shipping efficiency**. The dashboard provides **interactive visualizations and DAX calculations** to help businesses make **data-driven decisions**.

---

## 📂 Dataset  
- **Source:** Global Superstore Dataset  
- **Key Columns:**  
  - `Order ID`, `Product Name`, `Customer Name`, `Category`, `Sub-Category`, `Sales`, `Profit`, `Discount`, `Shipping Cost`, `Order Date`, `Ship Date`, `Country`, `Region`  

---

## 📊 Key Features & Visuals  

### 📌 **1. Sales Analysis**  
✅ **Top 10 Best-Selling Products** → *(Clustered Column Chart)*  
  - **X-Axis:** Product Name  
  - **Y-Axis:** Sum of Sales  
  - **Filter:** Top 10 by Sales  

✅ **Sales Trend Over Time** → *(Line Chart)*  
  - **X-Axis:** Order Date (Month-Year)  
  - **Y-Axis:** Sum of Sales  

✅ **Sales by Category & Sub-Category** → *(Pie Chart & Bar Chart)*  
  - **Legend:** Category  
  - **Values:** Sales  

---

### 📌 **2. Customer Insights**  
✅ **Customer Count by Country** → *(Map Visualization)*  
  - **Location:** Country  
  - **Size:** Customer Count  

✅ **Top 10 Customers by Sales** → *(Table with Ranking)*  
  - Columns: Customer Name, Total Sales  
  - Sorted by: Total Sales (Descending)  

---

### 📌 **3. Profitability Analysis**  
✅ **Profit vs. Sales** → *(Scatter Plot)*  
  - **X-Axis:** Sales  
  - **Y-Axis:** Profit  
  - **Size:** Discount  

✅ **Profit by Product Category** → *(Clustered Column Chart)*  
  - **X-Axis:** Category  
  - **Y-Axis:** Profit  

✅ **Profit by Country** → *(Tooltip in Map Chart)*  
  - **Tooltip Value:** Profit  

---

### 📌 **4. Shipping Performance**  
✅ **Impact of Shipping Cost on Profit** → *(Scatter Plot)*  
  - **X-Axis:** Shipping Cost  
  - **Y-Axis:** Profit  

✅ **Average Processing Time** → *(KPI Card & Table)*  
  - Order Processing Time = Order Date → Ship Date  

✅ **Orders by Shipping Mode** → *(Stacked Bar Chart)*  
  - **X-Axis:** Shipping Mode  
  - **Y-Axis:** Number of Orders  

---
## Images
![sales overview](https://github.com/user-attachments/assets/5cf9c4a5-2a93-46dd-85ca-8899ef70dc23)
![sales Shipment](https://github.com/user-attachments/assets/7363cb96-50ce-4e58-a474-87973264b99a)
![sales Sale](https://github.com/user-attachments/assets/8868197c-e9fe-4a73-afb5-ece9a8884e26)
![Sales Profit](https://github.com/user-attachments/assets/d1643eff-7ec0-45ae-9a67-1adfb15d1903)
![sales customer](https://github.com/user-attachments/assets/d8c1a762-ab59-45b1-915c-02b966045ce5)


## 🖩 DAX Measures Used  

```DAX
-- 💰 Total Sales Calculation
Total Sales = SUM('Global-Superstore'[Sales])

-- 📈 Total Profit Calculation
Total Profit = SUM('Global-Superstore'[Profit])

-- 🏆 Top Customers (Top 10 by Sales)
Top Customers = 
TOPN(10, 
    SUMMARIZE('Global-Superstore', 
        'Global-Superstore'[Customer Name], 
        "Total Sales", [Total Sales]
    ), 
    [Total Sales], DESC
)

-- 📊 Average Sales per Customer
Avg Sales per Customer = 
DIVIDE([Total Sales], DISTINCTCOUNT('Global-Superstore'[Customer Name]))

-- ⏳ Average Processing Time (Days)
Avg Processing Time = 
AVERAGEX('Global-Superstore', 
    DATEDIFF('Global-Superstore'[Order Date], 'Global-Superstore'[Ship Date], DAY)
)

-- 🚚 Shipping Cost Impact on Profit
Profit per Shipping Cost = 
DIVIDE([Total Profit], SUM('Global-Superstore'[Shipping Cost]))

-- 📍 Customer Count by Country
Customer Count = DISTINCTCOUNT('Global-Superstore'[Customer Name])

-- 📌 Profit by Country
Profit by Country = 
SUMX(FILTER('Global-Superstore', 'Global-Superstore'[Country] = SELECTEDVALUE('Global-Superstore'[Country])),
    'Global-Superstore'[Profit]
)
