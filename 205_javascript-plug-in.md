---
category: 8
frontpage: false
comments: true
refs: 110
created-utc: 2021-10-25
modified-utc: 2021-10-27
---
# JavaScript plug-in

Write your own custom logic for DNS query processing in JavaScript.

Your script code runs efficiently via Google's V8 JavaScript engine (the same that powers Chrome and Node.js).

There are 4 variations of the plug-in:
- **Host lookup**\
Executes a custom JavaScript function to look up a (single) IP address for a host name.
- **Reverse lookup**\
Executes a custom JavaScript function to look up the host name for an IP address.
- **TXT lookup**\
Executes a custom JavaScript function look up a TXT-record value for a host name.
- **Answer lookup**\
Executes a custom JavaScript function to do a DNS lookup returning multiple DNS records and/or special response properties (AA flag / RCode value).\
**NOTE:** The "Answer lookup" variation requires an **Unlimited Zones license** for Simple DNS Plus.

### User interface

On the "Plug-In Settings" tab, enter the following settings (explained below the image):

![](/img/205/settings.png)

- **Where to store JavaScript code**\
The first option "With the plug-in configuration in the Simple DNS Plus database" makes management and backup easier, while the second option "In a separate file" makes it possible to edit the file in another program - like Visual Studio Code to get JavaScript syntax highlighting etc.
- **Enable debugging**\
Check this and specify a port number to enable debugging (see "Debugging" section below).


### Writing scripts

The JavaScript code (that you write) must include a `Lookup` function, which is called by Simple DNS Plus for each DNS query. Your script may contain other functions as well, but the `Lookup` function is required.

Any script code outside functions (at the root of the script document) is executed at the first request. You can use this to initialize variables such as counters etc.

The signature of the `Lookup` function varies with each plug-in variation, as does the format of the return value.

If the plug-in does not have an answer for the request, it must return `null`. 

Each `Lookup` function has a `context` parameter, which is an object with the following properties:

- `fromip` (string)\
The IP address that the query originated from.
- `qname` (string)\
The domain name requested.
- `qtype` (string)\
The query / record type - such as "MX".
- `rd` (boolean)\
The RD flag (recursion desired) from the query.
- `ra` (boolean)\
Indicating if the server (Simple DNS Plus) will provide recursion to the client (ra=recursion available).
- `aa` (boolean)\
Indicating if the server (Simple DNS Plus) is authoritative for `qname` - meaning that `qname` belongs to a local DNS zone.\
Note: This property is only set for plug-ins listed after [LOCAL DNS ZONES] in the Plug-in / query order list.


**Host lookup**

Function signature: `Lookup(name, ipv6, context)`\
Where `name` (string) is the domain name queried, `ipv6` (boolean) indicates if an IPv6 address was requested (request for AAAA-record) or not (IPv4 address / request for A-record).

Return value: May be either a string with the resulting IP address (TTL defaults to zero), or an object with a `value` (string) property representing the resulting IP address, and a `ttl` (number) property representing the TTL (Time To Live) value in seconds - for example `{ value: '1.2.3.4', ttl: 300 }`.

Sample code: 

```
function Lookup(name, ipv6, context) {
    if(name !== 'example.com') return null;
    return { value: ipv6 ? '1234::1234' : '1.2.3.4', ttl: 300 };
}
```

**Reverse lookup**

Function signature: `Lookup(ip, context)`\
Where `ip` (string) is the IP address that was queried.

Return value: May be either a string with the resulting host name (TTL defaults to zero), or an object with a `value` (string) property representing the resulting host name, and a `ttl` (number) property representing the TTL (Time To Live) value in seconds - for example `{ value: 'server1.example.com', ttl: 300 }`.

Sample code: 

 ```
 function Lookup(ip, context) {
    if(ip !== '1.2.3.4') return null;
    return { value: 'example.com', ttl: 300 };
}
 ```

**TXT lookup**

Function signature: `Lookup(name, context)`\
Where `name` (string) is the domain name queried.

Return value: May be either a string with the resulting TXT-record value (TTL defaults to zero), or an object with a `value` (string) property representing the resulting TXT-record value, and a `ttl` (number) property representing the TTL (Time To Live) value in seconds - for example `{ value: 'This is an example', ttl: 300 }`.

Sample code:

```
function Lookup(name, context) {
    if(name !== 'example.com') return null;
    return { value: 'Example text', ttl: 300 };
}
```


**Answer lookup**

Function signature: `Lookup(context)`

Return value: An object with the following properties (all optional):

- `aa` (boolean)\
Sets response AA flag (authoritative answer). Defaults to server value (queried name belongs in local DNS zone or not).
- `rcode` (number or string)\
Set response RCode value (response code). Defaults to zero / NoError.\
Valid string values are: "noerror" (=0), "formerr" (=1),"servfail" (=2), "nxdomain" (=3), "notimp" (=4), "refused" (=5), "ignore" (=255).\
The special value "ignore" / 255 indicates to Simple DNS Plus that the query should be ignored / not responded to.
- `answer` (array)\
List of DNS records (see below) in the response Answer section.
- `authority` (array)\
List of DNS records (see below) in the response Authority section.
- `additional` (array)\
List of DNS records (see below) in the response Additional section.

DNS records in the `answer`, `authority`, `additional` array properties are objects with the following properties:
 
- `name` (string)\
Domain name .
- `type` (string or number)\
DNS record type - such as "MX".
- `ttl` (number)\
TTL (Time to Live) value in seconds.
- `data` (string)\
Record data in standard zone file format. For example for an MX record: `"10 smtp.example.com."`.

Sample code:

```
function Lookup(context) {
  if(context.qname !== 'example.com') return null;
  if(context.qtype !== 'MX') return null;
  return { aa: true,
           answer: [
             { name: context.qname, type: 'MX', ttl: 300, data: '10 server1.example.com.' },
             { name: context.qname, type: 'MX', ttl: 300, data: '20 server2.example.com.' }
           ]};
}
```

### console.log

Just like in a browser, you may use `console.log('some text')` to output debugging information. The output will appear in the Simple DNS Plus log.


### Debugging

When debugging is enabled (see "User interface" section above), you can connect a debugger which supports the "V8 Inspector Protocol". For example the Chrome browser developer tools.

In Chrome, open the address <chrome://inspect>, select the "Devices" section (should be selected by default), and look for "sdnsmain.exe", and click the "inspect" link after this.

Note that if you used a debugging port number other than 9222, then you need to add this ("localhost:&lt;port&gt;") using the "Configure..." button. 

![](/img/205/chrome1.png)

This will open a "DevTools" Window.

When a debugging event happens (like an exception), you can inspect the code, variable values, call stack etc. just like when debugging JavaScript in a web-page in the Chrome browser DevTools.

![](/img/205/chrome2.png)

TIP: Insert a "debugger" statement in your JavaScript code to force the debugger to pause execution.

Note that when the plug-in is restarted, for example when the JavaScript code is updated, you will need to re-connect the DevTools.

