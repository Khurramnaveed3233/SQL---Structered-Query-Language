# SQL-Functions-in-SQL

# SQL Comparison & Logical Operators (Roman Urdu mein)

SQL mein hum Comparison aur Logical Operators ka use karte hain taake hum data ko filter kar sakein, specific rows nikaal sakein, aur complex queries likh saken. Neeche sab operators ko example ke saath samjhaya gaya hai.

---

## `=` (Barabar)  
Ek value ko dusri se compare karta hai.

**Example:**
```sql
SELECT * FROM Students WHERE City = 'Lahore';
```

---

## `!=` ya `<>` (Barabar nahi)  
Dono ka matlab same hai — match na karne wali values nikaalta hai.

**Example:**
```sql
SELECT * FROM Students WHERE City != 'Karachi';
```

---

## `<` (Choti)  
Ek value doosri se choti hai ya nahi, yeh check karta hai.

**Example:**
```sql
SELECT * FROM Products WHERE Price < 1000;
```

---

## `>` (Bari)  
Ek value doosri se bari hai ya nahi.

**Example:**
```sql
SELECT * FROM Products WHERE Price > 5000;
```

---

## `<=` (Choti ya Barabar)  
Equal ya choti hone ka check.

**Example:**
```sql
SELECT * FROM Employees WHERE Age <= 30;
```

---

## `>=` (Bari ya Barabar)  
Equal ya bari hone ka check.

**Example:**
```sql
SELECT * FROM Employees WHERE Age >= 45;
```

---

## `AND` (Aur)  
Dono conditions ka sahi hona zaroori hai.

**Example:**
```sql
SELECT * FROM Students WHERE City = 'Lahore' AND Age > 18;
```

---

## `OR` (Ya)  
Kisi ek condition ka sahi hona kaafi hai.

**Example:**
```sql
SELECT * FROM Students WHERE City = 'Lahore' OR City = 'Karachi';
```

---

## `NOT` (Nahi)  
Condition ka ulta kar deta hai.

**Example:**
```sql
SELECT * FROM Products WHERE NOT Price < 1000;
```

---

## `BETWEEN` (Do values ke darmiyan)  
Lower aur upper limit ke darmiyan values nikaalne ke liye use hota hai.

**Example:**
```sql
SELECT * FROM Orders WHERE OrderDate BETWEEN '2025-01-01' AND '2025-01-31';
```

---

## `IN` (List ke andar)  
Aisi values dhoondhta hai jo list mein shamil hon.

**Example:**
```sql
SELECT * FROM Students WHERE City IN ('Lahore', 'Karachi', 'Islamabad');
```

---

## `LIKE` (Pattern search)  
Pattern match karne ke liye hota hai. `%` aur `_` wildcards use hotay hain.

**Example 1:**
```sql
SELECT * FROM Customers WHERE Name LIKE 'A%';
```
**Example 2:**
```sql
SELECT * FROM Customers WHERE Name LIKE '_li%';
```

---

## `IS NULL` (Value nahi hai)  
Jahan column ka value khali ho ya missing ho.

**Example:**
```sql
SELECT * FROM Employees WHERE Email IS NULL;
```

---

## `IS NOT NULL` (Value maujood hai)  
Jahan column ka value khali nahi hai.

**Example:**
```sql
SELECT * FROM Employees WHERE Email IS NOT NULL;
```

---

## 🔍 Summary Table

| Operator        | Roman Urdu Meaning                  |
|-----------------|--------------------------------------|
| =               | Barabar                             |
| !=  / <>        | Barabar nahi                        |
| <               | Choti                               |
| >               | Bari                                |
| <=              | Choti ya barabar                    |
| >=              | Bari ya barabar                     |
| AND             | Aur (dono condition sahi hon)       |
| OR              | Ya (koi ek sahi ho)                 |
| NOT             | Nahi                                |
| BETWEEN         | Do values ke darmiyan               |
| IN              | List ke andar                       |
| LIKE            | Pattern match (wildcards ke saath)  |
| IS NULL         | Value nahi hai                      |
| IS NOT NULL     | Value hai                           |

---

Umeed hai ke yeh summary aapko SQL ke logical aur comparison operators achi tarah samajhne mein madad degi.

# SQL Aggregate Functions 

Aggregate functions SQL mein use hoti hain jab humein kai rows ke upar calculations karni hoti hain — jaise total, average, count waghera. Ye functions aik column ki multiple values ko le kar ek single result return karte hain.

---

## `COUNT()` — Ginti karna  
Yeh function rows ki ginti karta hai.

**Example:**
```sql
SELECT COUNT(*) FROM Students;
```
Yeh total students ki ginti dega.

**Example with condition:**
```sql
SELECT COUNT(*) FROM Students WHERE City = 'Lahore';
```

---

## `SUM()` — Total nikalna  
Yeh kisi numeric column ka total nikalta hai.

**Example:**
```sql
SELECT SUM(Salary) FROM Employees;
```

---

## `AVG()` — Average nikalna  
Kisi numeric column ka average (mean) nikalta hai.

**Example:**
```sql
SELECT AVG(Marks) FROM Students;
```

---

## `MIN()` — Sabse choti value  
Column mein sabse choti (minimum) value nikalta hai.

**Example:**
```sql
SELECT MIN(Price) FROM Products;
```

---

## `MAX()` — Sabse badi value  
Column mein sabse badi (maximum) value nikalta hai.

**Example:**
```sql
SELECT MAX(Salary) FROM Employees;
```

---

## `GROUP BY` ke saath use karna  
Aggregate functions ko aksar `GROUP BY` ke saath use kiya jata hai taake categories ke mutabiq calculations ho sakein.

**Example: Total salary by department:**
```sql
SELECT Department, SUM(Salary)
FROM Employees
GROUP BY Department;
```

**Example: Student count by city:**
```sql
SELECT City, COUNT(*) 
FROM Students 
GROUP BY City;
```

---

## `HAVING` clause  
`HAVING` clause aggregate results ko filter karta hai (jaise `WHERE`, lekin `GROUP BY` ke saath).

**Example:**
```sql
SELECT City, COUNT(*) 
FROM Students 
GROUP BY City
HAVING COUNT(*) > 5;
```

---

## 🔍 Summary Table

| Function   | Kaam (Roman Urdu)                     |
|------------|----------------------------------------|
| COUNT()    | Rows ki ginti karta hai               |
| SUM()      | Total nikalta hai                     |
| AVG()      | Average (mean) nikalta hai            |
| MIN()      | Sabse choti value nikalta hai         |
| MAX()      | Sabse badi value nikalta hai          |

---

Umeed hai ke yeh aggregate functions ke examples aur explanation aapko SQL mein calculations aur summarization ko behtar samajhne mein madad denge.
