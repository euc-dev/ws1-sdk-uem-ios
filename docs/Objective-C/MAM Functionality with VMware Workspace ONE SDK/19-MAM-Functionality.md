---
layout: page
title: MAM Functionality with VMware Workspace ONE SDK
hide:
  #- navigation
  - toc
---

The Settings and Policies in VMware Workspace ONE® UEM powered by AirWatch has settings that control security, application behaviors, and the data retrieval of specific applications. The settings are also called SDK settings because they run on the Workspace ONE SDK framework.

You can apply these SDK features to applications built with the Workspace ONE SDK, to supported Workspace ONE UEM applications, and to applications wrapped by the VMware AirWatch App Wrapping engine. Same features can be applied in both the places as the Workspace ONE SDK framework processes the functionality.

## Types of Options for SDK Settings

Workspace ONE UEM has two types of the SDK settings, default and custom. To choose the type of SDK setting, determine the scope of deployment.

* Default settings work well across organization groups, applying to large numbers of devices.
  
  Find the default settings in Groups & Settings > All Settings > Apps > Settings and Policies and then select Security Policies, Settings, or SDK App Compliance. You can apply these options across all the Workspace ONE UEM applications in an organization group. Shared options are easier to manage and configure because they are in a single location. View the matrices for information on which default settings apply to specific Workspace ONE UEM applications or the Workspace ONE SDK and app wrapping.

* Custom settings work with individual devices or for small numbers of devices with applications that require special mobile application management (MAM) features.
  
  Find the custom settings in Groups & Settings > All Settings > Apps > Settings and Policies > Profiles. Custom settings for profiles offer granular control for specific applications and the ability to override default settings. However, they also require separate input and maintenance.

* Assign the Default or Custom Profile
  
  To apply Workspace ONE UEM features built with the VMware Workspace ONE SDK, you must apply the applicable default or custom profile to an application.
* Authentication
  
  The VMware Workspace ONE SDK for iOS (Objective-C) provides helper classes to authenticate credentials against Workspace ONE UEM.
* Offline Access
  
  The VMware Workspace ONE SDK for iOS (Objective-C) provides a way to allow access to the application when the device is offline and not communicating with the mobile network.
* Detect a Change of Users in Shared Device Mode
  
  The VMware Workspace ONE SDK for iOS (Objective-C) detects a user change on a shared device during initialization (and on background-foreground if it's already initialized). Ensure your application implements the needed delegate method and performs an application data wipe appropriate for the previous user.
* Compliance or Compromised Protection
  
  You can use a method in your SDK-built app to check the compromised status of devices. This method works whether the device is offline or online.
* Dynamic Compromise Detection Requirements
  
  Dynamic compromise detection for iOS sets SDK-built apps to securely update the compromise detection algorithm over-the-air. Apps that use this feature do not need to update or re-release after compromise detection rule updates. To configure this feature, update to the supported SDK version and ensure that devices can access specific URLs.
* Activate App Tunneling
  
  The purpose of app tunneling is to redirect the traffic in your application through a specific gateway. To access internal resources in your organization, use the VMware Tunnel as the proxy.
* Content Filtering
  
  The Forcepoint content filtering component in the SDK is used for infrastructures that use a Forcepoint proxy or content filter.
* Geofencing
  
  Geofence settings are configured within an SDK profile. To do so, create an SDK profile or edit an existing one.
* Restrictions, DLP
  
  In this section of the SDK profile, you can identify what type of restriction rules you implement in your application.
* Branding
  
  Branding can change the look of the application with minimal development, and it can delegate several user interface properties to the configuration settings in the SDK profiles.
* Logging
  
  The Logging module of the VMware Workspace ONE SDK allows developers to instrument their applications to discover bugs or any issues when the application is deployed to users.
* Analytics
  
  Analytics track the important events that occur within your application. The system uses these metrics to analyze use patterns and to account for how people use your app.
* Custom Settings
  
  The VMware Workspace ONE SDK allows you to define your own custom settings for your application using an SDK Profile. You can paste raw text in this section, and the SDK makes this content available inside the application using the AWCustomPayload object.