---
id: 186
title: 32bit management pack on 64bit Windows Server
date: 2010-05-25T13:51:19+00:00
author: mats
layout: post
guid: http://www.opsmode.com/?p=186
permalink: /2010/05/32bit-management-pack-on-64bit-windows-server/
categories:
  - Authoring
  - Management Pack
  - OpsMgr
---
When using a management pack designed to discover a 32bit application and that application is installed on a 64bit server OS the application will probably not get discovered.

This is because the 32bits app will write its registry keys in the HKLM\SOFTWARE\Wow6432Node\ (because its a 32bit app on a 64bit system) and the discovery will look for keys and values in HKLM\SOFTWARE\

To resolve this you can either create the registry keys under HKLM\SOFTWARE or install a 32bit agent on the system.
  
If you install the 32bit agent it will bee replaced every time you do a upgrade from the console, and worse you wont bee able to monitor your 64bit system properly.

When author MP’s for OpsMgr 2007 R2 there is a new feature that can be used in the discovery.
  
**<RegistryView>32bit</RegistryView>**

Should go somthing like this:

> <RegistryAttributeDefinition>
  
>   <AttributeName>TheApplication</AttributeName>
  
>   <Path>SOFTWARE\TheApplication</Path>
  
>   <PathType>0</PathType>
  
>   <AttributeType>0</AttributeType>
  
>   <span style="color: #ff0000;"><strong><RegistryView>32bit</RegistryView></strong><br /> </span></RegistryAttributeDefinition>

And this will make it look in the Wow6432Node