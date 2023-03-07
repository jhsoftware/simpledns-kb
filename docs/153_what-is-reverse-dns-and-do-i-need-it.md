---
category: 9
frontpage: false
comments: true
refs: 53,77
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# What is "reverse DNS" and do I need it?

Reverse DNS is IP address to domain name mapping - the opposite of forward (normal) DNS which maps domain names to IP addresses.

Reverse DNS is separate from forward DNS.  
Forward DNS for "abc.com" pointing to IP address "1.2.3.4", does not necessarily mean that reverse DNS for IP "1.2.3.4" also points to "abc.com".  
This comes from two separate sets of data.

A special PTR-record type is used to store reverse DNS entries. The name of the PTR-record is the IP address with the segments reversed + ".in-addr.arpa".  
For example the reverse DNS entry for IP 1.2.3.4 would be stored as a PTR-record for "4.3.2.1.in-addr.arpa".

Reverse DNS is also different from forward DNS in who points the zone (domain name) to your DNS server.  
With forward DNS, you point the zone to your DNS server by registering that domain name with a registrar.  
With reverse DNS, your Internet connection provider (ISP) must point (or "sub-delegate") the zone ("....in-addr.arpa") to your DNS server.  
Without this sub-delegation from your ISP, your reverse zone will not work.

Reverse DNS is mostly used by humans for such things as tracking where a web-site visitor came from, or where an e-mail message originated etc.  
It is typically not as critical in as forward DNS - visitors will still reach your web-site just fine without any reverse DNS for your web-server IP or the visitor's IP.

However reverse DNS is important for one particular application.  
Many e-mail servers on the Internet are configured to reject incoming e-mails from any IP address which does not have reverse DNS.  
So if you run your own e-mail server, reverse DNS must exist for the IP address that outgoing e-mail is sent from.  
It does not matter what the reverse DNS record for your IP address points to as long as it is there. If you host multiple domains on one e-mail server, just setup reverse DNS to point to whichever domain name you consider primary.  
(e-mail servers checking for reverse DNS do recognize that it is normal to host many domains on a single IP address and it would be impossible to list all those domains in reverse DNS for the IP).

Special note about AOL:  
It appears that AOL has recently restricted this even further:  
They also require that reverse DNS points to a "fully qualified domain name" (we assume they mean a name with 3 or more segments, such as "mail.jhsoft.com"), and that this name does not contain the segments "in-addr.arpa" and is not just an IP address.  
If you want to be able to send e-mail to AOL users, the reverse DNS record for your e-mail server IP address must adhere to this as well.  
For details, please see [http://postmaster.aol.com/Postmaster.Errors.php#whatisrdns](http://postmaster.aol.com/Postmaster.Errors.php#whatisrdns)

