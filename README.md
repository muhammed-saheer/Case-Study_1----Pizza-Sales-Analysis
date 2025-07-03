# 🍕 Pizza Sales Analysis – Power BI Case Study

This project analyzes a year's worth of pizza sales data from a fictional pizza place using **Power BI**. The goal is to uncover sales trends, customer behavior, popular and unpopular pizzas, and recommend actionable insights such as **promotions** or **menu optimization**.

---

## 📁 Files Included

- `orders.csv`
- `order_details.csv`
- `pizzas.csv`
- `pizza_types.csv`
- Power BI Dashboard screenshots:
  - Customers & Peak Hours
  - Pizzas per Order & Bestsellers
  - Revenue & Seasonality
  - Promotions & Poor Performers
- `Pizza_Sales_Analysis.pbix` (Power BI File)

---

## 📊 Questions Answered

### 1. **How many customers do we have each day? Are there any peak hours?**

#### 🔧 Cleaning & Transformation
- Created a `DateTime` column by merging `date` and `time` in the `orders` table.
- Extracted:
  - `Day`, `Month Name`, `Weekday Name`, `Hour` columns using Power Query.

#### 📈 Visuals Created
- **Line Chart:** Customers per Day
- **Bar Chart:** Orders by Hour

#### 💡 Insight
- Peak customer traffic occurs at **12 PM to 1 PM** and **5 PM to 6 PM**.
- Highest daily customer count reached **820+**.
- Weekends show slightly higher activity, indicating strong lunchtime demand.

---

### 2. **How many pizzas are typically in an order? Do we have any bestsellers?**

#### 🔧 Cleaning & Measures
- Created `TotalPizzasPerOrder` using:
  ```dax
  PizzasPerOrder = SUMMARIZE(order_details, order_details[order_id], "TotalPizzas", SUM(order_details[quantity]))
