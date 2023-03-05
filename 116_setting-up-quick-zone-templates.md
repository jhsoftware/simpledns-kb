---
category: 11
frontpage: false
comments: true
refs: 98,95
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# Setting up Quick Zone Templates

In Simple DNS Plus v. 5.0 and later, the "Quick Zone Wizard" (formerly "Quick Domain Wizard") is template based, and supports multiple templates through a drop-down menu on the Quick button.

Making and using your own templates is easy and can be a great help and time saver if you frequently setup new DNS zones.  
You can use templates for example to ensure company standards are followed, automate which DNS records to add for different customer types, make it easier for novice staff, etc.

Templates can simply be static standard RFC based zone files, but they can also become "active" by adding ASP style tags (&lt;%...%&gt;), VB.NET code, and custom input fields.

### Very Simple Templates - Copy, Rename, Done

You can add a new template simply by copying and renaming an existing zone file.  
A simple template like this allows you to easily create new zones with exactly the same layout each time.

First pick an existing zone (or make a new one) that you want to use as a template for new zones.  
Copy the zone file for that zone to the "Templates" directory.

The location of zones files is configured in the Options dialog / DNS / Data Files section. By default this is:  
Windows Vista/2008: C:\ProgramData\JH Software\Simple DNS Plus\ZoneFiles  
Earlier Windows versions: C:\Documents and Settings\All Users\Application Data\JH Software\Simple DNS Plus\ZoneFiles

The "Templates" directory is found at (create it if it isn't there already):  
Windows Vista/2008: C:\ProgramData\JH Software\Simple DNS Plus\Templates  
Earlier Windows versions: C:\Documents and Settings\All Users\Application Data\JH Software\Simple DNS Plus\Templates

![](img/116/1.png)

In the "templates" directory, rename the zone file to whatever you want to call the template + ".dnstp":  
(make sure the Windows Explorer "Hide extensions for known file types" setting is turned off)

![](img/116/2.png)

That's it - Now you have a working template!  
To use it, simply select it from the drop-down menu on the Quick button:

![](img/116/3.png)

And you will get to the Quick Zone Wizard dialog for the new template:

![](img/116/4.png)

Enter a zone name, and the wizard will create a new zone exactly like the one you copied the template file from.

If you want your new template to be the default template so you can use it by just hitting the "Quick" button, simply name the template file "_default.dnstp".

### Customizing the Quick Zone Wizard dialog

You can add an introduction text as well as custom input fields to the wizard dialog by adding some special XML code at the top of the template file.  
For example; open the template file with a text editor, and add the XML shown here:

![](img/116/5.png)

After saving the template file, the Quick Zone Wizard dialog for this template will look like this:

![](img/116/6.png)

### Adding input fields

To add input fields to the wizard dialog, you add &lt;INPUT&gt; elements to the XML.  
You can use the data entered in the input field by adding an ASP style tag &lt;%=input_field_id%&gt; wherever you want the data appear in the zone file:

![](img/116/7.png)

After saving the template file, the Quick Zone Wizard dialog will have a new "Server IP" input field:

![](img/116/8.png)

And the resulting zone will have an A-record for "www.&lt;zonename&gt;" pointing to the entered IP address.

### Input field types and attributes

You can add as many input fields as you need (above a certain number the dialog will just get a scroll bar).

For each input field (&lt;INPUT&gt; element) you must specify a "type" attribute, which controls what style of input control is used and what type of variable the entered data is returned as:

<table style="background-color: #f0f0ff; border-collapse: collapse;" border="1" bordercolor="black" cellpadding="2">
    <tbody>
        <tr>
            <th>type value</th>
            <th>Variable type</th>
            <th>Other attributes</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>IPV4</td>
            <td>String</td>
            <td>id, title, value, required</td>
            <td>An IP address entry box with a lookup button</td>
        </tr>
        <tr>
            <td>IPV6</td>
            <td>String</td>
            <td>id, title, value, required</td>
            <td>An IPv6 address entry box</td>
        </tr>
        <tr>
            <td>DOMAIN</td>
            <td>String</td>
            <td>id, title, value, required</td>
            <td>A domain name entry box</td>
        </tr>
        <tr>
            <td>TEXT</td>
            <td>String</td>
            <td>id, title, value, required</td>
            <td>A input box which accepts any entry</td>
        </tr>
        <tr>
            <td>TTL</td>
            <td>Integer</td>
            <td>id, title, value</td>
            <td>A TTL (time to live) entry control</td>
        </tr>
        <tr>
            <td>CHECK</td>
            <td>Boolean</td>
            <td>id, title, checked</td>
            <td>A check box</td>
        </tr>
        <tr>
            <td>SELECT</td>
            <td>String</td>
            <td>id, title, required</td>
            <td>A drop-down selection control</td>
        </tr>
    </tbody>
</table>
IMPORTANT: To ensure proper formatting in the zone file, make sure to use the correct type rather than just using TEXT for everything.  
For example the DOMAIN type automatically punycodes IDN domain names, adds a trailing dot, etc. which doesn't happen with the TEXT type.

Other &lt;INPUT&gt; element attributes:

<table style="background-color: #f0f0ff; border-collapse: collapse;" border="1" bordercolor="black" cellpadding="2">
    <tbody>
        <tr>
            <th>Attribute</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>id</td>
            <td>Unique name of the variable that the entered data is returned in (required)</td>
        </tr>
        <tr>
            <td>title</td>
            <td>Lead text for the input field (required)</td>
        </tr>
        <tr>
            <td>value</td>
            <td>Default value</td>
        </tr>
        <tr>
            <td>required</td>
            <td>"true" or "false" indicating if data entry is required (defaults to "true")</td>
        </tr>
        <tr>
            <td>checked</td>
            <td>"true" or "false" indicating if the checkbox is checked (defaults to "false") </td>
        </tr>
    </tbody>
</table>
"SELECT" type Input fields must have &lt;OPTION&gt; sub-elements. Each of these elements contains the text value of a selection. One of the &lt;OPTION&gt; elements may have a *selected="true"* attribute to specify the default selection.

### Adding program code

Just like an ASP page, you can add program code (VB.NET) to a template file between &lt;% ... %&gt; tags.  
In the following example, we first add a drop-down selection control used to select which web-server we want to host a new customer's domain name on, and then add code to populate the zone with different data based on the selection - or cancel the process if an unavailable server is selected:

![](img/116/9.png)

The dialog will now have a drop-down control, and will generate the new zone according to the template program code:

![](img/116/10.png)

### More details

1) After a template has been processed (with or without input fields/program code), Simple DNS Plus will automatically check all SOA, NS, MX, CNAME, and SRV records in the generated zone to see if they reference any host names within the same zone, and if so, if A-records matching those names exist.  
If any A-records are missing, it will then ask for their IP addresses and add the A-records:

![](img/116/11.png)

For example if your template has an input field asking for a host name (DOMAIN) for a mail server (MX-record), you won't know if the user enters a host name belonging in the same zone or somewhere else.  
So should you also have an IP address input field for the mail server A-record?  
No, simply leave it to Simple DNS Plus to ask for the IP address and add an A-record if the host name entered by the users turns out to belong in the same zone.

2) A number of pre-set ReadOnly variables are available for use in your code:

<table style="background-color: #f0f0ff; border-collapse: collapse;" border="1" bordercolor="black" cellpadding="2">
    <tbody>
        <tr>
            <th>Variable name</th>
            <th>Type</th>
            <th>Description</th>
        </tr>
        <tr>
            <td>ServerName</td>
            <td>String</td>
            <td>The name of this DNS server in zone file format</td>
        </tr>
        <tr>
            <td>AdminEmail</td>
            <td>String</td>
            <td>The admin e-mail address of this DNS server in zone file domain name format</td>
        </tr>
        <tr>
            <td>defSOASerial</td>
            <td>Integer</td>
            <td>The default SOA-record serial number (see "Default Zone Values" dialog)</td>
        </tr>
        <tr>
            <td>defSOARefresh</td>
            <td>Integer</td>
            <td>The default SOA-record Refresh interval (see "Default Zone Values" dialog)</td>
        </tr>
        <tr>
            <td>defSOARetry</td>
            <td>Integer</td>
            <td>The default SOA-record Retry interval (see "Default Zone Values" dialog)</td>
        </tr>
        <tr>
            <td>defSOAExpire</td>
            <td>Integer</td>
            <td>The default SOA-record Expire time (see "Default Zone Values" dialog) </td>
        </tr>
        <tr>
            <td>defSOAMinimum</td>
            <td>Integer</td>
            <td>The default SOA-record Minimum TTL (see "Default Zone Values" dialog)</td>
        </tr>
        <tr>
            <td>defNS2Servers</td>
            <td>String()</td>
            <td>The default secondary DNS servers (see "Default Zone Values" dialog) </td>
        </tr>
        <tr>
            <td>defAllowZT</td>
            <td>String</td>
            <td>The default allowed zone transfer IPs (see "Default Zone Values" dialog) </td>
        </tr>
        <tr>
            <td>defNotifyNS</td>
            <td>Boolean</td>
            <td>Notify DNS servers in zone level NS-records (added in v. 5.2 build 119).</td>
        </tr>
        <tr>
            <td>defAlsoNotify</td>
            <td>String</td>
            <td>Additional DNS server IP addresses to notify (added in v. 5.2 build 119).</td>
        </tr>
        <tr>
            <td>defDefaultTTL</td>
            <td>Integer</td>
            <td>The default "Defaut TTL" (see "Default Zone Values" dialog) </td>
        </tr>
        <tr>
            <td>ZoneName</td>
            <td>String</td>
            <td>The name of the zone being created in zone file format.</td>
        </tr>
    </tbody>
</table>
3) If you find that your template generates more of the zone file dynamically than what is static, you may want to write out the whole zone file or parts of it through code by appending text to the "ZoneFile" StringBuilder object (similar to "Response.Write" in ASP). For example:

`ZoneFile.AppendLine("@ A 1.2.3.4")`

4) If you want to add classes or sub-routines (sub/function) to the template code, you need to put these in a special &lt;%! %&gt; block. For example:

```
<%! Function Add(a As Integer, b As Integer) As Integer
Return a + b
End Function %>
```

5) If you want to use other .NET assemblies from your template code, you can reference these by adding &lt;ASSEMBLY&gt; elements to the &lt;QUICKZONE&gt; XML. For example:

```
<QUICKZONE>
<ASSEMBLY>system.dll</ASSEMBLY>
<QUICKZONE>
```

