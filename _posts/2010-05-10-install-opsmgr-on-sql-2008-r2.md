---
id: 179
title: Install OpsMgr on SQL 2008 R2
date: 2010-05-10T16:20:37+00:00
author: mats
layout: post
guid: http://www.opsmode.com/?p=179
permalink: /2010/05/install-opsmgr-on-sql-2008-r2/
aktt_notify_twitter:
  - 'yes'
aktt_tweeted:
  - "1"
categories:
  - OpsMgr
---
When installing OpsMgr on SQL 2008 R2 the installation will not find the SQL instance and give the following error: _Microsoft SQL Server is required. Please see details_

[<img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="prereq" border="0" alt="prereq" src="http://www.opsmode.com/wp-content/uploads/2010/05/prereq_thumb.png" width="507" height="333" />](http://www.opsmode.com/wp-content/uploads/2010/05/prereq.png)&#160;

To go around this requirement, use the **DBCreateWizard.exe** that you find on the OpsMgr media **\SupportTools\<architecture>\DBCreateWizard.exe**

**Observe that this is NOT TESTED OR SUPPORTED by Microsoft!!!**

And that one will find the instance.

[<img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="sqlr2" border="0" alt="sqlr2" src="http://www.opsmode.com/wp-content/uploads/2010/05/sqlr2_thumb.png" width="448" height="190" />](http://www.opsmode.com/wp-content/uploads/2010/05/sqlr2.png) </p> 

**Observe that this is NOT TESTED OR SUPPORTED by Microsoft!!!**