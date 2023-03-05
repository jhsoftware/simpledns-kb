---
title: Regex Ignore plug-in
category: 8
frontpage: false
comments: true
refs: 110
created-utc: 2019-01-01
modified-utc: 2020-01-08
---
<p>With this plug-in, you can make Simple DNS Plus ignore all DNS requests for names that match a configurable <a href="http://en.wikipedia.org/wiki/regular_expression" target="_blank">regular expression</a>.</p>

<p>This could be used, for example, when the server is being bombarded with requests with a specific pattern (as is often seen in <a href="https://simpledns.plus/news/11">DNS amplification attacks</a>).</p>

<p>Another example is simple parental control - blocking domain names containing bad words.</p>

<p>Regular expressions are compiled when Simple DNS Plus loads the plug-in instance and are therefore evaluated very efficiently.</p>

<p>In the plug-in instance dialog / Plug-In Settings tab you can specify the regular expression to match:</p>

<p><img src="img/184/1.png" /></p>

<p>The sample in the screen shot would match and ignore any requests for domain names containing 'xxx'.</p>

<p>Keep in mind that the dot (.) character has special meaning in regular expressions (matches any character), so when matching multi-segment domains names, the domain name dots must be enclosed in square brackets [.].<br />
For example to match exactly &quot;something.example.com&quot;, the regular expression would be &quot;^something[.]example[.]com$&quot; without the quotes.<br />
The regular expression equivalent to the wildcard record name &quot;*.example.com&quot; is &quot;.*[.]example[.]com$&quot;.</p>