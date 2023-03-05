---
category: 6
frontpage: false
comments: true
refs: 130,140
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# How do I use Simple DNS Plus with a proxy server?

Please see the reference articles below for Illustrations on how to setup popular proxy server products.

A proxy server often includes a DNS proxy or mapping function used to relay DNS requests from clients behind the proxy server.

If the proxy server and Simple DNS Plus are running on the same computer, this may conflict as both programs are trying to use port 53.  
Simple DNS Plus may display the message:  
"Could not start DNS service / port 53 may be in use by another program"

You may be able solve this by configuring Simple DNS Plus to only listen on 127.0.0.1 or an external IP address (see Options dialog / IP addresses).

Or you can disable the DNS function on the proxy server. Most likely you won't need functionality in the proxy server because Simple DNS Plus provides this directly.

