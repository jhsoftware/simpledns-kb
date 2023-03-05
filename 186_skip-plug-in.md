---
title: Skip plug-in
category: 8
frontpage: false
comments: true
refs: 110
created-utc: 2019-01-01
modified-utc: 2020-01-08
---
<p>This plug-in is used to skip other plug-in instances when processing DNS requests.</p>

<p>This is typically used to apply one or more conditions (in the &quot;DNS Requests&quot; tab) to several other plug-ins at the same time.</p>

<p>This plug-in is different than other plug-ins in that it does not fetch or provide any DNS records directly.<br />
Instead it instructs Simple DNS Plus to skip some or all of the following plug-in instances (listed in the Simple DNS Plus Options dialog / Plug-Ins section) - when the conditions in the &quot;DNS Requests&quot; tab are met.</p>

<p>In the plug-in instance dialog / Plug-In Settings tab you can specify how many of the following plug-in instances to skip:</p>

<p><img src="img/186/1.png"  /></p>

<p>After creating and configuring the plug-in instance, use the &quot;Up&quot; and &quot;Down&quot; buttons in the Options dialog / Plug-ins section to position it immediately above the plug-in instance(s) that should be skipped:</p>

<p><img src="img/186/2.png" /></p>

<p>NOTE: This plug-in is new in Simple DNS Plus v. 5.2 and replaces the &quot;Domain Whitelist&quot; and &quot;Scheduler&quot; plug-ins from v. 5.1. Whitelisted domain names / dates/times can now be specified in the &quot;DNS Requests&quot; tab.</p>