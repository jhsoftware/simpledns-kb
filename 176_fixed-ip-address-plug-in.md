---
category: 8
frontpage: false
comments: true
refs: 110,149
created-utc: 2019-01-01
modified-utc: 2020-01-07
---
# Fixed IP Address plug-in

This plug-in serves a fixed IP address (IPv4 and/or IPv6) to all DNS requests for host records (A/AAAA).  
This can be used as a simple way to host DNS records.

WARNING: By default, this plug-in responds to ALL requests for A/AAAA records. It is therefore important to limit which DNS requests are processed using the settings in the "DNS Requests" tab.

On the "Plug-In Settings" tab, enter the IP address(es) and TTL value to respond with.  
At least one of the IP addresses (IPv4 or IPv6) must be specified, but the other can be left blank:

![](img/176/1.png)

