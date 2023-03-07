---
category: 7
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# Does Simple DNS Plus support split-horizon / split-view / BIND views?

Some DNS server implementations have a feature where you can have different versions of a zone served to different clients based on which IP address the DNS request originates from. This is often referred to split-horizon, split-view, or BIND views.

Very often this feature is used to handle the situation where clients on a private LAN need to access a server using a private IP address and clients from the Internet need to access the same server using a public IP address.

Simple DNS Plus does not have the ability to serve different versions of the same zone, but it does have a feature that makes it easy to serve private/public IP addresses as in the case above. This called the "NAT IP Alias" feature, and is found in the Options dialog / DNS / NAT IP Alias section:

![](img/36/1.png)

With the configuration show above - any request from 192.168.0.xxx for a host record that points to 1.2.3.4 - will be served a "cloned" host record pointing to 192.168.0.4.

So rather than maintaining duplicates of one or more zones, you can simply configure this in one place.

