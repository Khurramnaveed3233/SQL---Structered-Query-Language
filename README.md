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

Here is a complete and easy-to-understand `Markdown` note file that explains **SQL Joins** with examples using your attached database schema.

---


#  SQL Joins: Complete Guide

SQL Joins ka use hum tab karte hain jab humein **multiple tables ki information ikathhi dikhani ho**. Joins help karte hain rows ko connect karne mein based on related columns (e.g. foreign keys).

###  Types of Joins:
1. **INNER JOIN**
2. **LEFT JOIN** (Left Outer Join)
3. **RIGHT JOIN** (Right Outer Join)
4. **FULL OUTER JOIN**
5. **CROSS JOIN**
6. **SELF JOIN**

<img width="1068" height="596" alt="33" src="https://github.com/user-attachments/assets/c427e32f-9a7f-41ff-99e1-f441e0a35a6b" />

### 1. INNER JOIN

**Simple Matlab:**
Sirf woh rows jo dono tables me match ho jaati hain.

**Example:**
Customers jo order kar chuke hain.

**Analogy:**
2 lists me jo naam dono me common hain, bas unhi ko lo.

**SQL:**
SELECT c.FullName, o.OrderID
FROM Customers c
INNER JOIN Orders o
ON c.CustomerID = o.CustomerID;

## INNER JOIN Example

**Customers Table:**
| CustomerID | FullName   |
|------------|------------|
| 1          | Ali Khan   |
| 2          | Sara Malik |
| 3          | Usman Shah |
| 4          | Ayesha     |

**Orders Table:**
| OrderID | CustomerID |
|---------|------------|
| 101     | 1          |
| 102     | 2          |
| 103     | NULL       |
| 104     | 5          |

**Output (INNER JOIN):**
| FullName   | OrderID |
|------------|---------|
| Ali Khan   | 101     |
| Sara Malik | 102     |

**Explanation:**
Sirf woh rows dikhte hain jahan `Customers.CustomerID = Orders.CustomerID` match hota hai.  
CustomerID NULL` aur `CustomerID 5` ka match nahi mila, isliye wo rows skip ho gayi.

## LEFT JOIN Example

**Customers Table:**
| CustomerID | FullName   |
|------------|------------|
| 1          | Ali Khan   |
| 2          | Sara Malik |
| 3          | Usman Shah |
| 4          | Ayesha     |

**Orders Table:**
| OrderID | CustomerID |
|---------|------------|
| 101     | 1          |
| 102     | 2          |
| 103     | NULL       |
| 104     | 5          |

**Output (LEFT JOIN):**
| FullName   | OrderID |
|------------|---------|
| Ali Khan   | 101     |
| Sara Malik | 102     |
| Usman Shah | NULL    |
| Ayesha     | NULL    |

**Explanation:**
- LEFT JOIN me **Customers table ka poora data** aata hai.
- Agar matching order hai to `OrderID` show hota hai, warna `NULL` hota hai.
- `CustomerID 3` aur `CustomerID 4` ke orders nahi the, isliye unka `OrderID = NULL`.

---

## RIGHT JOIN Example

**Customers Table:**
| CustomerID | FullName   |
|------------|------------|
| 1          | Ali Khan   |
| 2          | Sara Malik |
| 3          | Usman Shah |
| 4          | Ayesha     |

**Orders Table:**
| OrderID | CustomerID |
|---------|------------|
| 101     | 1          |
| 102     | 2          |
| 103     | NULL       |
| 104     | 5          |

**Output (RIGHT JOIN):**
| FullName   | OrderID |
|------------|---------|
| Ali Khan   | 101     |
| Sara Malik | 102     |
| NULL       | 103     |
| NULL       | 104     |

**Explanation:**

- RIGHT JOIN me **Orders table ka poora data** aata hai.
- Agar matching customer hai to `FullName` show hota hai, warna `NULL` hota hai.
- OrderID 103` ka customer `NULL` tha aur `OrderID 104` ka customer ID 5 tha jo Customers table me nahi mila, isliye `FullName = NULL`.

## FULL OUTER JOIN Example (Easy & Detailed)

### Customers Table:
| CustomerID | FullName    |
|------------|-------------|
| 1          | Ali Khan    |
| 2          | Sara Malik  |
| 3          | Usman Shah  |
| 4          | Ayesha      |

### Orders Table:
| OrderID | CustomerID |
|---------|------------|
| 101     | 1          |
| 102     | 2          |
| 103     | NULL       |
| 104     | 5          |

**Output:**

| FullName   | OrderID |
|------------|---------|
| Ali Khan   | 101     |
| Sara Malik | 102     |
| Usman Shah | NULL    |
| Ayesha     | NULL    |
| NULL       | 103     |
| NULL       | 104     |

**Easy Explanation:**
FULL OUTER JOIN = **LEFT JOIN + RIGHT JOIN ka combination**.

- Dono tables ka **poora data** lete hain.  
- Agar match hota hai → dono ka data **same row me** aata hai.  
- Agar match nahi hota → jis side ka data missing hota hai, wahan **NULL** show hota hai.

**Example Breakdown:**
- **Ali Khan (1)** → Order **101** se match.  
- **Sara Malik (2)** → Order **102** se match.  
- **Usman Shah (3)** → No order → **OrderID = NULL**.  
- **Ayesha (4)** → No order → **OrderID = NULL**.  
- **Order 103 (NULL CustomerID)** → No customer → **FullName = NULL**.  
- **Order 104 (CustomerID = 5)** → No customer → **FullName = NULL**.

**Mechanism:**

1. **Pehle LEFT JOIN ka result leta hai**  
   - Left table ke saare rows + matching right table rows.  
   - Jo match nahi milta, unke right table columns **NULL** ho jate hain.  

2. **Phir RIGHT JOIN ka result leta hai**  
   - Right table ke saare rows + matching left table rows.  
   - Jo match nahi milta, unke left table columns **NULL** hote hain.  

3. **Dono results ko merge (UNION) karta hai**  
   - Is tarah dono tables ke saare rows aajate hain — chahe match ho ya na ho.  

--- 

## CROSS JOIN in SQL 

**Simple Definition:**  
CROSS JOIN ka matlab hai **dono tables ki har row ko dusre table ki har row ke saath jorna**.  
Yani har record Table A ka, Table B ke sabhi records ke saath mil jata hai.  
Isme **matching ka koi rule** nahi hota — bas combination banta hai.

**Formula:**  
`Total Rows = (Rows in Table A) × (Rows in Table B)`

---

### Example Tables

**Customers Table:**

| CustomerID | FullName   |
|------------|------------|
| 1          | Ali Khan   |
| 2          | Sara Malik |
| 3          | Usman Shah |
| 4          | Ayesha     |

**Orders Table:**

| OrderID | CustomerID |
|---------|------------|
| 101     | 1          |
| 102     | 2          |
| 103     | NULL       |
| 104     | 5          |

**Easy Roman Urdu Explanation:**

CROSS JOIN me hum dono tables ka **har possible combination** banate hain.

**Matlab:**
- Customers table me 4 log hain  
- Orders table me 4 order IDs hain  
- Har customer ke saath 4 orders match honge  
- Total **4 × 4 = 16 rows** output milengi  

**Example breakdown:**
- "Ali Khan" ke saath → 101, 102, 103, 104  
- "Sara Malik" ke saath → 101, 102, 103, 104  
- "Usman Shah" ke saath → 101, 102, 103, 104  
- "Ayesha" ke saath → 101, 102, 103, 104  

**Mechanism (CROSS JOIN):**

1. CROSS JOIN me **har row** left table ka, **har row** right table ke saath combine hota hai.  
2. Ye **Cartesian product** banata hai, matlab saare possible combinations.  
3. Formula:  

Total Rows = (Left Table Rows) × (Right Table Rows)

4. Koi ON condition nahi hoti, isliye har ek record doosre table ke har record ke saath pair hota hai.  
5. Zyada rows ka output aa sakta hai agar tables bade hon.  

---

#  SQL Window Functions Guide 

SQL Window Functions aise functions hote hain jo rows ke group par calculation karte hain, lekin **har row ka data preserve** karte hain. Ye analytics, ranking, running totals aur comparison ke liye kaafi useful hote hain.

---

##  Window Functions Kyun Use Karte Hain?

- Har row ka data rakhtay huay calculation karna
- Rank dena, running totals nikalna, pehle/baad wali row compare karna
- Complex subqueries ya self-joins se bachna

---

##  Syntax

```sql
<function_name>(expression) 
OVER (
    [PARTITION BY column_name]
    [ORDER BY column_name]
)
```

- `PARTITION BY`: Optional — data ko groups mein divide karta hai
- `ORDER BY`: Row ka order define karta hai

---

##  Common Window Functions

### 1. `ROW_NUMBER()`

Har partition ke andar unique row number assign karta hai.

```sql
SELECT 
  employee_name,
  department,
  ROW_NUMBER() OVER (PARTITION BY department ORDER BY salary DESC) AS row_num
FROM employees;
```

 **Output Example:**

| employee_name | department | row_num |
|---------------|------------|---------|
| Ali           | HR         | 1       |
| Ahmed         | HR         | 2       |
| Sara          | IT         | 1       |
| Bilal         | IT         | 2       |

---

### 2. `RANK()` vs `DENSE_RANK()`

- `RANK()` tie par number skip karta hai
- `DENSE_RANK()` tie par number skip nahi karta

```sql
SELECT 
  employee_name,
  salary,
  RANK() OVER (ORDER BY salary DESC) AS rank,
  DENSE_RANK() OVER (ORDER BY salary DESC) AS dense_rank
FROM employees;
```

 **Output Example:**

| employee_name | salary | rank | dense_rank |
|---------------|--------|------|------------|
| Ali           | 90000  | 1    | 1          |
| Sara          | 90000  | 1    | 1          |
| Ahmed         | 85000  | 3    | 2          |
| Bilal         | 80000  | 4    | 3          |

---

### 3. `NTILE(n)`

Data ko `n` equal groups (quantiles) mein divide karta hai.

```sql
SELECT 
  employee_name,
  salary,
  NTILE(4) OVER (ORDER BY salary DESC) AS quartile
FROM employees;
```

 **Output Example:**

| employee_name | salary | quartile |
|---------------|--------|----------|
| Ali           | 95000  | 1        |
| Sara          | 90000  | 1        |
| Ahmed         | 85000  | 2        |
| Bilal         | 80000  | 2        |

---

### 4. `LAG()` aur `LEAD()`

Previous ya next row ka data access karne ke liye use hotay hain.

```sql
SELECT 
  employee_name,
  salary,
  LAG(salary) OVER (ORDER BY hire_date) AS prev_salary,
  LEAD(salary) OVER (ORDER BY hire_date) AS next_salary
FROM employees;
```

 **Output Example:**

| employee_name | salary | prev_salary | next_salary |
|---------------|--------|-------------|-------------|
| Ali           | 70000  | NULL        | 75000       |
| Sara          | 75000  | 70000       | 80000       |
| Ahmed         | 80000  | 75000       | 85000       |
| Bilal         | 85000  | 80000       | NULL        |

---

### 5. `FIRST_VALUE()` aur `LAST_VALUE()`

Partition ke andar pehli ya aakhri value return karta hai.

```sql
SELECT 
  department,
  employee_name,
  salary,
  FIRST_VALUE(salary) OVER (PARTITION BY department ORDER BY salary DESC) AS top_salary
FROM employees;
```

 **Output Example:**

| department | employee_name | salary | top_salary |
|------------|----------------|--------|------------|
| HR         | Ali            | 90000  | 90000      |
| HR         | Ahmed          | 85000  | 90000      |
| IT         | Sara           | 95000  | 95000      |
| IT         | Bilal          | 87000  | 95000      |

---

### 6. Aggregates with Window (e.g., SUM, AVG)

```sql
SELECT 
  department,
  employee_name,
  salary,
  SUM(salary) OVER (PARTITION BY department ORDER BY hire_date) AS running_total
FROM employees;
```

 **Output Example:**

| department | employee_name | salary | running_total |
|------------|----------------|--------|----------------|
| HR         | Ali            | 70000  | 70000          |
| HR         | Ahmed          | 75000  | 145000         |
| IT         | Sara           | 80000  | 80000          |
| IT         | Bilal          | 85000  | 165000         |

---

##  Real Example: Sales Table

**Table: sales**

| id | region | salesperson | amount | sale_date  |
|----|--------|-------------|--------|------------|
| 1  | East   | Ali         | 1000   | 2023-01-01 |
| 2  | East   | Sara        | 1500   | 2023-01-02 |
| 3  | East   | Ali         | 700    | 2023-01-03 |
| 4  | West   | Bilal       | 2000   | 2023-01-01 |

**Query**: Salesperson ka running total aur region ke andar rank:

```sql
SELECT 
  region,
  salesperson,
  amount,
  SUM(amount) OVER (PARTITION BY salesperson ORDER BY sale_date) AS running_sales,
  RANK() OVER (PARTITION BY region ORDER BY amount DESC) AS region_rank
FROM sales;
```

 **Output Example:**

| region | salesperson | amount | running_sales | region_rank |
|--------|-------------|--------|----------------|--------------|
| East   | Ali         | 1000   | 1000           | 2            |
| East   | Sara        | 1500   | 1500           | 1            |
| East   | Ali         | 700    | 1700           | 3            |
| West   | Bilal       | 2000   | 2000           | 1            |

---

##  Summary Table

| Function        | Kya Karta Hai                           |
|------------------|------------------------------------------|
| `ROW_NUMBER()`   | Har row ko unique number deta hai        |
| `RANK()`         | Rank deta hai, tie par number skip karta hai |
| `DENSE_RANK()`   | Rank deta hai, number skip nahi karta     |
| `NTILE(n)`       | Data ko buckets mein divide karta hai     |
| `LAG()`          | Previous row ka data laata hai            |
| `LEAD()`         | Next row ka data laata hai                |
| `FIRST_VALUE()`  | Partition ka pehla value laata hai        |
| `LAST_VALUE()`   | Partition ka aakhri value laata hai       |
| `SUM()`, `AVG()` | Aggregate functions per row mein          |

---

##  Use Cases in Real Life

- Top 3 salespersons per region nikaalna
- Month-over-month product sale comparison
- Customer behavior (first/last purchase)
- Running totals aur moving averages
- Leaderboard create karna

---

##  Tips

- `ORDER BY` zaroori hai jab row-wise comparison kar rahe ho
- `PARTITION BY` se groups define karo jahan calculation repeat honi chahiye
- Multiple window functions combine karo for powerful insights
- Excel jese kaam SQL mein easily window functions se hotay hain

---

#  SQL: Views, Stored Procedures, aur CTEs 

---

##  1. Views

###  View Kya Hoti Hai?

- View aik **virtual table** hoti hai jo SQL query ka result hoti hai.
- Is mein actual data store nahi hota — ye sirf **query ka saved version** hoti hai.
- Views ka use readability, reusability, aur security ke liye kiya jata hai.

---

###  View Banane ka Syntax:

```sql
CREATE VIEW view_name AS
SELECT columns
FROM table
WHERE condition;
```

---

###  Example:

```sql
CREATE VIEW high_salary_employees AS
SELECT employee_name, salary
FROM employees
WHERE salary > 80000;
```

 **Output (jab view ko select karein):**

```sql
SELECT * FROM high_salary_employees;
```

| employee_name | salary |
|---------------|--------|
| Ali           | 90000  |
| Sara          | 95000  |

---

###  View Ko Update Karna:

```sql
ALTER VIEW high_salary_employees AS
SELECT employee_name, salary
FROM employees
WHERE salary > 85000;
```

---

###  View Ko Delete Karna:

```sql
DROP VIEW high_salary_employees;
```

---

##  2. Stored Procedures

###  Stored Procedure Kya Hoti Hai?

- Stored procedure aik **predefined SQL statements ka group** hota hai.
- Aap isay **once define kar ke baar baar call** kar sakte hain.
- Useful for: Automation, complex logic, performance, and security.

---

### 🔧 Syntax:

```sql
CREATE PROCEDURE procedure_name
AS
BEGIN
  SQL statements
END;
```

---

###  Example:

```sql
CREATE PROCEDURE get_high_salary
AS
BEGIN
  SELECT employee_name, salary
  FROM employees
  WHERE salary > 80000;
END;
```

 **Procedure Call Karna:**

```sql
EXEC get_high_salary;
```

 **Output:**

| employee_name | salary |
|---------------|--------|
| Ali           | 90000  |
| Sara          | 95000  |

---

###  Parameters Ke Sath Procedure:

```sql
CREATE PROCEDURE get_salary_above @min_salary INT
AS
BEGIN
  SELECT employee_name, salary
  FROM employees
  WHERE salary > @min_salary;
END;
```

 **Call Example:**

```sql
EXEC get_salary_above @min_salary = 85000;
```

 **Output:**

| employee_name | salary |
|---------------|--------|
| Sara          | 95000  |

---

###  Procedure Delete Karna:

```sql
DROP PROCEDURE get_high_salary;
```

---

##  3. CTE (Common Table Expression)

###  CTE Kya Hoti Hai?

- CTE aik temporary result set hota hai jo aap query ke sath define karte hain.
- Isay mainly readability aur recursion ke liye use karte hain.

---

###  Syntax:

```sql
WITH cte_name AS (
  SELECT ...
  FROM ...
  WHERE ...
)
SELECT * FROM cte_name;
```

---

###  Example:

```sql
WITH high_salary AS (
  SELECT employee_name, salary
  FROM employees
  WHERE salary > 80000
)
SELECT * FROM high_salary;
```

 **Output:**

| employee_name | salary |
|---------------|--------|
| Ali           | 90000  |
| Sara          | 95000  |

---

###  Recursive CTE Example:

```sql
WITH numbers AS (
  SELECT 1 AS num
  UNION ALL
  SELECT num + 1
  FROM numbers
  WHERE num < 5
)
SELECT * FROM numbers;
```

 **Output:**

| num |
|-----|
| 1   |
| 2   |
| 3   |
| 4   |
| 5   |

---

##  Summary Table

| Concept          | Kya Hai?                              | Use Case                           |
|------------------|----------------------------------------|------------------------------------|
| `View`           | Virtual table (query ka result)        | Reusable queries, security         |
| `Stored Procedure` | SQL commands ka reusable group       | Automation, encapsulation          |
| `CTE`            | Temporary named result set             | Clean queries, recursion, clarity  |

---

##  Real-World Use Cases

- Views: Reports aur dashboards ke liye filtered data banana
- Stored Procedures: Monthly salary process automation
- CTE: Recursive hierarchy jaise category trees, org charts, etc.

---

##  Tips

- Views lightweight hoti hain, lekin performance tab effect hota hai jab view ke andar complex joins hon.
- Stored Procedures mein parameters use karne se flexibility milti hai.
- CTEs ko nested ya recursive queries readable banane ke liye use karein.

---

# SQL Built-in Functions & Logical Expressions 

Yeh document SQL ke commonly used functions aur expressions ko **simple Roman Urdu** mein explain karta hai — taake aap asaani se samajh sakein aur real-world data analytics projects mein use kar sakein.

---

##  1. `SUBSTRING()`

###  Kya karta hai?
Ek string ke andar se **specified part** ko nikalta hai.

###  Syntax:
```sql
SUBSTRING(column_name, start_position, length)
```

###  Example:
```sql
SELECT SUBSTRING('Pakistan Zindabad', 1, 8) AS result;
```

 **Output:**
| result    |
|-----------|
| Pakistan  |

---

##  2. `CHARINDEX()`

### ➤ Kya karta hai?
Ek character ya word ka **index number (position)** batata hai string ke andar.

###  Syntax:
```sql
CHARINDEX('find_this', 'search_in_this_string')
```

###  Example:
```sql
SELECT CHARINDEX('Zind', 'Pakistan Zindabad') AS position;
```

 **Output:**
| position |
|----------|
| 10       |

---

##  3. `Use of Substring and Charindex Together

### 1. `SUBSTRING()` Syntax
```sql
SUBSTRING(expression, start, length)
```

**Parameters:**
- `expression`: The text (column or string literal) to extract from
- `start`: The starting position (1-based index)
- `length`: How many characters to extract

**Example:**
```sql
SELECT SUBSTRING('SQLServer', 4, 6) AS Result;
-- Output: 'Server'
```

---

### 2. `CHARINDEX()` Syntax
```sql
CHARINDEX(search_expression, expression)
```

**Parameters:**
- `search_expression`: The character or substring to find
- `expression`: The full string in which to search

**Example:**
```sql
SELECT CHARINDEX('@', 'alice@test.org') AS Position;
-- Output: 6
```

---

### Example: Using Both Together to Extract Email Domain
To extract the domain name (e.g., `test.org`) from email addresses:

```sql
SELECT 
  Email,
  SUBSTRING(Email, CHARINDEX('@', Email) + 1, LEN(Email)) AS DomainName
FROM CustomerData;
```

**Explanation:**
- `CHARINDEX('@', Email)` → finds the position of `@`
- `+ 1` → moves to the first character after `@`
- `LEN(Email)` → extracts the remaining string (domain name)

--- 
##  4. `DATEDIFF()`

###  Kya karta hai?
Do dates ke darmiyan **difference (days, months, years)** batata hai.

###  Syntax:
```sql
DATEDIFF(interval, start_date, end_date)
```

###  Example:
```sql
SELECT DATEDIFF(DAY, '2023-01-01', '2023-01-10') AS days_between;
```

 **Output:**
| days_between |
|--------------|
| 9            |

---

##  5. `DATEADD()`

###  Kya karta hai?
Date mein **naya time (days, months, etc.) add karta hai**.

###  Syntax:
```sql
DATEADD(interval, number, date)
```

###  Example:
```sql
SELECT DATEADD(DAY, 5, '2023-01-01') AS new_date;
```

 **Output:**
| new_date  |
|-----------|
| 2023-01-06|

---

##  6. `DATENAME()`

###  Kya karta hai?
Date ka **part (day, month name, weekday)** return karta hai in text form.

###  Syntax:
```sql
DATENAME(part, date)
```

###  Example:
```sql
SELECT DATENAME(MONTH, '2023-08-03') AS month_name;
```

 **Output:**
| month_name |
|------------|
| August     |

---

##  7. `CAST()` vs `CONVERT()`

###  Kya karte hain?
Data type **convert karte hain** (e.g., number to string, string to date)

###  CAST Syntax:
```sql
CAST(expression AS data_type)
```

###  CONVERT Syntax:
```sql
CONVERT(data_type, expression, style)
```

###  Example:
```sql
SELECT CAST(123 AS VARCHAR) AS casted_value,
       CONVERT(VARCHAR, GETDATE(), 103) AS converted_date;
```

 **Output:**
| casted_value | converted_date |
|--------------|----------------|
| 123          | 03/08/2025     |

---

##  8. `CASE WHEN THEN ELSE END`

### ➤ Kya karta hai?
Conditional logic apply karta hai (jaise IF/ELSE).

### Syntax:
```sql
CASE 
  WHEN condition THEN result
  ELSE default_result
END
```

###  Example:
```sql
SELECT 
  salary,
  CASE 
    WHEN salary > 80000 THEN 'High'
    ELSE 'Normal'
  END AS salary_status
FROM employees;
```

 **Output:**
| salary | salary_status |
|--------|----------------|
| 90000  | High           |
| 70000  | Normal         |

---

##  9. `COALESCE()`

###  Kya karta hai?
Jo pehli **non-null value** milti hai, woh return karta hai.

###  Syntax:
```sql
COALESCE(val1, val2, val3, ...)
```

###  Example:
```sql
SELECT COALESCE(NULL, NULL, 'Value Mil Gayi') AS result;
```

 **Output:**
| result         |
|----------------|
| Value Mil Gayi |

---

##  10. `NULLIF()`

### ➤ Kya karta hai?
Agar dono values same hon to `NULL` return karta hai, warna pehli value.

###  Example:
```sql
SELECT NULLIF(100, 100) AS result1,
       NULLIF(100, 90) AS result2;
```

 **Output:**
| result1 | result2 |
|---------|---------|
| NULL    | 100     |

---

##  11. `IIF()` (Shortcut of CASE)

###  Kya karta hai?
Simple condition evaluate karta hai (IF/ELSE style).

###  Syntax:
```sql
IIF(condition, true_value, false_value)
```

###  Example:
```sql
SELECT IIF(100 > 50, 'Yes', 'No') AS result;
```

 **Output:**
| result |
|--------|
| Yes    |

---

##  12. `EXISTS`

###  Kya karta hai?
Check karta hai ke subquery se **kuch result aaya ya nahi**.

###  Example:
```sql
IF EXISTS (SELECT * FROM employees WHERE salary > 100000)
   PRINT 'High salary employee exists';
```

 **Output:**
```text
High salary employee exists
```

---

##  13. `IN` vs `NOT IN`

###  Kya karte hain?
`IN`: Check karta hai value list ke andar hai ya nahi  
`NOT IN`: Check karta hai value list ke andar **nahi** hai

###  Example:
```sql
SELECT employee_name
FROM employees
WHERE department IN ('HR', 'IT');
```

 **Output:**
| employee_name |
|---------------|
| Ali           |
| Sara          |

---
## 14. PATINDEX() Example in SQL Server

**Purpose**  
The `PATINDEX()` function returns the starting position of a pattern within a string.  
It is similar to `CHARINDEX()` but allows the use of wildcard characters (`%`).

**Details**  
- `%` matches any sequence of characters (including zero characters).  
- Returns a 1-based index for the first occurrence of the pattern.  
- Returns `0` if the pattern is not found.  
- Works with `CHAR`, `VARCHAR`, `NCHAR`, `NVARCHAR` data types.

SELECT CustomerID,
       Email,
       PATINDEX('%.com%', Email) AS DotComPosition
       
FROM dirtyCustomerData

**Output:** 

<img width="317" height="256" alt="pp" src="https://github.com/user-attachments/assets/6a12fb64-008f-4a53-8f0f-33dea4a7a620" />

--- 
## REPLICATE() Example in SQL Server


**Output**



---
##  Summary Table

| Function         | Use (Roman Urdu)                              |
|------------------|------------------------------------------------|
| `SUBSTRING()`     | String ka hissa nikalna                        |
| `CHARINDEX()`     | Word ka position find karna                   |
| `DATEDIFF()`      | Do dates ka farq nikalna                       |
| `DATEADD()`       | Date mein din/mahina/year add karna           |
| `DATENAME()`      | Date ka part (month, day name) nikalna        |
| `CAST()`, `CONVERT()` | Data type change karna                     |
| `CASE WHEN`       | IF/ELSE logic apply karna                     |
| `COALESCE()`      | First non-null value lana                     |
| `NULLIF()`        | Same values ko NULL banakar return karna      |
| `IIF()`           | One-line IF condition                         |
| `EXISTS`          | Check karna ke result aata hai ya nahi        |
| `IN`, `NOT IN`    | Value list mein hai ya nahi                   |

---

##  Real-World Use Cases

- `SUBSTRING()`, `CHARINDEX()` → Email se domain nikalna
- `DATEDIFF()` → Customer ko kitne din se contact nahi kiya
- `DATEADD()` → Next follow-up date set karna
- `CASE` / `IIF()` → Customer status label assign karna
- `EXISTS` → Data presence validation in subqueries

---

##  Tips

- Hamesha `NULL` values handle karein with `COALESCE()` ya `IS NULL`
- `CASE` bohot powerful hota hai for custom logic
- `IN` small lists ke liye efficient hota hai, lekin large subqueries mein `JOIN` ya `EXISTS` better hota hai

---
