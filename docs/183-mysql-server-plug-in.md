---
category: 8
frontpage: false
comments: true
refs: 110
created-utc: 2019-01-01
modified-utc: 2020-01-08
---
# MySQL Server plug-in

This plug-in queries a [MySQL Server](http://www.mysql.com/){target=_blank} for host records and optionally reverse records.  
SQL queries are executed asynchronously (in a separate thread) and therefore won't slow down other requests not using the plug-in.

In the plug-in instance dialog / Plug-In Settings tab you can specify the database connection string and SQL SELECT statements to be used to fetch records:

![](img/183/1.png)

Helper dialogs are available to build the connection string and SELECT statements:

![](img/183/2.png)

At least one of the SELECT statement fields must be filled out, but you can leave some blank if you don't want to use that feature.

There are no specific requirements for database table layout. You just need to be able to execute an SQL query which returns the required data. The query can be based on a table, view, stored procedure, or any other valid SQL expression.

For forward lookups (name to IP) you need to include a ?hostname parameter in the SELECT statement, and the query must return two columns; IP-address and TTL as the first and second columns.

For reverse lookups (IP to name) you need to include a ?ipaddress parameter in the SELECT statement, and the query must return two columns; host-name and TTL as the first and second columns.

For either type of lookups (forward/reverse), you may optionally include a ?clientip parameter which will contain the IP address of the client requesting the data.

The column names of the returned data do not matter - only the column order.

If there are more than one row or more than two columns returned, additional rows and columns are ignored.

NOTE: This plug-in is uses the MySQL "Connector/Net 5.0" component v. 5.0.8.1 (included with the plug-in download).  
For details see [http://dev.mysql.com/downloads/connector/net/5.0.html](http://dev.mysql.com/downloads/connector/net/5.0.html){target=_blank}

