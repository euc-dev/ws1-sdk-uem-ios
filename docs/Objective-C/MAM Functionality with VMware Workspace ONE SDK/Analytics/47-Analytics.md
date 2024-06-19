---
layout: page
title: Analytics
hide:
  #- navigation
  - toc
---

Analytics track the important events that occur within your application. The system uses these metrics to analyze use patterns and to account for how people use your app.

Analytic Types
The Workspace ONE SDK for iOS (Objective-C) offers the several types of analytics.

* Event Analytics – Records and reports information about events specific to your organization that you code into the application.
* Data Usage Analytics – Records and reports information about network traffic to track telecom statistics.

* [Implement the DataSampler](33-Implement-DataStreamer.md)
The DataSampler module (formerly known as Interrogator) samples detailed device data and reports it back to the Workspace ONE UEM console.
* [Develop Event Analytics with the DataSampler](34-Develop-Event-Analytics.md)
The event analytics function requires enabling analytics in the Workspace ONE UEM console and setting up the DataSampler module to report the analytics.
* [Enable Data Tracking in Your SDK Application](35-Enable-Data-Tracking.md)
Enable the data tracking module by embedding a PLIST into your application project.
* [Developing Data Usage Analytics](36-Developing-Data-Usage-Analytics.md)
The VMware Workspace ONE SDK for iOS (Objective-C) allows your application to monitor the amount of network traffic used specifically by your application. It also reports network traffic used to the Workspace ONE UEM console for telecom tracking purposes. The SDK hooks into the common iOS networking classes to monitor the amount of data transferring in an application.
