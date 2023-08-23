---
category: 17
frontpage: false
comments: true
vgroup: 7
vname: v. 6.0
vsort: 60
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# New in Simple DNS Plus (v. 6.0)

### Zone version control

Simple DNS Plus now stores a number of old versions of each zone (each version identified by a SOA-record serial number).  
This makes it easy to track changes and to restore a previous version if an update caused trouble.  
These stored versions are now also used to provide optimized incremental zone transfers (IXFR) to secondary servers (by calculating and sending only a single diff-set).  
New HTTP API functions "zoneversions" and "getzoneversion" have been added to list the stored versions of a zone and to retrieve the zone file text for a specific version (build 105 and later).

To view, compare, export, or restore old versions of a zone, in the DNS Records window, right-click a zone and select "Versions...":

![](img/105/1.png)

This opens the new "Zone versions" window. Select an old version (by serial number) to see the records of that version, or select two versions to compare them (hold down CTRL key while clicking versions).  
With a single version selected, click the "Restore" button to restore that version, or click the "View/Save as standard zone file..." to export it:

![](img/105/2.png)

In the Options dialog there is a new DNS / Local Zones / Zone Versions section. Here you can specify the number of versions to retain.

![](img/105/3.png)

### All DNS data and program settings in single database file

Simple DNS Plus no longer stores DNS records in individual zone files.  
These and almost all other configuration files used by previous versions of Simple DNS Plus have been moved into a single SQLite database file - "sdnsplus.db" in the application data directory.  
Using the transactional features of the SQLite database engine, your data is now much better protected from power outages, crashes, etc.  
Also, DNS records are now stored in a binary format within this database, making loading and saving zones even faster.

We do <u>NOT</u> recommend that you update the new database file directly, but since it is a standard SQLite file, you can access / inspect it with any SQLite tool - for example "SQLiteStudio" ([http://sqlitestudio.pl](http://sqlitestudio.pl){target=_blank}).

Note: We have also added a command line option (-b) to make a backup of this database while Simple DNS Plus is still running (build 102 and later). For details see [/kb/50/how-do-i-backup-and-restore-simple-dns-plus-settings-and-data-v6-0-and-later](/kb/50/how-do-i-backup-and-restore-simple-dns-plus-settings-and-data-v6-0-and-later)

### View/Save as standard zone file

As mention above, Simple DNS Plus no longer stores DNS records in standard zone files (RFC1035 format), but you can now easily generate such a file for any DNS zone in Simple DNS Plus.  
In the DNS Records window, right-click a zone and select "View/Save as standard zone file":

![](img/105/4.png)

This opens a new window with the text of a standard zone file for the DNS records currently listed in the DNS Records window.  
Click the "Save as..." button to save this to a file, or the "Copy" button to copy this text to the Windows clipboard:

![](img/105/5.png)

### Export standard boot file and zone files

You can now also export a standard boot file along with standard zone files for all the zones in Simple DNS Plus (or for the zones in one or more zone groups). The resulting files can easily be imported on another DNS server since everything is in standard RFC defined file formats.  
In the DNS Records window, from the "File" menu, select "Export...", then select "Standard boot file and zone files":

![](img/105/6.png)

### Export/import plug-in configuration

Typically plug-ins need to be configured the same way on primary and secondary servers, and some plug-ins have very complex configurations.  
It is now easy to copy a plug-in instance configuration from Simple DNS Plus on one server to another.  
In the plug-in instances dialog (also new in this version - see below), click the "Export" button. This will copy the configuration of the selected plug-in instance to the Windows clipboard (XML format). Then Remote Desktop into the other Simple DNS Plus server, and click the "Import" button there, and a new plug-in instance will be created there with the same settings:

![](img/105/7.png)

### SHA-256 and SHA-512 in DNSSEC signatures

These algorithms are more secure and now recommended over SHA-1:

![](img/105/8.png)

### SHA-256 and SHA-384 hashes in DNSSEC DS-records

These algorithms are more secure and now recommended over SHA-1:

![](img/105/9.png)

### CAA-records (Certification Authority Authorization)

"Allows a DNS domain name holder to specify one or more Certification Authorities (CAs) authorized to issue certificates for that domain." (RFC 6844).

To create a new CAA-record, in the DNS Records window, right-click a zone, select "Other new record" and then "CAA-record":

![](img/105/10.png)

### Miscellaneous

- HTTP API specification in Swagger / OpenAPI format, and Swagger UI for exploring and testing the HTTP API included (build 106 and later). [Details](https://simpledns.plus/news/47).
- The DNS Records module now sends record updates to the service as a diff-set rather than a full zone, solving problem with dynamic updates received while editing a zone being overwritten.
- Plug-in configuration moved from Options dialog to a separate dialog. A new "Plug-Ins" button on main tool bar and new menu item in main Tools menu were added to access this.
- Export Wizard / IP address to "hosts" or ".csv" file function - now also includes IPv6 addresses.
- Many performance optimizations.

### Note about Adding / updating zones from command line

You may need to update any programs/scripts using the command line to add/update DNS zones in Simple DNS Plus.

Simple DNS Plus has since early versions included a command line option to add/update a DNS zone:

<pre>
SDNSPLUS -z  z:&lt;zone-name&gt; [f:&lt;file-name&gt;] [p:&lt;primary-ip&gt;] [g:&lt;group-id&gt;]
</pre>

In previous versions the zone file would be read from the directory specified in the Options dialog / DNS / Local Zones / Data Files section, but that settings is gone in v. 6.0 (because Simple DNS Plus now stores all DNS zones in a database instead of individual files).  
Therefore, for v. 6.0, we have updated the program so that you can now specify a full path in the f: parameter. For example:

<pre>
SDNSPLUS -z  z:example.com &quot;f:C:\my zone files\example.com.dns&quot;
</pre>

If you do NOT specify a full path in the f: parameter, Simple DNS Plus v. 6.0 will try to load the zone file from a "ZoneFiles" directory under the application data directory (typically "c:\ProgramData\JH Software\Simple DNS Plus") - the default location for zone files in previous versions.

Note: This applies to primary zones only, as the f: parameter is not needed when adding/updating a secondary zone.

### Retired features

- Alias zones (shared zone files).  
This feature was not compatible with the new zone versions and single database features (see above), and it is easy to achieve the same thing using either an "Alias Zones" plug-in (see [https://simpledns.plus/plugin-aliaszones](https://simpledns.plus/plugin-aliaszones){target=_blank}) or the "ALIAS record" feature (see [/kb/2/alias-records-auto-resolved-alias](/kb/2/alias-records-auto-resolved-alias){target=_blank})
- HTTP API commands "addaliaszone" and "aliaszonelist".  
Alias zones feature retired (see above). Using these commands now result in a "404 Not Found" response.
- HTTP API commands "loadzone" and "reloadall".  
Zones are no longer stored in individual files, so these are no longer relevant. Using these commands still result in a "200 OK" response - but do nothing.
- Options dialog / DNS / Local Zones / Data Files section (Location of DNS data files, Defer loading, record TTL limits).  
Zones are no longer stored in individual files, so this is no longer relevant.
- Command line "SDNSPLUS -r" (reload all zones) .  
Zones are no longer stored in individual files, so this is no longer relevant.
- Command line "SDNSPLUS -o" (reload options / "sdnsplus.config.xml" file).  
Program options are no longer stored in an individual file, so this is no longer relevant.
- Main window / File menu / Reload DNS Records.  
Zones are no longer stored in individual files, so this is no longer relevant.
- "ZoneDBViewer.exe" tool.  
Simple DNS Plus no longer uses the proprietary boot file "_zones.sdzdb", so there is no longer any need for this tool. See information above about using SQLite tools instead.
- Default Zone Values dialog / SOA record serial number format (date/sequential).  
SOA serial number incrementation now always uses date format if such value is larger than the previous.
- Export Wizard / Zone list (.csv file export)
- Individual plug-in configuration files.  
Plug-in interface "PlugInTypeInfo.ConfigFile" is now ignored.

