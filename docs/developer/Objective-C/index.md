---
layout: page
title: Workspace ONE SDK for iOS (Objective-C)
permalink: /sdks/ws1/ws1-sdk-uem-ios/developer/Objective-C/
hide:
  #- navigation
  - toc
---

The VMware Workspace ONE® SDK is a set of tools allowing organizations to incorporate a host of features and functionality into their custom-built iOS applications. The Workspace ONE SDK enhances the security and functionality of those applications and in turn helps save application development time and money.

This content is no longer maintained. Checkout updated Workspace ONE SDK developer documentation on code.vmware.com.

Integrating an application with the Workspace ONE SDK can be broken down into five main steps. A high-level overview of each step is listed below.

## Enable the Core SDK Framework within Xcode

These steps detail the core iOS frameworks and the Workspace ONE SDK frameworks that you add to your project in order for the SDK to function properly. The Workspace ONE SDK frameworks are made available by running the provided AirWatchSDK.dmg file.

In order for your custom application to use the SDK, you must first complete the following setup procedures in Xcode:

* Add Required Frameworks
* Configure the Server Connections

The following modules enable the device management framework and allow you to configure device management features into your application:
* Implement the Beacon
* Implement the DataSampler

## Select and Implement Additional SDK Modules

Workspace ONE UEM provides a number of pre-configured functions for your app that can be controlled from the Workspace ONE UEM console. These modules make up the Application Management Framework. You must decide which SDK modules to use within your application.

* Developing Modules
Developers have the option, for most modules, to code the expected behavior or to set the behavior in the Workspace ONE UEM console. If you want the application to behave a certain way every time, you must code this behavior in to the application.
* Coding the Logging Level
The exception is Logging. You must code the logging level and you must set this option in the Workspace ONE UEM console. This configuration ensures that your network is not burdened with unwanted logging activity.
* Using Default Settings for SDK Profiles
Use the SecurityPolicies and Settings pages to configure settings once and then share them across Workspace ONE UEM applications using the iOS Default Settings @ [Organization Group] profile.

You can also use the Profiles page to configure custom settings with specific behaviors.

Implementing each module into your app is a two-step process:
1. Implement the functionality for the desired module within your app (in Xcode).
2. Add the corresponding configuration to the SDK Profile (in the Workspace ONE UEM console) that gets assigned to the app.

## Using Certificates

The Workspace ONE SDK allows you to provision and embed certificates into your app upon deployment. The process involves three main steps:
* Configuring the certificate authority (CA) and the CA Template.
* Creating the App Profile in the Workspace ONE UEM console.
* Assigning the App Profile to the application in Workspace ONE UEM prior to app deployment. See Certificate Provisioning.

## Set Default Settings within Workspace ONE UEM

In the Workspace ONE UEM console, you must configure default SDK settings to assign it to your app. These settings include configurations specific to each module you plan on utilizing.

## Upload the Application to Workspace ONE UEM

Once your app is completely built, you need to upload the file into Workspace ONE UEM using the Workspace ONE UEM console. During this process, you need to assign the SDK profile you created, making the settings defined in the SDK profile available to your application. The Mobile Application Management (MAM) Guide describes how to upload an application.

## Deploy the Application
The final step is to deploy your application to managed devices through the Workspace ONE UEM console. Users now have access to the application, along with all the SDK enabled features you've implemented.

For more information on deploying applications to managed devices, see the Mobile Application Management (MAM) Guide.
* [Migrate to the Latest SDK Version](01-Migrate.md)  
  In the latest SDK for iOS, we have updated various UI screens presented by the SDK. These pages now incorporate storyboards that require you to import the new AWKit.bundle included in the new SDK DMG. This AWKit.bundle contains the compiled storyboards required for the app to function.
* [Supported Operating Systems and Requirements for the Workspace ONE SDK for iOS (Objective-C)](02-Supported-OS-and-Requirements.md)  
  The Workspace ONE SDK for iOS (Objective-C) is compatible with the listed operating systems and requires the listed components.
* [Security Considerations for OpenURL in iOS](03-Security-Considerations.md)  
  With changes to OpenURL in iOS 13, update to the latest version of the Workspace ONE SDK for iOS (Objective-C) to mitigate possible security issues.