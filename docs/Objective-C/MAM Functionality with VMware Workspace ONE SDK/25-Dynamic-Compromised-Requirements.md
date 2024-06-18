---
layout: page
title: Dynamic Compromise Detection Requirements
hide:
  #- navigation
  - toc
---

Dynamic compromise detection for iOS sets SDK-built apps to securely update the compromise detection algorithm over-the-air. Apps that use this feature do not need to update or re-release after compromise detection rule updates. To configure this feature, update to the supported SDK version and ensure that devices can access specific URLs.

To use dynamic compromise detection, update the SDK version and ensure that devices can access specific URLs.
* The SDK-built app must consume Workspace ONE SDK for iOS (Objective-C) v5.9.9.
* To receive the latest compromise detection rules, ensure that devices can connect to the listed URLs.
  * api.na1.region.data.vmwservices.com
  * discovery.awmdm.com
  * signing.awmdm.com
* If devices cannot access these URLs, they still get compromise detection but rules only update when the SDK-built app consumes the latest SDK. This lapse in rule updates might result in false positives.