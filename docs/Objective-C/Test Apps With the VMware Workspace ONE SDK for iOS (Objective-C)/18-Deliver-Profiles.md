---
layout: page
title: Deliver Profiles to SDK Applications
hide:
  #- navigation
  - toc
---

The Workspace ONE SDK for iOS (Objective-C) allows developers to configure their applications dynamically using SDK and application profiles.

* SDK Profiles provide common settings for multiple applications. For example branding schemes, or the type of authentication you want to use on all your applications.
* Application Profiles deploy certificates for your SDK applications.

The Workspace ONE SDK for iOS (Objective-C) allows your application to integrate with the Workspace ONE UEM console to retrieve the most current settings that apply to the application. You can update settings periodically when required without a single change to the source code of the application.

Every time you save an application profile or an SDK profile, a new command to install the profiles goes to the Command Queue. The install command works on all applications and devices that are associated with the saved profiles. From the testing perspective, change what you want to test in the profile.

This change generates a new command that you can retrieve from the test code. The SDK looks for new commands when you background and foreground the application. You can also manually load commands with the AWCommandManager method.
