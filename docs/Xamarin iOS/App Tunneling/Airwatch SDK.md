---
layout: page
title: Airwatch SDK
hide:
  #- navigation
  - toc
---

## Overview

The steps in this tutorial are done with the assumption that you have gone through the steps in General Setup tutorial as well as the SDK Setup section.

In this section, you will learn how to tunnel using the iOS SDK with Xamarin integration. The purpose of app tunneling is to redirect the traffic in your application through a specific gateway to access internal resources in your organization. This is possible through the use of the AirWatch Mobile Access Gateway (MAG), an F5 or a standard proxy.

Important: You will need to download the SDK binary separately via [https://components.xamarin.com/view/awsdk](https://components.xamarin.com/view/awsdk).

## Developer Considerations

Due to platform and other technical limitations, only network traffic made from certain network classes can tunnel.

- `NSURLConnection` – Calls made using `NSURLConnection` tunnel with one exception that calls made synchronously on the main thread do not tunnel.
- `NSURLSession` – Calls made using `NSURLSession` tunnel only on iOS 8 devices and depend on the configuration used. Default and ephemeral configuration types tunnel; however, background configuration types do not tunnel.
- `CFNetwork` – Most calls made using `CFNetwork` tunnel; however, `CFSocketStreamdoes` not tunnel.
- URLs containing .local– Requests with URLs containing .local do not tunnel. Various Apple services on the device utilize this .local string pattern, so the SDK does not attempt to tunnel these requests through the Mobile Access Gateway (MAG) in order to avoid interfering with these services.

## Tutorial

Proxy configuration with the iOS SDK in Xamarin Studio or Visual Studio is setup via the following steps:

1. Policy configuration – Tunnel profile is configured via the AirWatch Console.
1. Logic Implementation – Connect to an endpoint in your application using one of the supported networking classes
1. Assignment and Deployment – Configure the assignment and deployment rules for your organization’s devices.

### Policy Configuration

At this point in the tutorial, we assume you have already gone through the steps of uploading your app and assigning the wrapping profile mentioned in General Setup.

Log into the AirWatch Console and identify if the wrapping profile you assigned to your application is the default profile or a custom profile. If there is no profile assigned, you can choose from one of two ways to configure the policy: group-wide default settings or an ad-hoc custom profile.

### Using the Default Profile (Recommended)

1. If the profile assigned is the default profile, then the policy settings can be edited by navigating to Apps & Books > All Apps & Books Settings > Apps > Settings And Policies > Security Policies.
1. Enable the AirWatch App Tunnel option.
1. Set your App Tunnel Mode to the proxy you plan on using. (If there is no proxy configured, follow the configure proxy settings link on the UI to walk through setting up your proxy)
1. Click the Save button to persist any changes you have made.

!!!Note
    These changes will reflect via the Default Profile during profile assignment which will be done in a later step in the tutorial.

### Using an Ad-hoc Custom Profile

1. Navigate to Apps & Books > All Apps & Books Settings > Apps > Settings And Policies > Profiles.
1. Select your assigned profile, or click on Add Profile and select the App Wrapping Profile.
1. In the General section, assign a name to your profile.
1. Select the Proxy payload and Enable App Tunnel and set your App Tunnel Mode to the proxy you plan on using.
1. Click Save to create or update your app wrapping profile.
 
### Logic Implementation

#### Implementation in Xamarin Studio or Visual Studio

To use tunneling, AirWatch recommends that developers use the [ModernHttpClient](https://components.xamarin.com/view/modernhttpclient) library. This client can be downloaded via Xamarin Components. To use this library import the `ModernHttpClient` Component into your project, and add the appropriate imports to begin using it:

```C
using ModernHttpClient;
using System.Net.Http;
```

Once the component is re, simply use the `HTTPClient` [constructor](https://msdn.microsoft.com/en-US/library/windows/apps/windows.web.http.httpclient#constructors) that supplies an `IHTTPFilter`, and use the `NativeMessageHandler` filter provided by `ModernHttpClient`:

`var httpClient = new HttpClient (new NativeMessageHandler ());`

This works because `ModernHttpClient` uses the platform native APIs mentioned above, which are compatible with tunneling.

#### Assignment and Deployment

The last step is to assign who should get the app and when.

1. Click Add Assignment.
1. Select or create a smart group with your desired set of device assignments.
1. Configure the push mode and deployment time if applicable.
1. Add the assignment.
1. Once ready, click Save and Publish to start the wrapping and deployment process.

Once you receive the `initialCheckDoneWithError` callback from the `AWSDKDelegate`, check to see if the error object is nil or not.
