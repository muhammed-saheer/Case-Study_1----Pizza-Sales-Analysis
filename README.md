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

![Customers & Peak Hours](./https://github.com/muhammed-saheer/Case-Study_1----Pizza-Sales-Analysis/blob/main/Dashboard%20images/Peak%20Hour%20%20%20Customers%20Per%20Day.png)

---

### 2. **How many pizzas are typically in an order? Do we have any bestsellers?**

#### 🔧 Cleaning & Measures
- Created `TotalPizzasPerOrder` using:
  ```dax
  PizzasPerOrder = SUMMARIZE(order_details, order_details[order_id], "TotalPizzas", SUM(order_details[quantity]))
  Total Pizza Quantity = SUM(order_details[quantity])
  Sales = order_details[quantity] * RELATED(pizzas[price])  ```


#### 📈 Visuals Created
- **Bar Chart:** Number of orders vs pizzas per order
- **Table/Bar Chartt:** Bestselling pizzas by quantity & sales

#### 💡 Insight
- Most orders contain 1 to 4 pizzas.
- Top 5 pizzas (by quantity & revenue):
  - The Classic Deluxe Pizza
  - The Barbecue Chicken Pizza
  - The Hawaiian Pizza
  - The Pepperoni Pizza
  - The Thai Chicken Pizza
 
  ---
 

### 3. How much money did we make this year? Can we identify any seasonality in sales?

### 🔧 Measures

  ```dax
Total Revenue = SUM(order_details[quantity] * RELATED(pizzas[price]))
  ```

### 📊 Visuals
- **Card:** Total Revenue (₹39.03 Billion)
- **Bar Chart:** Revenue by Weekday
- **Line Chart:** Revenue by Month

### 💡 Insight
- **Friday** generated the highest revenue.
- **July** was the best-performing month; **October** was the lowest.
- Revenue fluctuates with minor seasonality—could indicate **summer/festival** spikes.

---

### 4. Are there any pizzas we should take off the menu, or promotions we could leverage?

### 🔧 Steps
- Grouped by pizza name to calculate:
 -  `Total Quantity`
 - `Total Revenue`

### 📊 Visuals
- **Table:** Worst-performing pizzas
- **Bar Chart:** Top 5 pizzas by revenue
- **Slicers:** By size and category

### 💡 Insight
- 🚫 Poor Performers :- Very low sales & revenue:
  - **The Brie Carre Pizza**
  - **The Greek Pizza**
  - **The Mediterranean Pizza**

#### ✅ These pizzas can be removed or replaced.

- 🟢 Promotion Opportunities
- - Run combo deals or upsells using top-selling items.
- Consider discounts for:
  - **Weekdays with lower traffic**
-Off-season months

---

### 📌 Tools Used
- Power BI Desktop
- Power Query (M Language)
- DAX for calculated measures
- Visuals: Line charts, bar charts, tables, slicers

### 📁 Dataset Source
- This is a simulated dataset for learning and portfolio purposes. All files are provided in the repository.

### 📌 Author
- **Muhammed Saheer K**

