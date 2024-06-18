---
layout: page
title: Initialize the AWRestrictions Class
hide:
  #- navigation
  - toc
---

To monitor the MDM enrollment and allow offline mode restrictions, the application must initialize the AWRestrictions class.

The example code starts the monitoring of the defined SDK restrictions. The system can initialize it multiple times with no adverse effect.

```
      NSError *error = nil;
      [AWRestrictions startService:&error];
       
      if (error)
      {
      NSLog(@"AWRestrictions startService error: %@", error);
      }
```
