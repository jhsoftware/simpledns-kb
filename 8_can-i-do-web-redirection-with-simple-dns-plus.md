---
title: Can I do web redirection with Simple DNS Plus?
category: 16
frontpage: false
comments: true
refs: 179,148
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<p>You can do simple redirection with CNAME (alias) records from one domain to another.</p>
<p>However, if the target web-server runs multiple web-sites on the same IP address (and most do), then it is not enough to simply point another name to it via DNS. You also need to configure the web-site on that web-server to accept the additional domain name.<br />
When redirecting with a CNAME record, the web-server will still only "see" the original domain name entered into the web-browser address field.</p>
<p>Also, a CNAME record can only point to another domain name - not a sub-directory or a specific web-page.</p>
<p>So i f you do not have access to configure the target web-server, or if you want to redirect to a sub-directory or a specific web-page, then you will need to use HTTP redirection instead.<br />
You can do this with the <a href="https://simpledns.plus/plugin-httpredir">HTTP Redirector plug-in</a> or by some type of server side script on a web-server.</p>