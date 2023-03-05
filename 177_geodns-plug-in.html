---
title: GeoDNS plug-in
category: 8
frontpage: false
comments: true
refs: 110
created-utc: 2019-01-01
modified-utc: 2021-10-28
---
<p>This plug-in provides a different DNS response depending on what country the DNS request originates from.<br />
This can be used to direct Internet traffic (web, FTP, streaming media, etc.) to a server geographically closer to the end-user, or with contents specific for a geographical area.<br />
Note that this is based on the IP address of the resolving DNS server sending the DNS request, which could be in a different country than end-user. However most end-users will typically be using a DNS server in their own country.</p>

<p>To determine the sender's country, the plug-in is designed to use the free and daily updated IP-to-Country database from <a href="http://software77.net/geo-ip/" target="_blank">http://software77.net/geo-ip/</a><br />
Countries are grouped into &quot;regions&quot; for each of which a unique server IP address/alias can be defined.<br />
The plug-in is pre-configured with a default set of 10 regions (North America, Middle East, etc.) based on <a href="https://www.cia.gov/the-world-factbook/" target="_blank">CIA's World Factbook</a>, but you can configure this in any way that you prefer.</p>

<p>There are two variants of this plug-in - &quot;IP&quot; and &quot;CNAME&quot; - both included in the same .dll file.<br />
The &quot;IP&quot; variant responds with a single server IP address (A-record). We recommend using this when you only have a single server (or multiple servers in a cluster behind a single IP address) serving each region.<br />
The &quot;CNAME&quot; variant responds with a server name alias (CNAME-record). The host name pointed to by this CNAME-record may represent multiple IP addresses (multiple A-records) defined elsewhere - for example a local or remote DNS zone or by another plug-in. This can be used when you have multiple servers on multiple IP addresses for each region -typically using round robin load distribution.<br />
Note that the &quot;CNAME&quot; plug-in variant requires an &quot;unlimited zones&quot; license for Simple DNS Plus.</p>

<p>On the &quot;Plug-In Settings&quot; tab, enter the following settings (explained below the image):</p>

<p><img src="img/177/1.png"  /></p>

<ul>
	<li><strong>Host name</strong><br />
	Enter the host name that you want to provide GeoDNS data for. For example &quot;www.example.com&quot;.<br />
	IMPORTANT: For the &quot;CNAME&quot; plug-in variant, always use a sub-name (like a &quot;www.&quot; prefixed name) for which no other DNS records exist. Never use a zone name (such as &quot;example.com&quot;) because the CNAME-record would conflict with the zone's SOA- and NS-records and cause various problems.<br />
	If you want to allow end-users to enter your web-site address without the www prefix, you should point (using an A-record in the zone) the name without the prefix to a default web-server which redirects (via HTTP header) to the www version of the name - this is exactly what Google.com does.<br />
	 </li>
	<li><strong>IP-to-Country data file</strong><br />
	Specify the data file to use.<br />
	Click the &quot;...&quot; button to browse the local file system and find the file.<br />
	Click the &quot;Test&quot; button to get a count of IP address ranges and countries in the file, and to look up IP addresses in it.<br />
	 </li>
	<li><strong>Automatically re-load data file when it is updated</strong><br />
	When checked, the plug-in will monitor the data file for updates.<br />
	 </li>
	<li><strong>Default server IP address / alias</strong><br />
	The server IP address / alias to serve if the country/region is not found or does not have a specific server IP address / alias defined.<br />
	 </li>
	<li><strong>DNS record TTL (Time To Live)</strong><br />
	How long the DNS record served may be cached by other DNS servers / caches.<br />
	 </li>
	<li><strong>Edit Regions / Servers...</strong><br />
	Click this button to open the Regions dialog where you can configure regions and map these to server IP addresses/aliases:<br />
	<br />
	<img src="img/177/2.png"  /><br />
	<br />
	<img src="img/177/3.png" /><br />
	 </li>
	<li><strong>Edit Countries / Regions...</strong><br />
	Click this button to open the Countries dialog where you can configure countries and map these to regions:<br />
	<br />
	<img src="img/177/4.png" /><br />
	<br />
	<img src="img/177/5.png"  /></li>
</ul>

<p>The GeoDNS plug-in can also be used as a source when setting up DNS request rules for other plug-ins:</p>

<p><img src="img/177/6.png" /></p>

<p><img src="img/177/7.png"  /></p>

<p>For an example of using this for blocking DNS requests from specific countries, see <a href="https://simpledns.plus/kb/6">KB6</a>.</p>
