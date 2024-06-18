---
layout: page
title: Compliance or Compromised Protection
hide:
  #- navigation
  - toc
---

You can use a method in your SDK-built app to check the compromised status of devices. This method works whether the device is offline or online.

Code this method to work after initialization.
```
	func initialCheckDoneWithError(_ error: Error!) {
        guard error != nil else {
            return
        }
        
        let status = AWController.clientInstance()?.jailBrokenStatus()
        if status == AWDeviceJailBroken {
            print("Device is jailbroken. Take necessary actions")
        }
    }
```

* The method can return one of three statuses.
* `AWDeviceJailBroken`: The device is identified as compromised.
* `AWDeviceNotJailBroken`: The device is not identified as compromised.
* `AWJailBrokenStatusNotAvailable`: The status is not available because the SDK initialization failed or the SDK is in the process of being initialized.
  
  Note: The SDK refreshes the jailbroken status every time the app becomes active. If the status is queried during a refresh, the app returns `AWJailBrokenStatusNotAvailable`.