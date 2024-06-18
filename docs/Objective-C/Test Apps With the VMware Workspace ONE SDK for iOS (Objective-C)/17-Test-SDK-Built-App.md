---
layout: page
title: Test the SDK-Built App
hide:
  #- navigation
  - toc
---

Test the SDK-Built App
Test the integration of your application with the Workspace ONE SDK for iOS (Swift), including the delivery of profiles from the Workspace ONE UEM console to your application.

Initialize the SDK in your application to set communication with the Workspace ONE UEM server and to test the application.

## Procedure
1. Enroll your test devices to the Workspace ONE UEM console to enable communication between them.
  The SDK does not currently support testing in a simulator.
2. Upload the SDK-built app or a placeholder application that has the same bundle ID as the testing application.
    1. Create an empty application with the bundle ID of the testing-application to identify the application.
    2. Upload the empty application to the console and assign a default or custom SDK profile to it.
3. Assign an SDK profile to the application.
If you do not assign a profile, the SDK does not initialize correctly.This step enables the console to send commands to the application with the record.
4. Push the application to test devices. Save the application and assign it using the flexible deployment feature.
Use devices for testing that are Workspace ONE UEM managed devices.
You do not have to repush the application every time you make a change.

Flexible deployment rules push the application to test devices with the app catalog.
5. Run your application in Xcode.

## Results

The console pushes the initialization data to the application when the application installs on test devices.

## What to do next

After the application initializes, you can run the application as many times as you want to debug it.