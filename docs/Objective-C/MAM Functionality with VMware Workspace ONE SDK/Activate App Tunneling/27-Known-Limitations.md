---
layout: page
title: Known Limitations and Other Considerations
hide:
  #- navigation
  - toc
---

Due to platform and other technical limitations, only network traffic made from certain network classes can tunnel. Consider the purpose of the listed classes and review their known limitations.

* NSURLConnection – Calls made with NSURLConnection tunnel. There is one exception to this behavior. If calls are made synchronously on the main thread, they do not tunnel.
* NSURLSession – Calls made using NSURLSession tunnel only on iOS 8+ devices and depending on the configuration used. Default and ephemeral configuration types tunnel. However, background configuration types do not tunnel.
* CFNetwork – Most calls made using CFNetwork tunnel. However, CFSocketStream do not tunnel.
* URLs that contain .local – Requests with URLs containing .local do not tunnel. Various Apple services on the device use this .local string pattern. The SDK does not tunnel these requests through the VMware Tunnel to avoid interfering with these services.
* WKWebView - Requests made with WKWebView do not tunnel so use UIWebView.
