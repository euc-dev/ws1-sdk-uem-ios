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
    You will need to include the SDK as a Swift package and it is available in [Workspace ONE software development kit (SDK) for iOS repository](https://github.com/euc-releases/iOS-WorkspaceONE-SDK/releases).

## Requirements

- iOS 16+
- Xcode
- iOS Device
- AirWatch SDK via swift package manager

## Tutorial

### Step 1: Integrate the AirWatch SDK

Follow the instructions in the [Getting Started](../getting-started.md) tutorial to integrate the AirWatch Software Development Kit (SDK) for iOS into your application.

### Step 2: Add Custom Settings in your SDK profile

For this next part, you will need to check which profile you have assigned to your SDK app. You can do this by navigating to Apps & Books > Details View. Click Edit. Choose More > SDK. Check what profile is assigned for SDK Profile.
   ![Assign SDK Profile](4eb714f1-eea9-450e-910f-72918fa69db4.png)

### Using the Default SDK Profile (Recommended)

1. If the profile assigned is the default profile, then the policy settings can be edited by navigating to Apps & Books > All Apps & Books Settings > Apps > Settings And Policies > Settings.
2. Enable the custom settings and add your custom settings. This is a string field and can contain XML, JSON, or plain text. You can also insert lookup values if desired.
   ![SDK Profile Custom Settings](0f6e3878-664c-4e51-a289-0d1e5153ceb8.png)
3. Once you are done, click save to start enforcing the new policy.

### Using a custom profile

1. In the AirWatch Console, Choose Apps & Books > All Apps & Books Settings.
2. Choose Settings and Policies > Profiles and click Add Profile to create a custom profile or edit an already existing profile currently assigned to your app.
   ![Profiles](6e5a2fef-d552-42d2-9f1d-2051c98499b7.png)
3. You will be asked to Choose SDK Profile or Application Profile. Select the SDK profile.
4. Choose iOS and fill in the Name field on the General Tab.
   ![General Settings](096c369b-212b-40b0-9285-f3f14edbd8b5.png)
5. Click Custom Settings on the left, and add your custom settings. This is a string field and can contain XML, JSON, or plain text. You can also insert lookup values if desired.
   ![Custom Settings](46ee9319-0fa7-4794-b2b5-8ab1f8c1a47e.png)
6. Save the Profile.

### Step 3: Retrieving the Profile within Your Application

The code to retrieve these settings within the app is very simple if SDK integration is already done from Step 1:

```C
- (void) receivedProfiles: (NSArray *) profiles {
NSLog(@"Profiles received");

AWCustomPayload *custom = [[profiles firstObject] customPayload];
NSString *customSettings = custom.settings;
...
}
```

Here is a screenshot from the debugger showing the sample XML settings entered in the AirWatch Console above:

![6-ios_SDK_received_custom_profile](084359f3-b62e-48d3-9afb-f757f7ab9884.png)

Use these settings however you wish in your app!
