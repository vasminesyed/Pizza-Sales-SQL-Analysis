# Pizza Sales SQL Analysis

SQL-based analysis of pizza sales data to find revenue patterns, top-selling products, and peak ordering times.

## What this project does

Analyzed 40,000+ pizza order records to answer business questions like which pizzas make the most money, what time of day is busiest, and which days have the highest orders.

## Dataset

The dataset has 4 tables:

| Table | Description |
|-------|-------------|
| orders | Order ID, date, time |
| order_details | Order ID, pizza ID, quantity |
| pizzas | Pizza ID, type, size, price |
| pizza_types | Pizza type ID, name, category, ingredients |

## Questions answered

**Revenue Analysis**
- Total revenue, total orders, total pizzas sold
- Average order value
- Revenue by pizza category and size

**Product Analysis**
- Top 10 revenue-generating pizzas
- Bottom 5 pizzas (least selling)
- Revenue contribution of top 10 pizzas to total sales (found they contribute 45% of total revenue)

**Time-based Analysis**
- Orders by hour of day (peak hours)
- Orders by day of week
- Monthly revenue trend

**Advanced SQL**
- Cumulative revenue by date (window function)
- Rank pizzas within each category by revenue (RANK + PARTITION BY)
- Top 3 pizzas per category using CTE
- Running totals and percentage contributions

## Key findings

- Top 10 pizzas contribute to 45% of total revenue
- Peak ordering time is between 12 PM to 1 PM and 5 PM to 7 PM
- Friday and Saturday have the highest order volume
- Classic category brings in the most revenue overall

## Query optimization

Before adding indexes, complex queries with multiple joins on 40,000+ rows were taking around 5 minutes. After creating indexes on commonly used join and filter columns, query time came down to 30 seconds.

```sql
CREATE INDEX idx_orders_date ON orders(date);
CREATE INDEX idx_order_details_pizza_id ON order_details(pizza_id);
CREATE INDEX idx_order_details_order_id ON order_details(order_id);
```

## Tech Stack

- MySQL / PostgreSQL
- SQL (joins, subqueries, CTEs, window functions, aggregations)

## How to run

```bash
# 1. Import the dataset into your MySQL or PostgreSQL database
# 2. Open pizza_sales_analysis.sql
# 3. Run queries one by one or all at once
```

## File structure

```
Pizza-Sales-SQL-Analysis/
│
├── pizza_sales_analysis.sql    # All SQL queries with comments
├── pdf sql.pdf                 # Output/results reference
├── README.md                   # Project documentation
```
