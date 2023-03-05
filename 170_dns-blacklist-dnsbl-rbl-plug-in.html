---
title: DNS Blacklist (DNSBL / RBL) plug-in
category: 8
frontpage: false
comments: true
refs: 110
created-utc: 2019-01-01
modified-utc: 2021-10-28
---
<p>This plug-in is used to host a DNS blacklist (a.k.a. &quot;DNSBL&quot; / &quot;RBL&quot;).</p>

<p>DNS blacklists are typically used with e-mail servers to filter spam and other unwanted e-mails.<br />
Many e-mail servers can be configured to check if a sender's IP address is listed in a specified DNS blacklist, and based on this decide to reject or flag the incoming e-mail message.<br />
Every time such an e-mail server receives an inbound e-mail message, it does a DNS lookup against one or more DNS blacklists by reversing the segments of the sender's IP address and adding the blacklist domain name.<br />
For example if the sender's IP address is 1.2.3.4 and the blacklist domain name is &quot;dnsbl.example.com&quot;,  it will do a DNS lookup for &quot;4.3.2.1.dnsbl.example.com&quot;.<br />
If the DNS lookup returns an value (typically the dummy IP address 127.0.0.2), this means that the sender's IP address is on the blacklist, and the e-mail server can take appropriate action according to its configuration.<br />
Many blacklists also contain text strings associated with each blacklist entry - typically describing why an IP address is listed and what to do to get de-listed.<br />
E-mail servers can request this text through a DNS TXT-record lookup and log and/or include this in error messages etc.<br />
For more details on this concept and its history, please see <a href="http://en.wikipedia.org/wiki/dnsbl" target="_blank">this Wikipedia article</a>.</p>

<p>Theoretically a DNS blacklist can be hosted as a normal DNS zone with A-records and TXT-records.<br />
However a DNS blacklist typically contains thousands and often millions of IP addresses, and the standard DNS zone file format and the normal way of storing DNS records in computer memory is just not efficient for this type of data.<br />
This plug-in however is highly optimized for this, and can load a dataset for millions of IP addresses in a fraction of a second using minimal memory, and can query this data extremely efficiently.</p>

<p>You can create your own blacklists with the <a href="https://simpledns.plus/dnsbl-editor">DNS Blacklist Editor</a> tool.<br />
If you receive a lot of e-mails and do a lot of DNS blacklist lookups against other blacklists (for example as an ISP), it may also be more efficient to periodically download the full blacklists and host them yourself with this plug-in.</p>

<p>In the plug-in instance dialog / Plug-In Settings tab you can specify the blacklist domain name, the compiled data file, select if the data file should automatically be re-loaded when updated, and the TTL value for responses:</p>

<p><img src="img/170/1.png" /></p>

<p><b><u>IMPORTANT</u></b>:<br />
The &quot;Compiled data file&quot; is highly optimized proprietary binary file type (&quot;.sdnsbl&quot; file extension) which is only understood by this plug-in. This should NOT be confused with standard text based DNSBL/RBL files.<br />
You compile this file type from a DNSBL/RBL text file using the <a href="https://simpledns.plus/dnsbl-editor">DNS Blacklist Editor</a> tool.<br />
You can compile either from DNS Blacklist Editor's Tools menu, or from the command line (or as part of an automated script) by executing: <code>DNSBLEDIT.EXE &lt;input-file&gt; &lt;output-file&gt;</code><br />
Note: You should always keep a copy of your blacklist data in the standard text based format (RBLDNSD format) for editing. Compiling to the plug-in data file format is a one way process. A compiled data file cannot be opened for editing.</p>

<p><b><u>IMPORTANT</u></b>:<br />
When hosting a DNS blacklist with this plug-in, make sure to also configure a local DNS zone for the blacklist domain name or a parent name. Otherwise Simple DNS Plus will attempt to resolve any DNS request which does not have a match in the blacklist (according to recursion settings etc.).<br />
This local zone also provides a place to configure other records for the blacklist domain name - such as SOA, NS, MX records, perhaps an A-records for a web-site about the blacklist, etc.</p>

