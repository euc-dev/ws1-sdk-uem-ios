---
layout: page
title: App Wrapping
hide:
  #- navigation
  - toc
---

## Overview

The steps in this tutorial are done with the assumption that you have gone through the steps in [Getting Started](../getting-started.md) tutorial including the wrapping subsection.

## Requirements

- Enterprise Developer Certificate (can also be ad-hoc developer certificate for testing purposes only)
- Provisioning Profile corresponding with certificate and application
- Access to AirWatch Console on v7.0+
- iOS 7+ Devices

## Developer Considerations

The app developer must follow a specific regimen about what networking APIs are used in the app in order for traffic to be tunneled via wrapping. Application networking calls must be made using one of the following APIs.

### NSURLConnection

- Full Support
- Exceptions/Constraints:
  - Network calls made synchronously on the main thread will not be tunneled.

### NSURLSession

- Partial Support
- Exceptions/Constraints:
  - Requires iOS 8+
  - NSURLSession must use the sharedSession instance.
  - Background configuration types are not supported

### AFNetworking Version 1

- Full Support
- Exceptions/Constraints: None

### AFNetworking Version 2

- Partial Support
- Exceptions/Constraints:
  - Only calls made using `AFHttpRequestOperation`, `AFHttpRequestOperationManager`, and `AFURLConnectionOperation` will be supported with tunneling in wrapped apps.

!!!Note
    Traffic made in app extensions will not be tunneled.

## Tutorial

The app wrapping process consists of 3 main steps:

1. Policy configuration – Define the security policies you want to apply to your app. This is where the tunneling policy will be defined.
2. Wrapping the app – Provide the code signing assets required to wrap the app.
3. Assignment and Deployment – Configure the deployment rules for when the app wrapping is complete.

### Policy Configuration

There are two approaches for assigning policies to your wrapped application. You can use the group-wide default settings or you can create an ad-hoc profile specifically for one or more apps.

1. Log into the AirWatch Console, navigate to Apps & Books in your desired organization group.
2. Click on All Apps & Books Settings.
3. Expand the “Settings and Policies” section and to show the Security Policies, Settings, and Profiles options.
At this point, you can choose from one of two ways to configure the policy. Group-wide default settings or an ad-hoc custom profile.

### Using the Default Profile (Recommended)

1. Select the Security Policies option and enable the AirWatch App Tunnel option.
2. Set your App Tunnel Mode to the proxy you plan on using. (If there is no proxy configured, follow the configure proxy settings link on the UI to walk through setting up your proxy)
3. Click the save button to persist any changes you have made.
4. These changes will reflect via the Default Profile during profile assignment which will be done in a later step in the tutorial.

### Using an Ad-hoc Custom Profile

1. Expand the “Settings and Policies” section and select Profiles.
2. Click on Add Profile and select the App Wrapping Profile.
3. In the General section, assign a name to your profile.
4. Select the Proxy payload and enable app tunnel and set your App Tunnel Mode to the proxy you plan on using.
5. Click Save to create or update your app wrapping profile.

### Wrapping the app

Once you have set up the appropriate configuration policies. The next step is to actually wrap the application.

1. Navigate to the Apps & Books section back on the AirWatch Console and select the list view.
2. Select the internal tab in the list view and add an application.
3. Upload the .ipa file you intend to wrap.
4. Click the “More” tab and select App Wrapping.
5. Enable app wrapping. Choose the app wrapping profile to assign to your wrapped application. (This is what you created in the Policy Configuration section above)
6. Upload your mobile provisioning profile along with its corresponding code signing certificate.
7. Once complete, click “Save and assign” to move to the next portion for deploying your app to the appropriate device smart groups.

### Assignment and Deployment

The last step is to assign who should get the app and when.

1. Click add assignment.
2. Select or create a smart group with your desired set of device assignments.
3. Configure the push mode and deployment time if applicable.
4. Add the assignment.
5. Once ready, click Save and Publish to start the wrapping and deployment process.
