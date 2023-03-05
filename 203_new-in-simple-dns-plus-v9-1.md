---
category: 17
frontpage: false
comments: true
vgroup: 7
vname: v. 9.1
vsort: 91
created-utc: 2021-10-26
modified-utc: 2021-10-28
---
# New in Simple DNS Plus (v. 9.1)

New features / updates in v. 9.1:

- [JavaScript plug-in](#jspi)
- [New asynchronous plug-in interface](#piasync)
- [Plug-in query order enhanced](#piorder)
- [Miscellaneous updates](#misc)
- [Breaking changes](#breaking)

### JavaScript plug-in{#jspi}

Write your own custom logic for DNS query processing in JavaScript. Your script code runs efficiently via Google's V8 JavaScript engine - the same that powers Chrome and Node.js.

![](/img/203/js1.png)

The JavaScript code can be as simple or complex as needed - for example: 

![](/img/203/js4.png)


The plug-in supports storing the JavaScript code in a separate file (optional), which lets you edit the code in the editor of your choice - for example Visual Studio Code to get JavaScript syntax highlighting etc.

![](/img/203/js2.png)

The plug-in also supports connecting debuggers (such as Chrome DevTools) to debug your JavaScript code running in Simple DNS Plus live:

![](/img/203/js3.png)

This plug-in is automatically installed with Simple DNS Plus v. 9.1.

Read more about this at <https://simpledns.plus/plugin-javascript>

### New asynchronous plug-in interface{#piasync} 

The programming interface for plug-ins has been updated use the asynchronous programming model (async/await).

This improves performance by allowing simple plug-ins (like "Fixed IP address") to execute directly in the main thread, while making it easier to take advantage of asynchronous operations with I/O bound plug-ins (like "MS SQL Server").

The new plug-in interface also shares more code with the main Simple DNS Plus program, so that fewer conversions are needed when communicating between the plug-in and the program, which also improves performance.

Plug-ins included with the Simple DNS Plus installer are updated automatically, but you will need to download new versions of any downloadable plug-ins (v. 9.1 updates have been published for all of them), and any custom developed plug-ins will need to be [re-programmed](/kb/31) to work with the new interface.


### Plug-in query order enhanced{#piorder}

It is now possible to have some plug-ins queried before local zones and other plug-ins queried after local zones (used to be either all plug-ins before or all plugs-ins after):

![](/img/203/query-order.png)


### Miscellaneous updates{#misc}

- New plug-in DNS Request rule "Server is authoritative (AA)". Can be used to only "ask" the plug-in when the server is (or is not) authoritative (has a zone) for the requested name. (only works for plug-ins listed after [LOCAL DNS ZONES] - see "Plug-in query order enhanced" above). 
- The "Automatic SPF records" feature (Options dialog / DNS / Local Zones / Automatic SPF) has been removed. A new [Auto SPF plug-in](/plugin-autospf) is now available to provide this functionality.
- "Maximum inbound DNS TCP connections" option (Options dialog / DNS / Inbound requests section) changed to "...per source IP address". To avoid blocking legitimate connections from other IP addresses.


### Breaking changes{#breaking}

- The programming interface for plug-ins has changed (see "New asynchronous plug-in interface" above). 
- The "Automatic SPF records" feature has been replaced by a new plug-in (see Miscellaneous above). If you were using this feature, you will need to re-configure this with the plug-in.
