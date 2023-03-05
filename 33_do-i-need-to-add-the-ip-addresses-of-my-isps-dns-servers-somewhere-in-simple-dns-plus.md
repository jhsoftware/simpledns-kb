---
title: Do I need to add the IP addresses of my ISP's DNS servers somewhere in Simple DNS Plus?
category: 11
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<p>No, you don't need any other DNS servers to use Simple DNS Plus.<br />
<br />
The Internet DNS system is basically a BIG tree of DNS servers which are all connected, and at the root of this tree are the "root" DNS servers.<br />
<br />
Simple DNS Plus comes pre-configured with a "root file", which is a list of the 13 "root" DNS servers on the internet.<br />
<br />
For example to find "www.volvo.se" (the web server for Volvo in Sweden), Simple DNS Plus does the following:<br />
<br />
1) Ask one of the 13 root DNS servers for the addresses of "se" DNS servers.<br />
2) Ask one of these "se" DNS servers for the addresses of "volvo.se" DNS servers.<br />
3) Ask one of these "volvo.se" DNS servers for the address of "www.volvo.se"</p>
<p>By iterating through the tree (starting at the root), Simple DNS Plus can find any address in the world based on this "root file".</p>