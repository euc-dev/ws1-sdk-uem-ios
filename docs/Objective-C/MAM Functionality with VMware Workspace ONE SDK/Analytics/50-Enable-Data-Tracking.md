---
layout: page
title: Enable Data Tracking in Your SDK Application
hide:
  #- navigation
  - toc
---

Enable the data tracking module by embedding a PLIST into your application project.

## Procedure

1. Create a PLIST named AWSDKDefaultSettings.plist, add it to your application project, and copy it to your bundle resources.
2. Define the AWDataUsageEnabled boolean flag in the PLIST.
3. Define the AWDataUsageConfiguration dictionary with SyncInterval and Network in the PLIST.
