---
title: Weighted Round Robin plug-in
category: 8
frontpage: false
comments: true
refs: 110
created-utc: 2019-01-01
modified-utc: 2020-01-08
---
<p>This plug-in serves IP addresses for a host name <a href="https://simpledns.plus/helplink?p=df_rrobin">round robin</a> from a weighted list.</p>

<p>IP addresses are rotated so that the first visitor gets one IP address, the next visitor another IP address, etc.<br />
However IP addresses with higher weight values are served more often than IP addresses with lower weight values.<br />
This makes it possible for example to send more traffic to high capacity servers in a round robin set.</p>

<p>In the plug-in instance dialog / Plug-In Settings tab you can specify the host name, weight / IP addresses, and host record TTL:</p>

<p><img src="img/190/1.png" /></p>

<p>The weight value for each IP address is a number from 1 to 99.<br />
You can treat these as percentages if you make sure they total 100.<br />
However any combination of weight values can be used - they do not need to add up to any specific total.<br />
With the configuration in the screen shot above, out of 10 requests, 1 response would point to 1.1.1.1, 3 responses to 3.3.3.3 and 6 responses to 6.6.6.6.</p>

<p>This plug-in works with both IPv4 and IPv6 addresses.</p>

<p>NOTE: DNS round robin cannot provide an exact weight distribution of traffic because other DNS server will cache the records and potentially serve multiple end users with the same data, and different end users may use services more or less. But measured on average over time the traffic distribution will be as weighted.</p>