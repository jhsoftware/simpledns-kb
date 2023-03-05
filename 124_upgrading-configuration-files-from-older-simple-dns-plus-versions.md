---
category: 11
frontpage: false
comments: true
created-utc: 2019-01-01
modified-utc: 2021-10-16
---
# Upgrading configuration files from older Simple DNS Plus versions

### From Simple DNS Plus. v. 6.0 and later

If you upgrade to the current version of Simple DNS Plus from v. 6.0 or later, you can simply run the current version and it will automatically upgrade the data files.

However, if you upgrade from version 5.3 or earlier, you will first need to convert the data files using one or two tools.

### From Simple DNS Plus v. 4.00 and earlier

You first need to convert the files to v. 5.3 format, using the upgrade tool "upgrade5.exe" available at <https://simpledns.plus/outbox/upgrade5.exe>

Place this file in the directory where Simple DNS Plus is installed and then run it from there.

Then proceed to converting the files to v. 9.0 format as described below.

### From Simple DNS Plus v. 5.x

Convert the data files to v. 9.0 format, using the upgrade tool "upgrade5to9.exe" available at <https://simpledns.plus/outbox/upgrade5to9.zip>

Note that this tool requires [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48) to run.

Unzip the "upgrade5to9.zip" file to a new directory (anywhere), and run "upgrade5to9.exe" from there.

You can optionally specify an alternate application data folder (for example when using multiple instances) as the first parameter when executing "upgrade5to9.exe" from a command line.

The tool will run through a series of steps to upgrade the files:

![](/img/124/upgrade5to9.png)

