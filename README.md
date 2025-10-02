# Sales_Dataset_Python_Sql-github.io


🚀 Objective

The goal of this project is to connect Python with a SQLite database, extract sales information using SQL queries, and summarize the results.

We calculate:

Total quantity sold per product

Total revenue per product

The results are displayed in both text format and as a bar chart.

🛠 Tools & Libraries Used

Python

SQLite3 (built-in Python library for database connection)

Pandas (for data handling)

Matplotlib (for visualization)

📂 Dataset

A small SQLite database file named sales_data.db is created.
It contains a single table:

sales

Column	Description
product	Name of the product
quantity	Units sold
price	Price per unit
📌 Steps in the Project

Connect to the SQLite database (sales_data.db).

Run SQL query to get total quantity & revenue per product.

Load query results into pandas DataFrame.

Print results in the console.

Create a bar chart of product revenue using matplotlib.

🧑‍💻 Code Overview
import sqlite3
import pandas as pd
import matplotlib.pyplot as plt

# 1. Connect to database
conn = sqlite3.connect("sales_data.db")

# 2. SQL Query
query = """
SELECT product, 
       SUM(quantity) AS total_qty, 
       SUM(quantity * price) AS revenue
FROM sales
GROUP BY product;
"""

# 3. Load into pandas
df = pd.read_sql_query(query, conn)

# 4. Print results
print(df)

# 5. Plot bar chart
df.plot(kind="bar", x="product", y="revenue", legend=False)
plt.title("Revenue by Product")
plt.ylabel("Revenue")
plt.xlabel("Product")
plt.tight_layout()
plt.savefig("sales_chart.png")
plt.show()

📊 Example Output

Console Output:

  product  total_qty  revenue
0   Apple        150    3000
1  Banana        200    2500
2  Orange        180    2700


Bar Chart:
A bar chart showing revenue for each product.

🎯 Learning Outcomes

Connect Python with SQLite database.

Write and execute SQL queries inside Python.

Use pandas for handling SQL results.

Create simple visualizations with matplotlib.

End-to-end workflow of Data Analysis Project.


📤 Submission

GitHub repo includes:

Python script / Jupyter notebook

SQLite database (sales_data.db)

Generated bar chart (sales_chart.png)

This README.md
