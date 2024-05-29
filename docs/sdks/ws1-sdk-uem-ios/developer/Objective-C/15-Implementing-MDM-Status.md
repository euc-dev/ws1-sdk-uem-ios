---
layout: page
title: Implementing MDM Status
permalink: /sdks/ws1/ws1-sdk-uem-ios/
hide:
  #- navigation
  - toc
---

The MDM Status module allows an application to check certain properties and the status of some MDM properties for the device that the application lives in.

This information is useful because you cannot obtain it directly from the SDK. You can use the data to improve security and usability at the application level. For example, a developer may want to check that another application is installed on the same device before exposing or hiding certain features in the application.

* Device Status – Indicates the following statuses:
  * Managed Status – Indicates if the device is enrolled in the onsole or not.
  * Compliance Status – Indicates if the device is conforming to all the compliance rules.
* Requery Method – Queries the console to send to the containing device a query command to collect certain types of device information.
* Compliance Policies – Retrieves a list of policies and lists details about each policy.
* Application List – Retrieves the list of applications that are available on the same device.

See the sample application for code examples.