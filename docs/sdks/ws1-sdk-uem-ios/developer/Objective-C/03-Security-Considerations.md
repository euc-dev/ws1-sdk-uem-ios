---
layout: page
title: Security Considerations for OpenURL in iOS
permalink: /sdks/ws1/ws1-sdk-uem-ios/
hide:
  #- navigation
  - toc
---

With changes to OpenURL in iOS 13, update to the latest version of the Workspace ONE SDK for iOS (Objective-C) to mitigate possible security issues.

## Actions

If you build apps with the Workspace ONE SDK for iOS (Objective-C) and deploy them to devices that are enrolled with the Workspace ONE Intelligent Hub, consider updating to the latest versions of the Workspace ONE Intelligent Hub for iOS and the Workspace ONE SDK for iOS (Objective-C).

You can add the key RestrictCredentialsExchangeWithThirdPartyApplications to the default SDK setting profile assigned to the Workspace ONE Intelligent Hub. If the attack scenarios mentioned in Security Considerations might impact your use cases, consider adding the key. Adding the key affects the user experience of SDK applications. Users must authenticate when they first start every Objective-C SDK app after installation, even if single sign-on is enabled.

## OpenURL Changes

iOS 13 includes a change involving parameters returned during the OpenURL process between applications from different developer accounts. This change directly affects the communication mechanism between the Workspace ONE SDK and Workspace ONE Intelligent Hub or the Workspace ONE Legacy application.

## Security Considerations

Workspace ONE SDK for iOS (Objective-C) has a workflow where the Workspace ONE SDK retrieved an authentication token with user credentials from Workspace ONE Intelligent Hub using the iOS OpenURL mechanism for single sign-on purposes. Before the Workspace ONE Intelligent Hub app returned the credentials back to the requesting SDK, Workspace ONE Intelligent Hub validated the bundle identifier of the requesting SDK-integrated app to ensure it was legitimate. By combining this Workspace ONE Intelligent Hub validation mechanism with MDM device restrictions to prevent devices from trusting unmanaged enterprise apps, users were protected against malicious applications pretending to be SDK-integrated apps.

iOS 13 no longer provides the bundle identifier of the requesting SDK-integrated app to the Workspace ONE Intelligent Hub (older OS versions still provide the bundle identifier). Not having the bundle identifier restricts the Workspace ONE Intelligent Hub from performing the validation. The lack of this validation creates an avenue for malicious applications to mask themselves as the Workspace ONE SDK for iOS (Objective-C).

For example, if an opportunistic attacker makes an iOS user install a malicious app from the App Store, and if the malicious app knows the Workspace ONE SDK's OpenURL protocol, the app can appear legitimate. The malicious app can retrieve the user's login credentials from the Workspace ONE Intelligent Hub app.

## Security Mitigations

To mitigate possible problems, perform one of the listed actions.  
* Consider updating your Workspace ONE SDK for iOS (Objective-C) apps to use the Workspace ONE SDK for iOS (Swift).  
The Workspace ONE SDK for iOS (Swift) does not use the OpenURL mechanism for single sign-on purposes. Instead, the first Workspace ONE SDK for iOS (Swift) app installed on the device requires the user to log in. Subsequent SDK-integrated apps that share the keychain login, do not need manual login after the first app.

* If the device is MDM enrolled, disable the menu item in the MDM profile restriction for Allow user to trust unmanaged enterprise apps. Disabling this menu item prevents malicious spoofed applications from being installed and from running on the device.
  
* If the device is MDM enrolled and supervised, disable the menu item in the MDM profile restriction for Allow installing public apps. Disabling this menu item prevents malicious public apps that are not permitted by the administrator from being installed on the device.
  
* You can add a key, `RestrictCredentialsExchangeWithThirdPartyApplications`, to the custom settings payload in the default SDK settings profile assigned to the Workspace ONE Intelligent Hub for iOS. Set the value to `true`. If you do add the key, it can lead to usability degradation, so add it if you see the mentioned security gap as a serious threat.  
This key sets the Workspace ONE Intelligent Hub to not return the credentials to any requesting SDK-integrated app. This key also sets Workspace ONE SDK for iOS (Objective-C) apps to no longer share the integrated authentication certificate credentials. Each Workspace ONE SDK for iOS (Objective-C) app refetches its own integrated authentication credentials separately.  
Important: You must format the custom settings payload correctly. You can add keys within the brackets, but do not add any strings outside of the brackets.
```
{
"RestrictCredentialsExchangeWithThirdPartyApplications": true
}
```