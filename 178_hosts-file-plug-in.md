---
title: Hosts File plug-in
category: 8
frontpage: false
comments: true
refs: 110
created-utc: 2019-01-01
modified-utc: 2020-01-08
---
<p>This plug-in serves host (A/AAAA) and reverse (PTR) DNS records from a standard <a href="https://simpledns.plus/helplink?p=df_hostsfile">hosts file</a>.</p>

<p>This can be used as a very simple way to store and host DNS records, but more commoly this is used to block ads and malicious web-sites.<br />
You can create your own hosts file, but there are also some very kind people on the Internet who maintain hosts files for various purposes and make these publicly available. For example <a href="http://hosts-file.net" target="_blank">http://hosts-file.net</a> and <a href="http://pgl.yoyo.org/adservers" target="_blank">http://pgl.yoyo.org/adservers</a><br />
For more advanced web-site blocking, see also the <a href="https://simpledns.plus/plugin-domainbl">Domain Blacklist plug-in</a>.</p>

<p>On the &quot;Plug-In Settings&quot; tab, enter the location of the hosts file, specify if the file should be re-loaded automatically when updated,  and enter the TTL to be used:</p>

<p><img src="img/178/1.png" /></p>

<p>You can use multiple hosts files by setting up multiple &quot;Hosts File&quot; plug-in instances.</p>

<p>Host file line example:</p>

<pre>1.2.3.4 example.com</pre>

<p>Defines an A-Record (example.com -&gt; 1.2.3.4) and a PTR-record (4.3.2.1.in-addr.arpa -&gt; example.com).</p>