---
title: Simple DNS Plus service fails to start on computer reboot
category: 14
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<p>If the Simple DNS Plus service doesn't automatically start up after you start the computer, and you find error events in the Windows Event Log / Application log like this:</p>
<blockquote dir="ltr" style="margin-right: 0px;">
<p>"The Simple DNS Plus service failed to start due to the following error:<br />
The service did not respond to the start or control request in a timely fashion"</p>
</blockquote>
<p>and/or like this:</p>
<blockquote dir="ltr" style="margin-right: 0px;">
<p>"Timeout (30000 milliseconds) waiting for the Simple DNS Plus service to connect."</p>
</blockquote>
<p>Then it may be because your computer is a just too busy at startup - for example if the computer is low on memory and begins swapping to disk.</p>
<p>By default the Windows Service Manager gives a service 30 seconds to start, and then it kills the service process assuming something is wrong.</p>
<p>You may be able to get around this issue by overriding the 30 second default with a higher value by setting a Windows registry key.</p>
<p dir="ltr" style="margin-right: 0px;">From the Windows Start menu, select "Run", type in "regedit" and click OK, and browse to</p>
<blockquote dir="ltr" style="margin-right: 0px;">
<p dir="ltr" style="margin-right: 0px;">HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control</p>
</blockquote>
<p>If it is not already there, create a new DWORD value named "ServicesPipeTimeout":<br />
<br />
<img height="291" src="img/120/1.png" width="505" /></p>
<p> <img height="291" src="img/120/2.png" width="406" /></p>
<p>Double click "ServicesPipeTimeout" and set the value to the number of milliseconds that the Windows Service Manager should wait for services to start. For example decimal 300000 (= 5 minutes):</p>
<p> <img height="203" src="img/120/3.png" width="345" /></p>