---
category: 11
frontpage: false
comments: true
vgroup: 5
vname: Windows Server 2008
vsort: 103
refs: 26
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# Configuring Windows to use local DNS server (Windows Server 2008)

In the Windows Control Panel, under "Network and Internet", click "View network status and tasks":

![](img/25/1.png)

Click the "Manage network connections" task:

![](img/25/2.png)

Right-click your Internet connection's icon and select "Properties":

![](img/25/3.png)

Select the "Internet Protocol Version 4 (TCP/IPv4)" item, and click the "Properties" button:

![](img/25/4.png)

Select "Use the following DNS server addresses", and enter the IP address of the local DNS server (*) as the Preferred DNS server:

![](img/25/5.png)

Finally click the "OK" in this and the previous dialogs to save your changes.

(*) The DNS server IP address must match an IP address that Simple DNS Plus is configured to listen on in the Options dialog / DNS / Inbound Requests section.  
If you are configuring the computer which Simple DNS Plus is running on, you can use 127.0.0.1 (the "localhost" address) - otherwise you must use an IP address which is accessible over the local area network.

