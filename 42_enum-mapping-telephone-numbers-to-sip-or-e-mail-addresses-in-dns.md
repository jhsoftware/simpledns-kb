---
category: 7
frontpage: false
comments: true
refs: 112
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# ENUM - Mapping telephone numbers to SIP or e-mail addresses in DNS

"ENUM" is a method of mapping traditional telephone numbers to SIP, SMTP (e-mail), and other internet services.

This is done using DNS "NAPTR" records under the "e164.arpa" domain.  
Telephone numbers are mapped by reversing the digits of a phone number starting with the international dialing code (1=USA/Canada, 44=U.K., 45=Denmark, etc.) and inserting dots between all digits.  
For example the phone number 12345678 in Denmark (45) would be "8.7.6.5.4.3.2.1.5.4.e164.arpa".

The "e164.arpa" domain is sub-delegated by RIPE (see [http://www.ripe.net/enum/](http://www.ripe.net/enum/){target=_blank}) to authorities in each country.  
Note: Not all countries are delegated yet at this time.

To host ENUM records for your phone numbers, the e164.arpa sub-domain for your phone numbers would first need to be delegated to your DNS servers by the local authority in your country (typically whoever assigns phone numbers to phone companies).

To setup NAPTR records in Simple DNS Plus, in the main window click the "Records" button, then right-click a zone in the left list, select "Other new record...", and then "NAPTR record".

For example:

![](img/42/1.png)

For specifics and various configuration examples see [RFC2916](http://www.rfc-editor.org/rfc/rfc2916.txt) and [RFC3761](http://www.rfc-editor.org/rfc/rfc3761.txt).

For more information about ENUM, see [http://www.enum.org/faq.html](http://www.enum.org/faq.html){target=_blank}

