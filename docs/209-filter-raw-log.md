---
category: 20
frontpage: false
comments: true
created-utc: 1970-01-01
modified-utc: 2023-10-01
---
# Filter Raw Log

Command line tool which parses a raw log file (.sdraw) from [Simple DNS Plus](https://simpledns.plus) (v. 5.0 and later), filters and summarizes the data, and writes the result to a text file as comma separated values (csv format). The data can be summarized either by zone, query name (qname), query type (qtype), request source IP address (fromip), or by hour.

This tool uses and includes the ["Simple DNS Plus - Raw Log Library"](https://github.com/jhsoftware/SDNSRawLogDLL)

Simple DNS Plus raw log files are enabled in the Options dialog / Logging / Log Files section.
The raw log files are then found in the Simple DNS Plus log files directory (See Options dialog / Logging section). 

### Requirements

- Microsoft .NET Framework v. 2.0 - 3.5

Can be re-compiled for later .NET versions without any source code changes.

### Download / Installation

Download the latest binary from <https://github.com/jhsoftware/SDNSFilterRawLog/releases> (32 or 64 bit depending on your OS) and unzip the file.

### Usage

```
FilterRawLog zone   <simple-dns-plus-database-file> <raw-log-file> <output-file>  
FilterRawLog qname  <raw-log-file> <output-file>  
FilterRawLog qtype  <raw-log-file> <output-file>  
FilterRawLog fromip <raw-log-file> <output-file>  
FilterRawLog hour   <raw-log-file> <output-file>
```

Note: The "zone" option only works with a database file from Simple DNS Plus v. 6.0 or later.  
The other options work with raw log files from Simple DNS Plus v. 5.0 and later.

### Source code / Git repository

See <https://github.com/jhsoftware/SDNSFilterRawLog>

Contributions are most welcome. Fork the repository, create a branch, commit your changes, push, and submit a pull request.
Or just e-mail us the changes :-)

