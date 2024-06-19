---
layout: page
title: Use DLP to Control the Copy and Paste of Data Out and Into Your SDK-Built Application
hide:
  #- navigation
  - toc
---

Control the copy and paste interaction between your SDK-built applications and non-SDK-built applications. Use the two settings Enable Copy and Paste Out and Enable Copy and Paste Into.

When you set Enable Copy and Paste Out to No, you can only paste copied data from your SDK-built application out to other SDK-built applications.

When you set Enable Copy and Paste Into to No, you can only paste copied data from other SDK-built applications into your SDK-built application.

There are specific limitations with certain UI classes.
* UIWebView and WKWebView
  * The SDK evaluates javascript in UIWebView and WKWebView to get the HTML of selected content. If using WKWebView, javascript must be enabled. Javascript is always enabled in UIWebView.

  * You cannot copy Images in DOC and PDF files loaded in UIWebView or WKWebView due to a technical limitation.
* Out of Process Classes - The SDK does not support copy-out and copy-in restrictions in views that are out of process. For example, the feature does not work in the listed views, and this list is not exhaustive.
  * SFSafariViewController
  * UIDocumentInteractionViewController
  * QLPreviewController
* Other Limitations
  * Two sets of SDK-built applications that have different SSO settings (for example, one is set with SSO on and another with SSO off) cannot share the pasteboard.
  * You cannot copy from an application which has no restriction (Enable Copy and Paste Out set to Yes) and paste that content into a restricted application (Enable Copy and Paste Into set to No).
  * You cannot share a pasteboard between two or more sets of applications that are in different keychain groups.

   For example, VMware productivity applications and custom SDK-built applications cannot share the clipboard. However, multiple custom SDK-built applications from the same developer that are in the same keychain group can share the clipboard.

To add this functionality, create a bundle and PLIST file, locally, and set the keys and values.

## Procedure

1. Create a bundle named AWSDKDefaults.
2. Create a PLIST named AWSDKDefaultSettings.plist and put it in the AWSDKDefaults bundle.
3. In the PLIST, create a Boolean named AWClipboardEnabled and set it to YES.

## Results

After you add the local flag, and your admin sets the default or custom SDK policies for these features in the console, the SDK enforces the restriction. It enforces it across your application’s user interfaces that use cut, copy, and paste in the listed classes and subclasses.
* UITextField
* UITextView
* UIWebView
* WKWebView