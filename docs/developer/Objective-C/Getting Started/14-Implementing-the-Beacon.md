---
layout: page
title: Implementing the Beacon
#permalink: /sdks/ws1/ws1-sdk-uem-ios/developer/Objective-C/
hide:
  #- navigation
  - toc
---

You can set up the Beacon to send device information to the Workspace ONE UEM console by specifying a time interval. Generic device information such as the device name, OS version, and compromised status is sampled. In addition, the Beacon module is used to start location services by specifying a location mode.

## Configuration of Location

To take advantage of the location functionality of the Beacon, the host application registers itself as needing location updates in the background. In the info.plist file, set the UIBackgroundModes array with a value configured as location. For information on the location functionality of the Beacon, refer to the Declaring Your App's Supported Background Tasks section in the App Programming Guide for iOS at [https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/BackgroundExecution/BackgroundExecution.html#//apple_ref/doc/uid/TP40007072-CH4-SW1](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/BackgroundExecution/BackgroundExecution.html#//apple_ref/doc/uid/TP40007072-CH4-SW1).

### Sample Code

```
  // Initialize Beacon.   Modify the values as needed. 
AWBeacon *_beacon = [[AWBeacon alloc] initWithAPNSToken:nil
  transmitInterval:300
    locationGroup:nil
      locationMode:AWLocationModeDisabled 
        distance:kCLDistanceFilterNone];
 
  // Starts the beacon to send periodically a ping to the server.
  [_beacon start];

  // Force to send a ping right now.
  [_beacon send];
```

  * initWithAPNSToken – Determines if your application uses APNS tokens and sends tokens to the Workspace ONE UEM console. You can send this value as nil.
  * transmitInterval – Represents the frequency in which the Beacon checks in with the Workspace ONE UEM console (in seconds).
  * locationGroup – Corresponds to the organization group. If your application uses authentication, it prompts users to log in. You can send this value as nil.
  * locationMode – Uses location services for the Beacon and includes the coordinates when reporting back to the server. This method also sets up the Beacon to run in the background.
    * AWLocationModeDisabled – Specifies no location mode.
    * AWLocationModeStandard – Captures data using the GPS (on only GPS-enabled devices), which can consume battery power when enabled.

    Note: For GPS sampling to function, ensure your application supports location tracking. For more information, see Apple's documentation at https://developer.apple.com/documentation/corelocation.
    * AWLocationModeSignificant – Uses the significant location services from iOS and provides updates only when the device location changes at a significant level. Consider using this mode if you want to use location services.
  * distance – Determines if you are using the standard location servers and sets the threshold, in meters, of when to generate a location service notification.

## Starting and Stopping the Beacon

Once you create an instance of the Beacon with the appropriate configuration settings, you can start it or stop it at any time. Start the Beacon after initializing the SDK, and leave it running permanently.

```
[_beacon start];  // Starts sending information to the AW Console 
[_beacon stop];  // Stops sending information to the AW Console
```

## Manually Sending a Beacon Message

Instead of waiting for the next interval to send a Beacon to the server, you can explicitly invoke the send command and a packet will be sent to the server.

```
// Force to send a ping right now.[_beacon send];
```
