---
category: 11
frontpage: false
comments: true
refs: 148,179
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# Can I specify a TCP/IP port number for my web-server in DNS? (Other than the standard port 80)

Unfortunately the standard DNS A-record (domain name to IP address) used by web-browsers to locate web-servers does not include a port number.  
Web-browsers use the URL protocol prefix (http://) to determine the port number (http = 80, https = 443, ftp = 21, etc.) unless the port number is specifically typed in the URL (for example "https://simpledns.plus:5000" = port 5000).

If you need to run a web-server on a TCP/IP port other than 80, the visitor will need to specify this port directly in the URL (see above), or you need to point the DNS A-record to the IP address of a different web-server (running on port 80) which redirects your domain name to your own server IP address and port number.  
For details, please see the reference articles below.

