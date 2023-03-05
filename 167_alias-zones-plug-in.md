---
category: 8
frontpage: false
comments: true
refs: 110
created-utc: 2019-01-01
modified-utc: 2020-01-07
---
# Alias Zones plug-in

This plug-in provides DNS records for one or more "virtual" zones by cloning records from another zone (local or remote).

This is an easy way to host many domain names that have the exact same records (except for their zone names).

On the "Plug-In Settings" tab, enter the following settings (explained below the image):

![](img/167/1.png)

- **Alias zone names**  
A list of domain names representing the "virtual zones".
- **Clone from zone**  
The zone name to query for a response to be cloned. This can be a local zone or a domain hosted elsewhere.

When this plug-in processes a DNS request, it first checks if the requested name matches, or is a sub-name of, one of the names listed in the "Alias zones names" list - using the longest match.  
Then a new DNS request is generated for the requested domain name less the matched alias zone name + the "Clone from zone" name.  
This new request is then resolved (from local zones, other plug-ins, resolved from Internet, etc.) and the resulting response is cloned - replacing all instances of the "Clone from zone" name with the alias zone part of the requested name.

For example, say the plug-in is configured as in the image above ("Alias zones names" is "example.net" / "example.org" and the "Clone from zone" name is "example.com"), and the plug-in receives a DNS request for "host5.example.net".  
A new request is then generated for "host5.example.com" ("host5.example.net" less "example.net" + "example.com").  
When this new request is resolved, all instances of "example.com" in the response are replaced with "example.net" so that this matches the original request.

