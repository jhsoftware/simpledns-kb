---
title: Using Simple DNS Plus with WinGate
category: 6
frontpage: false
comments: true
refs: 56
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<p>(WinGate is a product from QBIK - <a href="http://www.wingate.com" target="_blank">www.wingate.com</a>)</p>
<p>WinGate includes a DNS proxy or mapping function ("DNS Service") used to relay DNS requests from clients behind the proxy server.<br />
If WinGate and Simple DNS Plus are running on the same computer, this will conflict as both programs are trying to use port 53.</p>
<p>You can disable the DNS function in WinGate. You won't need this because Simple DNS Plus provides this functionality directly.</p>
<p>In WinGate GateKeeper - select the "System" tab, right-click on "DNS Service", and select "Properties":</p>
<p> <img height="381" src="img/140/1.png" width="527" /></p>
<p>As "Service startup", select "Service is disabled", and click the OK button:</p>
<p> <img height="374" src="img/140/2.png" width="549" /></p>
<p>After changing this setting, you should be able to start the DNS service in Simple DNS Plus (select "Start Server" from the "File" menu).</p>
<p>WinGate also includes firewall functionality which may block DNS requests from the Internet.<br />
If you want to host Internet domain names with Simple DNS Plus, you need to add the following configuration in WinGate to allow this:</p>
<p>In WinGate GateKeeper - select the "System" tab, right-click on "Extended Networking", and select "Properties":</p>
<p> <img height="381" src="img/140/3.png" width="527" /></p>
<p>Select "Port Security" in the left list and click the "Add" button:</p>
<p> <img height="383" src="img/140/4.png" width="522" /></p>
<p>Enter description "DNS server", check "Internet computers to WinGate PC", check both "TCP" and "UDP", enter ports 53 to 53, select "Allow Packet", and click the OK button:</p>
<p> <img height="478" src="img/140/5.png" width="390" /></p>