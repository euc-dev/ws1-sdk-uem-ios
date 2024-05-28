---
#title: Workspace ONE SDK for iOS
#summary: 
#authors:
    - 
    - 
date: 2024-05-27
#hide:
#  - navigation
#  - toc
---

# Getting Started  
Perform the following tasks to prepare to use the VMware Workspace ONE SDK for iOS (Objective-C).

[] [Add Frameworks in Xcode]()  
The SDK depends on the following frameworks to function properly. Follow the steps to add the necessary frameworks to your project.
[] [Adding the Required Xcode Bundle Resources]()  
The SDK depends on the following bundle resources to function properly, so add the necessary bundles to your project.
[] [Add the Workspace ONE SDK Frameworks]()  
The Workspace ONE SDK frameworks are made available by running the provided AirWatch SDK.dmg file.
[] [Using Valid Architectures]()  
[] [Register Callback Scheme]()  
To receive a callback from the Workspace ONE Intelligent Hub, the application exposes a custom scheme in the info.plist.
[] [Miscellaneous Entries for the Info.PLIST File]()
[] [Compile With Xcode 7]()  
If you use Xcode 7 to compile your SDK application, take these steps to ensure that the application functions properly.
[] [Initialize the SDK]()  
Before you can use the SDK, you must initialize it. The AWController class is the main component responsible for initializing the SDK.
[] [SDK and Application Profiles]()  
The SDK associates with two types of Workspace ONE UEM profiles. These two types are SDK Profiles and application profiles. You assign both types of profiles to the application from the Workspace ONE UEM console.
[] [Implementing the Beacon]()  
You can set up the Beacon to send device information to the Workspace ONE UEM console by specifying a time interval. Generic device information such as the device name, OS version, and compromised status is sampled. In addition, the Beacon module is used to start location services by specifying a location mode.
[] [Implementing MDM Status]()  
The MDM Status module allows an application to check certain properties and the status of some MDM properties for the device that the application lives in.