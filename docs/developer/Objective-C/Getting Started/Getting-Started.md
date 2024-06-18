---
layout: page
title: Getting Started
hide:
  #- navigation
  - toc
---

Perform the following tasks to prepare to use the VMware Workspace ONE SDK for iOS (Objective-C).

- [ ] [Add Frameworks in Xcode](05-Add-Frameworks-in-Xcode.md)  
The SDK depends on the following frameworks to function properly. Follow the steps to add the necessary frameworks to your project.
- [ ] [Adding the Required Xcode Bundle Resources](06-Adding-Xcode-Bundle-Resources.md)  
The SDK depends on the following bundle resources to function properly, so add the necessary bundles to your project.
- [ ] [Add the Workspace ONE SDK Frameworks](07-Add-WS1-SDK-Frameworks.md)  
The Workspace ONE SDK frameworks are made available by running the provided AirWatch SDK.dmg file.
- [ ] [Using Valid Architectures](08-Using-Valid-Architectures.md)  
- [ ] [Register Callback Scheme](09-Register-Callback-Scheme.md)  
To receive a callback from the Workspace ONE Intelligent Hub, the application exposes a custom scheme in the info.plist.
- [ ] [Miscellaneous Entries for the Info.PLIST File](10-Misc-Entries-for-Info.PLIST-file.md)
- [ ] [Compile With Xcode 7](11-Compile-With-XCode-7.md)  
If you use Xcode 7 to compile your SDK application, take these steps to ensure that the application functions properly.
- [ ] [Initialize the SDK](12-Initialize-the-SDK.md)  
Before you can use the SDK, you must initialize it. The AWController class is the main component responsible for initializing the SDK.
- [ ] [SDK and Application Profiles](13-SDK-and-Application-Profiles.md)  
The SDK associates with two types of Workspace ONE UEM profiles. These two types are SDK Profiles and application profiles. You assign both types of profiles to the application from the Workspace ONE UEM console.
- [ ] [Implementing the Beacon](14-Implementing-the-Beacon.md)  
You can set up the Beacon to send device information to the Workspace ONE UEM console by specifying a time interval. Generic device information such as the device name, OS version, and compromised status is sampled. In addition, the Beacon module is used to start location services by specifying a location mode.
- [ ] [Implementing MDM Status](15-Implementing-MDM-Status.md)  
The MDM Status module allows an application to check certain properties and the status of some MDM properties for the device that the application lives in.
