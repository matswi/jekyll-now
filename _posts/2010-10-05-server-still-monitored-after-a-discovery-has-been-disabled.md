---
id: 225
title: Server still monitored after a discovery has been disabled
date: 2010-10-05T16:56:01+00:00
author: mats
layout: post
guid: http://www.opsmode.com/2010/10/server-still-monitored-after-a-discovery-has-been-disabled/
permalink: /2010/10/server-still-monitored-after-a-discovery-has-been-disabled/
categories:
  - OpsMgr
  - Powershell
---
I see this question a lot in the technet forums: 

“I don’t want to monitor the IIS on this server and have disabled the discovery, but the server wont disappear. How do I get rid of it?”

To resolve this you just need to open a Operations Manager Shell and enter: **Remove-DisabledMonitoringObject**

**Description of cmdlet:**   
Removes all monitoring objects for which discovery is disabled. For example, if you created an override to disable discovery for a particular database on a database server, calling this cmdlet would cause the removal of this database from Operations Manager.