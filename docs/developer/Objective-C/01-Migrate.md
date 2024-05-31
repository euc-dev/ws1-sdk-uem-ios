---
layout: page
title: Migrate to the Latest SDK Version
#permalink: /sdks/ws1/ws1-sdk-uem-ios/developer/Objective-C/
hide:
  #- navigation
  - toc
---

In the latest SDK for iOS, we have updated various UI screens presented by the SDK. These pages now incorporate storyboards that require you to import the new AWKit.bundle included in the new SDK DMG. This AWKit.bundle contains the compiled storyboards required for the app to function.

We have also integrated with the latest Safari View Controller for various process flows on UI screens. Add SafariServices.Framework so all Workspace ONE UEM screens work without error.

## Procedure
1. Replace or import the AWKit.bundle.
   1. Replace the older version of AWKit.bundle with the newer version provided in the DMG file if you already import AWKit.bundle into your project bundle resources today.
   2. Import AWKit.bundle into your project under Bundle Resources in Xcode Build Phases if you have never imported the AWKit.bundle into your project.
2. Import the SafariServices.Framework into your project.