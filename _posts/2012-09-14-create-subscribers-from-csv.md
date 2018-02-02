---
id: 376
title: Create subscribers from .CSV
date: 2012-09-14T13:21:06+00:00
author: mats
layout: post
guid: http://www.opsmode.com/?p=376
permalink: /2012/09/create-subscribers-from-csv/
categories:
  - OpsMgr
  - Powershell
tags:
  - OpsMgr
  - Powershell
---
Here is a small powershell script for creating multiple subscribers from a CSV-file. 

Your file should look like this:

> "Name","Email","SMS","IM"   
> "Marsellus Wallace","marsellus.wallace@opsmode.com","12345678","marsellusw"

And the code looks like this:

> $NotificationSubscribers = Import-Csv "D:\temp\SCOMNotificationSubscribers.csv" 
> 
> foreach($NotificationSubscriber in $NotificationSubscribers)   
> {   
> $Name = $NotificationSubscriber.Name   
> $eMail = $NotificationSubscriber.Email   
> $SMS = $NotificationSubscriber.SMS   
> $IM = $NotificationSubscriber.IM
> 
> Add-SCOMNotificationSubscriber -Name $Name -DeviceList $eMail,"sms:$SMS","sip:$IM"   
> }