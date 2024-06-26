---
layout: page
title: Add the Workspace ONE SDK Frameworks
hide:
  #- navigation
  - toc
---

The Workspace ONE SDK frameworks are made available by running the provided AirWatch SDK.dmg file.

## Procedure  
1. Drag AWSDK.framework into the Frameworks group in the sidebar of Xcode. Make sure to check Copy items into destination group's folder.
2. Ensure the application is linking against the AWSDK.framework.
   * Select the Build Phases tab in the properties of the target.
   * Expand the Link Binary With Libraries section to see if AWSDK.framework is added.
   * If not, select the + button and select AWSDK.framework.
3. Import the umbrella header wherever you use the SDK. Add #import <AWSDK/AWSDKCore.h to the top of the file.
4. Add Linker Flags.
   Since the Workspace ONE SDK for iOS (Objective-C) categories, you must pass linker flags to the linker to properly load them.
   a. Select the project or workspace in the Groups & Files pane.
   b. Select the target for the application.
   c. Select the Build Settings tab.
   d. Ensure the  -ObjC flag is added in the Other Linker Flags entry.
