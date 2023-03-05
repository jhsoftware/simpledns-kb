---
category: 3
frontpage: false
comments: true
refs: 63,60,61,62
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# Using unqualified domain names (names with no dots)

Whenever you enter a domain name without any dots (unqualified) in a browser, in Windows Explorer, and in most other places, the Windows operating system will always attempt to "complete" the domain name by adding a "DNS suffix" to this.

So if your computer uses a DNS suffix "mydomain.com", and you enter "webserver" in the browser, Windows will try to resolve this as "webserver.mydomain.com".  
This would then be resolved correctly if your DNS server (Simple DNS Plus) is configured with a zone "mydomain.com" and an A-record for "webserver.mydomain.com" in this zone.

Make sure that all the client computers on your LAN are configured with the same DNS suffix(es).

See the reference articles below for details on how to configure DNS suffixes.

NOTE: Computers configured to get their IP address from a DHCP server ("obtain IP address automatically") will typically get the DNS suffix from the DHCP server.

