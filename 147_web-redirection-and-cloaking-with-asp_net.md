---
title: Web redirection and "cloaking" (ASP.NET)
category: 16
frontpage: false
comments: true
vgroup: 3
vname: ASP.NET
vsort: 1
refs: 148,179
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
<p>NOTE: You can also the web redirection and cloaking using the <a href="https://simpledns.plus/plugin-httpredir">HTTP Redirector plug-in</a>.</p>
<p>Some ISPs offer "web redirection" service, where they will redirect web-requests for your domain name to another website.<br />
For example from <strong>www.myname.com</strong> to <strong>www.ispname.com/~myname</strong><br />
or from <strong>www.myname.com</strong> to <strong>myname.ispname.com</strong>.</p>
<p>You can do simple redirection with CNAME (alias) DNS records, but this does not work if you need to redirect to a sub-directory (like the first sample above), or if the destination web-server is using virtual hosting (multiple domain names on the same IP address).</p>
<p>Domain redirection is most often done on a web-server with some type of script.<br />
(often in combination with a database if redirecting many domain names)</p>
<p>You can do this with ASP.NET on IIS. The following examples are in VB.NET.<br />
<br />
First create a DNS A-records for the domain name pointing to the IIS web-server that will do the redirection (not the destination web-server).</p>
<p>Then create a "default.aspx" page on this web-server with the following contents:</p>

<pre>&lt;%
Select Case Request.Url.Host
Case "myname.com", "www.myname.com"
&nbsp; Response.Redirect("http://www.ispname/~myname")
Case "othername.com", "www.othername.com"
&nbsp; Response.Redirect("http://www.ispname/~othername")
End Select 
%&gt;</pre>

<p>Add "case" statements for each domain name you want to redirect.<br />
You can automate this further with a database containing each domain name and corresponding redirect destination.</p>
<p>On IIS you can also point 404 errors (page not found) to this ASP page so requests for individual pages will also be redirected correctly.</p>
<p>Another variant of this is called "cloaking" - where your domain name still shows in the browser's address bar even after the redirection.<br />
This is achieved by "hiding" the redirection in a frame-set where the first frame is zero width or height:</p>

<pre>&lt;%
Dim destURL As String
Select Case Request.Url.Host
Case "myname.com", "www.myname.com"
&nbsp; destURL = "http://www.ispname/~myname"
Case "othername.com", "www.othername.com"
&nbsp; destURL = "http://www.ispname/~othername"
End Select
%&gt;
&lt;html&gt;
&nbsp; &lt;frameset cols="0,*" framespacing="0" border="0" frameborder="0"&gt;
&nbsp;&nbsp;&nbsp; &lt;frame name="zero" scrolling="no" noresize&gt;
&nbsp;&nbsp;&nbsp; &lt;frame name="main" src="&lt;%=destURL%&gt;"&gt;
&nbsp;&nbsp;&lt;/frameset&gt;
&lt;/html&gt;</pre>