---
title: How do I get reverse DNS for my IP addresses delegated to my own DNS server?
category: 9
frontpage: false
comments: true
refs: 153,77
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<p>Reverse DNS is controlled by whoever "owns" the IP address.<br />
The owner can choose to sub-delegate reverse DNS for a range of IP range to someone else, who in turn can sub-delegate parts of that range further, etc.</p>
<p>
<a href="http://www.iana.org" target="_blank">IANA</a> ultimately "owns" all Internet IP addresses.<br />
IANA delegates these IP addresses to 5 regional registires; <a href="http://www.afrinic.net/" target="_blank">AfriNIC</a> (Africa), <a href="http://www.apnic.net/" target="_blank">APNIC</a> (Asia/Pacific), <a href="http://www.arin.net/" target="_blank">ARIN</a> (North America), <a href="http://lacnic.net/en/index.html" target="_blank">LACNIC</a> (Latin America), and <a href="http://www.ripe.net/" target="_blank">RIPE</a> (Europe, Middle East, Central Asia).<br />
And these registries delegate their IP addresses to backbones providers and ISPs, who delegate to end-users.</p>
<p>So as an end-user, if you want control of reverse DNS for your IP addresses, you need to contact whoever provides you with these IP addresses, and ask them to do a reverse DNS sub-delegation to your DNS servers.</p>
<p>For example if your IP range is 1.2.3.0 to 1.2.3.255, then the reverse DNS sub-delegation is typically done using a DNS zone name "3.2.1.in-addr.arpa".<br />
If you have less than a class C (256 IP addresses), then the reverse DNS sub-delegation uses a slightly different format called "Classless IN-ADDR.ARPA delegation". The exact zone name format used for this vary for each ISP, so it is very important that you setup your reverse zone on your DNS server with the zone name provided by the ISP.<br />
For more on this, please see <a href="http://www.rfc-editor.org/rfc/rfc2317.txt">RFC2317</a></p>
<p>If you only have one or a few IP addresses, most ISPs will not do reverse DNS sub-delegation for this at all.<br />
However in most cases, they will point reverse DNS for your IP addresses to whatever domain name that you want, at least if you are a business customer.</p>