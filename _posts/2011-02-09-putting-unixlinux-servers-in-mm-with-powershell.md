---
id: 263
title: Putting Unix/Linux servers in MM with Powershell
date: 2011-02-09T13:04:52+00:00
author: mats
layout: post
guid: http://www.opsmode.com/2011/02/putting-unixlinux-servers-in-mm-with-powershell/
permalink: /2011/02/putting-unixlinux-servers-in-mm-with-powershell/
categories:
  - OpsMgr
  - Powershell
---
I saw a question in the TechNet forum today on how to schedule Maintenance mode for Unix/Linux servers.   
After some testing this powershell script came out, put it in the task scheduler to automate it, or even better put it in the Opalis policy that is taking care of your maintenance..

> $rmsServer=&#8221;**RMS.fqdn**&#8221;   
> add-pssnapin &#8220;Microsoft.EnterpriseManagement.OperationsManager.Client&#8221;;   
> Set-Location &#8220;OperationsManagerMonitoring::&#8221;;   
> $mgConnection = New-ManagementGroupConnection -connectionString:$rmsServer;
> 
> Set-Location $rmsServer; 
> 
> $unixClass = get-monitoringclass -name "Microsoft.Unix.Computer"   
> $monObject = Get-MonitoringObject -monitoringclass:$unixClass   
> $mmServer = $monObject | where {$_.displayname -eq "**unixserver.fqdn**"}
> 
> New-MaintenanceWindow -MonitoringObject $mmServer -Comment "Enter maintenance mode reason here" -StartTime (Get-Date) -EndTime (Get-Date).AddMinutes(60)