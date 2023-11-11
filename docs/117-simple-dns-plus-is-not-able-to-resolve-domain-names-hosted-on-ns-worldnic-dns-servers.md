---
category: 14
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# Simple DNS Plus is not able to resolve domain names hosted on ns##.worldnic DNS servers. What could be wrong?

Network Solutions' ns##.worldnic.com DNS servers occasionally respond incorrectly to standard DNS requests (sets the response TC flag even when the response isn't truncated).

This causes older versions of Simple DNS Plus not to be able to resolve domain names hosted on those servers.

Simple DNS Plus version 4.00.05 and later is able to resolve these names when this happens without any problems.  
Make sure you are using this or a newer version.

