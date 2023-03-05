---
category: 19
frontpage: false
comments: true
created-utc: 2021-09-19
modified-utc: 2021-09-19
---
# How to enable DNS over TLS (DoT) / DNS over HTTPS (DoH) in MacOS v. 11+

DNS over TLS (DoT) / DNS over HTTPS (DoH) are ways to encrypt DNS queries and responses between a user's device and the resolving DNS server. For more on this see [New in Simple DNS Plus v. 9.0](/kb/194).

Configuring this in MacOS (v. 11 / BigSur or later), requires installing a "configuration profile" file (a file with a ".mobileconfig" extenion), containing data about the DNS server(s) to use.

Various DNS service providers (such as Google, Cloudflare, etc.) provide such files on their web-sites.

You can generate such a file for your own DNS servers at <https://simpledns.plus/apple-dot-doh>

Enter you company name, select the protocol (DoT or DoH), enter you DNS server host name or query URL, and the DNS server IP addresses, click the Download button, and click/open the downloaded file:

![](/img/201/mac1.png)

A "Profile installation" message should appear:

![](/img/201/mac2.png)

Open the system menu, and select "System Preferences...":

![](/img/201/mac3.png)

Go to "Profiles":

![](/img/201/mac4.png)

The downloaded profile should appear. Click the "Install..." button:

![](/img/201/mac5.png)

Click "Install" in the confirmation dialog:

![](/img/201/mac6.png)

You will be prompted to enter your password to confirm, and then the profile is installed.