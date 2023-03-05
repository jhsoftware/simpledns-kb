---
title: Web-site domain filtering using the "Fixed IP Address" plug-in
category: 8
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<div>This article describes a simple way to block access to a few web-sites (and make an exception for the manager's PC) using the &quot;Fixed IP Address&quot; plug-in.<br />
To block a longer list of sites we recommend using the more advanced <a href="https://simpledns.plus/plugin-domainbl">Domain Blacklist plug-in</a>.<br />
<br />
In the Simple DNS Plus main window,click the &quot;Options&quot; button:<br />
<br />
<img src="img/149/1.png" /><br />
<br />
In the &quot;Options&quot; dialog &quot;Plug-ins&quot; section under &quot;Available plug-in components&quot;, select &quot;Fixed IP Address&quot; and click the &quot;Create New Instance&quot; button:<br />
<br />
<img src="img/149/2.png" /><br />
 <br />
In the &quot;Fixed IP Address Plug-In Instancd&quot; dialog, select the &quot;Plug-in Settings&quot; tab, and enter the IP address(es) of the web-server that you want to redirect requests for blocked web-sites to - or enter a dummy address to have blocked requests fail:<br />
<br />
<img src="img/149/3.png" /> <br />
<br />
Under the &quot;DNS Reqests&quot; tab, in the &quot;Process DNS requests&quot; drop-down select &quot;Only when...&quot;. Click the &quot;Add&quot; button, select &quot;Requested domain name&quot; and &quot;is in list...&quot;:<br />
<br />
<img src="img/149/4.png" /><br />
<br />
In the &quot;DNS reqest access rule&quot; dialog, click the &quot;Add...&quot; button:<br />
 <br />
<img src="img/149/5.png" /> <br />
<br />
Enter a web-site domain name that you want to block and click the &quot;OK&quot; button.<br />
Repeat this for each domain name that you wish to block.<br />
<br />
<img src="img/149/6.png" /> <br />
<br />
Next, if you want to exclude some client IP addresses (like the manager's PC) from the block, back in the &quot;Fixed IP Address Plug-In Instance&quot; dialog, click the &quot;Add&quot; button, select &quot;Sender's IP address&quot; and &quot;is in list...&quot;:<br />
<br />
<img src="img/149/7.png" /><br />
<br />
In the &quot;DNS requst access rule&quot; dialog add an IP address for each client PC IP address that you don't want to block, make sure to check the &quot;Not (reverse result&quot; checkbox:<br />
 <br />
<img src="img/149/8.png" /> <br />
<br />
Back in the &quot;Fixed IP Address Plug-In Instance&quot; dialog, you should now have two &quot;rules&quot; - one to list the blocked domain names and one to list the IP addresses which should not be blocked:<br />
<br />
<img src="img/149/9.png" /><br />
<br />
Click the &quot;OK&quot; button here and in the &quot;Options&quot; dialog to save.
</div>