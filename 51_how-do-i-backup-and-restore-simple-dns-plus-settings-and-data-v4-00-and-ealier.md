---
category: 1
frontpage: false
comments: true
vgroup: 4
vname: v.4.00 and earlier
vsort: 3
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# How do I backup and restore Simple DNS Plus settings and data? (v.4.00 and earlier)

The different settings (Options dialog etc.) are recorded in various ".ini" files in the directory where Simple DNS Plus is installed.

The actual zone data files (zones and records) are stored in a separate directory as specified in the Options dialog / DNS / Records section:

![](img/51/1.png)

To backup: Copy all ".ini" files, and ALL files in the data directory.

To restore the settings and data on a new or reinstalled computer, install a fresh copy of Simple DNS Plus and copy the backup files back to their original location relative to the directory where Simple DNS Plus is installed.

If you are using a version of Simple DNS Plus prior to 4.00, and it was running as an Windows service, you will need to manually edit the "sdnsplus.ini" files and change the line "NTService=Yes" to "NTService=No" before starting the program again.
You can re-activate the Windows service in the Options dialog.