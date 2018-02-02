---
id: 157
title: Scheduling OpsMgr PowerShell scripts
date: 2009-09-17T10:37:29+00:00
author: mats
layout: post
guid: http://www.opsmode.com/?p=157
permalink: /2009/09/scheduling-opsmgr-powershell-scripts/
aktt_notify_twitter:
  - 'yes'
categories:
  - OpsMgr
  - Powershell
tags:
  - OpsMgr
  - Powershell
---
When scheduling an Operations Manager PowerShell script you have to load the powershell snapins.

Insert this in the beginning of your script

_$ServerName = &#8220;hostname&#8221;
  
add-pssnapin &#8220;Microsoft.EnterpriseManagement.OperationsManager.Client&#8221;;
  
set-location &#8220;OperationsManagerMonitoring::&#8221;;
  
new-managementGroupConnection -ConnectionString:$ServerName;
  
set-location $ServerName;_