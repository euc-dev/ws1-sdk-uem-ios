---
layout: page
title: Disable the Default Blocker Screen
hide:
  #- navigation
  - toc
---

The Workspace ONE SDK displays a blocker screen to cover the application’s content when the application is not active. When the app is in the foreground, the Workspace ONE SDK dismisses the blocker screen.

You can disable this sceen and use your own custom backgroud blocker screen or use the Workspace ONE SDK screen.

## Procedure

1. Work in the AWSDKDefaults bundle.
2. Create a dictionary named AWBlockerViewEnableKey and put it in the AWSDKDefaultSettings.plist.
3. Configure the AWBlockerViewEnableKey dictionary, create a new Boolean entry with the key name as enabled and set the Boolean value to No.
   1. If you set AWBlockerViewEnableKey to Nothen the Workspace ONE SDK disables the blocker screen so that you can use your own blocker screen.
   2. If you set AWBlockerViewEnableKey to Yes then the Workspace ONE SDK uses its blocker screen.
      
      If AWBlockerViewEnableKey is empty, the Workspace ONE SDK displays its blocker screen.
