---
layout: page
title: Developing Data Usage Analytics
hide:
  #- navigation
  - toc
---

The VMware Workspace ONE SDK for iOS (Objective-C) allows your application to monitor the amount of network traffic used specifically by your application. It also reports network traffic used to the Workspace ONE UEM console for telecom tracking purposes. The SDK hooks into the common iOS networking classes to monitor the amount of data transferring in an application.

## AWSDKDefaultSettings.plist

The following keys are in the PLIST.

* AWDataUsageConfiguration
* SyncInterval – Interval which defines how often the samples of data transmit to the Workspace ONE UEM server.
   * kSyncOnResume
   * kSyncPerDayBasis
  
      If data use tracking is enabled but SyncInterval is not defined, this key is the default value.

   * kSyncEveryOneHour
   * kSyncEveryTwoHours
   * kSyncEveryFourHours
   * kSyncEveryEightHours
* Network – Type of data to collect.
   * kNetworkMonitorWWAN – Track only cellular data.

      Default if network is not defined and data tracking is enabled.

   * kNetworkMonitorWIFI – Track only WIFI data.
   * kNetworkMonitorBoth – Track both WIFI and cellular data.
* AWDataUsageEnabled – Enable tracking.

## Transmit to the Workspace ONE UEM Server

No additional code is required for transmitting data usage analytics to the Workspace ONE UEM server. The SDK checks on every app launch if the interval for transmitting to Workspace ONE UEM has been reached and handles the transmission accordingly.

Event analytics requires implementation of the DataSampler class to transmit.

## Supported Networking Classes

SDK data usage tracking is supported for the listed iOS network classes.
* NSURLSession
    
    With the exception that traffic made using dataTaskWithRequest and dataTaskWithURL is not monitored on iOS 7 devices.
* NSURLConnection
* AVPlayer