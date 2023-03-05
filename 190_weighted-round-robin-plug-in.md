---
category: 8
frontpage: false
comments: true
refs: 110
created-utc: 2019-01-01
modified-utc: 2020-01-08
---
# Weighted Round Robin plug-in

This plug-in serves IP addresses for a host name [round robin](https://simpledns.plus/helplink?p=df_rrobin) from a weighted list.

IP addresses are rotated so that the first visitor gets one IP address, the next visitor another IP address, etc.  
However IP addresses with higher weight values are served more often than IP addresses with lower weight values.  
This makes it possible for example to send more traffic to high capacity servers in a round robin set.

In the plug-in instance dialog / Plug-In Settings tab you can specify the host name, weight / IP addresses, and host record TTL:

![](img/190/1.png)

The weight value for each IP address is a number from 1 to 99.  
You can treat these as percentages if you make sure they total 100.  
However any combination of weight values can be used - they do not need to add up to any specific total.  
With the configuration in the screen shot above, out of 10 requests, 1 response would point to 1.1.1.1, 3 responses to 3.3.3.3 and 6 responses to 6.6.6.6.

This plug-in works with both IPv4 and IPv6 addresses.

NOTE: DNS round robin cannot provide an exact weight distribution of traffic because other DNS server will cache the records and potentially serve multiple end users with the same data, and different end users may use services more or less. But measured on average over time the traffic distribution will be as weighted.

