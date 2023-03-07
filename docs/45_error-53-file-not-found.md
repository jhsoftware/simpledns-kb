---
category: 14
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# Error 53 - File not found

If you get this error message

![](img/45/1.png)  

[Error number: 53 / Description: File not found / Module name: Main / Additional: 2 / False / ]

\- you are running Simple DNS Plus v. 3.60.xx or earlier, and someone / something has removed the "sdnsmain.exe" file from the directory where Simple DNS Plus is installed.  

We have received a number of reports about this error message, and usually it turns out that some anti-virus or other security program has (incorrectly) identified "sdnsmain.exe" (Simple DNS Plus' service module) as a malicious program, and has "quarantined" it - effectively removing the file. A so called "false positive".  
This probably happens because these older versions of Simple DNS Plus used a compression / encryption system (to prevent reverse engineering) which has later become popular with virus/trojan developers.  

You may be able to resolve this by restoring "sdnsmain.exe", or by re-installing.  
Make sure to tell your anti-virus/security software that the file is OK, so it doesn't remove it again.  

Note that Simple DNS Plus v. 5.0 and later releases are not affected by this problem, as they do not use this compression / encryption system.  

In any case, we recommend that you upgrade to the latest version of Simple DNS Plus.