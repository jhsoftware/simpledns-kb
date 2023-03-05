---
category: 7
frontpage: false
comments: true
refs: 42
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# Publishing your SIP server address in DNS

If you are using a SIP server for VOIP communication and want to enable other Internet users to call people in your organization using addresses such as "1004@domain.com" (where 1004 is a local phone extension) or e-mail addresses such as "user@domain.com", you need to setup a DNS SRV-record for "_sip._udp." + your domain.

To setup SRV-records in Simple DNS Plus, in the main window click the "Records" button, then right-click a zone in the left list, select "Other new record...", and then "SRV-record".

For example:

![](img/112/1.png)

The "port" field must be the port number that your SIP server listens on (typically 5060).  
And the "Target host" field must be the host name of your SIP server (you must have an A-record for the host name pointing to the IP address of the SIP server).

