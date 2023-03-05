---
category: 4
frontpage: false
comments: true
refs: 35,40,125,127,173
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# HTTP based dynamic DNS service (DynDNS)

<div class="yellowbox">NB: This article was written before we released the [DynDNS Service plug-in](https://simpledns.plus/plugin-dyndns).  
The DynDNS Service plug-in makes it much easier to run a HTTP based DynDNS service</div>

You can run your own dynamic DNS service (like [http://www.dyndns.org/](http://www.dyndns.org/){target=_blank}) using Simple DNS Plus.

Simple DNS Plus supports TSIG signed dynamic updates directly through the DNS protocol.  
This is the most efficient and recommend way to do dynamic updates.  
However TSIG signed update are currently only supported by few software clients (see reference articles below).

To enable dynamic updates over HTTP, which is supported by practically all software clients as well as many broadband Internet routers, you need to setup a simple dynamic web-page on your web-server to validate the user name/password, and then update Simple DNS Plus.

A sample web-page (ASP.NET and Classic ASP) doing just this is available for download from here:  
[dyndns.zip (2 KB)](https://simpledns.plus/outbox/dyndns.zip)

The zip file includes 3 files:  
\- dyndns.asp (Classic ASP version)  
\- dyndns.aspx (ASP.NET 2.0 version)  
\- ddnsuser.txt (user list configuration file)

Extract the files into your IIS web-site and make sure ASP or ASP.NET 2.0 is enabled depending on which version you want to use.

Edit the dyndns.asp/aspx file and update the "sdnsIPAddr", "sdnsPort", "sdnsPassword" variables (at the top of the file) to match the settings in your Simple DNS Plus Options dialog / HTTP API section.

The "UserListFile" variable specifies the relative location and file name of the user list file (ddnsuser.txt).  
This is a simple text file where each line lists the user-id, password, and host name of a user - separated by semicolons (;). For example:

alex;1234;alex.yourname.com

IMPORTANT: You should move the user list file to a location where it cannot be accessed directly through the web-site (for example the "app_data" directory for ASP.NET) or deny access to it using IIS or file security settings.

Make sure you have setup the parent zone(s) for all user's host names.  
For example if a users host name is "alex.yourname.com", you must have a primary zone "yourname.com" setup in Simple DNS Plus.

After updating the user list file, the dynamic DNS service should be ready to use.  
The update URL which you can use in dyndns client software, routers, or directly in a browser is:

http://&lt;www.your-domain.com&gt;/dyndns.asp?user=&lt;userid&gt;&amp;pw=&lt;password&gt;&amp;ip=&lt;ip-address&gt;

For example:

http://www.yourname.com/dyndns.asp?user=alex&amp;pw=1234&amp;ip=1.2.3.4

The last "ip" parameter is optional. If no IP address is specified, the web page script will use the IP address that the HTTP request came from.

If you want to integrate this with your existing user database or store user/domains in some other way, you can modify the "LookupUsersHostName" sub-routine in the web-page to fetch this information in whatever way you want.

