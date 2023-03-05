---
title: Blocking DNS requests from specific countries
category: 8
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<div>This is an example of how you might combine the functionality of two different plug-ins to achieve something else.<br />
<br />
Using the <a href="https://simpledns.plus/plugin-geodns">GeoDNS plug-in</a> and the <a href="https://simpledns.plus/plugin-ignorereq">Ignore DNS request plug-in</a> it is possible to block (ignore) DNS requests from specified countries.<br />
<br />
First&nbsp;download the GeoDNS plug-in and unzip this to the plug-ins folder, and download and unzip the ip-to-country database file (see <a href="https://simpledns.plus/plugin-geodns">this article</a>).<br />
The Ignore DNS request plug-in comes with Simple DNS Plus, so you don't need to prepare anything for this.<br />
<br />
Then, in the Simple DNS Plus Options dialog, Plug-Ins section, select the &quot;GeoDNS (IP)&quot; component and click the &quot;Create New Instance...&quot; button:<br />
<br />
<img src="img/6/1.png" /><br />
<br />
In the Plug-In Instance dialog, select the &quot;Plug-In Settings&quot; tab, and something in the &quot;Host name&quot; field (doesn't matter what), specify the location of the un-zipped IP-to-country data file, and enter some IP address in the &quot;Default server IP address&quot; field (doesn't matter what):<br />
<br />
<img src="img/6/2.png" /><br />
<br />
In the &quot;DNS Requests&quot; tab,&nbsp;under &quot;Process DNS requests&quot; select &quot;Never&quot;.<br />
This prevents this GeoDNS plug-in from processing any DNS requests directly.<br />
Click the &quot;OK&quot; button to save the plug-in configuration:<br />
<br />
<img src="img/6/3.png" /><br />
<br />
Back in the Options dialog, select the &quot;Ignore DNS Request&quot; component and click the &quot;Create New Instance...&quot; button:<br />
<br />
<img src="img/6/4.png" /><br />
<br />
In the Plug-In Instance dialog, select the &quot;DNS Requests&quot; tab,&nbsp;under &quot;Process DNS requests&quot; select &quot;Only when...&quot;, select the first/only entry in the list, click the &quot;Edit...&quot; button, select &quot;One or more of the following are true&quot; and click the &quot;OK&quot; button:<br />
<br />
<img src="img/6/5.png" /><br />
<br />
Click the &quot;Add&quot; button, then &quot;Rule from plug-in&quot;, then &quot;GeoDNS (IP)1&quot;, then &quot;Request originates from country...&quot;:<br />
<br />
<img src="img/6/6.png" /><br />
<br />
Enter the 2 letter ISO code for the country that you wish to block requests from (for example &quot;NL&quot; for the Netherlands):<br />
<br />
<img src="img/6/7.png" /><br />
<br />
Add another entry for each country that you wish to block the same way.<br />
When done, click the &quot;OK&quot; button to save the plug-in configuration:<br />
<br />
<img src="img/6/8.png" /><br />
<br />
Back in the Options dialog you should now have an instance of both the GeoDNS (IP) plug-in and the Ignore DNS Request plug-in listed.<br />
Click the &quot;OK&quot; button to save:<br />
<br />
<img src="img/6/9.png" /><br />
<br />
Now all DNS requests originating from the specified countries will be ignored.
</div>