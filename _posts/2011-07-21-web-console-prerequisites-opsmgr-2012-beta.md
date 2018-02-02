---
id: 326
title: Web Console prerequisites, OpsMgr 2012
date: 2011-07-21T17:43:51+00:00
author: mats
layout: post
guid: http://www.opsmode.com/2011/07/web-console-prerequisites-opsmgr-2012-beta/
permalink: /2011/07/web-console-prerequisites-opsmgr-2012-beta/
categories:
  - OpsMgr
  - Powershell
tags:
  - OpsMgr 2012 Beta
  - Powershell
  - Web Console
---
When installing the Web Console there is a couple of components that is required, the Operations Manager 2012 Supported Configuration ([http://technet.microsoft.com/en-us/library/hh205990.aspx](http://technet.microsoft.com/en-us/library/hh205990.aspx "http://technet.microsoft.com/en-us/library/hh205990.aspx")) list these:

  * Recommended processor speed: 2.8 GHz or faster.
  * Minimum memory: not less than 2 GB.
  * Operating System: Windows Server 2008 R2
  * Processor Architecture: must be AMD64
  * Internet Information Services (IIS) v7.5 or later, with the IIS Management Console and the following role services installed: 
      * Static Content 
      * Default Document 
      * Directory Browsing 
      * HTTP Errors 
      * HTTP Logging 
      * Request Monitor 
      * Request Filtering
      * Static Content Compression
      * Web Server (IIS) Support
      * IIS 6 Metabase Compatibility
      * ASP.NET 
      * Windows Authentication
  * Default website: must have an http or https binding configured
  * Both .NET Framework 3.5 SP1 and .NET Framework 4 is required for setup to run. For more information, see the following. 
      * [.NET Framework 3.5 SP1 redistributable package](http://go.microsoft.com/fwlink/p/?LinkId=214947)
      * [.NET Framework 4 redistributable package](http://go.microsoft.com/fwlink/p/?LinkId=201924)

&#160;

The role services is easily installed with powershell, which makes it a little quicker then using Server Manager GUI:

> Import-Module ServerManager   
> Add-WindowsFeature NET-Framework-Core,Web-WebServer,Web-Static-Content,Web-Default-Doc,Web-Dir-Browsing,Web-Http-Errors,Web-Asp-Net,Web-Http-Logging,Web-Request-Monitor,Web-Windows-Auth,Web-Filtering,Web-Stat-Compression,Web-Mgmt-Console,Web-Metabase

As you might see I&#8217;ve also added _NET-Framework-Core_&#160; (.NET Framework 3.5.1) there as well.

When the IIS install is ready you should install .NET Framework 4. ([http://www.microsoft.com/download/en/details.aspx?id=17851](http://www.microsoft.com/download/en/details.aspx?id=17851 "http://www.microsoft.com/download/en/details.aspx?id=17851"))

If you installed .NET Framework 4 before installing the IIS you&#8217;ll get an error:

[<img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="The ASP.NET 4.0 handler is not registered with IIS." border="0" alt="The ASP.NET 4.0 handler is not registered with IIS." src="http://www.opsmode.com/wp-content/uploads/2011/07/image_thumb.png" width="647" height="72" />](http://www.opsmode.com/wp-content/uploads/2011/07/image.png)   
_<font size="1">The ASP.NET 4.0 handler is not registered with IIS</font>_&#160;

To fix this, the Operations Manager 2012 Deployment document states that you should run:

> %WINDIR%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -r

I suggest that that you add the **_-enable_** option (%WINDIR%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -enable -r), that enables the ASP.NET ISAPI extension. And gets rid of this prerequisites error:

[<img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="Web Console cannot operate properly because the ISAPI and CGI Restrictions in Internet Information Services (IIS) are disabled or missing for ASP.NET 4.0." border="0" alt="Web Console cannot operate properly because the ISAPI and CGI Restrictions in Internet Information Services (IIS) are disabled or missing for ASP.NET 4.0." src="http://www.opsmode.com/wp-content/uploads/2011/07/image_thumb1.png" width="645" height="109" />](http://www.opsmode.com/wp-content/uploads/2011/07/image1.png)   
<font size="1"><em>Web Console cannot operate properly because the ISAPI and CGI Restrictions in Internet Information Services (IIS) are disabled or missing for ASP.NET 4.0.</em></font>

Lastly do a restart of the server before running the setup again.