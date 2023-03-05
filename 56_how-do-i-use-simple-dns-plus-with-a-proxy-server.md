---
title: How do I use Simple DNS Plus with a proxy server?
category: 6
frontpage: false
comments: true
refs: 130,140
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<p>Please see the reference articles below for Illustrations&nbsp;on how to setup&nbsp;popular proxy server products.</p>
<p>A proxy server often includes a DNS proxy or mapping function used to relay DNS requests from clients behind the proxy server.</p>
<p>If the proxy server and Simple DNS Plus are running on the same computer, this may conflict as both programs are trying to use port 53.<br />
Simple DNS Plus may display the message:<br />
"Could not start DNS service / port 53 may be in use by another program"</p>
<p>You may be able solve this by configuring Simple DNS Plus to only listen on 127.0.0.1 or an external IP address (see Options dialog / IP addresses).</p>
<p>Or you can disable the DNS function on the proxy server. Most likely you won't need functionality in the proxy server&nbsp;because Simple DNS Plus provides this directly.</p>