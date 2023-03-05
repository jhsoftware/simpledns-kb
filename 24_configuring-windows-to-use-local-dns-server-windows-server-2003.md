---
category: 11
frontpage: false
comments: true
vgroup: 5
vname: Windows Server 2003
vsort: 105
refs: 26
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# Configuring Windows to use local DNS server (Windows Server 2003)

First Double click the "Network Connections" icon in the Control Panel:

![](img/24/1.png)

Right-click your Internet connection's icon and select "Properties":

![](img/24/2.png)

Select the "Internet Protocol (TCP/IP)" item, and click the "Properties" button:

![](img/24/3.png)

Check "Use the following DNS server addresses" and enter the IP address of the local DNS server (*) as the Preferred DNS server:

![](img/24/4.png)

Finally click "OK" both in the "Internet Protocol (TCP/IP) Properties" and "Local Area Connection Properties" dialogs to save your changes.

(*) The DNS server IP address must match an IP address that Simple DNS Plus is configured to listen on in the Options dialog / DNS / Inbound Requests section.  
If you are configuring the computer which Simple DNS Plus is running on, you can use 127.0.0.1 (the "localhost" address) - otherwise you must use an IP address which is accessible over the local area network.

