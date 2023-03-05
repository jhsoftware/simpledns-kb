---
title: TFTP Server plug-in
category: 8
frontpage: false
comments: true
refs: 110,73
created-utc: 2019-01-01
modified-utc: 2020-01-08
---
<p>This plug-in provides TFTP (Trivial File Transfer Protocol) server functionality.</p>

<p>It supports the &quot;blksize&quot;, &quot;timeout&quot; and &quot;tsize&quot; options (implements RFC1350, 2347,2348, and 2349).</p>

<p>TFTP is typically used in combination with <a href="https://simpledns.plus/kb/169">DHCP</a> to enable PXE / diskless booting of PCs, provisioning IP phones, etc.<br />
An example of this is provided in <a href="https://simpledns.plus/kb/73">KB73 - How to serve a network based Debian Linux installation with Simple DNS Plus</a>.</p>

<p>On the &quot;Plug-In Settings&quot; tab, enter the following settings (explained below the image):</p>

<p><img src="img/189/1.png" /></p>

<ul>
	<li><strong>Server IP address</strong><br />
	The local IP address that the plug-in should listen for incoming requests on (UDP port 69).</li>
	<li><strong>Data folder </strong><br />
	The local folder to serve files from.<br />
	IMPORTANT: Make sure to specify a folder on a local harddisk as the service is not be able to access network shares.</li>
	<li><strong>Max. connections </strong><br />
	The maximum number of simultaneous connections (file transfers).</li>
	<li><strong>Max. block size</strong><br />
	The maximum size (in bytes) of individual data blocks.<br />
	The default block size is 512, but clients may request a larger block size (&quot;blksize&quot; option).<br />
	You may need to adjust this setting if you network limits UDP packet size.</li>
	<li><strong>Default timeout</strong><br />
	How long the server should wait for acknowledgeent that a client received the last data block.<br />
	When the timeout expires, the last data block will be resent.<br />
	Clients may request a different timeout value (&quot;timeout&quot; option). </li>
	<li><strong>Max. retransmits </strong><br />
	The maximum number of times a data block will be resent (after timeout or repeat request from client).</li>
</ul>

<p>To test your setup, you can use the TFTP command line tool.<br />
Note that in recent Windows version this first needs to be enabled from the Windows Control Panel / Programs &amp; Features / Turn Windows features on or off / TFTP client.</p>

<p><img src="img/189/2.png" /></p>

<p>The Simple DNS Plus log (Active Log View and log files) will show the request:</p>

<p><img src="img/189/3.png"  /></p>

<p>IMPORTANT: TFTP has no built-in security (authentication or otherwise). Anyone who can access the server's IP address / UDP port 69 can download all the files in the data folder and sub-directories.<br />
We recommend that you limit access with a firewall, or enable the plug-in only on private IP addresses.<br />
This plug-in does not support writes/uploads so there is no risk of new files being uploaded or existing files being altered.</p>

<p>NOTE: This plug-in does not provide any DNS records or any other functionality related to directly to DNS. But you can of course point domain names to the IP address that the plug-in listens for connections on, using A-records provided through local zones or other plug-ins.</p>

<p>Note: Requires Simple DNS Plus v. 5.2 build 111 or later.</p>