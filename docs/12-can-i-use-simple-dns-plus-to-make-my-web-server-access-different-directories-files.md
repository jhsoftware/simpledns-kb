---
category: 16
frontpage: false
comments: true
refs: 145,144
created-utc: 2019-01-01
modified-utc: 2021-11-01
---
# Can I use Simple DNS Plus to make my web-server access different directories / files on my computer for different domain names? (Sometimes referred to as "virtual hosting")

Simple DNS Plus is part of the solution, but you also need a web-server that supports this.

A URL consists of 3 parts: Protocol (http://), Domain Name (www.domain.com), and Path/File (/somedir/page.htm).

The Protocol tells the browser how to communicate with the web server.  
The Domain Name is used to locate the IP address of the web server (through DNS).  
The Path/File is sent to the web server as part of the http request.

When a browser opens a web-page, it first locates the web server's IP address through DNS. This DNS request only contains the Domain Name - not the Path/File.  
Second it connects to the web server and sends a HTTP request, which includes both the Domain Name and Path/File.

If the web server supports different domain names, it then serves the page from a directory according to the domain name supplied in the request.

This is supported directly by Microsoft IIS (Internet Information Server) for all current Windows versions - [click here to see how](/kb/144/virtual-hosting-with-iis-internet-information-services)

There are also several free / inexpensive web servers available that do support it directly on all Windows platforms. For example:

"Apache" [http://httpd.apache.org/](http://httpd.apache.org/){target=_blank}  
This is the "original" and still the most widely used web-server on the Internet.  
It is free (or OpenSource), but because it uses text configuration files instead of a GUI, it is probably not the most user friendly choice on Windows.  
And it is also supported directly by Apache.  
For information about virtual hosting with Apache, see  
[https://httpd.apache.org/docs/2.4/vhosts/name-based.html](https://httpd.apache.org/docs/2.4/vhosts/name-based.html){target=_blank}

"Abyss web server" [http://www.aprelium.com](http://www.aprelium.com){target=_blank}

