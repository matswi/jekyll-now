---
id: 344
title: Running both OpsMgr 2012 beta and 2007 R2 consoles on the same workstation
date: 2011-09-17T14:32:46+00:00
author: mats
layout: post
guid: http://www.opsmode.com/2011/09/running-both-opsmgr-2012-beta-and-2007-r2-consoles-on-same-client/
permalink: /2011/09/running-both-opsmgr-2012-beta-and-2007-r2-consoles-on-same-client/
categories:
  - Console
  - OpsMgr
tags:
  - Console
  - OpsMgr 2007 R2
  - OpsMgr 2012 Beta
---
Connecting to a OpsMgr 2012 beta management server with a OpsMgr 2007 R2 console doesn&#8217;t work either does connecting with the 2012 beta console to a 2007 R2 RMS.

If you like me wants to be able to connect to both a 2012 beta management group and a 2007 R2 management group you can run 2 consoles on the same workstation. Just start with running the OpsMgr 2012 beta setup on your workstation, if an OpsMgr R2 console is already installed it will be upgraded, otherwise just install the console. If you don&#8217;t want to go through the setup GUI just run this from an elevated command prompt: _setup.exe /silent /install /components:OMConsole /UseMicrosoftUpdate:[0|1]_

When this is done, load your R2 media and install the console from that one.

This will give you two folders in **%programfiles%**: 

[<img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="folder" border="0" alt="folder" src="http://www.opsmode.com/wp-content/uploads/2011/09/folder_thumb.png" width="298" height="65" />](http://www.opsmode.com/wp-content/uploads/2011/09/folder.png)

And also on the **Start menu** and **Programs and Features**: 

[<img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="startmenu" border="0" alt="startmenu" src="http://www.opsmode.com/wp-content/uploads/2011/09/startmenu_thumb.png" width="409" height="195" />](http://www.opsmode.com/wp-content/uploads/2011/09/startmenu.png)&#160;

[<img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="features" border="0" alt="features" src="http://www.opsmode.com/wp-content/uploads/2011/09/features_thumb.png" width="305" height="41" />](http://www.opsmode.com/wp-content/uploads/2011/09/features.png)

Now we are able to run the consoles simultaneously

[<img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="console" border="0" alt="console" src="http://www.opsmode.com/wp-content/uploads/2011/09/console_thumb.png" width="628" height="362" />](http://www.opsmode.com/wp-content/uploads/2011/09/console.png)

But you will soon notice that the Connect to Server.. windows is showing now and then when opening a console. This is also mentioned in this post:   
[http://www.opsmode.com/2011/03/manage-multiple-management-groups-with-powershell/](http://www.opsmode.com/2011/03/manage-multiple-management-groups-with-powershell/ "http://www.opsmode.com/2011/03/manage-multiple-management-groups-with-powershell/")

[<img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="connect to" border="0" alt="connect to" src="http://www.opsmode.com/wp-content/uploads/2011/09/connect-to_thumb.png" width="521" height="279" />](http://www.opsmode.com/wp-content/uploads/2011/09/connect-to.png)

To get rid of this I edit the shortcut and add **/Server:OPS-OMbeta-MS01.opsmgr.se** for my 2012 console and **/Server:OM.opsmode.local** for the 2007 R2 console   
"C:\Program Files\System Center Operations Manager 2007\Microsoft.MOM.UI.Console.exe" /Server:OM.opsmode.local   
"C:\Program Files\System Center Operations Manager 2012\Console\Microsoft.EnterpriseManagement.Monitoring.Console.exe" /server:OPS-OMbeta-MS01.opsmgr.se