---
layout: page
title: Activate App Tunnel
hide:
  #- navigation
  - toc
---

The purpose of app tunneling is to redirect the traffic in your application through a specific gateway. To access internal resources in your organization, use the VMware Tunnel as the proxy.

You do not need extra code to use the app tunnel. You only need the code you added when you initialized the SDK initialization. For more information, see Initialize the SDK.

To activate app tunneling, make sure that this app has an SDK profile assigned to it in the Workspace ONE UEM console and that the profile has App Tunneling enabled with a proper proxy configuration. When you call start in AWController, it reads the SDK profile assigned to your application. If needed, it also starts the traffic redirection service for the application.

After you receive the `initialCheckDoneWithError` callback from the `AWSDKDelegate`, check to see if the error object is nil or not.

* Known Limitations and Other Considerations
  
  Due to platform and other technical limitations, only network traffic made from certain network classes can tunnel. Consider the purpose of the listed classes and review their known limitations.
