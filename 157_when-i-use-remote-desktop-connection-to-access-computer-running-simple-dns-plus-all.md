---
category: 14
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# When I use Remote Desktop Connection to access the computer running Simple DNS Plus, all the Simple DNS Plus icons are black. How do I fix this?

This typically happens when the terminal session uses a 15 bit display color depth.  
You may have requested a higher color depth in the Remote Desktop client, but the default group policy on XP/2003 limits the maximum display color depth to 15 bits.  
To solve this, you can either try connecting with a lower color depth (256 colors), or set the group policy on the server computer to allow a higher color depths, and then connect requesting 16 bit color depth.  
To set the group policy for this, please see [MS KB article 278502](https://simpledns.plus/mskb/278502.pdf){target=_blank}.

