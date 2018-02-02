---
id: 198
title: The new Operations Manager Management pack 6.1.7672.0
date: 2010-06-30T11:01:45+00:00
author: mats
layout: post
guid: http://www.opsmode.com/?p=198
permalink: /2010/06/the-new-operations-manager-management-pack-6-1-7672-0/
categories:
  - Management Pack
  - OpsMgr
---
A new version of the Operations Manager Management Pack was released yesterday.

Download: [http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=61365290-3c38-4004-b717-e90bb0f6c148](http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=61365290-3c38-4004-b717-e90bb0f6c148 "http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=61365290-3c38-4004-b717-e90bb0f6c148")

And a nice change is that they have made the rules that monitor failure of scripts, commands and WMI queries less noisy and easier to understand. The rules has also been renamed, new names is listed in the following table:

<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td width="295" valign="top">
      <strong>Old name</strong>
    </td>
    
    <td width="295" valign="top">
      <strong>New name</strong>
    </td>
  </tr>
  
  <tr>
    <td width="295" valign="top">
      Alert on Failure to Create Process for Batch Response
    </td>
    
    <td width="295" valign="top">
      Workflow Initialization: Failed to start a process or script
    </td>
  </tr>
  
  <tr>
    <td width="295" valign="top">
      Alert on Failed Batch Responses
    </td>
    
    <td width="295" valign="top">
      Workflow Runtime: Failed to run a process or script
    </td>
  </tr>
  
  <tr>
    <td width="295" valign="top">
      WMI Probe Module Runtime Failure
    </td>
    
    <td width="295" valign="top">
      Workflow Runtime: Failed to run a WMI query
    </td>
  </tr>
  
  <tr>
    <td width="295" valign="top">
      WMI Probe Module Initialization Failure
    </td>
    
    <td width="295" valign="top">
      Workflow Initialization: Failed to start a workflow that queries WMI
    </td>
  </tr>
  
  <tr>
    <td width="295" valign="top">
      WMI Event Module Runtime Failure
    </td>
    
    <td width="295" valign="top">
      Workflow Runtime: Failed to run a WMI query for WMI events
    </td>
  </tr>
  
  <tr>
    <td width="295" valign="top">
      WMI Event Module Initialization Failure
    </td>
    
    <td width="295" valign="top">
      Workflow Initialization: Failed to start a workflow that queries WMI for WMI events
    </td>
  </tr>
  
  <tr>
    <td width="295" valign="top">
      WMI Raw Performance Counter Module Runtime Failure
    </td>
    
    <td width="295" valign="top">
      Workflow Runtime: Failed to run a WMI query for performance data
    </td>
  </tr>
  
  <tr>
    <td width="295" valign="top">
      WMI Raw Performance Counter Module Initialization Failure
    </td>
    
    <td width="295" valign="top">
      Workflow Initialization: Failed to start a workflow that queries WMI for performance data
    </td>
  </tr>
  
  <tr>
    <td width="295" valign="top">
      (new rule)
    </td>
    
    <td width="295" valign="top">
      Workflow Initialization: Failed to start a workflow that runs a process or script
    </td>
  </tr>
</table>

 

So if you have alot of script failuers and WMI errors import this MP!

The catalog accessible from the console has not been updated with the new version when this is published.