---
layout: page
title: SDK Setup
hide:
  #- navigation
  - toc
---

## Overview

The steps in this tutorial are NOT required if you are using App Wrapping or using only approaches from AppConfig.org. This tutorial will walk developers through how to setup the core SDK framework for those who have chosen the SDK approach.

Before moving forward to the SDK setup tutorial, ensure you have completed the instructions in the [Getting Started](getting-started.md) tutorial and uploaded your app with an assigned SDK profile.

!!!Important
    Workspace ONE SDK for iOS is distributed as a Swift package and is be available in the [Workspace ONE software development kit (SDK) for iOS repository](https://github.com/orgs/euc-dev/packages/container/package/ws1-sdk-uem-ios).

## Requirements

- iOS 7+
- Xcode
- iOS Test Device
- AirWatch SDK from AirWatch Resource Portal

## Tutorial

### Adding Required Xcode Frameworks

The AirWatch SDK depends on the following frameworks to function properly. Please follow the steps below to add the necessary frameworks to your project:

1. Select the project in the Navigator pane in Xcode.
2. Verify that the proper build target is selected on the left side under TARGETS.
3. Select the Build Phases tab.
4. Expand the Link Binary With Libraries section.
5. Click the + button at the bottom of the section to add the required frameworks and libraries.
6. Select each one of the following frameworks and libraries and click Add.
    - libc++.dylib
    - libsqlite3.dylib
    - libstdc++.6.0.9.dylib
    - libz.dylib
    - Accelerate.framework
    - AssetsLibrary.framework
    - AudioToolbox.framework
    - AVFoundation.framework
    - CFNetwork.framework
    - CoreData.framework
    - CoreFoundation.framework
    - CoreGraphics.framework
    - CoreLocation.framework
    - CoreMedia.framework
    - CoreMotion.framework
    - CoreTelephony.framework
    - CoreText.framework
    - CoreVideo.framework
    - Foundation.framework
    - ImageIO.framework
    - LocalAuthentication.framework
    - MediaPlayer.framework
    - MessageUI.framework
    - MobileCoreServices.framework
    - QuartzCore.framework
    - Security.framework
    - SystemConfiguration.framework
    - UIKit.framework

!!!Note
    When adding libraries, instead of filenames ending in `.dylib`, you may see filenames ending in `.tbd`, such as `libc++.tbd`. If you see files with the `.tbd` extension, select them; they are text-based wrappers that point to the corresponding `.dylib` files, and they will appear in your list of selected libraries with the `.dylib` extension. If you have difficulties, please see [this thread](https://forums.developer.apple.com/message/8609) on the Apple Developer Forums.

### Adding Required Xcode Bundle Resources

The SDK depends on the following bundle resources to function properly, so add the necessary bundles to your project. Find some of these bundles inside the AWSDK.framework file structure.

- AWKit.bundle
- EVAssets.bundle
- EVImages.xcassets
- SDKLocalization.bundle

### Adding the Workspace ONE SDK Frameworks

The Workspace ONE frameworks are found inside the provided Workspace ONE SDK.dmg archive.

- Drag `AWSDK.framework` into the Frameworks group in the sidebar of Xcode. Make sure to check Copy items into destination group’s folder (if needed).
- Ensure the application is linking against the `AWSDK.framework`. To verify, click the Build Phases tab in the target’s properties. Expand the Link Binary With Libraries section to see if `AWSDK.framework` is added. If not, click the +button and select `AWSDK.framework`.
- Wherever the  SDK is used, be sure to import the umbrella header. Add `#import <AWSDK/AWSDKCore.h>` to the top of the file.

### Adding Linker Flags

Since the Workspace ONE SDK uses Objective-C categories, a few linker flags must be passed to the linker to properly load them. Follow the next steps to configure your project:

- Select the project or workspace in the Groups & Files pane.
- Select the target for the application.
- Select the Build Settings tab.
- Ensure the `-ObjC` flag is added in the Other Linker Flags entry.

### Valid Architectures

The SDK currently supports the following architectures:

- armv7
- armv7s
- arm64

The Workspace ONE SDK does not run on the simulator at this time. Be sure not to compile your application for the x86 architecture.

### Callback Scheme Registration

In order to receive a callback from the Workspace ONE Agent, your application will need to expose a custom scheme in Info.plist:

1. Navigate to Supporting Files in Xcode.
2. Select the file `Info.plist`.
3. Navigate to the URL Types section. If it does not exist, add it, as an Array, at the Information Property List root node of the .plist.
4. Ensure that the Item 0 entry of the URL Types array is a Dictionary. In that dictionary, create a new String entry named URL identifier and set its name to a unique value that identifies this URL scheme. Apple recommends that the name be based on the package name of your application, e.g. `com.airwatch.SampleIntegrationApp.awsdksampleapp`.
5. In the same dictionary, create a new Array entry named URL Schemes.
6. Set the next Item 0 under URL Schemes to the desired callback scheme. Choose a value that begins with a letter and contains only letters, digits, or the characters `+`, `-`, and `.`. Workspace ONE Agent will read this value and use to construct the URLs it uses to communicate with your app.

When you are finished, the Info.plist editor will look something like this:
![Sample Integration info.plist](a9dbd943-dc9f-454c-8c39-ea5ef185bfbe.png)

If you are viewing raw keys and values, the key names for URL Types, URL identifier, and URL Schemes are CFBundleURLTypes, CFBundleURLName, and CFBundleURLSchemes respectively.
![Raw Keys Sample Integration info.plist](be5711f2-6dc9-44aa-9f08-8f0ed00316bd.png)

For more information, see [App Programming Guide](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Inter-AppCommunication/Inter-AppCommunication.html#//apple_ref/doc/uid/TP40007072-CH6-SW1) for iOS in the Apple iOS Developer Library.

### Registering the Anchor App (iOS 9.0 and above)

Beginning in iOS 9.0, as a security feature, iOS applications must “whitelist” the schemes of any custom URLs they may wish to open. If you build with and link against the iOS 9.0 SDK — even if your app is meant to run on earlier iOS versions — your app must declare the URL schemes for the Workspace ONE Agent and/or Workspace applications so it can initiate communication with them.

1. Navigate to Supporting Files in Xcode.
2. Select the file Info.plist.
3. Add an Array key named LSApplicationQueriesSchemes to the root Information Property List dictionary.
4. Add the URL schemes used by the Workspace ONE Agent and/or Container application to the array. The scheme for Agent is `airwatch`, and the scheme for the Container is `workspace`. If you know that your app will be run only on devices using Agent, or only on devices using Container, you can declare only the appropriate scheme; if you are not sure, you can safely declare both.
![Declare Schemes](94c07394-94c0-4567-ba7c-e52ed9ea06fa.png)

You can think of this process as the converse of registering a callback scheme; the callback scheme identifies a URL scheme that your app will be listening for, while the LSApplicationQueriesSchemes list identifies URL schemes that your app can send communications to.

For more information, see the [Information Property List Key Reference](https://developer.apple.com/library/ios/documentation/General/Reference/InfoPlistKeyReference/Articles/LaunchServicesKeys.html#//apple_ref/doc/uid/TP40009250-SW14) in the Apple iOS Developer Library.

### Disable Bitcode

The Workspace ONE SDK is not built using Apple’s new Bitcode format, so your application cannot be built with Bitcode. To disable Bitcode, navigate to the Xcode build settings for your app target and set Enable Bitcode to No.
![Disable Bitcode](1fe18961-7858-4365-b414-f827d41f5e41.png)

For more information on Bitcode, see [Bitcode](https://developer.apple.com/library/tvos/documentation/IDEs/Conceptual/AppDistributionGuide/AppThinning/AppThinning.html#//apple_ref/doc/uid/TP40012582-CH35-SW2) in the App Distribution Guide in the Apple iOS Developer Library.

### Initialize the SDK

The AWController class is the main entry point for the Workspace ONE SDK. It automatically handles and implements certain core SDK functionalities such as:

- Passcode Mode
- Single Sign On (SSO)
- SSID Filtering
- Proxy and Tunneling

In order to start using the Workspace ONE SDK, you must initialize it when your application starts. Initialization allows the SDK to obtain your profile from the device server and configure the features above.

The following example demonstrates how to initialize the SDK.

1. Inside your app delegate’s implementation (.m) file, import `<AWSDK/AWController.h>` and add the following code to `application:didFinishLaunchingWithOptions:` to set up the SDK controller:

```C
#import <AWSDK/AWController.h>
```

```C
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

    // Initialize the SDK by:
    // 1) Getting the singleton instance of AWController.
    AWController *controller = [AWController clientInstance];

    // 2) Defining the callback scheme so the app can get called back --
    // this should match the URL scheme you defined in "Callback Scheme Registration".
    controller.callbackScheme = @"awsdkcallback";

    return YES;
}
```

2. In your app delegate’s `applicationDidBecomeActive:` method, call `start` on the AWController singleton. This will cause the Workspace ONE SDK to initialize itself and contact the device management server.

```C
- (void)applicationDidBecomeActive:(UIApplication *)application {
   [[AWController clientInstance] start];
}
```

!!!Note
    It is best not to call the start method above in `application:didFinishLaunchingWithOptions:` because the SDK may display modal view controllers that rely on a reference view controller. In certain cases when you use a storyboard, the view controllers have not yet been generated at the time `application:didFinishLaunchingWithOptions:` is called. To avoid any unstable behavior with the app, call `[[AWController clientInstance] start]` inside `applicationDidBecomeActive:` instead.

3. Finally, override `application:openURL:sourceApplication:annotation:` to handle communication from the Workspace ONE Agent or AirWatch Workspace app.

```C
- (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *) sourceApplication annotation:(id)annotation {
    return [[AWController clientInstance] handleOpenURL:url fromApplication:sourceApplication];
}
```

If your goal is simply to add a passcode screen to the application, you’re done! The SDK presents a passcode screen when your application starts or returns from the background. You do not need to add any code to your view-controller classes to enable this.

For greater functionality, however, you will find it useful to create a delegate object to receive and react to messages from the SDK. This is described in the section below.

## Adding an AWSDKDelegate

The `AWSDKDelegate` protocol defines the methods the SDK expects to use to communicate with your app. It contains seven methods, although you will usually only need to implement a few of them.

To add an `AWSDKDelegate` to your application:

1. Create a new class that implements the `AWSDKDelegate` protocol. Give it a weak property to hold a reference to your app delegate.

```C
#import <AWSDK/AWSDKController.h>

@interface SampleAppSDKDelegate : NSObject <AWSDKDelegate>

@property (weak, nonatomic) AppDelegate *appDelegate;

@end
```

Leave this class empty for now; we will return to it shortly.

2. Inside the app delegate, import the header of your `AWSDKDelegate` implementation, add an instance variable to hold a reference to it, and add the following code to `application:didFinishLaunchingWithOptions:` to set up the SDK controller:

```C
#import "SampleAWSDKDelegate.h"
```

```C
@implementation AppDelegate

SampleAWSDKDelegate *sdkDelegate;

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

    // Configure the Controller by:
    // 1) Getting the singleton instance of AWController.
    AWController *controller = [AWController clientInstance];

    // 2) Defining the callback scheme so the app can get called back --
    // this should match the URL scheme you defined in "Callback Scheme Registration".
    controller.callbackScheme = @"UrlScheme";

    // 3) Setting the controller's delegate to know when the initialization has been completed.
    SampleAWSDKDelegate *sdkDelegate = [SampleAWSDKDelegate new];
    sdkDelegate.appDelegate = self;
    controller.delegate = sdkDelegate;

    return YES;
}
```

Now return to the `AWSDKDelegate` implementation you created in step 1. You can now implement the delegate methods you need to support your application.

1. `(void)initialCheckDoneWithError: (NSError *)error`
  This delegate method is invoked when the SDK initializes. This method is ALWAYS called after the SDK passes through the initialization flow. If the initialization is successful then the error object is nil. If the initialization fails, then the error object contains the reason code for why it fails.In most cases, you will simply want to check the error parameter of this method. If it is nil, then the SDK was initialized successfully, and your application can proceed. If error is not nil, then some problem was encountered in initializing the SDK, in which case you may not want to allow the user to access the rest of the application. Instead, you might choose to log the error message and/or provide a “retry” button to allow the user to launch another attempt to call `[[AWController clientInstance] start]`.
  
  !!!Note
    Calling start in AWController automatically sets up the proxy to redirect network traffic, but the proxy does not actually begin to handle traffic until this callback is received. To ensure that you do not transmit sensitive data outside your proxy connection, do not make any network calls that need to go through your proxy until initialCheckDoneWithError: is called.

2. `(void)receivedProfiles:(NSArray *)profiles`
  This delegate method is invoked when settings of an SDK profile assigned to this application update on the AirWatch Admin Console. It notifies the app that new settings are available. The profiles array contains the list of `AWProfileobjects` that contain configuration payloads.If you have any custom configuration values in the app’s SDK profile, you will check for them here to see if they have been updated.
3. `(void)lock`
  This method is invoked when the SSO session has expired and the SDK passcode input view is displayed. It is intended for use as an indicator of when a user should no longer have to access the app.You do not need to implement this method to have simple passcode protection. However, if you choose to display a “guard screen” over your app to prevent sensitive data from being visible when the app is locked, this method is where you would display that screen.
4. `(void)unlock`
  This delegate method is invoked immediately after you initiate a new SSO session by inputting the correct password/passcode.If you have implemented the lock method, you will need to implement this method to undo whatever you did in lock, e.g., you would hide a “guard screen” here. If you did not implement lock, you will not need to implement unlock.
5. `(void)wipe`
  This method is invoked when the SDK identifies that the device has been wiped or unenrolled from the AirWatch Admin Console. This method is also invoked when a user reaches the limit of failed passcode attempts defined in the SDK profile.Your application should implement this method to delete any databases or other resources used by your app.
  
  !!!Note
    that the AirWatch SDK does not take any action other than invoking this method when it receives a “wipe” instruction, whether from the server or from a passcode retry count failure. The application developer must implement the necessary local app wipe logic.

6. `(void)stopNetworkActivity`
  This method is invoked when the device connects to an SSID that is blacklisted in the SDK profile. If your application transfers sensitive data across network connections, you may choose to implement this method to pause or cancel those connections while the device is on a blacklisted network.
7. `(void)resumeNetworkActivity`
  This method is invoked when the device connections to a valid SSID after network activity is already stopped. If you stopped network activity in `stopNetworkActivity`, you will restart it here.

## Debug Your Application

Your application is now integrated with the SDK! Once you call the start method, you should expect to receive the `initialCheckDoneWithError` callback without any errors.

In order for the SDK to initialize successfully, your app bundle ID will need to match the bundle ID of the application you uploaded in [Getting Started](index.md) tutorial section.

!!!Note
    The Workspace ONE SDK does not run on the simulator at this time.

## Next Steps

Once the SDK setup is completed, move on to the next SDK sections to implement the feature specific logic.
