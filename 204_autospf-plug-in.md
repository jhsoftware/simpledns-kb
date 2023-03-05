---
category: 8
frontpage: false
comments: true
refs: 110
created-utc: 2021-10-25
modified-utc: 2021-10-27
---
# Auto SPF plug-in

This plug-in synthesizes missing SPF records (TXT) for local domains.

Using this plug-in you can provide SPF records for all domain names on your server without having to setup and maintain SPF-records separately for every single domain name.

**Important:** This plug-in only works when there are no TXT-records (of any kind) for the requested name in a local zone.

**Important:** This plug-in must be listed AFTER "[LOCAL DNS ZONES]" in the plug-in / query order list. Otherwise it will have no effect.

**Important:** The synthesized records are provided in responses to standard DNS lookups for TXT-records only - they are NOT provided in zone transfers to secondary DNS servers. Therefore you must configure this plug-in the same way on any secondary DNS servers for your domain names.

**What is SPF?**

SPF is a spam and phishing fighting method which uses DNS records to define which hosts are permitted to send e-mails for a domain.

When SPF enabled e-mail servers receive an inbound e-mail (via SMTP) they will lookup the DNS SPF-record (TXT type) for the domain name of the senders e-mail address in order to verify that sending e-mail server's IP address is permitted to send e-mail for that domain name.

For details more on SPF, please see <http://www.open-spf.org>

**How to use this:**

If you need to provide unique SPF-records for certain domain names, you can still setup individual SPF-records for those names. This function only kicks in when there are no SPF-records defined for a domain name already.

Consider using the value "v=spf1 -all" (meaning "these domains never send e-mail").

This forces you to have specific SPF-records for all domain names that send e-mails.

But it very effectively prevents spamming/phishing from all other domain names on your server - including common sub-names such as www.example.com which most users forget to setup SPF records for.

A good alternative to this is "v=spf1 mx -all" (meaning "these domains only send e-mail from the mail server listed in their MX-record").

This way any domain name that has an [MX-record](https://simpledns.plus/help/mx-records) is covered automatically.

And sub-names such as www.example.com which typically do not have MX-records are still excluded.

In addition to checking the domain name part of the sender's e-mail address, some e-mail servers also perform SPF checks on the SMTP session HELO/EHLO greeting host name.

Therefore always make sure that your e-mail server is configured to use a correct host name (like "mail.example.com") in the HELO/EHLO greeting, and that an A- and/or AAAA-record exists for this host name in DNS.

And when using this option, make sure that the SPF-record data is also valid for the HELO/EHLO host name used by your e-mail server, or define a specific SPF-record for the HELO/EHLO name in the zone where this belongs (this will override the automatic SPF record).

Note that the default data "v=spf1 mx -all" will fail such a test if no MX-record exists for your HELO/EHLO name.

For example, if your domain name is "example.com" and your mail server is named "mail.example.com" (and uses this in HELO/EHLO greetings), you would probably only have an MX-record for "example.com" - not for "mail.example.com", and therefore "v=spf1 mx -all" fails to validate "mail.example.com".

Instead you could use "v=spf1 ip4:1.2.3.4 -all" (where 1.2.3.4 is the IP address of your mail server), which would work for both types of tests.

**Note:** This plug-in does not provide SPF records for domain names starting with the underscore (\_) character to avoid collision problems with special purpose names such as "\_domainkey".

**Note:** In Simple DNS Plus v. 9.0 and earlier, this functionality used to be built-in - configurable in the Options dialog / DNS / Local Zones / Automatic SPF section.
