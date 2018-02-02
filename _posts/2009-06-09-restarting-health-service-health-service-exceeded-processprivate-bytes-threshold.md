---
id: 82
title: Restarting Health Service. Health Service exceeded Process\Private Bytes threshold.
date: 2009-06-09T12:37:11+00:00
author: mats
layout: post
guid: http://www.opsmode.com/?p=82
permalink: /2009/06/restarting-health-service-health-service-exceeded-processprivate-bytes-threshold/
categories:
  - Agent
  - OpsMgr
tags:
  - Agent
  - Health service
---
I have been trying to fix an issue with a SQL 2008 cluster node restarting the Health Service every 10 minutes. Logging EventID: 6024 with the description:   
_RestartHealthService.js : Restarting Health Service. Health Service exceeded Process\Private Bytes threshhold._

It didnt mater if I did an override on the monitor **Health Service Private Bytes Threshold**. I got the event anyway   
[<img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" border="0" alt="healthserviceprivatebytes" src="http://www.opsmode.com/wp-content/uploads/2009/06/healthserviceprivatebytes-thumb.jpg" width="297" height="292" />](http://www.opsmode.com/wp-content/uploads/2009/06/healthserviceprivatebytes.jpg)

Then I realized that this is a multi-homed agent, so when I did an override on the same monitor but in the other management group as well, the problem was resolved.