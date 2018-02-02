---
id: 123
title: Installing Operations Manager agent on Solaris 9 SPARC
date: 2009-06-29T11:24:00+00:00
author: mats
layout: post
guid: http://www.opsmode.com/?p=123
permalink: /2009/06/installing-agent-on-solaris-9-sparc/
categories:
  - Agent
  - OpsMgr
  - Unix
tags:
  - Agent
  - OpsMgr 2007 R2
  - solaris
  - Unix
---
Today when installing OpsMgr R2 agents on a couple of Solaris servers we ran in to a problem on the Solaris 9 servers.

The error we got in OpsMgr:   
_<![CDATA[Executing command: echo -e mail=\ninstance=overwrite\npartial=nocheck\nidepend=quit\nrdepend=quit\nconflict=nocheck\naction=nocheck\nbasedir=default\n > /tmp/scx-$USER/scx;uncompress -f /tmp/scx-om_unix/scx-1.0.4-248.solaris.9.sparc.pkg.Z_

[<img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="solariserror" border="0" alt="solariserror" src="http://www.opsmode.com/wp-content/uploads/2009/07/solariserror_thumb.jpg" width="479" height="309" />](http://www.opsmode.com/wp-content/uploads/2009/07/solariserror.jpg) 

We found this on the Solaris box:   
_[ verifying class <config> ]   
\## Executing postinstall script.   
ld.so.1: .scxsslconfig: fatal: libssl.so.0.9.7: open failed: No such file or directory   
Killed   
pkgadd: ERROR: postinstall script did not complete successfully   
Installation of <MSFTscx> failed.   
bash-2.05# ssh –version   
Sun\_SSH\_1.1, SSH protocols 1.5/2.0, OpenSSL 0x0090700f   
Bad escape character &#8216;rsion&#8217;._

And if you look in [Appendix A](http://technet.microsoft.com/en-us/library/dd789030.aspx) in the Operations Manager 2007 R2 Operations Guide you se that OpenSSL is required. So after installing OpenSSL the agent install went fine!   
_Sun does not provide a version of OpenSSL for Solaris 9 SPARC. There is a version available from [Sunfreeware](http://www.sunfreeware.com/)._