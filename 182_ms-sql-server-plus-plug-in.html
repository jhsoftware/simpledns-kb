---
title: MS SQL Server "Plus" plug-in
category: 8
frontpage: false
comments: true
refs: 110,181
created-utc: 2019-01-01
modified-utc: 2020-01-08
---
<p>This plug-in queries a Microsoft SQL Server for one or more DNS records of any type.</p>

<p>The &quot;Plus&quot; in the title is to signal that this plug-in is more powerful (and more difficult to use correctly) than the original <a href="https://simpledns.plus/plugin-mssql">MS SQL Server Plug-In</a>.<br />
It is more powerful because it can be fetch multiple DNS records of any type, whereas the original can only fetch a single host or reverse record.<br />
This &quot;Plus&quot; version also requires an &quot;unlimited zones&quot; license for Simple DNS Plus, whereas the original works with any license size.</p>

<p>SQL queries are executed asynchronously (in a separate thread) and therefore won't slow down other requests not using the plug-in.</p>

<p>In the plug-in instance dialog / Plug-In Settings tab you can specify the database connection string and SQL SELECT statement to be used to fetch records:</p>

<p> <img src="img/182/1.png" /></p>

<p>A helper dialog is available to build the database connection string:</p>

<p><img src="img/182/2.png" /></p>

<p>And in the plug-in instance dialog / Ask About tab, you can specify which domain name and record types the plug-in will be queried about:</p>

<p><img src="img/182/3.png"  /></p>

<p>There are no specific requirements for database table layout. You just need to be able to execute an SQL query which returns the required data. The query can be based on a table, view, stored procedure, or any other valid SQL expression.</p>

<p>Your SELECT statement may optionally include the parameters @QNAME (the requested domain name), @QTYPE (the requested DNS record type), and @QIP (the IP address where the DNS request came from).</p>

<p>Your SELECT statement must return a &quot;RecData&quot; column with DNS record data in zone file format, and can optionally return &quot;RecName&quot;, &quot;RecType&quot;, &quot;RecTTL&quot;, and &quot;RecSec&quot; columns.<br />
It is important that the string data returned in the RecData column is in the correct format as defined by the DNS RFCs.<br />
For example the data for an MX-record might be: &quot;10 mail.example.com.&quot; (without quotes), and for a TXT-record: &quot;sample text&quot; (WITH quotes).</p>

<p>NOTE: Serving data from directly from a SQL server with this plug-in can be very powerful, but keep in mind that querying a SQL server will never be as fast as serving DNS records directly from RAM, as Simple DNS Plus does when serving data from local zones. Therefore we recommend that you limit plug-in queries to only those specific domains and record types that you have stored in SQL.</p>