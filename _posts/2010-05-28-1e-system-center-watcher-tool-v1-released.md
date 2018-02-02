---
id: 189
title: 1E System Center Watcher Tool v1 released
date: 2010-05-28T23:07:00+00:00
author: mats
layout: post
guid: http://www.opsmode.com/?p=189
permalink: /2010/05/1e-system-center-watcher-tool-v1-released/
categories:
  - OpsMgr
  - tool
---
I couple of weeks ago I had the pleasure to beta test Dan Kregors tool OMWatcher. And I must say, this is a great tool that I will use at many customer sites…

This is the answer when some one is asking: “_But who is watching the watcher?”_ Meaning, who is monitoring OpsMgr. Well the answer i OMWatcher!

> ##### Overview
> 
> The 1E OMWatcher tool for System Center Operations Manager 2007 fills an important, and often overlooked gap in every OpsMgr environment.
> 
> Arising from the question…
> 
> _“Who’s watching the watcher?”_
> 
> … 1E OMWatcher is designed to monitor the 3 critical service on the Root Management Server (SDK, Config and HealthService). 1E OMWatcher will proactively mitigate unnecessary and potentially expensive downtime by ensuring the RMS is active (via a ping), and taking remedial action should one of the core RMS services stop. In addition, 1E OMWatcher will notify administrators (via email) were an issue arises.
> 
> 1E OMWatcher should be installed on a server other than the RMS (preferably on a secondary Management Server), and configured to run under an account that has local administrative rights on the RMS.
> 
> ##### Key Features
> 
>   * Actively pings the RMS at regular polling intervals, alerting (via email) should the RMS not respond (indicating the potential for the server to be offline).
>   * Checking the status for the 3 OpsMgr services, ensuring they are running. In the event that a service is stopped, OMWatcher will attempt to restart the service, and will alert (via email) that the service had stopped.
>   * Checking the startmode for the OpsMgr service, they are not set to disabled. In the event that a service is set to disabled, OMWatcher will set the service to Automatic, restart the service, and will alert (via email) that the service was set to Disabled and stopped.

More here: <a title="http://opsm.gr/2010/05/28/1e-system-center-watcher-tool-v1-now-available/" href="http://opsm.gr/2010/05/28/1e-system-center-watcher-tool-v1-now-available/" target="_blank">http://opsm.gr/2010/05/28/1e-system-center-watcher-tool-v1-now-available/</a>
  
Download here (registration required): <a title="http://www.1e.com/Downloads/FreeTools/Index.aspx" href="http://www.1e.com/Downloads/FreeTools/Index.aspx" target="_blank">http://www.1e.com/Downloads/FreeTools/Index.aspx</a>