---
id: 91
title: 'PowerShell: List agent based on setting'
date: 2009-06-15T12:48:31+00:00
author: mats
layout: post
guid: http://www.opsmode.com/?p=91
permalink: /2009/06/powershell-list-agent-based-on-agent-setting/
categories:
  - Powershell
tags:
  - Agent
  - Powershell
---
Based on the data you get from the cmdlet _get-agent_ you can list all agents with a specific setting.

This line for example, will list all agents with the Agent Proxy setting enabled:   
_get-agent | where {$_.ProxyingEnabled -like $true}_

Change _$_.ProxyingEnabled_ to _$_.ManuallyInstalled_ and you’ll get a list with all manually installed agents.

In OM2007 SP1 there is a bug on updating the ManuallyInstalled property, so that wont work. This is corrected in R2.   
If you dont have to use powershell there is a workaround in [this thread](http://social.technet.microsoft.com/Forums/en-US/operationsmanagerdeployment/thread/78f93ce1-deaf-4188-87eb-6700d98f22f4).

&#160;   
Your options are:   
_PrimaryManagementServerName   
Id   
LastModified   
Name   
DisplayName   
HostComputer   
HostedHealthService   
HealthState   
PrincipalName   
NetworkName   
ComputerName   
Domain   
IPAddress   
Version   
RequestCompression   
CommunicationPort   
MaximumSizeOfAllTransferredFilesBytes   
MaximumQueueSizeBytes   
ManuallyInstalled   
InstallTime   
InstalledBy   
CreateListener   
AuthenticationName   
ActionAccountIdentity   
HeartbeatInterval   
ProxyingEnabled   
ManagementGroup   
ManagementGroupId_