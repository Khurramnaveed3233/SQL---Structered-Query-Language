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

# SQL String Functions (Roman Urdu mein)

String functions SQL mein un scenarios mein use hoti hain jahan humein text data (strings) par operations perform karne hote hain — jaise text ko join karna, length nikalna, capital letters mein lana, waghera.

---

## `LENGTH()` — String ki lambai nikalna  
Yeh function string (text) ki total characters count karta hai.

**Example:**
```sql
SELECT LENGTH('Khurram') AS NameLength;
```

---

## `LOWER()` — Sab letters chhoti (small) mein  
Text ko chhoti letters (lowercase) mein convert karta hai.

**Example:**
```sql
SELECT LOWER('HELLO WORLD') AS LowerText;
```

---

## `UPPER()` — Sab letters bari (capital) mein  
Text ko capital letters mein convert karta hai.

**Example:**
```sql
SELECT UPPER('hello world') AS UpperText;
```

---

## `TRIM()` — Extra spaces hataana  
String ke start aur end se extra spaces hataata hai.

**Example:**
```sql
SELECT TRIM('   Khurram   ') AS TrimmedName;
```

---

## `LTRIM()` — Left side ke spaces hataata hai  
**Example:**
```sql
SELECT LTRIM('   Khurram') AS LeftTrimmed;
```

## `RTRIM()` — Right side ke spaces hataata hai  
**Example:**
```sql
SELECT RTRIM('Khurram   ') AS RightTrimmed;
```

---

## `SUBSTRING()` — String ka hissa nikalna  
String ke andar se specific part nikalta hai.

**Syntax:**  
```sql
SUBSTRING(column_name, start_position, length)
```

**Example:**
```sql
SELECT SUBSTRING('Khurram Naveed', 1, 7) AS FirstName;
```

---

## `REPLACE()` — Text ko badalna  
Ek word ya character ko kisi aur se replace karta hai.

**Example:**
```sql
SELECT REPLACE('Lahore is beautiful', 'Lahore', 'Karachi') AS NewText;
```

---

## `CONCAT()` — Strings ko jorna (join karna)  
Do ya zyada strings ko ek saath jorta hai.

**Example:**
```sql
SELECT CONCAT('Khurram', ' ', 'Naveed') AS FullName;
```

---

## `LEFT()` — String ke start se n characters nikalta hai  
**Example:**
```sql
SELECT LEFT('Khurram', 3) AS StartPart;
```

## `RIGHT()` — String ke end se n characters nikalta hai  
**Example:**
```sql
SELECT RIGHT('Naveed', 3) AS EndPart;
```

---

## `CHARINDEX()` — Character ya word ki position batata hai  
**Example:**
```sql
SELECT CHARINDEX('r', 'Khurram') AS Position;
```

---

## 🔍 Summary Table

| Function     | Kaam (Roman Urdu)                              |
|--------------|-------------------------------------------------|
| LENGTH()     | String ki lambai nikalta hai                    |
| LOWER()      | Chhoti letters mein convert karta hai           |
| UPPER()      | Capital letters mein convert karta hai          |
| TRIM()       | Start/end se spaces hataata hai                 |
| SUBSTRING()  | String ka hissa nikalta hai                     |
| REPLACE()    | Text ko badalta hai                             |
| CONCAT()     | Strings ko jorta hai                            |
| LEFT()       | Starting se n characters nikalta hai            |
| RIGHT()      | End se n characters nikalta hai                 |
| CHARINDEX()  | Character ki position batata hai                |

---

In functions ko use karke aap apne SQL queries mein text data par powerful operations kar sakte hain — chahe data cleaning ho, formatting ho ya searching.


# SQL Date & Time Functions (Roman Urdu mein)

Date & Time functions un scenarios mein use hoti hain jahan humein date ya time ke saath kaam karna hota hai — jaise aaj ki date lena, koi specific hissa nikalna, dinon ka farq nikalna, waghera.

---

## `GETDATE()` — Aaj ki tareekh aur waqt  
Yeh function current system date aur time return karta hai.

**Example:**
```sql
SELECT GETDATE() AS CurrentDateTime;
```

---

## `CURRENT_TIMESTAMP` — Aaj ki tareekh aur waqt (alternate)  
`GETDATE()` jaisa hi kaam karta hai.

**Example:**
```sql
SELECT CURRENT_TIMESTAMP AS Now;
```

---

## `DATEPART()` — Date ka specific hissa nikalna  
Jaise saal, mahina, din, hour, etc.

**Syntax:**  
```sql
DATEPART(part, date)
```

**Example:**
```sql
SELECT 
  DATEPART(year, GETDATE()) AS Saal,
  DATEPART(month, GETDATE()) AS Mahina,
  DATEPART(day, GETDATE()) AS Din;
```

---

## `DATENAME()` — Date ke hissey ka naam return karta hai  
Jaise din ka naam, mahine ka naam, etc.

**Example:**
```sql
SELECT 
  DATENAME(weekday, GETDATE()) AS AajKaDin,
  DATENAME(month, GETDATE()) AS AajKaMahina;
```

---

## `DAY()`, `MONTH()`, `YEAR()` — Date ke hisse nikalna  
Seedha din, mahina, saal nikalne ke liye.

**Example:**
```sql
SELECT 
  DAY(GETDATE()) AS Din,
  MONTH(GETDATE()) AS Mahina,
  YEAR(GETDATE()) AS Saal;
```

---

## `DATEDIFF()` — Do dates ka farq (difference) nikalna  
Date1 aur Date2 ke darmiyan din, mahine, ya saal ka farq.

**Syntax:**  
```sql
DATEDIFF(part, start_date, end_date)
```

**Example:**
```sql
SELECT 
  DATEDIFF(day, '2023-01-01', GETDATE()) AS DinKaFarq,
  DATEDIFF(month, '2023-01-01', GETDATE()) AS MahinayKaFarq;
```

---

## `DATEADD()` — Kisi date mein din, mahina ya saal add karna  
Kisi date mein kuch time add karke future ya past date nikalta hai.

**Syntax:**
```sql
DATEADD(part, number, date)
```

**Example:**
```sql
SELECT 
  DATEADD(day, 10, GETDATE()) AS DasDinBaad,
  DATEADD(month, -1, GETDATE()) AS PichlaMahina;
```

---

## `EOMONTH()` — Month ka aakhri din nikalna  
**Example:**
```sql
SELECT 
  EOMONTH(GETDATE()) AS MonthEndDate;
```

---

## `SWITCHOFFSET()` — Time zone ka offset change karta hai  
**Example:**
```sql
SELECT SWITCHOFFSET(SYSDATETIMEOFFSET(), '+05:00') AS PakistanTime;
```

---

## 🔍 Summary Table

| Function         | Kaam (Roman Urdu)                                     |
|------------------|--------------------------------------------------------|
| GETDATE()        | Aaj ki tareekh aur waqt deta hai                      |
| CURRENT_TIMESTAMP| System ki current date & time return karta hai        |
| DATEPART()       | Date ka specific part (saal, mahina, din) nikalta hai |
| DATENAME()       | Date ke part ka naam deta hai                         |
| DAY(), MONTH(), YEAR() | Seedha din, mahina, saal deta hai               |
| DATEDIFF()       | Do dates ka farq nikalta hai                          |
| DATEADD()        | Kisi date mein din/mahina/saal add/subtract karta hai |
| EOMONTH()        | Mahine ka aakhri din batata hai                       |
| SWITCHOFFSET()   | Time zone offset ko change karta hai                  |

---

In date functions ka use kar ke aap reports, trends, calculations aur date filtering mein powerful queries likh sakte hain.

# SQL Window Functions (Roman Urdu + Real-Time Examples + Output)

Window functions aise SQL functions hain jo multiple rows ke upar calculation karte hain — lekin har row ka result separately return karte hain. Bohat useful hote hain analytics mein, jaise ranking, running totals, comparison, etc.

---

## 🎓 Sample Table: Employees

| EmpID | Name   | Department | Salary |
|-------|--------|------------|--------|
| 1     | Ali    | HR         | 50000  |
| 2     | Sara   | IT         | 80000  |
| 3     | Ahmed  | HR         | 60000  |
| 4     | Ayesha | IT         | 85000  |
| 5     | Usman  | Sales      | 55000  |

---

## 1. `ROW_NUMBER()` – Har row ko unique number deta hai per group

```sql
SELECT 
  Name, Department, Salary,
  ROW_NUMBER() OVER(PARTITION BY Department ORDER BY Salary DESC) AS RowNum
FROM Employees;
```

🔹 **Output:**

| Name   | Department | Salary | RowNum |
|--------|------------|--------|--------|
| Ahmed  | HR         | 60000  | 1      |
| Ali    | HR         | 50000  | 2      |
| Ayesha | IT         | 85000  | 1      |
| Sara   | IT         | 80000  | 2      |
| Usman  | Sales      | 55000  | 1      |

---

## 2. `RANK()` – Same salary walon ko same rank deta hai (gap ke saath)

```sql
SELECT 
  Name, Department, Salary,
  RANK() OVER(PARTITION BY Department ORDER BY Salary DESC) AS RankNum
FROM Employees;
```

🔹 **Output:**

| Name   | Department | Salary | RankNum |
|--------|------------|--------|---------|
| Ahmed  | HR         | 60000  | 1       |
| Ali    | HR         | 50000  | 2       |
| Ayesha | IT         | 85000  | 1       |
| Sara   | IT         | 80000  | 2       |
| Usman  | Sales      | 55000  | 1       |

---

## 3. `DENSE_RANK()` – Same rank deta hai, lekin without skipping numbers

```sql
SELECT 
  Name, Department, Salary,
  DENSE_RANK() OVER(PARTITION BY Department ORDER BY Salary DESC) AS DenseRank
FROM Employees;
```

🔹 **Output (Same as RANK in this case):**

| Name   | Department | Salary | DenseRank |
|--------|------------|--------|-----------|
| Ahmed  | HR         | 60000  | 1         |
| Ali    | HR         | 50000  | 2         |
| Ayesha | IT         | 85000  | 1         |
| Sara   | IT         | 80000  | 2         |
| Usman  | Sales      | 55000  | 1         |

---

## 4. `NTILE(2)` – Salary ke base pe data ko 2 buckets mein divide karta hai

```sql
SELECT 
  Name, Salary,
  NTILE(2) OVER(ORDER BY Salary DESC) AS SalaryGroup
FROM Employees;
```

🔹 **Output:**

| Name   | Salary | SalaryGroup |
|--------|--------|-------------|
| Ayesha | 85000  | 1           |
| Sara   | 80000  | 1           |
| Ahmed  | 60000  | 2           |
| Usman  | 55000  | 2           |
| Ali    | 50000  | 2           |

---

## 5. `LAG()` – Pehle row ki salary dikhaata hai

```sql
SELECT 
  Name, Salary,
  LAG(Salary, 1) OVER(ORDER BY Salary) AS PreviousSalary
FROM Employees;
```

🔹 **Output:**

| Name   | Salary | PreviousSalary |
|--------|--------|----------------|
| Ali    | 50000  | NULL           |
| Usman  | 55000  | 50000          |
| Ahmed  | 60000  | 55000          |
| Sara   | 80000  | 60000          |
| Ayesha | 85000  | 80000          |

---

## 6. `LEAD()` – Agli row ki salary dikhaata hai

```sql
SELECT 
  Name, Salary,
  LEAD(Salary, 1) OVER(ORDER BY Salary) AS NextSalary
FROM Employees;
```

🔹 **Output:**

| Name   | Salary | NextSalary |
|--------|--------|------------|
| Ali    | 50000  | 55000      |
| Usman  | 55000  | 60000      |
| Ahmed  | 60000  | 80000      |
| Sara   | 80000  | 85000      |
| Ayesha | 85000  | NULL       |

---

## 7. `FIRST_VALUE()` – Group ya window ki pehli value return karta hai

```sql
SELECT 
  Name, Department, Salary,
  FIRST_VALUE(Salary) OVER(PARTITION BY Department ORDER BY Salary ASC) AS MinDeptSalary
FROM Employees;
```

🔹 **Output:**

| Name   | Department | Salary | MinDeptSalary |
|--------|------------|--------|---------------|
| Ali    | HR         | 50000  | 50000         |
| Ahmed  | HR         | 60000  | 50000         |
| Sara   | IT         | 80000  | 80000         |
| Ayesha | IT         | 85000  | 80000         |
| Usman  | Sales      | 55000  | 55000         |

---

## 8. `LAST_VALUE()` – Group ya window ki last value return karta hai (correct windowing needed)

```sql
SELECT 
  Name, Department, Salary,
  LAST_VALUE(Salary) OVER(
    PARTITION BY Department ORDER BY Salary ASC 
    ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING
  ) AS MaxDeptSalary
FROM Employees;
```

🔹 **Output:**

| Name   | Department | Salary | MaxDeptSalary |
|--------|------------|--------|----------------|
| Ali    | HR         | 50000  | 60000          |
| Ahmed  | HR         | 60000  | 60000          |
| Sara   | IT         | 80000  | 85000          |
| Ayesha | IT         | 85000  | 85000          |
| Usman  | Sales      | 55000  | 55000          |

---

## 9. `SUM()` OVER – Running Total of Salary

```sql
SELECT 
  Name, Salary,
  SUM(Salary) OVER(ORDER BY Salary) AS RunningSalaryTotal
FROM Employees;
```

🔹 **Output:**

| Name   | Salary | RunningSalaryTotal |
|--------|--------|--------------------|
| Ali    | 50000  | 50000              |
| Usman  | 55000  | 105000             |
| Ahmed  | 60000  | 165000             |
| Sara   | 80000  | 245000             |
| Ayesha | 85000  | 330000             |

---

## 10. `AVG()` OVER – Department-wise average salary

```sql
SELECT 
  Name, Department, Salary,
  AVG(Salary) OVER(PARTITION BY Department) AS AvgDeptSalary
FROM Employees;
```

🔹 **Output:**

| Name   | Department | Salary | AvgDeptSalary |
|--------|------------|--------|----------------|
| Ali    | HR         | 50000  | 55000          |
| Ahmed  | HR         | 60000  | 55000          |
| Sara   | IT         | 80000  | 82500          |
| Ayesha | IT         | 85000  | 82500          |
| Usman  | Sales      | 55000  | 55000          |

---

 **Yeh sab Window Functions report generation, dashboards, aur analytics ke liye bohot kaam aate hain** — jaise performance reports, financial summaries, leaderboard rankings, etc.

Agle topic ka kehna ho to batayen: **JOINS**, **CTEs**, **Subqueries**, ya **Pivot Tables**?

# SQL Conditional Functions (Roman Urdu + Real-Time Examples + Output)

Conditional functions SQL mein istamaal hoti hain taake hum data ko condition ke basis par manipulate ya classify kar saken — jaise agar salary zyada ho to "High", warna "Low", etc.

---

## 🎓 Sample Table: Employees

| EmpID | Name   | Department | Salary | BonusEligible |
|-------|--------|------------|--------|---------------|
| 1     | Ali    | HR         | 50000  | Yes           |
| 2     | Sara   | IT         | 80000  | No            |
| 3     | Ahmed  | HR         | 60000  | Yes           |
| 4     | Ayesha | IT         | 85000  | Yes           |
| 5     | Usman  | Sales      | 55000  | No            |

---

## 1. `CASE` Statement – Condition ke mutabiq custom output dena

```sql
SELECT 
  Name, Salary,
  CASE 
    WHEN Salary >= 80000 THEN 'High'
    WHEN Salary >= 60000 THEN 'Medium'
    ELSE 'Low'
  END AS SalaryCategory
FROM Employees;
```

🔹 **Output:**

| Name   | Salary | SalaryCategory |
|--------|--------|----------------|
| Ali    | 50000  | Low            |
| Sara   | 80000  | High           |
| Ahmed  | 60000  | Medium         |
| Ayesha | 85000  | High           |
| Usman  | 55000  | Low            |

---

## 2. `IF()` – Simple condition (sirf MySQL mein hoti hai)

```sql
SELECT 
  Name, Salary,
  IF(Salary > 60000, 'Above Avg', 'Below Avg') AS SalaryLabel
FROM Employees;
```

🔹 **Output:**

| Name   | Salary | SalaryLabel |
|--------|--------|-------------|
| Ali    | 50000  | Below Avg   |
| Sara   | 80000  | Above Avg   |
| Ahmed  | 60000  | Below Avg   |
| Ayesha | 85000  | Above Avg   |
| Usman  | 55000  | Below Avg   |

---

## 3. `IIF()` – SQL Server mein IF ka short form

```sql
SELECT 
  Name, Salary,
  IIF(Salary >= 60000, 'Eligible', 'Not Eligible') AS BonusStatus
FROM Employees;
```

🔹 **Output:**

| Name   | Salary | BonusStatus   |
|--------|--------|---------------|
| Ali    | 50000  | Not Eligible  |
| Sara   | 80000  | Eligible      |
| Ahmed  | 60000  | Eligible      |
| Ayesha | 85000  | Eligible      |
| Usman  | 55000  | Not Eligible  |

---

## 4. `NULLIF()` – Dono values barabar hon to NULL return karega, warna pehli value

```sql
SELECT 
  Name, BonusEligible,
  NULLIF(BonusEligible, 'Yes') AS BonusCheck
FROM Employees;
```

🔹 **Output:**

| Name   | BonusEligible | BonusCheck |
|--------|----------------|------------|
| Ali    | Yes            | NULL       |
| Sara   | No             | No         |
| Ahmed  | Yes            | NULL       |
| Ayesha | Yes            | NULL       |
| Usman  | No             | No         |

---

## 5. `COALESCE()` – Pehli non-null value return karta hai

```sql
SELECT 
  Name,
  COALESCE(NULL, NULL, Salary, 0) AS FinalSalary
FROM Employees;
```

🔹 **Output:**

| Name   | FinalSalary |
|--------|-------------|
| Ali    | 50000       |
| Sara   | 80000       |
| Ahmed  | 60000       |
| Ayesha | 85000       |
| Usman  | 55000       |

---

## 6. `ISNULL()` – Agar value NULL ho to default value return karo (SQL Server only)

```sql
SELECT 
  Name,
  ISNULL(BonusEligible, 'Pending') AS BonusStatus
FROM Employees;
```

🔹 **Output:**

| Name   | BonusStatus |
|--------|-------------|
| Ali    | Yes         |
| Sara   | No          |
| Ahmed  | Yes         |
| Ayesha | Yes         |
| Usman  | No          |

(Agar kisi row mein NULL hota to 'Pending' show hota)

---

## 7. `CASE WHEN` with Aggregation – Conditional aggregation example

```sql
SELECT 
  Department,
  COUNT(CASE WHEN BonusEligible = 'Yes' THEN 1 END) AS EligibleCount,
  COUNT(CASE WHEN BonusEligible = 'No' THEN 1 END) AS NotEligibleCount
FROM Employees
GROUP BY Department;
```

🔹 **Output:**

| Department | EligibleCount | NotEligibleCount |
|------------|----------------|------------------|
| HR         | 2              | 0                |
| IT         | 1              | 1                |
| Sales      | 0              | 1                |

---

🧠 **Summary:**
- `CASE`, `IF`, `IIF()` – condition ke mutabiq value dena
- `NULLIF()` – same value ho to NULL return
- `COALESCE()` – pehli non-null value return
- `ISNULL()` – agar NULL ho to default value
- Aggregated `CASE` – group-wise condition counting

Yeh functions reporting aur decision-making mein bohat kaam aate hain — jaise grade assign karna, eligibility check karna, ya custom columns banana.

Agle topic ka kehna ho to batayen: **JOINS**, **CTEs**, ya **Subqueries**?


# SQL Table & Schema Related Commands (Roman Urdu + Real-Time Examples + Output)

Yeh commands SQL mein table banane, usmein data insert/update karne, aur table structure modify ya delete karne ke liye use hoti hain. Neeche sab kuch examples ke saath samjhaya gaya hai.

---

## 🎓 Scenario: Student Management System

---

## 1. `CREATE TABLE` – Nayi table banani

```sql
CREATE TABLE Students (
  StudentID INT PRIMARY KEY,
  Name VARCHAR(50),
  Age INT,
  City VARCHAR(50)
);
```

📌 **Output:** Table `Students` create ho gayi.

---

## 2. `INSERT INTO` – Table mein data daalna

```sql
INSERT INTO Students (StudentID, Name, Age, City)
VALUES 
  (1, 'Ali', 20, 'Lahore'),
  (2, 'Sara', 22, 'Karachi'),
  (3, 'Usman', 21, 'Islamabad');
```

📌 **Output:** 3 rows insert ho gayin.

---

## 3. `SELECT *` – Data dekhna table se

```sql
SELECT * FROM Students;
```

🔹 **Output:**

| StudentID | Name   | Age | City       |
|-----------|--------|-----|------------|
| 1         | Ali    | 20  | Lahore     |
| 2         | Sara   | 22  | Karachi    |
| 3         | Usman  | 21  | Islamabad  |

---

## 4. `ALTER TABLE` – Table mein column add/update/delete karna

### ➤ Add column:
```sql
ALTER TABLE Students ADD Grade CHAR(1);
```

 **Output:** `Grade` column add ho gaya.

### ➤ Update Grade:
```sql
UPDATE Students SET Grade = 'A' WHERE StudentID = 1;
```

 **Output:** Ali ka grade update ho gaya.

### ➤ Remove column:
```sql
ALTER TABLE Students DROP COLUMN Grade;
```

 **Output:** `Grade` column delete ho gaya.

---

## 5. `UPDATE` – Kisi row ka data change karna

```sql
UPDATE Students SET City = 'Rawalpindi' WHERE Name = 'Usman';
```

 **Output:** Usman ki city ab Rawalpindi ho gayi.

---

## 6. `DELETE` – Row delete karna

```sql
DELETE FROM Students WHERE StudentID = 2;
```

 **Output:** Sara ka record delete ho gaya.

---

## 7. `SELECT INTO` – Nayi table create karna existing data se

```sql
SELECT * INTO StudentsBackup FROM Students;
```

 **Output:** Nayi table `StudentsBackup` ban gayi, jis mein `Students` ka data copy hua hai.

---

## 8. `DROP TABLE` – Table poori delete karna

```sql
DROP TABLE StudentsBackup;
```

 **Output:** `StudentsBackup` table permanently delete ho gayi.

---

 **Summary:**
| Command       | Kaam |
|---------------|------|
| `CREATE TABLE` | Nayi table banata hai |
| `INSERT INTO`  | Data insert karta hai |
| `SELECT`       | Data dekhne ke liye |
| `UPDATE`       | Data modify karta hai |
| `DELETE`       | Row delete karta hai |
| `ALTER TABLE`  | Table ka structure change karta hai |
| `SELECT INTO`  | Nayi table banata hai aur data copy karta hai |
| `DROP TABLE`   | Table delete karta hai |

Ye sab commands **table structure aur data management** ke liye basic aur essential hain.

Agle topic mein `JOINS`, `Views`, ya `CTEs` chahiye ho to batayen 
