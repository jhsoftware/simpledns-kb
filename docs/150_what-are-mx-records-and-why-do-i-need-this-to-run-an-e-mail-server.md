---
category: 7
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# What are MX records, and why do I need this to run an e-mail server?

When you visit a web site like http://simpledns.plus, your browser firsts send a DNS request (via the operating system) to a DNS server asking for the IP address of "simpledns.plus".  
When the DNS server replies with the IP address, the browser contacts the web-server with the given IP address and fetches the page.

However, that DNS request contains more than just the name desired. It also contains the record-type desired, information on how the DNS server should respond, etc.

In the case of the browser, the record type is "A" - or basic Name=IP address record type - like the hosts file.

The process of e-mail delivery is a little more complex (getting to MX records).  
For example if you send an e-mail to "someone@simpledns.plus", first your e-mail client software forwards the message to an e-mail server (typically located at your ISP).  
It is now that e-mail server's job to forward the message to an e-mail server responsible for "simpledns.plus" (the last part of the e-mail address).  
It would be simple enough if it could just look up the IP address of "simpledns.plus" (the "A" record) like you suggest - but in case of e-mail that's not the way things work.  
It must first determine who is responsible for mail delivery to "simpledns.plus".  
This could be "mail.simpledns.plus", but often it's someone else.  
This is done by first sending a DNS request for MX-records for "simpledns.plus", which will return the names of the responsible e-mail servers. It often returns a number of server names when a larger company has multiple e-mail servers.  
The sending e-mail server (your ISP's) will then pick one of these mail-server names (according to the MX-record preference value), look up it's IP address (the "A" record), connect via that IP address, and deliver the e-mail.  
If delivery fails, it will try another server in the list of MX-records returned, and so on until it succeeds.  
The receiving e-mail server is now responsible for delivery to "someone" - the first part of the e-mail address.

Other DNS record types also have other specialized functions.  
For details see the [help file](https://simpledns.plus/helplink?p=rectypes).