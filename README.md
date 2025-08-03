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

---

##  Sample Tables Based on ERD

###  Sample Data - `Customers`

| CustomerID | FullName   | Country | City      |
|------------|------------|---------|-----------|
| 1          | Ali Khan   | Pakistan| Lahore    |
| 2          | Sara Baloch| UAE     | Dubai     |

###  Sample Data - `Orders`

| OrderID | CustomerID | StoreID | OrderDate  |
|---------|------------|---------|------------|
| 101     | 1          | 201     | 2023-01-10 |
| 102     | 2          | 202     | 2023-03-15 |

###  Sample Data - `Stores`

| StoreID | StoreName       | Country   |
|---------|------------------|-----------|
| 201     | TechStore Lahore | Pakistan  |
| 202     | GadgetHub Dubai  | UAE       |

###  Sample Data - `OrderDetails`

| OrderDetailID | OrderID | ProductID | Quantity |
|---------------|---------|-----------|----------|
| 1             | 101     | 301       | 2        |
| 2             | 102     | 302       | 1        |

###  Sample Data - `Products`

| ProductID | ModelName  | BasePrice |
|-----------|------------|-----------|
| 301       | iPhone 13  | 1200      |
| 302       | Galaxy S21 | 1000      |

---

##  1. INNER JOIN

**Explanation:** Sirf woh rows return karta hai jahan dono tables mein matching data ho.

```sql
SELECT 
    Customers.FullName,
    Orders.OrderID,
    Orders.OrderDate
FROM Customers
INNER JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

 **Output:**

| FullName   | OrderID | OrderDate  |
|------------|---------|------------|
| Ali Khan   | 101     | 2023-01-10 |
| Sara Baloch| 102     | 2023-03-15 |

---

##  2. LEFT JOIN (Left Outer Join)

**Explanation:** Left (First) Table ki sari rows return karta hai, chahe matching right table mein ho ya naa ho.

```sql
SELECT 
    Customers.FullName,
    Orders.OrderID,
    Orders.OrderDate
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

 **Output:** (If Customer has no Orders, tab bhi show hoga)

| FullName   | OrderID | OrderDate  |
|------------|---------|------------|
| Ali Khan   | 101     | 2023-01-10 |
| Sara Baloch| 102     | 2023-03-15 |

(Note: agar ek aur customer hota jiska order nahi hota, tab bhi uska name dikhta)

---

##  3. RIGHT JOIN (Right Outer Join)

**Explanation:** Right Table ki sari rows return karta hai, left table se matching ho toh show karega, warna NULL.

```sql
SELECT 
    Orders.OrderID,
    Customers.FullName
FROM Orders
RIGHT JOIN Customers ON Customers.CustomerID = Orders.CustomerID;
```

 **Output:** Same as LEFT JOIN but Right table focus:

| OrderID | FullName   |
|---------|------------|
| 101     | Ali Khan   |
| 102     | Sara Baloch|

---

##  4. FULL OUTER JOIN

**Explanation:** Dono tables ki sari rows return karta hai. Jahaan match nahi hota wahan NULL show karta hai.

```sql
SELECT 
    Customers.FullName,
    Orders.OrderID
FROM Customers
FULL OUTER JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

 **Output:** (Assume 1 customer without order & 1 order without customer)

| FullName   | OrderID |
|------------|---------|
| Ali Khan   | 101     |
| Sara Baloch| 102     |
| Ahmed      | NULL    |
| NULL       | 103     |

---

##  5. CROSS JOIN

**Explanation:** Har row ko dusri table ke har row ke saath milaata hai — Cartesian product.

```sql
SELECT 
    Customers.FullName,
    Stores.StoreName
FROM Customers
CROSS JOIN Stores;
```

 **Output:** 2 Customers × 2 Stores = 4 Rows

| FullName   | StoreName       |
|------------|------------------|
| Ali Khan   | TechStore Lahore |
| Ali Khan   | GadgetHub Dubai  |
| Sara Baloch| TechStore Lahore |
| Sara Baloch| GadgetHub Dubai  |

---

##  6. SELF JOIN

**Explanation:** Table ko khud se join karte hain – useful jab humein hierarchy ya comparison dikhana ho.

Example: Do customers same city ke hain?

```sql
SELECT 
    A.FullName AS Customer1,
    B.FullName AS Customer2,
    A.City
FROM Customers A
JOIN Customers B ON A.City = B.City AND A.CustomerID <> B.CustomerID;
```

 **Output:** (If 2 log same city mein ho)

| Customer1 | Customer2 | City   |
|-----------|-----------|--------|
| Ali Khan  | Ahmed     | Lahore |

---

##  Tips for Real World
- **INNER JOIN**: daily operations jaise orders + customers details
- **LEFT JOIN**: report generation, e.g.: sab customers aur unke orders (chahe kuch keh nahi ho)
- **FULL JOIN**: audit reports, missing relationships
- **CROSS JOIN**: sab combinations banana ho tab
- **SELF JOIN**: hierarchy, comparisons

---

##  Summary Table

| Join Type     | Result Description                        |
|---------------|-------------------------------------------|
| INNER JOIN    | Sirf matching rows dono tables se         |
| LEFT JOIN     | Left table saari rows + matching right    |
| RIGHT JOIN    | Right table saari rows + matching left    |
| FULL JOIN     | Dono tables ki all rows + NULLs for miss  |
| CROSS JOIN    | Har row har row se match karega           |
| SELF JOIN     | Table apne aap se join hota hai           |

---
```

---

**Use Case:** You can copy this whole markdown into your notes and reference it while studying or applying joins in your real-world personal or work projects.

Let me know if you want this in PDF, HTML, or a Jupyter notebook format as well!

