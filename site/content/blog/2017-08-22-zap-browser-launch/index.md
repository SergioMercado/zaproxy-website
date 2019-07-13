---
title: "ZAP Browser Launch"
type: post
tags:
- TODO
date: "2017-08-22"
authors:
    - simon
---
We have just released a new feature for ZAP that allows you to launch browsers from within ZAP. The browsers are automatically configured to
proxy via ZAP and ignore certificate warnings, making it much easier for people to get started with ZAP as well as for more experienced users
who want to use ZAP with a variety of browsers. You can install and use Browser Launch right now via the ZAP Marketplace, which can be accessed
via the 'Manage Add-ons' button in ZAP:  
  
![](https://github.com/zaproxy/zap-extensions/wiki/images/zap-screenshot-browse-addons.png)  
  
just 'Check for Updates':  
{{< img "images/Check-for-updates.png" "Alt title" >}}  
and 'Update All':  
{{< img "images/update-all.png" "Alt title" >}}  
You will now get a new 'Launch Browser' option in the Quick Start tab:  
  
{{< img "images/launch-browser.png" "Alt title" >}}  
To see a demo of this feature see the following video:  
{{ youtube "https://www.youtube.com/embed/lYHwR7UEggA?feature=player_embedded" }}  
  
Note that you must be using the latest version of ZAP (currently 2.8.0) and at least Java 8.  
Version 2.8.0 does support Java 7, but this functionality requires Java 8. It’s worth noting that the next full release of ZAP will also require
Java 8 as a minimum.  
  
If you have any problems or questions about this new feature then please head over the the [ZAP User Group](https://groups.google.com/group
/zaproxy-users).
