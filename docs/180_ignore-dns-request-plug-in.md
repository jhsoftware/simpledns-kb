---
category: 8
frontpage: false
comments: true
refs: 110,6
created-utc: 2019-01-01
modified-utc: 2020-01-08
---
# Ignore DNS Request plug-in

This plug-in instructs Simple DNS Plus to ignore (not answer) all DNS requests that the plug-in processes.

This can be used to ignore requests from specific IP addresses, for specific domain names, record types, etc.  
As an example, you could configure it to ignore DNS requests from IP addresses listed by a blacklist plug-in.

IMPORTANT: By default this plug-in instructs Simple DNS Plus to ignore ALL DNS requests, so it is important that it be limited in scope using the "DNS Requests" tab:

![](img/180/1.png)

