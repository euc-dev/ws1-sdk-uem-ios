---
layout: page
title: Register Callback Scheme
permalink: /sdks/ws1/ws1-sdk-uem-ios/developer/Objective-C/
hide:
  #- navigation
  - toc
---
 
To receive a callback from the Workspace ONE Intelligent Hub, the application exposes a custom scheme in the info.plist.

## Procedure
1. Navigate to Supporting Files in Xcode.
2. Select the file `<YourAppName> > -Info.plist`.
3. Navigate to the URL Types section.
   a. If it does not exist, add it at the Information Property List root node of the PLIST.
4. Expand the Item 0 entry and add an entry for URL Schemes.
5. Set the next Item 0 under URL Schemes to the desired callback scheme.
