---
category: 9
frontpage: false
comments: true
vgroup: 6
vname: IPv6
vsort: 2
refs: 153,53,64
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# How to sub-delegate a reverse zone (IPv6)

If for example you are an ISP providing Internet connections to your customers, you can sub-delegate reverse DNS for the IP addresses that you provide to your customers to the customers' own DNS servers.
This makes it possible for your customers to control their own reverse DNS without contacting you every time they need this updated.

Typically you would only do this for customers with multiple static IP addresses.
For customers with only one IP address or dynamic IP addresses, it usually makes more sense to host the reverse DNS records on your own DNS server.

Before you can sub-delegate reverse DNS to others, reverse DNS for your IP range(s) must of course first be delegated to your DNS servers. For more on this see [this article](/kb/53/how-do-i-get-reverse-dns-for-my-ip-addresses-delegated-to-my-own-dns-server).

A reverse DNS record for an IPv6 address is a PTR-record where the record name is the hex-digits of the IP address in reverse order + ".ip6.arpa". For example for the IP address "1234:5678:9ABC:DEF0:1234:5678:9ABC:DEF0" the reverse DNS record would be a PTR-record named "0.f.e.d.c.b.a.9.8.7.6.5.4.3.2.1.0.f.e.d.c.b.a.9.8.7.6.5.4.3.2.1.ip6.arpa".

Reverse zones can be subdelegated at any dot in this name - that is at every 4 bits (/124, /120, /116, etc.).
For example if you own the /64 subnet of above IP address, your reverse zone name would be "0.f.e.d.c.b.a.9.8.7.6.5.4.3.2.1.ip6.arpa".

In order the sub-delegate reverse DNS for 1234:5678:9ABC:DEF0:3000::/68 you would add the following NS-records to the zone:

NS: 3.0.f.e.d.c.b.a.9.8.7.6.5.4.3.2.1.ip6.arpa -> ns1.customer.com\
NS: 3.0.f.e.d.c.b.a.9.8.7.6.5.4.3.2.1.ip6.arpa -> ns2.customer.com