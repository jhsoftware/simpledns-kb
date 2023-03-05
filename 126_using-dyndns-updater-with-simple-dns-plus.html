---
title: Using DynDNS Updater with Simple DNS Plus
category: 4
frontpage: false
comments: true
refs: 35,115,173
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<p>"DynDNS Updater" is a product by KanaSolution - <a href="http://www.kanasolution.com" target="_blank">http://www.kanasolution.com</a><br />
This tutorial was created using DynDNS Updater version 3.1.0.15. </p>
<p>You can use DynDNS Updater to automatically update DNS records on a remote Simple DNS Plus server - either using the <a href="https://simpledns.plus/plugin-dyndns">DynDNS Service plug-in</a> or through the <a href="/kb/115/sending-simple-dns-plus-http-commands">HTTP API</a> directly.<br />
This makes it possible to run different services (such as a web-server) on a computer with a dynamic IP address.<br />
You can also use this when you need to access roaming computers - for example traveling sales people with laptops.</p>
<p>If you use the DynDNS Service plug-in, you must enable the "HTTP - Basic HTTP Authentication" update method in the plug-in configuration.<br />
If you use the HTTP API directly, you must configure the HTTP API to listen on an IP address which can be accessed remotely (not the default 127.0.0.1) and set a password - see Simple DNS Plus Options dialog.</p>
<p>
<br />
The first step in configuring DynDNS Updater is to disable DynDNS.org only mode (enables multiple provider support) in the "DynDNS.ini" file. This file is automatically created in the directory where DynDNS Updater is installed the first time the program is run. So run DynDNS Updater, and exit right away as follows:</p>
<p>In the DynDNS Updater Wizard dialog, click the "Cancel" button:</p>
<p>
<img height="411" src="img/126/1.png" width="481" />
</p>
<p>In the "DynDNS Updater - Settings" dialog, click the "Cancel" button:</p>
<p>
<img height="435" src="img/126/2.png" width="419" />
</p>
<p>Right-click the tray icon in the Windows notification area and select "Exit" from the pop-up menu:</p>
<p> <img height="234" src="img/126/3.png" width="337" /></p>
<p>Now open the "DynDNS.ini" file (in the directory where DynDNS Updater is installed) with Notepad, and add the line "IsDynDNS=0" immediately after the [Options] line, save the file, and exit:</p>
<p>
<img height="264" src="img/126/4.png" width="492" />
</p>
<p>Next we need to create a custom provider configuration file.<br />
Create a new text file (for example using Notepad) with the following contents and save this as "Simple DNS Plus.txt" in the directory where DynDNS Updater is installed:</p>
<p>For use with the DynDNS Service plug-in:</p>

<pre>[default]
withpass=1
host=dyndns.example.com
port=80
path=/ddns
protocol=http

[requests]
ip=%IP%

[result]
multilines=0
success=OK
warning=FAIL
</pre>

<p>For use with the HTTP API directly:</p>

<pre>[default]
withpass=1
host=ns1.example.com
port=8053
path=/updatehost
protocol=http

[requests]
host=%HOST%
data=%IP%

[result]
multilines=0
success=OK
warning=ERROR
</pre>

<p>Change the "host" setting to match the host name or IP address of the computer running Simple DNS Plus.</p>
<p>Now run DynDNS Updater again, and once again click the "Cancel" button in the "DynDNS Updater Wizard" dialog:</p>
<p>
<img height="411" src="img/126/5.png" width="481" />
</p>
<p>In the "DynDNS Updater - Settings" dialog / Groups tab, click the "Add" button:</p>
<p>
<img height="435" src="img/126/6.png" width="419" />
</p>
<p>In the "Group Name" dialog, enter "Simple DNS Plus" and click the "OK" button:</p>
<p>
<img height="242" src="img/126/7.png" width="348" />
</p>
<p>In the "Simple DNS Plus - Properties" dialog, enter username (must be "admin" with HTTP API) and password matching those in Simple DNS Plus, and click the "Add" button:</p>
<p>
<img height="436" src="img/126/8.png" width="472" />
</p>
<p>Enter the fully qualified host name that you want to update, set System to "custom", and click the "OK" button:</p>
<p>
<img height="199" src="img/126/9.png" width="305" />
</p>
<p>Back in the "Simple DNS Plus - Properties" dialog, select the "Options" tab, enter "Simple DNS Plus" in the Provider field (don't use dropdown - just type it), in the "Profile" field specify the provider configuration file created earlier, UN-check "Use secure connection", and click the "OK" button:</p>
<p>
<img height="436" src="img/126/10.png" width="472" />
</p>
<p>You may need to adjust other settings in DynDNS Updater to match your connection type etc.</p>
<p>Once configured, you can test the setup using the "Force Update" button in the DynDNS Updater window / Info tab:</p>
<p>
<img height="431" src="img/126/11.png" width="423" />
</p>
<p>If everything is setup correctly, the result (see "Log" tab) should look something like this:</p>
<p>
<img height="431" src="img/126/12.png" width="423" />
</p>