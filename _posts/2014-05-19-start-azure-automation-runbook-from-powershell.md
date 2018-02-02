---
id: 447
title: Start Azure Automation runbook from powershell
date: 2014-05-19T12:04:57+00:00
author: mats
layout: post
guid: http://www.opsmode.com/?p=447
permalink: /2014/05/start-azure-automation-runbook-from-powershell/
categories:
  - Azure
  - Orchestrator
  - Powershell
tags:
  - Automation
  - Azure
  - Orchestrator
  - Powershell
---
With the new Azure Automation cmdlets I wrote about in the <a href="http://www.opsmode.com/2014/05/azure-automation-powershell-cmdlets/" target="_blank">previous post</a> we are now able to start runbooks from outside of Azure.   
Here is an example how to start a runbook and also get the output from the runbook:

> 
> $AzureAccount = "Name of Azure Automation Account"   
> $RBname = "Name of runbook to start"   
> $Params = @{"Param1" = "Value1";"Param2" = "Value2"} 
> 
> $RBjob = Start-AzureAutomationRunbook -AutomationAccountName $AzureAccount -name $RBname -Parameters $Params 
> 
> DO {   
> &#160;&#160;&#160; $RBjobId = Get-AzureAutomationJob -AutomationAccountName $AzureAccount -id $RBjob.Id   
> &#160;&#160;&#160; $RBjobstatus = $RBjobId.Status   
> &#160;&#160;&#160; } Until ($RBjobstatus -eq "Completed") 
> 
> Get-AzureAutomationJobOutput -AutomationAccountName $AzureAccount -Id $RBjob.Id -stream Any