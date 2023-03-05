---
title: Using DirectUpdate with Simple DNS Plus
category: 4
frontpage: false
comments: true
refs: 35,127,80,40,173
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<div style="border: 1px solid black; background-color: #ffffc0;">NB: This article was written before we released the <a href="https://simpledns.plus/plugin-dyndns">DynDNS Service plug-in</a>.<br />
DirectUpdate can also be used with the DynDNS Service plug-in making it even easier to run a DynDNS service</div>
<p>DirectUpdate is a product by William Levra-Juillet - <a href="http://www.directupdate.net" target="_blank">http://www.directupdate.net</a></p>
<p>You can use DirectUpdate to automatically update DNS records on a remote Simple DNS Plus server. DirectUpdate will update the DNS records each time the IP address changes on the local computer.</p>
<p>This makes it possible to run different services (such as a web-server) on a computer with a dynamic IP address.<br />
You can also use this anytime you need to access roaming computers - for example traveling sales people with laptops.</p>
<p>In the following example, we have a roaming laptop with a dynamic IP address (currently 5.6.7.8) which we want to access using the domain name "laptop.jhsoft.com", and we are running a Simple DNS Plus server with the name of "ns1.example.com" on IP address 11.22.33.44 (static).</p>
<p>Step 1:  First you need to setup a zone that will hold the DNS record for the laptop (the dynamic IP computer). See <a href="/kb/4/basic-dns-server-configuration-example">this article</a>. If you have already setup a zone for your domain name, you can use that.</p>
<p>Step 2: Next you need to setup a TSIG key (basically a user name / password pair) for the laptop.</p>
<p>In the main window of Simple DNS Plus, click the Options button:</p>
<p>
<img height="147" alt="sdns1.png" src="img/125/1.png" width="324" />
</p>
<p>In the Options dialog, under "DNS" select "TSIG Dynamic Updates", and click the "Add..." button:</p>
<p> <img height="361" alt="sdns2.png" src="img/125/2.png" width="545" /></p>
<p>Enter a key name, a key value, and specify which domain(s) the client with this key may update.<br />
The key name can be whatever you find convenient - for example the name of the client computer or the person using it.<br />
The key value is basically a binary password entered in base64 encoding. You can click the "Generate" button to automatically create a new random value of either 128, 256, or 512 bit length:</p>
<p> <img height="399" alt="sdns3.png" src="img/125/3.png" width="425" /></p>
<p> When done click the "OK" button, and also click the "OK" button in the previous dialog to save your settings.</p>
<p>Step 3: Setup DirectUpdate on the laptop.</p>
<p>After installing Directupdate, you need to add a new account to it.<br />
Right-click the tray icon and from the the pop-up menu select "Launch admin now..."  to access to admin module:</p>
<p> <img height="228" alt="du1.png" src="img/125/4.png" width="461" /></p>
<p>In the "administration module", select "DNS accounts", and click the "Add..." button:</p>
<p> <img height="455" alt="du2.png" src="img/125/5.png" width="582" /></p>
<p>- Select "Simple DNS Plus" from the "Account type" drop-down list.<br />
- Un-check "Disable/ignore this account".<br />
- Make sure "Perform updates using secure protocol" is checked.<br />
- In IP Detection to use select "Default IP detection".<br />
- In the "TSIG key name" fiield, copy the key name used in Simple DNS Plus.<br />
- In the "TSIG secret" field, copy the key value used in Simple DNS Plus.<br />
- In the "Domain / host" field, enter the host name you want to update.<br />
- In the "Server" field, enter the host name or IP address of your Simple DNS Plus server. </p>
<p> <img height="455" alt="du3.png" src="img/125/6.png" width="582" /></p>
<p>When everything is setup correctly, DirectUpdate will now update Simple DNS Plus.<br />
If you select "DNS accounts", you should see the Status as "OK":</p>
<p>
<img height="124" alt="du4.png" src="img/125/7.png" width="582" />
</p>
<p>And you can see the new/updated record in Simple DNS Plus:</p>
<p> <img height="276" alt="sdns4.png" src="img/125/8.png" width="595" /></p>