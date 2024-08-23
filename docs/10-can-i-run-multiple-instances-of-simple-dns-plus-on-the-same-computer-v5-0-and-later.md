---
category: 11
frontpage: false
comments: true
vgroup: 1
vname: Simple DNS Plus v. 5.0 and later
vsort: 1
created-utc: 2019-01-01
modified-utc: 2024-08-23
---
# Can I run multiple instances on the same computer? (Simple DNS Plus v. 5.0 and later)

One instance of Simple DNS Plus can serve multiple IP addresses on the same machine.  
You can specify which IP addresses in the Options dialog / DNS / Inbound Requests section.

Under normal circumstances it wouldn't be necessary to run multiple instances because, to the rest of the Internet, each IP address looks like a different DNS server (easy way to run primary and secondary on one machine).

However, it is possible to run multiple instances (from different directories), for example if you want to serve different data to clients on different network segments.

Just make sure to configure each instance to listen on different local IP addresses, so they won't conflict.  
If you are going to use the HTTP API, you will also need to make sure that each instance uses different IP addresses or port numbers for this - see Options dialog / HTTP API.

To do this:

Install the first instance as normal. Typically, this will install to "C:\Program Files\Simple DNS Plus".  
Then copy this whole directory for example to "C:\Program Files\Simple DNS Plus2".

Next create a text file called "instance.txt" in the copy's directory.  
The content of the "instance.txt" file must be a short unique instance ID. For example "LAN" or "NS2".  
No white space characters or line breaks are allowed.

Finally you need to install the Windows Service for the second instance using the .NET "InstallUtil.exe" tool on "sdnsmain.exe" in the second instance directory.  
For example:

```
C:\>cd "\Program Files\Simple DNS Plus2"  
C:\Program Files\Simple DNS Plus2>\windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe sdnsmain.exe  
```

> [!Note] For Simple DNS Plus versions prior to v. 9.0, you need to use the .NET 2.0 version of `InstallUtil.exe`
> found in `c:\windows\Microsoft.NET\Framework\v2.0.50727`.

> [!Note] On Windows 10/11 you will need to run this "As administrator" 
> (right-click "Command Prompt" shortcut in Start menu and select "Run as administrator"
> prior to executing above commands). 

After this you can start the second instance:  
- If you are using Simple DNS Plus v. 5.2 or later - run "sdnsgui.exe" from the copy's directory.  
- If you are using Simple DNS Plus v. 5.0 or 5.1 - run "sdnsplus.exe" from the copy's directory.

The service name for the second instance is `SDNSPLUS_<instance ID>` where `<instance ID>` is the content of the instance.txt file.  
For example if the instance ID is "LAN", you can start the service from a command prompt with "NET START SDNSPLUS_LAN"  
The instance ID will also be part of the service description in the Windows Services list.

Simple DNS Plus configuration files for the second instance will be stored in a sub-directory of the application data directory
`C:\ProgramData\JH Software\Simple DNS Plus\<instance ID>\`  

> [!Note] The user interface, including the tray icon, can only be accessed for one instance at a time. We recommend you disable the tray icon option (Options dialog / General section) for both instances.  
> To make it easier to access the GUI, you can make a desktop shortcut to "sdnsplus.exe" for each instance.
