---
category: 11
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# How to manually remove / uninstall Simple DNS Plus

In order to remove / uninstall Simple DNS Plus from your computer, you should always first try to use the Windows Control Panel / Program and Features function.

If that fails for some reason (corrupted installer database, etc.), you can remove Simple DNS Plus manually by performing the following steps:

1. **Installer registry data**  
Delete the following registry keys:  
**- HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\{6931AE04-8A43-48E6-82EF-7D3F2147B2C8}  
\- HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\Simple DNS Plus &lt;version&gt;  
\- HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Installer\UserData\S-1-5-18\Products\40EA139634A86E8428FED7F312742B8C  
\- HKEY_CLASSES_ROOT\Installer\Products\40EA139634A86E8428FED7F312742B8C**
2. **Windows Service**  
Delete the registry key:  
**HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\sdnsplus**
3. **Application registry data**  
Delete the registry key:  
**HKEY_LOCAL_MACHINE\SOFTWARE\JH Software\Simple DNS Plus**
4. **Windows Event log sources**  
Delete the registry key:  
**HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\EventLog\Application\Simple DNS Plus**
5. **Windows Performance counter category.**  
Delete the registry key:  
**HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Simple DNS Plus**
6. **Windows login/startup entry**  
Delete the "**Simple DNS Plus**" value (**NOT** the entire key) from:  
**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run**
7. **Installer Files**  
Delete the folders:  
**- C:\Windows\Installer\{6931AE04-8A43-48E6-82EF-7D3F2147B2C8}  
\- C:\ProgramData\Caphyon\Advanced Installer\{6931AE04-8A43-48E6-82EF-7D3F2147B2C8}**
8. **Application program files**  
Delete the folder where the program was installed. The default is:  
**C:\Program Files\Simple DNS Plus**
9. **Application data files**  
Delete the folder:  
**C:\ProgramData\JH Software\Simple DNS Plus**
10. **User specific data files**  
Delete the folder(s):  
**C:\Users\&lt;user&gt;\AppData\Local\JH Software\Simple DNS Plus**
11. **Windows Start menu folder**  
Delete the folder:  
**C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Simple DNS Plus**
12. **Desktop shortcut**  
Delete the **"Simple DNS Plus" link** (**NOT** the entire folder) from:  
**C:\Users\Public\Desktop**
13. **Windows Firewall rule**  
In the Windows Control Panel / Administrative Tools / Windows Firewall, under "Inbound Rules", locate and delete "Simple DNS Plus (In)",

**Notes:**

- It is assumed that you know how to modify the Windows registry using "RegEdit" or other tools. Otherwise please get assistance from someone who does (mistakes could mess up your Windows installation).
- Some of the folders mentioned above are hidden by default. Again if you don't know how to get to these, please get assistance from someone who does.
- Above is based on Simple DNS Plus version 6.0. Some of this is different for other versions.
- Above registry / folders locations are based on Windows 10 / Windows Server 2016. Some of these are different in other Windows versions.
- Above folder locations are based on the U.S. English edition of Windows. These folder names may be different in other language editions of Windows.

