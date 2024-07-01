---
layout: page
title: AppConfig.org
hide:
  #- navigation
  - toc
---

## Overview

This tutorial will walk developers through how to send dynamic configurations to an app by utilizing the native iOS managed configuration capability as prescribed by the AppConfig.org standard. The steps in this tutorial are done with the assumption that you have gone through the steps in [General Setup Tutorial](../index.md).

## Requirements

- Minimum Project Deployment Target iOS 8.0 or above
- Requires managed configuration from an MDM server to enable

## Getting Started

1. Either add the ManagedAppConfig Project to your existing Solution, or build the ManagedAppConfig.dll and add it to the References section of your Project.
2. Modify AppDelegate.cs to import the ManagedAppConfig DLL:
`using ManagedAppConfig;`
3. Modify the AppDelegate class definition to implement IManagedAppConfigSettingsCallback:
`public class AppDelegate : UIApplicationDelegate, IManagedAppConfigSettingsCallback`
4. In your AppDelegate.cs add the following lines within FinishedLaunching:

```C
public override bool FinishedLaunching (UIApplication application, NSDictionary launchOptions)
{
    ManagedAppConfigSettings.ClientInstance.callback = this;
    ManagedAppConfigSettings.ClientInstance.Start ();

    return true;
}
```

5. Implement the IManagedAppConfigSettingsCallback interface:

```C
public void SettingsDidChange (Dictionary<string, object> changes)
{
    foreach (KeyValuePair<string, object> entry in changes) {
       var message = String.Format ("Changed: {0} : {1}", entry.Key, entry.Value);
       Debug.WriteLine (message);
    }
}
```

6. Modify this callback to consume the changes as makes sense for your app. Some recommended keys for your MDM server are defined in ManagedAppConfigKeys.cs. Using these keys will help your app and its configuration be consistent with best practices.
