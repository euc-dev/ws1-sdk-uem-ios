---
layout: page
title: AppConfig.org
hide:
  #- navigation
  - toc
---

## Overview

This tutorial will walk developers through how to create a tunnel for a mobile app’s network traffic to access intranet resources by utilizing the iOS per-app-VPN capability as prescribed by the AppConfig.org standard. The steps in this tutorial are done with the assumption that you have gone through the steps in [Getting Started](../index.md) tutorial.

## Requirements

- iOS 7.0.1+
- AirWatch Console version 7.3 and above
- AirWatch Tunnel or a Per App VPN Solution supported by AirWatch
- iOS Tunnel client application

## Developer Considerations

The app must implement either a Cocoa framework or a networking library derived from the Cocoa framework such as `AFNetworking`.

Additionally, the app must be deployed under “management” to the device by AirWatch. During distribution, AirWatch entitles the application to be an approved user of the Per-App VPN utilized.

## Tutorial

Per-app VPN configuration is setup via the following steps:

1. Infrastructure configuration – Per-app VPN infrastructure is installed and configured.
2. Profile configuration – Per-app VPN profile is configured via the AirWatch Console
3. App deployment/configuration – The application is added to the AirWatch Console and the Per-app VPN profile is assigned to the application

### Infrastructure Configuration

This tutorial assumes that the Per-app VPN infrastructure is in place already. For information on AirWatch tunnel please refer to Installation and Admin guides on the myAirWatch Resource portal.

A VPN Client application is required on the iOS Device. AirWatch Tunnel servers have an iOS companion app that needs to be deployed.

### Profile Configuration

1. Log into the AirWatch console and navigate to Devices > Profiles > List View
2. Click Add then add profile
3. Select iOS
4. Select VPN and click Configure
5. Select the VPN Connection type. AirWatch tunnel is selected for the Tutorial.
6. Click Save & Publish

### App Deployment & Configuration

1. Log into the AirWatch console and navigate to Apps & Books
2. For this tutorial, Dolphin Browser will receive the Per-app VPN profile
3. Select the Public Tab and click Add Application
4. Select the Platform and enter the name of the application
5. Select Dolphin
6. Select the assignment tab and assign the app to the desired Smart Group(s)
7. Select the Deployment Tab
8. Check the “Use VPN” box and select the VPN Profile from the drop down
9. Click Save and Publish
10. Verify device assignment
11. Click Publish to confirm settings
