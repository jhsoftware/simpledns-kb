---
title: Regular Expressions plug-in
category: 8
frontpage: false
comments: true
refs: 110
created-utc: 2019-01-01
modified-utc: 2020-01-08
---
<p>This plug-in uses Regular Expressions (see <a href="http://en.wikipedia.org/wiki/regular_expression" target="_blank">standard syntax in Wikipedia</a>) to pair host domain names to IP addresses.<br />
This gives you much more flexibility than simple wildcard records.</p>

<p>Here is a simple example:</p>

<p><img src="img/185/1.png"  /></p>

<p>This will cause requests for anything under &quot;mydomain.com&quot; starting with &quot;asia&quot; to resolve to IP 1.1.1.1.<br />
That would include for example &quot;asia123.mydomain.com&quot;.</p>

<p>Requests for &quot;europe...&quot; resolve to 2.2.2.2, requests for &quot;america...&quot; resolve to 3.3.3.3, and anything else under &quot;mydomain.com&quot; resolves to 4.4.4.4.</p>

<p>Regular expressions are compiled when the server modules loads them and therefore run very efficiently in Simple DNS Plus.</p>

<p>NOTE: Keep in mind that the dot (.) character has special meaning in regular expressions (matches any character), so when matching multi-segment domains names, the domain name dots must be enclosed in square brackets [.].<br />
For example to match exactly &quot;something.example.com&quot;, the regular expression would be &quot;^something[.]example[.]com$&quot; without the quotes.<br />
The regular expression equivalent to the wildcard record name &quot;*.example.com&quot; is &quot;.*[.]example[.]com$&quot;.</p>