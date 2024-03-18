# Superstore Analytics
Dataset: [db-fiddle](https://www.db-fiddle.com/f/4A9aN3jvK2mbU2gTuoF2eJ/0)

<br>

## Analysis
Collects information from a superstore database, focusing on item listings, prices, stock levels, and customer ratings across various categories.

<br>

### Show all items in order by price
```sql
SELECT 
  item_name, 
  price
FROM superstore
ORDER BY price DESC;
```
<details><summary><i>Show result</i></summary>

| item_name                     | price   |
|-------------------------------|--------:|
| Smart LED TV                  | 549.00  |
| Memory Foam Mattress          | 499.99  |
| Robot Vacuum Cleaner          | 199.50  |
| Ergonomic Office Chair        | 189.00  |
| Air Purifier                  | 129.50  |
| Stainless Steel Cookware Set  | 89.99   |
| Cotton Bedding Set            | 89.00   |
| Premium Coffee Maker          | 79.99   |
| Smart Home Security Camera    | 79.95   |
| Wireless Earbuds              | 49.99   |
| Slow Cooker                   | 49.95   |
| Wireless Bluetooth Speaker    | 39.99   |
| Cutlery Set                   | 34.50   |
| Non-Stick Baking Set          | 29.95   |
| Cozy Throw Blanket            | 24.99   |
</details>

<br>

### Show items from the Kitchen Supply category by most expensive
```sql
SELECT 
  item_name, 
  MAX(price)
FROM superstore
WHERE category = 'Kitchen Supplies'
GROUP BY item_name
ORDER BY MAX(price) DESC;
```
<details><summary><i>Show result</i></summary>

| item_name                     | MAX(price) |
|-------------------------------|------------|
| Stainless Steel Cookware Set  | 89.99      |
| Premium Coffee Maker          | 79.99      |
| Cutlery Set                   | 34.50      |
| Non-Stick Baking Set          | 29.95      |
</details>

<br>

### Show items low in stock from each category
```sql
SELECT 
  item_name, 
  category, 
  stock_quantity
FROM superstore
WHERE stock_quantity <= 25
ORDER BY category, stock_quantity;
```
<details><summary><i>Show result</i></summary>

| item_name                    | category    | stock_quantity |
|------------------------------|-------------|---------------:|
| Smart Home Security Camera   | Electronics | 15             |
| Smart LED TV                 | Electronics | 20             |
| Ergonomic Office Chair       | Furnishings | 20             |
| Cotton Bedding Set           | Furnishings | 25             |
</details>

<br>

### Show items in the "Electronics" category with a customer rating of at least 4.3 or higher
```sql
SELECT 
  item_name, 
  average_rating
FROM superstore
WHERE category = 'Electronics' AND average_rating >= 4.3
ORDER BY average_rating DESC;
```
<details><summary><i>Show result</i></summary>
  
| item_name         | average_rating |
|-------------------|----------------|
| Smart LED TV      | 4.50           |
| Wireless Earbuds  | 4.30           |
</details>

<br>
