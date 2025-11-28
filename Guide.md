# 📘 **PRACTICAL MANUAL: Pandas & NumPy**

---

# ✅ **1. Loading a CSV File & Basic Data Inspection**

### **📌 Objective**

Learn how to read a CSV file, inspect data, handle missing values, and remove duplicates.

---

### **🧭 Steps**

1. Import Pandas
2. Load a CSV file into a DataFrame
3. Inspect the data (head, info, missing values)
4. Handle missing values (drop or fill)
5. Remove duplicate rows

---

### **💻 Example Code**

```python
import pandas as pd

# 1. Load dataset
df = pd.read_csv("data.csv")

# 2. Inspect data
print(df.head())            # first 5 rows
print(df.info())            # data types + null info
print(df.isnull().sum())    # count missing values per column

# 3. Handle missing values
df = df.fillna(0)           # replace missing values
# OR df = df.dropna()       # remove rows with missing values

# 4. Remove duplicate rows
df = df.drop_duplicates()

print(df)
```

---

# ✅ **2. Column Operations in Pandas**

### **📌 Objective**

Add new columns, rename columns, change data types, and remove unnecessary columns.

---

### **🧭 Steps**

1. Add a calculated column
2. Rename columns
3. Convert data types
4. Drop columns

---

### **💻 Example Code**

```python
df = pd.DataFrame({
    "A": [10, 20, 30],
    "B": [5, 10, 20]
})

# Add new calculated column
df["C"] = df["A"] + df["B"]

# Rename columns
df = df.rename(columns={"A": "Column_A", "B": "Column_B"})

# Change data type
df["Column_A"] = df["Column_A"].astype(float)

# Drop unnecessary columns
df = df.drop(columns=["C"])

print(df)
```

---

# ✅ **3. NumPy Random Data & Statistics**

### **📌 Objective**

Generate 1000 random values and calculate statistical measures.

---

### **🧭 Steps**

1. Generate random numbers
2. Compute mean, median, variance, std, min & max

---

### **💻 Example Code**

```python
import numpy as np

# Random dataset of 1000 numbers
data = np.random.randn(1000)

print("Mean:", np.mean(data))
print("Median:", np.median(data))
print("Variance:", np.var(data))
print("Standard Deviation:", np.std(data))
print("Minimum:", np.min(data))
print("Maximum:", np.max(data))
```

---

# ✅ **4. Grouping Data using groupby()**

### **📌 Objective**

Group data by categories and calculate summary statistics.

---

### **🧭 Steps**

1. Create a DataFrame
2. Use `groupby()` on categorical columns
3. Apply count, mean, std

---

### **💻 Example Code**

```python
import pandas as pd

df = pd.DataFrame({
    "Category": ["A", "A", "B", "B", "B"],
    "Sales": [100, 200, 150, 300, 250],
    "Profit": [10, 20, 15, 30, 25]
})

grouped = df.groupby("Category").agg({
    "Sales": ["count", "mean", "std"],
    "Profit": ["mean", "std"]
})

print(grouped)
```

---

# ✅ **5. Filtering Rows with .loc and .query()**

### **📌 Objective**

Filter rows using conditions such as sales threshold and region.

---

### **🧭 Steps**

1. Use `.loc` for condition-based filtering
2. Use `.query()` for readable SQL-like queries

---

### **💻 Example Code**

```python
df = pd.DataFrame({
    "region": ["North", "South", "North", "East"],
    "sales": [500, 200, 800, 150]
})

# Using .loc
filtered_loc = df.loc[(df["sales"] > 300) & (df["region"] == "North")]

# Using .query()
filtered_query = df.query("sales > 300 and region == 'North'")

print(filtered_loc)
print(filtered_query)
```

---

# ✅ **6. NumPy Matrix Operations (3×3)**

### **📌 Objective**

Create matrices and perform various mathematical operations.

---

### **🧭 Steps**

1. Create two 3×3 matrices with random integers
2. Perform addition, subtraction, multiplication
3. Perform element-wise division
4. Compute determinant and inverse

---

### **💻 Example Code**

```python
import numpy as np

A = np.random.randint(1, 10, (3,3))
B = np.random.randint(1, 10, (3,3))

add = A + B
sub = A - B
multiply = A @ B
elementwise_div = A / B

det_A = np.linalg.det(A)
inverse_A = np.linalg.inv(A)

print("A:\n", A)
print("B:\n", B)
print("Addition:\n", add)
print("Subtraction:\n", sub)
print("Matrix Multiplication:\n", multiply)
print("Element-wise Division:\n", elementwise_div)
print("Determinant of A:", det_A)
print("Inverse of A:\n", inverse_A)
```

---

# ✅ **7. Merging DataFrames (Joins)**

### **📌 Objective**

Join two DataFrames using different join methods.

---

### **🧭 Steps**

1. Create two sample tables (customers, orders)
2. Apply merge with:

   * inner join
   * left join
   * right join
   * outer join

---

### **💻 Example Code**

```python
import pandas as pd

customers = pd.DataFrame({
    "customer_id": [1, 2, 3],
    "name": ["Alice", "Bob", "Charlie"]
})

orders = pd.DataFrame({
    "order_id": [101, 102, 103],
    "customer_id": [1, 2, 4],
    "amount": [250, 120, 300]
})

inner_join = customers.merge(orders, on="customer_id", how="inner")
left_join  = customers.merge(orders, on="customer_id", how="left")
right_join = customers.merge(orders, on="customer_id", how="right")
outer_join = customers.merge(orders, on="customer_id", how="outer")

print("Inner Join:\n", inner_join)
print("Left Join:\n", left_join)
print("Right Join:\n", right_join)
print("Outer Join:\n", outer_join)
```


Below are clear, complete examples for **Questions 8, 9, and 10** using **Pandas** and **NumPy**.
Each solution includes sample code + explanation.

---

# **8. Time Series Analysis Using Pandas DateTime Features**

### **Sample Dataset**

```python
import pandas as pd

data = {
    'date': ['2024-01-05', '2024-01-15', '2024-02-10', '2024-02-22', '2024-03-11'],
    'sales': [1200, 1500, 1700, 1600, 2000]
}

df = pd.DataFrame(data)
```

### **Convert to DateTime**

```python
df['date'] = pd.to_datetime(df['date'])
```

### **Extract year, month, day, weekday**

```python
df['year'] = df['date'].dt.year
df['month'] = df['date'].dt.month
df['day'] = df['date'].dt.day
df['weekday'] = df['date'].dt.day_name()
```

### **Group by month and calculate monthly sales**

```python
monthly_sales = df.groupby('month')['sales'].sum()
```

### **Result**

```python
print(df)
print(monthly_sales)
```

---

# **9. NumPy: Boolean Indexing + Random Array Filtering**

### **Generate 1D array of 100 random integers**

```python
import numpy as np

arr = np.random.randint(1, 1001, size=100)
```

### **Filter values: >500 and <800**

```python
filtered = arr[(arr > 500) & (arr < 800)]
```

### **Calculate mean of filtered values**

```python
mean_val = filtered.mean()
```

### **Output**

```python
print("Filtered values:", filtered)
print("Mean:", mean_val)
```

---

# **10. Pandas Pivot Table for Product-wise Sales per Region**

### **Sample Sales Data**

```python
import pandas as pd

data = {
    'Region': ['North', 'South', 'East', 'West', 'North', 'South'],
    'Product': ['A', 'A', 'B', 'A', 'B', 'B'],
    'Sales': [1500, 1200, 1800, 1400, 1600, 2000]
}

df = pd.DataFrame(data)
```

### **Create Pivot Table**

```python
pivot = df.pivot_table(
    values='Sales',
    index='Region',
    columns='Product',
    aggfunc='sum',
    fill_value=0
)
```

### **Result**

```python
print(pivot)
```

