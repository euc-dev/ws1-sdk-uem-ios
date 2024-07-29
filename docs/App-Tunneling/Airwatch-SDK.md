---
layout: page
title: Airwatch SDK
hide:
  #- navigation
  - toc
---

## Overview

The steps in this tutorial are done with the assumption that you have gone through the steps in [Getting Started](../getting-started.md) tutorial as well as the SDK Setup section.

!!!Important
    You will need to download the SDK binary separately via [resources.resources.com](resources.resources.com). Please contact your AirWatch representative or support to gain access.

## Requirements

- iOS 7+
- Xcode
- iOS Test Device
- AirWatch SDK from AirWatch Resource Portal

## Tutorial

***You do not need any additional code to tunnel traffic in your application after you successfully initialize the SDK and configure your SDK profile, the tunneling will be done automatically.***

### Policy configuration

At this point in the tutorial, we assume you have already gone through the steps of uploading your app and assigning the SDK profile mentioned in [General Setup](../index.md) tutorial.

Log into the AirWatch Console and identify if the SDK profile you assigned to your application is the default profile or a custom profile. If there is no profile assigned, you can choose from one of two ways to configure the policy: group-wide default settings or an ad-hoc custom profile.

### Using the Default Profile (Recommended)

1. If the profile assigned is the default profile, then the policy settings can be edited by navigating to Apps & Books > All Apps & Books Settings > Apps > Settings And Policies > Security Policies.
2. Enable the AirWatch App Tunnel option.
3. Set your App Tunnel Mode to the proxy you plan on using. (If there is no proxy configured, follow the configure proxy settings link on the UI to walk through setting up your proxy)
4. Click the Save button to persist any changes you have made.

!!!Note
    These changes will reflect via the Default Profile during profile assignment which will be done in a later step in the tutorial.

### Using an Ad-hoc Custom Profile

1. Navigate to Apps & Books > All Apps & Books Settings > Apps > Settings And Policies > Profiles.
2. Select your assigned profile, or click on Add Profile and select the App Wrapping Profile.
3. In the General section, assign a name to your profile.
4. Select the Proxy payload and Enable App Tunnel and set your App Tunnel Mode to the proxy you plan on using.
5. Click Save to create or update your app wrapping profile.
Once you receive the `initialCheckDoneWithError` callback from the AWSDKDelegate, check to see if the error object is nil or not.

### Testing

After you have configured your SDK profile to enable tunneling, run your app and the network traffic in your app will now be tunneled.
