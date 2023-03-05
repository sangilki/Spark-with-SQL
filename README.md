# Spark-with-SQL
SQL with Spark
SparkSession also includes all the APIs available in different contexts –

SparkContext,
SQLContext,
StreamingContext,
HiveContext.

pip install findspark 

import findspark
findspark.init()

import pyspark
from pyspark.sql import SparkSession
spark = SparkSession.builder.getOrCreate()
df = spark.sql("select 'spark' as hello ")
df.show()

pwd

pd1 = spark.read.json('sample1.json')

pd1.printSchema()

df2 = spark.read.format("json").load("sample1.json") 

df2.show()

df = spark.read.csv('Sample-Spreadsheet-100-rows.csv', inferSchema=True)
df.show(10)



create a temporary view by using createOrReplaceTempView() and use SparkSession.sql() to run the query. 
# PySpark SQL Group By AVG, SUM, MAX
# Create Temporary table in PySpark
df.createOrReplaceTempView("EMP")

# PySpark SQL
sql_str="select department, sum(salary) as sum_salary," \
"avg(salary) as avg_salary," \
"sum(bonus) as sum_bonus," \
"max(bonus) as max_bonus" \
" from EMP "  \
" group by department having sum_bonus >= 50000"

# Execute SQL
spark.sql(sql_str).show()

