---
title: Using DynSite with Simple DNS Plus
category: 4
frontpage: false
comments: true
refs: 35,125,80,40,173
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<div style="border: 1px solid black; background-color: #ffffc0;">NB: This article was written before we released the <a href="https://simpledns.plus/plugin-dyndns">DynDNS Service plug-in</a>.<br />
DynSite can also be used with the DynDNS Service plug-in making it even easier to run a DynDNS service</div>
<p>DynSite is a product from No&euml;l Danjou - <a href="http://noeld.com/dynsite.asp" target="_blank">http://noeld.com/dynsite.asp</a></p>
<p>You can use DynSite to automatically update DNS records on a remote Simple DNS Plus server. DynSite will update the DNS records each time the IP address changes on the local computer.</p>
<p>This makes it possible to run different services (such as a web-server) on a computer with a dynamic IP address.<br />
You can also use this anytime you need to access roaming computers - for example traveling sales people with laptops.</p>
<p>In the following example, we have a roaming laptop with a dynamic IP address (currently 5.6.7.8) which we want to access using the domain name "laptop.example.com", and we are running a Simple DNS Plus server with the name of "ns1.example.com" on IP address 11.22.33.44 (static).</p>
<p>Step 1:  First you need to setup a "example.com" zone that will hold the DNS record for the laptop (the dynamic IP computer). See <a href="/kb/4/basic-dns-server-configuration-example">this article</a>. If you have already setup a zone for your domain name, you can use that.</p>
<p>Step 2: Next you need to setup a TSIG key (basically a user name / password pair) for the laptop.</p>
<p>In the main window of Simple DNS Plus, click the Options button:</p>
<p>
<img height="147" alt="sdns1.png" src="img/127/1.png" width="324" />
</p>
<p>In the Options dialog, under "DNS" select "TSIG Dynamic Updates", and click the "Add..." button:</p>
<p> <img height="361" alt="sdns2.png" src="img/127/2.png" width="545" /></p>
<p>Enter a key name, a key value, and specify which domain(s) the client with this key may update.<br />
The key name can be whatever you find convenient - for example the name of the client computer or the person using it.<br />
The key value is basically a binary password entered in base64 encoding. You can click the "Generate" button to automatically create a new random value of either 128, 256, or 512 bit length:</p>
<p> <img height="399" alt="sdns3.png" src="img/127/3.png" width="425" /></p>
<p> When done click the "OK" button, and also click the "OK" button in the previous dialog to save your settings.</p>
<p>Step 3: Setup DynSite on the laptop.</p>
<p>After installing DynSite, you need to add a new account for the Simple DNS Plus server to it.<br />
The first time you run DynSite, the startup wizard eventually takes you to the "Account Assistant".<br />
If you are already running DynSite, you can invoke the "Account Assistant" by right clicking on the DynSite tray icon and selecting "Account Assistant" from the pop-up menu:</p>
<p> <img height="356" alt="du1.png" src="img/127/4.png" width="347" /></p>
<p>Click the "Next" button in the first page of the "Account Assistant":</p>
<p>
<img height="387" alt="du2.png" src="img/127/5.png" width="503" /> </p>
<p>Select server type "DNS Servers", and click the "Next" button:</p>
<p> <img height="387" alt="du3.png" src="img/127/6.png" width="503" /></p>
<p>Select "Configure a new DNS server", enter the name of the DNS server, and click the "Next" button:</p>
<p> <img height="386" alt="du4.png" src="img/127/7.png" width="503" /></p>
<p>In the "DNS server" field, enter the domain name or IP address of your Simple DNS Plus server.<br />
In the "Server Port" field, enter "53"<br />
In the "Method" field, select "Transaction Signature (hmac-md5)"<br />
In the "Key name" field, copy the key name used in Simple DNS Plus.<br />
In the "Key value" field, copy the key value used in Simple DNS Plus.<br />
Make sure "I want to configure a zone on this server" is checked, and click the "Next" button:</p>
<p> <img height="386" alt="du5.png" src="img/127/8.png" width="503" /></p>
<p>In the "Screen name" field, enter the full domain name of the client computer.<br />
In the "Zone" field, enter the name of the zone where you want the DNS record in Simple DNS Plus.<br />
In the "Host names" field, enter the first segment of the client computer domain name.<br />
In the "Time-To-Live" field, enter the number of seconds that this record may be cached by other DNS servers. Whenever your IP address changes, this value determines how long it takes before all of the Internet once again can reach you through the domain names. We recommend using 300 (5 minutes) or less.<br />
Make sure "Update zone as well" is NOT checked, and click the "Next" button:</p>
<p> <img height="386" alt="du6.png" src="img/127/9.png" width="503" /></p>
<p>Click the "Next" button, and then the "Finish" button on the following pages:</p>
<p> <img height="386" alt="du7.png" src="img/127/10.png" width="503" /></p>
<p>
<img height="387" alt="du8.png" src="img/127/11.png" width="503" />
</p>
<p>When everything is setup correctly, DynSite will now update Simple DNS Plus:</p>
<p> <img height="336" alt="du9.png" src="img/127/12.png" width="411" /></p>
<p>And you can see the new/updated record in Simple DNS Plus:</p>
<p> <img height="276" alt="sdns4.png" src="img/127/13.png" width="595" /></p>