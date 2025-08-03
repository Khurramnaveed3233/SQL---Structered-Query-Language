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

Bilkul! Yahan SQL JOINs par ek mukammal guide hai, jismein sample data aur har JOIN ka output table bhi shamil hai. Yeh aapke notes ke liye behtareen hai.

### **SQL JOINs ka Ta'aruf (Introduction)**

SQL mein, data aksar alag-alag, related tables mein store kiya jaata hai. JOIN clause ka istemal in alag-alag tables se data ko ek common column (jaise `CustomerID`) ki bunyad par mila kar, ek single result set mein dikhane ke liye hota hai.

---

### **Sample Data**

Hum in sample tables ko apni misalon ke liye istemal karenge.

**Customers Table**
| CustomerID | FullName | City |
|:---|:---|:---|
| 1 | Ali Khan | Lahore |
| 2 | Fatima Ahmed | Karachi |
| 3 | Zara Baig | Lahore |
| 4 | Bilal Chaudhry | Islamabad |

**Orders Table**
| OrderID | CustomerID | StoreID | OrderDate |
|:---|:---|:---|:---|
| 501 | 1 | 10 | 2023-01-15 |
| 502 | 2 | 20 | 2023-01-17 |
| 503 | 1 | 10 | 2023-02-10 |
| 504 | 3 | 10 | 2023-02-20 |
| 505 | 99 | 20 | 2023-03-01 |

**Products Table**
| ProductID | ModelName |
|:---|:---|
| 101 | iPhone 14 Pro |
| 102 | Samsung S23 Ultra |
| 103 | AirPods Pro |

**OrderDetails Table**
| OrderDetailID | OrderID | ProductID |
|:---|:---|:---|
| 1001 | 501 | 101 |
| 1002 | 502 | 102 |
| 1003 | 503 | 103 |

**Stores Table**
| StoreID | StoreName |
|:---|:---|
| 10 | Lahore Flagship |
| 20 | Karachi Central |
| 30 | Islamabad Express|

---

### **JOINs ki Iqsaam (Types of Joins)**

#### **1. INNER JOIN**

*   **Aasan Lafzon Mein:** Yeh sirf woh rows dikhata hai jo **dono tables** mein mojood hon (jinka data match karta ho).

*   **Asal Zindagi ki Misal:** Un customers ka naam (`FullName`) aur unke order ki tareekh (`OrderDate`) dikhao jinhon ne koi order place kiya hai.

*   **SQL Code:**
    ```sql
    SELECT
        c.FullName,
        o.OrderDate
    FROM
        Customers AS c
    INNER JOIN
        Orders AS o ON c.CustomerID = o.CustomerID;
    ```

*   **Output Table:**
| FullName | OrderDate |
|:---|:---|
| Ali Khan | 2023-01-15 |
| Fatima Ahmed | 2023-01-17 |
| Ali Khan | 2023-02-10 |
| Zara Baig | 2023-02-20 |

*   **Output ki Wazahat:** Sirf wohi customers (Ali, Fatima, Zara) dikhaye gaye jinki `CustomerID` `Orders` table mein mojood thi. Bilal Chaudhry ne koi order nahi kiya, isliye woh is list mein nahi hain. `OrderID` 505 ka `CustomerID` 99 `Customers` table mein nahi hai, isliye woh bhi skip ho gaya.

---

#### **2. LEFT JOIN**

*   **Aasan Lafzon Mein:** Yeh "left" (pehli) table ki **sabhi rows** dikhata hai, aur "right" (doosri) table se sirf matching rows dikhata hai. Jahaan match na mile, wahan `NULL` aa jaata hai.

*   **Asal Zindagi ki Misal:** **Sabhi** customers ka naam dikhao, aur agar unhon ne koi order kiya hai to uski `OrderID` bhi.

*   **SQL Code:**
    ```sql
    SELECT
        c.FullName,
        o.OrderID
    FROM
        Customers AS c
    LEFT JOIN
        Orders AS o ON c.CustomerID = o.CustomerID;
    ```

*   **Output Table:**
| FullName | OrderID |
|:---|:---|
| Ali Khan | 501 |
| Ali Khan | 503 |
| Fatima Ahmed | 502 |
| Zara Baig | 504 |
| **Bilal Chaudhry** | **NULL** |

*   **Output ki Wazahat:** `Customers` (left table) ke sabhi records shamil hain. Bilal Chaudhry ne koi order nahi kiya, isliye unke `OrderID` ke aage `NULL` hai. Yeh un customers ko dhundne ke liye mufeed hai jinhon ne koi kharidari nahi ki.

---

#### **3. RIGHT JOIN**

*   **Aasan Lafzon Mein:** Yeh `LEFT JOIN` ka ulta hai. Yeh "right" (doosri) table ki **sabhi rows** dikhata hai. Jahaan left table mein match na mile, wahan `NULL` aa jaata hai.

*   **Asal Zindagi ki Misal:** **Sabhi** orders aur unke customer ka naam dikhao. Isse hum woh orders bhi dekh sakte hain jinka koi valid customer record nahi hai.

*   **SQL Code:**
    ```sql
    SELECT
        c.FullName,
        o.OrderID
    FROM
        Customers AS c
    RIGHT JOIN
        Orders AS o ON c.CustomerID = o.CustomerID;
    ```

*   **Output Table:**
| FullName | OrderID |
|:---|:---|
| Ali Khan | 501 |
| Ali Khan | 503 |
| Fatima Ahmed | 502 |
| Zara Baig | 504 |
| **NULL** | **505** |

*   **Output ki Wazahat:** `Orders` (right table) ke sabhi records shamil hain. `OrderID` 505 ka `CustomerID` 99 hai, jo `Customers` table mein nahi hai. Isliye uske `FullName` ke aage `NULL` hai.

---

#### **4. FULL OUTER JOIN**

*   **Aasan Lafzon Mein:** Yeh `LEFT` aur `RIGHT` join ka combination hai. Yeh dono tables ki **sabhi rows** dikhata hai. Jahaan match nahi milta, wahan `NULL` aa jaata hai.

*   **Asal Zindagi ki Misal:** Sabhi customers aur sabhi orders ki ek poori list, chahe unka aapas mein koi link ho ya na ho.

*   **SQL Code:**
    ```sql
    SELECT
        c.FullName,
        o.OrderID
    FROM
        Customers AS c
    FULL OUTER JOIN
        Orders AS o ON c.CustomerID = o.CustomerID;
    ```

*   **Output Table:**
| FullName | OrderID |
|:---|:---|
| Ali Khan | 501 |
| Ali Khan | 503 |
| Fatima Ahmed | 502 |
| Zara Baig | 504 |
| **Bilal Chaudhry** | **NULL** |
| **NULL** | **505** |

*   **Output ki Wazahat:** Is list mein Bilal Chaudhry (customer jisne order nahi kiya) bhi hain, aur Order 505 (order jiska customer nahi) bhi hai. Yeh data mein har tarah ki maloomat ko ek saath dekhne ke liye istemal hota hai.

---

#### **5. SELF JOIN**

*   **Aasan Lafzon Mein:** Ek table ko **khud se hi join** karna. Yeh tab istemal hota hai jab ek hi table ki rows ke darmiyan koi relation ho.

*   **Asal Zindagi ki Misal:** Un customers ke joray (pairs) dikhao jo **ek hi sheher (City)** se hain.

*   **SQL Code:**
    ```sql
    SELECT
        c1.FullName AS Customer1,
        c2.FullName AS Customer2,
        c1.City
    FROM
        Customers AS c1
    INNER JOIN
        Customers AS c2 ON c1.City = c2.City AND c1.CustomerID < c2.CustomerID;
    ```

*   **Output Table:**
| Customer1 | Customer2 | City |
|:---|:---|:---|
| Ali Khan | Zara Baig | Lahore |

*   **Output ki Wazahat:** Humne `Customers` table ko do alag naam (`c1`, `c2`) diye. Join `City` par kiya gaya. `c1.CustomerID < c2.CustomerID` ki shart lagayi taake duplicate pairs (Zara-Ali) aur self-pairs (Ali-Ali) na banein.

---

#### **6. Multi-Table Joins (Ek se Zyada Tables ko Join Karna)**

*   **Aasan Lafzon Mein:** Aap ek hi query mein zaroorat ke mutabiq kai tables ko chain ki tarah jod (join) sakte hain.

*   **Asal Zindagi ki Misal:** Hamein customer ka naam (`Customers`), uske order mein khareeday gaye product ka naam (`Products`), aur woh order kis store (`Stores`) se place hua, yeh sab ek saath dekhna hai.

*   **SQL Code:**
    ```sql
    SELECT
        c.FullName,
        p.ModelName,
        s.StoreName
    FROM
        Customers AS c
    INNER JOIN Orders AS o ON c.CustomerID = o.CustomerID
    INNER JOIN OrderDetails AS od ON o.OrderID = od.OrderID
    INNER JOIN Products AS p ON od.ProductID = p.ProductID
    INNER JOIN Stores AS s ON o.StoreID = s.StoreID;
    ```
*   **Output Table:**
| FullName | ModelName | StoreName |
|:---|:---|:---|
| Ali Khan | iPhone 14 Pro | Lahore Flagship |
| Fatima Ahmed| Samsung S23 Ultra| Karachi Central |
| Ali Khan | AirPods Pro | Lahore Flagship |

*   **Output ki Wazahat:** Yeh query `Customers` -> `Orders` -> `OrderDetails` -> `Products` aur `Orders` -> `Stores` ke links ko istemal karke 5 alag tables se data ko combine kar rahi hai aur ek complete, meaningful report bana rahi hai.

