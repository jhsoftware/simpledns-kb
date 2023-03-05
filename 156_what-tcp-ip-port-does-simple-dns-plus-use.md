---
category: 11
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# What TCP/IP port does Simple DNS Plus use?

Simple DNS Plus (and all other DNS servers) listens for DNS requests on port 53 UDP and TCP.

Most DNS requests are via UDP.  
However if a DNS packet is too big for UDP, DNS servers will automatically switch to TCP.

Full zone transfers (synchronizing primary and secondary DNS servers) always use TCP.

