---
title: Configuring Windows to use local DNS server (Windows XP)
category: 11
frontpage: false
comments: true
vgroup: 5
vname: Windows XP
vsort: 104
refs: 26
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<p>First Double click the "Network Connections" icon in the Control Panel:<br />
(Click "Switch to Classic View" if it doesn't look like this)</p>
<p>
<img height="276" alt="1126a.png" src="img/28/1.png" width="414" />
</p>
<p>Right-click your Internet connection's icon and select "Properties":</p>
<p>
<img height="398" alt="1126b.png" src="img/28/2.png" width="433" />
</p>
<p>Select the "Internet Protocol (TCP/IP)" item, and click the "Properties" button: </p>
<p>
<img height="296" alt="1126c.png" src="img/28/3.png" width="367" />
</p>
<p style="text-align: center;">
</p>
<p>Check "Use the following DNS server addresses" and enter the IP address of the local DNS server (*) as the Preferred DNS server:</p>
<p>
<img height="455" alt="1126d.png" src="img/28/4.png" width="404" />
</p>
<p>Finally click "OK" both in the "Internet Protocol (TCP/IP) Properties" and "Local Area Connection Properties" dialogs to save your changes.</p>
<p>(*) The DNS server IP address must match an IP address that Simple DNS Plus is configured to listen on in the Options dialog / DNS / Inbound Requests section.<br />
If you are configuring the computer which Simple DNS Plus is running on, you can use 127.0.0.1 (the "localhost" address) - otherwise you must use an IP address which is accessible over the local area network. </p>