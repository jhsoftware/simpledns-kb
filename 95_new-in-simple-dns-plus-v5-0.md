---
category: 17
frontpage: false
comments: true
vgroup: 7
vname: v. 5.0
vsort: 50
refs: 101,100,110,116,98,102,99,97,96,113,3
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# New in Simple DNS Plus (v. 5.0)

### Faster!

The DNS engine and internal data structures have been further optimized, so resolving and serving DNS requests is generally much faster.

Program startup / loading zones is almost instantaneous even with +100,000 zones because of a new boot file format, and a "load on demand" option for both primary and secondary zones.

Managing large zone lists and/or large zones in the GUI is extremely fast compared to earlier versions.  
The DNS Records window now opens and is ready for use in 1-2 seconds even with +100,000 zones, and selecting a zone with +100,000 DNS records also takes just a few seconds.

Master/Slave synchronization with many zones is also much more efficient because serial numbers for all zones can now be verified in a single transaction (instead of one per zone).

And because v. 5.0 is 100% .NET managed code, it runs as a native 64 bit application on 64 bit Windows/CPUs = SPEED!
    
### IPv6

Simple DNS Plus v. 5.0 has full support for IPv6 - the next Internet Protocol version.

It has an option to control protocol preference (IPv4 / IPv6) on dual-stack computers, and it can even act as IPv6-to-IPv4 or IPv4-to-IPv6 forwarder.

### IDNs (internationalized domain names)

In version 5.0 you can enter domain names with native characters directly (no punycode conversion needed), and have an option to display native character or punycoded domain names anywhere in the user interface, and quickly switch between these modes.

### New plug-in system

For fetching host record data from various sources such as databases and custom programs and scripts.

Several plug-ins will be provided in the default installation, additional plug-ins will be available for download later, and the plug-in system will be completely open and documented for 3rd parties and users to develop their own.  
[More details...](/kb/110/plug-ins-in-simple-dns-plus)

### MS SQL Server plug-in

For fetching host records (A / AAAA) and reverse records (PTR) from a Microsoft SQL Server.  
Works with the free Express version as well as full versions of MS SQL Server.  
[More Details...](https://simpledns.plus/plugin-mssql)

### Regular Expressions plug-in

Setup your own matching rules using Regular Expressions to pair host domain names to IP addresses.  
This gives you much more flexibility than simple wildcard records.  
[More details...](https://simpledns.plus/plugin-regex)

### Quick Zone Templates

The "Quick Zone Wizard" (formerly "Quick Domain Wizard") is template based, and supports multiple templates through a drop-down menu on the Quick button. Templates can simply be static standard RFC based zone files, but they can also become "active" by adding ASP style tags (`<%...%>`), VB.NET code, and custom input fields.  
[More details...](/kb/116/setting-up-quick-zone-templates)

### More powerful DNS zone and record management

The "DNS Records" module has new export functions, new bulk update wizard functions, multi-record copy/paste, and much more...

### Many new settings for more fine grained control

The Options dialog has been re-arranged and has a bunch of new settings for fine tuning your DNS server.


### New HTTP API commands and parameters

The HTTP API has been extended to enable more powerful and easier integration between Simple DNS Plus and your solutions through simple scripting or programming.

### Enhanced DNS Lookup module

The "DNS Lookup" module can now do lookups over TCP (virtual circuit), supports UDP payload sizes (EDNS0), and more...

### Enhanced Cache Snapshot module

The "Cache Snapshot" module loads data much faster, has a new search function, and more...

### IP address Look Up / Favorites

All IP address entry fields now have a look up button and a favorites button next to them.

The look up button makes it easy to enter the IP addresses of any existing host name.

The favorites button makes it easy to use and maintain a simple list of often used  IP addresses.

![](img/95/1.png)

### Works with Windows Server 2008

Simple DNS Plus v. 5.0 runs on all Windows versions and editions from Windows 98 and later including Windows Server 2008.  
(Previous versions may not run on and are not supported on Windows Server 2008).

### New RFC and draft support

- [RFC 2671](http://www.rfc-editor.org/rfc/rfc2671.txt) - Extension Mechanisms for DNS (EDNS0)
- [RFC 3597](http://www.rfc-editor.org/rfc/rfc3597.txt) - Handling of Unknown DNS Resource Record (RR) Types
- [RFC 4408](http://www.rfc-editor.org/rfc/rfc4408.txt) - Sender Policy Framework (SPF)
- [draft-ietf-dnsop-default-local-zones](http://tools.ietf.org/html/draft-ietf-dnsop-default-local-zones) - Locally-served DNS Zones

### .NET

Simple DNS Plus has been migrated to the [Microsoft .NET platform](http://www.microsoft.com/net/) (runs under .NET Framework 2.0 and later).
This provides some major benefits including better performance and more secure code, and it enables many of the other new features such as IPv6 and IDNs.
