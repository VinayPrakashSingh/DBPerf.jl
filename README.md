###### This repository will contain the code that benchmarks all the Julia Database Drivers / Wrappers , End-Users can utilize this code to compare the performance between various Database drivers available in Julia. This code creates an artificial datasets of given size (Size can be specified in config.jl ) and performs following operations using one of the Database driver: Create, Insert, Update, Drop and retrieving the records from DataBase as a DataFrame. (End-Users can specify which Database driver they would like to use)

Datasets being created would cover following Data-types: ```TINYINT, SMALLINT, MEDIUMINT, INTEGER, BIGINT, FLOAT, DOUBLE, DOULBE PRECISION, DATETIME, CHAR, VARCHAR, ENUM```

Measures have been taken such that the random values being generated are well within the Lower bound and Upper bound of that particular datatype.

# USAGE

End-Users can provide input through command-line mode or they can directly invoke function ```DBPerf()``` and provide input as arguments.


#### Command-Line mode

```
$ julia DBPerf.jl <Database_Driver_1.jl> <Database_Driver_2.jl> ....... <Database_Driver_N.jl> <DBMS>
```
Wherein
* Database_Driver.jl can be one of the following: ODBC.jl, JDBC.jl, PostgreSQL.jl, MySQL.jl
* DBMS field is applicable only if you're using JDBC.jl, DBMS can be either one of the following: Oracle, MySQL

###### Example
```
DBPerf.jl ODBC.jl JDBC.jl Oracle
```
Above example will conduct a performance test on Database driver ODBC.jl and JDBC.jl, DBMS will be automatically selected for ODBC.jl based on the credentials provided in config.jl, whereas JDBC.jl will be tested against Oracle


#### Executing from Julia prompt 

```
julia> include("DBPerf.jl")
julia> DBPerf(<Database_Driver_1.jl>, <Database_Driver_2.jl>, ....... <Database_Driver_N.jl>, <DBMS>)
```
###### Example
```
DBPerf("ODBC.jl","JDBC.jl","Oracle")
```
Above example will conduct a performance test on Database driver ODBC.jl and JDBC.jl, DBMS will be automatically selected for ODBC.jl based on the credentials provided in config.jl, whereas JDBC.jl will be tested against Oracle

#### config.jl should contain all the credentials required for a DBMS connection and end-users can specify the size of the dataset to be created in config.jl

# TODO
1. Adding a functionality to check whether the retrieved records match the Inserted/Updated values. 
2. Include MongoDB, HBase, SQLite and Spark SQL in the performance test.
3. Create a performance table that lists the performance results for all the Database drivers. 
4. Creating an automated script that pulls the latest code from all the database drivers to conduct a performance test and automatically update the performance table every week.
