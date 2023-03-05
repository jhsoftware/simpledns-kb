---
category: 16
frontpage: false
comments: true
vgroup: 2
vname: IIS 6.0 (Windows XP / Server 2003) and earlier
vsort: 1
refs: 145,12
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# Virtual hosting with IIS (Internet Information Services) (IIS 6.0 (Windows XP / Server 2003) and earlier)

NOTE: Only IIS versions for Windows Server and Windows Vista support multiple web-sites as described below. If you are using Windows 98, Me, NT4 Workstation, Windows 2000 Professional, or Windows XP please see reference article below instead.

"Virtual hosting" means hosting multiple web-sites with different domain names on the same IP address.

This procedure is also described in [Microsoft KB article Q190008](http://support.microsoft.com/kb/q190008/){target=_blank}

From the "Internet Information Services (IIS) Manager" window, right click on a web-site, and select "Properties":

![](img/143/1.png)

In the web-site Properties dialog, click the "Advanced..." button:

![](img/143/2.png)

In the "Advanced Web Site Identification" dialog, select the first "identity", and click the "Edit" button:

![](img/143/3.png)

Enter the web-site domain name in the "Host Header Name" field:

![](img/143/4.png)

Click the OK button in all the dialogs to save your changes.

Create additional web sites the same way.

