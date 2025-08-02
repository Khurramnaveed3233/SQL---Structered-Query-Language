# 📊 Comparison & Logical Operators ka Istemaal (Roman Urdu mein)

Yeh operators data ko **filter**, **query** aur **analyze** karne ke liye use hote hain — chahe aap SQL use kar rahe ho, Python (Pandas), ya Power BI jaise tools.

---

## 🔁 1. Comparison Operators (Muqabla Karnay Wale)

| Operator | Matlab                       | Example                    | Real Life Use Case |
|----------|------------------------------|----------------------------|---------------------|
| =        | Barabar                      | `salary = 50000`           | Wo log jin ki salary exactly 50,000 ho |
| != or <> | Barabar nahi                 | `city != 'Lahore'`         | Lahore ke ilawa sari cities dekhni ho |
| <        | Chhota                       | `age < 30`                 | Aise log jo 30 se chhote hon |
| >        | Bara                         | `revenue > 100000`         | Products jin ka revenue 1 lakh se zyada ho |
| <=       | Chhota ya barabar            | `rating <= 3.5`            | Low-rated cheezein (3.5 ya us se kam) |
| >=       | Bara ya barabar              | `experience >= 5`          | 5 ya us se zyada experience walay log |

---

## 🧠 2. Logical Operators (Mantaqi Operators)

Ye operators multiple shartein combine karne ke kaam aate hain.

### ✅ AND
**Jab dono conditions true hon**

```sql
SELECT * FROM customers
WHERE age > 25 AND income > 50000;
```

🔍 *25 se upar aur 50k+ kamai walay customers*

---

### ✅ OR
**Agar aik bhi condition true ho**

```sql
SELECT * FROM orders
WHERE status = 'Pending' OR status = 'Delayed';
```

🔍 *Woh orders jo abhi complete nahi hue*

---

### ✅ NOT
**Condition ka ulta karta hai**

```sql
SELECT * FROM products
WHERE NOT category = 'Electronics';
```

🔍 *Electronics ke ilawa sari cheezein*

---

### ✅ BETWEEN
**Aik range ke andar value check karta hai (inclusive)**

```sql
SELECT * FROM sales
WHERE sale_date BETWEEN '2024-01-01' AND '2024-12-31';
```

🔍 *2024 ke andar ki sales dekhni ho*

---

### ✅ IN
**List ke andar koi value match ho**

```sql
SELECT * FROM employees
WHERE department IN ('HR', 'Finance', 'IT');
```

🔍 *Specific departments ke employees dhoondhna*

---

### ✅ LIKE
**Pattern match karna (wildcard ke sath)**

| Pattern | Matlab                      |
|---------|-----------------------------|
| %       | Koi bhi letters ya characters |
| _       | Sirf aik character           |

```sql
SELECT * FROM customers
WHERE email LIKE '%.edu';
```

🔍 *University walay emails (students mostly)*

---

### ✅ IS NULL / IS NOT NULL
**Khaali ya filled value check karta hai**

```sql
-- Khaali entries
SELECT * FROM surveys WHERE response IS NULL;

-- Filled entries
SELECT * FROM surveys WHERE response IS NOT NULL;
```

🔍 *Data cleaning ke liye missing values find karna*

---

## 🛠 Real-Time Data Science mein Istemaal

### 1. **Data Cleaning (Python / Pandas)**:
```python
df[df['age'] > 30]
df[df['city'].isin(['Lahore', 'Karachi'])]
df[df['email'].str.contains('.edu')]
```

### 2. **SQL for Dashboards (Power BI / Tableau)**:
```sql
SELECT * FROM traffic_data
WHERE region = 'North' AND speed > 80;
```

### 3. **Exploratory Data Analysis (EDA)**:
- Missing values dhoondhna: `df[df['column'].isnull()]`
- Filter karna: `df[(df['income'] > 50000) & (df['age'] < 35)]`

---

✅ **Conclusion**:  
Yeh sare operators data analysis mein **bohot zaroori** hain — filtering, reporting, dashboards, aur even predictive modeling mein yeh har jagah kaam aate hain.

