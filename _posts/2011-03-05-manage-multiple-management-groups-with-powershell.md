---
id: 313
title: Manage multiple Management Groups with PowerShell
date: 2011-03-05T22:09:14+00:00
author: mats
layout: post
guid: http://www.opsmode.com/2011/03/manage-multiple-management-groups-with-powershell/
permalink: /2011/03/manage-multiple-management-groups-with-powershell/
categories:
  - OpsMgr
  - Powershell
---
Sometimes we have more than one Management Group (MG), production, test and maybe a development environment. When opening the Operations Manager Console it connects with the last MG you were connected to. This is controlled by the registry value **SDKServiceMachine** in **HKEY\_CURRENT\_USER\Software\Microsoft\Microsoft Operations Manager\3.0\User Settings**

If we want to control this, there is a switch when opening console:   
**Microsoft.MOM.UI.Console.exe /Server:OPSRMS01.opsmgr.se**

[<img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="image" border="0" alt="image" src="http://www.opsmode.com/wp-content/uploads/2011/03/image_thumb.png" width="529" height="263" />](http://www.opsmode.com/wp-content/uploads/2011/03/image.png)

So for the console we can create different shortcuts for the MG&#8217;s with the switch..

When it comes to the Operations Manager Shell there isn&#8217;t any switch to do it the &#8220;easy way&#8221;. I do like this:

First I makes as many copy&#8217;s of the file **Microsoft.EnterpriseManagement.OperationsManager.ClientShell.Startup.ps1** as I have Management Groups. Renaming them to the different MG names, for example:   
**Microsoft.EnterpriseManagement.OperationsManager.ClientShell.StartupOPSMGRdev.ps1** for my development environment.

Second I open the ..StartupOPSMGRdev.ps1-file in my preferred editor and change **line 10**

[<img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="image" border="0" alt="image" src="http://www.opsmode.com/wp-content/uploads/2011/03/image_thumb1.png" width="664" height="65" />](http://www.opsmode.com/wp-content/uploads/2011/03/image1.png)

Just adding your RMS fqdn (remove **: &#8220;&#8221;**)

Third I make a copy of the Operations Manager Shell shortcut for every MG and change the .Startup.ps1 to the name you gave the Startup file, in my case it will be:   
**Microsoft.EnterpriseManagement.OperationsManager.ClientShell.StartupOPSMGRdev.ps1**

[<img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="image" border="0" alt="image" src="http://www.opsmode.com/wp-content/uploads/2011/03/image_thumb2.png" width="372" height="519" />](http://www.opsmode.com/wp-content/uploads/2011/03/image2.png)

So now I have a shortcut for every Management Group in my environment.

[<img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="image" border="0" alt="image" src="http://www.opsmode.com/wp-content/uploads/2011/03/image_thumb3.png" width="390" height="77" />](http://www.opsmode.com/wp-content/uploads/2011/03/image3.png)

<table border="0" cellspacing="0" cellpadding="2" width="704">
  <tr>
    <td valign="top" width="702">
      <p>
        <font style="style"><font style="background-color: #ffc000"><strong>Update! <br /></strong>Cory Delamarter have written a post on the same subject but with an other angle. <br />Check it out here: <br /></font></font><a title="http://blogs.technet.com/b/corydelamarter/archive/2011/03/25/using-the-operations-manager-command-shell-against-multiple-management-groups.aspx" href="http://blogs.technet.com/b/corydelamarter/archive/2011/03/25/using-the-operations-manager-command-shell-against-multiple-management-groups.aspx"><font style="background-color: #ffc000">http://blogs.technet.com/b/corydelamarter/archive/2011/03/25/using-the-operations-manager-command-shell-against-multiple-management-groups.aspx</font></a>
      </p>
    </td>
  </tr>
</table>