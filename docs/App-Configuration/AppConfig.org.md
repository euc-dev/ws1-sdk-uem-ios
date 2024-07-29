---
layout: page
title: AppConfig.org
hide:
  #- navigation
  - toc
---

## Overview

This tutorial will walk developers through how to send dynamic configurations to an app by utilizing the native iOS managed configuration capability as prescribed by the AppConfig.org standard. The steps in this tutorial are done with the assumption that you have gone through the steps in [Getting Started](../getting-started.md) tutorial.

## Requirements

- Minimum Project Deployment Target iOS 8.0 or above
- Requires managed configuration from an MDM server to enable
- This can be implemented without an Xcode workspace, but the use of a workspace is recommended. Once you create the workspace, ***always*** open the `.xcworkspace` file instead of opening the `.xcodeproj` directly.

## Tutorial

At this point in the tutorial, we assume you have already gone through the steps listed in [Getting Started](../index.md) tutorial to enroll a device in your AirWatch environment.

### Implementation

1. Create and open the `<project>.xcworkspace` file in Xcode.
2. Add your existing App to the workspace.
3. Control-click in the empty area of the project navigator, choose “Add Files to “, and select the “AppConfigPasscodeFramework” Xcode project (included in the sample code file) to add it the workspace. See [Apple’s help documentation](https://developer.apple.com/library/ios/recipes/xcode_help-structure_navigator/articles/Adding_an_Existing_Project_to_a_Workspace.html) for more information.
4. Under the `AppConfigSettingsFramework` project in the left-hand menu, open the **Products** group. If `AppConfigSettingsFramework.framework` is listed in red, it has not yet been built. Click the scheme changer and choose the “AppConfigSettingsFramework” scheme, and then press command-B to build the framework.
5. Add `AppConfigSettingsFramework` to “Embedded Binaries” in your app target’s general settings; this will cause it to also be added to “Linked Frameworks and Libraries” immediately below.
6. Edit the application’s AppDelegate:
   - Swift:
     - Import the Framework:
        `import AppConfigSettingsFramework`
     - Declare that AppDelegate implements the `ManagedAppConfigSettingsDelegate` protocol:
        `class AppDelegate: UIResponder, UIApplicationDelegate, ManagedAppConfigSettingsDelegate`
     - Implement the delegate protocol method:

      ```C
        func settingsDidChange(changes: Dictionary<String, AnyObject>) {
            print("Received \(changes)")
        }
      ```

     - Within `application(application: UIApplication, didFinishLaunchingWithOptions` set the delegate and call `start()`

      ```C
        ManagedAppConfigSettings.clientInstance().delegate = self
        ManagedAppConfigSettings.clientInstance().start()
      ```

   - Objective-C:
     - Import the Framework in `AppDelegate.h`:
     `@import AppConfigSettingsFramework;`
     - Declare that AppDelegate implements the `ManagedAppConfigSettingsDelegate` protocol
     `@interface AppDelegate : UIResponder <UIApplicationDelegate, ManagedAppConfigSettingsDelegate>`
     - Implement the delegate protocol method in `AppDelegate.m`:

      ```C
        - (void) settingsDidChange:(NSDictionary<NSString *, id> *) changes {
            NSLog(@"Received changes %@", changes);
        }
      ```

   - Within `application:didFinishLaunchingWithOptions:` set the delegate and call `start()`

    ```C
    [ManagedAppConfigSettings clientInstance].delegate = self;
    [[ManagedAppConfigSettings clientInstance] start];
    ```

### Deploy your app

After you have written the code to receive and read the iOS managed configurations, you’ll need to deploy and managed the app using AirWatch.

1. Go back to your AirWatch admin console.
2. Edit the app you uploaded in the [Getting Started](../index.md) tutorial.
3. Click on Save & Assign and then edit the assignment you had previously created.
4. Expand **Advanced** and then **Application Configuration**
5. Add your configuration keys and values that you want to send to your app.
6. Click on add at the bottom of the page when you’re done to add the assignment
7. Now back on your enrolled mobile device, install your app from the AirWatch App Catalog and run the app to read the assigned configurations you just set.
