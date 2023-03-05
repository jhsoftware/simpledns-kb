---
title: HTTP based dynamic DNS service (DynDNS)
category: 4
frontpage: false
comments: true
refs: 35,40,125,127,173
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<div style="border: 1px solid black; background-color: #ffffc0;">NB: This article was written before we released the <a href="https://simpledns.plus/plugin-dyndns">DynDNS Service plug-in</a>.<br />
The DynDNS Service plug-in makes it much easier to run a HTTP based DynDNS service</div>
<p>You can run your own dynamic DNS service (like <a href="http://www.dyndns.org/" target="_blank">http://www.dyndns.org/</a>) using Simple DNS Plus.</p>
<p>Simple DNS Plus supports TSIG signed dynamic updates directly through the DNS protocol.<br />
This is the most efficient and recommend way to do dynamic updates.<br />
However TSIG signed update are currently only supported by few software clients (see reference articles below).</p>
<p>To enable dynamic updates over HTTP, which is supported by practically all software clients as well as many broadband Internet routers, you need to setup a simple dynamic web-page on your web-server to validate the user name/password, and then update Simple DNS Plus.</p>
<p>A sample web-page (ASP.NET and Classic ASP) doing just this is available for download from here:<br />
<a href="https://simpledns.plus/outbox/dyndns.zip">dyndns.zip (2 KB)</a></p>
<p>The zip file includes 3 files:<br />
- dyndns.asp   (Classic ASP version)<br />
- dyndns.aspx   (ASP.NET 2.0 version)<br />
- ddnsuser.txt    (user list configuration file)</p>
<p>Extract the files into your IIS web-site and make sure ASP or ASP.NET 2.0 is enabled depending on which version you want to use.</p>
<p>Edit the dyndns.asp/aspx file and update the "sdnsIPAddr", "sdnsPort", "sdnsPassword" variables (at the top of the file) to match the settings in your Simple DNS Plus Options dialog / HTTP API section.</p>
<p>The "UserListFile" variable specifies the relative location and file name of the user list file (ddnsuser.txt).<br />
This is a simple text file where each line lists the user-id, password, and host name of a user - separated by semicolons (;). For example:</p>
<p>alex;1234;alex.yourname.com</p>
<p>IMPORTANT: You should move the user list file to a location where it cannot be accessed directly through the web-site (for example the "app_data" directory for ASP.NET) or deny access to it using IIS or file security settings.</p>
<p>Make sure you have setup the parent zone(s) for all user's host names.<br />
For example if a users host name is "alex.yourname.com", you must have a primary zone "yourname.com" setup in Simple DNS Plus.</p>
<p>After updating the user list file, the dynamic DNS service should be ready to use.<br />
The update URL which you can use in dyndns client software, routers, or directly in a browser is:</p>
<p>http://&lt;www.your-domain.com&gt;/dyndns.asp?user=&lt;userid&gt;&amp;pw=&lt;password&gt;&amp;ip=&lt;ip-address&gt;</p>
<p>For example:</p>
<p>http://www.yourname.com/dyndns.asp?user=alex&amp;pw=1234&amp;ip=1.2.3.4</p>
<p>The last "ip" parameter is optional. If no IP address is specified, the web page script will use the IP address that the HTTP request came from.</p>
<p>If you want to integrate this with your existing user database or store user/domains in some other way, you can modify the "LookupUsersHostName" sub-routine in the web-page to fetch this information in whatever way you want.</p>