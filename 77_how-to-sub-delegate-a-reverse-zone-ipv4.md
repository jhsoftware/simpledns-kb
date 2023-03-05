---
title: How to sub-delegate a reverse zone (IPv4)
category: 9
frontpage: false
comments: true
vgroup: 6
vname: IPv4
vsort: 1
refs: 153,53,64
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<p>If for example you are an ISP&nbsp;providing Internet connections&nbsp;to your customers, you can sub-delegate reverse DNS for the IP addresses&nbsp;that you provide to your customers to the customers' own DNS servers.<br />
This makes it possible for your customers to control their own reverse DNS without contacting you every time they need this updated.<br />
Typically you would only do this for customers with multiple static&nbsp;IP addresses.<br />
For customers with only one IP address or&nbsp;dynamic IP addresses, it usually&nbsp;makes more sense to host the reverse DNS records on your own DNS server.</p>
<p>Before you can sub-delegate reverse DNS to others, reverse DNS for your IP range(s) must of course first be delegated to your DNS servers. For more on this see <a href="/kb/53/how-do-i-get-reverse-dns-for-my-ip-addresses-delegated-to-my-own-dns-server">this article</a>.</p>
<p><strong><span style="text-decoration: underline;">Sub-delegate more than a class C (&gt; 256 IP addresses)</span> </strong></p>
<p>If you want to sub-delegate reverse DNS for an IP address range larger than a class C (&gt; 256 IP addresses)&nbsp;then you must break this into multiple class C sub-delegations (see below).</p>
<p><strong><span style="text-decoration: underline;">Sub-delegate full class C&nbsp;(256 IP addresses) from a&nbsp;class&nbsp;B or larger&nbsp;(65536+ IP addresses)</span> </strong></p>
<p>If you have at least a class B (65536 IP addresses)&nbsp;and provide a class C&nbsp;(256 IP addresses) from this to a customer, the reverse DNS&nbsp;sub-delegation is&nbsp;done simply by adding NS-records for the customer's DNS servers.<br />
For example say you&nbsp;have&nbsp;IP addresses&nbsp;11.22.0.0/16 and you want to sub-delegate reverse DNS for 11.22.33.0/24&nbsp;to your customer's DNS servers.<br />
Then in your "22.11.in-addr.arpa" zone, you would add an&nbsp;NS-record for "33.22.11.in-addr.arpa"&nbsp;for each of your customer's DNS servers like this:<br />
<br />
NS: 33.22.11.in-addr.arpa -&gt; ns1.customer.com<br />
NS: 33.22.11.in-addr.arpa -&gt; ns2.customer.com</p>
<p><strong><span style="text-decoration: underline;">Sub-delegate full class C&nbsp;(256 IP addresses) from less than a class B&nbsp;(&lt; 65536 IP addresses)</span> </strong></p>
<p>If you have multiple class Cs (multiple sets of 256 IP addresses) but not&nbsp;a full class B, then the best way to sub-delegate reverse DNS for one of those class Cs is to ask your IP address provider to create/change this delegation on their DNS servers.<br />
Technically you could use "classless IN-ADDR.ARPA delegation" (see below) but this is not recommend for a full class C because the customer will (rightly) expect&nbsp;a standard reverse delegation (as above).</p>
<p><strong><span style="text-decoration: underline;">Sub-delegate less than a class C&nbsp;(&lt; 256 IP addresses) from a&nbsp;class C or larger&nbsp;(256+ IP addresses)</span> </strong></p>
<p>If you have at least a class C&nbsp;(256 IP addresses), and you want to sub-delegate reverse DNS for only part of a class C to your customer's DNS servers, this is typically done using the "classless IN-ADDR.ARPA delegation" style described in <a href="http://www.rfc-editor.org/rfc/rfc2317.txt">RFC2317</a>.<br />
Technically it is possible to use other sub-delegation naming styles, but we highly recommend that you stick with the RFC2317 style because this is much more likely to work with various tools and programs. For example, the GUI record editor in&nbsp;Simple DNS Plus automatically recognizes the RFC2317 zone naming style as a reverse zone.</p>
<p>For example say you have IP addresses 11.22.33.0/24 (11.22.33.0 to 11.22.33.255) and you want to sub-delegate reverse DNS for 11.22.33.64/30 (11.22.33.64 to 11.22.33.67) to your customer's DNS servers.<br />
Then in your "33.22.11.in-addr.arpa" zone, you would add an NS-record&nbsp;for "64/30.33.22.11.in-addr.arpa" for each of your customers's DNS servers, and&nbsp;a CNAME-record for "XX.33.22.11.in-addr.arpa" pointing to "XX.64/30.33.22.11.in-addr.arpa" for each of the IP addresses in the customer's IP range where XX is the last segment of each IP address like this:<br />
<br />
NS: 64/30.33.22.11.in-addr.arpa -&gt; ns1.customer.com<br />
NS: 64/30.33.22.11.in-addr.arpa -&gt; ns2.customer.com<br />
CNAME: 64.33.22.11.in-addr.arpa -&gt; 64.64/30.33.22.11.in-addr.arpa<br />
CNAME: 65.33.22.11.in-addr.arpa -&gt; 65.64/30.33.22.11.in-addr.arpa<br />
CNAME: 66.33.22.11.in-addr.arpa -&gt; 66.64/30.33.22.11.in-addr.arpa<br />
CNAME: 67.33.22.11.in-addr.arpa -&gt; 67.64/30.33.22.11.in-addr.arpa</p>
<p>Your customer would setup a zone called "64/30.33.22.11.in-addr.arpa" on his DNS&nbsp;server with the following records:<br />
<br />
SOA: 64/30.33.22.11.in-addr.arpa ...<br />
NS: 64/30.33.22.11.in-addr.arpa -&gt; ns1.customer.com<br />
NS: 64/30.33.22.11.in-addr.arpa -&gt; ns2.customer.com<br />
PTR:&nbsp;64.64/30.33.22.11.in-addr.arpa -&gt; [reverse DNS name for IP 11.22.33.64]<br />
PTR:&nbsp;65.64/30.33.22.11.in-addr.arpa -&gt; [reverse DNS name for IP 11.22.33.65]<br />
PTR:&nbsp;66.64/30.33.22.11.in-addr.arpa -&gt; [reverse DNS name for IP 11.22.33.66]<br />
PTR:&nbsp;67.64/30.33.22.11.in-addr.arpa -&gt; [reverse DNS name for IP 11.22.33.67]</p>
<p><strong><span style="text-decoration: underline;">Sub-delegate from less than a class C&nbsp;(&lt; 256 IP addresses)</span> </strong></p>
<p>If you have an IP address range of less than&nbsp;256 IP addresses, then the best way to sub-delegate reverse DNS for part of that range is to ask your IP address provider to create/change this delegation on their DNS servers.<br />
Technically you could create another level of CNAME redirection similar to "classless IN-ADDR.ARPA delegation" (see above) but this is not recommend because the redirection becomes too deep.</p>