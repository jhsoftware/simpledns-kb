---
title: When I use Remote Desktop Connection to access the computer running Simple DNS Plus, all the Simple DNS Plus icons are black. How do I fix this?
category: 14
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<p>This typically happens when the terminal session uses a 15 bit
display color depth.<br />
You may have requested a higher color depth
in the Remote Desktop client, but the default group policy on
XP/2003 limits the maximum display color depth to 15 bits.<br />
To
solve this, you can either try connecting with a lower color depth
(256 colors), or set the group policy on the server computer to
allow a higher color depths, and then connect requesting 16 bit
color depth.<br />
To set the group policy for this, please see <a href="https://simpledns.plus/mskb/278502.pdf" target="_blank">MS KB
article 278502</a>.</p>