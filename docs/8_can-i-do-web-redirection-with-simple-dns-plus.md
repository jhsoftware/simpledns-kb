---
category: 16
frontpage: false
comments: true
refs: 179,148
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# Can I do web redirection with Simple DNS Plus?

You can do simple redirection with CNAME (alias) records from one domain to another.

However, if the target web-server runs multiple web-sites on the same IP address (and most do), then it is not enough to simply point another name to it via DNS. You also need to configure the web-site on that web-server to accept the additional domain name.  
When redirecting with a CNAME record, the web-server will still only "see" the original domain name entered into the web-browser address field.

Also, a CNAME record can only point to another domain name - not a sub-directory or a specific web-page.

So i f you do not have access to configure the target web-server, or if you want to redirect to a sub-directory or a specific web-page, then you will need to use HTTP redirection instead.  
You can do this with the [HTTP Redirector plug-in](https://simpledns.plus/plugin-httpredir) or by some type of server side script on a web-server.

