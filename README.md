<h1>Work with Data Tables in Python with SQLAlchemy</h1>
<p align="center">
<img src="https://github.com/andrew-disario/sql-with-python/blob/main/sql_python_pandas%20logo.png?raw=true" height="65%" width="65%" alt="sql_python_pandas"/>
<br />
In this project, we work with database tables using Python, Pandas and SQL. Using Pandas' ".read_sql(  )" method we can run SQL queries on existing database tables. Then, using Python and Pandas, we can work with the data as dataframes. Finally, using Pandas' method ".to_sql(  )" we can replace or append the existing tables with out modified dataframes.

<h2>Part I - Querying data with .read_sql(  )</h2>

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

<h2>Part II - Writing data with .to_sql(  ) </h2>

<b> Work with dataframe using Pandas and Python </b>
  1. Modify dataframe to change Maxwell's ID from 3 to 4
```
df['id'][2] = 4
```
  2. Output results to confirm change
```
df
```
<b> Important .to_sql(  ) arguments </b>
```
.to_sql('[TABLE_NAME]', [ENGINE_NAME], if_exists = '[IF_EXISTS_ACTION]', index = True/False)
```
  - ```'[TABLE_NAME]'``` Name of the table you want to create/write to
  - ```[ENGINE NAME]``` Name of the engine connection is running on
  - ```'[IF_EXISTS_ACTION]'``` What action to take if specified table already exists
    - ```'fail'``` Do nothing
    - ```'replace'``` Replace the existing table with dataframe
    - ```'append'``` Append dataframe to existing table
  - ```index = True/False``` Don't ignore / ignore index column

<b> Write modified dataframe to table </b>
1. Replace table with modified dataframe
```
df.to_sql(employees, engine, if_exists = 'replace', index = False)
```
2. Append table with modified dataframe
```
df.to_sql(employees, engine, if_exists = 'append', index = False)
```

<b> View modified tables in MySQL Workbench </b>
1. Open MySQL Workbench
2. Run SQL query
```
SELECT *
FROM db.employees
```
   
