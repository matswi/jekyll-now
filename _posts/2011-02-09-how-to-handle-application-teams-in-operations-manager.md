---
id: 281
title: How-To handle application teams in Operations Manager
date: 2011-02-09T17:53:03+00:00
author: mats
layout: post
guid: http://www.opsmode.com/2011/02/how-to-handle-application-teams-in-operations-manager/
permalink: /2011/02/how-to-handle-application-teams-in-operations-manager/
categories:
  - OpsMgr
---
<font color="#333333">This scenario is quite common here in Sweden and I get questions like this from customers and in forums. </font>

<font color="#333333">We have one team that administrates the infrastructure, Active Directory, MS Exchange, SQL server, Operations Manager etc. Then we have a application team that operates the business applications, for example Microsoft Dynamics CRM and a web application called DinnerNow.</font>

<font color="#333333">The application team wants to be able to see alerts and status as well as changing thresholds and doing overrides on "their" applications and all dependencies like storage, databases and web sites in the OpsMgr console. On top of that they also wants to get notified trough e-mail in non business hours.</font>

<font color="#333333"><font size="4"><strong>Console <br /></strong></font>So in this case we focus on the group that is administrating DinnerNow and Dynamics CRM. <br />First we need some groups, I&#8217;ve created one main group (OpsMode Application Team) with 8 subgroups containing the various components of Dynamics CRM and DinnerNow.</font>

[<font color="#333333"><img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="clip_image001" border="0" alt="clip_image001" src="http://www.opsmode.com/wp-content/uploads/2011/02/clip_image001_thumb.png" width="517" height="287" /></font>](http://www.opsmode.com/wp-content/uploads/2011/02/clip_image001.png)

  * <font color="#333333">DinnerNow Databases, contains objects from the SQL 2008 Database class</font> 
  * <font color="#333333">DinnerNow Storage and logging, contains objects from the Ubuntu server class</font> 
  * <font color="#333333">DinnerNow Web sites, contains objects from the IIS7 Web sites class</font> 
  * <font color="#333333">Dynamics CRM Application Servers, contains objects from the Microsoft Dynamics CRM 4.0 Server class</font> 
  * <font color="#333333">Dynamics CRM Data Disk, contains objects from the Logical Disk class</font> 
  * <font color="#333333">Dynamics CRM SQL components, contains objects from the SQL 2008 Database and SQL 2008 Agent Job class</font> 
  * <font color="#333333">Dynamics CRM Web sites, contains objects from the IIS 7 Web sites class</font> 
  * <font color="#333333">Dynamics CRM Windows Servers, contains objects from the Windows Computer class</font> 

<font color="#333333">Second we need to create a User Role. I base this User Role on the Advanced Operator role, because the team need to do overrides and similar.</font>

> <font color="#333333" size="1" face="Verdana"><em>The Advanced Operator profile includes a set of privileges designed for users that need access to limited tweaking of monitoring <br />configuration in addition to the Operators privileges. A role based on the Advanced Operators profile grants members the ability to override the configuration of rules and monitors for specific targets or groups of targets within the configured scope.</em></font>

<font color="#333333">I name the user role, and add the members of the team. In this case its Marsellus Wallace and Vincent Vega.</font>

[<font color="#333333"><img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="clip_image002" border="0" alt="clip_image002" src="http://www.opsmode.com/wp-content/uploads/2011/02/clip_image002_thumb.png" width="463" height="453" /></font>](http://www.opsmode.com/wp-content/uploads/2011/02/clip_image002.png)

<font color="#333333">Then I chose what groups this user role will be able to handle.</font>

[<font color="#333333"><img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="clip_image003" border="0" alt="clip_image003" src="http://www.opsmode.com/wp-content/uploads/2011/02/clip_image003_thumb.png" width="431" height="267" /></font>](http://www.opsmode.com/wp-content/uploads/2011/02/clip_image003.png)

<font color="#333333">When choosing what views will be available I also check Active Alerts, Windows Computers, Microsoft SQL Server, Microsoft Windows Internet Information Services and Microsoft Windows Server.</font>

[<font color="#333333"><img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="clip_image004" border="0" alt="clip_image004" src="http://www.opsmode.com/wp-content/uploads/2011/02/clip_image004_thumb.png" width="466" height="471" /></font>](http://www.opsmode.com/wp-content/uploads/2011/02/clip_image004.png)

<font color="#333333">I then finish the wizard. (All the settings set in the wizard can later be changed if we would like.) <br /></font><font color="#333333">Now we have a new User Role:</font>

[<font color="#333333"><img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="clip_image005" border="0" alt="clip_image005" src="http://www.opsmode.com/wp-content/uploads/2011/02/clip_image005_thumb.png" width="481" height="73" /></font>](http://www.opsmode.com/wp-content/uploads/2011/02/clip_image005.png)

<font color="#333333">And if I now log on the console with the user Vincent Vega I now only see the views we chose in the User Role Wizard.</font>

[<img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="image" border="0" alt="image" src="http://www.opsmode.com/wp-content/uploads/2011/02/image_thumb.png" width="750" height="517" />](http://www.opsmode.com/wp-content/uploads/2011/02/image.png)

<font color="#333333">We can create overrides on all management packs but only to computers that are members of a group that we chose in the wizard. <br /></font><font color="#333333">When doing an override for a group, we only get to chose from the groups chosen earlier.</font>

[<font color="#333333"><img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="clip_image007" border="0" alt="clip_image007" src="http://www.opsmode.com/wp-content/uploads/2011/02/clip_image007_thumb.png" width="390" height="310" /></font>](http://www.opsmode.com/wp-content/uploads/2011/02/clip_image007.png)

<font color="#333333" size="4"><strong>Notifications</strong></font>

<font color="#333333">So now the team can view and take care of the monitoring in the Console. They also wants to get critical alerts through e-mail on times they are not in front of a console, ie non office hours.</font>

<font color="#333333">So to set this up we can use the groups created earlier. I assume that you have a working Notification Channel and your subscribers all set up, otherwise check these:</font>

> <font color="#333333" size="1" face="Verdana"><strong>How to Create and Configure the Notification Action Account <br /></strong></font>[<font color="#333333" size="1" face="Verdana">http://technet.microsoft.com/en-us/library/dd744866.aspx</font>](http://technet.microsoft.com/en-us/library/dd744866.aspx)
> 
> <font color="#333333" size="1" face="Verdana"><strong>Enable an E-mail Notification Channel <br /></strong></font>[<font color="#333333" size="1" face="Verdana">http://technet.microsoft.com/en-us/library/dd440883.aspx</font>](http://technet.microsoft.com/en-us/library/dd440883.aspx)
> 
> <font color="#333333" size="1" face="Verdana"><strong>Create Notification Subscribers</strong> <br /></font>[<font color="#333333" size="1" face="Verdana">http://technet.microsoft.com/en-us/library/dd440875.aspx</font>](http://technet.microsoft.com/en-us/library/dd440875.aspx)

<font color="#333333">Creating a criteria for the subscription, it could look like this.</font>

[<font color="#333333"><img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="clip_image008" border="0" alt="clip_image008" src="http://www.opsmode.com/wp-content/uploads/2011/02/clip_image008_thumb.png" width="411" height="404" /></font>](http://www.opsmode.com/wp-content/uploads/2011/02/clip_image008.png)

<font color="#333333">This will send New Critical alerts from all the above groups classes to the subscriber.</font>

<font color="#333333"></font>