---
title: ENUM - Mapping telephone numbers to SIP or e-mail addresses in DNS
category: 7
frontpage: false
comments: true
refs: 112
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<p>"ENUM" is a method of mapping traditional telephone numbers to SIP, SMTP (e-mail), and other internet services.</p>
<p>This is done using DNS "NAPTR" records under the "e164.arpa" domain.<br />
Telephone numbers are mapped by reversing the digits of a phone number starting with the international dialing code (1=USA/Canada, 44=U.K., 45=Denmark, etc.) and inserting dots between all digits.<br />
For example the phone number 12345678 in Denmark (45) would be "8.7.6.5.4.3.2.1.5.4.e164.arpa".</p>
<p>The "e164.arpa" domain is sub-delegated by RIPE (see <a href="http://www.ripe.net/enum/" target="_blank">http://www.ripe.net/enum/</a>) to authorities in each country.<br />
Note: Not all countries are delegated yet at this time.</p>
<p>To host ENUM records for your phone numbers, the e164.arpa sub-domain for your phone numbers would first need to be delegated to your DNS servers by the local authority in your country (typically whoever assigns phone numbers to phone companies).</p>
<p>To setup NAPTR records in Simple DNS Plus, in the main window click the "Records" button, then right-click a zone in the left list, select "Other new record...", and then "NAPTR record".</p>
<p>For example:</p>
<p> <img height="506" alt="1217.png" src="img/42/1.png" width="425" /></p>
<p>For specifics and various configuration examples see <a href="http://www.rfc-editor.org/rfc/rfc2916.txt">RFC2916</a> and <a href="http://www.rfc-editor.org/rfc/rfc3761.txt">RFC3761</a>.</p>
<p>For more information about ENUM, see <a href="http://www.enum.org/faq.html" target="_blank">http://www.enum.org/faq.html</a></p>