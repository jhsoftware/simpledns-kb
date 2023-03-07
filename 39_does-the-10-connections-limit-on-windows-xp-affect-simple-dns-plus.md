---
category: 1
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# Does the 10 connections limit on Windows XP affect Simple DNS Plus?

The short answer is no.

Windows XP does limit simultaneous inbound TCP connections to 10 clients.

However, DNS only uses TCP connections for zone transfers. So this limitation would only be a problem if you have more than 10 secondary DNS servers all trying to connect at the same time.

Normal DNS requests are not sent via TCP. They are sent via UDP, which is a connectionless protocol, and therefore cannot really be limited.