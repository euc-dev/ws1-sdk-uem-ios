# Workspace ONE Software Development Kit Swift Package

This repository contains the Swift package description for the Workspace ONE software development kit (SDK) for iOS. You can integrate the SDK into your app using Swift package manager in Xcode.

The Workspace ONE SDK (formerly known as AirWatch SDK) code library for Apple iOS devices can be used to enable additional app config and security capabilities that may not yet be available natively as part of the AppConfig Community. Certain use cases such as granular analytics can be provided through a deeper integration with the SDK. The Workspace ONE SDK for iOS is also a good choice in deployment scenarios where a MDM profile installation on the device is not possible.

This repo is structured to feed into the developer.omnissa.com Developer Portal via the [](https://github.com/euc-dev/developer.omnissa.github.io) repo using MkDocs published by GitHub Pages. All documentation should be created in MarkDown format with the capabilities of MkDocs and the Material theme in mind under the /docs/sdks/ws1-sdk-uem-ios folder. This folder will be integrated into the [developer portal repo](https://github.com/euc-dev/developer.omnissa.github.io) when built using a GitHub Action.

## Downloads

By downloading, installing, or using the Software, you agree to be bound by the terms of Omnissa’s Software Development Kit License Agreement unless there is a different license provided in or specifically referenced by the downloaded file or package. If you disagree with any terms of the agreement, then do not use the Software.

## Application Integration

To integrate the SDK into your app, proceed as follows.

1. Open your app project in Xcode.

2. Navigate to File, Swift Packages, Add Package Dependency...

    This opens the Choose Package Repository screen.

3. Enter the address of this repository
    `https://github.com/euc-dev/ws1-sdk-uem-ios` and click Next.

    This opens the Choose Package Options screen.

4. Select the rule Branch, leave the default value for branch name, and click
    Next.

    Xcode will resolve the package dependency, which might take some time.

    When resolution finishes, an Add Package screen opens.

5. Select to add the AWSDK package product to your app target and click Finish.

The SDK has now been added to your application project. You can start the
integration work. See the developer documentation.

## Developer Documentation

Full instructions for integrating your app with the Workspace ONE SDK for iOS are
available on the developer.omnissa.com website. See:
[https://euc-dev.github.io/ws1-uem-sdk-for-ios/](https://euc-dev.github.io/ws1-uem-sdk-for-ios/)

## Other Integration

The SDK can also be integrated into products other than applications, such as
frameworks and libraries. Add code like the following to your `Package.swift`
file.

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

Build your product in the usual way, for example by running the `swift` `build`
command.

## License

This project is Licensed under the BSD 2-Clause License (Mozilla Public License Version 2.0) ; you may not use this file except in compliance with the License.

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
