# Big-Query-Magic

#### The package has been created for Mac OS
#### Requirements
It is assumed that you have basic packages like pandas installed
Install Auth2client and pandas_gbq
Ensure that you can query data using pandas gbq
<hr>

This packacge installs a magic in your startup directory which makes querying in jupyter environment more user friendly and easier to use.Post intallation simply type %%BQSQL and write your query
example
```python
%%BQSQL
SELECT *
FROM table
LIMIT 10;
```

<b>There are other features also present which makes it even more user friendly which can be explained with help of the argument this magic can take</b>

-job [Y or None] If Y is passed as job argument this will run just the query but will not pull the out put, this is useful when one is creating a large temp table during the workflow and does not want to download and load it in python, the existing pandas_gbq does not offer that

-save_to [Table Name] Pass a variable in which the output needs to be store

Note Do not pass both the arguments at the same time

-para [Y or None] If Y is passed the query will look if parameters or python variables are used in the query. Yes this is one of the best features of this magic you can use python variables directly in your query

example
```python
x = ['user1','user2']```

```python
%%BQSQL -para Y -job Y
SELECT *
FROM table
WHERE user_id IN @x
```
Currently string int and list of these two can be passed as a parameter. Note parameter needs to be preceded by <b><u> @ </u></b> in case one was planning to use @ just as character in that case please avoid using parameter

#### Installation
Run
```python
from pandas_gbq_magic import magic
magic.install('You Bigquery Project name')
```
Restart Jupyter notebook 
