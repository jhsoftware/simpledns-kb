---
category: 8
frontpage: false
comments: true
refs: 110
created-utc: 2019-01-01
modified-utc: 2020-01-08
---
# Regex Ignore plug-in

With this plug-in, you can make Simple DNS Plus ignore all DNS requests for names that match a configurable [regular expression](http://en.wikipedia.org/wiki/regular_expression){target=_blank}.

This could be used, for example, when the server is being bombarded with requests with a specific pattern (as is often seen in [DNS amplification attacks](https://simpledns.plus/news/11)).

Another example is simple parental control - blocking domain names containing bad words.

Regular expressions are compiled when Simple DNS Plus loads the plug-in instance and are therefore evaluated very efficiently.

In the plug-in instance dialog / Plug-In Settings tab you can specify the regular expression to match:

![](img/184/1.png)

The sample in the screen shot would match and ignore any requests for domain names containing 'xxx'.

Keep in mind that the dot (.) character has special meaning in regular expressions (matches any character), so when matching multi-segment domains names, the domain name dots must be enclosed in square brackets [.].  
For example to match exactly "something.example.com", the regular expression would be "^something[.]example[.]com$" without the quotes.  
The regular expression equivalent to the wildcard record name "*.example.com" is ".*[.]example[.]com$".

