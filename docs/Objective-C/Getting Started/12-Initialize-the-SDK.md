---
layout: page
title: Initialize the SDK
hide:
  #- navigation
  - toc
---
 
Before you can use the SDK, you must initialize it. The AWController class is the main component responsible for initializing the SDK.

In addition, it automatically handles and implements certain core SDK functionalities to improve ease of integration for developers, such as the following functions:
* Passcode mode
* Single sign-on (SSO)
* SSID filtering
* Proxy and tunneling

Calling start in AWController automatically sets up the proxy to redirect traffic. However, you must wait until the initial CheckDoneWithError callback is received before any network traffic redirects. Wait until the SDK finishes setting up before making any network calls through your proxy.

## Procedure  
1. Import the `<AWSDK/AWController.h>` header file. Associate the AWControllerDelegate to your app delegate.  
`@interface AppDelegate : UIResponder <UIApplicationDelegate, AWSDKDelegate>`  
2. Inside the app delegate, implement the following code:
` - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions{// Configure the Controller by:AWController *controller = [AWController clientInstance];// 1) defining the callback scheme so the app can get called back,controller.callbackScheme = @"UrlScheme";// 2) set the delegate to know when the initialization has been completed.controller.delegate = self; return YES;}`
3. Start the SDK initialization inside the applicationDidBecomeActive delegate method.  
`- (void)applicationDidBecomeActive:(UIApplication *)application {[[AWController clientInstance] start];}`  
Do not call the start method in didFinishLaunchingWithOptions because the SDK may display modal view controllers that rely on a reference view controller. Sometimes, when you use a storyboard, the view controllers have not yet been generated at the time `didFinishLaunchingWIthOptions` is called. To avoid any unstable behavior with the app, call `[[AWController clientInstance] start]` inside applicationDidBecomeActive instead.  
4. Implement the code to handle the callback from the Workspace ONE Intelligent Hub or Container app.
` - (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation {return [[AWController clientInstance] handleOpenURL:url fromApplication:sourceApplication];}`
5. Implement the remaining delegate methods:
`- (void)initialCheckDoneWithError: (NSError *)error`  
This delegate method is invoked when the SDK initializes. This method is ALWAYS called after the SDK passes through the initialization flow. If the initialization is successful, then the error object is nil. If the initialization fails, then the error object contains the reason code for why it fails.
`- (void)receivedProfiles:(NSArray *)profiles`  
This delegate method is invoked when settings of an SDK profile assigned to this application update on the Workspace ONE UEM console. It notifies the app that new settings are available. The profiles array contains the list of AWProfile objects that contain configuration payloads.
`- (void)unlock`  
This delegate method is invoked immediately after you initiate a new SSO session by inputting the correct password/passcode.
`- (void)lock`  
This method is invoked when the SSO session has expired and the SDK passcode input view is displayed. It is intended for use as an indicator of when a user no longer has to access the app. This lock allows the developer to implement the necessary logic to take the proper action for when the app is locked.
`- (void)wipe`  
This method is invoked when the SDK identifies that the device has been wiped or unenrolled from the Workspace ONE UEM console. This method is also invoked when a user reaches the limit of failed passcode attempts defined in the SDK profile.
Note: TheWorkspace ONE SDK for iOS (Objective-C) only invokes this method, and it takes no other actions. The application developer must implement the necessary local app wipe logic.
`- (void)stopNetworkActivity`  
This method is invoked when the device connects to an SSID that is blocked in the SDK profile.
`- (void)resumeNetworkActivity`  
This method is invoked when the device connections to a valid SSID after network activity is already stopped.

## What to do next  
For iOS 9+, ensure that the Device Services server meets Apple's security requirements. The SDK must communicate with the Device Services server to run. The system might block communication if the server does not comply with requirements. Search the Apple Developer site for current application transport security requirements:  
[https://developer.apple.com/library/prerelease/ios/releasenotes/General/WhatsNewIniOS/Articles/iOS9.html#//apple_ref/doc/uid/TP40016198-SW1](https://developer.apple.com/library/prerelease/ios/releasenotes/General/WhatsNewIniOS/Articles/iOS9.html#//apple_ref/doc/uid/TP40016198-SW1).
