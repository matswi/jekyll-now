---
id: 131
title: IIS Components when installing OpsMgr 2007 Web console on Windows 2008
date: 2009-04-03T13:04:00+00:00
author: mats
layout: post
guid: http://www.opsmode.com/?p=131
permalink: /2009/04/iis-components-when-installing-opsmgr-2007-web-console-on-windows-2008/
categories:
  - Console
  - OpsMgr
  - Windows Server 2008
tags:
  - Console
  - OpsMgr 2007
  - OpsMgr 2007 R2
  - Windows Server 2008
---
When installing the Operations Manager 2007 web console on Windows Server 2008 you need to install the following IIS components:   
[<img style="border-right-width: 0px; display: block; float: none; border-top-width: 0px; border-bottom-width: 0px; margin-left: auto; border-left-width: 0px; margin-right: auto" title="iis" border="0" alt="iis" src="http://www.opsmode.com/wp-content/uploads/2009/07/iis_thumb.jpg" width="271" height="665" />](http://www.opsmode.com/wp-content/uploads/2009/07/iis.jpg)

This can also be installed with a powershell script:

> Import-Module ServerManager   
> Add-WindowsFeature NET-Framework-Core,Web-Metabase,Web-WMI,Web-Static-Content,Web-Default-Doc,Web-Dir-Browsing,Web-Http-Errors,Web-Asp-Net,Web-Net-Ext,Web-ISAPI-Ext,Web-ISAPI-Filter,Web-Filtering,Web-Windows-Auth -restart