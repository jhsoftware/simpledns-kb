---
category: 20
frontpage: false
comments: true
created-utc: 1970-01-01
modified-utc: 2023-10-01
---
# DNS Blacklist Editor

The "DNS Blacklist Editor" is a freeware tool which can be used to create and/or maintain IP based DNS blacklists.

DNS blacklists (a.k.a. "RBL" and "DNSBL") are typically used with e-mail servers to
 filter out spam and other unwanted e-mails.  
For more details on this concept and its history, please see
[this Wikipedia article](http://en.wikipedia.org/wiki/Dnsbl).

### Screen Shot

![DNS Blacklist Editor - screen shot](/docs/img/208/dnsbleditor.png)

### Features

- **Opens most publicly available DNS blacklist files**  
This includes blacklist files formatted for Michael Tokarev's [RBLDNSD](http://www.corpit.ru/mjt/rbldnsd.html) (\*) and for D.J.Bernstein's [RBLDNS](http://cr.yp.to/djbdns/rbldns-data.html).  
(\*) This tool only implements a subset (the most commonly used features) of the RBLDNSD file format.  
Specifically it does not support name based lists, generic DNS record entries, nor "$" special entries (skipped if encountered).

- **Saves dataset files in the RBLDNSD format - optimized for file size**  
You can use files from this tool with RBLDNSD and any other software supporting this commonly used file format.  
Blacklist entries are grouped by return values so that each unique return value set (A/TXT) 
only appear once in the entire file, making the file as small as possible.

- **Find IP address**  
Quickly find blacklist entries containing a specific IP address, even if the IP address is in the middle of an IP subnet or IP range.  
*Not possible with generic text editor*.

- **Sorting**  
Sort the list by entry type (inclusion/exclusion), IP addresses, or return values (A/TXT).  
The QuickSort algorithm is used for sorting, so this is blazing fast even with millions of list entries.  
*Not possible with generic text editor*.

- **Merging**
One step function to merge all neighboring/overlapping entries with identical return values (A/TXT).  
This can reduce the size of some blacklists very dramatically.  
*Not possible with generic text editor</i>*.

- **Low memory usage**  
DNS blacklists often contain thousands of entries with identical TXT-record return values.  
This tool stores each unique TXT-record return value in memory only once.  
Depending on the list format, this may result in less than 20% memory usage compared to a generic text editor program.

- **Compiles data for the Simple DNS Plus [DNS Blacklist plug-in](https://simpledns.plus/plugin-blacklist)**  
Either use the Tools menu / Compile... function.  
Or compile from the command line (or as part of a script) by executing  
`DNSBLEDIT.EXE <input-file> <output-file>`


### Download

![download](/docs/img/208/todisk.gif)
Version 1.0 build 4 (May 18th 2009): [dnsbledit.exe (74 KB)](https://simpledns.plus/outbox/dnsbledit.exe)

### System Requirements

- Windows 98 / 2000 or later
- Microsoft .NET Framework 2.0 or later

### Licensing

The "DNS Blacklist Editor" software is freeware. It may be used and distributed free of charge in its original form.
