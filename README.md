#  Comparison & Logical Operators 

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

#  SQL Aggregate Functions 

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

 *Use Case*: Product ki average rating dekhni.

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

 **Usage**: Kitne alag-alag values hain kisi column mein.

 *Use Case*: Kitne unique cities mein humare customers hain?

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

**Usage**: Groups ke andar totals/averages etc. calculate karna.

 *Use Case*: Har department ki average salary.

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

 **Usage**: Jab aggregation ke baad filter karna ho (GROUP BY ke sath use hota hai).

 *Use Case*: Sirf un departments ko dikhana jinki avg salary 60k se zyada hai.

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

 **Usage**: Decimal values ko round karna, especially averages.

 *Use Case*: Round off average ratings to 1 decimal.

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

#  SQL String Functions 

String functions are used in **data cleaning**, **standardization**, **text extraction**, and **pattern analysis** — essential in data science and analytics workflows.

---

##  1. `UPPER()` – Convert to UPPERCASE

 **Use**: Convert text to capital letters.

 *Use Case*: Clean names or emails before comparison.

```sql
SELECT UPPER('khurram') AS upper_name;
```

 **Output:**

| upper_name |
|------------|
| KHURRAM    |

---

##  2. `LOWER()` – Convert to lowercase

 **Use**: Convert text to small letters.

 *Use Case*: Email comparisons are usually case-insensitive.

```sql
SELECT LOWER('HELLO@EMAIL.COM') AS lower_email;
```

 **Output:**

| lower_email     |
|-----------------|
| hello@email.com |

---

##  3. `TRIM()` – Remove spaces from both ends (SQL Server 2017+)

 **Use**: Clean extra white space from user input.

 *Use Case*: Standardize names entered with extra spaces.

```sql
SELECT TRIM('   Ali Raza   ') AS trimmed_name;
```

 **Output:**

| trimmed_name |
|--------------|
| Ali Raza     |

---

##  4. `LTRIM()` – Remove spaces from the LEFT side

```sql
SELECT LTRIM('   Lahore') AS clean_left;
```

 **Output:**

| clean_left |
|------------|
| Lahore     |

---

##  5. `RTRIM()` – Remove spaces from the RIGHT side

```sql
SELECT RTRIM('Lahore   ') AS clean_right;
```

 **Output:**

| clean_right |
|-------------|
| Lahore      |

---

##  6. `SUBSTRING()` – Extract part of a string

 **Use**: Extract specific characters based on position.

 *Use Case*: Extract year from a date string.

```sql
SELECT SUBSTRING('2025-08-01', 1, 4) AS year;
```

 **Output:**

| year |
|------|
| 2025 |

---

## ⬅ 7. `LEFT()` – Get characters from the LEFT

 **Use**: Useful for standard codes, phone prefixes, etc.

 *Use Case*: Get first 3 letters of a customer name.

```sql
SELECT LEFT('Khurram', 3) AS short_name;
```

 **Output:**

| short_name |
|------------|
| Khu        |

---

## ➡ 8. `RIGHT()` – Get characters from the RIGHT

 *Use Case*: Get last 4 digits of a phone number.

```sql
SELECT RIGHT('03001234567', 4) AS last_digits;
```

🧾 **Output:**

| last_digits |
|-------------|
| 4567        |

---

##  9. `LEN()` – Get string length

 **Use**: Check number of characters in a field.

 *Use Case*: Validate phone number length.

```sql
SELECT LEN('03451234567') AS phone_length;
```

 **Output:**

| phone_length |
|--------------|
| 11           |

---

##  10. `REPLACE()` – Replace part of a string

 **Use**: Replace unwanted characters (e.g., dashes in phone).

 *Use Case*: Clean phone numbers for uniformity.

```sql
SELECT REPLACE('0345-123-4567', '-', '') AS clean_phone;
```

 **Output:**

| clean_phone |
|-------------|
| 03451234567 |

---

##  11. `CHARINDEX()` – Find position of substring

 **Use**: Find where a specific character starts.

 *Use Case*: Find where "@" appears in an email.

```sql
SELECT CHARINDEX('@', 'ali@example.com') AS at_position;
```

 **Output:**

| at_position |
|-------------|
| 4           |

---

##  Real-Time Data Analysis Use Cases

### 1. **Email Cleanup & Standardization**
```sql
SELECT LOWER(TRIM(email)) AS clean_email FROM users;
```

### 2. **Extracting Domains from Emails**
```sql
SELECT SUBSTRING(email, CHARINDEX('@', email) + 1, LEN(email)) AS domain
FROM users;
```

 **Output:**

| domain         |
|----------------|
| gmail.com      |
| uopeople.edu   |

---

### 3. **Masking Credit Card Numbers**
```sql
SELECT CONCAT('****-****-****-', RIGHT(card_number, 4)) AS masked_card
FROM payments;
```

 **Output:**

| masked_card         |
|---------------------|
| ****-****-****-5678 |

---

### 4. **Detecting Invalid Names**
```sql
SELECT name
FROM employees
WHERE LEN(name) < 3 OR CHARINDEX('123', name) > 0;
```

---

##  Summary Table

| Function     | Purpose                        |
|--------------|--------------------------------|
| `UPPER()`    | Convert to capital letters     |
| `LOWER()`    | Convert to small letters       |
| `TRIM()`     | Remove spaces (both sides)     |
| `LTRIM()`    | Remove left-side spaces        |
| `RTRIM()`    | Remove right-side spaces       |
| `SUBSTRING()`| Extract specific part of string|
| `LEFT()`     | Get left side characters       |
| `RIGHT()`    | Get right side characters      |
| `LEN()`      | Count characters in string     |
| `REPLACE()`  | Replace specific characters    |
| `CHARINDEX()`| Find position of substring     |

---

 **Conclusion**:  
String functions are a key part of **data cleaning, feature engineering, text mining**, and **report preparation** in SQL-based data analytics workflows.

# 🕒 SQL Date & Time Functions: Usage, Examples & Outputs in Real-Time Data Analysis

These functions are crucial in **time-based reporting**, **trend analysis**, **cohort segmentation**, and **date formatting** for dashboards.

---

##  1. `GETDATE()` – Current System Date & Time

 **Use**: Returns current date & time (datetime datatype).

 *Use Case*: Stamp row insert time or filter "today's data".

```sql
SELECT GETDATE() AS current_datetime;
```

 **Output:**

| current_datetime       |
|------------------------|
| 2025-08-02 09:30:15.890|

---

##  2. `CURRENT_TIMESTAMP` – Same as `GETDATE()`

 **Use**: ANSI standard alternative to `GETDATE()`.

```sql
SELECT CURRENT_TIMESTAMP AS now_time;
```

 **Output:**

| now_time               |
|------------------------|
| 2025-08-02 09:30:15.890|

---

##  3. `DATEDIFF()` – Difference Between Two Dates

 **Use**: Get number of days, months, or years between two dates.

 *Use Case*: Customer age or time since last purchase.

```sql
SELECT DATEDIFF(DAY, '2025-01-01', GETDATE()) AS days_passed;
```

 **Output:**

| days_passed |
|-------------|
| 214         |

---

##  4. `DATEADD()` – Add/Subtract Date Parts

 **Use**: Add/subtract days, months, or years from a date.

 *Use Case*: Calculate subscription expiry date.

```sql
SELECT DATEADD(MONTH, 6, '2025-01-01') AS expiry_date;
```

 **Output:**

| expiry_date |
|-------------|
| 2025-07-01  |

---

##  5. `DATENAME()` – Return String Part of a Date

 **Use**: Return day name, month name, etc. as string.

 *Use Case*: Filter or group sales by weekday name.

```sql
SELECT DATENAME(WEEKDAY, '2025-08-02') AS day_name;
```

 **Output:**

| day_name |
|----------|
| Saturday |

---

##  6. `DAY()` – Extract Day (Number)

```sql
SELECT DAY('2025-08-02') AS day_number;
```

 **Output:**

| day_number |
|------------|
| 2          |

---

##  7. `MONTH()` – Extract Month (Number)

```sql
SELECT MONTH('2025-08-02') AS month_number;
```

 **Output:**

| month_number |
|---------------|
| 8             |

---

##  8. `YEAR()` – Extract Year (Number)

```sql
SELECT YEAR('2025-08-02') AS year_number;
```

 **Output:**

| year_number |
|-------------|
| 2025        |

---

##  9. `FORMAT()` – Custom Date Formatting (SQL Server 2012+)

 **Use**: Convert date to custom string format.

 *Use Case*: Format dates for reports or Excel exports.

```sql
SELECT FORMAT(GETDATE(), 'dd-MMM-yyyy') AS formatted_date;
```

 **Output:**

| formatted_date |
|----------------|
| 02-Aug-2025    |

---

##  10. `CAST()` – Convert Between Data Types

 **Use**: Convert strings to dates or vice versa.

 *Use Case*: Convert string column to date for filtering.

```sql
SELECT CAST('2025-08-02' AS DATETIME) AS converted_date;
```

 **Output:**

| converted_date       |
|----------------------|
| 2025-08-02 00:00:00.000|

---

## 11. `CONVERT()` – Convert & Format Dates

 **Use**: More formatting control (style-based).

 *Use Case*: Format dates in 'dd/mm/yyyy' style for reports.

```sql
SELECT CONVERT(VARCHAR, GETDATE(), 103) AS uk_style_date;
```

🧾 **Output:**

| uk_style_date |
|----------------|
| 02/08/2025     |

---

## 📈 Real-Time Analytics Use Cases

### 1. **Find Orders in the Last 7 Days**
```sql
SELECT * FROM orders
WHERE order_date >= DATEADD(DAY, -7, GETDATE());
```

---

### 2. **Monthly Sales Summary**
```sql
SELECT MONTH(order_date) AS sale_month, SUM(amount) AS total_sales
FROM orders
GROUP BY MONTH(order_date);
```

---

### 3. **Filter by Specific Day Name**
```sql
SELECT * FROM sales
WHERE DATENAME(WEEKDAY, sale_date) = 'Sunday';
```

---

### 4. **Subscription Expiring in Next 30 Days**
```sql
SELECT * FROM subscriptions
WHERE expiry_date BETWEEN GETDATE() AND DATEADD(DAY, 30, GETDATE());
```

---

##  Summary Table

| Function          | Purpose                                |
|-------------------|----------------------------------------|
| `GETDATE()`       | Current system date & time             |
| `CURRENT_TIMESTAMP`| ANSI version of GETDATE()             |
| `DATEDIFF()`      | Difference between 2 dates             |
| `DATEADD()`       | Add/subtract time                      |
| `DATENAME()`      | Day/Month name as string               |
| `DAY()`           | Numeric day of month                   |
| `MONTH()`         | Numeric month                          |
| `YEAR()`          | Numeric year                           |
| `FORMAT()`        | Custom date format string              |
| `CAST()`          | Convert data types                     |
| `CONVERT()`       | Convert and format (with style codes)  |

---

 **Conclusion**:  
Date & time functions are **indispensable** in data science for **time series**, **trend reporting**, **forecasting**, and **temporal filtering**. SQL gives full control to manipulate and format date values as needed for any project.

# 🪟 SQL Window Functions - Roman Urdu mein Samjhaayi gayi

Window functions aise SQL functions hote hain jo **row-wise analysis** karte hain bina data ko group kiye huye. Ye functions **analytics**, **ranking**, aur **time-series** tasks mein bohot kaam aate hain.

---

## 1. `ROW_NUMBER()`

 Har row ko unique number assign karta hai partition/order ke basis par.

 *Use Case*: Top N records per group nikalna.

```sql
SELECT name, department, salary,
       ROW_NUMBER() OVER (PARTITION BY department ORDER BY salary DESC) AS row_num
FROM employees;
```

 **Output:**

| name   | department | salary | row_num |
|--------|------------|--------|---------|
| Ali    | HR         | 80000  | 1       |
| Sara   | HR         | 75000  | 2       |
| Zain   | IT         | 90000  | 1       |

---

##  2. `RANK()`

 Same values ko **same rank** deta hai lekin **gaps** chhodta hai.

 *Use Case*: Sales ranking jahan tie scores ho sakte hain.

```sql
SELECT name, sales,
       RANK() OVER (ORDER BY sales DESC) AS rank_pos
FROM sellers;
```

 **Output:**

| name   | sales | rank_pos |
|--------|-------|----------|
| Ali    | 1000  | 1        |
| Sana   | 1000  | 1        |
| Umar   | 900   | 3        |

---

##  3. `DENSE_RANK()`

 Same rank deta hai **without skipping** numbers.

 *Use Case*: Leaderboard jahan aapko sequential ranking chahiye.

```sql
SELECT name, marks,
       DENSE_RANK() OVER (ORDER BY marks DESC) AS dense_rank
FROM students;
```

 **Output:**

| name   | marks | dense_rank |
|--------|-------|------------|
| Ahsan  | 95    | 1          |
| Fiza   | 95    | 1          |
| Nida   | 90    | 2          |

---

##  4. `LAG()`

 Previous row ka value laata hai.

 *Use Case*: Sales comparison with previous month.

```sql
SELECT month, sales,
       LAG(sales, 1) OVER (ORDER BY month) AS previous_sales
FROM monthly_sales;
```

🧾 **Output:**

| month | sales | previous_sales |
|-------|-------|----------------|
| Jan   | 1000  | NULL           |
| Feb   | 1200  | 1000           |
| Mar   | 1300  | 1200           |

---

##  5. `LEAD()`

 Next row ka value laata hai.

 *Use Case*: Predict next month's value or trend.

```sql
SELECT month, sales,
       LEAD(sales, 1) OVER (ORDER BY month) AS next_sales
FROM monthly_sales;
```

🧾 **Output:**

| month | sales | next_sales |
|-------|-------|------------|
| Jan   | 1000  | 1200       |
| Feb   | 1200  | 1300       |
| Mar   | 1300  | NULL       |

---

##  6. `FIRST_VALUE()`

 Partition/group ke first record ka value laata hai.

 *Use Case*: First order or first purchase amount track karna.

```sql
SELECT customer_id, order_date, amount,
       FIRST_VALUE(amount) OVER (PARTITION BY customer_id ORDER BY order_date) AS first_order_amount
FROM orders;
```

---

##  7. `LAST_VALUE()`

 Partition ka last value return karta hai (use with proper frame settings).

 *Use Case*: Last salary ya latest activity find karna.

```sql
SELECT employee_id, salary_date, salary,
       LAST_VALUE(salary) OVER (PARTITION BY employee_id ORDER BY salary_date ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS latest_salary
FROM salaries;
```

---

##  8. `SUM() OVER()` – Cumulative/Running Total

```sql
SELECT month, sales,
       SUM(sales) OVER (ORDER BY month) AS running_total
FROM monthly_sales;
```

 **Output:**

| month | sales | running_total |
|-------|-------|----------------|
| Jan   | 1000  | 1000           |
| Feb   | 1200  | 2200           |
| Mar   | 1500  | 3700           |

---

##  9. `AVG() OVER()` – Running/Cumulative Average

```sql
SELECT month, sales,
       AVG(sales) OVER (ORDER BY month) AS running_avg
FROM monthly_sales;
```

---

##  10. `COUNT() OVER()` – Row Count without GROUP BY

💡 *Use Case*: Count how many orders per customer without grouping.

```sql
SELECT customer_id, order_id,
       COUNT(*) OVER (PARTITION BY customer_id) AS total_orders
FROM orders;
```

---

##  PARTITION BY & ORDER BY – Kaise kaam karte hain?

###  `PARTITION BY`: Data ko group karta hai (lekin aggregate nahi karta)
###  `ORDER BY`: Us group ke andar sorting karta hai (ranking ya time series ke liye)

```sql
SELECT department, employee, salary,
       RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS dept_rank
FROM employees;
```

---

## 📈 Real-Life Examples in Data Analysis

###  Customer ke Top 3 Orders
```sql
SELECT *
FROM (
  SELECT customer_id, order_id, amount,
         ROW_NUMBER() OVER (PARTITION BY customer_id ORDER BY amount DESC) AS rn
  FROM orders
) x
WHERE rn <= 3;
```

###  Running Total of Sales per Region
```sql
SELECT region, month, sales,
       SUM(sales) OVER (PARTITION BY region ORDER BY month) AS region_running_sales
FROM sales_data;
```

---

##  Summary Table

| Function         | Kaam (Use)                                 |
|------------------|---------------------------------------------|
| ROW_NUMBER()     | Unique row number per partition             |
| RANK()           | Ranking with gaps (ties)                    |
| DENSE_RANK()     | Ranking without gaps                        |
| LAG()            | Previous row ka value                       |
| LEAD()           | Next row ka value                           |
| FIRST_VALUE()    | Pehli value partition mein                  |
| LAST_VALUE()     | Aakhri value partition mein                 |
| SUM() OVER()     | Running/cumulative total                    |
| AVG() OVER()     | Running average                             |
| COUNT() OVER()   | Total count per partition                   |
| PARTITION BY     | Groups data logically                       |
| ORDER BY (OVER)  | Sorts rows within each partition            |

---

 **Conclusion**:  
Window functions **group by ke bina aggregation, ranking, aur lag/lead analysis** karne ka sabse powerful tool hain — khas tor par **financial reporting**, **customer behavior tracking**, aur **time series analysis** mein.



