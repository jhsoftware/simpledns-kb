---
category: 14
frontpage: false
comments: true
refs: 52,57,146
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# Zone not transferred to or updated on secondary DNS server

On the secondary server, check the log file or Windows Event log for any warning messages with a text starting with ”Failed to Zone Transfer...”.

You can view the log live in the main window of Simple DNS Plus (View menu / Active Log), or you can enable logging to log file and/or Windows Event Log in the Options dialog / Logging section.

This warning message will contain the name of the zone attempted transferred, the IP address of the primary DNS server, and a description of the problem encountered.  
For example:  
*** Warning: Failed to Zone Transfer domain.com from 1.2.3.4 (problem description)

First make sure that the zone name is spelled correctly and matches the name used on the primary server, and make sure that the IP address is the correct address of your primary DNS server.

If the problem description is one of the following:  
”Timeout establishing TCP connection”  
”Error connecting...”  
”Error: 10054 The connection is reset by remote side”  
Make sure that any firewall between the primary and the secondary servers allow TCP connections to port 53.  
If your primary DNS server is behind a NAT router (as seen from the secondary server), make sure that you use the public IP address of the router and that port 53 TCP is correctly mapped to the private IP address of the primary DNS server on that router.  
For details see the reference articles below.

If the problem description is ”RCODE 5 Refused...”, check the reference knowledgebase article about this below.

