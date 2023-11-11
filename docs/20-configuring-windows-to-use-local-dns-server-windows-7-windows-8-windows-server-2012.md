---
category: 11
frontpage: false
comments: true
vgroup: 5
vname: Windows 7 / Windows 8 / Windows Server 2012
vsort: 101
refs: 26
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# Configuring Windows to use local DNS server (Windows 7 / Windows 8 / Windows Server 2012)

In the Windows Control Panel, under "Network and Internet", select "View network status and tasks":

![](img/20/1.png)

Click "Change adapter settings":

![](img/20/2.png)

Right-click your Internet connection's icon and select "Properties":

![](img/20/3.png)

Select the "Internet Protocol Version 4 (TCP/IPv4)" item, and click the "Properties" button:

![](img/20/4.png)  

Select "Use the following DNS server addresses", and enter the IP address of the local DNS server (*) as the Preferred DNS server:

![](img/20/5.png)

Finally click the "OK" button in this and the previous dialogs to save your changes.

(*) The DNS server IP address must match an IP address that Simple DNS Plus is configured to listen on in the Options dialog / DNS / Inbound Requests section.  
If you are configuring the computer which Simple DNS Plus is running on, you can use 127.0.0.1 (the "localhost" address) - otherwise you must use an IP address which is accessible over the local area network.

  
