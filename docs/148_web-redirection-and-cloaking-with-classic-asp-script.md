---
category: 16
frontpage: false
comments: true
vgroup: 3
vname: Classis ASP script
vsort: 2
refs: 179,147
created-utc: 2019-01-01
modified-utc: 2019-01-01
---
# Web redirection and "cloaking" (Classis ASP script)

NOTE: You can also the web redirection and cloaking using the [HTTP Redirector plug-in](https://simpledns.plus/plugin-httpredir).

Some ISPs offer "web redirection" service, where they will redirect web-requests for your domain name to another website.  
For example from **www.myname.com** to **www.ispname.com/~myname**  
or from **www.myname.com** to **myname.ispname.com**.

You can do simple redirection with CNAME (alias) DNS records, but this does not work if you need to redirect to a sub-directory (like the first sample above), or if the destination web-server is using virtual hosting (multiple domain names on the same IP address).

Domain redirection is most often done on a web-server with some type of script.  
(often in combination with a database if redirecting many domain names)

You can do this with ASP script on IIS or PWS.

First create a DNS A-records for the domain name pointing to the IIS/PWS web-server that will do the redirection (not the destination web-server).

Then create a "default.asp" page on this web-server with the following contents:

<pre>
&lt;%<br />
Select Case Request.ServerVariables("HTTP_HOST")
Case "myname.com", "www.myname.com"
&nbsp; Response.Redirect "http://www.ispname/~myname"
Case "othername.com", "www.othername.com" 
&nbsp; Response.Redirect "http://www.ispname/~othername"
End Select
%&gt;
</pre>

Add "case" statements for each domain name you want to redirect.  
You can automate this further with a database containing each domain name and corresponding redirect destination.

On IIS you can also point 404 errors (page not found) to this ASP page so requests for individual pages will also be redirected correctly.

Another variant of this is called "cloaking" - where your domain name still shows in the browser's address bar even after the redirection.  
This is achieved by "hiding" the redirection in a frame-set where the first frame is zero width or height:

<pre>
&lt;%
Select Case Request.ServerVariables("HTTP_HOST")
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
&nbsp; &lt;/frameset&gt; 
&lt;/html&gt;
</pre>