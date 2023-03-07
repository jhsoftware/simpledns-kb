---
category: 1
frontpage: false
comments: true
vgroup: 4
vname: v. 5.x
vsort: 2
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# How do I backup and restore Simple DNS Plus settings and data? (v. 5.x)

The different settings (Options dialog etc.) are recorded in various ".xml" files in the Simple DNS Plus application data directory:

On Windows Vista / Server 2008 and later, this location is typically:\
`C:\ProgramData\JH Software\Simple DNS Plus`\
On earlier Windows versions:\
`C:\Documents and Settings\All Users\Application Data\JH Software\Simple DNS Plus`

The actual zone data files (zones and records) are stored in a separate directory as specified in the Options dialog / DNS / Data Files section:

![](img/49/1.png)

To backup: Copy all ".xml" files, and ALL files in the data directory.

To restore the settings and data on a new or reinstalled computer: Install a fresh copy of Simple DNS Plus and copy the backup files back to their original location.