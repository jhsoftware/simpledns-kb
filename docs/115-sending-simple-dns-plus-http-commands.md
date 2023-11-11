---
category: 10
frontpage: false
comments: true
refs: 85
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# Sending Simple DNS Plus HTTP Commands

Simple DNS Plus can be prompted to perform certain actions through HTTP - either directly from a browser, or any other program that can communicate through HTTP.

If you are running Simple DNS Plus 4.00 or later with the default configuration on the same computer that you are currently browsing from, [click here](http://127.0.0.1:8053/){target=_blank} to test with YOUR server (opens http://127.0.0.1:8053).

The settings related to this are configured in the Options dialog / HTTP API section:

![](img/115/1.png)

Adjust these settings to match you IP addresses and security requirements.  
By default it listens on IP 127.0.0.1 which means that connections can only be made from the same computer.

The different "commands" that Simple DNS Plus can accept through the HTTP API are listed and described in the help file "How to use the HTTP API" section. See [on-line version](https://simpledns.plus/helplink?p=ht_http).

The following is a simple example of a web-page where a user can enter a host name and an IP address, and server side code that sends this data to Simple DNS Plus behind the scenes to create/update the A-record for the entered host name. This could be used as a simple dynamic DNS service.

Note this code is for demonstration purposes only - appropriate input validation and error checking should be added for this to be used on a real web-site.

Sample code in: [ASP.NET 2.0](#aspnet), [Classic ASP](#asp), [PHP](#php)

### ASP.NET 2.0{#aspnet}

To use this sample code, simply copy the code below into notepad, save it with a file name ending with ".aspx" in your web-site folder. The web-server and web-site must be configured for ASP.NET 2.0.

<pre>
&lt;%@ Page Language="VB" %&gt;
&lt;script runat="server"&gt;
Protected Sub Page_Load(ByVal sender As Object, ByVal e As System.EventArgs)
    If Not Page.IsPostBack Then Exit Sub
    Dim HostName, IPAddr, PostData As String
    HostName = txtHostName.Text.Trim
    IPAddr = txtIPAddr.Text.Trim
    PostData = "host=" &amp; Server.UrlEncode(HostName) &amp; _
    "&amp;data=" &amp; Server.UrlEncode(IPAddr)
    Dim wc As New System.Net.WebClient()
    '*** un-comment the following line if you have set a password
    '*** for the HTTP API in the Simple DNS Plus options dialog
    'wc.Credentials = New System.Net.NetworkCredential("admin", "password")
    lblResult.Text = wc.UploadString("http://127.0.0.1:8053/updatehost", PostData)
End Sub
&lt;/script&gt;
&lt;html&gt;
    &lt;body&gt;
        &lt;form id="form1" runat="server"&gt;
            Host name: &lt;asp:TextBox ID="txtHostName" runat="server" /&gt;&lt;br&gt;
            IP address: &lt;asp:TextBox ID="txtIPAddr" runat="server" /&gt;&lt;br&gt;
            &lt;asp:Button ID="btnSubmit" runat="server" Text="Submit" /&gt;&lt;br&gt;
            &lt;asp:Label ID="lblResult" runat="server" /&gt;
        &lt;/form&gt;
    &lt;/body&gt;
&lt;/html&gt;
</pre>

### Classic ASP{#asp}

The following classic ASP code uses the Windows HTTP Services 5.1 (WinHTTP) COM object to communicate with Simple DNS Plus. WinHTTP 5.1 is part of the Windows operating system for Windows 2000 SP3, Windows XP SP1, and all later Windows versions.  
To use this sample code, simply copy the code below into notepad, save it with a file name ending with ".asp" in your web-site folder. The web-server and web-site must be configured for classic ASP.

<pre>
&lt;html&gt;
    &lt;body&gt;
        &lt;form method="POST"&gt;
            Host name: &lt;input type="text" name="hostname"&gt;&lt;br&gt;
            IP address: &lt;input type="text" name="ipaddr"&gt;&lt;br&gt;
            &lt;input type=submit&gt;&lt;br&gt;
        &lt;/form&gt;
        &lt;%
        If Request.ServerVariables("HTTP_METHOD")="POST" Then
            Dim HostName, IPAddr, PostData, HttpReq
            HostName=Trim(Request.Form("hostname"))
            IPAddr=Trim(Request.Form("ipaddr"))
            PostData="host=" &amp; Server.UrlEncode(HostName) &amp; _
            "&amp;data=" &amp; Server.UrlEncode(IPAddr)
            Set HttpReq=Server.CreateObject("WinHttp.WinHttpRequest.5.1")
            HttpReq.open "POST", "http://127.0.0.1:8053/updatehost"
            '*** un-comment the following line if you have set a password
            '*** for the HTTP API in the Simple DNS Plus options dialog
            'HttpReq.SetCredentials "admin", "password", 0
            HttpReq.send PostData
            Response.Write Server.HTMLEncode(HttpReq.ResponseText)
        End If
        %&gt;
    &lt;/body&gt;
&lt;/html&gt;
</pre>

### PHP{#php}

The following PHP code uses the cURL library to communicate with Simple DNS Plus. cURL is typically installed with PHP and included with the full PHP distribution.  
To use this sample code, simply copy the code below into notepad, save it with a file name ending with ".php" in your web-site folder. The web-server and web-site must be configured for PHP.

<pre>
&lt;html&gt;
&lt;body&gt;
&lt;form method="POST"&gt;
Host name: &lt;input type="text" name="hostname"&gt;&lt;br&gt;
IP address: &lt;input type="text" name="ipaddr"&gt;&lt;br&gt;
&lt;input type=submit&gt;&lt;br&gt;
&lt;/form&gt;
&lt;?php
if(isset($_POST["hostname"]) || isset($_POST["ipaddr"])){
$hostname = urlencode(trim($_POST["hostname"]));
$ipaddr = urlencode(trim($_POST["ipaddr"]));
$postdata = "host=$hostname&amp;data=$ipaddr";
$url = "http://127.0.0.1:8053/updatehost";
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($ch, CURLOPT_HEADER, 0);
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS, $postdata);
//*** un-comment the following line if you have set a password
//*** for the HTTP API in the Simple DNS Plus options dialog
//curl_setopt($ch, CURLOPT_USERPWD, "admin:password");
$result = curl_exec($ch); 
curl_close($ch);
print $result;
}
?&gt;
&lt;/body&gt;
&lt;/html&gt;
</pre>