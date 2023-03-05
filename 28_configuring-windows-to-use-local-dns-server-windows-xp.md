---
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
# Configuring Windows to use local DNS server (Windows XP)

First Double click the "Network Connections" icon in the Control Panel:  
(Click "Switch to Classic View" if it doesn't look like this)

![](img/28/1.png)

Right-click your Internet connection's icon and select "Properties":

![](img/28/2.png)

Select the "Internet Protocol (TCP/IP)" item, and click the "Properties" button:

![](img/28/3.png)

Check "Use the following DNS server addresses" and enter the IP address of the local DNS server (*) as the Preferred DNS server:

![](img/28/4.png)

Finally click "OK" both in the "Internet Protocol (TCP/IP) Properties" and "Local Area Connection Properties" dialogs to save your changes.

(*) The DNS server IP address must match an IP address that Simple DNS Plus is configured to listen on in the Options dialog / DNS / Inbound Requests section.  
If you are configuring the computer which Simple DNS Plus is running on, you can use 127.0.0.1 (the "localhost" address) - otherwise you must use an IP address which is accessible over the local area network.

