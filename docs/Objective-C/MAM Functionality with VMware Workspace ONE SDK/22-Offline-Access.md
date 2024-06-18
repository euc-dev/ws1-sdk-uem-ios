---
layout: page
title: Offline Access
hide:
  #- navigation
  - toc
---

The VMware Workspace ONE SDK for iOS (Objective-C) provides a way to allow access to the application when the device is offline and not communicating with the mobile network.

It also allows access to Workspace ONE UEM applications that use the SSO feature while the device is offline.

## Offline Behavior

The SDK automatically parses the SDK profile and honors the offline access policy once AWController is started. If you enable offline access and an end-user exceeds the time allowed offline, then the SDK automatically presents a blocker view to prevent access into the application. The system calls the AWSDKDelegate’s lock method so your application can act locally.