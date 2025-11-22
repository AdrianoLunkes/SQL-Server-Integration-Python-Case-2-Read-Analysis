# SQL-Server-Integration-Python-Case-2-Read-Analysis
SQL Server data analysis in Jupyter using Python's pyodbc. Reads ContosoRetailDW's DimProduct table, analyzing attributes like ColorName and UnitPrice for key business insights and visualizations

# Preparing the Database for Analysis

We will focus on the existing DimProduct table:
```
SELECT ColorName, UnitPrice
FROM DimProduct;
```

This query will be used in Python to:

Analyze the total number of products per color.

Explore product price distribution.

Create visual summaries using graphs.

# Initial Configurations in Jupyter

Step 1 – Install required libraries:
```
!pip install pyodbc pandas matplotlib
```

Step 2 – Import libraries and set up connection:
```
import pyodbc
import pandas as pd
import matplotlib.pyplot as plt

connection_data = (
    "Driver={SQL Server};"
    "Server=SEU_HOSTNAME;"
    "Database=ContosoRetailDW;"
)

connection = pyodbc.connect(connection_data)
print("Connection successful!")
```

🔹 pyodbc: connects Python to SQL Server
🔹 pandas: data analysis and manipulation
🔹 matplotlib: plotting graphs and visualizations

This setup enables direct integration and interaction with SQL Server data.

# Reading Data from SQL Server
# Define SQL command
```
sql_command = "SELECT ColorName, UnitPrice FROM DimProduct"
```
# Execute query and load data into a DataFrame
```
data = pd.read_sql(sql_command, connection)
```
# Display data
```
display(data)
```

Explanation:
The pd.read_sql function executes the SQL query and imports the results into a pandas DataFrame, ready for analysis and visualization.

# Basic Grouping and Visualization

Step 1 – Group products by color:
```
total_products_by_color = data.groupby('ColorName').count()
display(total_products_by_color)
```

This shows the total number of products for each color.

groupby organizes the data for aggregation.

Step 2 – Plot a bar chart:
```
total_products_by_color.plot(kind='bar', y='UnitPrice', legend=False, title='Total Products by Color')
plt.xlabel('Color')
plt.ylabel('Number of Products')
plt.show()
```

Simple bar chart to visualize the distribution of products by color.

Makes it easier to interpret the dataset and identify trends.

✅ Conclusion

The Python and SQL Server Integration Project (Read Analysis) demonstrates how to:

Connect Python directly to SQL Server using pyodbc.

Execute SQL queries inside Jupyter Notebook.

Perform basic grouping and aggregation with pandas.

Create visual summaries with matplotlib.

This project showcases the potential of Python and SQL Server integration for data exploration and KPI analysis. It’s a practical approach to understanding database content quickly and generating insights without advanced complexity.
