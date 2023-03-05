---
title: Clone Response plug-in
category: 8
frontpage: false
comments: true
refs: 110
created-utc: 2019-01-01
modified-utc: 2021-10-28
---
<p>This plug-in provides DNS responses by cloning the DNS records from a response to requests for another specified domain name.</p>

<p>This is an easy way to host many domain names that have the exact same records (except for their zone names).</p>

<p>On the &quot;Plug-In Settings&quot; tab, enter the following settings (explained below the image):</p>

<p><img src="img/168/1.png" /></p>

<ul>
	<li><strong>Clone from zone</strong><br />
	The zone name to query for a response to be cloned.</li>
	<li><strong>Public suffix list file</strong><br />
	File containing list of domain name suffixes under which domain names can be registered on the Internet.<br />
	The data from this file is used to determine how many labels (segment between dots) of a requested domain name represents the zone name.<br />
	You can download a file (used by Firefox and other browsers) from <a href="http://publicsuffix.org">http://publicsuffix.org</a> or create your own using the format described on the same web-site.<br />
	Note that if you edit the file manually, it must be saved in UTF-8 encoding.</li>
</ul>

<p>When this plug-in processes a DNS request, it first determines what zone name the requested name belongs to.<br />
This will be the longest match in the public suffix list file + one more label of the requested name.<br />
Then a new DNS request is generated for the requested domain name less the zone name + the &quot;clone from zone&quot; name.<br />
This new request is then resolved (from local zones, other plug-ins, resolved from Internet, etc.) and the resulting response is cloned - replacing all instances of the &quot;clone from zone&quot; name with the zone name part of the requested name.</p>

<p>For example, say the configured &quot;clone from zone&quot; name is &quot;example.com&quot; and the plug-in receives a DNS request for &quot;host5.simpledns.co.uk&quot;.<br />
Assuming the longest match for &quot;host5.simpledns.co.uk&quot; in the public suffix list file is &quot;co.uk&quot;, then the zone name is determined to be &quot;simpledns.co.uk&quot;.<br />
A new request is generated for &quot;host5.example.com&quot; (&quot;host5.simpledns.co.uk&quot; less &quot;simpledns.co.uk&quot; + &quot;example.com&quot;).<br />
When this new request is resolved, all instances of &quot;example.com&quot; in the response are replaced with &quot;simpledns.co.uk&quot; so that this matches the original request.</p>

<p>IMPORTANT: By default this plug-in clones DNS responses for ALL DNS requests, so (unless this is what you want) it is important that it be limited in scope using the &quot;DNS Requests&quot; tab.</p>
