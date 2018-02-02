---
id: 212
title: SQL Job duration in SQL MP v6.1.314.36
date: 2010-09-14T12:26:23+00:00
author: mats
layout: post
guid: http://www.opsmode.com/2010/09/sql-job-duration-in-sql-mp-v6-1-314-36/
permalink: /2010/09/sql-job-duration-in-sql-mp-v6-1-314-36/
categories:
  - Management Pack
---
I have a customer with a lot of SQL Agent Jobs that are being monitored on Job duration and after upgrading the SQL MP to 6.1.314.36 they didn’t get alerted when the SQL Agent Jobs was running for to long.

It turned out that the threshold format has been changed, in previous versions it was HHMMSS (H=hours, M=minutes, S=Seconds). **And still is for the SQL 2000 MP!**   
So if you would set 2 hours you would write 020000.   
[<img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="image" border="0" alt="image" src="http://www.opsmode.com/wp-content/uploads/2010/09/image6_thumb.png" width="693" height="286" />](http://www.opsmode.com/wp-content/uploads/2010/09/image6.png) 

In the new version of the MP the threshold format has been changed to minutes instead.   
That makes you write 120 instead.   
[<img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="image" border="0" alt="image" src="http://www.opsmode.com/wp-content/uploads/2010/09/image17_thumb.png" width="694" height="286" />](http://www.opsmode.com/wp-content/uploads/2010/09/image17.png) 

I haven’t found anything about this in the MP Guide, but if you do please let me know.