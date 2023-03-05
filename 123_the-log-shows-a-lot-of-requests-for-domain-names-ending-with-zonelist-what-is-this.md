---
category: 7
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# The log shows a lot of requests for domain names ending with "_zonelist". What is this?

These requests typically come from a Simple DNS Plus server configured as a "super slave" server in order to automatically update its list of secondary zones.  
This is a special feature of Simple DNS Plus to fully automate secondary servers.  
To work correctly, this must be activated in the Options dialog / DNS / Local Zones / Zone Transfers section on both "super master" and "super slave" servers, so they "know" each other.

See also: [Can I use the "Super Master/Slave" feature with other DNS servers?](/kb/13/can-i-use-the-super-master-slave-feature-with-other-dns-servers)

