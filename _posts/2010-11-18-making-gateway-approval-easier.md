---
id: 239
title: Making Gateway approval easier
date: 2010-11-18T17:56:29+00:00
author: mats
layout: post
guid: http://www.opsmode.com/2010/11/making-gateway-approval-easier/
permalink: /2010/11/making-gateway-approval-easier/
categories:
  - OpsMgr
  - tool
---
I am right now deploying a lot of Gateway servers so to make the Gateway approval a little easier I wrote a little script.
  
There is probably some way of doing this even better, but here goes:

> <span style="font-size: xx-small;">$MS = Read-Host &#8220;FQDN of the Management Server&#8221;<br /> $GW = Read-Host &#8220;FQDN of the Gateway&#8221;<br /> $Site = Read-Host &#8220;Name of the site&#8221;</span>
> 
> <span style="font-size: xx-small;">& &#8220;Microsoft.EnterpriseManagement.GatewayApprovalTool.exe&#8221; /ManagementServerName=$MS /GateWayName=$GW /Site=$Site /Action=Create&#8221;</span>

**Note:
  
** When using the GateWayApprovalTool you need to have Write Permissions on the SQL Instance that holds the OpsMgr database.