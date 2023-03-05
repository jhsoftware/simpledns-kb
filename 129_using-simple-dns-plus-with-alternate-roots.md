---
category: 11
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2021-09-29
---
# Using Simple DNS Plus with alternate roots

Most DNS servers (including Simple DNS Plus) are by default configured with a "root file" (a.k.a. "hints file") pointing to the standard DNS root servers - which are controlled by [ICANN](http://www.icann.org).\
This gives you access to the standard Internet name space which includes .com, .net, .org, two letter country codes, etc.

There are however "alternate root operators" which provide access to other "non-standard" top level domain names (TLDs).

You don't need any special configuration in Simple DNS Plus to host these domain names.\
But to resolve such domain names not hosted on your server (and give your users access to them), you need replace the "named.root" file located in the Simple DNS Plus application data directory - typically "C:\ProgramData\JH Software\Simple DNS Plus" (note that "c:\ProgramData" is hidden).\
Most alternate root operators publish a "root file" usually named "named.root" or "named.cache" for download.\
Simply download this file, name it "named.root", and place it in the the directory mentioned above.\
Then select "Reload DNS Records" from the "Tools" menu.

If you want to go back to the original "named.root" file, just delete the current "named.root" file and restart Simple DNS Plus. It will then automatically recreate the original.\
Or you can download it from here: <ftp://ftp.rs.internic.net/domain/named.root>

There are several alternate root operators - see more at <https://en.wikipedia.org/wiki/Alternative_DNS_root> 

**PLEASE NOTE:**

"alternate root" domain names are not recognized by ICANN, which means that the majority of Internet users will not have access to any site you host under one of these domain names.

If you register a domain name with an "alternate root operator" there is a risk that ICANN will eventually commission the same top level name, and you may have to register the domain again or loose it to someone else.

The ICANN / standard DNS root has 13 different servers spread around the globe.\
The entire Internet depends on these 13 servers, so they are operated with some measure of redundancy and security.\
Some alternate root operators have solid setups as well, but some do not.\
If your DNS server cannot reach any of the root servers listed in the "named.root" file, then it cannot resolve any outside domain names.\
So before replacing your "named.root" file, you may want to check the number of servers listed in the new file, and check where these servers are located etc.