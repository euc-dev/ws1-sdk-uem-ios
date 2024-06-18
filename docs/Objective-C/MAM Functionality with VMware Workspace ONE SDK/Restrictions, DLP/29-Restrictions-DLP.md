---
layout: page
title: Restrictions, DLP
hide:
  #- navigation
  - toc
---

In this section of the SDK profile, you can identify what type of restriction rules you implement in your application.

* Initialize the AWRestrictions Class
  
  To monitor the MDM enrollment and allow offline mode restrictions, the application must initialize the AWRestrictions class.
* Check Device Enrollment
  
  Use the SDK to retrieve the enrollment status of the device. The snippet of code shows how to perform that check.
* Use DLP to Control the Copy and Paste of Data Out and Into Your SDK-Built Application
  
  Control the copy and paste interaction between your SDK-built applications and non-SDK-built applications. Use the two settings Enable Copy and Paste Out and Enable Copy and Paste Into.
* Use DLP to Control Links to Open in Workspace ONE Web and Workspace ONE Boxer
  
  Configure applications built with the Workspace ONE SDK to open in the Workspace ONE Web and to compose emails in Workspace ONE Boxer. This feature enables end users to use alternative systems other than Safari and the Mail app. To develop this feature, create a bundle in your iOS application and configure Workspace ONE UEM to enforce the behaviors in the bundle.
* Disable the Default Blocker Screen
  
  The Workspace ONE SDK displays a blocker screen to cover the application’s content when the application is not active. When the app is in the foreground, the Workspace ONE SDK dismisses the blocker screen.
* Restrict Document-Sharing with Data Loss Prevention
  
  You can manage document-sharing in your Workspace ONE SDK for iOS (Objective-C)-built app using the SDK and configuring the SDK default settings in the Workspace ONE UEM console.
