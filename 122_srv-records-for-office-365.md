---
category: 7
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# SRV records for Office 365

At the Office 365 support website, there is an article about setting up DNS records for your domain name in connection with Office 365.

See <https://support.office.com/en-us/article/Create-DNS-records-at-any-DNS-hosting-provider-for-Office-365-7b7b075d-79f9-4e37-8a9e-fb60c1d95166>

The section about SRV-records (for Lync) can be a bit confusing because of the way and order in which the data fields are listed.

![](img/122/1.png)

In Simple DNS Plus, adding these records would look like this:

![New SRV-record 1](img/122/2.png)

![New SRV-record 2](img/122/3.png)

> [!Note] The "Service" and "Protocol" fields are NOT locked to the drop-down choices. You can type any value into these.

And back in the record list:

![record list](img/122/4.png)