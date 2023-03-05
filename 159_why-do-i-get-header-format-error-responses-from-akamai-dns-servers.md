---
category: 14
frontpage: false
comments: true
refs: 95
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# Why do I get "Header: Format Error" responses from Akamai DNS servers?

By default Simple DNS Plus v. 5.0 uses a relatively new DNS feature called "EDNS0", which enables larger UDP network packets for DNS requests and responses as well as other enhancements to the DNS protocol.  
This can be enabled/disabled and configured in the Options dialog / DNS / Miscellaneous section.

The majority of Internet DNS servers today either fully support EDNS0 or they simply ignore the EDNS0 part of EDNS0 requests and process these requests like any other DNS requests.  
Previous versions of Simple DNS Plus do the later.

However a few Internet DNS servers, including those currently used by Akamai, will respond with "Format Error" to all EDNS0 request (Akamai is a DNS service provider used by Yahoo! and several other large web-sites).

When Simple DNS Plus v. 5.0 receives such a "Format Error" in response to an EDNS0 request, it will simply re-send the request without EDNS0 (a standard RFC behaviour used by all EDNS0 enabled DNS servers).

As you can see in the following log snapshot from Simple DNS Plus v. 5.0, it first sends a DNS request to the Akamai DNS server (use3.akadns.net) and gets a "Format Error" response. Then it sends the DNS request again (without EDNS0) and gets a good (no error) response:

<pre></pre>
To make it a bit clearer to see what is happening, you can enable logging of EDNS0 details (see Options dialog / Logging / Log Details section). Then it looks like this:

<pre></pre>
While this does result in an extra round-trip when resolving certain domain names (such as yahoo.com), we recommend leaving EDNS0 enabled because this is generally more efficient both in resolving and serving DNS requests.

We are sure that Akamai will fix their DNS servers eventually as this is only causing unnecessary DNS traffic for themselves and delays for users of their customers' web-sites.

