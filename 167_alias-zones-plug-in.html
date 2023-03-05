---
title: Alias Zones plug-in
category: 8
frontpage: false
comments: true
refs: 110
created-utc: 2019-01-01
modified-utc: 2020-01-07
---
<p>This plug-in provides DNS records for one or more "virtual" zones by cloning records from another zone (local or remote).</p>

<p>This is an easy way to host many domain names that have the exact same records (except for their zone names).</p>

<p>On the &quot;Plug-In Settings&quot; tab, enter the following settings (explained below the image):</p>

<p><img src="img/167/1.png" /></p>

<ul>
	<li><strong>Alias zone names</strong><br />
A list of domain names representing the "virtual zones".<br/>
<br/></li>

	<li><strong>Clone from zone</strong><br />
The zone name to query for a response to be cloned. This can be a local zone or a domain hosted elsewhere.<br/>
</li>

</ul>

<p>When this plug-in processes a DNS request, it first checks if the requested name matches, or is a sub-name of, one of the names listed in the "Alias zones names" list - using the longest match.<br />
Then a new DNS request is generated for the requested domain name less the matched alias zone name + the &quot;Clone from zone&quot; name.<br />
This new request is then resolved (from local zones, other plug-ins, resolved from Internet, etc.) and the resulting response is cloned - replacing all instances of the &quot;Clone from zone&quot; name with the alias zone part of the requested name.</p>

<p>For example, say the plug-in is configured as in the image above (&quot;Alias zones names&quot; is &quot;example.net&quot; / &quot;example.org&quot; and the &quot;Clone from zone&quot; name is &quot;example.com&quot;), and the plug-in receives a DNS request for &quot;host5.example.net&quot;.<br />
A new request is then generated for &quot;host5.example.com&quot; (&quot;host5.example.net&quot; less &quot;example.net&quot; + &quot;example.com&quot;).<br />
When this new request is resolved, all instances of &quot;example.com&quot; in the response are replaced with &quot;example.net&quot; so that this matches the original request.</p>