## Day 1 — 2025-08-16

**Problem**  
You are provided with a table named Products containing information about various products, including their names and prices. Write a SQL query to count the number of products in each category based on its price into three categories:  
1. "Low Price" for products with a price less than 100  
2. "Medium Price" for products with a price between 100 and 500 (inclusive)  
3. "High Price" for products with a price greater than 500  
Display the output in descending order of the number of products.

**Short Explanation**  
We used a `CASE` statement to classify products into three price categories.  
`COUNT(*)` was applied to get the number of products in each category.  
`GROUP BY` grouped rows by category, and `ORDER BY` sorted them in descending order by count.

**Why this works**  
By grouping after categorization, we avoid scanning the table multiple times and ensure each product is counted in exactly one category.

**Try Here:** [View](https://www.namastesql.com/coding-problem/2-product-category?complete_status=1).

**🧠Difficulty:** Easy 🟢

**Answer Query**
```sql
SELECT 
    CASE
        WHEN price < 100 THEN 'Low Price'
        WHEN price BETWEEN 100 AND 500 THEN 'Medium Price'
        ELSE 'High Price'
    END AS category, 
    COUNT(*) AS no_of_products
FROM products
GROUP BY category
ORDER BY no_of_products DESC;

 
 
