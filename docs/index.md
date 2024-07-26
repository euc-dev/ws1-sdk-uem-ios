---
layout: page
title: Workspace ONE SDK for iOS
hide:
  #- navigation
  - toc
---

The Workspace ONE SDK (formerly known as AirWatch SDK) code library for Apple iOS devices can be used to enable additional app config and security capabilities that may not yet be available natively as part of the AppConfig Community. Certain use cases such as granular analytics can be provided through a deeper integration with the SDK. The Workspace ONE SDK for iOS is also a good choice in deployment scenarios where a MDM profile installation on the device is not possible.

## Application Integration

To integrate the SDK into your app, proceed as follows.

1. Open your app project in Xcode.

2. Navigate to File, Swift Packages, Add Package Dependency...

    This opens the Choose Package Repository screen.

3. Enter the address of this repository `https://github.com/euc-dev/ws1-sdk-uem-ios` and click Next.

    This opens the Choose Package Options screen.

4. Select the rule Branch, leave the default value for branch name, and click Next.

    Xcode will resolve the package dependency, which might take some time.

    When resolution finishes, an Add Package screen opens.

5. Select to add the AWSDK package product to your app target and click Finish.

The SDK has now been added to your application project. You can start the integration work. See the developer documentation.

## Other Integration

The SDK can also be integrated into products other than applications, such as frameworks and libraries. Add code like the following to your `Package.swift` file.

```swift
// swift-tools-version:5.9
import PackageDescription

let package = Package(
    name: "YOUR_PROJECT_NAME",
    dependencies: [
        .package(url: "https://github.com/euc-dev/ws1-sdk-uem-ios.git", from: "24.6.0"),
    ]
)
```

Build your product in the usual way, for example by running the `swift` `build` command.

## Documentation and Reference

A number of resources are available to assist developers in getting started and using this SDK. Developers should start with [Workspace ONE SDK for iOS Getting Started Guide](./Native%20iOS/index.md)

### Additional Resources and Guides

| Name | Size |
|--- | --- |
| Development Guides |   |
| [VMware Workspace ONE for iOS and iPadOS Base Integration Guide](integration/WorkspaceONE_iOS_BaseIntegration.pdf) | 3.1 MB |
| [VMware Workspace ONE for iOS and iPadOS Integration Preparation Guide](integration/WorkspaceONE_iOS_IntegrationPreparation.pdf) | 1.7 MB |
| [VMware Workspace ONE Inactivity Wipe Technical Feature Guide](technical/InactivityWipe.pdf) | 549.8 KB |
| [VMware Workspace ONE SDK Identity Certificate Export Technical Feature Guide](technical/IdentityCertificateExport.pdf) | 259.9 KB |
| [VMware Workspace ONE SDK URL Scheme Replacement Technical Feature Guide](technical/URLSchemeReplacement.pdf) | 483.4 KB |
| [VMware Workspace ONE Shared Device Support Technical Feature Guide](technical/SharedDeviceSupport.pdf) | 349.0 KB |
| [VMware Workspace ONE SDK for iOS (Swift) Developer Guide - latest](developer/WS1iOSDeveloperGuide.pdf) | 2.7 MB |
| General |   |
| [Mobile Application Management Technical White Paper](technical/MobileApplicationManagement.pdf) | 1.2 MB |
| [Require Device Passcode Technical Feature Guide](technical/RequireDevicePasscode.pdf) | 449.4 KB |

## Sample Apps

A number of sample applications with code for integration of mobile applications with the Workspace ONE platform are provided in the [workspace-ONE-SDK-integration-samples](https://github.com/euc-releases/workspace-ONE-SDK-integration-samples) repository.
