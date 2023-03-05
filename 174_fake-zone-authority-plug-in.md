---
title: Fake Zone Authority plug-in
category: 8
frontpage: false
comments: true
refs: 110
created-utc: 2019-01-01
modified-utc: 2020-01-07
---
<p>This plug-in allows domain names to pass common tests performed by domain name registrars and similar without having to setup an actual zone for each domain name.</p>
This can be useful for example if you have a lot of domain names that are either served by other plug-ins or are inactive.<br />
<br />
Specifically, this plug-in provides synthesized SOA- and NS-records indicating that this DNS server is authoritative for whatever name that is requested. Optionally the plug-in will also respond to requests for other record types with a &quot;NO DATA&quot; response (a standard DNS response indicating that no records exist for the request name and type).<br />
<br />
On the &quot;Plug-In Settings&quot; tab, specify the following settings (explained below the image):<br />
<br />
<img src="img/174/1.png" /><br />
 
<ul>
	<li><strong>DNS server names (FQDN)</strong><br />
	Enter the DNS server host names that should be returned in SOA- and NS-records.<br />
	SOA-records will only include the first DNS server name, which must be the primary DNS server.<br />
	Responses to requests for NS-record will include one NS-record for each server name listed.<br />
	 </li>
	<li><strong>E-mail address of the person responsible for zone</strong><br />
	Enter the e-mail address to be returned in SOA-records.<br />
	 </li>
	<li><strong>Additional SOA-record settings</strong><br />
	Click this button to specify additional SOA-record settings in the following dialog.<br />
	Note that these settings are not really going to be used for anything, but some registrars might complain if they are not setup according to their liking. The default settings should satisfy most such tests.<br />
	<img src="img/174/2.png"  /> <br />
	 </li>
	<li><strong>DNS Record TTL (Time To Live)</strong><br />
	How long the DNS records served may be cached by other DNS servers / caches.<br />
	 </li>
	<li><strong>Send &quot;NO DATA&quot; response for record types other than SOA and NS</strong><br />
	Provide a standard DNS response indicating that no records exist for the request name and type.<br />
	Note that if this option is not checked, the plug-in provides no response to requests for record types other than SOA and NS.</li>
</ul>

<p>WARNING: By default, this plug-in responds to all DNS requests. If you only want it to respond for specific names or want to specify exceptions, you can limit which DNS requests are processed using the settings in the &quot;DNS Requests&quot; tab.</p>