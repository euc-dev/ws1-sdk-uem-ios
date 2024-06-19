---
layout: page
title: Check Device Enrollment
hide:
  #- navigation
  - toc
---

Use the SDK to retrieve the enrollment status of the device. The snippet of code shows how to perform that check.

```
      AWDeviceStatusConfiguration *configuration = [[AWDeviceStatusConfiguration alloc] initWithHostName:nilendpointPath:nil deviceStatusAction:nil];
       
      // Create the device status controller.
      AWDeviceStatusController *statusController = [[AWDeviceStatusController alloc] initWithConfiguration:configuration];
       
      // Query AirWatch to determine if the device is enrolled.
      [statusController queryDeviceEnrollmentStatus:^(BOOL enrolled, NSError *error) 
      {
      // Log the result of the enrollment check.
      NSLog(@"This device %@ enrolled.", (enrolled == YES) ? @"is" : @"is not");
      // Clean up.
      [configuration release];
      [statusController release];
      }];
```
