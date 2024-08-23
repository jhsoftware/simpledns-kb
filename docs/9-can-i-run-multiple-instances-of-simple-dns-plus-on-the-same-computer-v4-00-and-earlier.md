---
category: 11
frontpage: false
comments: true
vgroup: 1
vname: Simple DNS Plus v. 4.00 and earlier
vsort: 2
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# Can I run multiple instances on the same computer? (Simple DNS Plus v. 4.00 and earlier)

One instance of Simple DNS Plus can serve multiple IP addresses on the same machine.  
You can specify which IP addresses in the Options dialog / DNS / Inbound Requests section.

Under normal circumstances it wouldn't be necessary to run multiple instances because, to the rest of the Internet, each IP address looks like a different DNS server (easy way to run primary and secondary on one machine).

However it is possible to run multiple instances (from different directories), for example if you want to serve different data to clients on different network segments.

Just make sure to configure each instance to listen on different local IP addresses, so they won't conflict.  
If you are going to use the HTTP API, you will also need to make sure that each instance uses different IP addresses or port numbers for this - see Options dialog / HTTP API.

To do this:

Install the first instance as normal. Typically, this will install to "C:\Program Files\Simple DNS Plus".  
Then copy this whole directory - for example to "C:\Program Files\Simple DNS Plus2".

Now you can run the second instance from this directory.

The only issue with this is when Simple DNS Plus is running as a Windows services.  
The default service name is "sdnsplus" (NET START SDNSPLUS), and description "Simple DNS Plus" (Shows in the Services list).  
No two services can have the same name, so to run additional Simple DNS Plus services you need to change the service name (and description) for each additional copy.  
You can do this by manually editing the "sdnsplus.ini" file (with Notepad) and changing the "ServiceName" and "ServiceDesc" settings.