---
layout: page
title: SDK Log Types
hide:
  #- navigation
  - toc
---

Workspace ONE UEM displays logs for applications that report application failures and that report application-specific data. These logs integrate with the VMware Workspace ONE SDK so that you can manage applications built by it.

Find logs for applications in Apps & Books > Analytics > App Logs.

| Setting | Description |
| --- | --- |
| Application Logs | This type of log captures information about an application. You set the log level in the default SDK profiles section, Groups & Settings > All Settings > Apps > Settings and Policies > Settings > Logging. You must add code into the application to upload these logs to the Workspace ONE UEM console. |
| Crash Logs | This type of log captures data from an application the next time the application runs after it crashes. These logs are automatically collected and uploaded to the Workspace ONE UEM console without the need for extra code in the SDK application. |
