---
id: 364
title: Creating a xplat script monitor from the console, System Center 2012 Operations Manager
date: 2011-11-23T14:40:08+00:00
author: mats
layout: post
guid: http://www.opsmode.com/2011/11/creating-a-xplat-script-monitor-from-the-console-system-center-2012-operations-manager/
permalink: /2011/11/creating-a-xplat-script-monitor-from-the-console-system-center-2012-operations-manager/
categories:
  - Authoring
  - Console
  - Cross Platform
  - OpsMgr
tags:
  - Cross Platform
  - OpsMgr
  - OpsMgr 2012
---
Announced in the <a href="http://social.technet.microsoft.com/Forums/en-US/operationsmanagerunixandlinux/thread/9a30b000-2bbe-4b8c-b64c-1b17f10f2a2b" target="_blank">Technet forum</a> last week was the new ability to create a UNIX/Linux Shell Command Monitor. Download the file from <a href="http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=27974" target="_blank">here</a>, run it and after importing the file called **Microsoft.Unix.ShellCommand.Library.mpb** you will be able to create a two and/or three state UNIX/Linux script monitor from within the Operations Manager console.

[<img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="image" border="0" alt="image" src="http://www.opsmode.com/wp-content/uploads/2011/11/image_thumb.png" width="370" height="292" />](http://www.opsmode.com/wp-content/uploads/2011/11/image.png)

To create a monitor simply start the Create a Unit monitor wizard.

Make your choices:

[<img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="image" border="0" alt="image" src="http://www.opsmode.com/wp-content/uploads/2011/11/image_thumb1.png" width="536" height="665" />](http://www.opsmode.com/wp-content/uploads/2011/11/image1.png)

Give the monitor a **Name** select **Monitor target** and choose if it will be enabled.

Select how often your script will run on the agent.

In the **Shell Command details** you need to provide your command or path to binary/script without line breaks. So my little script that checks if a file exists.

> #!/bin/bash   
> if ! [ -f /tmp/OPSMGR.SE ];   
> then   
> echo "Error"   
> else   
> echo "OK"   
> fi

Needs to be put in a file on the agent or as a one-liner. Otherwise it wont be possible to continue the wizard and a red exclamation will show, like in this picture

[<img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="image" border="0" alt="image" src="http://www.opsmode.com/wp-content/uploads/2011/11/image_thumb2.png" width="320" height="222" />](http://www.opsmode.com/wp-content/uploads/2011/11/image2.png)

Putting the script in one line makes it look like this, I removed #!/bin/bash so the line wont be marked as a comment..

> if ! [ -f /tmp/OPSMGR.SE ]; then echo "Error"; else echo "OK"; fi

[<img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="image" border="0" alt="image" src="http://www.opsmode.com/wp-content/uploads/2011/11/image_thumb3.png" width="380" height="360" />](http://www.opsmode.com/wp-content/uploads/2011/11/image3.png)

Specifying the **Error Expression** 

[<img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="image" border="0" alt="image" src="http://www.opsmode.com/wp-content/uploads/2011/11/image_thumb4.png" width="528" height="100" />](http://www.opsmode.com/wp-content/uploads/2011/11/image4.png)

Specifying the **Healthy Expression**

[<img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="image" border="0" alt="image" src="http://www.opsmode.com/wp-content/uploads/2011/11/image_thumb5.png" width="534" height="94" />](http://www.opsmode.com/wp-content/uploads/2011/11/image5.png)

Finish the wizard and your monitor is now running.

[<img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="image" border="0" alt="image" src="http://www.opsmode.com/wp-content/uploads/2011/11/image_thumb6.png" width="811" height="453" />](http://www.opsmode.com/wp-content/uploads/2011/11/image6.png)