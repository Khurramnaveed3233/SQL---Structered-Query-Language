
# SQL Kya Hoti Hai?

**SQL** ka matlab hai **Structured Query Language**. Ye ek zubaan hai jo databases se baat karne ke liye use hoti hai.

### SQL se kya kya kar sakte hain?
- Data **search** karna (jaise: "Mujhe sab customers dikhayo")
- Data ko **filter** karna (jaise: "Sirf Lahore ke orders dikhayo")
- Data ko **group** karna (jaise: "Har din ki total sales")
- Data ko **update** ya **delete** karna (jaise: "Galat entry hata do")

---

#  Data Science Mein SQL Kyun Zaroori Hai?

Data Science ka kaam hota hai data ko samajhna aur us se insights nikalna. Aur data aksar databases mein pada hota hai — jaise MySQL, SQL Server, PostgreSQL.

###  SQL ka role Data Science mein:
- **Raw data access** karne ke liye
- **Data cleaning aur filtering** ke liye
- **Summaries aur trends** nikalne ke liye
- **Dashboards aur reports** banane ke liye (Power BI mein bhi SQL ka use hota hai)

---
#  SQL vs NoSQL — Asaan Lafzon Mein Farq

##  SQL (Structured Query Language)
- **Type:** Relational Database (RDBMS)
- **Data Format:** Tables (rows & columns)
- **Schema:** Fixed schema — pehle se structure define karna hota hai
- **Examples:** MySQL, SQL Server, PostgreSQL, Oracle
- **Best For:** Structured data jahan relationships important hon (jaise customer-orders system)

###  SQL ki khasiyat:
- Strong consistency
- Complex queries (joins, filters, aggregations)
- ACID compliance (Atomicity, Consistency, Isolation, Durability)

---

##  NoSQL (Not Only SQL)
- **Type:** Non-relational Database
- **Data Format:** Flexible — documents, key-value pairs, graphs, wide-columns
- **Schema:** Dynamic schema — structure change hota reh sakta hai
- **Examples:** MongoDB, Cassandra, Redis, Firebase
- **Best For:** Unstructured ya semi-structured data (jaise social media posts, logs, IoT data)
  
###  NoSQL ki khasiyat:
- High scalability (big data ke liye)
- Fast performance for large volumes
- Flexible data modeling

---

## Summary Table

| Feature            | SQL                          | NoSQL                          |
|--------------------|------------------------------|--------------------------------|
| Structure          | Relational (tables)          | Non-relational (flexible)      |
| Schema             | Fixed                        | Dynamic                        |
| Scalability        | Vertical                     | Horizontal                     |
| Query Language     | SQL                          | Varies (JSON, key-value, etc.) |
| Use Case           | Structured data              | Big data, real-time apps       |
| Examples           | MySQL, PostgreSQL            | MongoDB, Cassandra             |

---

##  Kab Kya Use Karein?

- **SQL:** Jab data structured ho aur complex relationships ho (e.g. ERP, finance systems)
- **NoSQL:** Jab data fast grow kar raha ho, flexible ho, ya real-time ho (e.g. chat apps, analytics)

#  What is Database?

**Database** ek organized jagah hoti hai jahan data store kiya jata hai — taake usay easily access, manage, aur update kiya ja sake.

###  Real-life Example:
Socho ek Excel sheet jisme tumhare customers ka naam, address, aur order details hain — ye bhi ek chhoti database jaisi hoti hai. Lekin jab data bohot zyada ho jaye, to hum proper database systems use karte hain.

---

# Types of Databases

## 1. **Relational Database (RDBMS)**
- Data tables mein store hota hai (rows & columns)
- Tables ke beech relationships hotay hain
- Example: MySQL, SQL Server, PostgreSQL, Oracle

## 2. **NoSQL Database**
- Data flexible format mein hota hai (documents, key-value, graphs)
- Schema fixed nahi hota
- Example: MongoDB, Cassandra, Firebase

## 3. **In-Memory Database**
- Data RAM mein store hota hai — super fast access
- Example: Redis

## 4. **Cloud Database**
- Internet ke zariye access hoti hai
- Scalable aur distributed hoti hai
- Example: Amazon Aurora, Google BigQuery

## 5. **Graph Database**
- Data nodes aur edges mein hota hai (relationships ko highlight karta hai)
- Example: Neo4j

---

#  What is RDBMS?

**RDBMS** ka matlab hai **Relational Database Management System**. Ye ek software hota hai jo relational databases ko manage karta hai.

###  RDBMS ki khasiyat:
- Data tables mein hota hai
- Tables ke beech relationships define kiye ja sakte hain (foreign keys)
- SQL language use hoti hai
- ACID properties follow karta hai (Atomicity, Consistency, Isolation, Durability)

### 🔧 Common RDBMS Examples:
- MySQL  
- Microsoft SQL Server  
- PostgreSQL  
- Oracle Database

---

#  Summary Table

| Feature              | RDBMS                          | NoSQL                         |
|----------------------|--------------------------------|-------------------------------|
| Data Format          | Tables (rows & columns)        | Documents, key-value, etc.    |
| Schema               | Fixed                          | Flexible                      |
| Query Language       | SQL                            | Varies (JSON, etc.)           |
| Relationships        | Strong (joins, foreign keys)   | Weak or none                  |
| Use Case             | Structured business data       | Big data, real-time apps      |

#  SQL SELECT Statement — Full Guide

##  Basic Syntax

SELECT column1, column2, ...
FROM table_name
WHERE condition
GROUP BY column
HAVING condition
ORDER BY column ASC|DESC;

# SQL SELECT Statement — All 6 Clauses in One Example

1️⃣ **SELECT**  
- Matlab: "Mujhe yeh data chahiye"  
- Use: Specific columns choose karna  
`SELECT name, age` → Sirf name aur age ka data dikhayega  

2️⃣ **FROM**  
- Matlab: "Ye data is table se lo"  
`FROM customers` → Data customers table se aayega  

3️⃣ **WHERE**  
- Matlab: "Sirf woh data do jo is condition ko meet kare" (filtering)  
`WHERE age > 25` → Sirf un records ka data jinki age 25 se zyada ho  

4️⃣ **GROUP BY**  
- Matlab: "Data ko group mein divide karo"  
- Mostly aggregate functions ke saath use hota hai (SUM, COUNT, AVG)  
`GROUP BY city` → City ke hisaab se grouping karega  

5️⃣ **HAVING**  
- Matlab: "Grouped data par filter lagao"  
`HAVING COUNT(*) > 5` → Sirf woh groups show karega jahan 5 se zyada records hain  

6️⃣ **ORDER BY**  
- Matlab: "Data ko arrange karo"  
- ASC = chhote se bara | DESC = bare se chhota  
`ORDER BY age DESC` → Sabse badi age se start karega  

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
## 15. REPLICATE() Example in SQL Server

**Purpose**  
The `REPLICATE()` function repeats a string value a specified number of times.

**Details**  
- Syntax: `REPLICATE(expression, number_of_times)`  
- `expression` is the string or column to repeat.  
- `number_of_times` is how many times the string should be repeated.  
- If the result exceeds the maximum size of the return type, it will be truncated.

**Output**

<img width="365" height="412" alt="rep" src="https://github.com/user-attachments/assets/c17c1f14-7623-477c-b74f-6eab7c122be1" />

---
## 16. FORMAT() Example in SQL Server

**Purpose**  
The `FORMAT()` function formats a value (numeric or date/time) according to a specified format and culture.

**Details**  
- Syntax: `FORMAT(value, format_string, culture)`  
- `value`: The number or date/time you want to format.  
- `format_string`: The format pattern, for example:  
  - `'C'` → Currency  
  - `'N'` → Number with commas  
  - `'P'` → Percentage  
- `culture`: The locale used for formatting, e.g., `'en-US'`, `'fr-FR'`.  

**Output**

<img width="501" height="373" alt="ff" src="https://github.com/user-attachments/assets/9aca94f9-8b99-42d9-a02d-84e0e4e08603" />

---

## 17. SYSDATETIME() and GETDATE()  Example in SQL Server

Difference between GETDATE() and SYSDATETIME() precision

SYSDATETIME() ka output GETDATE() se zyada accurate hota hai 
kyunki isme seconds ke baad fractional seconds nanoseconds tak include hote hain

GETDATE() precision: milliseconds (seconds ke 3 decimal places tak)
SYSDATETIME() precision: nanoseconds (seconds ke 7 decimal places tak)

SELECT 
    GETDATE() AS GetDateExample,         -- Millisecond precision
    SYSDATETIME() AS SysDateTimeExample  -- Nanosecond precision


    GETDATE() AS GetDateExample,         -- Returns current date and time (precision: milliseconds)
    
    SYSDATETIME() AS SysDateTimeExample  -- Returns current date and time (precision: nanoseconds)

**Output**

<img width="590" height="146" alt="cc" src="https://github.com/user-attachments/assets/9affd4a0-6ba1-4292-b313-8eddf5ef81e7" />

---

## 18. `EOMONTH()

-- Last day of the month return karta hai, optional offset ke sath  
-- **Syntax:** `EOMONTH(start_date [, month_to_add])`  

SELECT EOMONTH('2025-08-10') AS LastDay;

**Output**

<img width="204" height="62" alt="eo" src="https://github.com/user-attachments/assets/15f5207e-c74d-43cc-a9a4-ba6fde54869c" />

--- 

## 19. ISDATE()

SELECT 
    ISDATE('2025-08-10') AS IsValidDate, 
    ISDATE('ABC123') AS IsValidDate2;

**Explanation**

ISDATE('2025-08-10')

- '2025-08-10' ek valid ISO date format hai (YYYY-MM-DD)

- SQL Server isko valid date recognize karta hai

- Result: 1 (true)

ISDATE('ABC123')

- 'ABC123' date format ke rules follow nahi karta

- SQL Server isko date mein convert nahi kar sakta

- Result: 0 (false)

**Output**

<img width="222" height="51" alt="is" src="https://github.com/user-attachments/assets/d60a233f-da83-4cf2-9a3e-c96ed1c15e21" />

##  STDEV() → Standard Deviation

**Easy Words:**  

Batata hai ki numbers **mean** se kitne door-door bikhre huye hain.  
- Zyada value = data zyada spread.

**Example:**

<img width="374" height="169" alt="st" src="https://github.com/user-attachments/assets/9c4b916c-ce0a-4829-8d32-e01d3f90649b" />

**Example Data:**

100, 102, 105, 500

- Mean ke paas wale values ka STDEV chhota hota hai.
- 500 jaisa outlier STDEV ko bada bana deta hai.

## Standard Deviation Layman (Aam Zubaan) Mein

Socho tumhare paas 5 dosto ki height ka data hai.  
Agar sab ki height lagbhag barabar ho, iska matlab sab **ek jese** hain — is case mein standard deviation chhota hoga.

Lekin agar ek dost bohot lamba hai, ek bohot chhota hai, aur baaki beech beech ke hain, to heights **bikhri hui** hongi — is case mein standard deviation bara hoga.

### Simple Baat:
- **Chhota standard deviation** → sab numbers ek dusre ke kareeb.
- **Bara standard deviation** → numbers door door, zyada difference.

### Easy Example:

1. **Close numbers:** 50, 51, 52, 53, 54  
   - Sab kareeb hain → SD chhota.
2. **Far numbers:** 10, 50, 90, 130, 170  
   - Numbers door door → SD bara.

**Yaani:** Standard deviation bas ek tarika hai measure karne ka  
"Numbers kitne ek jese hain ya kitne alag alag hain."

--- 

## VAR() → Variance

**Easy Words:**

Ye standard deviation ka square hota hai.

- Zyada variance = data ka spread zyada.
- Kam variance = data tight group me.

**Example:**

<img width="415" height="160" alt="vv" src="https://github.com/user-attachments/assets/7a885297-4ab5-49c4-b548-165bb7b80d02" />

- Agar STDEV = 20 hai, to VAR ≈ 400 hoga.

## Variance Layman (Aam Zubaan) Mein

Socho tumhare paas kuch numbers hain, jaise tumhare dosto ki test marks.  
Tum dekhna chahte ho ke ye marks **kitne ek jese** hain ya **kitne alag alag**.

Variance ek number hai jo batata hai:
- Agar variance **chhota** hai → sab marks kareeb kareeb hain.
- Agar variance **bara** hai → marks mein zyada farq hai.

### Easy Example:

1. **Close marks:** 50, 52, 53, 54, 55  
   - Sab kareeb → variance chhota.
2. **Far marks:** 20, 40, 60, 80, 100  
   - Door door → variance bara.

### Simple Soch:

Variance = har number ka mean se difference ka square ka average.  
Yaani pehle dekhte ho har number mean se kitna door hai,  
phir un distances ka **average** lete ho.

**Short me:** 

Variance batata hai data kitna spread (bikhar) hua hai.

## Class A

### Step 1: Mean (Average) nikalna
- Sab numbers ka sum karo:  
  50 + 52 + 55 + 57 + 60 = 274  
- Total ko 5 (numbers ki tadaad) se divide karo:  
  274 ÷ 5 = 54.8  
- **Mean (μ)** = **54.8**

---

### Step 2: Har number ka Squared Deviation nikalna
1. Har score se mean minus karo: (xᵢ − μ)  
2. Result ka square karo: (xᵢ − μ)²  

| Score (xᵢ) | xᵢ − μ  | (xᵢ − μ)² |
|------------|--------|-----------|
| 50         | -4.8   | 23.04     |
| 52         | -2.8   | 7.84      |
| 55         | 0.2    | 0.04      |
| 57         | 2.2    | 4.84      |
| 60         | 5.2    | 27.04     |

---

### Step 3: Variance nikalna
- Squared deviations ka sum:  
  23.04 + 7.84 + 0.04 + 4.84 + 27.04 = 62.8  
- Isko 5 se divide karo:  
  62.8 ÷ 5 = 12.56  
- **Variance (σ²) = 12.56**

---

## Class B

### Step 1: Mean nikalna
- Sum: 30 + 45 + 55 + 75 + 90 = 295  
- Divide by 5: 295 ÷ 5 = 59  
- **Mean (μ)** = 59

---

### Step 2: Squared Deviations

| Score (xᵢ) | xᵢ − μ  | (xᵢ − μ)² |
|------------|--------|-----------|
| 30         | -29    | 841       |
| 45         | -14    | 196       |
| 55         | -4     | 16        |
| 75         | 16     | 256       |
| 90         | 31     | 961       |

---

### Step 3: Variance nikalna
- Squared deviations ka sum:  
  841 + 196 + 16 + 256 + 961 = 2270  
- Divide by 5:  
  2270 ÷ 5 = 454  
- **Variance (σ²) = 454**

---

## Final Conclusion
- **Class A ka Variance:** 12.56 → scores zyada close hain.
- **Class B ka Variance:** 454 → scores bohot zyada spread hain.

Matlab Class B ka data zyada bikhra hua hai compare to Class A.


# SQL Server: UPDATE, ALTER, and TRY_CONVERT

## 1. UPDATE
- Used to modify **data values** inside a table.
- Works row by row without changing the column definition.

### Example:

UPDATE kaps_cafe
SET transaction_time = CAST(transaction_time AS TIME);

Updates the values in transaction_time but does not change the column type.

## 2. ALTER

- Used to modify the table schema (column type, size, nullability).

- Changes the structure of the table.

### Example:

ALTER TABLE kaps_cafe
ALTER COLUMN transaction_time TIME;

- Converts the column itself into TIME. Fails if invalid values exist.

## 3. TRY_CONVERT

- Used to safely attempt conversion of values into another data type.
- If conversion succeeds → returns value.
- If conversion fails → returns NULL instead of throwing error.

### Example:

SELECT transaction_time,
       TRY_CONVERT(TIME, transaction_time) AS SafeTime
FROM kaps_cafe;

**Finding invalid values:**

-  Identifies rows that cannot be converted to TIME before running ALTER.

###  Example (checking conversion):

SELECT transaction_time,
       TRY_CONVERT(TIME, transaction_time) AS SafeTime
FROM kaps_cafe;

**Example (finding invalid values):**

SELECT transaction_time
FROM kaps_cafe
WHERE TRY_CONVERT(TIME, transaction_time) IS NULL
  AND transaction_time IS NOT NULL;

- Identifies rows that cannot be converted to TIME before running ALTER.

## 4. Converting Invalid Text Values to NULL

Before altering a column, invalid entries can be replaced with NULL safely.

**Example:**

UPDATE kaps_cafe
SET transaction_time = NULL
WHERE TRY_CONVERT(TIME, transaction_time) IS NULL;

- Any value that cannot be converted into TIME (like abc, 25:99, empty strings) is set to NULL.

**Summary**

- UPDATE → change data
- ALTER → change schema
- TRY_CONVERT → validate and clean data safely
- Use TRY_CONVERT + UPDATE to replace invalid text with NULL before running ALTER

## Mathematical Functions with Explanations and Examples

### 1. `ABS()`

- **Description:** Returns the absolute value of a number (negative ko positive bana deta hai)

- ABS ka matlab absolute value hota hai, jo kisi number ka distance from zero hota hai regardless of sign.

- Matlab, chahe number positive ho ya negative, ABS() uska positive magnitude return karega.

**Example samjho:**

- ABS(25) → 25

- ABS(-25) → 25

Iska use tab hota hai jab hume sirf magnitude chahiye, sign ignore karke, jaise difference calculation me.

SELECT ABS(-25) AS AbsoluteValue; -- Output: 25

<img width="246" height="64" alt="a" src="https://github.com/user-attachments/assets/414666ff-1abf-4aae-a052-30f0b5bfbb90" />

--- 
### 2. `CEILING()

- Description: Decimal number ko upar wali nearest integer tak round karta hai

SELECT CEILING(4.3) AS CeilingValue;

**Output**

<img width="232" height="72" alt="c" src="https://github.com/user-attachments/assets/c9d53471-1aa5-4236-a95e-345bda9cbe45" />

---
### 3. FLOOR()

- Description: Decimal number ko neeche wali nearest integer tak round karta hai

SELECT FLOOR(4.8) AS FloorValue; 

**Output**

<img width="179" height="75" alt="f" src="https://github.com/user-attachments/assets/c7058741-faa9-4842-94f8-825339294160" />

---
### 4. ROUND()

- Description: Number ko specified decimal places tak round karta hai

**Output**

<img width="166" height="52" alt="r" src="https://github.com/user-attachments/assets/1ebf486a-42ed-44bc-99d5-9ade30e5834e" />

--- 

### 5. POWER()

- Description: Ek number ko doosre number ki power tak uthata hai

SELECT POWER(2, 3) AS PowerValue;

**Description:** Ek number ko doosre number ki power tak uthata hai (exponentiation).  

- POWER(x, y)` ka matlab hai **x raised to the power y**.

- Asaan lafzon me, POWER(2, 3) ka matlab hai 2 ko 3 martaba apne aap se multiply karna

- 2 × 2 × 2 = 8

Yani base number (2) ko exponent (3) times multiply karte hain

**Example:**

SELECT POWER(2, 3) AS PowerValue;

**Output**

<img width="165" height="65" alt="p" src="https://github.com/user-attachments/assets/5fc338a9-04ab-4c52-b4fa-b79f70e05a0e" />

--- 

### 6.SQRT()

- Description: Number ka square root return karta hai

- Asaan lafzon me, SQRT(16) ka matlab hai wo number jo apne aap se multiply ho kar 16 banata hai

- Yani 4 × 4 = 16, is liye answer 4 aata hai

SELECT SQRT(16) AS SquareRoot; -- Output: 4

**Output**

<img width="237" height="59" alt="s" src="https://github.com/user-attachments/assets/d6e9ee21-4fac-42c6-bc04-196108c70686" />

--- 

### 7. PI()

- Description: Pi constant (3.141592...) return karta hai

SELECT PI() AS PiValue; 

- Asaan lafzon me, PI() hamesha ek fixed number deta hai jo circle ke circumference aur diameter ka ratio hota hai

- ye lagbhag 3.141593 hota hai, aur geometry me bohot use hota hai

**Output**

<img width="187" height="75" alt="pp" src="https://github.com/user-attachments/assets/a77c3819-2617-485a-9bd1-89c1b2ae541a" />

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
| `REPLICATE()`     | String ko multiple times repeat karna         |
| `DATALENGTH()`    | Data ka size (bytes me) check karna            |
| `PATINDEX()`      | Pattern ka position find karna (wildcards use hotay hain) |
| `SYSDATETIME()`   | Current date aur time lana nanoseconds precision ke saath |
| `DATEPART()`      | Date ka specific part integer form me nikalna  |

---
## Real-World Use Cases

- `SUBSTRING()`, `CHARINDEX()` → Email se domain nikalna  
- `DATEDIFF()` → Customer ko kitne din se contact nahi kiya  
- `DATEADD()` → Next follow-up date set karna  
- `CASE` / `IIF()` → Customer status label assign karna  
- `EXISTS` → Data presence validation in subqueries  
- `REPLICATE()` → Customer name ko do ya zyada baar repeat karke display karna  
- `DATALENGTH()` → Email ya address ka size bytes me check karna  
- `PATINDEX()` → Email me specific pattern (jaise %.com%) ka position find karna  
- `SYSDATETIME()` → Current date-time high precision (nanoseconds tak) ke sath lena  
- `DATEPART()` → Date ka specific part extract karna (year, month, day, hour etc)  


---

##  Tips

- Hamesha `NULL` values handle karein with `COALESCE()` ya `IS NULL`
- `CASE` bohot powerful hota hai for custom logic
- `IN` small lists ke liye efficient hota hai, lekin large subqueries mein `JOIN` ya `EXISTS` better hota hai

---
