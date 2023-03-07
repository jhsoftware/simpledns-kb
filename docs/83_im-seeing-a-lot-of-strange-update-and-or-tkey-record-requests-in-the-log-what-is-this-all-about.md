---
category: 7
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# I'm seeing a lot of strange "Update" and/or TKEY-record requests in the log. What is this all about?

Windows Me/2000 and later have an option to "register this connection in DNS" (under Networking TCP/IP properties) which is enabled by default.

This means that every so often these Windows clients will send an "update" request to the primary DNS server for the domain they belong to (computer name) to "register" themselves in DNS.  
If you don't allow "dynamic updates" (the default setting) for that particular domain (see zone properties dialog), the update will be refused by Simple DNS Plus.

After this refusal, the client will try an encrypted update (thinking it was refused because it wasn't secure) which starts with request for a transaction encryption key (TKEY).

Unfortunately this often results in excessive and invalid Update and TKEY requests being sent all over the Internet, to the annoyance of many ISPs and even the Internet root DNS servers.

If you want client computers registered in DNS - enable "dynamic updates" for the zone.  
Otherwise the best thing to do is disabling the "register this connection in DNS" option on all Windows machines.  
(Or contact the people sending the requests and tell them to do so)

