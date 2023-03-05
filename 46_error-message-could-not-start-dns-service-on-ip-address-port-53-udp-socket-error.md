---
title: Error message "Could not start DNS service on <ip-address> port 53 UDP (Socket error 10049 The requested address is not valid in its context)"
category: 14
frontpage: false
comments: true
refs: 47
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<p>This is probably because you have previously configured Simple DNS Plus to listen for DNS requests on an IP address which is no longer present on the computer.</p>
<p>To fix this, go to the Options dialog / DNS / Inbound Requests section, and select which IP addresses Simple DNS Plus should listen on, and then click the OK button:</p>
<p> <img height="425" src="img/46/1.png" width="641" /></p>