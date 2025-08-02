# 📊 Comparison & Logical Operators with Outputs (Roman Urdu + Example Results)

Yeh examples real-world data analysis mein use hotay hain, jaise SQL databases ya Python Pandas DataFrames mein filtering karte waqt.

---

## 1. Comparison Operators (Muqabla Karne Wale)

### = (Barabar)

```sql
SELECT name, salary FROM employees
WHERE salary = 50000;
```

 **Output:**

| name     | salary |
|----------|--------|
| Ali      | 50000  |
| Sana     | 50000  |

---

### != or <> (Barabar nahi)

```sql
SELECT name, city FROM customers
WHERE city != 'Lahore';
```

 **Output:**

| name   | city     |
|--------|----------|
| Ahmed  | Karachi  |
| Ayesha | Islamabad|

---

### < (Chhota)

```sql
SELECT * FROM students
WHERE age < 20;
```

 **Output:**

| name   | age |
|--------|-----|
| Sara   | 19  |
| Bilal  | 18  |

---

### > (Bara)

```sql
SELECT * FROM orders
WHERE amount > 10000;
```

 **Output:**

| order_id | amount |
|----------|--------|
| 101      | 15000  |
| 105      | 11000  |

---

### <= (Chhota ya Barabar)

```sql
SELECT * FROM reviews
WHERE rating <= 3.5;
```

 **Output:**

| product | rating |
|---------|--------|
| Phone A | 3.0    |
| Phone B | 2.5    |

---

### >= (Bara ya Barabar)

```sql
SELECT * FROM candidates
WHERE experience >= 5;
```

 **Output:**

| name     | experience |
|----------|------------|
| Uzair    | 6          |
| Fatima   | 5          |

---

## 🧠 Logical Operators (Mantaqi)

###  AND

```sql
SELECT * FROM customers
WHERE age > 25 AND income > 50000;
```

 **Output:**

| name   | age | income |
|--------|-----|--------|
| Ali    | 30  | 60000  |
| Hina   | 28  | 70000  |

---

### OR

```sql
SELECT * FROM orders
WHERE status = 'Pending' OR status = 'Delayed';
```

🧾 **Output:**

| order_id | status  |
|----------|---------|
| 201      | Pending |
| 204      | Delayed |

---

### NOT

```sql
SELECT * FROM products
WHERE NOT category = 'Electronics';
```

 **Output:**

| product_name | category   |
|--------------|------------|
| Sofa         | Furniture  |
| Shampoo      | Cosmetics  |

---

###  BETWEEN

```sql
SELECT * FROM sales
WHERE sale_date BETWEEN '2024-01-01' AND '2024-01-31';
```

 **Output:**

| sale_id | sale_date |
|---------|-----------|
| 1001    | 2024-01-10|
| 1002    | 2024-01-25|

---

###  IN

```sql
SELECT * FROM employees
WHERE department IN ('HR', 'Finance');
```

 **Output:**

| name   | department |
|--------|------------|
| Zainab | HR         |
| Omar   | Finance    |

---

### LIKE

```sql
SELECT * FROM customers
WHERE email LIKE '%.edu';
```

🧾 **Output:**

| name   | email                |
|--------|----------------------|
| Ali    | ali@uni.edu          |
| Sara   | sara@student.edu.pk  |

---

###  IS NULL / IS NOT NULL

**IS NULL:**

```sql
SELECT * FROM surveys WHERE response IS NULL;
```

 **Output:**

| user_id | response |
|---------|----------|
| 101     | NULL     |
| 104     | NULL     |

**IS NOT NULL:**

```sql
SELECT * FROM surveys WHERE response IS NOT NULL;
```

 **Output:**

| user_id | response   |
|---------|------------|
| 102     | Excellent  |
| 103     | Average    |

---

##  Python (Pandas) mein Comparison & Logical Operators

Assume karo aik DataFrame `df` hai:

```python
import pandas as pd

df = pd.DataFrame({
    'name': ['Ali', 'Sara', 'Bilal'],
    'age': [30, 19, 24],
    'income': [60000, 20000, 50000]
})
```

### `df[df['age'] < 25]`

 **Output:**

| name  | age | income |
|-------|-----|--------|
| Sara  | 19  | 20000  |
| Bilal | 24  | 50000  |

---

### `df[df['income'] >= 50000]`

 **Output:**

| name | age | income |
|------|-----|--------|
| Ali  | 30  | 60000  |
| Bilal| 24  | 50000  |

---

### `df[df['name'].isin(['Ali', 'Sara'])]`

 **Output:**

| name | age | income |
|------|-----|--------|
| Ali  | 30  | 60000  |
| Sara | 19  | 20000  |

---

 **Summary**: 
 
Yeh sare comparison aur logical operators data analysis ka foundation hain — filtering, reporting, dashboards, aur machine learning models sab mein inka use hota hai.

#  SQL Aggregate Functions Explained with Examples, Usage & Output

Aggregate functions **summarize multiple rows into a single result** — essential in data science for KPIs, summaries, dashboards, and reports.

---

## 1.  `COUNT()` – Total Number of Rows

 **Usage**: Ginti nikalna — e.g., kitne customers, orders, ya missing values hain.

 *Use Case*: Kitne users ne survey submit kiya.

```sql
SELECT COUNT(*) AS total_responses
FROM surveys
WHERE response IS NOT NULL;
```

 **Output:**

| total_responses |
|-----------------|
| 245             |

---

## 2.  `SUM()` – Total of a Column

 **Usage**: Kisi column ka total nikalna — jaise total sales, revenue, ya points.

 *Use Case*: Monthly total revenue calculate karna.

```sql
SELECT SUM(amount) AS total_sales
FROM orders
WHERE order_date BETWEEN '2025-01-01' AND '2025-01-31';
```

 **Output:**

| total_sales |
|-------------|
| 150000      |

---

## 3.  `AVG()` – Average Value

 **Usage**: Kisi column ki average value nikalna — e.g., average salary, rating.

💡 *Use Case*: Product ki average rating dekhni.

```sql
SELECT AVG(rating) AS avg_rating
FROM product_reviews
WHERE product_id = 101;
```

 **Output:**

| avg_rating |
|------------|
| 4.2        |

---

## 4.  `MIN()` – Minimum Value

 **Usage**: Sabse chhoti value nikalna — jaise lowest marks, salary, price.

 *Use Case*: Kis employee ki sabse kam salary hai?

```sql
SELECT MIN(salary) AS lowest_salary
FROM employees;
```

 **Output:**

| lowest_salary |
|---------------|
| 25000         |

---

## 5.  `MAX()` – Maximum Value

 **Usage**: Sabse badi value nikalna — jaise highest income, rating, score.

 *Use Case*: Kis customer ne sabse zyada kharche kiye?

```sql
SELECT MAX(total_spent) AS top_customer_spending
FROM customers;
```

 **Output:**

| top_customer_spending |
|------------------------|
| 185000                 |

---

## 6.  `COUNT(DISTINCT)` – Unique Values Count

🧠 **Usage**: Kitne alag-alag values hain kisi column mein.

💡 *Use Case*: Kitne unique cities mein humare customers hain?

```sql
SELECT COUNT(DISTINCT city) AS unique_cities
FROM customers;
```

 **Output:**

| unique_cities |
|----------------|
| 12             |

---

## 7.  `GROUP BY` with Aggregate Functions

🧠 **Usage**: Groups ke andar totals/averages etc. calculate karna.

💡 *Use Case*: Har department ki average salary.

```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department;
```

 **Output:**

| department | avg_salary |
|------------|------------|
| HR         | 45000      |
| IT         | 65000      |
| Finance    | 60000      |

---

## 8.  `HAVING` – Filter after Aggregation

🧠 **Usage**: Jab aggregation ke baad filter karna ho (GROUP BY ke sath use hota hai).

💡 *Use Case*: Sirf un departments ko dikhana jinki avg salary 60k se zyada hai.

```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 60000;
```

 **Output:**

| department | avg_salary |
|------------|------------|
| IT         | 65000      |

---

## 9.  `ROUND()` with Aggregates (Bonus)

🧠 **Usage**: Decimal values ko round karna, especially averages.

💡 *Use Case*: Round off average ratings to 1 decimal.

```sql
SELECT product_id, ROUND(AVG(rating), 1) AS rounded_avg
FROM product_reviews
GROUP BY product_id;
```

 **Output:**

| product_id | rounded_avg |
|------------|-------------|
| 101        | 4.3         |
| 102        | 3.8         |

---

##  Summary Table

| Function            | Purpose                            | Typical Use Case                        |
|---------------------|-------------------------------------|-----------------------------------------|
| `COUNT()`           | Total rows                          | Total orders, users                     |
| `SUM()`             | Column total                        | Total revenue, sales                    |
| `AVG()`             | Average value                       | Avg rating, salary                      |
| `MIN()`             | Smallest value                      | Lowest score, price                     |
| `MAX()`             | Largest value                       | Top scorer, highest spender             |
| `COUNT(DISTINCT)`   | Unique values count                 | Unique cities, products                 |
| `GROUP BY`          | Group-wise aggregation              | Avg salary per dept                     |
| `HAVING`            | Filter after GROUP BY               | Only depts with avg > 60k               |
| `ROUND()`           | Rounds decimal aggregates           | Round off averages                      |

---

 **Conclusion**:  
Aggregate functions are essential in **summarizing**, **reporting**, and **finding insights** from big datasets — they’re everywhere in **SQL-based dashboards**, **data pipelines**, and **analyst reports**.

