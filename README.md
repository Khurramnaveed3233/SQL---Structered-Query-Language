#  SQL Functions for Data Analysis 

Yeh examples real-world data analysis mein use hotay hain, jaise SQL databases ya Python Pandas DataFrames mein filtering karte waqt.

---

##  DDL (Data Definition Language)

**DDL ka kaam hota hai database ke structure ko define karna** — jaise tables, views ya indexes banana, modify karna ya delete karna. Data analysts analysis start karne se pehle mostly tables ya views banate hain using DDL.

---

### 1.  CREATE

 **Kaam**: Nayi table ya object create karta hai.

 **Syntax**:
```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    ...
);
```

 **Example**:
```sql
CREATE TABLE sales_data (
    sale_id INT,
    customer_name VARCHAR(100),
    sale_amount DECIMAL(10,2),
    sale_date DATE
);
```

 **Output**: Ek nayi table `sales_data` create ho gayi with 4 columns.

 **Real-world Use**: Jab data analyst naye sales records analyze karna chahta hai, to pehle table structure create karta hai jisme woh data load karega.

---

### 2.  ALTER

 **Kaam**: Pehle se existing table ka structure change karta hai.

 **Syntax**:
```sql
ALTER TABLE table_name
ADD column_name datatype;
```

 **Example**:
```sql
ALTER TABLE sales_data ADD region VARCHAR(50);
```

 **Output**: `sales_data` table mein ek naya column `region` add ho gaya.

 **Real-world Use**: Jab analyst ko regional performance analyze karni ho aur pehle region ka column nahi tha.

---

### 3.  DROP

 **Kaam**: Table ko permanently database se delete karta hai.

 **Syntax**:
```sql
DROP TABLE table_name;
```

 **Example**:
```sql
DROP TABLE sales_data;
```

 **Output**: `sales_data` table permanently delete ho gayi — data + structure dono gaye.

 **Real-world Use**: Jab old ya temporary tables ko clean karna ho analysis ke baad.

 **Note**: Ye irreversible hota hai — backup nahi hota to data chala jata hai.

---

### 4.  TRUNCATE

 **Kaam**: Table ka sara data delete karta hai, magar table structure rehta hai.

 **Syntax**:
```sql
TRUNCATE TABLE table_name;
```

 **Example**:
```sql
TRUNCATE TABLE sales_data;
```

 **Output**: `sales_data` table empty ho gayi, lekin structure ab bhi maujood hai.

 **Real-world Use**: Jab ek analyst nayi data load karna chahta hai test ya production ke liye without changing table design.

---

##  Summary Table

| Command  | Syntax Example                            | Kaam                              | Output                             | Use Case                          |
|----------|--------------------------------------------|-----------------------------------|------------------------------------|-----------------------------------|
| CREATE   | `CREATE TABLE sales_data (...)`            | Nayi table banata hai             | Empty table with defined columns   | Analysis ke liye data rakhne ke liye |
| ALTER    | `ALTER TABLE sales_data ADD region ...`    | Column add karta hai              | Table mein naye column add         | New metrics ya dimension add karna |
| DROP     | `DROP TABLE sales_data`                    | Table permanently delete karta hai| Table & data dono delete           | Old/test table hatana             |
| TRUNCATE | `TRUNCATE TABLE sales_data`                | Sirf data delete karta hai        | Table khali ho jati hai            | Clean slate se analysis start karna |

---

 **Real-time Data Analysis Mein DDL Ka Use:**
- Data warehouse ya BI dashboard banane se pehle tables design karna
- ETL processes mein staging tables define karna
- Data clean-up aur backup ke liye TRUNCATE
- Security & maintenance ke liye DROP ya ALTER

##  DML (Data Manipulation Language)

**DML SQL ka wo part hai jiska use hum table ke andar data insert, update, ya delete karne ke liye karte hain.** Data analysts aur data engineers mostly DML use karte hain jab woh data analysis ke liye tables mein data manage karte hain.

---

### 1.  INSERT

 **Kaam**: Table ke andar naye records add karta hai.

 **Syntax**:
```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

 **Example**:
```sql
INSERT INTO sales_data (sale_id, customer_name, sale_amount, sale_date, region)
VALUES (1, 'Ali Khan', 1200.50, '2025-07-01', 'Punjab');
```

 **Output**: Ek naya row insert ho gaya `sales_data` table mein.

 **Real-time Use**: Jab analyst sales data manually enter kar raha ho ya kisi ETL pipeline ke zariye data load kar raha ho.

---

### 2.  UPDATE

 **Kaam**: Table ke existing records ko modify karta hai.

 **Syntax**:
```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

 **Example**:
```sql
UPDATE sales_data
SET sale_amount = 1300.00
WHERE sale_id = 1;
```

 **Output**: Row jisme `sale_id = 1` hai uska `sale_amount` ab 1300.00 ho gaya.

 **Real-time Use**: Analyst ne dekha ke koi data galat load ho gaya, to woh correct karne ke liye `UPDATE` karta hai.

 **Note**: Hamesha `WHERE` clause use karo warna sari table update ho sakti hai!

---

### 3.  DELETE

 **Kaam**: Table ke andar se specific rows delete karta hai.

 **Syntax**:
```sql
DELETE FROM table_name
WHERE condition;
```

 **Example**:
```sql
DELETE FROM sales_data
WHERE sale_id = 1;
```

 **Output**: Row jisme `sale_id = 1` tha, wo table se delete ho gaya.

 **Real-time Use**: Jab analyst ko duplicate ya test data remove karna ho.

 **Note**: Agar `WHERE` use nahi kiya to saari table ka data delete ho sakta hai.

---

##  Summary Table

| Command | Syntax Example | Kaam | Output | Use Case |
|--------|----------------|------|--------|----------|
| INSERT | `INSERT INTO sales_data (...) VALUES (...)` | Table mein naya data daalna | Naya row add hota hai | Nayi sales entry insert karna |
| UPDATE | `UPDATE sales_data SET ... WHERE ...` | Existing row update karna | Specific data change hota hai | Galat entry ko correct karna |
| DELETE | `DELETE FROM sales_data WHERE ...` | Row delete karna | Row remove ho jata hai | Duplicate ya unwanted data delete karna |

---

##  Real-Time Data Analysis Mein DML Ka Use

1.  **INSERT** – Jab naye data sources se records load kiye ja rahe ho.
2.  **UPDATE** – Jab data cleanse process mein values sahi ki ja rahi ho.
3.  **DELETE** – Jab NULL ya test entries remove ki ja rahi ho analysis se pehle.

**Example Scenario:**
Data analyst ko ek weekly sales report banani hai. Wo ETL tool se data `INSERT` karta hai, fir agar koi entry galat ho to `UPDATE`, aur agar duplicates milte hain to `DELETE`.

##  DQL – Data Query Language

 **Kaam**: Table se data fetch (query) karne ke liye use hoti hai. Ye data analysis ka sabse important part hai.

 **Command**: `SELECT`

---

### 1.  SELECT

 **Syntax**:
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```

 **Example**:
```sql
SELECT customer_name, sale_amount
FROM sales_data
WHERE region = 'Punjab';
```

 **Output**:
| customer_name | sale_amount |
|---------------|-------------|
| Ali Khan      | 1300.00     |

 **Real-time Use**: Analyst Punjab region ke sales dekh raha hai report ke liye.

---

##  DCL – Data Control Language

 **Kaam**: User permissions aur access rights control karne ke liye use hoti hai. Ye security aur collaboration mein help karti hai.

 **Commands**: `GRANT`, `REVOKE`

---

### 1.  GRANT

 **Syntax**:
```sql
GRANT SELECT, INSERT ON sales_data TO analyst_user;
```

 **Output**: `analyst_user` ab `sales_data` table ko SELECT aur INSERT kar sakta hai.

 **Real-time Use**: Analyst ko data access dena report banane ke liye.

---

### 2.  REVOKE

 **Syntax**:
```sql
REVOKE INSERT ON sales_data FROM analyst_user;
```

 **Output**: `analyst_user` ka INSERT access hata diya gaya.

 **Real-time Use**: Jab analyst ka role change ho jaye ya unauthorized action prevent karna ho.

---

##  TCL – Transaction Control Language

 **Kaam**: Transactions manage karna — yaani multiple SQL commands ko ek unit ke tor par execute karna. Useful for maintaining **data consistency and recovery**.

 **Commands**: `COMMIT`, `ROLLBACK`

---

### 1.  COMMIT

 **Syntax**:
```sql
BEGIN TRANSACTION;
UPDATE sales_data SET sale_amount = 1500 WHERE sale_id = 2;
COMMIT;
```

 **Output**: Sale amount update ho gaya permanently — changes save ho gayi.

 **Real-time Use**: Jab data analyst ne analysis ke liye records fix kiye aur save karne hain.

---

### 2.  ROLLBACK

 **Syntax**:
```sql
BEGIN TRANSACTION;
UPDATE sales_data SET sale_amount = 99999 WHERE sale_id = 2;
ROLLBACK;
```

 **Output**: Galat update ki wajah se change cancel ho gaya — original value wapas aa gayi.

 **Real-time Use**: Jab analyst ne accidentally galat data update kar diya ho aur usko undo karna ho.

---

##  Summary Table

| Type | Commands | Kaam | Example Use Case | Output |
|------|----------|------|------------------|--------|
| DQL  | SELECT   | Data ko query karna | Sales report banani ho | Filtered rows |
| DCL  | GRANT, REVOKE | Access dena ya lena | Analyst ko SELECT access dena ya lena | Permissions change |
| TCL  | COMMIT, ROLLBACK | Transactions ko manage karna | ETL ya updates ke dauran data save/undo karna | Permanent save ya cancel |

---

##  Real-World Scenario for Data Analysts

- Tum `SELECT` se filtered data nikaalte ho charts ke liye.
- Tumhare team members ko limited access dena ho to `GRANT`/`REVOKE` use hota hai.
- Data updates karte waqt agar galti ho jaye to `ROLLBACK` helpful hota hai warna `COMMIT` se changes save kar lete hain

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

# SQL Date & Time Functions: 

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


The `CAST()` function is used to **convert a data type** into another.

**Syntax:**
```sql
CAST(expression AS target_data_type)
```

**Example:**
```sql
SELECT CAST(JoinDate AS DATE) AS JoinDateOnly
FROM Customers;
```
➡ Converts full datetime to just the `DATE` part.

---

## 11. `CONVERT()` – Convert & Format Dates


The `CONVERT()` function is also used to **change data types**, but it supports **style codes** (especially useful when formatting dates).

**Syntax:**
```sql
CONVERT(target_data_type, expression, style_code)
```

**Example:**
```sql
SELECT CONVERT(varchar, JoinDate, 102) AS FormattedJoinDate
FROM Customers;
```
➡ Converts `JoinDate` into a string formatted as `yyyy.mm.dd`.


### 📌 Common Date Style Codes

| Style Code | Format        | Example      | Description             |
|------------|---------------|--------------|-------------------------|
| `102`      | `yyyy.mm.dd`  | 2025.08.02   | ISO-style with dots     |
| `101`      | `mm/dd/yyyy`  | 08/02/2025   | US format               |
| `103`      | `dd/mm/yyyy`  | 02/08/2025   | UK format               |
| `104`      | `dd.mm.yyyy`  | 02.08.2025   | German style            |
| `105`      | `dd-mm-yyyy`  | 02-08-2025   | Italian style           |
| `112`      | `yyyymmdd`    | 20250802     | ISO standard no symbols |

---

### ✅ Summary

- Use `CAST()` for **basic type conversion**.
- Use `CONVERT()` when you need **specific formatting**, especially for **dates** using style codes like `102`.


---

##  Real-Time Analytics Use Cases

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

# SQL Window Functions 

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

 **Output:**

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

 **Output:**

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
-- 👇 Example Dataset: Customers Table

| FullName | Status   | PurchaseAmount | JoinDate   |
|----------|----------|----------------|------------|
| Ali      | Active   | 500            | 2021-01-01 |
| Sana     | Active   | 700            | 2021-02-01 |
| Ahmed    | Inactive | 300            | 2020-12-01 |
| Ayesha   | Inactive | 600            | 2021-03-01 |

--------------------------------------------------------------------------------

-- 🥇 FIRST_VALUE(): Har group ka pehla PurchaseAmount return karta hai
SELECT 
  FullName,
  Status,
  PurchaseAmount,
  JoinDate,
  FIRST_VALUE(PurchaseAmount) OVER (
    PARTITION BY Status 
    ORDER BY JoinDate
  ) AS FirstPurchase
FROM Customers;

-- 📌 Explanation:
-- Status ke mutabiq group banayenge (Active/Inctive)
-- Har group mein rows ko JoinDate ke mutabiq order karenge
-- Pehle record ka PurchaseAmount return hoga sab rows ke liye

-- ✅ Output:
| FullName | Status   | PurchaseAmount | FirstPurchase |
|----------|----------|----------------|----------------|
| Ali      | Active   | 500            | 500            |
| Sana     | Active   | 700            | 500            |
| Ahmed    | Inactive | 300            | 300            |
| Ayesha   | Inactive | 600            | 300            |

--------------------------------------------------------------------------------

-- 🏁 LAST_VALUE(): Har group ka akhri PurchaseAmount return karta hai
-- 🔐 Important: WINDOW RANGE define karna lazmi hai warna incorrect result milega
SELECT 
  FullName,
  Status,
  PurchaseAmount,
  JoinDate,
  LAST_VALUE(PurchaseAmount) OVER (
    PARTITION BY Status 
    ORDER BY JoinDate 
    ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING
  ) AS LastPurchase
FROM Customers;

-- 📌 Explanation:
-- Har group ke andar sabse akhri record ka PurchaseAmount sab rows mein show hoga
-- "UNBOUNDED PRECEDING AND FOLLOWING" se pura window consider hoga

-- ✅ Output:
| FullName | Status   | PurchaseAmount | LastPurchase |
|----------|----------|----------------|----------------|
| Ali      | Active   | 500            | 700            |
| Sana     | Active   | 700            | 700            |
| Ahmed    | Inactive | 300            | 600            |
| Ayesha   | Inactive | 600            | 600            |











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

 *Use Case*: Count how many orders per customer without grouping.

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

##  Real-Life Examples in Data Analysis

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

#  SQL Conditional Functions 

SQL mein conditional functions ka use hum tab karte hain jab humein kisi condition ke base par values assign karni hoti hain. Data science & analysis mein yeh kaafi useful hoti hain – jaise classification, flagging, ya NULL values ka handling.

---

## 1. CASE WHEN THEN ELSE END

 **Explanation**:
IF-ELSE jaisa logic hota hai SQL mein. Har row ke liye alag condition check hoti hai.

 **Real-World Example**:
Customer ke salary ke basis par unko "High", "Medium", ya "Low" earning category mein daalna.

```sql
SELECT name, salary,
  CASE 
    WHEN salary >= 100000 THEN 'High Earner'
    WHEN salary BETWEEN 50000 AND 99999 THEN 'Medium Earner'
    ELSE 'Low Earner'
  END AS income_group
FROM customers;
```

 **Output**:

| name  | salary  | income_group   |
|-------|---------|----------------|
| Ali   | 120000  | High Earner    |
| Sara  | 75000   | Medium Earner  |
| Omer  | 30000   | Low Earner     |

 **Use Cases**:
- Risk score category assign karna
- Age ke basis par group banana
- Custom segmentation

---

## 2. COALESCE()

 **Explanation**:
Jo pehli non-NULL value milti hai wo return karta hai. Alternative values assign karne ke liye useful.

 **Real-World Example**:
Agar kisi customer ka email missing hai to phone ya default message show karo.

```sql
SELECT name, COALESCE(email, phone, 'No Contact Info') AS contact_info
FROM customers;
```

 **Output**:

| name  | contact_info       |
|-------|--------------------|
| Ali   | ali@example.com    |
| Sara  | 03001234567        |
| Omer  | No Contact Info    |

 **Use Cases**:
- NULL values fill karna
- Reporting mein fallback contact ya values show karna
- Data cleaning

---

## 3. NULLIF()

 **Explanation**:
Agar dono values same hon to NULL return karta hai, warna pehli value return hoti hai.

 **Real-World Example**:
Divide by zero error avoid karne ke liye targets ko 0 hone par NULL bana do.

```sql
SELECT name, sales, targets,
  sales / NULLIF(targets, 0) AS achievement_ratio
FROM sales_data;
```

 **Output**:

| name  | sales | targets | achievement_ratio |
|-------|-------|---------|-------------------|
| Ali   | 5000  | 2500    | 2.0               |
| Sara  | 3000  | 0       | NULL              |
| Omer  | 2000  | 1000    | 2.0               |

 **Use Cases**:
- Divide by 0 error handle karna
- Conditional logic with NULL values
- Clean numeric analysis

---

## 4. IIF()

 **Explanation**:
Short version of CASE – sirf ek single condition ke liye use hota hai (ternary logic).

 **Real-World Example**:
Bonus eligible hai ya nahi based on salary threshold.

```sql
SELECT name, salary,
  IIF(salary >= 60000, 'Bonus Eligible', 'Not Eligible') AS bonus_status
FROM employees;
```

 **Output**:

| name  | salary | bonus_status     |
|-------|--------|------------------|
| Ali   | 65000  | Bonus Eligible   |
| Sara  | 40000  | Not Eligible     |
| Omer  | 60000  | Bonus Eligible   |

 **Use Cases**:
- Flags generate karna (Yes/No)
- Binary decision making
- Quick logic for dashboards

---

##  Summary Table:

| Function      | Kya karta hai                                | Real Data Use |
|---------------|----------------------------------------------|----------------|
| CASE WHEN     | Multiple condition check aur value return    | Segmentation, classification |
| COALESCE()    | Pehli non-NULL value return karta hai         | Fallback values, NULL handling |
| NULLIF()      | Dono same ho to NULL return karta hai         | Avoid divide-by-zero |
| IIF()         | Quick if-else for single condition            | Flags, Yes/No logic |

---

 **Conclusion**:
 
Ye conditional functions data analyst ke toolkit ka core part hain. Inka use reporting, dashboards, feature engineering, and anomaly detection mein hota hai. Especially tab jab data inconsistent ho ya business rules apply karne ho.

#  SQL Conditional Functions + Set Operators 

SQL mein Conditional aur Set Operators dono ka bohot important role hota hai real-time data analysis mein — jaise decision-making, missing data handle karna, aur multi-query data combine karna. Neeche sab kuch detail mein diya gaya hai:

---

##  1. CASE WHEN THEN ELSE END

 **Explanation**:
Yeh IF-ELSE jaisa logic lagata hai rows pe based on conditions.

 **Use Case**: Customer salary ke base par earning group banani hai.

```sql
SELECT name, salary,
  CASE 
    WHEN salary >= 100000 THEN 'High'
    WHEN salary BETWEEN 50000 AND 99999 THEN 'Medium'
    ELSE 'Low'
  END AS income_level
FROM customers;
```

 **Output**:

| name  | salary  | income_level |
|-------|---------|---------------|
| Ali   | 120000  | High          |
| Sara  | 75000   | Medium        |
| Omer  | 30000   | Low           |

 **Real Use**:
- Risk scoring
- Tier grouping
- Custom business logic apply karna

---

## 2. COALESCE()

 **Explanation**:
Pehli non-NULL value return karta hai jo list mein pehli milti ho.

 **Use Case**: Contact column create karni hai jahan email ya phone ho, warna "No Info".

```sql
SELECT name, COALESCE(email, phone, 'No Info') AS contact_info
FROM users;
```

 **Output**:

| name  | contact_info   |
|-------|----------------|
| Ali   | ali@gmail.com  |
| Sara  | 03001234567    |
| Omer  | No Info        |

 **Real Use**:
- Missing data ka replacement
- Reporting dashboards
- Default values assign karna

---

##  3. NULLIF()

 **Explanation**:
Agar dono values same hoon to NULL return karega, warna pehli value.

 **Use Case**: Divide-by-zero error avoid karna.

```sql
SELECT name, sales, target,
  sales / NULLIF(target, 0) AS performance_ratio
FROM performance_data;
```

 **Output**:

| name  | sales | target | performance_ratio |
|-------|-------|--------|-------------------|
| Ali   | 5000  | 2500   | 2.0               |
| Sara  | 4000  | 0      | NULL              |

 **Real Use**:
- Safe division karna
- NULLs se bachna
- Smart math operations

---

##  4. IIF()

 **Explanation**:
Simple IF condition – CASE ka short version.

 **Use Case**: Eligible for bonus ya nahi salary base par.

```sql
SELECT name, salary,
  IIF(salary >= 60000, 'Eligible', 'Not Eligible') AS bonus_status
FROM employees;
```

 **Output**:

| name  | salary | bonus_status   |
|-------|--------|----------------|
| Ali   | 70000  | Eligible       |
| Sara  | 45000  | Not Eligible   |

 **Real Use**:
- Quick flags
- Binary classification
- Fast condition checks

---

##  Set Operators

Set operators ka use hum multiple queries ke result ko combine karne ke liye karte hain. Har query ka number of columns aur data types same hone chahiye.

---

##  5. UNION

 **Explanation**: Duplicates hata ke combine karta hai multiple SELECTs.

 **Use Case**: Active + retired employees ka unique list.

```sql
SELECT name FROM active_employees
UNION
SELECT name FROM retired_employees;
```

 **Output**:

| name     |
|----------|
| Ali      |
| Sara     |
| Aslam    |

 **Real Use**:
- Unique customer list
- Combining old + new data
- Duplicate-free joins

---

##  6. UNION ALL

 **Explanation**: Duplicates ko include karta hai. Fast hota hai UNION se.

 **Use Case**: Total transactions list from online + offline.

```sql
SELECT transaction_id FROM online_sales
UNION ALL
SELECT transaction_id FROM offline_sales;
```

 **Output**: Includes all transactions, even if repeated

| transaction_id |
|----------------|
| T001           |
| T002           |
| T001           |

 **Real Use**:
- Logs combine karna
- Raw data analysis
- Faster performance

---

##  7. INTERSECT

 **Explanation**: Sirf wo rows return karta hai jo dono queries mein common hoti hain.

 **Use Case**: Customers jinhone app + website dono pe order diya.

```sql
SELECT customer_id FROM app_orders
INTERSECT
SELECT customer_id FROM web_orders;
```

 **Output**:

| customer_id |
|-------------|
| C101        |
| C204        |

 **Real Use**:
- Cross-channel user analysis
- Loyalty user tracking
- Common data analysis

---

##  8. EXCEPT

 **Explanation**: Pehli query ki wo rows jo doosri mein nahi hain.

 **Use Case**: Customers who bought online, but never in-store.

```sql
SELECT customer_id FROM online_orders
EXCEPT
SELECT customer_id FROM store_orders;
```

 **Output**:

| customer_id |
|-------------|
| C305        |
| C498        |

 **Real Use**:
- Unique audience detection
- Channel gap analysis
- Targeted marketing

---

##  Summary Table:

| Function       | Kya karta hai                                | Real Analysis Use Case        |
|----------------|----------------------------------------------|-------------------------------|
| CASE WHEN      | Conditional logic apply karta hai            | Segment, band, risk flag      |
| COALESCE()     | Pehli non-null value return karta hai         | NULL handle, fallback data    |
| NULLIF()       | Same value ho to NULL return karta hai        | Division safety               |
| IIF()          | IF-ELSE ka shortcut hai                       | Binary flags, eligibility     |
| UNION          | Duplicates ko remove karke combine karta hai  | Unique lists                  |
| UNION ALL      | Duplicates ke sath combine karta hai          | Logs, fast union              |
| INTERSECT      | Common records dono queries mein              | Cross-segment user match      |
| EXCEPT         | Pehli query ki non-matching rows return karta hai | Exclusive segment analysis    |

---

Ye sab functions aur operators data analysis workflows, dashboards, ETL, customer segmentation, and business rule validation mein commonly use hote hain.

#  SQL Joins Explained 

SQL Joins ka use do ya zyada tables ko connect karke ek combined result banane ke liye hota hai. Data analysis mein yeh bahut important hota hai — jaise customer data ko order data ke sath link karna, ya regions ko sales se join karna.

---

## 1 INNER JOIN

 **Explanation**: Sirf wo rows return karta hai jo dono tables mein match karti hain.

 **Use Case**: Customers jinhon ne order kiya ho.

```sql
SELECT c.customer_id, c.name, o.order_id
FROM customers c
INNER JOIN orders o ON c.customer_id = o.customer_id;
```

 **Output**:

| customer_id | name  | order_id |
|-------------|-------|----------|
| C001        | Ali   | O101     |
| C002        | Sara  | O102     |

 **Real Use**:
- Active customers analysis
- Matched records only
- Transaction-based dashboards

---

## 2 LEFT JOIN (LEFT OUTER JOIN)

 **Explanation**: Left table ki saari rows laata hai, even agar match na ho right table mein.

 **Use Case**: Sab customers dikhao, chahe order kiya ho ya nahi.

```sql
SELECT c.customer_id, c.name, o.order_id
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id;
```

 **Output**:

| customer_id | name  | order_id |
|-------------|-------|----------|
| C001        | Ali   | O101     |
| C002        | Sara  | O102     |
| C003        | Aslam | NULL     |

 **Real Use**:
- Customer retention analysis
- NULL-based filtering
- Who didn't perform any action

---

## 3 RIGHT JOIN (RIGHT OUTER JOIN)

 **Explanation**: Right table ki saari rows laata hai, chahe match na ho left mein.

 **Use Case**: Sab orders dikhao, chahe customer missing ho.

```sql
SELECT c.customer_id, c.name, o.order_id
FROM customers c
RIGHT JOIN orders o ON c.customer_id = o.customer_id;
```

 **Output**:

| customer_id | name  | order_id |
|-------------|-------|----------|
| C001        | Ali   | O101     |
| C002        | Sara  | O102     |
| NULL        | NULL  | O103     |

 **Real Use**:
- orphan records check karna
- System integrity validate karna

---

## 4 FULL OUTER JOIN

 **Explanation**: Dono tables ki saari rows return karta hai, match ho ya na ho.

 **Use Case**: Complete customer + order activity (with unmatched too).

```sql
SELECT c.customer_id, c.name, o.order_id
FROM customers c
FULL OUTER JOIN orders o ON c.customer_id = o.customer_id;
```

 **Output**:

| customer_id | name  | order_id |
|-------------|-------|----------|
| C001        | Ali   | O101     |
| C002        | Sara  | O102     |
| C003        | Aslam | NULL     |
| NULL        | NULL  | O103     |

 **Real Use**:
- Comprehensive data view
- Mismatches identify karna
- Audit reports

---

## 5 CROSS JOIN

 **Explanation**: Har row ek table ki, doosri table ki har row ke sath combine hoti hai (Cartesian product).

 **Use Case**: Sab possible combinations banani hain — e.g., products × regions.

```sql
SELECT p.product_name, r.region_name
FROM products p
CROSS JOIN regions r;
```

 **Output** (3 products × 2 regions = 6 rows):

| product_name | region_name |
|--------------|-------------|
| Mobile       | North       |
| Mobile       | South       |
| Laptop       | North       |
| Laptop       | South       |
| TV           | North       |
| TV           | South       |

 **Real Use**:
- Scenario simulation
- Sales plan matrix
- Test data generation

---

## 6 SELF JOIN

 **Explanation**: Table khud se join hoti hai — usually hierarchy ke liye.

 **Use Case**: Employees ke managers dikhane hain (same table mein).

```sql
SELECT e1.emp_name AS employee, e2.emp_name AS manager
FROM employees e1
LEFT JOIN employees e2 ON e1.manager_id = e2.emp_id;
```

 **Output**:

| employee | manager  |
|----------|----------|
| Ali      | Sara     |
| Sara     | Aslam    |
| Aslam    | NULL     |

 **Real Use**:
- Organizational hierarchy
- Recursive relationships
- Tree structures

---

##  Summary Table:

| Join Type        | Return karta hai...                            | Real Use Case                    |
|------------------|------------------------------------------------|----------------------------------|
| INNER JOIN       | Sirf matching rows dono tables se              | Linked data only                 |
| LEFT JOIN        | Left table ke saare rows + matched from right  | Find missing right-side data     |
| RIGHT JOIN       | Right table ke saare rows + matched from left  | Find missing left-side data      |
| FULL OUTER JOIN  | Saari rows dono tables se, matched + unmatched | Full picture, audit reports      |
| CROSS JOIN       | Har row ke saath har row ka combination        | Simulations, planning            |
| SELF JOIN        | Table khud se join hoti hai                    | Hierarchy, employee-manager view |

---

 Real-time data analysis mein joins ka use hota hai:
- Customer purchase behavior track karne ke liye
- Sales + Region ya Date tables ko combine karne ke liye
- Reports aur dashboards banane ke liye
- Business intelligence mein relationship mapping ke liye

#  Subqueries & CTEs in SQL 

---

##  SUBQUERIES

Subquery ka matlab hai ek query ke andar doosri query likhna. Ye SELECT, WHERE, ya FROM clause mein ho sakti hai.

---

### 1 Subquery in SELECT

 **Explanation**: Ek subquery SELECT mein lagake derived ya calculated value nikalte hain.

 **Use Case**: Har employee ki salary ko average salary ke sath compare karo.

```sql
SELECT emp_name, salary,
       (SELECT AVG(salary) FROM employees) AS avg_salary
FROM employees;
```

 **Output**:

| emp_name | salary | avg_salary |
|----------|--------|------------|
| Ali      | 50000  | 56666.66   |
| Sara     | 60000  | 56666.66   |
| Aslam    | 60000  | 56666.66   |

 **Real Use**:
- Relative comparisons
- Standard benchmarks calculate karna

---

### 2 Subquery in WHERE

 **Explanation**: Filter karne ke liye subquery use hoti hai.

 **Use Case**: Wo customers dikhayein jinhon ne order diya hai.

```sql
SELECT name FROM customers
WHERE customer_id IN (SELECT customer_id FROM orders);
```

 **Output**:

| name  |
|-------|
| Ali   |
| Sara  |

 **Real Use**:
- Existence check
- Related entity filtering

---

### 3 Subquery in FROM

 **Explanation**: Subquery ek temporary table create karti hai jise hum alias dekar use karte hain.

 **Use Case**: Department-wise average salary dikhani hai.

```sql
SELECT dept_id, AVG_SALARY
FROM (
    SELECT dept_id, AVG(salary) AS AVG_SALARY
    FROM employees
    GROUP BY dept_id
) AS dept_avg;
```

 **Output**:

| dept_id | AVG_SALARY |
|---------|------------|
| D001    | 52000      |
| D002    | 60000      |

 **Real Use**:
- Derived tables
- Complex aggregations
- Dashboard-level summaries

---

##  EXISTS vs IN vs NOT IN

---

### EXISTS

 **Explanation**: Check karta hai agar subquery se koi record return ho raha ho.

 **Use Case**: Wo customers jinke orders hain.

```sql
SELECT name FROM customers c
WHERE EXISTS (
  SELECT 1 FROM orders o WHERE o.customer_id = c.customer_id
);
```

 **Real Use**:
- Performance ke liye fast on indexed columns
- Existence-based filtering

---

### IN

 **Explanation**: List ke against matching karta hai.

```sql
SELECT name FROM customers
WHERE customer_id IN (SELECT customer_id FROM orders);
```

 **Real Use**:
- Small lists ke liye theek hai
- Readability zyada hoti hai

---

### NOT IN

 **Explanation**: Wo records jo list mein nahi hain.

```sql
SELECT name FROM customers
WHERE customer_id NOT IN (SELECT customer_id FROM orders);
```

 **Output**:

| name  |
|-------|
| Aslam |

 **Real Use**:
- Non-participating records dhoondhna
- Jaise inactive customers

---

##  Common Table Expressions (CTEs)

CTE temporary named result set hota hai jo `WITH` keyword ke sath banta hai.

---

### 1 Simple CTE

 **Explanation**: CTE define karke usko aage ki query mein use karte hain.

 **Use Case**: Top earning employees nikaalne hain.

```sql
WITH HighEarners AS (
  SELECT emp_name, salary FROM employees WHERE salary > 55000
)
SELECT * FROM HighEarners;
```

 **Output**:

| emp_name | salary |
|----------|--------|
| Sara     | 60000  |
| Aslam    | 60000  |

 **Real Use**:
- Clean code likhne ke liye
- Reusable subqueries

---

### 2 RECURSIVE CTE

 **Explanation**: Jab data hierarchical ho jaise employee-manager, ya category-subcategory.

 **Use Case**: Employee hierarchy banana (manager ke neeche kon kon hai).

```sql
WITH EmpHierarchy AS (
  SELECT emp_id, emp_name, manager_id
  FROM employees
  WHERE manager_id IS NULL
  UNION ALL
  SELECT e.emp_id, e.emp_name, e.manager_id
  FROM employees e
  JOIN EmpHierarchy h ON e.manager_id = h.emp_id
)
SELECT * FROM EmpHierarchy;
```

 **Output**:

| emp_id | emp_name | manager_id |
|--------|----------|------------|
| 1      | Aslam    | NULL       |
| 2      | Sara     | 1          |
| 3      | Ali      | 2          |

 **Real Use**:
- Organizational charts
- Category levels (Product Catalogs)
- Recursive tree structures

---

##  Summary

| Feature           | Real Use Case                           |
|-------------------|------------------------------------------|
| Subquery (SELECT) | Derived metrics, comparisons             |
| Subquery (WHERE)  | Filtering based on other tables          |
| Subquery (FROM)   | Temporary aggregated tables              |
| EXISTS            | Fast existence checks                    |
| IN / NOT IN       | Inclusion/exclusion lists                |
| CTE               | Modular & readable query building        |
| Recursive CTE     | Hierarchical data handling               |

---

 Data science ya analysis mein yeh concepts use hote hain:
- Dashboards & KPIs banane ke liye
- Business rule implementation
- Hierarchy analysis
- Performance-efficient complex queries likhne ke liye

#  DISTINCT, TOP / LIMIT, ORDER BY, GROUP BY, HAVING — 

---

##  1. DISTINCT

 **Kya karta hai?**
DISTINCT kisi column ya columns ki **duplicate values hata deta hai**.

 **Use Case (Real-world)**: Kitne unique cities se customers hain?

```sql
SELECT DISTINCT city FROM customers;
```

**Output**:

| city     |
|----------|
| Lahore   |
| Karachi  |
| Islamabad|

 **Real Use**:
- Unique categories ya regions nikalna
- Exploratory data analysis (EDA)

---

##  2. TOP / LIMIT

 **Kya karta hai?**
TOP (SQL Server) ya LIMIT (MySQL/PostgreSQL) results ki **maximum rows control** karta hai.

 **Use Case**: Top 5 highest paid employees dikhayein

### SQL Server:
```sql
SELECT TOP 5 emp_name, salary FROM employees ORDER BY salary DESC;
```

### MySQL/PostgreSQL:
```sql
SELECT emp_name, salary FROM employees ORDER BY salary DESC LIMIT 5;
```

 **Output**:

| emp_name | salary |
|----------|--------|
| Ali      | 90000  |
| Sara     | 85000  |
| Aslam    | 82000  |
| Ayesha   | 80000  |
| Zain     | 78000  |

 **Real Use**:
- Top N customers/products/orders
- Performance testing mein limited data lena

---

## 🔹 3. ORDER BY

 **Kya karta hai?**
ORDER BY results ko **sort** karta hai (ASC by default, ya DESC).

 **Use Case**: Employees ko salary ke hisaab se sort karna

```sql
SELECT emp_name, salary FROM employees ORDER BY salary DESC;
```

 **Output**:

| emp_name | salary |
|----------|--------|
| Ali      | 90000  |
| Sara     | 85000  |
| ...      | ...    |

 **Real Use**:
- Reports banate waqt sorting
- Rank-wise display
- Trends dekhna (sales by date)

---

##  4. GROUP BY

 **Kya karta hai?**
GROUP BY records ko group karta hai **aggregation functions** (SUM, AVG, COUNT) ke saath use karne ke liye.

 **Use Case**: Har city mein kitne customers hain?

```sql
SELECT city, COUNT(*) AS total_customers
FROM customers
GROUP BY city;
```

 **Output**:

| city     | total_customers |
|----------|------------------|
| Lahore   | 5                |
| Karachi  | 3                |

 **Real Use**:
- KPIs banane mein
- Regional, category-wise summaries

---

##  5. HAVING

 **Kya karta hai?**
HAVING filter karta hai **aggregated groups** ko (WHERE jaise but after GROUP BY).

 **Use Case**: Wo cities jahan 3 se zyada customers hain

```sql
SELECT city, COUNT(*) AS total_customers
FROM customers
GROUP BY city
HAVING COUNT(*) > 3;
```

 **Output**:

| city   | total_customers |
|--------|------------------|
| Lahore | 5                |

 **Real Use**:
- High-performing regions/groups filter karna
- Grouped summaries ke upar conditions lagana

---

##  Summary Table

| Keyword     | Kaam kya karta hai                        | Real-time Use Case                     |
|-------------|--------------------------------------------|----------------------------------------|
| DISTINCT    | Duplicate hataata hai                      | Unique values dekhna (e.g., cities)    |
| TOP / LIMIT | Limited records dikhata hai                | Top 10 products, recent 5 orders       |
| ORDER BY    | Sorting karta hai                          | Rankings, date-wise trends             |
| GROUP BY    | Group karta hai aggregation ke liye        | Sales by region, customer type         |
| HAVING      | Aggregated results ko filter karta hai     | High-value customers, active cities    |

---

** Tip:** 
Ye sab clauses commonly use hote hain **Power BI**, **Excel Pivot Tables**, aur **Python Pandas groupby()** operations mein — to agar aapko inka SQL version aata hai to aap visual tools aur coding mein easily transition kar sakte ho.


