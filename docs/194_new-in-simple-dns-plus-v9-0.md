---
category: 17
frontpage: false
comments: true
vgroup: 7
vname: v. 9.0
vsort: 90
created-utc: 2021-09-10
modified-utc: 2021-09-18
---
# New in Simple DNS Plus (v. 9.0)

New features / updates in v. 9.0:

- [DNS over TLS (DoT) and DNS over HTTPS (DoH)](#dotdoh)
- [New "Bind SSL certificate" helper function](#bindssl)
- [New "HTTPS" DNS record type](#https-rectype)
- [Miscellaneous updates](#misc)
- [Breaking changes](#breaking)


### DNS over TLS (DoT) and DNS over HTTPS (DoH){#dotdoh}

DNS clients (like end user devices) can now send DNS queries to Simple DNS Plus via two new protocols - DNS over TLS (DoT) and DNS over HTTPS (DoH).

Classic DNS queries (UDP/TCP) are sent in plain text, which means anyone "listening" to the network can read them. This is a privacy issue, especially on the first leg between the user device and the resolving DNS server (think coffee shop wifi hotspot).

DNS over TLS (DoT) and DNS over HTTPS (DoH) encrypt DNS queries and responses - to keep user data private and secure.

DNS over TLS (DoT) and DNS over HTTPS (DoH) use the same type of encryption - TLS.
The difference is that DNS over HTTPS (DoH) uses an additional network layer (HTTP). This makes network packets a bit larger (the HTTP headers), but since it is standard HTTPS and use the standard HTTPS port (443), network packets are indistinguishable from regular HTTPS traffic (making censorship harder) - and it can use standard HTTP tools and services (like reverse proxy servers).
With DNS over TLS (DoT), network packets are smaller, but you need to open another port (853) making network packets easier to categorize, and it cannot use standard HTTP tools and services.

Operating systems and browsers have recently implemented support for this as well:

- **Windows 11** and **Windows Server 2022** support DoH.\
See how to enable: [Windows 11](/kb/199) / [Windows Server 2022](/kb/200).

- **MacOS** 11+ (BigSur) and **IOS** 14+ support both DoT and DoH.\
See how to enable: [MacOS](/kb/201) / [IOS](/kb/202).

- **Android** v. 9+ supports DoT.\
See how to enable: [Android](/kb/198)

- **Chrome OS** does not support DoT or DoH at the operating system level, but the Chrome browser running on Chrome OS supports DoH (see below).

- Some **Browsers** support DoH independently of the operating system (also works on earlier versions of Windows).\
See how to enable: [Chrome](/kb/195) / [Firefox](/kb/197) / [Edge](/kb/196).\
Note: Safari (on MacOS and IOS) does not have such a setting, but DoT/DoH can be enabled in these operating systems (see above).


In the Simple DNS Plus Options dialog, in the "DNS / Inbound requests" section, there is now a list of protocols / interfaces that Simple DNS Plus listens for DNS requests via / on.
These can be either UDP/TCP (the classic and only option in previous versions), DoT (DNS over TLS), and DoH (DNS over HTTPS):

![](/img/194/inbound-list.png)

The following options can be configured for DoT (DNS over TLS):

![](/img/194/inbound-dot.png)

The following options can be configured for DoH (DNS over HTTPS):

![](/img/194/inbound-doh.png)

In the DNS Look Up tool, it is now also possible to select DoT and DoH network protocols (in addition to UDP and TCP):

![](/img/194/lookup-protocol.png)

When the DoH protocol is selected, the DoH query URL and the HTTP method (GET or POST) can be specified, and you can select to use the DNS server and port from the query URL (or to specify them seperately):

![](/img/194/lookup-http.png)


**About SSL certificates**

Simple DNS Plus uses the Windows HTTP Server API for serving HTTP request - both for DoH (DNS over HTTPS) (see above) and for the HTTP API. This allows Simple DNS Plus to share port 80 / 443 with IIS and other applications.

The easiest way to setup SSL for DoH (and the HTTP API) in Simple DNS Plus is if you are also running an SSL based web-site on IIS on the same computer, and you configure DoH / the HTTP API to be served under the same host name as that site (but at a sub-path). This way you can just manage the SSL certificate in IIS.\
This also makes is easy to use and manage free Let's Encrypt certificates (and similar) with software like [win-acme](https://www.win-acme.com) or [Certify the web](https://certifytheweb.com).

DoT (DNS over TLS) requests are served directly (not via the Windows HTTP Server API), but can use the same SSL/TLS certificate as used by DoH (DNS over HTTPS) and IIS web-sites (fetched from the Windows certificate store).


### New "Bind SSL certificate" helper function{#bindssl}

If you are not running an SSL web-site with IIS on the same computer (see above), or if you are using a different SSL/TLS certificate for DoH (DNS over HTTPS) or the HTTP API, you will need to "bind" an SSL/TLS certificate to the host name (and port) used.

This can be done with a command line ("netsh http add sslcert hostnameport:..."), but requires first obtaining the "thumb print" ID of the certificate.

To make this a bit easier, we have added a helper dialog for this, which lets you simply pick the certificate from a drop down list.

A "Bind SSL certificate..." button can be found in the "Listen for inbound DNS requests" dialog with the "DoH" protocol selected (see above) and on the Options dialog / HTTP API page. 
Clicking this button will bring up the following dialog:

![](/img/194/bind-ssl.png)


### New "HTTPS" DNS record type{#https-rectype}

HTTPS-records allows browsers to efficiently obtain complete instructions for accessing a web-site for a domain name - including supported protocols (HTTP/1.1, 2, 3, etc.), ip address(es), port number, and public keys (all optional) - saving the browser from doing a number of DNS lookups and other protocol negotiation steps.

The Safari browser (on MacOS/IOS) has supported and requested this record type for a while now, and this appears to be [coming soon in Chrome](https://docs.google.com/document/d/1RX7LsepbdTrrvfKCIH104qZyhU0jo9ZN9meTAGHufSU/edit#heading=h.7nki9mck5t64) too.

The HTTPS record-type is defined in a ["Service binding and parameter specification via the DNS (DNS SVCB and HTTPS RRs)" draft](https://datatracker.ietf.org/doc/draft-ietf-dnsop-svcb-https) expected to become an official RFC soon.

To create a new HTTPS-record in Simple DNS Plus, right-click a zone in the left list in the DNS Records window, select "Other new record" from the pop-up menu, and then select "HTTPS". This will open the following dialog:

![](/img/194/https-record.png)

The DNS Look Up tool has also been updated to support the HTTPS record type:

![](/img/194/https-lookup.png)


### Miscellaneous updates{#misc}

- Now uses .NET Framework v. 4.8 (previously used v. 2.0), improving memory handling, performance, etc.
- Now uses context synchronization instead of locks, which results in fewer locked threads, freeing up system resources and improving overall system performance.
- GZIP support in the HTTP API (reduced network traffic).


### Breaking changes{#breaking}

- Supported Windows versions are now Windows 7 / Windows Server 2008 R2 and later. Older Windows versions are no longer supported.
- HTTP API v. 1 "/getconfig" and "/updateconfig" URLs removed. Use the HTTP API v. 2 "/options" URL instead (The HTTP API v. 1 is deprecated since Simple DNS Plus v. 7.0, and will eventually be removed completely).
- Removed UI support for obsolete record types: ATMA, ISDN,  MB, MG, MINFO, MR, NSAP, RT, and X25.
