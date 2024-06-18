---
layout: page
title: Detect a Change of Users in Shared Device Mode
hide:
  #- navigation
  - toc
---

The VMware Workspace ONE SDK for iOS (Objective-C) detects a user change on a shared device during initialization (and on background-foreground if it's already initialized). Ensure your application implements the needed delegate method and performs an application data wipe appropriate for the previous user.

## Behavior When User Changes

When a user change happens, the system calls the userChanged delegate method in AWController. The SDK prompts the user about the user change. After the user acknowledges the prompt, the SDK initializes as a new user.

## Detect a User Change and Offline Access

The SDK needs to confirm a user change when the device is offline and comes back online. The SDK behavior depends on if offline access is enabled or disabled.
* Offline Access Enabled
  
  The SDK must prompt the user to flip to the anchor application and retrieve data on the last users for confirmation.

  If the user did not change, then the anchor application flips back to the SDK application and continues with the existing user. If the user changed, the SDK wipes previous user data and sends the userChanged delegate method call back to your application.

* Offline Access Disabled

  When the user tries to access the application and the user is offline, then the SDK blocks access. The SDK tells the user they must be online to access the application.

## Code User Change Detection When Application is Offline

In your application project, white list a new scheme called awcontextid.

1. Open the info.plist file for your application.

2. Add a new scheme awcontextid under the LSApplicationQueriesSchemes key.

