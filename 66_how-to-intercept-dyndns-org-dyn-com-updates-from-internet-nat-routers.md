---
title: How to intercept dyndns.org (Dyn.com) updates from Internet/NAT routers
category: 4
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<div>Many Internet/NAT routers (and other devices) have a built-in function to update a dyndns service&nbsp;(a.k.a. &quot;ddns&quot;) whenever the public IP address changes. This is often hard-coded to use a few specific dyndns providers / update formats, and dyndns.org (Dyn.com)&nbsp;is typically one of these.</div>

<div>&nbsp;</div>

<div>With Simple DNS Plus (on a public static IP address), you can run your own dyndns service and pretend&nbsp;to be&nbsp;dyndns.org (Dyn.com) -&nbsp;and have such routers update it.</div>

<div>&nbsp;</div>

<div>Note that this requires Simple DNS Plus v. 5.2 or later with the&nbsp;<a href="https://simpledns.plus/plugin-dyndns" target="_blank">DynDNS Service&nbsp;plug-in</a> v. 5.2.30 (or later). This plug-in version comes with Simple DNS Plus v. 6.0 build 119 and later. For earlier Simple DNS Plus versions/builds, it&nbsp;can be downloaded from&nbsp;<a href="https://github.com/jhsoftware/sdns-DynDns/releases" target="_blank">https://github.com/jhsoftware/sdns-DynDns/releases</a></div>

<div>&nbsp;</div>

<div>With many routers, the dyndns.org (Dyn.com) update URL host name (&quot;members.dyndns.org&quot;)&nbsp;is hard-coded, and so you need to &quot;fake&quot; the IP address&nbsp;for this in order to intercept update requests from the router. You can do this by configuring the router to use your own&nbsp;DNS server, and then have your DNS server point &quot;members.dyndns.org&quot; to your&nbsp;own server IP address - for example using the &quot;Fixed IP Address&quot; plug-in as described below.</div>

<div>If your router allows you to specify the IP address of the dyndns server, then you should do so instead and skip the step below about configuring the router's DNS IP addresses.</div>

<div>&nbsp;</div>

<div>For the walk-through below, we have setup Simple DNS Plus on a computer&nbsp;with static IP address&nbsp;40.69.210.0 and, in a different location,&nbsp;we have an ASUS RT-N56U&nbsp;Internet router in with&nbsp;a dynamic public IP address (80.62.117.233 at the time of this writing).</div>

<div>On the firewall on / in front of the Simple DNS Plus computer, we have allowed UDP and TCP to port 53 (DNS requests) and TCP to port 80 (HTTP requests).</div>

<div>&nbsp;</div>

<div>On the DNS server computer, in the main window of Simple DNS Plus, click the &quot;Plug-ins&quot; button:</div>

<div>&nbsp;</div>

<div><img height="150" src="img/66/1.png" width="590" /></div>

<div>&nbsp;</div>

<div>In the &quot;Plug-in instances&quot; dialog, click the &quot;Add&quot; button:</div>

<div>&nbsp;</div>

<div><img height="119" src="img/66/2.png" width="410" /></div>

<div>&nbsp;</div>

<div>In the &quot;Add new Plug-In instance&quot; dialog, select &quot;Fixed IP Address&quot; and click the &quot;Create Instance...&quot; button:</div>

<div>&nbsp;</div>

<div><img height="374" src="img/66/3.png" width="496" /></div>

<div>&nbsp;</div>

<div>In the &quot;Fixed IP Address Plug-In Instance&quot; dialog, select &quot;Plug-in Settings&quot; tab, enter the public IP address of the the computer that Simple DNS Plus is running on:</div>

<div>&nbsp;</div>

<div><img height="365" src="img/66/4.png" width="418" /></div>

<div>&nbsp;</div>

<div>In the &quot;DNS Requests&quot; tab, under &quot;Process DNS requests&quot; select &quot;Only when...&quot;, then add a rule for&nbsp;&quot;Requested domain name&nbsp;is:&nbsp;members.dyndns.org&quot; (click the &quot;Add&quot; button and select &quot;Requested domain name&quot;, then &quot;is...&quot;, then enter &quot;members.dyndns.org&quot;), and click the &quot;OK&quot; button:</div>

<div>&nbsp;</div>

<div><img height="365" src="img/66/5.png" width="418" /></div>

<div>&nbsp;</div>

<div>Back in the &quot;Plug-In instances&quot; dialog, click the &quot;Add...&quot; button again:</div>

<div>&nbsp;</div>

<div><img height="121" src="img/66/6.png" width="410" /></div>

<div>&nbsp;</div>

<div>In the &quot;Add new Plug-In instance&quot; dialog, select &quot;DynDNS Service&quot; and click the &quot;Create Instance...&quot; button:</div>

<div>&nbsp;</div>

<div><img height="374" src="img/66/7.png" width="496" /></div>

<div>&nbsp;</div>

<div>In the &quot;DynDNS Service Plug-In Instance&quot; dialog, in the &quot;General&quot; tab, check &quot;Perform DNS recursion for IP addresses listed by this plug-in&quot;:</div>

<div>&nbsp;</div>

<div><img height="365" src="img/66/8.png" width="418" /></div>

<div>&nbsp;</div>

<div>In the &quot;Plug-In Settings&quot; tab, enter the host name suffix you want to use, and click the &quot;Add...&quot; button:</div>

<div>&nbsp;</div>

<div><img height="365" src="img/66/9.png" width="418" /></div>

<div>&nbsp;</div>

<div>In the &quot;DynDNS Service User&quot; dialog, enter a user-ID and a password (remember these for the router configuration) and click the &quot;OK&quot; button:</div>

<div>&nbsp;</div>

<div><img height="463" src="img/66/10.png" width="316" /></div>

<div>&nbsp;</div>

<div>Back in the &quot;DynDNS Service Plug-In Instance&quot; dialog, click the &quot;Update methods...&quot; button:</div>

<div>&nbsp;</div>

<div><img height="365" src="img/66/11.png" width="418" /></div>

<div>&nbsp;</div>

<div>In the &quot;DynDNS client update methods&quot; dialog, check &quot;HTTP - Dyn.com URL format (Basic HTTP auth.), and click the &quot;OK&quot; button:</div>

<div>&nbsp;</div>

<div><img height="395" src="img/66/12.png" width="335" /></div>

<div>&nbsp;</div>

<div>Click the &quot;OK&quot; buttons in the previous dialogs. Back in the main window, in the &quot;View&quot; menu, select the DynDNS Service plug-in to open a new tab for this:</div>

<div>&nbsp;</div>

<div><img height="224" src="img/66/13.png" width="668" /></div>

<div>&nbsp;</div>

<div>At the client site, configure your router to use the public IP address of the computer running Simple DNS Plus for DNS.<br />
In our &quot;ASUS RT-N56U&quot; router, this is done in the &quot;WAN&quot; section, under the &quot;Internet Connection&quot; tab, under &quot;WAN DNS Setting&quot; as follows:</div>

<div>&nbsp;</div>

<div><img height="628" src="img/66/14.png" width="650" /></div>

<div>&nbsp;</div>

<div>
<div>Configure your router to use the dyndns.org (Dyn.com) service using the user-ID and password setup in Simple DNS Plus above.<br />
In our &quot;ASUS RT-N56U&quot; router, this is done in the &quot;WAN&quot; section, under the &quot;DDNS&quot; tab.</div>

<div>Note that the &quot;Host Name&quot; setting / parameter is not used&nbsp;by the Simple DNS Plus plug-in and can be set to any value (such as &quot;dummy&quot;):</div>
</div>

<div>&nbsp;</div>

<div><img height="525" src="img/66/15.png" width="650" /></div>

<div>&nbsp;</div>

<div>If everything is configured correctly, you should now see a DNS request for &quot;members.dyndns.org&quot; followed by an DynDNS service update message, and the updated DynDNS user status / IP address in Simple DNS Plus:</div>

<div>&nbsp;</div>

<div><img height="409" src="img/66/16.png" width="682" /></div>

<div>&nbsp;</div>

<div>&nbsp;</div>

<div>Please note:</div>

<div>For above to work, the router must use the dyndns.org (Dyn.com)&nbsp;&quot;Legacy Authentication URL&quot;.</div>

<div>All routers that we have tested with so far do this.</div>

<div>However in addition to the &quot;Legacy Authentication URL&quot;, dyndns.org (Dyn.com) also provides another&nbsp;(newer) update URL which uses SSL (https://...). The specification for both URLs is available&nbsp;at&nbsp;<a href="https://help.dyn.com/remote-access-api/perform-update/" target="_blank">https://help.dyn.com/remote-access-api/perform-update/</a>&nbsp;.</div>

<div>So some routers may use the newer SSL version. It would not be possible to intercept such requests as this&nbsp;would require the private key of the SSL certificate for &quot;members.dyndns.org&quot;.</div>