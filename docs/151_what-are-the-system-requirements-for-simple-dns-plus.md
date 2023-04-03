---
category: 15
frontpage: false
comments: true
refs: 82,81
created-utc: 2019-01-01
modified-utc: 2021-09-08
---
# What are the system requirements for Simple DNS Plus?

<table cellpadding="5" cellspacing="2">
	<tbody>
		<tr bgcolor="#e0f0ff">
			<td style="white-space: nowrap;" valign="top">Operating system:</td>
			<td>
Any edition of:

- Windows 7 (SP1+)
- Windows 8 (except "RT")
- Windows 8.1 (except "RT")
- Windows 10
- Windows 11
- Windows Server 2008 R2 (SP1+)
- Windows Server 2012
- Windows Server 2012 R2
- Windows Server 2016
- Windows Server 2019
- Windows Server 2022

<p>Both 32 bit and 64 bit Windows versions are fully supported.<br/>
"Windows Server Core" is also supported - <a href="/kb/119/simple-dns-plus-on-windows-server-core">details</a>.<br/>
"Windows Embedded 7" is also supported - <a href="/kb/118/simple-dns-plus-on-windows-embedded-standard-7">details</a>.</p>
			</td>
		</tr>
		<tr bgcolor="#c0d0e0">
			<td style="white-space: nowrap;" valign="top">Software:</td>
			<td>Microsoft .NET Framework 4.8<br />
			(automatically downloaded and installed if missing)</td>
		</tr>
		<tr bgcolor="#e0f0ff">
			<td style="white-space: nowrap;" valign="top">Processor (CPU):</td>
			<td>1 GHz or better.</td>
		</tr>
		<tr bgcolor="#c0d0e0">
			<td style="white-space: nowrap;" valign="top">Memory (RAM):</td>
			<td>64 MB + Windows and .NET Framework requirements.</td>
		</tr>
		<tr bgcolor="#e0f0ff">
			<td style="white-space: nowrap;" valign="top">Hard disk space:</td>
			<td>10 MB + Windows and .NET Framework requirements.</td>
		</tr>
		<tr bgcolor="#c0d0e0">
			<td style="white-space: nowrap;" valign="top">Network:</td>
			<td>Any type of TCP/IP (IPv4 or IPv6) connection.</td>
		</tr>
		<tr bgcolor="#e0f0ff">
			<td style="white-space: nowrap;" valign="top">Internet IP address:</td>
			<td>You need a static (*) Internet IP address only if you want to use Simple DNS Plus for hosting domain names on the Internet. A dynamic IP address can be used for a resolving and caching Internet domain names.</td>
		</tr>
	</tbody>
</table>

(*) By "static" we mean an IP address which does not change, or only very seldom changes.\
It doesn't matter how the IP address is assigned to your computer/router (manually or dynamically).\
Many "always-on" Internet connections such as cable and ADSL connections provide an Internet IP address which never actually change even if it is supposed be be "dynamic". Such an IP address can be considered "static" and works fine for hosting domain names.