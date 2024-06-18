---
layout: page
title: Compile With Xcode 7
#permalink: /sdks/ws1/ws1-sdk-uem-ios/developer/Objective-C/
hide:
  #- navigation
  - toc
---
 
If you use Xcode 7 to compile your SDK application, take these steps to ensure that the application functions properly.

## Procedure  
1. Add an array key named LSApplicationQueriesSchemes to thinfo.plist.
2. Add the bundle identifier of the Workspace ONE Intelligent Hub or AWSSOBroker2 application to the array.  
The schemes for the Workspace ONE Intelligent Hub and AWSSOBroker2 are as follows:
   * airwatch
   * AWSSOBroker2
3. Navigate to your Xcode build settings and set Enable Bitcode to No.