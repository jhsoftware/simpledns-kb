---
category: 19
frontpage: false
comments: true
created-utc: 2021-09-19
modified-utc: 2021-09-19
---
# How to enable DNS over TLS (DoT) / DNS over HTTPS (DoH) in IOS v. 14+

DNS over TLS (DoT) / DNS over HTTPS (DoH) are ways to encrypt DNS queries and responses between a user's device and the resolving DNS server. For more on this see [New in Simple DNS Plus v. 9.0](/kb/194).

Configuring this in IOS (v. 14 or later), requires installing a "configuration profile" file (a file with a ".mobileconfig" extenion), containing data about the DNS server(s) to use.

Various DNS service providers (such as Google, Cloudflare, etc.) provide such files on their web-sites.

You can generate such a file for your own DNS servers at <https://simpledns.plus/apple-dot-doh>

Note: It is important that you do this in the **Safari browser** as it may not work with other browsers.

Enter you company name, select the protocol (DoT or DoH), enter you DNS server host name or query URL, and the DNS server IP addresses, click the Download button:

![](/img/202/ipad1.png)

Safari will prompt you "This website is trying to download a configuration profile. Do you want to allow this?" - click "Allow":

![](/img/202/ipad2.png)

Safari will prompt you "Profile downloaded". Click "Close":

![](/img/202/ipad3.png)

From the home screen open the Settings app:

![](/img/202/ipad4.png)

Click "Profile Downloaded":

![](/img/202/ipad5.png)

In the "Install Profile" dialog, click "Install":

![](/img/202/ipad6.png)

Enter your passcode and click "Done":

![](/img/202/ipad7.png)

And in the final Warning dialog, click "Install":

![](/img/202/ipad8.png)

