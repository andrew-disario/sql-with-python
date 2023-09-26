<h1>SQL with Python</h1>
<p align="center">
<img src="https://github.com/andrew-disario/sql-with-python/blob/main/sql_python_pandas%20logo.png?raw=true" height="75%" width="75%" alt="sql_python_pandas"/>
<br />
In this project, we work with database tables using Python, Pandas and SQL. Using Pandas' "read_sql" method we can run SQL queries on existing database tables. Then, using Python and Pandas, we can work with the data as dataframes. Finally, using Pandas' method "write_sql" we can replace or append the existing tables with out modified dataframes.
<h2>Querying with read_sql</h2>

<b> Create connection using SQLAlchemy </b>
  1. Import libraries
```
import pandas as pd
import sqlalchemy
import pymysql
from sql alchemy import create_engine
```
  2. Set up a connection string
```
con_string = 'mysql+pymysql://root:my-secret-pw@localhost/employees'
```
  3. Connect engine using connection string
```
engine = create_engine(con_string)
```
  4. Write in SQL query
```
query = """
  SELECT *
  FROM db.employees;
"""
```
  5. Output and view query results as a dataframe
```
df = pd.read_sql(query, engine)

df
```


   
