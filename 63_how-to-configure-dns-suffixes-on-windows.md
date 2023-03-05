---
title: How to configure DNS suffixes on Windows
category: 11
frontpage: false
comments: true
refs: 75,142
created-utc: 2019-01-01
modified-utc: 2021-11-01
---
<p>"DNS suffixes" are used for resolving unqualified domain names (names with no dots).</p>
<p>In the Windows Control Panel, under "Network and Internet" click the "View network status and tasks" link:</p>
<p>
<img height="393" src="img/63/1.png" width="560" />
</p>
<p>Click the "Manage network connections" link:</p>
<p>
<img height="251" src="img/63/2.png" width="382" />
</p>
<p>Right-click a network connection and select "Properties" from the pop-up menu:</p>
<p>
<img height="412" src="img/63/3.png" width="376" />
</p>
<p>In the network connection Properties dialog select "Internet Protocol Version 4 (TCP/IPv4)" and click the "Properties" button:</p>
<p>
<img height="472" src="img/63/4.png" width="377" />
</p>
<p>In the "Internet Protocol Version 4 (TCP/IPv4) Properties" dialog click the "Advanced..." button:</p>
<p>
<img height="459" src="img/63/5.png" width="414" />
</p>
<p>In the "Advanced TCP/IP Settings" dialog select the "DNS" tab, and specify which DNS suffixes to use for resolving unqualified domain names:</p>
<p>
<img height="492" src="img/63/6.png" width="414" />
</p>
<p>If you choose the first (and default) option to append primary and connection specific DNS suffixes, then you will also need to configure the primary DNS suffix. See reference article below.</p>