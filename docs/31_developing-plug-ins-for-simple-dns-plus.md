---
category: 8
frontpage: false
comments: true
refs: 85,110
created-utc: 2019-01-01
modified-utc: 2021-10-28
---
# Developing plug-ins for Simple DNS Plus

Plug-ins can be developed in any .NET Framework 4.8 programming language including Visual Basic.NET and C#.

The standard Simple DNS Plus installation includes the "sdnscommon.dll" file (and "sdnscommon.xml" file to provide Visual Studio intellisense) in the main installation directory.

To create your own plug-in for Simple DNS Plus, create a .NET 4.8 library (.dll file) that references "sdnscommon.dll" with a public class that implements one of the following 8 interfaces (ILookupHost, ILookupReverse, and ILookupTXT can be combined - the rest cannot):

- **JHSoftware.SimpleDNS.Plugin.ILookupHost**\
	For plug-ins designed to fetch a single host record (A or AAAA) - that is the IP address (IPv4/IPv6) for a host name.

- **JHSoftware.SimpleDNS.Plugin.ILookupReverse**\
	For plug-ins designed to fetch a reverse record (PTR) - that is the host name for an IP address (IPv4/IPv6).

- **JHSoftware.SimpleDNS.Plugin.ILookupTXT**\
	For plug-ins designed to fetch a single TXT record for a host name.

- **JHSoftware.SimpleDNS.Plugin.ILookupRecord**\
	For plug-ins designed to fetch a single DNS record of any type.\
	(New from Simple DNS Plus v. 9.1.115)

- **JHSoftware.SimpleDNS.Plugin.ILookupAnswer**\
	For plug-ins designed to fetch multiple DNS records of any type.\
	NOTE: Plug-ins based on this interface only work with the "Unlimited zones" license type.

- **JHSoftware.SimpleDNS.Plugin.IIgnoreRequest**\
	For plug-ins that instruct Simple DNS Plus to ignore (not answer) a DNS request when the DNS request meets conditions defined and evaluated by the plug-in.
	
- **JHSoftware.SimpleDNS.Plugin.ISkip**\
	For plug-ins that instruct Simple DNS Plus to skip some or all of the following plug-in instances when a DNS request meets conditions defined and evaluated by the plug-in.\
	This works similar to a script statement "IF &lt;condition&gt; THEN GOTO X" providing powerful flow control to the plug-in instances list.

- **JHSoftware.SimpleDNS.Plugin.ICloneAnswer**\
	For plug-ins that instruct Simple DNS Plus to create a cloned response (clone the records in the response to a request for another domain name provided by the plug-in).\
	NOTE: Plug-ins based on this interface only work with the "Unlimited zones" license type.

- **JHSoftware.SimpleDNS.Plugin.INoDNS**\
	For plug-ins that do not process DNS requests directly, but provide some other related functionality.
	

Additionally the plug-in class may implement one or more of the following interfaces:

- **JHSoftware.SimpleDNS.Plugin.IOptionsUI**\
	Implement this interface in plug-ins that provide a user interface to configure plug-in settings.

- **JHSoftware.SimpleDNS.Plugin.IViewUI**\
	Implement this interface in plug-ins that provide a View (main Simple DNS Plus Window / View menu).

- **JHSoftware.SimpleDNS.Plugin.IState**\
	Implement this interface in plug-ins that need to store state between runs.

- **JHSoftware.SimpleDNS.Plugin.IListsDomainName**\
	Implement this interface in plug-ins that in some way lists domain names. This can be used to create DNS request access rules for other plug-ins. I.E. "allow access if plug-in xyz lists the requested domain name".
	
- **JHSoftware.SimpleDNS.Plugin.IListsIPAddress**\
	Implement this interface in plug-ins that in some way lists IP addresses. This can be used to create DNS request access rules for other plug-ins. I.E. "allow access if plug-in xyz lists the sender's IP address".
	
- **JHSoftware.SimpleDNS.Plugin.IQuestions**\
	Implement this interface in plug-ins that provide one or more questions that Simple DNS Plus can ask of the plug-in.\
	These questions are used only in DNS request access rules for other plug-ins.
	
- **JHSoftware.SimpleDNS.Plugin.ITSIGUpdateHost**\
	Implement this interface in plug-ins which can authenticate and process TSIG signed dynamic update requests for a single host record.
	
- **JHSoftware.SimpleDNS.Plugin.ISignal**\
	Plug-in specific signaling between plug-in and Simple DNS Plus.<br />
	Used for unique plug-in situations which require extra information to be passed between the plug-in and Simple DNS Plus. Also allows for the implementation of new features without changing the plug-in interfaces. Plug-in developers who need to retrieve/update settings etc. which are not provided by other plug-in methods may request a unique signal code for this.

Your compiled library must be placed in the "Plugins" sub-directory of the directory where Simple DNS Plus is installed, and it will then appear in the list of available plug-in types when creating a new plug-in instance.


