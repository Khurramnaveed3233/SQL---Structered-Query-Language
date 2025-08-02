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

