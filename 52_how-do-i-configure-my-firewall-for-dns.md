---
category: 6
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# How do I configure my firewall for DNS?

The are two main categories of firewalls:

### 1) Software firewall - filtering network traffic to and from the local computer

Recent versions of Windows include a software firewall ("Windows Firewall" / "Windows Defender Firewall").
When you install Simple DNS Plus, Windows Firewall "rules" are automatically added to allow Simple DNS Plus to communicate.

Many 3rd party software firewalls are also available. With this type of firewall running on the same computer as Simple DNS Plus, you typically only need to "allow" Internet access for the Simple DNS Plus application modules (.exe files).

### 2) Hardware/Server firewalls - filtering network traffic between the Internet and a local network

This type of firewall is often built into routers, and filters TCP/IP traffic by protocol (UDP, TCP, IGMP, etc.), to/from IP address, and to/from port number.

DNS mainly uses the UDP protocol - except for zone transfer which use TCP.

TCP/IP port numbers are often categorized as either "server ports" (1 to 1023), or "application ports" (>1023).

Most server programs listen for requests on a "server port", and client programs (applications) communicate with the server from a random "application port".

A DNS server listens for requests on port 53 (both UDP and TCP).

So all DNS requests are sent to port 53, usually from an application port (>1023).

You can specify which port Simple DNS Plus sends outgoing DNS requests from in the Options dialog / DNS / Outbound Requests section.

DNS responses are returned from port 53 back to the original from-port (>1023).

Many firewalls are by default configured to accept all traffic sent to application port numbers, so you may not need to worry about DNS responses.

So you have to allow all traffic (in and out) sent to port 53 (requests), and possibly all traffic (in and out) from port 53 to any application port (responses).

This could mean as many as 8 "firewall rules" (UDP/TCP, In/Out, To/From 53).

NOTE: Some older firewall firmware (such as Cisco PIX) will block all DNS packets with EDNS0 enabled.
If needed, you can disable EDNS0 in the Simple DNS Plus Options dialog / DNS / Miscellaneous section, but we highly recommend you get the firewall firmware updated instead.

NOTE: Some firewall products have special filters that block certain type DNS requests.
One example is the "NG" firewall software from "Check Point Software Technologies" which is also embedded in some hardware solutions.
This software has a "DNS verification / inspection" feature, which will block all but the most basic type DNS traffic.
It is necessary to disable this feature for certain DNS functions such as zone update notifications to secondary servers to work.