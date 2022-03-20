# Reading data from an external database
You can also add data by connecting your existing databases to the datapreparer.

## Supported Databases 
Datapreparer supports: 

- DB2 (version 11.5 or newer)
- Informix(versions 12.10, 14.10)
- MariaDB (version 10.4 or newer)
- MySQL (version 5.6 or newer)
- PostgreSQL (version 8.2 or newer)
- Presto (version 0.234.1 or newer)
- Snowflake (driver version 3.12.3)
- SQL Server (version 2017 or newer)

## Supported Jdbc Connection Strings
> Note: The schema to import needs to be defined where available.
> Jdbc connection strings are in a single line and should be in the following form:

- DB2.jdbc:db2://<\host>:<\port>/<\database>:currentSchema=<\schema>;
user=<\user>;
password=<\password>;
- Informix.jdbc:informix-sqli://<\host>:<\port>/<\database>:user=<\user>;password=<\password>
- MariaDB.jdbc:mariadb://<\host>:<\port>/<\database>?user=<\user>
&password=<\password>
- MySQL.jdbc:mysql://<\host>:<\port>/<\database>?user=<\user>&password=<\password>
- PostgreSQL.jdbc:postgresql://<\host>:<\port>/<\database>?currentSchema=<\schema>
&user=<\user>&password=<\password>
- Presto.jdbc:presto://<\host>:<\port>/<\catalog>/<\schema>?user=<\user>&password=<\password>
- Snowflake.jdbc:snowflake://<\account>.snowflakecomputing.com/?db=<\database>
&schema=<\schema>&user=<\user>&password=<\password>
- SQL Server.jdbc:sqlserver://<\host>:<\port>;database=<\database>;
user=<\user>;password=<\password>;
