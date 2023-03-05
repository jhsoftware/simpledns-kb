---
title: Configuring Windows to use local DNS server (Windows Vista)
category: 11
frontpage: false
comments: true
vgroup: 5
vname: Windows Vista
vsort: 102
refs: 26
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<p>In the Windows Control Panel, under "Network and Internet", select "View network status and tasks":</p>
<p>
<img height="277" alt="1188a.png" src="img/27/1.png" width="410" />
</p>
<p>Click the "Manage network connections" task: </p>
<p>
<img height="190" alt="1188b.png" src="img/27/2.png" width="235" />
</p>
<p>Right-click your Internet connection's icon and select "Properties":</p>
<p>
<img height="327" alt="1188c.png" src="img/27/3.png" width="238" />
</p>
<p>Select the "Internet Protocol Version 4 (TCP/IPv4)" item, and click the "Properties" button: </p>
<p>
<img height="472" alt="1188d.png" src="img/27/4.png" width="377" />
</p>
<p style="text-align: center;">
</p>
<p>Select "Use the following DNS server addresses", and enter the IP address of the local DNS server (*) as the Preferred DNS server:</p>
<p> <img height="459" alt="1188e.png" src="img/27/5.png" width="414" /></p>
<p>Finally click the "OK" in this and the previous dialogs to save your changes.</p>
<p>(*) The DNS server IP address must match an IP address that Simple DNS Plus is configured to listen on in the Options dialog / DNS / Inbound Requests section.<br />
If you are configuring the computer which Simple DNS Plus is running on, you can use 127.0.0.1 (the "localhost" address) - otherwise you must use an IP address which is accessible over the local area network. </p>