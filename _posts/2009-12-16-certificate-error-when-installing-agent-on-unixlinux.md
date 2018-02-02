---
id: 197
title: Certificate error when installing agent on Unix/Linux
date: 2009-12-16T12:07:00+00:00
author: mats
layout: post
guid: http://www.opsmode.com/?p=197
permalink: /2009/12/certificate-error-when-installing-agent-on-unixlinux/
categories:
  - OpsMgr
  - Unix
---
Some times when installing X-plat agents you get an error: 

> _The server certificate on the destination computer (server:1270) has the following errors:&#160;&#160;&#160;&#160;   
> The SSL certificate contains a common name (CN) that does not match the hostname._

The problem here is that Operations Manager uses the FQDN in the DNS, but the certificate will contain the server name taken from the server.   
To solve this issue you can change the DNS record, change the server name or you can add the server name to the HOSTS file on the Root Management Server or the Management Server. 

> **Example:**        _  
> 192.168.80.37 name.in.certificate_