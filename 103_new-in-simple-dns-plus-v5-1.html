---
title: New in Simple DNS Plus (v. 5.1)
category: 17
frontpage: false
comments: true
vgroup: 7
vname: v. 5.1
vsort: 51
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<p>New features in v. 5.1:<br />
<a href="#suspend">Suspending Zones</a><br />
<a href="#syslog">Remote logging to syslog server</a><br />
<a href="#rfilter">Response Filtering - Stops "DNS rebinding attacks"</a><br />
<a href="#spoofing">Stronger protection against DNS spoofing (cache poisoning) attacks</a><br />
<a href="#events">Choose events for Windows Event Log</a><br />
<a href="#import">Import a list of domain names</a><br />
<a href="#bulk">Bulk update primary DNS server IP for secondary zones</a><br />
<a href="#httpapi">New and updated HTTP API commands</a><br />
<a href="#expired">Information bar for expired secondary zones</a><br />
<a href="#export">Export to standard boot file</a><br />
<a href="#edns0">Automatic test of firewall EDNS0 support</a><br />
<a href="#misc">Miscellaneous</a><br />
<a href="#rfc">New RFC and draft support</a></p>
<hr class="JHHR" />
<h3 id="suspend">Suspending Zones</h3>
<p>Suspending a zone allows you to temporarily stop serving data for a zone without deleting the zone.<br />
This can be useful for example if you are hosting the domain name for someone else, and they forgot to pay their bill...<br />
In the DNS Records window suspended zones are marked with a "paused" icon and a red zone name:</p>
<p>
<img src="img/103/1.png" width="258" height="102" />
</p>
<p>You can suspend / resume a zone from the right-click popup-menu:</p>
<p>
<img src="img/103/2.png" width="243" height="141" />       <img src="img/103/3.png" width="251" height="147" /></p>
<p>When you suspend or resume a zone on a "super master" server, the zone's suspended status is automatically transferred to all Simple DNS Plus "super slave" servers.</p>
<p>In the main Options dialog, there is a new section to configure how Simple DNS Plus responds to DNS requests for names under suspended zones:</p>
<p>
<img src="img/103/4.png" width="641" height="425" />
</p>
<p>In the Export Wizard, you can select to included suspended zones or not:</p>
<p>
<img src="img/103/5.png" width="505" height="114" />
</p>
<p>We have added a new "Suspended" column in the Zone Database Viewer tool:</p>
<p>
<img src="img/103/6.png" width="482" height="161" />
</p>
<p>And finally, the HTTP API has been extended with two new commands; "suspendzone" and "resumezone", and the XML version of the "zonelist" command has been extended with a new "suspended" attribute:</p>
<p>
<img src="img/103/7.png" width="543" height="101" />
</p>
<hr class="JHHR" />
<h3 id="syslog">Remote logging to syslog server</h3>
<p>Log data can be sent to a remote syslog server using the standard syslog protocol (RFC3164).<br />
This can be useful centralize logging and/or take advantage of various alerting features of syslog server software.<br />
There is a new "Syslog Server" section in the main Options dialog to configure this:</p>
<p> <img alt="syslog.png" src="img/103/8.png" width="641" height="425" /></p>
<p>Many different syslog server software packages exist for various operating systems.<br />
A nice choice for Windows is the "Kiwi Syslog Deamon" from <a href="http://www.kiwisyslog.com" target="_blank">Kiwi Enterprises</a> which is shown here receiving data from Simple DNS Plus:</p>
<p>
<img src="img/103/9.png" width="677" height="210" />
</p>
<hr class="JHHR" />
<h3 id="rfilter">Response Filtering - Stops "DNS rebinding attacks"</h3>
<p>Your web-browser will generally allow any script, Java object, Flash object, etc. to communicate via HTTP / TCP with the server that served a web-page for as long as that web-page is open in the browser.<br />
This is controlled by the host name specified in the web-page URL.<br />
A <a href="http://crypto.stanford.edu/dns/" target="_blank">DNS rebinding attack</a> is done by having the DNS record for the host name time out very quickly (low TTL and other tricks) and then serve a new IP address for the host name in response to the next DNS request ("rebinding").<br />
The new IP address would be the private/local IP address of an intranet server or device at your location. Now with a bit of scripting, the attacker can in effect use your browser as a gateway to your entire intranet - completely bypassing your firewall.<br />
The same type attack may also be possible with other Internet applications that rely on host names for security.</p>
<p>Browser companies are taking steps to prevent this in new browser versions, but it is much more efficient and secure to stop this type of attack at the DNS level by filtering out any private/local IP addresses in DNS responses from outside DNS servers:</p>
<p> <img alt="respfilt.png" src="img/103/10.png" width="641" height="425" /></p>
<p>The log will show removed host records like this:</p>
<p>
<img src="img/103/11.png" width="564" height="266" />
</p>
<hr class="JHHR" />
<h3 id="spoofing">Stronger protection against DNS spoofing (cache poisoning) attacks</h3>
<p>Two new features provide additional protection against DNS spoofing attacks:<br />
1) Option to allocate a new random port for each outbound DNS request - and only accept a response sent back to the same port. In recent news this is also called "port randomization".<br />
NOTE: This option was enhanced in build 103. Previous builds used random ports from a limited range whereas build 103 and later uses the full range of possible port numbers.<br />
2) New "Ignore responses which do not echo the request question section" option.<br />
Both of these features are based on the recommendations in a new Internet draft (soon to be RFC) <a href="http://tools.ietf.org/html/draft-ietf-dnsext-forgery-resilience" target="_blank">Measures for making DNS more resilient against forged answers</a>.</p>
<p> <img src="img/103/12.png" width="641" height="425" /></p>
<hr class="JHHR" />
<h3 id="events">Choose events for Windows Event Log</h3>
<p>Previous versions could also record events to the Windows Event Log, but this was all or nothing.<br />
In v. 5.1 you can choose which specific events to record (or not).<br />
This can be useful to exclude events that you do not care about if your event log is filling up to quickly.<br />
It can also make it easier to use eventtriggers / Task Scheduler to process events with scripts/programs, as you can choose to record only those events that you want to process. </p>
<p> <img alt="winevent.png" src="img/103/13.png" width="641" height="425" /></p>
<hr class="JHHR" />
<h3 id="import">Import a list of domain names</h3>
<p>A new option in the Import Wizard lets you import a list of domain names from a simple text file:</p>
<p>
<img alt="import1.png" src="img/103/14.png" width="505" height="406" />
</p>
<p>You need to specify the domain name list file and which existing zone to copy/shared zone data from:</p>
<p>
<img alt="import2.png" src="img/103/15.png" width="505" height="406" />
</p>
<p>And finally you can select which zones from the list you want to import:</p>
<p>
<img alt="import3.png" src="img/103/16.png" width="505" height="406" />
</p>
<hr class="JHHR" />
<h3 id="bulk">Bulk update primary DNS server IP for secondary zones</h3>
<p>Use this new option in the Bulk Update Wizard on your secondary servers when the IP address of your primary DNS server has changed to quickly update all your secondary zones:</p>
<p>
<img src="img/103/17.png" width="505" height="413" />
</p>
<p>
<img src="img/103/18.png" width="505" height="413" />
</p>
<hr class="JHHR" />
<h3 id="httpapi">New and updated HTTP API commands</h3>
<ul>
    <li>New "pluginstate", "getpluginconfig" and "updatepluginconfig" commands to fetch/update plug-in instance state/configuration data (added in v. 5.1 build 122).</li>
    <li>New "zonestatus" command to get the current status of a zone (added in v. 5.1 build 121).</li>
    <li>New "getconfig" and "updateconfig" commands - retrieves/updates the Simple DNS Plus configuration (Options dialog settings).
    </li>
    <li>New "zonegrouplist", "addzonegroup", "renamezonegroup", and "removezonegroup" commands to manage zone groups.
    </li>
    <li>New "aliaszonelist" and "addaliaszone" commands to manage zones using same zone file.
    </li>
    <li>New "comment" parameter added to "updatehost", "addrecord", and "updaterecord" commands for specifying record comments (no longer adds automatic comment "Added via HTTP API at ...").
    </li>
    <li>New "format" parameter added to "zonelist" command. The value can be either "xml" or "text". <br />
    This replaces the "listtype" parameter which still works but is now deprecated.
    </li>
    <li>New "suspendzone" and "resumezone" commands - see "Suspending Zones" above.
    </li>
    <li>XML version of the "zonelist" command has new "suspended" attribute - see "Suspending Zones" above.
    </li>
    <li>The "updatezone" command will no longer accept a "data" field without at least a valid SOA-record for primary zones (does not apply for secondary zones). </li>
</ul>
<hr class="JHHR" />
<h3 id="expired">Information bar for expired secondary zones</h3>
<p>When a secondary zone has expired (because of problems communicating with the primary DNS server) or has not yet been transferred from the primary DNS server, Simple DNS Plus plus will respond to queries for names under that zone with a "server failure" response.<br />
This new information bar makes it easier to recognize this situation:</p>
<p>
<img alt="expired.png" src="img/103/19.png" width="624" height="211" />
</p>
<hr class="JHHR" />
<h3 id="export">Export to standard boot file</h3>
<p>Simple DNS Plus v. 5.0 and later uses a proprietary database format for storing its list of DNS zones.<br />
While we hope you never need or want to use another DNS server, we don't want you to feel locked in either.<br />
This new Export Wizard function allows you to easily export the zone list to a standard boot file format which most DNS servers can either use directly or import from.<br />
Note: This function is also available in v. 5.0 as part of the external zone database viewer tool (ZoneDBViewer.exe).<br />
However moving it to the Export Wizard makes it easier to find and adds options to filter the exported file by zone groups and to exclude suspended zones.</p>
<p>
<img src="img/103/20.png" width="505" height="449" />
</p>
<hr class="JHHR" />
<h3 id="edns0">Automatic test of firewall EDNS0 support</h3>
<p>We introduced EDNS0 in Simple DNS Plus v. 5.0. EDNS0 is a relatively new addition to the DNS protocol and is a way to extend DNS UDP packet size and add other options to the DNS protocol.<br />
It turns out that many users have firewalls that block EDNS0 packets (typically Cisco PIX with older firmware).<br />
This can be very difficult to troubleshoot since you typically won't know that this is what you are looking for.<br />
So in v. 5.1 we have added an option to test for this problem at start up (enabled by default).<br />
If the test is negative, a warning will be logged (and written to the Windows Event Log if enabled), and Simple DNS Plus will then proceed without using EDNS0.</p>
<p>
<img alt="edns0test1.png" src="img/103/21.png" width="641" height="425" />
</p>
<p>
<img alt="edns0test2.png" src="img/103/22.png" width="546" height="250" />
</p>
<hr class="JHHR" />
<h3 id="misc">Miscellaneous</h3>
<ul>
    <li>The "New Zone Wizard" now supports /31 and /32 (single IP) reverse zones.
    </li>
    <li>Lists in IP Address Blocking dialog now permits selecting multiple items (shift/ctrl) for faster removal of many entries.
    </li>
    <li>Enhanced "Check for Updates" function (doesn't open browser).
    </li>
    <li>Extended data length for automatic SPF records (was limited 255 characters in previous versions, now 32767 characters.
    </li>
    <li>Removed v. 5.0 option "Refuse DNS requests for record type ANY".
    </li>
    <li>Moved options "Enable Round Robin (rotate DNS records in responses)" and "Always include NS referral in DNS responses from local zones" to "Inbound DNS Requests" section in Options dialog
    </li>
    <li>Renamed option "Only accept DNS responses from the IP address that request was sent to" to "Ignore responses not coming from the IP address that request was sent to" and moved it to "Outbound DNS Requests" section in Options dialog.
    </li>
    <li>Moved Active Log View settings to separate section in Options dialog.
    </li>
    <li>Now ignores duplicate DNS servers (different NS-names but same IP) when resolving.
    </li>
    <li>Options dialog opens with same section selected as the last time it was open during the same session (GUI/tray running).
    </li>
    <li>No longer sends 3rd request without EDNS0 - not needed with new EDNS0 test option.
    </li>
    <li>Now retries IXFR without EDNS0 when receiving FORMERR response (to counter bug in MS DNS Win2003).
    </li>
    <li>Zone group data moved to separate "_zonegroups.xml" file in data files directory (this data was part of "editrecs.config.xml" in v. 5.0) </li>
    <li>New option "Query plug-ins before local zones (plug-in data overrides local zones)" in Options dialog / Plug-Ins section (added in v. 5.1 build 115).</li>
</ul>
<hr class="JHHR" />
<h3 id="rfc">New RFC and draft support</h3>
<p>
- <a href="http://www.rfc-editor.org/rfc/rfc3164.txt" target="_blank">RFC3164</a> - The BSD syslog Protocol.<br />
- <a href="http://tools.ietf.org/html/draft-ietf-dnsext-forgery-resilience" target="_blank">draft-ietf-dnsext-forgery-resilience</a> - Measures for making DNS more resilient against forged answers.
</p>