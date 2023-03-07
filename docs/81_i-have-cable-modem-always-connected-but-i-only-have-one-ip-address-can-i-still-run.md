---
category: 15
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# I have a cable modem (always connected), but I only have one IP address. Can I still run a DNS server for my own domain name?

Many registrars require at least two DNS servers per domain name.  
It is sometimes possible to specify the same IP address for both servers, but this really defeats the purpose - redundancy.  
A better solution would be to have someone else run your secondary DNS server.  
You will still be in full control as you are running the primary DNS server, and the secondary server will simply be updated through notifications and zone transfers each time you change something.  
Should the secondary server be down, DNS requests will still be resolved correctly by the primary - and vice versa.

For example you can use [https://ns2service.net](https://ns2service.net/){target=_blank}

