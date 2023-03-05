---
title: Why do I get "Header: Format Error" responses from Akamai DNS servers?
category: 14
frontpage: false
comments: true
refs: 95
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<p>By default Simple DNS Plus v. 5.0 uses a relatively new DNS feature called "EDNS0", which enables larger UDP network packets for DNS requests and responses as well as other enhancements to the DNS protocol.<br />
This can be enabled/disabled and configured in the Options dialog / DNS / Miscellaneous section.</p>
<p>The majority of Internet DNS servers today either fully support EDNS0 or they simply ignore the EDNS0 part of EDNS0 requests and process these requests like any other DNS requests.<br />
Previous versions of Simple DNS Plus do the later.</p>
<p>However a few Internet DNS servers, including those currently used by Akamai, will respond with "Format Error" to all EDNS0 request (Akamai is a DNS service provider used by Yahoo! and several other large web-sites).</p>
<p>When Simple DNS Plus v. 5.0 receives such a "Format Error" in response to an EDNS0 request, it will simply re-send the request without EDNS0 (a standard RFC behaviour used by all EDNS0 enabled DNS servers).</p>
<p>As you can see in the following log snapshot from Simple DNS Plus v. 5.0, it first sends a DNS request to the Akamai DNS server (use3.akadns.net) and gets a "Format Error" response. Then it sends the DNS request again (without EDNS0) and gets a good (no error) response: </p>

<pre>13:49:01   Request from 127.0.0.1 for A-record for www.yahoo.com
...
13:49:02   Sending request to 204.2.178.133 (use3.<span class="MAGIC ">akadns.net</span>) for A-record for www.yahoo-ht3.akadns.net
13:49:02   Reply from 204.2.178.133:
13:49:02   <span class="MAGIC ">-&gt; Header: Format Error</span>
13:49:02   Sending request to 204.2.178.133 (use3.akadns.net) for A-record for www.yahoo-ht3.akadns.net
13:49:02   Reply from 204.2.178.133 about A-record for www.yahoo-ht3.akadns.net:
13:49:02   -&gt; Answer: A-record for www.yahoo-ht3.akadns.net = 87.248.113.14
13:49:02   Sending reply to 127.0.0.1 about A-record for www.yahoo.com:
13:49:02   -&gt; Answer: CNAME-record for www.yahoo.com = www.yahoo-ht3.akadns.net
13:49:02   -&gt; Answer: A-record for www.yahoo-ht3.akadns.net = 87.248.113.14</pre>

<p>To make it a bit clearer to see what is happening, you can enable logging of EDNS0 details (see Options dialog / Logging / Log Details section). Then it looks like this:</p>

<pre>13:49:01   Request from 127.0.0.1 for A-record for www.yahoo.com
...
13:49:02   Sending request to 204.2.178.133 (use3.akadns.net) for A-record for www.yahoo-ht3.akadns.net
13:49:02   <span class="MAGIC ">-&gt; EDNS0: UDP payload size = 1280 bytes</span>
13:49:02   Reply from 204.2.178.133:
13:49:02   -&gt; Header: Format Error
13:49:02   Sending request to 204.2.178.133 (use3.akadns.net) for A-record for www.yahoo-ht3.akadns.net
13:49:02   Reply from 204.2.178.133 about A-record for www.yahoo-ht3.akadns.net:
13:49:02   -&gt; Answer: A-record for www.yahoo-ht3.akadns.net = 87.248.113.14
13:49:02   Sending reply to 127.0.0.1 about A-record for www.yahoo.com:
13:49:02   -&gt; Answer: CNAME-record for www.yahoo.com = www.yahoo-ht3.akadns.net
13:49:02   -&gt; Answer: A-record for www.yahoo-ht3.akadns.net = 87.248.113.14</pre>

<p>While this does result in an extra round-trip when resolving certain domain names (such as yahoo.com), we recommend leaving EDNS0 enabled because this is generally more efficient both in resolving and serving DNS requests.</p>
<p>We are sure that Akamai will fix their DNS servers eventually as this is only causing unnecessary DNS traffic for themselves and delays for users of their customers' web-sites.</p>