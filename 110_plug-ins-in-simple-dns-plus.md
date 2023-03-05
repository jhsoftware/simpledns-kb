---
category: 8
frontpage: false
comments: true
refs: 31,72
created-utc: 2019-01-01
modified-utc: 2021-10-28
---
# Plug-ins in Simple DNS Plus

Simple DNS Plus has a plug-in system for providing additional services (such as DHCP) and for fetching DNS data from various sources such as databases and custom programs and scripts.

A list of available plug-ins is available at <https://simpledns.plus/plugins>

### Plug-ins user interface

From the main window, click the "Plug-Ins" button:

![](/img/110/1.png)

This will bring up the "Plug-In instances" dialog:

![](/img/110/2.png) 

Click the "Add..." button to add a new plug-in instance, the "Properties..." button to edit the selected plug-in instance,
the "Remove" button to remove the selected plug-in instance, the "Up" / "Down" button to change the order of the plug-in instances,
and the "Export" / "Import" button copy to the selected plug-in instance configuration to/from another Simple DNS Plus installation.

When you add or edit a plug-in instance, you will see the Plug-in instance dialog.

The first input field is the **Plug-in instance display name**, which is the name that will be displayed in the plug-in instances list, in the logs, and in the plug-in View tab.

**The "Plug-in Settings" tab**

The content of this tab is defined by the each individual plug-in type (this tab is not available for plug-ins which do not have any unique settings):

![](/img/110/3.png) 

**The "DNS Requests" tab**

On this tab you can limit which DNS requests are processed by the plug-in (this tab is not available for plug-ins which do not handle DNS requests).

![](/img/110/4.png)

By default all DNS requests are processed by the plug-in, but if the plug-in does a lot of work for each request (such as database lookups) it might by a good idea to limit this to specific domains, IP ranges, record types, etc. in order to optimize performance.

You can set "Process DNS requests" to either "Always", "Never", or "Only when...".\
With the "Only when..." option, you can configure a list of "rules" which determine what DNS requests are process or not.\
Available "rules" are:</p>

- Sender's IP address
	- is a specific IP address
	- is in a list of IP addresses / ranges / subnets
	- is an IPv4 address
	- is an IPv6 address
	- is listed in another plug-in
- Requested domain name
	- is a specific domain name (or wildcard name)
	- is in a list of domain names / wildcard names
	- is listed in another plug-in
- Requested record type is a specific type
- Reverse lookup IP address
	- is a specific IP address
	- is in a list of IP addresses / ranges / subnets
	- is an IPv4 address
	- is an IPv6 address
	- is listed in another plug-in
- Request is DNSBL lookup
- DNSBL lookup IP address
	- is a specific IP address
	- is in a list of IP addresses / ranges / subnets
	- is listed in another plug-in
- Sender requests recursion (RD)
- Server offers recursion (RA)
- Server is authroritative (AA) (Note: this only works for plug-ins listed AFTER [LOCAL DNS ZONES])
- Date/time is (see [this article](/kb/72))
- Rule from plug-in
- Sublist of rules

You can reverse the result of a selected rule by clicking the [Not] button.

Rules are evaluated in the listed order - you can re-arrage this using the Up/Down buttons.

**The "Listed IPs" tab**

On this tab you can set options for listed IP addresses (this tab is not available for plug-ins which do not "list" IP addresses).
(Note to developers: ths option is enabled for plug-ins that implement the IListsIPAddress interface).

![](/img/110/5.png)

- **Perform DNS recursion for IP addresses listed by this plug-in**\
When enabled, Simple DNS Plus will resolve DNS requests received from IP addresses listed by this plug-in - even if they are not listed in the Options dialog / DNS / Recursion section.

- **Whitelist IP addresses listed by this plug-in from all DNSBLs**\
When enabled, Simple DNS Plus will respond to any DNS request for A-records for names starting with a reversed IP address, that is listed by this plug-in, with a "name does not exist" error code.\
When a client computer (who's IP address is listed by this plug-in) sends an e-mail to a local e-mail server which is using this same Simple DNS Plus server, and this e-mail server looks up the sender's IP address (the client computer) in some DNSBL list, this option ensures that the result is always "not black listed".\
This can be useful because dynamic IP address ranges are often black listed as e-mail senders.


### Views

Some plug-ins will have their own "View" - a dockable sub-window of the Simple DNS Plus main window:

![](/img/110/6.png)

### Why plug-ins?

Users often ask us to implement different new features in Simple DNS Plus, and we are always very happy to get these suggestions.\
However some of the suggested features are things that only a smaller group of users would be interested in, and while it might be a really cool feature for those users, it might be a distraction to others.\
Of course adding a new feature also makes the software more complex and gives it a larger "attack surface".\
So we decided to implement a plug-in system, allowing us (and 3rd parties) to develop new features without cluttering the base product, and allowing users to select which of these features they want - or don't want.

Some of the benefits of this model are:

- Simpler user interface; settings for un-used plug-ins are not in the way.
- Allows us to implement new features without touching the core DNS server code.
- Less memory usage; only selected plug-in modules are loaded into memory.
- Smaller attack surface; evil doers can't attack plug-ins that aren't loaded.
- Great for asynchronous lookups; a plug-in lookup can run asynchronously not holding up other DNS requests.
- Allows users and 3rd parties to develop their own plug-ins (see [this article](/kb/31/))
- Allows separate distribution of selected plug-in modules and required libraries (reducing size of main installer).

### Open Architecture

The plug-in architecture open for users and 3rd parties interested in developing their own plug-ins. Please see [this article](/kb/31/) for details.