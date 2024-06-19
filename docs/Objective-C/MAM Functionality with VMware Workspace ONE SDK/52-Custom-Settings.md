---
layout: page
title: Custom Settings
hide:
  #- navigation
  - toc
---

The VMware Workspace ONE SDK allows you to define your own custom settings for your application using an SDK Profile. You can paste raw text in this section, and the SDK makes this content available inside the application using the AWCustomPayload object.

You can define an XML, JSON, or key-value pairs for your settings and parse the raw text in the application once it is received. However, you can use other text formats like CSV or plain text.

## Implementation in Xcode

The sample shows how to retrieve custom settings from the local cached settings.

```
      // Get an instance of the Command Manager
      AWCommandManager *commandManager = [AWCommandManager sharedManager];
      // Get a pointer to the SDK Profile stored locally.
      AWProfile *profile = [commandManager sdkProfile];
      // profile may be nil if an AWProfile has not been received from the console
      if (profile == nil)
      {
      NSLog(@"There is no SDK Profile currently installed");
      } else
      {
      AWCustomPayload *customPayload = [profile customPayload];
      if (customPayload != nil)
      {
      NSString *customSettings = [customPayload settings];
      // Do custom processing on your settings.
      NSLog(@"%@", customSettings);
      }
      }
```