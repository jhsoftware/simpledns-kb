---
category: 15
frontpage: false
comments: true
refs: 82,81
created-utc: 2019-01-01
modified-utc: 2021-09-08
---
# What are the system requirements for Simple DNS Plus?

<table class="data">
		<tr>
			<td style="white-space: nowrap;vertical-align:top">Operating system:</td>
			<td style="white-space:wrap">
Windows 7 (SP1+) / Windows Server 2008 R2 (SP1+) or later.
<p>Both 32 bit and 64 bit Windows versions are fully supported.<br/>
"Windows Server Core" is also supported - <a href="/kb/119/simple-dns-plus-on-windows-server-core">details</a>.<br/>
"Windows Embedded 7" is also supported - <a href="/kb/118/simple-dns-plus-on-windows-embedded-standard-7">details</a>.</p>
			</td>
		</tr>
		<tr>
			<td style="vertical-align:top">Software:</td>
			<td style="white-space:wrap">Microsoft .NET Framework 4.8<br />
			(automatically downloaded and installed if missing)</td>
		</tr>
		<tr>
			<td style="vertical-align:top">Processor (CPU):</td>
			<td style="white-space:wrap">1 GHz or better.</td>
		</tr>
		<tr>
			<td style="vertical-align:top">Memory (RAM):</td>
			<td style="white-space:wrap">64 MB + Windows and .NET Framework requirements.</td>
		</tr>
		<tr>
			<td style="vertical-align:top">Hard disk space:</td>
			<td style="white-space:wrap">10 MB + Windows and .NET Framework requirements.</td>
		</tr>
		<tr>
			<td style="vertical-align:top">Network:</td>
			<td style="white-space:wrap">Any type of TCP/IP (IPv4 or IPv6) connection.</td>
		</tr>
		<tr>
			<td style="vertical-align:top">Internet IP address:</td>
			<td style="white-space:wrap">You need a static (*) Internet IP address only if you want to use Simple DNS Plus for hosting domain names on the Internet. A dynamic IP address can be used for a resolving and caching Internet domain names.</td>
		</tr>
</table>

(*) By "static" we mean an IP address which does not change, or only very seldom changes.\
It doesn't matter how the IP address is assigned to your computer/router (manually or dynamically).\
Many "always-on" Internet connections such as cable and ADSL connections provide an Internet IP address which never actually change even if it is supposed be be "dynamic". Such an IP address can be considered "static" and works fine for hosting domain names.