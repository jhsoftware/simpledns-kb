---
category: 14
frontpage: false
comments: true
refs: 153
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# NSLOOKUP: *** Can't find server name... / Default Server: UnKnown

NSLOOKUP is a command line tool which comes with most operating systems and is used for querying DNS servers.

When NSLOOKUP starts, before anything else, it checks the computer's network configuration to determine the IP address of the DNS server that the computer uses.  
Then it does a reverse DNS lookup on that IP address to determine the name of the DNS server.

If reverse DNS for that IP address is not setup correctly, then NSLOOKUP cannot determine the name associated with the IP address.  
On Windows Vista/2008, it then says "Default Server: UnKnown".  
On earlier Windows versions, it displays the error message "*** Can't find server name for address ...".

This does NOT indicate a problem with the actual domain name that you are trying to look up.  
It only means that there is no reverse DNS name for the DNS server IP address, which in most cases may not be a problem at all.

To fix this you need to properly configure the reverse zone for the IP address of the DNS server, and make sure that the reverse zone is properly delegated to the server by your IP provider. See the reference article below for more details.

To create a reverse zone in Simple DNS Plus, click the "Records" button, select "New" -&gt; "Zone", select "Reverse Zone...", and follow the prompts.

