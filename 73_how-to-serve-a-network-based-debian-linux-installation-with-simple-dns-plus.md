---
title: How to serve a network based Debian Linux installation with Simple DNS Plus
category: 8
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<div>This articles describes how to install Debian Linux over the network (no CDs, floppy-disks, USB keys, etc.) using the <a href="https://simpledns.plus/plugin-dhcp">DHCP Server</a> and <a href="https://simpledns.plus/plugin-tftp">TFTP Server</a> plug-ins in Simple DNS Plus (running on a Windows computer).<br />
<br />
This Debian Linux installation is just an example to demonstrate the DHCP/TFTP plug-in combination.<br />
Similar procedures can be used to network install or boot other operating systems, or provision IP phones and other devices.<br />
<br />
You will need two computers (real or virtual) - one running Windows and Simple DNS Plus, and another empty computer (to install Debian Linux on) with a BIOS and network card that support PXE booting (most computers/network cards manufatured since ~2000 support this). Make sure&nbsp;PXE / network booting is enabled in BIOS.<br />
<br />
First, make sure that you have the lastest version of Simple DNS Plus installed (<a href="https://simpledns.plus/download">download</a>), as well as the lastest release of the <a href="https://simpledns.plus/plugin-dhcp">DHCP Server</a> and <a href="https://simpledns.plus/plugin-tftp">TFTP Server</a> plug-ins.<br />
<br />
Next, prepare the TFTP folder structure:<br />
1) Create a directory on the Simple DNS Plus computer to be the TFTP root - for example C:\TFTP_Root.<br />
2) Download the 3 files <a href="http://http.us.debian.org/debian/dists/lenny/main/installer-i386/current/images/netboot/debian-installer/i386/pxelinux.0">pxelinux.0</a>,&nbsp;<a href="http://http.us.debian.org/debian/dists/lenny/main/installer-i386/current/images/netboot/debian-installer/i386/initrd.gz">initrd.gz</a> and <a href="http://http.us.debian.org/debian/dists/lenny/main/installer-i386/current/images/netboot/debian-installer/i386/linux">linux</a> (right-click / Save target as...) to&nbsp;the TFTP root. Make sure the file &quot;linux&quot; has no file extension (Windows might add &quot;.txt&quot;)<br />
3) Under the TFTP root, create a new folder &quot;pxelinux.cfg&quot;.<br />
4) Download the file <a href="https://simpledns.plus/kb1304-default.ashx">default</a> to the &quot;pxelinux.cfg&quot; folder.<br />
<br />
The next step will be to configure the DHCP server and TFTP server plug-ins in Simple DNS Plus.<br />
From the main Window click the &quot;Options&quot; button, then select &quot;Plug-ins&quot; in the left list, under &quot;Available plug-in components&quot; select &quot;DHCP Server&quot;, and click the &quot;Create New Instance...&quot; button:<br />
<br />
<img src="img/73/1.png" /><br />
<br />
In the &quot;DHCP Server Plug-In Instance&quot; dialog, select the &quot;Plug-In Settings&quot; tab, fill in the &quot;DNS Suffix&quot; and IP address range, and click the &quot;DHCP Options...&quot; buttion:<br />
<br />
<img src="img/73/2.png" /><br />
<br />
In the &quot;Default DHCP options&quot; dialog, select the &quot;IP routing&quot; tab, and enter the IP address of your Internet router:<br />
<br />
<img src="img/73/3.png" /><br />
<br />
Selec the &quot;TFTP / Boot file&quot; tab, in the &quot;TFTP server IP address&quot; field enter the IP address of the computer running Simple DNS Plus, and in the &quot;Boot file name&quot; field enter &quot;pxelinux.0&quot;, click the &quot;OK&quot; button in this and the previous dialog:<br />
<br />
<img src="img/73/4.png" /><br />
<br />
Back in the Options dialog, under &quot;Available plug-in components&quot; select &quot;TFTP&nbsp;Server&quot; and click the &quot;Create New Instance&quot; button:<br />
<br />
<img src="img/73/5.png" /><br />
<br />
In the &quot;TFTP Server Plug-In Instance&quot; dialog, select the &quot;Plug-In Settings&quot; tab, in the &quot;Data folder&quot; field enter the path to the TFTP root folder created earlier, and click the &quot;OK&quot; button in this and all the previous dialogs.<br />
<br />
<img src="img/73/6.png" /><br />
<br />
Now turn on the second computer and you should see Simple DNS Plus assigning it an IP address (via DHCP) and then&nbsp;TFTP file transfer requests in the Simple DNS Plus log:<br />
<br />
<img src="img/73/7.png" /><br />
<br />
On the second computer you should see a matching boot sequence:<br />
<br />
<img src="img/73/8.gif" /><br />
<br />
Shortly after, the Debian Linux installation prompts should appear, and it will automatically download remaning files from the Internet:<br />
<img src="img/73/9.png" /></div>